---
date: '2026-02-16'
description: Lär dig hur du vattenstämplar en specifik diagram‑sida med GroupDocs.Watermark
  för Java, inklusive hur du lägger till en bildvattenstämpel i Java och skyddar dina
  filer.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Vattenstämpel på specifik diagram‑sida med GroupDocs.Watermark för Java
type: docs
url: /sv/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Vattenstämpel på specifik diagramssida med GroupDocs.Watermark för Java

Att skydda dina diagram är avgörande, särskilt när du behöver **watermark specific diagram page** för immateriell säkerhet eller varumärkesattribution. I den här handledningen lär du dig steg för steg hur du lägger till både text- och bildvattenstämplar på valda sidor i en diagramfil med **GroupDocs.Watermark för Java**. När du är klar är du redo att säkra dina diagram och exakt kontrollera var varje vattenstämpel visas.

## Snabba svar
- **Vad är huvudsyftet?** Lägg till vattenstämplar på valda diagramssidor.  
- **Vilket bibliotek krävs?** GroupDocs.Watermark för Java (Maven eller direkt nedladdning).  
- **Kan jag lägga till en bildvattenstämpel i Java?** Ja – använd `ImageWatermark` med sid‑specifika alternativ.  
- **Behöver jag en licens?** En tillfällig provlicens fungerar för testning; en full licens krävs för produktion.  
- **Hur många kodrader?** Mindre än 30 rader för ett komplett text + bildvattenstämpel‑arbetsflöde.

## Vad är “watermark specific diagram page”?
En **watermark specific diagram page** innebär att applicera en visuell markör—text eller bild—endast på de sidor du väljer i ett flersidigt diagram (t.ex. Visio . vsdx). Detta ger dig fin‑granulär kontroll över varumärkesprofilering, konfidentialitetsmeddelanden eller upphovsrättsdeklarationer utan att påverka hela dokumentet.

## Varför använda GroupDocs.Watermark för Java?
- **Fullständig sidkontroll** – rikta in dig på vilket sidindex du än behöver.  
- **Rich styling** – teckensnitt, färger, opacitet, rotation och bildskalning är alla konfigurerbara.  
- **Performance‑optimized** – bearbetar stora diagram effektivt och integreras smidigt med Maven‑byggen.  
- **Cross‑format support** – fungerar med Visio, SVG och många andra diagramformat.

## Förutsättningar
- **GroupDocs.Watermark för Java** bibliotek version 24.11 eller senare.  
- Maven eller en direkt JAR‑nedladdning.  
- Grundläggande Java‑utvecklingsmiljö (JDK 8+ rekommenderas).  

## Installera GroupDocs.Watermark för Java
### Använda Maven groupdocs watermark
Inkludera GroupDocs.Watermark i ditt projekt via Maven genom att lägga till följande i din `pom.xml`:

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

### Direkt nedladdning
Alternativt, ladda ner den senaste versionen direkt från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Licensanskaffning
Börja med en gratis provperiod genom att ladda ner en tillfällig licens. Köpalternativ finns på deras officiella webbplats om du väljer att fortsätta använda GroupDocs.Watermark.

### Grundläggande initiering och konfiguration
När den är installerad, initiera `Watermarker`‑klassen för vattenstämpeloperationer:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Implementeringsguide
### Lägga till textvattenstämpel på en specifik sida
För att lägga till en textvattenstämpel, skapa och konfigurera den innan du anger målsidan.

#### Skapa en textvattenstämpel
Definiera din textvattenstämpel med anpassningsbart innehåll, teckensnittsstil, storlek osv.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Ange sidindex för vattenstämpeln
Bestäm vilken diagramssida som ska visa vattenstämpeln med `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Lägg till textvattenstämpeln
Lägg till din konfigurerade vattenstämpel i diagrammet:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Lägga till bildvattenstämpel på en specifik sida
Följ liknande steg för bildvattenstämplar med ett `ImageWatermark`‑objekt.

#### Skapa en bildvattenstämpel
Skapa en instans av `ImageWatermark` med den önskade vattenstämpelbildens sökväg:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Ange sidindex för vattenstämpeln
Specificera vilken sida som ska visa bildvattenstämpeln:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Lägg till bildvattenstämpeln
Lägg till bilden på den angivna diagramssidan:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Spara och stäng resurser
Kom ihåg att spara ändringar och stänga resurser för att undvika läckor:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Praktiska tillämpningar
- **Dokumentsäkerhet** – Applicera konfidentiella vattenstämplar endast på sidor som innehåller känsliga scheman.  
- **Varumärkesprofilering** – Placera ditt företagslogo på framsidan medan de inre sidorna förblir rena.  
- **Upphovsrättsskydd** – Lägg till ett upphovsrättsmeddelande på den sista sidan i ett tekniskt diagrampaket.

## Prestandaöverväganden
- **Minneshantering** – Stäng varje vattenstämpelobjekt efter sparning för att frigöra inhemska resurser.  
- **Bildoptimering** – Använd lämpligt storleksanpassade PNG/JPEG‑filer för att hålla bearbetningen snabb.  
- **Batch‑bearbetning** – När du hanterar många diagram, återanvänd en enda `Watermarker`‑instans där det är möjligt.

## Vanliga problem och lösningar
| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-------|
| Vattenstämpel syns inte | Fel `pageIndex` (noll‑baserad) | Verifiera att indexet matchar den avsedda sidan. |
| Bild visas förvrängd | Högupplöst källbild | Ändra storlek på bilden innan du skapar `ImageWatermark`. |
| Licensfel i produktion | Användning av provlicens efter dess utgång | Använd en full licensfil via `License.setLicense("path/to/license.json")`. |

## Vanliga frågor

**Q1: Kan jag lägga till flera vattenstämplar på en enda diagramssida?**  
A1: Ja, anropa helt enkelt `watermarker.add()` med olika vattenstämpelobjekt för samma sidindex.

**Q2: Vilka filformat stöds av GroupDocs.Watermark för Java?**  
A2: Det stöder olika diagram- och bildformat. Se [API documentation](https://reference.groupdocs.com/watermark/java) för hela listan.

**Q3: Hur hanterar jag licensproblem när jag använder en provversion?**  
A3: Börja med en gratis tillfällig licens från GroupDocs. Köp en full licens för att låsa upp alla funktioner i produktion.

**Q4: Vilka är vanliga felsökningstips om vattenstämplar inte visas som förväntat?**  
A4: Säkerställ att sidindexet är korrekt och dubbelkolla filsökvägar för bildresurser. Verifiera också att vattenstämpelns opacitet inte är satt till 0.

**Q5: Hur kan jag anpassa vattenstämpelns utseende ytterligare?**  
A5: Justera teckenstorlek, opacitet, rotation och positionering med metoder som finns på `TextWatermark` eller `ImageWatermark`.

## Resurser
- [GroupDocs.Watermark Dokumentation](https://docs.groupdocs.com/watermark/java/)  
- [API-referensguide](https://reference.groupdocs.com/watermark/java)  
- [Ladda ner bibliotek](https://releases.groupdocs.com/watermark/java/)  
- [GitHub‑arkiv](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Gratis supportforum](https://forum.groupdocs.com/c/watermark/10)  
- [Information om tillfällig licens](https://purchase.groupdocs.com/temporary-license/)

Utforska dessa resurser för att fördjupa din förståelse och dina möjligheter med GroupDocs.Watermark för Java. Lycka till med vattenstämpling!

**Senast uppdaterad:** 2026-02-16  
**Testad med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs