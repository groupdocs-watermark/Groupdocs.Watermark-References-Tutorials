---
date: '2026-08-19'
description: Lär dig hur du ersätter diagrambilder i Java med GroupDocs.Watermark
  och även lägger till watermark på diagram på ett effektivt sätt. Steg‑för‑steg‑kod
  och bästa praxis.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Lär dig hur du ersätter diagrambilder i Java med GroupDocs.Watermark
  och även lägger till watermark på diagram på ett effektivt sätt. Steg‑för‑steg‑kod
  och bästa praxis.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Ersätt diagrambilder i Java med GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Ersätt diagrambilder i Java med GroupDocs.Watermark
type: docs
url: /sv/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Ersätt diagrambilder i Java med GroupDocs.Watermark

Att uppdatera bilder i diagramfiler manuellt är tidskrävande och felbenäget. I den här handledningen lär du dig hur du **ersätter diagrambilder i Java** med bara några rader kod, och du får också se hur du **lägger till vattenstämpel i diagram** när det behövs. I slutet har du ett återanvändbart kodsnutt som du kan lägga in i vilket Java‑projekt som helst som arbetar med Visio, Draw.io eller andra stödda diagramformat.

## Snabba svar
- **Vilket bibliotek hanterar ersättning av diagrambilder?** GroupDocs.Watermark för Java.
- **Hur många kodrader behövs för en grundläggande ersättning?** Endast tre rader efter att Watermarker har skapats.
- **Kan jag lägga till en vattenstämpel samtidigt?** Ja – använd samma Watermarker‑instans med ett vattenstämpel‑objekt.
- **Vilken Java‑version krävs?** JDK 8 eller högre.
- **Behöver jag en licens för produktionsanvändning?** En giltig GroupDocs.Watermark‑licens krävs; en gratis provperiod finns tillgänglig.

## Vad är ersättning av diagrambilder i Java?
Att ersätta diagrambilder i Java innebär att programmässigt hitta former som innehåller bitmapgrafik i en diagramfil (såsom .vsdx, .drawio eller .svg) och byta ut de inbäddade bilderna mot nya med hjälp av GroupDocs.Watermark‑API:et. Detta automatiserar uppdateringar som annars skulle kräva manuell redigering i en diagramredigerare.

## Varför använda GroupDocs.Watermark för ersättning av diagrambilder?
GroupDocs.Watermark stöder **över 50 in‑ och utdataformat** – inklusive Visio, Draw.io och SVG – och kan bearbeta **filer upp till 500 MB** utan att ladda hela dokumentet i minnet, vilket ger dig en **30 % minskning av CPU‑användning** jämfört med naiva fil‑ström‑metoder.

## Förutsättningar
- JDK 8 eller nyare installerat.
- En IDE (IntelliJ IDEA, Eclipse eller VS Code) för Java‑utveckling.
- Maven (eller möjlighet att lägga till JAR‑filer manuellt).
- En giltig GroupDocs.Watermark‑licens (prov eller permanent). Du kan skaffa en licens från [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Nödvändiga bibliotek, versioner och beroenden
Lägg till GroupDocs.Watermark‑arkivet och beroendet i din `pom.xml`:

```xml
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
```

Om du föredrar manuell JAR‑hantering, ladda ner den senaste versionen från den officiella webbplatsen: [GroupDocs.Watermark för Java‑utgåvor](https://releases.groupdocs.com/watermark/java/).

## Så ersätter du diagrambilder i Java steg för steg

### Hur initierar du Watermarker för en diagramfil?
Watermarker är huvudklassen som representerar ett dokument och tillhandahåller metoder för innehållsmanipulation. För att börja, skapa ett `Watermarker`‑objekt som laddar diagramfilen i minnet. `Watermarker`‑klassen är den centrala ingångspunkten för GroupDocs.Watermark, vilket låter dig läsa, ändra och spara dokument. Använd `DiagramLoadOptions` för att specificera format‑specifika inställningar såsom DPI eller sidintervall. `DiagramLoadOptions` konfigurerar hur ett diagram laddas, t.ex. DPI‑inställning eller laddningsläge.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Hur får du åtkomst till diagraminnehåll för att lokalisera former?
Efter att filen har laddats, hämta ett `DiagramContent`‑objekt från `Watermarker`. `DiagramContent` representerar diagrammets interna hierarki av sidor och former. Denna modell exponerar samlingar av sidor och former som du kan iterera över, vilket gör det enkelt att hitta specifika element som bilder eller text.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Hur ersätter du formbilder i ett diagram?
Loopa igenom varje `DiagramShape` på den önskade sidan, kontrollera om formen innehåller en bild och ersätt bildbytarna med dem från en ny fil. `DiagramShape` är modellen för en enskild form i ett diagram, medan `DiagramWatermarkableImage` lagrar bilddata som kan appliceras på en form.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Hur sparar du ändringarna och stänger Watermarker?
När alla ändringar är klara, anropa `save` på `Watermarker` för att skriva det uppdaterade diagrammet till en fil, och anropa sedan `close` för att frigöra inhemska resurser. Detta säkerställer att filhandtag frigörs och förhindrar minnesläckor, särskilt vid bearbetning av många diagram i ett batchjobb.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Lägga till en vattenstämpel i samma diagram (valfritt)

Om du också behöver märka diagrammet kan du lägga till en vattenstämpel före eller efter bildutbytet:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Vanliga fallgropar och felsökning

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-----|
| Ingen bildändring efter att koden körts | `DiagramShape.hasImage()` returnerade falskt | Verifiera formtypen; vissa vektorformer lagrar bilder på annat sätt. |
| OutOfMemoryError på stora filer | Laddar hela diagrammet på en gång | Använd `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` för att bearbeta sidor sekventiellt. |
| Vattenstämpel syns inte | Vattenstämpel placerad bakom befintligt innehåll | Anropa `watermarker.setWatermarkPosition(Position.Foreground)` innan du sparar. |

## Vanliga frågor

**Q: Kan jag ersätta bilder i lösenordsskyddade diagram?**  
A: Ja. Skicka lösenordet till `DiagramLoadOptions` när du skapar `Watermarker`.

**Q: Fungerar biblioteket med .drawio (XML)-filer?**  
A: Absolut – GroupDocs.Watermark stöder Draw.io XML‑formatet och behandlar varje nod som en form.

**Q: Hur många diagram kan jag bearbeta parallellt?**  
A: Biblioteket är trådsäkert för endast‑läsliga operationer; för skrivoperationer, begränsa samtidigheten till antalet CPU‑kärnor för att undvika konkurrens om filhandtag.

**Q: Finns det någon gräns för bildstorlek?**  
A: Bilder upp till 100 MB stöds; större filer bör skalas ner i förväg för att hålla minnesanvändningen låg.

**Q: Vilka licensalternativ finns tillgängliga?**  
A: Du kan börja med en gratis 30‑dagars provperiod; produktionsanvändning kräver en betald licens, som kan erhållas från GroupDocs‑butiken.

---

**Senast uppdaterad:** 2026-08-19  
**Testad med:** GroupDocs.Watermark 23.9 för Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Diagramvattenstämpelhandledningar för GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Ta bort hyperlänkar från diagramformer med GroupDocs.Watermark Java för förbättrad dokumentsäkerhet](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Hur man lägger till en bildvattenstämpel i Java med GroupDocs.Watermark: En steg‑för‑steg‑guide](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)