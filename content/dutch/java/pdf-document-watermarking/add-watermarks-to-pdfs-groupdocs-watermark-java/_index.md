---
date: '2026-01-23'
description: Leer hoe u PDF‑bestanden kunt voorzien van tekst‑ en afbeeldingwatermerken
  met GroupDocs.Watermark voor Java – een volledige gids voor PDF‑documentbeveiliging.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Hoe PDF te watermerken met GroupDocs.Watermark voor Java
type: docs
url: /nl/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Hoe PDF Watermerken met GroupDocs.Watermark voor Java

In de digitale wereld van vandaag is **hoe PDF te watermerken** bestanden een veelgestelde vraag voor iedereen die intellectueel eigendom of merkassets moet beschermen. Het toevoegen van watermerken—of het nu tekst of afbeeldingen zijn—helpt je **PDF-documentbeveiliging** af te dwingen en maakt ongeautoriseerde distributie veel moeilijker. In deze tutorial leer je stap‑voor‑stap hoe je **GroupDocs.Watermark for Java** gebruikt om zowel tekst- als afbeeldingwatermerken toe te voegen aan PDF‑documenten.

## Quick Answers
- **Welke bibliotheek voegt watermerken toe aan PDF in Java?** GroupDocs.Watermark for Java.  
- **Kan ik zowel tekst- als afbeeldingwatermerken toevoegen?** Ja, de API ondersteunt beide typen.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een betaalde licentie verwijdert beperkingen.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.  
- **Wordt Maven ondersteund?** Absoluut – voeg gewoon de repository en afhankelijkheid toe.

## Wat is PDF‑watermarking en waarom gebruiken?
Watermarking van een PDF voegt een zichtbaar of onzichtbaar merkteken toe dat eigendom, vertrouwelijkheid of branding identificeert. Het is een lichte maar krachtige manier om kopiëren te ontmoedigen, auteurschap te bewijzen en te voldoen aan bedrijfsbeleid.

## Prerequisites

Voordat je begint, zorg ervoor dat je het volgende hebt:

1. **Java Development Kit (JDK) 8+** geïnstalleerd op je machine.  
2. **GroupDocs.Watermark for Java** (de nieuwste versie).  
3. **Maven** (of de mogelijkheid om handmatig een JAR toe te voegen).

### Environment Setup

#### Maven Configuration
Voeg de GroupDocs-repository en de watermark‑afhankelijkheid toe aan je `pom.xml`:

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

#### Direct Download
Als je liever geen Maven gebruikt, kun je de JAR direct downloaden van [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition
Om te beginnen met een gratis proefversie of een tijdelijke licentie te verkrijgen, bezoek [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Voor productiegebruik koop je een abonnement om alle functies te ontgrendelen.

## Setting Up GroupDocs.Watermark for Java

Importeer de kernklasse die alle watermark‑bewerkingen aanstuurt:

```java
import com.groupdocs.watermark.Watermarker;
```

Deze import geeft je toegang tot de `Watermarker`‑klasse, die het startpunt is voor het toevoegen van watermerken aan elk ondersteund documenttype.

## Step‑by‑Step Implementation

Hieronder splitsen we het proces op in logische secties: het maken van tekst‑watermerken, het maken van afbeelding‑watermerken, en uiteindelijk het toepassen ervan op afbeeldingen binnen een PDF.

### 1. Initialize a Text Watermark

**Waarom een tekst‑watermerk?** Het is lichtgewicht, doorzoekbaar en perfect voor het toevoegen van copyright‑vermeldingen of vertrouwelijkheidsverklaringen.

#### 1.1 Maak de TextWatermark‑instantie
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Stel uitlijning in
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Roteer het watermerk
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Configureer grootte
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Initialize an Image Watermark

**Wanneer een afbeelding‑watermerk gebruiken?** Ideaal voor branding met logo's of voor het toevoegen van complexe visuele patronen.

#### 2.1 Laad het afbeeldingsbestand
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Stel uitlijning in
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Roteer het afbeelding‑watermerk
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Configureer grootte
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Add Watermarks to Images Inside a PDF

Nu zetten we alles samen: open een PDF, vind elke afbeelding, en pas afhankelijk van de grootte het tekst‑ of afbeelding‑watermerk toe.

#### 3.1 Open het PDF‑document
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Haal alle afbeeldingen op
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Pas watermerken conditioneel toe
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 Maak afbeeldingsbronnen vrij
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Sla de gewijzigde PDF op
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Opruimen
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Practical Applications of PDF Watermarking

| Use Case | Hoe watermerken helpt |
|----------|-----------------------|
| **DocumentPad‑scheidingstekens:** Gebruik dubbele backslashes (`\\`) op/macOS-Xmx2g`) om OutOfMemory‑fouten te voorkomen.
- **Licentie‑beperkingen:** De proefversie kan het aantal verwerkte pagina’s beperken; upgrade voor onbeperkt gebruik.
- **Rotatie‑verwarring:** Onthoud dat `setRotateAngle` graden verwacht; negatieve waarden roteren tegen de klok in.

## Frequently Asked Questions

**Q: Kan ik wachtwoord‑beveiligde PDF’s watermerken?**  
A: Ja. Open het document met het wachtwoord via de `Watermarker`‑constructor die een wachtwoord‑string accepteert.

**Q: Ondersteunt de bibliotheek andere formaten zoals DOCX of PPTX?**  
A: Absoluut. GroupDocs.Watermark werkt ook met Word, PowerPoint, Excel en afbeeldingsbestanden.

**Q: Hoe wijzig ik de opacity van een watermerk?**  
A: Gebruik `setOpacity(float opacity)` op het watermerk‑object (waarde tussen 0.0 en 1.0).

**Q: Is het mogelijk om een watermerk alleen op de eerste pagina toe te voegen?**  
A: Haal de paginacollectie op via `watermarker.getPages()` en pas het watermerk toe op de gewenste paginanaam (index).

**Q: Wat als ik een PDF moet watermerken die in een cloud‑bucket staat?**  
A: Laad de PDF in een `InputStream` en geef deze door aan de `Watermarker`‑constructor; schrijf na verwerking de output‑stream terug naar de cloud.

## Conclusion

Je hebt nu een volledige, productie‑klare methode voor **hoe PDF te watermerken** bestanden met GroupDocs.Watermark voor Java. Door tekst‑ en afbeelding‑watermerken te combineren, kun je robuuste **PDF-documentbeveiliging** bereiken die zowel aan branding‑ als compliance‑eisen voldoet. Verken de andere functies van de bibliotheek—zoals het verwijderen van watermerken of batch‑verwerking—to om je document‑workflow verder uit te breiden.

---

**Last Updated:** 2026-01-23  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---