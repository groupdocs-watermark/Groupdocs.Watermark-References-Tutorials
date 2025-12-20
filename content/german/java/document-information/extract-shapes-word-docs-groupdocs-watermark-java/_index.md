---
date: '2025-12-20'
description: Erfahren Sie, wie Sie Bilder aus Word‑Dokumenten extrahieren und Formen
  mit GroupDocs.Watermark für Java extrahieren, ideal für die Dokumentenautomatisierung
  und -manipulation.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Wie man Bilder aus Word-Dokumenten mit GroupDocs.Watermark in Java extrahiert
type: docs
url: /de/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# So extrahieren Sie Bilder aus Word-Dokumenten mit GroupDocs.Watermark in Java

In modernen Dokumenten‑Verarbeitungsanwendungen ist das **Bilder aus Word extrahieren**‑Dokumenten ein häufiges Bedürfnis – egal, ob Sie Grafiken wiederverwenden, OCR ausführen oder einfach Inhalte prüfen müssen. Dieses Tutorial zeigt Ihnen Schritt für Schritt, wie Sie ein Word‑Dokument in Java mit GroupDocs.Watermark laden und dann **Bilder aus Word**‑Dateien extrahieren, wobei auch **wie man Shapes extrahiert** demonstriert wird. Am Ende haben Sie ein wiederverwendbares Code‑Snippet, das sich nahtlos in Ihre Automatisierungspipeline einfügt.

## Schnelle Antworten
- **Welche Bibliothek übernimmt die Bildextraktion?** GroupDocs.Watermark for Java  
- **Kann ich sowohl Bilder als auch Vektor‑Shapes extrahieren?** Ja – die API bietet Zugriff auf Bilder und Shape‑Metadaten.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher.  
- **Benötige ich eine Lizenz für die Produktion?** Eine kommerzielle Lizenz wird empfohlen; ein kostenloser Testzeitraum reicht für die Evaluierung.  
- **Ist der Vorgang speichereffizient für große Dateien?** Ja, Sie können Ressourcen zeitnah freigeben und Abschnitte inkrementell verarbeiten.

## Was bedeutet „Bilder aus Word extrahieren“?
Das Extrahieren von Bildern aus Word bedeutet, programmgesteuert jedes Bild, jede Zeichnung oder jede eingebettete Grafik in einer `.docx`‑Datei zu finden und deren Binärdaten oder Metadaten abzurufen. Dies ermöglicht nachgelagerte Aufgaben wie Bildanalyse, Inhaltsmigration oder dynamische Berichtserstellung.

## Warum GroupDocs.Watermark für diese Aufgabe verwenden?
GroupDocs.Watermark bietet eine High‑Level‑API, die die Komplexität des OpenXML‑Formats abstrahiert. Sie ermöglicht es Ihnen, **load word document java**‑Projekte mit nur wenigen Codezeilen zu **laden**, während gleichzeitig detaillierte Shape‑Informationen bereitgestellt werden – perfekt für Entwickler, die sowohl Bildextraktion als auch Shape‑Analyse benötigen.

## Voraussetzungen
- **Java Development Kit (JDK)** 8 oder neuer  
- **IDE** – IntelliJ IDEA, Eclipse oder ein beliebiger Java‑kompatibler Editor  
- Grundkenntnisse in Java‑I/O  
- Zugriff auf eine GroupDocs.Watermark‑Lizenz (Testlizenz funktioniert für Tests)

## Einrichtung von GroupDocs.Watermark für Java
Integrieren Sie die Bibliothek über Maven oder direkten Download.

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
Alternativ laden Sie das neueste JAR von [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) herunter.

### Lizenzbeschaffung
Für die volle Funktionalität erhalten Sie einen Lizenzschlüssel über das GroupDocs‑Portal. Eine temporäre Testlizenz kann angefordert werden, um alle Funktionen uneingeschränkt zu testen.

## Implementierungs‑Leitfaden
Wir teilen die Implementierung in zwei logische Teile:

1. **Wie man ein Word‑Dokument in Java lädt**  
2. **Wie man Shapes und Bilder extrahiert (d.h. Bilder aus Word extrahiert)**

### Laden eines Word‑Dokuments
Zuerst konfigurieren Sie die Ladeoptionen und instanziieren den `Watermarker`.

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

> **Pro‑Tipp:** Ersetzen Sie `"YOUR_DOCUMENT_DIRECTORY/document.docx"` durch einen absoluten oder relativen Pfad, der auf die zu verarbeitende Datei verweist.

### Extrahieren von Shape‑ und Bildinformationen
Jetzt, da das Dokument geladen ist, können Sie durch jeden Abschnitt und jedes Shape iterieren und sowohl Vektor‑Shape‑Daten als auch eingebettete Bilddetails extrahieren.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **Warum das wichtig ist:** Der Aufruf `shape.getImage()` gibt Ihnen direkten Zugriff auf die binäre Darstellung jedes Bildes, sodass Sie es auf die Festplatte speichern, über ein Netzwerk senden oder in eine Bildverarbeitungs‑Bibliothek einspeisen können.

## Häufige Probleme und Lösungen
| Problem | Lösung |
|---------|----------|
| **FileNotFoundException** – falscher Pfad | Überprüfen Sie den Dateipfad und stellen Sie sicher, dass die Anwendung Leseberechtigungen hat. |
| **OutOfMemoryError** bei großen Dokumenten | Verarbeiten Sie Abschnitte einzeln und rufen Sie `watermarker.close()` auf, sobald Sie einen Batch abgeschlossen haben. |
| Shapes geben `null` für `getImage()` zurück | Nicht alle Shapes sind Bilder; einige sind Zeichenobjekte. Prüfen Sie `shape.getShapeType()`, bevor Sie auf das Bild zugreifen. |
| Lizenz nicht angewendet | Fügen Sie `License.setLicense("path/to/license/file.lic");` hinzu, bevor Sie `Watermarker` erstellen. |

## Praktische Anwendungsfälle
- **Automatisierte Berichtserstellung:** Diagramme und Logos aus Vorlagen extrahieren, um sie in Dashboards wiederzuverwenden.  
- **Inhaltsprüfung:** Unternehmensdokumente nach verbotenen Grafiken durchsuchen.  
- **Migrationsprojekte:** Eingebettete Bilder exportieren, bevor Inhalte in ein neues CMS übertragen werden.

## Leistungsüberlegungen
- Die `Watermarker`‑Instanz zeitnah freigeben (`watermarker.close()`).  
- Bei sehr großen Dateien (> 50 MB) sollten Sie das Streamen von Abschnitten in Betracht ziehen, anstatt das gesamte Dokument in den Speicher zu laden.  
- Verwenden Sie die neueste Version von GroupDocs.Watermark für Leistungsverbesserungen.

## Fazit
Sie haben nun einen vollständigen, produktionsbereiten Ansatz, um **Bilder aus Word**‑Dokumenten zu extrahieren und Shape‑Metadaten mit GroupDocs.Watermark für Java abzurufen. Diese Fähigkeit eröffnet leistungsstarke Automatisierungsszenarien, von der Erstellung dynamischer Berichte bis hin zu groß angelegten Dokumentenprüfungen.

### Nächste Schritte
- Experimentieren Sie mit dem Speichern extrahierter Bilder auf die Festplatte (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Erkunden Sie zusätzliche APIs wie das Entfernen oder Hinzufügen von Wasserzeichen.  
- Integrieren Sie diese Logik in Ihren bestehenden Dokumenten‑Management‑Workflow.

## FAQ‑Abschnitt
**Q: Was ist GroupDocs.Watermark für Java?**  
A: Es ist eine umfassende Bibliothek, die entwickelt wurde, um Wasserzeichen zu verwalten und visuelle Elemente aus verschiedenen Dokumentformaten zu extrahieren, wodurch die Automatisierung von Dokumenten‑Manipulationsaufgaben verbessert wird.

**Q: Kann ich Bilder aus passwortgeschützten Word‑Dateien extrahieren?**  
A: Ja. Laden Sie das Dokument mit `WordProcessingLoadOptions`, das das Passwort enthält, und fahren Sie dann mit derselben Extraktionslogik fort.

**Q: Unterstützt die API auch .doc (binäre) Dateien?**  
A: Die Bibliothek richtet sich hauptsächlich an das OpenXML‑Format `.docx`, kann jedoch nach einer Konvertierung auch Legacy‑`.doc`‑Dateien öffnen.

**Q: Wie speichere ich die extrahierten Bilder im Dateisystem?**  
A: Verwenden Sie `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` innerhalb der Schleife, in der `shape.getImage()` nicht null ist.

**Q: Gibt es ein Limit für die Anzahl der zu verarbeitenden Shapes?**  
A: Es gibt kein festes Limit, aber der Speicherverbrauch steigt mit der Dokumentgröße; verarbeiten Sie Abschnitte sequenziell bei sehr großen Dateien.

---

**Zuletzt aktualisiert:** 2025-12-20  
**Getestet mit:** GroupDocs.Watermark 24.11 für Java  
**Autor:** GroupDocs