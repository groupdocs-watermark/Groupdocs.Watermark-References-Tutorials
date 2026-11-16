---
date: '2026-09-26'
description: Erfahren Sie, wie Sie ein Dokument in ein Bild konvertieren und mit Java
  Miniaturansichten mithilfe von GroupDocs.Watermark erstellen. Die Schritt‑für‑Schritt‑Anleitung
  behandelt die Einrichtung, Vorschau‑Streams und Performance‑Tipps.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Erfahren Sie, wie Sie ein Dokument in ein Bild konvertieren und mit
  Java Miniaturansichten mithilfe von GroupDocs.Watermark erstellen. Diese Anleitung
  führt Sie durch Installation, Stream‑Verarbeitung und Optimierung der Performance
  für die schnelle Erstellung von Vorschauen.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Dokument in Bild konvertieren mit GroupDocs.Watermark Java
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
title: Dokument in Bild konvertieren mit GroupDocs.Watermark Java
type: docs
url: /de/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Dokument in Bild konvertieren mit GroupDocs.Watermark Java

Leichte Bildvorschauen von mehrseitigen Dokumenten zu erzeugen ist eine gängige Anforderung für Portale, Content‑Management‑Systeme und Cloud‑Speicherdienste. Durch **convert document to image** geben Sie End‑Benutzern einen schnellen visuellen Hinweis, ohne die gesamte Datei laden zu müssen. Die GroupDocs.Watermark Java‑Bibliothek fügt nicht nur Wasserzeichen hinzu, sondern bietet auch eine Hochleistungs‑Vorschau‑Engine, die **java generate thumbnails** für jede Seite in einem Durchlauf erzeugen kann.

In diesem Tutorial lernen Sie, wie Sie die Bibliothek einrichten, benutzerdefinierte Seiten‑Streams erstellen, Ressourcen sicher freigeben und schließlich Bildvorschauen für jede Seite eines Quelldokuments erzeugen. Die Anweisungen richten sich an Entwickler, die mit Java und objektorientierten Konzepten vertraut sind, und enthalten Best‑Practice‑Tipps für die Verarbeitung großer Dateibatches.

## Schnelle Antworten
- **What is the first step?** Fügen Sie die GroupDocs.Watermark Maven‑Abhängigkeit hinzu und initialisieren Sie einen `Watermarker` mit dem Pfad zur Quelldatei.  
- **How are preview images created?** Implementieren Sie `ICreatePageStream`, um für jede Seite einen Ausgabestream zu öffnen, und rufen Sie dann `generatePreview()` mit den entsprechenden Optionen auf.  
- **Do I need a license?** Eine Testversion funktioniert für grundlegende Szenarien, aber eine Voll‑Lizenz entfernt Wasserzeichen und schaltet die Stapelverarbeitung frei.  
- **Can I process PDFs larger than 200 pages?** Ja – die Bibliothek streamt Seiten, sodass der Speicherverbrauch selbst bei 500‑seitigen Dateien gering bleibt.  
- **What image formats are supported?** PNG, JPEG, BMP und TIFF stehen sofort zur Verfügung.

## Was ist convert document to image?
Der Ausdruck **convert document to image** beschreibt den Vorgang, jede Seite einer Quelldatei (PDF, DOCX, PPTX usw.) in ein Rasterbild wie PNG oder JPEG zu rendern. Diese Konvertierung ist nützlich für Thumbnail‑Galerien, Vorschaufenster und mobil‑freundliche Dokumenten‑Viewer.

## Warum GroupDocs.Watermark für die Vorschauerstellung verwenden?
GroupDocs.Watermark unterstützt **30+ Eingabeformate** und kann Vorschauen für Dokumente bis zu **500 Seiten** erzeugen, ohne die gesamte Datei in den Speicher zu laden. Intern werden Seiten sequenziell verarbeitet, wodurch die Java‑Heap‑Nutzung selbst bei großen PDFs unter 50 MB bleibt. Die Bibliothek bietet zudem integrierte Bildoptimierung, sodass Sie DPI, Farbtiefe und Kompressionsgrad festlegen können, was zu Thumbnails führt, die typischerweise **70 % kleiner** sind als naive Rasterisierung.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- **Java Development Kit (JDK) 11 oder neuer** – die Bibliothek ist für Java 8+ kompiliert, aber JDK 11 bietet langfristigen Support und bessere Performance.  
- **Maven 3.6+** – für das Abhängigkeitsmanagement.  
- **GroupDocs.Watermark für Java Version 24.11** – die neueste stabile Veröffentlichung zum Zeitpunkt des Schreibens.  
- **Grundkenntnisse von Java I/O‑Streams** – Sie werden `FileOutputStream`‑Objekte für jede Vorschauseite erstellen.  
- **Ein Lizenzschlüssel** (optional für die Produktion) – die Testversion begrenzt die Vorschaugröße auf 5 MB pro Dokument.

## So richten Sie GroupDocs.Watermark für Java ein

Um GroupDocs.Watermark einzurichten, fügen Sie zuerst das Maven‑Repository hinzu und binden dann die Bibliothek als Abhängigkeit in Ihrer `pom.xml` ein. So kann Maven die richtigen Artefakte herunterladen und die Klassen stehen im Klassenpfad für Kompilierung und Laufzeit zur Verfügung.

### Maven‑Abhängigkeit hinzufügen
Die Bibliothek wird über Maven Central verteilt. Fügen Sie das folgende Snippet in Ihre `pom.xml` innerhalb des `<dependencies>`‑Blocks ein:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Pro tip:** Bewahren Sie die Versionsnummer in einer Property (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) auf, damit Sie einfach upgraden können.

### Direkter Download (Alternative)
Falls Sie die manuelle Installation bevorzugen, können Sie das JAR von der offiziellen Release‑Seite herunterladen: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Lizenz erwerben und anwenden

Das Anwenden einer Lizenz auf GroupDocs.Watermark entfernt die Einschränkungen der Testversion und deaktiviert das standardmäßige Wasserzeichen‑Overlay. Platzieren Sie die Lizenzdatei an einem bekannten Ort und verweisen Sie die API darauf, oder betten Sie den Lizenzpfad direkt im Code ein, bevor andere Aufrufe erfolgen. Sobald geladen, laufen alle nachfolgenden Vorgänge im Voll‑Feature‑Modus.

Sie können:

- **Eine kostenlose Testversion anfordern** über das GroupDocs‑Portal – sie liefert eine 30‑tägige Lizenzdatei.  
- **Eine temporäre Lizenz** über den Online‑Lizenzgenerator für Evaluierungsumgebungen erzeugen.  
- **Eine kommerzielle Lizenz** für unbegrenzte Produktion und Prioritäts‑Support erwerben.

Platzieren Sie die Lizenzdatei (`GroupDocs.Watermark.lic`) im Stammverzeichnis Ihres Projekts oder geben Sie den Pfad programmgesteuert mit `Watermarker.setLicense("path/to/license.file")` an.

## Watermarker initialisieren

Initialisieren Sie den `Watermarker`, indem Sie den Pfad zum Quelldokument angeben, optional mit einem Passwort für geschützte Dateien. Der Konstruktor prüft das Format und bereitet interne Parser vor, sodass Sie sofort Vorschau‑ oder Wasserzeichen‑Methoden aufrufen können. Nach der Erstellung behalten Sie eine Referenz, um die Instanz bei Bedarf für mehrere Vorgänge wiederzuverwenden.

Die Klasse `Watermarker` ist das Kernobjekt von GroupDocs.Watermark, das ein Dokument lädt und Vorgänge wie das Einfügen von Wasserzeichen und das Erzeugen von Vorschauen bereitstellt.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – absoluter oder relativer Pfad zur Quelldatei.  
- Der Konstruktor prüft das Dateiformat und bereitet interne Parser vor.

> **Definition anchor:** `Watermarker` ist der Einstiegspunkt für alle Dokument‑Verarbeitungs‑Aktionen in GroupDocs.Watermark für Java.

## Seiten‑Streams für die Vorschauerstellung erstellen

Erstellen Sie benutzerdefinierte Seiten‑Streams, indem Sie das Interface `ICreatePageStream` implementieren, das die Bibliothek für jede zu rendernde Seite aufruft. Ihre Implementierung sollte einen frischen `OutputStream` erzeugen – typischerweise einen `FileOutputStream` – der auf eine eindeutig benannte Datei basierend auf der Seitennummer zeigt. Dieser Ansatz isoliert die Ausgabe jeder Seite und verhindert Datenüberschneidungen.

Um **java generate thumbnails** zu erzeugen, müssen Sie für jede Seite einen Stream bereitstellen, in den das gerenderte Bild geschrieben wird. Implementieren Sie das Interface `ICreatePageStream`; die Bibliothek ruft Ihre Implementierung für jede zu verarbeitende Seite auf.
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

- **`fileNameTemplate`** ermöglicht es, die Seitennummer direkt in den Dateinamen einzubetten, was die Stapelverarbeitung vereinfacht.  
- Die Methode liefert für jede Seite einen frischen `OutputStream` zurück, sodass vorherige Seiten die nachfolgenden Schreibvorgänge nicht beeinträchtigen.

> **Definition anchor:** `ICreatePageStream` ist ein Callback‑Interface, das Ihnen erlaubt zu definieren, wie Ausgabestreams für jede Vorschauseite erstellt werden.

## Seiten‑Streams nach der Vorschauerstellung freigeben

Nachdem ein Seitenbild geschrieben wurde, ruft die Bibliothek `IReleasePageStream` auf, um Ihnen das Schließen und Aufräumen des zugehörigen Ausgabestreams zu ermöglichen. Implementieren Sie diesen Callback, um Dateihandles sicher zu schließen, Puffer zu flushen und ggf. zusätzliche Protokollierung vorzunehmen. Eine ordnungsgemäße Bereinigung verhindert Descriptor‑Leaks und stellt sicher, dass nachfolgende Seiten ohne Interferenzen verarbeitet werden können.

Eine ordnungsgemäße Ressourcen‑Bereinigung verhindert Dateihandle‑Leaks und hält die JVM davon ab, Deskriptoren zu erschöpfen. Implementieren Sie `IReleasePageStream`, um Streams zu schließen, sobald die Bibliothek signalisiert, dass eine Seite fertig ist.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definition anchor:** `IReleasePageStream` ist ein Callback‑Interface, das Ihnen erlaubt, benutzerdefinierte Logik zum Freigeben von seiten‑spezifischen Ausgaberesourcen zu definieren.

## Dokumentvorschauen erzeugen (convert document to image)

Erzeugen Sie Vorschauen, indem Sie `generatePreview()` auf der `Watermarker`‑Instanz aufrufen und ein `PreviewOptions`‑Objekt übergeben, das Auflösung, Bildformat und Seitenbereich definiert. Die Methode iteriert über jede Seite, verwendet Ihre Stream‑Erzeuger, um das Rasterbild zu schreiben, und gibt anschließend die Streams frei. Dieser Vorgang erzeugt eine Menge Bilddateien, die die Dokumentseiten repräsentieren.

Mit dem `Watermarker`, `FeatureCreatePageStream` und `FeatureReleasePageStream` bereit, können Sie die Vorschau‑Engine aufrufen. Die Methode `generatePreview()` iteriert über jede Seite, ruft Ihre Stream‑Erzeuger auf, schreibt das Bild und gibt schließlich die Streams frei.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** steuert die DPI; 150 DPI ist ein guter Kompromiss für Web‑Thumbnails.  
- **`ImageFormat`** kann PNG, JPEG, BMP oder TIFF sein, je nach Ihren nachgelagerten Anforderungen.  
- Die Methode verarbeitet Seiten sequenziell, sodass der Speicherverbrauch selbst bei Dokumenten mit Hunderten von Seiten niedrig bleibt.

> **Definition anchor:** `generatePreview()` ist der API‑Aufruf, der jede Seite des geladenen Dokuments in ein Bild rendert, wobei die von Ihnen bereitgestellten Streams verwendet werden.

## Praktische Anwendungen von convert document to image

Die Erzeugung von Bildvorschauen eröffnet zahlreiche Möglichkeiten:

1. **Document browsers** – Zeigen Sie ein Raster aus PNG‑Thumbnails, sodass Benutzer große PDFs überfliegen können, ohne sie zu öffnen.  
2. **Search result snippets** – Hängen Sie ein Vorschau‑Bild an Suchindex‑Einträge für eine reichhaltigere UI an.  
3. **Email attachments** – Betten Sie eine kleine Vorschau angehängter PDFs in den E‑Mail‑Body ein.  
4. **Mobile apps** – Reduzieren Sie die Bandbreite, indem Sie 200 KB PNG‑Vorschauen anstelle vollständiger PDFs senden.  
5. **Compliance portals** – Rendern Sie gesetzlich vorgeschriebene, wasserzeichen‑versehene Versionen von Verträgen als Bilder für Audit‑Trails.

## Leistungsüberlegungen beim java generate thumbnails

Wenn Sie mit Massenverarbeitung zu tun haben, beachten Sie diese Optimierungstipps:

