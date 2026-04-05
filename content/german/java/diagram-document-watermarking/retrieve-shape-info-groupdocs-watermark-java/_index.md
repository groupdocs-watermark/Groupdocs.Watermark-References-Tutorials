---
date: '2026-02-13'
description: Erfahren Sie, wie Sie Formen extrahieren und Bilder aus Formen mit GroupDocs.Watermark
  für Java extrahieren, um detaillierte Diagramminformationen effizient abzurufen.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Wie man Formen aus Diagrammen mit GroupDocs.Watermark in Java extrahiert
type: docs
url: /de/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Wie man Formen aus Diagrammen mit GroupDocs.Watermark in Java extrahiert

Wenn Sie **wie man Formen extrahiert** aus einem Visio‑ähnlichen Diagramm programmatisch benötigen, bietet die GroupDocs.Watermark‑Bibliothek eine saubere, Java‑erste Möglichkeit, jedes Detail zu erhalten – Abmessungen, Positionen, eingebettete Bilder und sogar den Text in jeder Form. In diesem Tutorial sehen Sie genau **wie man Formen extrahiert**, warum das wichtig ist und Schritt‑für‑Schritt‑Code, den Sie in Ihr Projekt kopieren können.

## Schnelle Antworten
- **Welche Bibliothek übernimmt die Formextraktion?** GroupDocs.Watermark für Java  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher  
- **Kann ich Bilddaten aus einer Form erhalten?** Ja – verwenden Sie `shape.getImage()`  
- **Ist Text in einer Form zugänglich?** Absolut, über `shape.getText()`  
- **Benötige ich eine Lizenz für die Produktion?** Eine gültige GroupDocs.Watermark‑Lizenz ist erforderlich  

## Einführung

Die Verwaltung komplexer Diagramme erfordert häufig den Zugriff auf detaillierte Informationen über deren Komponenten, wie Formen und Bilder. Wenn Sie jemals programmatisch Daten wie Abmessungen, Positionen oder Text, die mit Diagrammformen verbunden sind, mit Java abrufen mussten, ist dieses Tutorial genau das Richtige für Sie. Die Leistungsfähigkeit der GroupDocs.Watermark‑Bibliothek zu nutzen, kann diesen Prozess in einer Java‑Anwendung vereinfachen. In diesem Leitfaden zeigen wir Ihnen, wie man **Formen aus einer Diagrammdatei extrahiert** und zudem, wie man **Bilder aus einer Form extrahiert** und **Text aus einer Form extrahiert**.

## Was ist „wie man Formen extrahiert“?

Formen zu extrahieren bedeutet, die internen Objekte des Diagramms (Seiten, Formen, Bilder, Text) zu lesen, sodass Sie sie analysieren, transformieren oder in anderen Anwendungen wiederverwenden können – ideal für Automatisierung, Berichterstellung oder die Integration mit CAD‑Tools.

## Warum GroupDocs.Watermark für die Formextraktion verwenden?

- **Vollständige Formatunterstützung** – funktioniert mit VSDX, VDX und vielen anderen Diagrammtypen.  
- **Umfangreiches Objektmodell** – bietet direkten Zugriff auf Formgeometrie, Bilder und Text.  
- **Keine externen Abhängigkeiten** – reines Java, einfach in Maven‑Projekten einzubetten.  

## Voraussetzungen

- **GroupDocs.Watermark für Java** (Version 24.11 oder neuer)  
- Java Development Kit (JDK) 8 oder höher  
- Maven für die Abhängigkeitsverwaltung  
- Eine IDE wie IntelliJ IDEA oder Eclipse  

## Einrichtung von GroupDocs.Watermark für Java

Fügen Sie die Bibliothek zu Ihrer Maven `pom.xml` hinzu:

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

Sie können die neuesten Binärdateien auch von [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) herunterladen.

### Schritte zum Erwerb einer Lizenz
- **Kostenlose Testversion:** Laden Sie ein Testpaket herunter, um die API zu evaluieren.  
- **Temporäre Lizenz:** Fordern Sie einen temporären Schlüssel für erweiterte Tests an.  
- **Kauf:** Erwerben Sie eine Voll­lizenz für den Produktionseinsatz.

### Grundlegende Initialisierung und Einrichtung

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Wie man Formen extrahiert – Implementierungs‑Leitfaden

### Laden und Abrufen von Inhalten

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Durch Formen iterieren

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Wie man ein Bild aus einer Form extrahiert

