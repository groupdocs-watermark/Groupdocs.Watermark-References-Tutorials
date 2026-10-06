---
date: '2026-09-26'
description: Ismerje meg, hogyan lehet a dokumentumot képpé konvertálni és a Java
  segítségével thumbnail-eket generálni a GroupDocs.Watermark használatával. A lépésről-lépésre
  útmutató bemutatja a beállítást, az előnézeti adatfolyamokat és a teljesítmény tippeket.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Ismerje meg, hogyan lehet a dokumentumot képpé konvertálni és a Java
  segítségével thumbnail-eket generálni a GroupDocs.Watermark használatával. Ez az
  útmutató végigvezet a telepítésen, az adatfolyam-kezelésen és a teljesítmény optimalizáláson
  a gyors előnézet létrehozásához.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Dokumentum átalakítása képpé a GroupDocs.Watermark Java segítségével
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
title: Dokumentum átalakítása képpé a GroupDocs.Watermark Java segítségével
type: docs
url: /hu/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Dokumentum konvertálása képpé a GroupDocs.Watermark Java-val

Könnyűsúlyú kép előnézetek generálása többoldalas dokumentumokhoz gyakori követelmény a portálok, tartalomkezelő rendszerek és felhőalapú tárolási szolgáltatások számára. A **convert document to image** használatával a végfelhasználók gyors vizuális jelzést kapnak anélkül, hogy a teljes fájlt be kellene tölteni. A GroupDocs.Watermark Java könyvtár nem csak vízjeleket ad hozzá, hanem egy nagy teljesítményű előnézeti motorral is rendelkezik, amely **java generate thumbnails** képes minden oldalra egyetlen átfutásban.

Ebben az oktatóanyagban megtanulja, hogyan állítsa be a könyvtárat, hozzon létre egyedi oldal‑streameket, szabadítsa fel a erőforrásokat biztonságosan, és végül állítson elő kép előnézeteket a forrásdokumentum minden oldalához. Az útmutató fejlesztőknek készült, akik jártasak a Java és az objektum‑orientált koncepciókban, és tartalmaz legjobb gyakorlatokra vonatkozó tippeket nagy fájlbatches kezeléséhez.

## Gyors válaszok
- **Mi az első lépés?** Add the GroupDocs.Watermark Maven dependency and initialise a `Watermarker` with the source file path.  
- **Hogyan jönnek létre az előnézeti képek?** Implement `ICreatePageStream` to open an output stream for each page, then call `generatePreview()` with appropriate options.  
- **Szükségem van licencre?** A trial works for basic scenarios, but a full license removes watermarks and unlocks batch processing.  
- **Feldolgozhatok 200 oldalnál nagyobb PDF-eket?** Yes – the library streams pages, so memory usage stays low even for 500‑page files.  
- **Milyen képformátumok támogatottak?** PNG, JPEG, BMP, and TIFF are available out of the box.

## Mi a convert document to image?
A **convert document to image** kifejezés azt a folyamatot írja le, amikor egy forrásfájl (PDF, DOCX, PPTX stb.) minden oldalát raster képpé, például PNG vagy JPEG formátumba rendereljük. Ez a konverzió hasznos thumbnail galériákhoz, előnézeti panelekhez és mobilbarát dokumentumnézőkhöz.

## Miért használjuk a GroupDocs.Watermark-ot az előnézet generálásához?
A GroupDocs.Watermark **30+ bemeneti formátumot** támogat, és képes előnézeteket generálni akár **500 oldalas** dokumentumokhoz is anélkül, hogy a teljes fájlt a memóriába töltené. Belsőleg oldalanként dolgozza fel a dokumentumot, ami a Java heap használatát 50 MB alá tartja még nagy PDF-ek esetén is. A könyvtár beépített képoptimalizálást is kínál, lehetővé téve DPI, színmélység és tömörítési szint megadását, ami általában **70 % kisebb** thumbnail‑eket eredményez a naív rasterizációhoz képest.

## Előkövetelmények

- **Java Development Kit (JDK) 11 vagy újabb** – the library is compiled for Java 8+, but JDK 11 gives you long‑term support and better performance.
- **Maven 3.6+** – for dependency management.
- **GroupDocs.Watermark for Java version 24.11** – the latest stable release at the time of writing.
- **Basic knowledge of Java I/O streams** – you’ll be creating `FileOutputStream` objects for each preview page.
- **A licence key** (optional for production) – the trial limits preview size to 5 MB per document.

## Hogyan állítsuk be a GroupDocs.Watermark-ot Java-hoz

A GroupDocs.Watermark beállításához először adja hozzá a Maven tárolót, majd tartalmazza a könyvtárat függőségként a projekt `pom.xml`‑ében. Ez biztosítja, hogy a Maven letölthesse a megfelelő artefaktumokat, és a osztályok elérhetők legyenek a fordítás és futás során.

### Maven függőség hozzáadása
A könyvtár a Maven Central‑on keresztül érhető el. Adja hozzá a következő kódrészletet a `pom.xml`‑jéhez a `<dependencies>` blokkba:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Pro tip:** Keep the version number in a property (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) so you can upgrade easily.

### Közvetlen letöltés (alternatíva)
Ha a manuális telepítést részesíti előnyben, letöltheti a JAR‑t a hivatalos kiadási oldalról: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Hogyan szerezzünk és alkalmazzunk licencet

A licenc alkalmazása a GroupDocs.Watermark‑on eltávolítja a próbaverzió korlátozásait és letiltja az alapértelmezett vízjel‑réteget. Helyezze a licencfájlt egy ismert helyre, és mutassa meg az API‑nak, vagy ágyazza be a licenc útvonalát közvetlenül a kódban minden más hívás előtt. Betöltés után minden további művelet teljes funkcionalitással fut.

Megteheti:

- **Request a free trial** from the GroupDocs portal – it provides a 30‑day licence file.
- **Generate a temporary licence** via the online licence generator for evaluation environments.
- **Purchase a commercial licence** for unlimited production use and priority support.

Helyezze a licencfájlt (`GroupDocs.Watermark.lic`) a projekt gyökerébe, vagy adja meg az útvonalát programozottan a `Watermarker.setLicense("path/to/license.file")` hívással.

## Hogyan inicializáljuk a Watermarker-t

Inicializálja a `Watermarker`‑t a forrásdokumentum útvonalának megadásával, opcionálisan jelszóval a védett fájlokhoz. A konstruktor ellenőrzi a formátumot és előkészíti a belső parszereket, lehetővé téve, hogy azonnal hívja az előnézet vagy vízjel metódusokat. Létrehozás után tartson egy referenciát, hogy több művelethez újra felhasználhassa az objektumot, ha szükséges.

```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – absolute or relative path to the source file.
- The constructor validates the file format and prepares internal parsers.

> **Definition anchor:** `Watermarker` is the entry point for all document‑processing actions in GroupDocs.Watermark for Java.

## Hogyan hozzunk létre oldal‑streameket az előnézet generálásához

Hozzon létre egyedi oldal‑streameket az `ICreatePageStream` interfész megvalósításával, amelyet a könyvtár minden renderelt oldalhoz meghív. A megvalósításnak friss `OutputStream`‑et kell előállítania – általában `FileOutputStream`‑et – amely egy egyedi névvel ellátott fájlra mutat az oldal száma alapján. Ez a megközelítés elkülöníti az egyes oldalak kimenetét és megakadályozza az adat‑átfedést.

A **java generate thumbnails** funkcióhoz minden oldalhoz streamet kell biztosítania, ahová a renderelt kép íródik. Implementálja az `ICreatePageStream` interfészt; a könyvtár minden feldolgozott oldalhoz meghívja az Ön megvalósítását.
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

- **`fileNameTemplate`** lets you embed the page number directly into the file name, making batch processing straightforward.
- The method returns a fresh `OutputStream` for each page, ensuring that previous pages do not interfere with subsequent writes.

> **Definition anchor:** `ICreatePageStream` is a callback interface that lets you define how output streams are created for each preview page.

## Hogyan szabadítsuk fel az oldal‑streameket az előnézet generálása után

Miután egy oldal képe ki lett írva, a könyvtár meghívja az `IReleasePageStream`‑et, hogy lehetőséget adjon a kapcsolódó output stream biztonságos lezárására és takarítására. Implementálja ezt a visszahívást a fájl‑handle‑ek zárásához, puffer‑flush‑hoz és esetleges további naplózáshoz. A megfelelő takarítás elkerüli a descriptor‑szivárgásokat és biztosítja, hogy a következő oldalak feldolgozása zavarás nélkül folytatódhasson.

A megfelelő erőforrás‑takarítás megakadályozza a fájl‑handle‑szivárgásokat és megakadályozza, hogy a JVM kifogyjon a descriptor‑okból. Implementálja az `IReleasePageStream`‑et, hogy a streamek lezáródjanak, amint a könyvtár jelzi, hogy az oldal befejeződött.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definition anchor:** `IReleasePageStream` is a callback interface that lets you define custom logic for disposing of page‑specific output resources.

## Hogyan generáljunk dokumentum előnézeteket (convert document to image)

Generáljon előnézeteket a `Watermarker` példány `generatePreview()` metódusának meghívásával, egy `PreviewOptions` objektum átadásával, amely meghatározza a felbontást, a képformátumot és az oldaltartományt. A metódus minden oldalon iterál, az Ön stream‑készítőit használva írja a raster képet, majd felszabadítja a streameket. Ez a folyamat egy sor képfájlt hoz létre, amelyek a dokumentum oldalait képviselik.

A `Watermarker`, a `FeatureCreatePageStream` és a `FeatureReleasePageStream` készen áll, meghívhatja az előnézeti motort. A `generatePreview()` metódus minden oldalon iterál, meghívja az Ön stream‑készítőit, írja a képet, és végül felszabadítja a streameket.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** controls the DPI; 150 DPI is a good balance for web thumbnails.
- **`ImageFormat`** can be PNG, JPEG, BMP, or TIFF depending on your downstream requirements.
- The method processes pages sequentially, so memory consumption stays low even for documents with hundreds of pages.

> **Definition anchor:** `generatePreview()` is the API call that renders each page of the loaded document into an image using the streams you supplied.

## A convert document to image gyakorlati alkalmazásai

A kép előnézetek generálása számos lehetőséget nyit meg:

1. **Document browsers** – Show a grid of PNG thumbnails so users can skim large PDFs without opening them.
2. **Search result snippets** – Attach a preview image to search index entries for richer UI.
3. **Email attachments** – Embed a small preview of attached PDFs in the body of an email.
4. **Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead of full PDFs.
5. **Compliance portals** – Render legally‑required watermarked versions of contracts as images for audit trails.

## Teljesítmény szempontok, amikor java generate thumbnails

Bulk feldolgozás esetén tartsa szem előtt ezeket az optimalizálási tippeket:

- **Stream buffering** – Wrap the `FileOutputStream` in a `BufferedOutputStream` to minimise disk I/O.
- **Parallel batch execution** – Use Java’s `ForkJoinPool` to process multiple documents concurrently; each task should create its own `Watermarker` instance to avoid thread‑safety issues.
- **Limit DPI for thumbnails** – 72–150 DPI is sufficient for most UI scenarios; higher DPI should be reserved for print‑ready previews.
- **Reuse licence objects** – Loading the licence file once per JVM reduces overhead.
- **Monitor memory** – The library keeps only the current page in memory. For extremely large files, consider increasing the JVM heap modestly (e.g., `-Xmx512m`) to accommodate occasional spikes.

## Gyakori buktatók és hogyan kerüljük el őket

| Tünet | Valószínű ok | Javítás |
|-------|--------------|---------|
| `OutOfMemoryError` during preview generation | `ImageFormat.Jpeg` használata 300 DPI‑vel egy 1000‑oldalas PDF‑en | Reduce DPI or switch to PNG with lower colour depth |
| Empty preview files | `FeatureCreatePageStream` returns the same `FileOutputStream` for every page | Ensure a new stream is created per `pageNumber` |
| Preview images are rotated | Source PDF contains rotation metadata that isn’t honoured | Call `previewOptions.setRotatePages(true)` (if available) |
| License warning appears | Licence file not found or path incorrect | Verify `Watermarker.setLicense("path/to/license.file")` runs before any other API calls |

## Gyakran feltett kérdések

**Q: Generálhatok előnézetet jelszóval védett PDF‑ekhez?**  
A: Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf", "password")`.

**Q: Mely képformátumok támogatottak az előnézeti kimenethez?**  
A: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless thumbnails.

**Q: Hány oldalt lehet feldolgozni egyetlen hívásban?**  
A: The library imposes no hard limit; you can preview documents with thousands of pages, limited only by storage space and I/O throughput.

**Q: Szükség van külön licencre minden szerverpéldányhoz?**  
A: A single licence file can be reused across multiple instances as long as the total usage complies with the licence terms.

**Q: Van mód egyetlen kombinált thumbnail (pl. csak az első oldal) generálására?**  
A: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to the first page.

## Következtetés

Most már rendelkezik egy teljes, termelésre kész munkafolyamattal a **convert document to image** és **java generate thumbnails** használatához a GroupDocs.Watermark segítségével. Egyedi oldal‑stream kezelők konfigurálásával alacsony memóriahasználatot tart, a `PreviewOptions` finomhangolásával pedig szabályozhatja a képminőséget és a fájlméretet. Ezek a technikák lehetővé teszik, hogy gyors, magas minőségű előnézeteket ágyazzon be bármely Java‑alapú alkalmazásba – legyen az webportál, asztali kliens vagy felhő‑natív mikroszolgáltatás.

---

**Utoljára frissítve:** 2026-09-26  
**Tesztelve ezzel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs

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

## Kapcsolódó oktatóanyagok

- [Hogyan lehet lekérni a dokumentum információkat a GroupDocs.Watermark for Java segítségével: lépésről lépésre útmutató](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Haladó vízjel funkciók oktatóanyagok a GroupDocs.Watermark Java-hoz](/watermark/java/advanced-features/)
- [Hogyan adjunk hozzá képi vízjelet Java-ban a GroupDocs.Watermark segítségével: lépésről lépésre útmutató](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)