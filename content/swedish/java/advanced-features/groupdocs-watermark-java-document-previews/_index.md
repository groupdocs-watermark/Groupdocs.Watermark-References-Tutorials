---
date: '2026-09-26'
description: Lär dig hur du konverterar dokument till bild och genererar thumbnails
  med Java och GroupDocs.Watermark. Steg-för-steg-guiden täcker installation, preview
  streams och prestandatips.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Lär dig hur du konverterar dokument till bild och genererar thumbnails
  med Java och GroupDocs.Watermark. Denna guide går igenom installation, stream handling
  och performance optimisation för snabb preview creation.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Konvertera dokument till bild med GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Konvertera dokument till bild med GroupDocs.Watermark Java
type: docs
url: /sv/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Konvertera dokument till bild med GroupDocs.Watermark Java

Att generera lätta bildförhandsvisningar av flersidiga dokument är ett vanligt krav för portaler, innehållshanteringssystem och molnlagringstjänster. Genom att **convert document to image** ger du slutanvändare en snabb visuell ledtråd utan att behöva ladda hela filen. GroupDocs.Watermark Java‑biblioteket lägger inte bara till vattenstämplar utan erbjuder också en högpresterande förhandsvisningsmotor som kan **java generate thumbnails** för varje sida i ett enda pass.

I den här handledningen kommer du att lära dig hur du installerar biblioteket, skapar anpassade sidströmmar, frigör resurser på ett säkert sätt och slutligen producerar bildförhandsvisningar för varje sida i ett källdokument. Instruktionerna är skrivna för utvecklare som är bekanta med Java och objektorienterade koncept, och de innehåller bästa praxis‑tips för hantering av stora filbatcher.

## Snabba svar
- **Vad är första steget?** Lägg till GroupDocs.Watermark Maven‑beroendet och initiera en `Watermarker` med källdokumentets filsökväg.  
- **Hur skapas förhandsvisningsbilder?** Implementera `ICreatePageStream` för att öppna en utdata‑ström för varje sida, och anropa sedan `generatePreview()` med lämpliga alternativ.  
- **Behöver jag en licens?** En provversion fungerar för grundläggande scenarier, men en full licens tar bort vattenstämplar och låser upp batch‑bearbetning.  
- **Kan jag bearbeta PDF‑filer som är större än 200 sidor?** Ja – biblioteket strömmar sidor, så minnesanvändningen förblir låg även för filer med 500 sidor.  
- **Vilka bildformat stöds?** PNG, JPEG, BMP och TIFF finns tillgängliga direkt ur lådan.

## Vad är convert document to image?
Frasen **convert document to image** beskriver processen att rendera varje sida i en källfil (PDF, DOCX, PPTX osv.) till en rasterbild som PNG eller JPEG. Denna konvertering är användbar för miniatyrgallerier, förhandsvisningspaneler och mobila dokumentvisare.

## Varför använda GroupDocs.Watermark för förhandsgenerering?
GroupDocs.Watermark stöder **30+ inmatningsformat** och kan generera förhandsvisningar för dokument upp till **500 sidor** utan att ladda hela filen i minnet. Internt bearbetar det sidor sekventiellt, vilket håller Java‑heap‑användningen under 50 MB även för stora PDF‑filer. Biblioteket erbjuder också inbyggd bildoptimering, så att du kan ange DPI, färgdjup och komprimeringsnivå, vilket resulterar i miniatyrer som vanligtvis är **70 % mindre** än naiv rasterisering.

## Förutsättningar

Innan du börjar, se till att du har följande:

- **Java Development Kit (JDK) 11 eller nyare** – biblioteket är kompilerat för Java 8+, men JDK 11 ger långsiktigt stöd och bättre prestanda.
- **Maven 3.6+** – för beroendehantering.
- **GroupDocs.Watermark för Java version 24.11** – den senaste stabila releasen vid skrivtillfället.
- **Grundläggande kunskap om Java I/O‑strömmar** – du kommer att skapa `FileOutputStream`‑objekt för varje förhandsvisningssida.
- **En licensnyckel** (valfri för produktion) – provversionen begränsar förhandsvisningsstorleken till 5 MB per dokument.

## Så här installerar du GroupDocs.Watermark för Java

För att installera GroupDocs.Watermark, lägg först till Maven‑arkivet och inkludera sedan biblioteket som ett beroende i ditt projekts `pom.xml`. Detta säkerställer att Maven kan ladda ner rätt artefakter och gör klasserna tillgängliga på klassvägen för kompilering och körning.

### Lägg till Maven‑beroendet
Biblioteket distribueras via Maven Central. Lägg till följande kodsnutt i din `pom.xml` inom `<dependencies>`‑blocket:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Proffstips:** Håll versionsnumret i en egenskap (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) så att du enkelt kan uppgradera.