Der Aufruf `shape.getImage()` gibt ein Objekt zurück, das das rohe Bitmap, seine Abmessungen und das Byte‑Array enthält. Verwenden Sie die oben gezeigten Eigenschaften, um das Bild auf der Festplatte zu speichern oder in eine andere Verarbeitungspipeline einzuspeisen.

### Wie man Text aus einer Form extrahiert

Die Methode `shape.getText()` gibt den Klartext zurück, der sich innerhalb der Form befindet. Enthält die Form keinen Text, liefert die Methode `null`. Die Beispiel‑Schleife gibt den Text bereits aus, und Sie können ihn weiter verarbeiten – zum Beispiel, indem Sie einen Index aller Form‑Beschriftungen erstellen.

## Tipps zur Fehlerbehebung
- Überprüfen Sie den Dateipfad und die Leseberechtigungen.  
- Stellen Sie sicher, dass Sie ein unterstütztes Diagrammformat (VSDX, VDX usw.) verwenden.  
- Wenn eine Form ohne erwartete Daten erscheint, prüfen Sie die Release‑Notes der Bibliothek auf format‑spezifische Besonderheiten.

## Praktische Anwendungen

1. **Diagrammanalyse:** Diagramme automatisch auf Konformität prüfen, indem Sie Formgrößen oder fehlende Beschriftungen überprüfen.  
2. **Datenvisualisierung:** Extrahierte Abmessungen in ein Reporting‑Dashboard einspeisen, um die Layout‑Dichte zu visualisieren.  
3. **CAD‑Integration:** Formdaten mit CAD‑APIs kombinieren, um Design‑Spezifikationen über Werkzeuge hinweg zu synchronisieren.  

## Leistungsüberlegungen

- **Ressourcen schließen:** Rufen Sie `watermarker.close()` auf, wenn Sie fertig sind, um native Ressourcen freizugeben.  
- **Speicherverwaltung:** Große Diagramme können viel Heap verbrauchen; überwachen Sie den Speicher und erhöhen Sie `-Xmx` bei Bedarf.  
- **Batch‑Verarbeitung:** Verarbeiten Sie Dateien stapelweise und verwenden Sie nach Möglichkeit eine einzelne `Watermarker`‑Instanz wieder.

## Fazit

Indem Sie diesem Leitfaden gefolgt sind, wissen Sie jetzt, **wie man Formen extrahiert**, wie man **Bilder aus einer Form extrahiert** und wie man **Text aus einer Form extrahiert** mit GroupDocs.Watermark für Java. Diese Techniken öffnen die Tür zu automatisierter Diagrammanalyse, Berichterstellung und Integration mit anderen Engineering‑Systemen. Als nächster Schritt erkunden Sie die vollständige API, indem Sie die [Dokumentation](https://docs.groupdocs.com/watermark/java/) prüfen, und versuchen Sie, die Formextraktion mit benutzerdefinierter Geschäftslogik zu kombinieren.

## FAQ‑Abschnitt

1. **Was ist GroupDocs.Watermark?**  
   - Eine umfassende Java‑Bibliothek, die für das Hinzufügen von Wasserzeichen und das Extrahieren von Informationen aus verschiedenen Dokumentformaten, einschließlich Diagrammen, entwickelt wurde.  

2. **Kann ich diese Bibliothek verwenden, um alle Arten von Diagrammdateien zu verarbeiten?**  
   - Ja, stellen Sie jedoch sicher, dass das Dateiformat unterstützt wird, indem Sie die [API‑Referenz](https://reference.groupdocs.com/watermark/java/) prüfen.  

3. **Wie extrahiere ich Form‑Abmessungen und Positionen aus einem Diagramm mit Java und GroupDocs.Watermark?**  
   - Laden Sie das Diagramm, greifen Sie auf `DiagramContent` zu und iterieren Sie dann über die Formen, um Eigenschaften wie Breite, Höhe, X und Y zu erhalten.  

4. **Kann GroupDocs.Watermark mit Java eingebettete Bilder in Diagrammformen extrahieren?**  
   - Ja, es stellt Methoden bereit, um Bilddaten innerhalb von Formen zuzugreifen, einschließlich Größe und Pixeldaten, was für Analyse oder Modifikation nützlich ist.  

5. **Was sind die Voraussetzungen für das Extrahieren von Diagramm‑Form‑Informationen in Java?**  
   - Java JDK 8+, Maven‑Einrichtung, GroupDocs.Watermark‑Bibliothek (24.11+), und grundlegende Java‑Kenntnisse sind für die Implementierung erforderlich.  

---

**Zuletzt aktualisiert:** 2026-02-13  
**Getestet mit:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs