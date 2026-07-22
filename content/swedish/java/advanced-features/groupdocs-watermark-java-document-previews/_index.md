---
date: '2026-02-03'
description: Lär dig hur du förhandsgranskar dokument med GroupDocs.Watermark för
  Java – en snabb guide för Java‑utvecklare som arbetar med dokumentförhandsgranskning.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: Hur man förhandsgranskar dokument med GroupDocs.Watermark för Java
type: docs
url: /sv/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Så förhandsgranskar du dokument med GroupDocs.Watermark i Java

Att skapa **how to preview documents**‑funktionalitet är viktigt. Med du hela dokumentet i minnet. I den här guiden kommer du steg för steg att lära dig hur du installerar biblioteket, hanterar sidströmmar och producerar förhandsgranskningsbilder för varje sida i ett dokument.

## Snabba svar
- **Vilket bibliotek rekommenderas?** GroupDocs.Watermark for Java (v24.11)  
- **Vilket primärt nyckelord riktar den här handledningen in på?** *how to preview documents*  
- ** en full  
 page‑stream‑mallen.  
- **Är koden trådsäker?** Watermarker‑instansen är inte trådsäker; skapa en separat instans per tråd.

## Vad är dokumentförhandsgranskning i Java?
En dokumentförhandsgr. Den låål använda: Genererar sidbilder utan att rendera hela dokumentet.  
- **Stöd för flera format**: Fungerar med PDF‑filer, Office‑dokument, Visio och många andra.  
- **Inbyggd strömhantering**: Tillhandahåller `ICreatePageStream` och `IReleasePageStream`‑gränssnitt för ren resurshantering.  

## Förutsättningar

1. **GroupDocs.Watermark Java v24.11** – den senaste stabila utgåvan.  
2. **JDK 8+** installerat och en IDE som IntelliJ IDEA eller Eclipse.  
3. Grundläggande kunskaper i Java (fil‑I/O, objekt‑orienterad programmering).  

## Så installerar du GroupDocs.Watermark för Java

Lägg till biblioteket i ditt projekt med Maven:

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

Eller ladda ner JAR-filen direkt från den officiella sidan:  
[GroupDocs.Watermark för Java‑utgåvor](https://releases.groupdocs.com/watermark/java/)

### Licensanskaffning

- **Free Trial** – begränsad funktionalitet, utmärkt för testning.  
- **Temporary License** – full funktionalitet för en kort utvärderingsperiod.  
- **Full License** – obegränsad användning och prioriterad support.  

## Implementeringsguide

### Initiera Watermarker

Det första steget är att skapa en `Watermarker`‑instans som pekar på källdokumentet.

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

> **Tips:** Ersätt `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` med den faktiska sökvägen till filen du vill förhandsgranska.

### Skapa sidström för generering av förhandsgranskning

Implementera `ICreatePageStream` för att tala om för biblioteket var och hur varje sidbild ska lagras.

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

*`page%s.png`* är ett **page stream java**‑mönster som automatiskt namnger varje förhandsgranskningsfil (t.ex. `page1.png`, `page2.png`).

### Släppa strömmar på rätt sätt förhindrar minnesläckor.

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

### Generera dokumentförhandsgranskning

Kombinera nu allt och anropa `generatePreview` med **preview options java**.

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

- `createPageStream` hanterar **page stream java**‑skapandet för varje förhandsgranskningsbild.  
- `releasePageStream` säkerställer att resurser frigörs efter att varje sida har skrivits.  

## Praktiska tillämpningar

- **PDF‑visningsappar** – visa miniatyrförhandsgranskningar innan hela filen öppnas.  
- **Content Management Systems** – låt redaktörer snabbt bläddra i dokumentinnehåll.  
- **Cloud Storage Services** – generera miniatyrbilder i farten för alla uppladdade filer.  

## Prestandaöverväganden

- **Minnesanvändning** – Använd strömmgränssnitten dokument i RAM.  
- **I/O‑optimering** – Wrappa `FileOutputStream` med en `BufferedOutputStream` om du bearbetar många sidor.  
- **generering i parallella trå## VanOutOfMemoryError** | Stora dokument laddas helt | Använd strömmgränssnitten (som visas) förida. |
| **FileNotig sökväg för utdatamappen | Verifiera att `YOUR_OUTPUT_DIRECTORY` finns och är skrivbar. |
| **Preview images are blank** | Filformatet stöds inte | Säkerställ att dokumenttypen stöds av GroupDocs.Watermark (t.ex. PDF, DOCX, VDX). |

## Vanliga frågor

**Q: Kan jag generera förhandsgranskningar för lösenordsskyddade dokument?**  
A: Ja. Skicka lösenordet till `Watermarker`‑konstruktörens överlagring som accepterar en lösenordsträng.

**Q: Vilka bildformat stöds för förhandsgranskningar?**  
A: PNG är standard, men du kan ändra filändelsen i `FeatureCreatePageStream` till JPEG, BMP, etc.

**Q: Är det möjligt att begränsa förhandsgranskningen till specifika sidor?**  
A: Använd `PreviewOptions.setPageNumber(int pageNumber)` för att generera en förhandsgranskning av en enskild sida.

**Q GroupDocs.Watermark är plattformsoberoende så länge Java‑runtime finns tillgänglig.

**Q: Hur rens efter batch‑bearbetning?**  
A: Radera degransknfilerna manuellt eller implementera en schemalagd rensningsuppgift.

---

**Senast upp GroupDocs.Watermark Java 24.11  
**Författare:** GroupDocs