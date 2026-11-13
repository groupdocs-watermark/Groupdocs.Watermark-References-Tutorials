---
date: 2026-11-13
description: Lär dig hur du extraherar metadata, listar stödda format och hämtar dokumentinformation
  med GroupDocs.Watermark för Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Hur du extraherar metadata med GroupDocs.Watermark för Java. Lär dig
  att lista stödda format, hämta dokumentinformation och extrahera bildbakgrunder
  på några minuter.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Hur man extraherar metadata med GroupDocs.Watermark för Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Hur man extraherar metadata med GroupDocs.Watermark för Java
type: docs
url: /sv/java/document-information/
weight: 14
---

# Hur man extraherar metadata med GroupDocs.Watermark för Java

I den här guiden kommer du att upptäcka **hur man extraherar metadata** från ett brett spektrum av dokumenttyper med GroupDocs.Watermark för Java. Oavsett om du behöver läsa filtyp, sidantal, författarinformation eller anpassade egenskaper, ger biblioteket dig programmatisk åtkomst till denna information så att du kan fatta intelligenta beslut om vattenstämpelplacering, dokumentruttning eller efterlevnadskontroller. Handledningen visar också hur man listar stödda format, hämtar slide‑bakgrundsdata och återställer andra användbara dokumentegenskaper.

## Snabba svar
- **Kan jag extrahera metadata från PDF‑ och Word‑filer?** Ja, API:et läser metadata från över 70 vanliga format.  
- **Behöver jag en licens för utveckling?** En gratis tillfällig licens fungerar för testning; en full licens krävs för produktion.  
- **Vilken Java‑version krävs?** Java 8 eller högre stöds.  
- **Är biblioteket trådsäkert?** Kärn‑extraktionsklasser är designade för samtidig användning.  
- **Hur många format känns igen?** Mer än 70 in‑ och utdataformat känns igen direkt.

## Vad är metadataextraktion?
Metadataextraktion är processen att läsa inbäddad information—såsom författare, skapandedatum, sidantal och anpassade egenskaper—från en dokumentfil utan att ändra dess innehåll. Det möjliggör automatiserade arbetsflöden som är beroende av dokumentattribut. Det inkluderar vanligtvis egenskaper som titel, nyckelord och ändringstidstämplar, vilka kan utnyttjas för indexering och efterlevnadsrapportering.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark för Java stöder **70+ filformat**, inklusive PDF, DOCX, PPTX, XLSX och bildtyper, och kan bearbeta dokument upp till 500 MB utan att ladda hela filen i minnet. Dess API returnerar metadata i ett enda, konsekvent objekt, vilket minskar behovet av format‑specifika parserar och kortar utvecklingstiden med upp till 40 %.

## Förutsättningar
- Java 8 eller nyare installerat på din utvecklingsmaskin.  
- Maven eller Gradle för att hantera `groupdocs-watermark`‑beroendet.  
- En tillfällig eller fullständig GroupDocs.Watermark‑licensfil.

## Så här extraherar du metadata steg för steg

### Hur hämtar jag grundläggande dokumentinformation?
Klassen `Watermark` representerar ett dokument och ger åtkomst till dess metadata. Metoden `getDocumentInfo()` extraherar metadata‑objektet från det laddade dokumentet. Ladda dokumentet med `Watermark`‑klassen, anropa sedan `getDocumentInfo()` för att få ett objekt som innehåller filtyp, storlek, sidantal och skapandedatum. Detta enda anrop returnerar all kärnmetadata på under en sekund för typiska filer under 100 MB. Det returnerade `DocumentInfo`‑objektet inkluderar även dokumentets författare, senast ändrade datum och eventuella inbäddade anpassade egenskaper, vilket ger en omfattande översikt.

### Hur kan jag lista alla stödda filformat?
`SupportedFormats`‑verktyget ger en katalog över alla filtyper som SDK:n kan bearbeta. Använd `SupportedFormats`‑verktyget som tillhandahålls av SDK:n. Det returnerar en samling av formatidentifierare som du kan visa eller validera mot innan du laddar upp filer, vilket säkerställer kompatibilitet och förhindrar körningsfel. Varje post innehåller formatets namn, typisk filändelse och en kort beskrivning av dess funktioner, vilket hjälper utvecklare att validera indata innan bearbetning.

### Hur extraherar jag slide‑bakgrundsdetaljer från en PowerPoint‑fil?
`SlideInfo` är ett objekt som beskriver visuella egenskaper för en slide, såsom bakgrundsbild och dimensioner. `getSlides()` returnerar en samling av `SlideInfo`‑objekt för varje slide i presentationen. `SlideInfo`‑objektet visar bakgrundsbildens dimensioner, filstorlek och färgdjup. Åtkomst via `getSlides()`‑samlingen, iterera sedan över varje slide för att läsa dess bakgrundsegenskaper—användbart för dynamisk styling eller generering av miniatyrbilder. Dessa detaljer kan användas för att skapa miniatyrbilder, tillämpa enhetlig styling eller ersätta bakgrunder programatiskt över flera presentationer.

## Vanliga problem och lösningar
- **Saknad metadata:** Vissa äldre filer kanske inte innehåller standardegenskaper. I så fall, aktivera flaggan `extractCustomProperties` för att hämta eventuella användardefinierade fält.  
- **Stora filer orsakar tidsgränser:** Öka SDK:ns `maxMemory`‑inställning eller bearbeta dokumentet i streaming‑läge för att undvika att ladda hela filen i RAM.  
- **Fel för ej stödt format:** Verifiera formatet mot listan som returneras av `SupportedFormats` innan du försöker extrahera.

## Vanliga frågor

**Q: Kan jag extrahera metadata från lösenordsskyddade dokument?**  
A: Ja, ange lösenordet när du öppnar dokumentet; API:et kommer att dekryptera det i minnet och sedan läsa metadata.

**Q: Fungerar biblioteket på Android?**  
A: Kärn‑extraktionsfunktionerna är kompatibla med Android API 21+ när de paketeras som en standard‑JAR.

**Q: Hur hanterar jag anpassade metadatafält?**  
A: Använd metoden `getCustomProperties()` på `DocumentInfo`‑objektet; den returnerar en karta med nyckel‑värde‑par som du kan iterera över.

**Q: Finns det ett sätt att batch‑processa många filer?**  
A: Omslut extraktionslogiken i en loop och återanvänd en enda `Watermark`‑instans; SDK:n är designad för hög‑genomströmning.

**Q: Vilka licensalternativ finns tillgängliga?**  
A: GroupDocs.Watermark erbjuder eviga, prenumerations‑ och tillfälliga licenser; den tillfälliga licensen är idealisk för utvärdering och CI‑pipelines.

## Tillgängliga handledningar

### [Extrahera dokumentinformation med GroupDocs.Watermark för Java&#58; En komplett guide](./extract-document-info-groupdocs-watermark-java/)
Lär dig hur du effektivt extraherar dokumentmetadata såsom filtyp, sidantal och storlek med GroupDocs.Watermark för Java. Denna guide täcker installation, implementering och praktiska tillämpningar.

### [Extrahera PDF‑sidodimensioner i Java med GroupDocs.Watermark&#58; En komplett guide](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Lär dig hur du extraherar PDF‑sidodimensioner med GroupDocs.Watermark för Java. Denna guide täcker installation, kodexempel och praktiska tillämpningar.

### [Extrahera former från Word‑dokument med GroupDocs.Watermark i Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Lär dig hur du extraherar och analyserar former från Word‑dokument med GroupDocs.Watermark för Java, vilket förbättrar dokumentautomatisering och manipulation.

### [Hur man extraherar slide‑bakgrundsinformation med GroupDocs.Watermark för Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Lär dig hur du extraherar slide‑bakgrundsdetaljer såsom bilddimensioner och filstorlek med GroupDocs.Watermark för Java. Perfekt för anpassning, analys eller dokumentation.

### [Hur man listar stödda filformat med GroupDocs.Watermark för Java&#58; En komplett guide](./groupdocs-watermark-java-list-supported-formats/)
Lär dig hur du effektivt listar stödda filformat med GroupDocs.Watermark i Java, vilket säkerställer kompatibilitet över olika dokumenttyper.

### [Hur man hämtar dokumentinformation med GroupDocs.Watermark för Java&#58; En steg‑för‑steg‑guide](./retrieve-document-info-groupdocs-watermark-java/)
Lär dig hur du effektivt hämtar dokumentinformation såsom filtyp, sidantal och storlek med GroupDocs.Watermark för Java. Följ vår detaljerade guide med kodexempel.

### [Hur man hämtar sektionsegenskaper i Word‑dokument med GroupDocs.Watermark för Java](./groupdocs-java-word-section-properties-retrieval/)
Lär dig hur du effektivt hämtar och manipulerar sektionsegenskaper i Word‑dokument med GroupDocs.Watermark för Java. Perfekt för utvecklare som vill förbättra dokumenthantering.

## Ytterligare resurser

- [GroupDocs.Watermark för Java‑dokumentation](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark för Java API‑referens](https://reference.groupdocs.com/watermark/java/)
- [Ladda ner GroupDocs.Watermark för Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark‑forum](https://forum.groupdocs.com/c/watermark)
- [Gratis support](https://forum.groupdocs.com/)
- [Tillfällig licens](https://purchase.groupdocs.com/temporary-license/)

---

**Senast uppdaterad:** 2026-11-13  
**Testat med:** GroupDocs.Watermark 23.12 för Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Hur man listar stödda filformat med GroupDocs.Watermark för Java: En komplett guide](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Hur man hämtar dokumentinformation med GroupDocs.Watermark för Java: En steg‑för‑steg‑guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Extrahera dokumentinformation med GroupDocs.Watermark för Java: En komplett guide](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)