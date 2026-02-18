---
date: '2026-02-18'
description: Lär dig hur du lägger till vattenstämpel och hur du tar bort vattenstämpel
  i diagramfiler som .vsdx med GroupDocs.Watermark för Java. Skydda dokumentets integritet
  med GroupDocs.Watermark för Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Hur man lägger till en vattenstämpel i diagram med GroupDocs.Watermark för
  Java
type: docs
url: /sv/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Så lägger du till vattenstämpel i diagram med GroupDocs.Watermark för Java

Att hantera vattenstämplar i diagramfiler är en grundläggande del av att skydda immateriella rättigheter och hålla dokument rena för offentlig distribution. I den här guiden lär du dig **hur du lägger till vattenstämpel** i ett Visio‑diagram, samt **hur du tar bort vattenstämpel** när den inte längre behövs, allt med **groupdocs watermark java**‑biblioteket. Oavsett om du bygger en företagsklassad dokumentpipeline eller ett snabbt verktygsskript, ger dessa steg dig full kontroll över vattenstämpling av diagram.

## Snabba svar
- **Vilket bibliotek hanterar diagramvattenstämplar i Java?** GroupDocs.Watermark för Java.  
- **Kan jag lägga till och ta bort vattenstämplar i samma körning?** Ja – ladda diagrammet en gång och utför både lägg‑till‑ och ta‑bort‑operationer.  
- **Vilka filformat stöds?** Visio‑format som `.vsdx`, `.vdx`, samt andra diagramtyper.  
- **Behöver jag en licens?** En provlicens fungerar för utveckling; en full licens krävs för produktion.  
- **Vilken Java‑version krävs?** JDK 8 eller högre.

## Vad betyder “how to add watermark” i diagramkontext?
Att lägga till en vattenstämpel innebär att bädda in en synlig eller osynlig markör – text, logotyp eller bild – i en diagramfil. Denna markör följer med filen och gör det enkelt att bevisa ägandeskap eller flagga utkastversioner.

## Varför använda GroupDocs.Watermark för Java?
* **Rich API** – Sök, lägg till och ta bort både text‑ och bildvattenstämplar med några få kodrader.  
* **Cross‑format support** – Fungerar med Visio (`.vsdx`, `.vdx`) och många andra diagramtyper.  
* **Performance‑focused** – Laddar endast de delar av ett diagram som behövs för vattenstämpeloperationer, vilket håller minnesanvändningen låg.

## Förutsättningar
1. **Java Development Kit (JDK) 8+** – Säkerställ att `java -version` visar 1.8 eller nyare.  
2. **IDE** – IntelliJ IDEA, Eclipse eller någon annan editor du föredrar.  
3. **GroupDocs.Watermark för Java** – Lägg till i ditt projekt via Maven eller en direkt JAR‑nedladdning.  

### Nödvändiga bibliotek och beroenden
Lägg till repository och beroende i din `pom.xml`:

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

*Om du föredrar att inte använda Maven kan du ladda ner den senaste JAR‑filen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Licensanskaffning
- **Gratis prov:** Testa alla funktioner utan licensnyckel.  
- **Tillfällig licens:** Begär en tidsbegränsad nyckel för utvärdering.  
- **Full licens:** Köp ett abonnemang för obegränsad produktionsanvändning.

## Installera GroupDocs.Watermark för Java
1. **Lägg till biblioteket** i ditt projekt (Maven eller manuell JAR).  
2. **Skapa en `Watermarker`‑instans** – detta objekt är ingångspunkten för att ladda diagram, söka, lägga till och ta bort vattenstämplar.

## Implementeringsguide

### Ladda ett diagramdokument
Laddning är första steget innan du kan **lägga till vattenstämpel** eller **ta bort vattenstämpel**. Koden nedan visar hur du öppnar en `.vsdx`‑fil med anpassade laddningsalternativ.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Söka efter textvattenstämplar
Innan du lägger till en ny vattenstämpel kan du vilja verifiera om en textvattenstämpel redan finns. Detta kodsnutt söker efter frasen “Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Söka efter bildvattenstämplar
Om du behöver lokalisera en logotyp eller någon bild som använts som vattenstämpel, använd `ImageDctHashSearchCriteria`. Detta är praktiskt när du vill **ta bort vattenstämpel** som matchar en känd logotyp.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Ta bort vattenstämplar
När du har identifierat vattenstämplar – text, bild eller båda – kan du rensa dem från diagrammet. Exemplet nedan demonstrerar en kombinerad borttagningsoperation.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Praktiska tillämpningar
1. **Enterprise‑software‑integration** – Bädda in vattenstämpelhantering i ditt ERP‑ eller dokumentgenereringssystem för att upprätthålla varumärkesprofilen.  
2. **Content Management Systems (CMS)** – Skanna automatiskt uppladdade diagram för obehöriga logotyper och ta bort dem.  
3. **Legal Document Handling** – Lägg till en “Confidential”‑textvattenstämpel under utkastfaser och **ta bort vattenstämpel** innan slutlig inlämning.

## Vanliga problem och lösningar
| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-------|
| Inga vattenstämplar hittas | Söktext/-bild matchar inte exakt | Använd `or()` för att kombinera kriterier eller justera skiftlägeskänsligheten. |
| `OutOfMemoryError` på stora filer | Diagrammet laddas helt i minnet | Använd `DiagramLoadOptions.setLoadPages()` för att ladda endast nödvändiga sidor. |
| Sparad fil är korrupt | `watermarker.save()` anropas innan alla vattenstämplar rensats | Säkerställ att `possibleWatermarks.clear()` slutförs och att `watermarker.close()` anropas efter sparning. |

## Vanliga frågor

**Q: Kan jag söka efter både text och bilder samtidigt?**  
A: Ja. Kombinera `TextSearchCriteria` och `ImageDctHashSearchCriteria` med `or()`‑metoden, som visas i borttagningsexemplet.

**Q: Är det möjligt att ta bort vattenstämplar utan att skada diagrammet?**  
A: Absolut. Biblioteket isolerar vattenstämpelobjekt, så ett anrop till `clear()` tar bara bort vattenstämpellagren medan originalinnehållet bevaras.

**Q: Stöder GroupDocs.Watermark flera diagramformat?**  
A: Ja. Format som `.vsdx`, `.vdx` och andra Visio‑kompatibla filer stöds fullt ut.

**Q: Hur hanterar jag stora volymer dokument på ett effektivt sätt?**  
A: Implementera batch‑processloopar, återanvänd en enda `Watermarker`‑instans där det är möjligt, och begränsa sidladdning med `DiagramLoadOptions`.

**Q: Finns det ett sätt att automatisera vattenstämpeldetektion i en CI/CD‑pipeline?**  
A: Du kan bädda in de medföljande Java‑snuttarna i dina byggskript (t.ex. Maven eller Gradle) för att validera att inga obehöriga vattenstämplar finns innan artefakter släpps.

---

**Senast uppdaterad:** 2026-02-18  
**Testat med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs