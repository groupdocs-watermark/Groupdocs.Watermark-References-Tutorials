---
date: 2026-09-16
description: Lär dig hur du lägger till watermark i pdf, laddar dokument från olika
  källor och sparar watermarked files med GroupDocs.Watermark for Java.
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: Lägg till watermark i pdf snabbt med GroupDocs.Watermark for Java.
  Lär dig att ladda dokument, hantera lösenord och spara watermarked files.
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: Lägg till watermark i pdf med GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: Hur du lägger till watermark i pdf med GroupDocs.Watermark for Java
type: docs
url: /sv/java/document-loading-saving/
weight: 2
---

# Lägg till vattenstämpel i pdf med GroupDocs.Watermark för Java

I den här guiden kommer du att lära dig hur du **lägger till vattenstämpel i pdf**-filer med hjälp av GroupDocs.Watermark Java SDK. Vi går igenom hur man laddar dokument från disk, strömmar eller lösenordsskyddade källor, applicerar text- eller bildvattenstämplar och slutligen sparar den uppdaterade PDF-filen. Oavsett om du bygger en batch‑processor eller en en‑fil‑tjänst, ger dessa steg dig en pålitlig, produktionsklar lösning.

## Snabba svar
- **Kan jag lägga till en vattenstämpel i ett lösenordsskyddat PDF?** Ja – ange lösenordet när du laddar dokumentet, och applicera sedan vattenstämpeln som vanligt.  
- **Vilka format kan vattenmärkas?** Över 30 format, inklusive PDF, DOCX, PPTX och bilder.  
- **Behöver jag en licens för utveckling?** En tillfällig licens fungerar för testning; en full licens krävs för produktion.  
- **Vilken Java‑version krävs?** Java 8 eller högre stöds.  
- **Stöds strömning?** Absolut – du kan ladda från `InputStream` och spara till `OutputStream` utan att röra filsystemet.

## Vad är lägga till vattenstämpel i pdf?
*Add watermark to pdf* avser processen att överlagra halvtransparent text eller bilder på varje sida i ett PDF‑dokument för att förmedla äganderätt, konfidentialitet eller varumärkesprofilering. GroupDocs.Watermark för Java tillhandahåller ett enkelfunktions‑API som automatiskt hanterar positionering, opacitet och sidintervallval.

## Varför använda GroupDocs.Watermark för Java?
GroupDocs.Watermark stöder **35+ filformat** och kan bearbeta **500‑sidiga PDF‑filer på under 2 sekunder** på en vanlig server‑klass CPU. Biblioteket arbetar helt i minnet, så du behöver aldrig ha Microsoft Office eller Adobe Acrobat installerat. Dess API är trådsäkert, vilket gör det idealiskt för höggenomströmmande webbtjänster.

## Förutsättningar
- Java 8 eller nyare installerat.  
- Maven‑ eller Gradle‑projekt konfigurerat med `groupdocs-watermark`‑beroendet.  
- En giltig GroupDocs.Watermark‑licens (tillfällig licens för utvärdering).  
- PDF‑filer du vill skydda, eventuellt med lösenord.

## Så här lägger du till vattenstämpel i pdf – steg för steg

Läs in källdokumentet, applicera en vattenstämpel och spara sedan resultatet. Följande avsnitt svarar på varje deluppgift direkt.

### Hur laddar man ett dokument från disk?

`Watermarker` är den primära klassen som används för att ladda och manipulera dokument för vattenmärkning. Ange den fullständiga filsökvägen till `Watermarker`‑konstruktorn; SDK:n upptäcker automatiskt filformatet, validerar innehållet och laddar dokumentet i minnet redo för alla vattenstämpel‑operationer. Detta tillvägagångssätt fungerar för PDF‑filer, Word‑filer, bilder och många andra stödjade typer.  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

Efter den här raden är PDF‑filen helt inläst i minnet, redo för alla vattenstämpel‑operationer.

### Hur laddar man ett dokument från en ström?

`Watermarker` kan också ta emot en `InputStream` för att ladda dokument direkt från minnet. När du får en fil via HTTP eller en meddelandekö, omslut byte‑arrayen i en `ByteArrayInputStream` och skicka den till `Watermarker`‑konstruktorn som accepterar en `InputStream`. SDK:n läser strömmen utan att skriva till disk, vilket bevarar prestanda och säkerhet, och stödjer stora filer genom att bearbeta data i bitar. Denna metod är idealisk för webbtjänster och mikrotjänst‑arkitekturer.  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

SDK:n läser strömmen utan att skriva till disk, vilket bevarar prestanda och säkerhet.

### Hur laddar man ett lösenordsskyddat dokument?

`Watermarker` stödjer inläsning av lösenordsskyddade PDF‑filer genom att ange lösenordet som ett andra argument. Ange lösenordet som ett andra argument till konstruktorn. SDK:n dekrypterar PDF‑filen i realtid, varefter du kan behandla den som vilket annat dokument som helst. Om lösenordet är korrekt blir alla sidor tillgängliga för vattenmärkning; annars kastar biblioteket ett tydligt undantag som du kan fånga och logga för felsökning.  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

Om lösenordet är felaktigt kastar SDK:n ett informativt undantag som du kan fånga och logga.

### Hur applicerar man en textvattenstämpel?