- **Stream buffering** – Wickeln Sie den `FileOutputStream` in einen `BufferedOutputStream`, um die Festplatten‑I/O zu minimieren.  
- **Parallel batch execution** – Nutzen Sie Java‑s `ForkJoinPool`, um mehrere Dokumente gleichzeitig zu verarbeiten; jede Aufgabe sollte ihre eigene `Watermarker`‑Instanz erstellen, um Thread‑Safety‑Probleme zu vermeiden.  
- **Limit DPI for thumbnails** – 72–150 DPI reichen für die meisten UI‑Szenarien aus; höhere DPI sollten nur für druckfertige Vorschauen verwendet werden.  
- **Reuse licence objects** – Das Laden der Lizenzdatei einmal pro JVM reduziert den Overhead.  
- **Monitor memory** – Die Bibliothek hält nur die aktuelle Seite im Speicher. Bei extrem großen Dateien sollten Sie den JVM‑Heap moderat erhöhen (z. B. `-Xmx512m`), um gelegentliche Spitzen abzufangen.

## Häufige Fallstricke und wie man sie vermeidet

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| `OutOfMemoryError` während der Vorschauerstellung | Verwendung von `ImageFormat.Jpeg` mit 300 DPI bei einem 1000‑seitigen PDF | DPI reduzieren oder zu PNG mit geringerer Farbtiefe wechseln |
| Leere Vorschaugdateien | `FeatureCreatePageStream` gibt denselben `FileOutputStream` für jede Seite zurück | Sicherstellen, dass für jede `pageNumber` ein neuer Stream erstellt wird |
| Vorschau‑Bilder sind gedreht | Quell‑PDF enthält Rotations‑Metadaten, die nicht berücksichtigt werden | `previewOptions.setRotatePages(true)` aufrufen (falls verfügbar) |
| Lizenzwarnung erscheint | Lizenzdatei nicht gefunden oder Pfad ist falsch | Vergewissern Sie sich, dass `Watermarker.setLicense("path/to/license.file")` vor allen anderen API‑Aufrufen ausgeführt wird |

## Häufig gestellte Fragen

**Q: Kann ich Vorschauen für passwortgeschützte PDFs erzeugen?**  
A: Ja. Übergeben Sie das Passwort dem `Watermarker`‑Konstruktor: `new Watermarker("file.pdf", "password")`.

**Q: Welche Bildformate werden für die Vorschauausgabe unterstützt?**  
A: PNG, JPEG, BMP und TIFF stehen zur Verfügung. PNG wird für verlustfreie Thumbnails empfohlen.

**Q: Wie viele Seiten können in einem einzigen Aufruf verarbeitet werden?**  
A: Die Bibliothek setzt kein hartes Limit; Sie können Dokumente mit Tausenden von Seiten vorschauen, begrenzt nur durch Speicherplatz und I/O‑Durchsatz.

**Q: Benötige ich für jede Server‑Instanz eine separate Lizenz?**  
A: Eine einzelne Lizenzdatei kann über mehrere Instanzen hinweg wiederverwendet werden, solange die Gesamtnutzung den Lizenzbedingungen entspricht.

**Q: Gibt es eine Möglichkeit, ein einzelnes kombiniertes Thumbnail zu erzeugen (z. B. nur die erste Seite)?**  
A: Ja. Setzen Sie `previewOptions.setPages(new int[]{1})`, um die Erzeugung auf die erste Seite zu beschränken.

## Fazit

Sie verfügen nun über einen vollständigen, produktions‑reifen Workflow für **convert document to image** und **java generate thumbnails** mit GroupDocs.Watermark. Durch die Konfiguration benutzerdefinierter Seiten‑Stream‑Handler halten Sie den Speicherverbrauch niedrig, und durch das Anpassen von `PreviewOptions` steuern Sie Bildqualität und Dateigröße. Diese Techniken ermöglichen das Einbetten schneller, hochwertiger Vorschauen in jede Java‑basierte Anwendung – sei es ein Web‑Portal, ein Desktop‑Client oder ein cloud‑native Microservice.

**Last Updated:** 2026-09-26  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

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

## Verwandte Tutorials

- [Wie man Dokumentinformationen mit GroupDocs.Watermark für Java abruft: Eine Schritt‑für‑Schritt‑Anleitung](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Erweiterte Watermarking‑Features Tutorials für GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Wie man ein Bildwasserzeichen in Java mit GroupDocs.Watermark hinzufügt: Eine Schritt‑für‑Schritt‑Anleitung](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)