### Direktnedladdning (alternativ)
Om du föredrar manuell installation kan du ladda ner JAR‑filen från den officiella releases‑sidan: [GroupDocs.Watermark för Java releases](https://releases.groupdocs.com/watermark/java/).

## Så här skaffar och tillämpar du en licens

Att tillämpa en licens på GroupDocs.Watermark tar bort provbegränsningar och inaktiverar standardvattenstämpel‑övertäckningen. Placera licensfilen på en känd plats och peka API‑et på den, eller bädda in licenssökvägen direkt i koden innan några andra anrop. När den är laddad körs alla efterföljande operationer i full‑funktionsläge.

Du kan:

- **Begära en gratis provlicens** från GroupDocs‑portalen – den ger en 30‑dagars licensfil.
- **Generera en temporär licens** via den online‑licensgeneratorn för utvärderingsmiljöer.
- **Köpa en kommersiell licens** för obegränsad produktionsanvändning och prioriterat stöd.

Placera licensfilen (`GroupDocs.Watermark.lic`) i projektets rot eller ange dess sökväg programatiskt med `Watermarker.setLicense("path/to/license.file")`.

## Så här initierar du Watermarker

Initiera `Watermarker` genom att ange sökvägen till källdokumentet, eventuellt med ett lösenord för skyddade filer. Konstruktorn validerar formatet och förbereder interna parserare, så att du omedelbart kan anropa förhandsvisnings‑ eller vattenstämpel‑metoder. Efter skapandet, behåll en referens för att återanvända instansen för flera operationer om så behövs.

`Watermarker`‑klassen är GroupDocs.Watermark:s kärnobjekt som laddar ett dokument och exponerar operationer såsom vattenstämpelinsättning och förhandsgenerering.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – absolut eller relativ sökväg till källfilen.
- Konstruktorn validerar filformatet och förbereder interna parserare.

> **Definition ankare:** `Watermarker` är ingångspunkten för alla dokument‑bearbetningsåtgärder i GroupDocs.Watermark för Java.

## Så här skapar du sidströmmar för förhandsgenerering

Skapa anpassade sidströmmar genom att implementera `ICreatePageStream`‑gränssnittet, som biblioteket anropar för varje sida det renderar. Din implementation bör generera ett nytt `OutputStream`—vanligtvis ett `FileOutputStream`—som pekar på en unikt namngiven fil baserad på sidnumret. Detta tillvägagångssätt isolerar varje sidas utdata och förhindrar dataöverlappning.

För att **java generate thumbnails** måste du tillhandahålla en ström för varje sida där den renderade bilden ska skrivas. Implementera `ICreatePageStream`‑gränssnittet; biblioteket anropar din implementation för varje sida den bearbetar.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** låter dig infoga sidnumret direkt i filnamnet, vilket gör batch‑bearbetning enkel.
- Metoden returnerar ett nytt `OutputStream` för varje sida, så att tidigare sidor inte stör efterföljande skrivningar.

> **Definition ankare:** `ICreatePageStream` är ett callback‑gränssnitt som låter dig definiera hur utdata‑strömmar skapas för varje förhandsvisningssida.

## Så här frigör du sidströmmar efter förhandsgenerering

När en sidbild har skrivits, anropar biblioteket `IReleasePageStream` för att låta dig stänga och rensa den associerade utdata‑strömmen. Implementera detta callback för att säkert stänga filhandtag, spola buffertar och utföra eventuell extra loggning. Korrekt städning förhindrar descriptor‑läckor och säkerställer att efterföljande sidor kan bearbetas utan störningar.

Korrekt resurshantering förhindrar fil‑handtagsläckor och håller JVM‑en från att tömma descriptorer. Implementera `IReleasePageStream` för att stänga strömmar när biblioteket signalerar att en sida är klar.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definition ankare:** `IReleasePageStream` är ett callback‑gränssnitt som låter dig definiera anpassad logik för att avyttra sid‑specifika utdataresurser.

## Så här genererar du dokumentförhandsvisningar (convert document to image)

Generera förhandsvisningar genom att anropa `generatePreview()` på `Watermarker`‑instansen, med ett `PreviewOptions`‑objekt som definierar upplösning, bildformat och sidintervall. Metoden itererar genom varje sida, använder dina strömskapare för att skriva rasterbilden och frigör sedan strömmarna. Detta skapar ett set av bildfiler som representerar dokumentets sidor.

Med `Watermarker`, `FeatureCreatePageStream` och `FeatureReleasePageStream` klara, kan du starta förhandsvisningsmotorn. `generatePreview()`‑metoden itererar över varje sida, anropar dina strömskapare, skriver bilden och släpper slutligen strömmarna.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** styr DPI; 150 DPI är en bra balans för webb‑miniatyrer.
- **`ImageFormat`** kan vara PNG, JPEG, BMP eller TIFF beroende på dina efterföljande krav.
- Metoden bearbetar sidor sekventiellt, så minnesförbrukningen förblir låg även för dokument med hundratals sidor.

> **Definition ankare:** `generatePreview()` är API‑anropet som renderar varje sida i det laddade dokumentet till en bild med de strömmar du tillhandahållit.

## Praktiska tillämpningar av convert document to image

Att generera bildförhandsvisningar öppnar många möjligheter:

1. **Dokumentbläddrare** – Visa ett rutnät av PNG‑miniatyrer så att användare snabbt kan skumma igenom stora PDF‑filer utan att öppna dem.
2. **Sökresultat‑snuttar** – Bifoga en förhandsvisningsbild till sökindex‑poster för ett rikare UI.
3. **E‑postbilagor** – Bädda in en liten förhandsvisning av bifogade PDF‑filer i e‑postens kropp.
4. **Mobila appar** – Minska bandbredden genom att skicka 200 KB PNG‑förhandsvisningar istället för fulla PDF‑filer.
5. **Efterlevnadsportaler** – Rendera lagstadgade vattenmärkta versioner av kontrakt som bilder för revisionsspår.

## Prestanda‑överväganden när du java generate thumbnails

När du hanterar bulk‑bearbetning, ha dessa optimeringstips i åtanke:

- **Strömbuffring** – Wrappa `FileOutputStream` i en `BufferedOutputStream` för att minimera disk‑I/O.
- **Parallell batch‑exekvering** – Använd Java:s `ForkJoinPool` för att bearbeta flera dokument samtidigt; varje uppgift bör skapa sin egen `Watermarker`‑instans för att undvika trådsäkerhetsproblem.
- **Begränsa DPI för miniatyrer** – 72–150 DPI räcker för de flesta UI‑scenarier; högre DPI bör reserveras för utskriftsklara förhandsvisningar.
- **Återanvänd licensobjekt** – Ladda licensfilen en gång per JVM för att minska overhead.
- **Övervaka minne** – Biblioteket håller endast den aktuella sidan i minnet. För extremt stora filer, överväg att öka JVM‑heapen något (t.ex. `-Xmx512m`) för att hantera tillfälliga spikar.

## Vanliga fallgropar och hur du undviker dem

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-----|
| `OutOfMemoryError` under förhandsgenerering | Använder `ImageFormat.Jpeg` med 300 DPI på en 1000‑sidig PDF | Minska DPI eller byt till PNG med lägre färgdjup |
| Tomma förhandsvisningsfiler | `FeatureCreatePageStream` returnerar samma `FileOutputStream` för varje sida | Säkerställ att en ny ström skapas per `pageNumber` |
| Förhandsvisningsbilder är roterade | Käll‑PDF innehåller rotationsmetadata som inte beaktas | Anropa `previewOptions.setRotatePages(true)` (om tillgängligt) |
| Licensvarning visas | Licensfilen hittas inte eller sökvägen är fel | Verifiera att `Watermarker.setLicense("path/to/license.file")` körs innan några andra API‑anrop |

## Vanliga frågor

**Q: Kan jag generera förhandsvisningar för lösenordsskyddade PDF‑filer?**  
A: Ja. Skicka lösenordet till `Watermarker`‑konstruktorn: `new Watermarker("file.pdf", "password")`.

**Q: Vilka bildformat stöds för förhandsvisningsutdata?**  
A: PNG, JPEG, BMP och TIFF är tillgängliga. PNG rekommenderas för förlustfria miniatyrer.

**Q: Hur många sidor kan bearbetas i ett enda anrop?**  
A: Biblioteket har ingen hård gräns; du kan förhandsvisa dokument med tusentals sidor, begränsat endast av lagringsutrymme och I/O‑genomströmning.

**Q: Behöver jag en separat licens för varje serverinstans?**  
A: En enda licensfil kan återanvändas på flera instanser så länge den totala användningen följer licensvillkoren.

**Q: Finns det ett sätt att generera en enda kombinerad miniatyr (t.ex. bara första sidan)?**  
A: Ja. Sätt `previewOptions.setPages(new int[]{1})` för att begränsa genereringen till den första sidan.

## Slutsats

Du har nu ett komplett, produktionsklart arbetsflöde för **convert document to image** och **java generate thumbnails** med GroupDocs.Watermark. Genom att konfigurera anpassade sid‑strömshanterare håller du minnesanvändningen låg, och genom att justera `PreviewOptions` styr du bildkvalitet och filstorlek. Dessa tekniker låter dig bädda in snabba, högkvalitativa förhandsvisningar i vilken Java‑baserad applikation som helst—oavsett om det är en webbportal, en skrivbordsklient eller en molnbaserad mikrotjänst.

---

**Senast uppdaterad:** 2026-09-26  
**Testat med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Relaterade handledningar

- [Hur du hämtar dokumentinformation med GroupDocs.Watermark för Java: En steg‑för‑steg‑guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Avancerade vattenstämpelfunktioner – handledningar för GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Hur du lägger till en bildvattenstämpel i Java med GroupDocs.Watermark: En steg‑för‑steg‑guide](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)