`TextWatermark` representerar en textbaserad vattenstämpel som kan appliceras på sidor med anpassningsbar stil. Skapa ett `TextWatermark`‑objekt med önskad text, teckensnitt, storlek och färg. Anropa sedan `add` på `Watermarker`‑instansen, eventuellt med angivna sidintervall. Vattenstämpeln renderas med den angivna opaciteten och rotationen, och den kan placeras med fördefinierade positioner eller egna koordinater, vilket säkerställer ett enhetligt utseende på alla sidor.  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

Detta anrop placerar vattenstämpeln på varje sida som standard; du kan begränsa den med `new PageRange(1, 5)` om så behövs.

### Hur applicerar man en bildvattenstämpel?

`ImageWatermark` representerar en bildbaserad vattenstämpel, såsom en logotyp eller sigill. Instansiera ett `ImageWatermark` med sökvägen eller strömmen för din logotyp, och lägg sedan till det på samma sätt som textvattenstämpeln. SDK:n skalar automatiskt bilden för att passa sidan samtidigt som bildförhållandet bevaras, och du kan justera opacitet, rotation och placering för att uppnå önskad visuell effekt utan att förvränga originalinnehållet.  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

SDK:n skalar bilden för att passa sidan samtidigt som bildförhållandet bevaras.

### Hur sparar man det vattenmärkta dokumentet?

`save` skriver det modifierade dokumentet till den angivna platsen i det valda formatet. Anropa `save` med utsökvägen och önskat format. Samma format som källan används när du utelämnar formatparametern. Metoden skriver den modifierade PDF‑filen till disk, bevarar allt originalinnehåll förutom de nyss tillagda vattenstämpellagren, och stödjer sparande till strömmar för vidare bearbetning.  
```java
watermarker.save("C:/files/output.pdf");
```

Metoden skriver den modifierade PDF‑filen till disk, bevarar allt originalinnehåll förutom de nyss tillagda vattenstämpellagren.

## Tillgängliga handledningar

### [Hur man laddar lösenordsskyddade dokument i Java med GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-documents/)
Lär dig hur du laddar och hanterar vattenstämplar i lösenordsskyddade dokument med GroupDocs.Watermark för Java. Denna guide ger steg‑för‑steg‑instruktioner, praktiska exempel och felsökningstips.

### [Hur man laddar och vattenmärker lösenordsskyddade Word‑dokument med GroupDocs.Watermark i Java](./groupdocs-watermark-java-password-protected-word-docs/)
Lär dig hur du använder GroupDocs.Watermark med Java för att ladda, hantera och vattenmärka lösenordsskyddade Word‑dokument på ett effektivt sätt.

## Ytterligare resurser

- [GroupDocs.Watermark för Java-dokumentation](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark för Java API‑referens](https://reference.groupdocs.com/watermark/java/)
- [Ladda ner GroupDocs.Watermark för Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark‑forum](https://forum.groupdocs.com/c/watermark)
- [Gratis support](https://forum.groupdocs.com/)
- [Tillfällig licens](https://purchase.groupdocs.com/temporary-license/)

## Vanliga problem och lösningar
- **Felaktigt lösenord‑fel** – dubbelkolla lösenordsträngen; den måste vara UTF‑8‑kodad.  
- **Out‑of‑memory på stora PDF‑filer** – aktivera strömningsläge genom att använda `Watermarker`‑konstruktörer som accepterar `InputStream` och `OutputStream`.  
- **Vattenstämpeln syns inte** – säkerställ att vattenstämpelns opacitet är satt över 0.1 och att färgen kontrasterar mot sidbakgrunden.

## Vanliga frågor

**Q: Kan jag lägga till flera vattenstämplar i samma PDF?**  
A: Ja. Anropa `watermarker.add()` upprepade gånger med olika `TextWatermark`‑ eller `ImageWatermark`‑objekt; var och en kommer att staplas i den ordning de läggs till.

**Q: Bevarar biblioteket befintliga annotationer?**  
A: Absolut. Alla ursprungliga PDF‑objekt, inklusive annotationer, formulärfält och metadata, förblir orörda såvida du inte explicit ändrar dem.

**Q: Är det möjligt att vattenmärka endast utvalda sidor?**  
A: Ja. Skicka en `PageRange` (t.ex. `new PageRange(2, 4)`) till `add`‑metoden för att begränsa vattenstämpeln till specifika sidor.

**Q: Vad är den maximala filstorleken som stöds?**  
A: SDK:n kan hantera filer upp till **2 GB** utan att ladda hela dokumentet i minnet, tack vare dess strömningsarkitektur.

**Q: Hur tar jag bort en vattenstämpel efter att den har lagts till?**  
A: Använd `watermarker.remove(watermarkId)` där `watermarkId` är identifieraren som returnerades när du först lade till vattenstämpeln.

---

**Senast uppdaterad:** 2026-09-16  
**Testad med:** GroupDocs.Watermark 23.9 for Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Hur man lägger till en textvattenstämpel i PDF med GroupDocs.Watermark för Java (2023‑guide)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [Hur man lägger till text‑ och bildvattenstämplar på specifika PDF‑sidor med GroupDocs.Watermark för Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Hur man laddar lösenordsskyddade dokument i Java med GroupDocs.Watermark](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)