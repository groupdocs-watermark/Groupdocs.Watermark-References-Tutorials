---
date: '2026-02-05'
description: Erfahren Sie, wie Sie Formen aus Word‑Dokumenten mit GroupDocs.Watermark
  für Java extrahieren, einschließlich des Ladens eines Word‑Dokuments in Java und
  der Manipulation von Formdaten.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Wie man Formen aus Word‑Dokumenten mit GroupDocs.Watermark Java extrahiert
type: docs
url: /de/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Wie man Formen aus Word-Dokumenten mit GroupDocs.Watermark in Java extrahiert

In diesem Tutorial erfahren Sie **wie man Formen** aus Word-Dokumenten mit der GroupDocs.Watermark Java-Bibliothek extrahiert. Egal, ob Sie Diagramme analysieren, eingebettete Bilder herausziehen oder die Berichtserstellung automatisieren müssen, das Extrahieren von Form‑Metadaten gibt Ihnen die Kontrolle, intelligentere Dokument‑Verarbeitungspipelines zu bauen. Wir führen Sie durch die Einrichtung der Bibliothek, das Laden eines Word-Dokuments und das Abrufen detaillierter Form‑Informationen – alles in klaren, schrittweisen Java‑Code.

## Schnelle Antworten
- **Was bedeutet „Formen extrahieren“?** Abrufen von Metadaten (Typ, Größe, Position, Text, Bilder) für jedes Zeichenobjekt in einer Word‑Datei.  
- **Welche Bibliothek übernimmt das?** GroupDocs.Watermark für Java.  
- **Benötige ich eine Lizenz?** Eine Testversion funktioniert für die Entwicklung; eine Vollversion entfernt Nutzungslimits.  
- **Kann ich auch Bilder aus Formen erhalten?** Ja – die API stellt die Bild‑Bytes für Bildformen bereit.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder neuer.

## Was bedeutet „Formen extrahieren“ im Kontext von Word‑Dokumenten?
Formen extrahieren bedeutet, programmgesteuert jedes Zeichen‑Element zuzugreifen – Bilder, WordArt, Auto‑Formen, Diagramme und sogar in Kopf‑ oder Fußzeilen eingebettete Formen. Diese Informationen können für Validierung, Migration oder inhaltsbasierte Analysen verwendet werden.

## Warum GroupDocs.Watermark für Java verwenden?
GroupDocs.Watermark bietet eine hoch‑levelige, speichereffiziente API, die die Komplexität des zugrunde liegenden Office Open XML‑Formats abstrahiert. Sie ermöglicht Ihnen:
- Dokumente schnell laden (`WordProcessingLoadOptions`).  
- Durch Abschnitte und Formen iterieren, ohne sich mit Low‑Level‑XML befassen zu müssen.  
- Bilddaten, Text, Ausrichtung und Drehung in einem einzigen Aufruf abrufen.  
- Nahtlos in bestehende Java‑Dienste oder Micro‑Services integrieren.

## Voraussetzungen
- **Java Development Kit (JDK)** 8 oder höher.  
- **IDE** wie IntelliJ IDEA oder Eclipse.  
- Grundkenntnisse in Java‑I/O.  
- Zugriff auf eine **GroupDocs.Watermark für Java**‑Lizenz oder Testversion.

## Einrichtung von GroupDocs.Watermark für Java
Integrieren Sie die Bibliothek über Maven oder einen Direktdownload.

### Verwendung von Maven
Fügen Sie das Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

### Direkter Download
Alternativ können Sie das neueste JAR von [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) herunterladen.

### Lizenzbeschaffung
Eine kostenlose Testversion reicht für Tests. Für die Produktion sollten Sie eine permanente Lizenz anfordern, um alle Funktionen freizuschalten.

## Implementierungs‑Leitfaden
Wir teilen die Implementierung in zwei klare Schritte auf: **Laden des Word‑Dokuments** und **Extrahieren von Form‑Informationen**.

### Schritt 1: Laden eines Word‑Dokuments (load word document java)
Zuerst konfigurieren Sie die Ladeoptionen und erstellen eine `Watermarker`‑Instanz. Dies bereitet das Dokument für weitere Untersuchungen vor.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Pro‑Tipp:** Halten Sie die `Watermarker`‑Instanz so eng wie möglich im Scope; ein sofortiges Schließen gibt native Ressourcen frei und verhindert Speicherlecks.

### Schritt 2: Form‑Informationen extrahieren (extract images from shapes)
Jetzt holen wir die Details jeder Form, einschließlich eingebetteter Bilder. Der Code iteriert durch jeden Abschnitt und jede Form und gibt nützliche Metadaten aus.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**Was dieser Code macht:**  
- Ruft den **Typ** jeder Form ab (z. B. Bild, WordArt).  
- Gibt **Größe**, **Position** und **Drehung** aus.  
- Zeigt **alternativen Text** und **Name** an, die für Barrierefreiheitsprüfungen nützlich sind.  
- Wenn die Form ein Bild enthält, gibt sie die **Pixelabmessungen** und **Byte‑Größe** des Bildes aus – ideal zum Extrahieren von Bildern aus Formen.

### Häufige Fallstricke & wie man sie behebt
| Problem | Ursache | Lösung |
|---------|---------|--------|
| `FileNotFoundException` | Falscher Dateipfad oder fehlende Berechtigungen | Überprüfen Sie den absoluten/relativen Pfad und stellen Sie sicher, dass die Datei lesbar ist. |
| Null `shape.getImage()` | Form ist kein Bild (z. B. Auto‑Form) | Schützen Sie mit `if (shape.getImage() != null)`, wie gezeigt. |
| Hoher Speicherverbrauch bei großen Dokumenten | Laden des gesamten Dokuments auf einmal | Verarbeiten Sie Abschnitte einzeln oder erhöhen Sie den JVM‑Heap (`-Xmx`). |
| Fehlende Kopf‑/Fußzeilen‑Formen | Keine Prüfung von `shape.getHeaderFooter()` | Das Beispiel protokolliert bereits, wenn eine Form zu einer Kopf‑ oder Fußzeile gehört. |

## Praktische Anwendungen
1. **Automatisierte Berichtserstellung** – Diagramme und Grafiken extrahieren, um sie in nachgelagerten PDFs einzubetten.  
2. **Compliance‑Audit** – Überprüfen, dass alle Formen geeigneten alternativen Text für Barrierefreiheit enthalten.  
3. **Inhaltsmigration** – Eingebettete Bilder aus alten Word‑Dateien in ein Digital‑Asset‑Management‑System exportieren.  

## Leistungsüberlegungen
- **Ressourcen freigeben**: Rufen Sie stets `watermarker.close()` in einem `finally`‑Block auf oder verwenden Sie try‑with‑resources, wenn Sie die API einbetten.  
- **Chunk‑Verarbeitung**: Bei Dokumenten über 50 MB sollten Sie jede Sektion separat verarbeiten, um den Speicherverbrauch gering zu halten.  
- **Thread‑Sicherheit**: `Watermarker`‑Instanzen sind nicht thread‑sicher; erstellen Sie pro Thread eine neue Instanz.

## Fazit
Sie wissen jetzt **wie man Formen** aus Word‑Dokumenten mit GroupDocs.Watermark für Java extrahiert, vom Laden der Datei bis zum Lesen aller Form‑Metadaten und eingebetteter Bilddaten. Diese Fähigkeit eröffnet Möglichkeiten für fortgeschrittene Dokumenten‑Analysen, automatisierte Inhalts‑Pipelines und Barrierefreiheits‑Validierung.

### Nächste Schritte
- Experimentieren Sie mit dem Ändern von Form‑Eigenschaften (z. B. Größe ändern oder neu positionieren).  
- Kombinieren Sie diesen Ansatz mit **GroupDocs.Parser**, um umgebenden Text zu extrahieren.  
- Integrieren Sie die Extraktions‑Logik in einen REST‑Service für On‑Demand‑Verarbeitung.

## FAQ‑Abschnitt
**Q: Was ist GroupDocs.Watermark für Java?**  
A: Es ist eine umfassende Bibliothek, die entwickelt wurde, um Wasserzeichen und Dokumenteninhalte über verschiedene Formate hinweg zu verwalten und Aufgaben wie Form‑Extraktion, Bild‑Abruf und Textmanipulation zu ermöglichen.

**Q: Kann ich Bilder aus Formen ohne Lizenz extrahieren?**  
A: Die Testversion erlaubt das Extrahieren, aber eine Voll‑Lizenz entfernt Nutzungslimits und ermöglicht den kommerziellen Einsatz.

**Q: Funktioniert das mit `.doc` (binären) Dateien?**  
A: Ja, die API unterstützt sowohl `.docx` als auch das alte `.doc`‑Format.

**Q: Wie gehe ich mit passwortgeschützten Dokumenten um?**  
A: Geben Sie das Passwort über `WordProcessingLoadOptions.setPassword("yourPassword")` an, bevor Sie den `Watermarker` erstellen.

**Q: Gibt es eine Möglichkeit, die extrahierten Form‑Daten nach JSON zu exportieren?**  
A: Sie können die ausgegebenen Werte in ein POJO abbilden und jede JSON‑Bibliothek (z. B. Jackson) verwenden, um die Sammlung zu serialisieren.

---
**Zuletzt aktualisiert:** 2026-02-05  
**Getestet mit:** GroupDocs.Watermark 24.11 für Java  
**Autor:** GroupDocs