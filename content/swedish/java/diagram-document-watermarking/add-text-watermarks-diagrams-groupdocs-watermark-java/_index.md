---
date: '2025-12-19'
description: Lär dig hur du lägger till textvattenstämpel i diagram med GroupDocs.Watermark
  för Java. Denna steg‑för‑steg‑guide täcker installation, inställningar för vattenstämpelns
  teckensnitt och praktiska användningsfall.
keywords:
- text watermarks in Java
- add text watermark to diagram
- GroupDocs Watermark for Java setup
title: Hur man lägger till en textvattenstämpel i diagram med GroupDocs.Watermark
  för Java
type: docs
url: /sv/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Så lägger du till textvattenstämpel i diagram med GroupDocs.Watermark för Java

Att skydda dina diagram från obehörig återanvändning är en hög prioritet för många utvecklare och formgivare. I den här handledningen kommer du att lära dig **hur du lägger till textvattenstämpel** i diagramfiler med det kraftfulla **GroupDocs.Watermark for Java**-biblioteket. Vi går igenom varje steg—från Maven‑inställning till att tillämpa anpassade vattenstämpelfontinställningar—så att du snabbt och pålitligt kan säkra dina visuella tillgångar.

## Quick Answers
- **Vad gör biblioteket?** Det bäddar in text‑ (eller bild‑) vattenstämplar i över 100 dokument‑ och diagramformat.  
- **Vilket primärt nyckelord bör jag rikta in mig på?** *add text watermark* – används genom hela guiden.  
- **Behöver jag en licens?** En tillfällig provlicens fungerar för utveckling; en full licens krävs för produktion.  
- **Kan jag anpassa teckensnittet?** Ja, du kan styra teckensnittsfamilj, storlek, färg och rotation via vattenstämpelfontinställningar.  
- **Är det kompatibelt med Java‑8?** Absolut – biblioteket stöder JDK 8 och nyare.

## What is “add text watermark”?
Att lägga till en textvattenstämpel innebär att överlagra halvgenomskinlig text på varje sida eller form i ett dokument så att innehållet förblir identifierbart. Denna teknik används ofta för varumärkesprofilering, upphovsrättsskydd och samarbetsredigering.

## Why use GroupDocs.Watermark for Java?
- **Brett formatstöd** – fungerar med Visio, SVG, PDF, Word och många fler.  
- **Finjusterad kontroll** – du kan ställa in teckensnitt, färg, rotation, opacitet och placering.  
- **Enkelt API** – några rader kod klarar jobbet, vilket sparar utvecklingstid.  
- **Prestandaoptimerad** – hanterar stora filer effektivt när du stänger resurser omedelbart.

## Prerequisites
- JDK 8 eller högre installerat på din maskin.  
- En IDE som IntelliJ IDEA eller Eclipse.  
- Grundläggande kunskaper i Java (klasser, objekt och Maven).

### Required Libraries and Dependencies
Vi kommer att använda Maven för att hämta GroupDocs.Watermark‑biblioteket. Lägg till repository och beroende i din `pom.xml` exakt som visas:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

Om du föredrar en manuell nedladdning, besök den officiella sidan: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) och följ instruktionerna.

### License Acquisition
Börja med en gratis provperiod genom att skaffa en tillfällig licens från provportalen: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Ladda licensfilen innan någon vattenstämpeloperation:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Implementation Guide

### Step 1: Load Your Diagram
Först pekar du `Watermarker` på din källdiagramfil. Objektet `DiagramLoadOptions` talar om för biblioteket att behandla filen som ett diagramformat.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Step 2: Initialize the Text Watermark (with custom **watermark font settings**)
Skapa en `TextWatermark`‑instans och ange text, teckensnittsfamilj, storlek och eventuell extra formatering du behöver.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **Proffstips:** Justera `setColor` och `setRotationAngle` för att matcha dina varumärkesriktlinjer. Anropet `setBackground(false)` säkerställer att vattenstämpeln ligger ovanpå diagramformer snarare än bakom dem.

### Step 3: Choose Placement – Background vs. Foreground
GroupDocs låter dig bestämma om vattenstämpeln visas bakom diagramformer (bakgrund) eller ovanpå (förgrund). För de flesta varumärkesfall fungerar bakgrundsplacering bäst.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Step 4: Save the Watermarked Diagram
Slutligen skriv den modifierade filen till disk och frigör resurser.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Common Issues and Solutions
| Symtom | Trolig orsak | Lösning |
|--------|---------------|---------|
| **Fil ej hittad** fel | Felaktig `inputFilePath` eller saknade läsbehörigheter | Verifiera sökvägen och säkerställ att Java‑processen kan läsa filen. |
| **Vattenstämpel syns inte** | Placering satt till `Foreground` med transparent färg | Använd `Background` placering eller välj en kontrasterande färg. |
| **Out‑of‑memory‑undantag** på stora diagram | `Watermarker` stängs inte eller bearbetar många filer i en loop | Anropa `watermarker.close()` efter varje fil och överväg att bearbeta i batchar. |
| **Licens känns inte igen** | Fel licensfilssökväg eller utgången provlicens | Dubbelkolla sökvägen och använd en aktuell licensfil. |

## Practical Applications
1. **Dokumentsäkerhet** – Förhindra att konkurrenter stjäl proprietära flödesscheman.  
2. **Varumärkesprofilering** – Inkludera företagsnamn eller logotyp på alla diagramssidor.  
3. **Samarbetsspårning** – Lägg till användarinitialer som vattenstämpel för att ange vem som redigerade ett diagram.  

## Performance Considerations
- Stäng `Watermarker` omedelbart efter sparning för att frigöra inhemska resurser.  
- Håll vattenstämpeltexten kortfattad; alltför stora teckensnitt ökar behandlingstiden.  
- Testa på ett representativt urval innan du batch‑processar tusentals filer.

## Conclusion
Du har nu en komplett, produktionsklar metod för att **lägga till textvattenstämpel** i diagramfiler med **GroupDocs.Watermark for Java**. Detta tillvägagångssätt skyddar din immateriella egendom samtidigt som du får full kontroll över vattenstämpelfontinställningar och placering.

### Next Steps
- Utforska bildvattenstämplar för en visuell varumärkesdetalj.  
- Kombinera flera vattenstämplar (text + bild) för lagerbaserat skydd.  
- Automatisera batch‑bearbetning med en enkel `for`‑loop och samma API‑anrop.

## FAQ Section
1. **Kan jag använda GroupDocs.Watermark för andra filformat?**  
   Ja, det stödjer ett brett sortiment av dokumenttyper utöver diagram, inklusive PDF, DOCX, PPTX och mer.  
2. **Finns det någon gräns för hur många vattenstämplar jag kan lägga till?**  
   Ingen strikt gräns, men att lägga till många komplexa vattenstämplar kan påverka prestandan.  
3. **Hur tar jag bort en vattenstämpel från ett diagram?**  
   Biblioteket erbjuder detekterings‑ och borttagnings‑API:er; se den officiella dokumentationen för detaljer.  
4. **Kan textvattenstämplar läggas till på alla sidor eller endast utvalda?**  
   Du kan konfigurera `DiagramShapeWatermarkOptions` för att rikta in dig på specifika sidor eller former.  
5. **Vad ska jag göra om vattenstämpeln inte visas som förväntat?**  
   Verifiera placeringsinställningarna, teckensnittsfärgkontrast och säkerställ att du sparade filen efter att ha lagt till vattenstämpeln.

## Frequently Asked Questions

**Q: Fungerar GroupDocs.Watermark med de senaste Java‑versionerna?**  
A: Ja, det är fullt kompatibelt med Java 8 till Java 21.

**Q: Kan jag anpassa opaciteten för textvattenstämpeln?**  
A: Absolut. Använd `textWatermark.setOpacity(0.5)` för att sätta 50 % opacitet.

**Q: Finns det ett sätt att lägga till vattenstämplar endast på utvalda diagramformer?**  
A: Du kan filtrera former via `DiagramShapeWatermarkOptions` genom att ange form‑ID:n eller namn.

**Q: Hur hanterar jag lösenordsskyddade diagramfiler?**  
A: Ladda filen med `DiagramLoadOptions` som inkluderar lösenordet, och applicera sedan vattenstämpeln som vanligt.

**Q: Finns det licensrestriktioner för kommersiell användning?**  
A: En kommersiell licens krävs för produktionsdistributioner; provlicenser är endast för utvärdering.

## Resources
- [Dokumentation](https://docs.groupdocs.com/watermark/java/)
- [API‑referens](https://reference.groupdocs.com/watermark/java)
- [Ladda ner senaste versionen](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑arkiv](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Gratis supportforum](https://forum.groupdocs.com/c/watermark/10)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs