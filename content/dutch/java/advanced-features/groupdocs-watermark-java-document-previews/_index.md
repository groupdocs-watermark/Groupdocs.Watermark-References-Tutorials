---
date: '2026-02-03'
description: Leer hoe u documenten kunt voorvertonen met GroupDocs.Watermark voor
  Java – een snelle gids voor Java‑ontwikkelaars die documenten willen voorvertonen.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: Hoe documenten te bekijken met GroupDocs.Watermark voor Java
type: docs
url: /nl/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Hoe Documenten Vooraf Bekijken met GroupDocs.Watermark in Java

Het creëren van **how to preview documents** functionaliteit is essentieel voor elke applicatie die grote aantallen bestanden verwerkt. Met GroupDocs.Watermark voor Java kun je snelle, hoogwaardige previews dezeromen beheert en preview‑afbeeldingen maakt voor elke pagina van een document.

## Snelle Antwoorden
- **Welkevhow to preview documents*  
- **Heb ik een licentie nodig?** Een proefversie werkt voor evaluatie; een volledige licentie is vereist voor productie.  
- **Kan ik het uitvoerformaat aanpassen? de page De Watermarker‑instantie is niet thread‑safe; maak een aparte instantie per thread.

## Wat is document preview in Java?
Een documentpreview is een lichtgewicht afbeelding (vaak PNG of JPEG) die een enkele pagina van een bestand weergeeft. Het stelt gebruikers in staat om snel een blik op de inhoud te werpen, waardoor de UX in bestandsbrowsers, CMS‑platforms en cloud‑opslagdienstenatermark gebruiken zonder het volledige document te renderen.  
- **Cross‑format ondersteuning**: Werkt met PDF’s, Office‑bestanden, Visio en vele anderen.  
- **Ingebouwde stream‑afhandeling**: Biedt de `ICreatePageStream` en `IReleasePageStream` interfaces voor nette resource‑beheer.

## Vereisten

Voordat je begint, zorg ervoor dat je het volgende hebt:

1. **GroupDocs.Watermark Java v24.11** – de nieuwste stabiele release.  
2. **JDK 8+** geïnstalleerd en een IDE zoals IntelliJ IDEA of Eclipse.  
3. Basiskennis‑I/O, object‑georiënteerd programmeren).

## GroupDocs.Watermark voor Java Instellen

Voeg de bibliotheek toe aan je project met Maven:

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

Of download de JAR rechtstreeks van de officiële pagina:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### Licentieverwerving

- **Gratis proefversie** – beperkte functionaliteit, ideaal voor testen.  
- **Tijdelijke licentie** – volledige functionaliteit voor een korte evaluatieperiode.  
- **Volledige licentie** – onbeperkt gebruik en prioriteitsondersteuning.

## Implementatieg eerste stap is het aanmaken van een `Watermarker`‑instantie die naar het bron‑document wijst.

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

> **Tip:** Vervang `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` door het daadwerkelijke pad van het bestand dat je wilt previewen.

### Pagina‑Stream Maken voor Preview‑Generer `ICreatePageStream` om de bibliotheek te vertellen waar en hoe elke pagina‑afbeelding moet worden opgeslagen.

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

*`page%s.png`* is een **page stream java** patroon dat automatisch elke preview‑bestand benoemt (bijv. `page1.png`, `page2.png`).

### Pagina‑Stream Vrijgeven

Het correct sluiten van streams voorkomt geheugenlekken.

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

### Documentpreview Genereren

Combineer nu alles en roep `generatePreview` aan met **preview options java**.

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

- `createPage- ` vrijgegeven nadat elke pagina is geschreven.

## Praktische Toepassingen

- **PDF Viewer Apps** – toon miniatuur‑previews voordat het volledige bestand wordt geopend.  
- **Content Management Systems** – laat redacteuren snel door documentinhoud bladeren.  
- **Cloud Storage Services** – genereer on‑the‑fly miniaturen voor elk geüpload bestand.

## Prestatieoverwegingen

- **Geheugengebruik** – Gebruik de stream‑interfaces om te voorkomen dat volledige documenten in RAM worden geladen.  
- **I/O‑optimalisatie** – Wikkel `FileOutputStream` in een `BufferedOutputStream` als je veel pagina's verwerkt.  
- **Batchverwerking** – Voer preview‑generatie uit in parallelle threads, elk met een eigen `Watermarker`‑instantie.

## Veelvoorkomende Problemen & Oplossingen

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **OutOfMemoryError** | Grote documenten volledig geladen | Gebruik de stream‑interfaces (zoals getoond) om pagina‑voor‑pagina te verwerken. |
| **FileNotFoundException** | Onjuiste uitvoermap pad | Controleer of `YOUR_OUTPUT_DIRECTORY` bestaat en beschrijfbaar is. |
| **Preview images are blank** | Niet‑ondersteund bestandsformaat | Zorg ervoor dat het documenttype wordt ondersteund door GroupDocs.Watermark (bijv. PDF, DOCX, VDX). |

## Veelgestelde Vragen

 genereren doorload die Welke afbeeldingsformaten worden ondersteund voor previews?**  
A: PNG kunt de bestandsextensie wijzigen in `FeatureCreatePageStream` naar JPEG, BMP, enz.

**Q: Is het mogelijk om de preview te beperken tot specifieke pagina's?**  
A: Gebruik `PreviewOptions.setPageNumber(int pageNumber)` om een preview van één pagina te genereren.

**Q: Werkt de bibliotheek op Linux/macOS?**  
A: Absoluut. GroupDocs.Watermark is platform‑onafhankelijk zolang de Java‑runtime beschikbaar is.

**Q: Hoe maak ik tijdelijke bestanden op na batchverwerking?**  
A:bestanden handmatig ofaatst bijgewerkt:** 2026-02-03  
**Getest met:** GroupDocs.Watermark Java 24.