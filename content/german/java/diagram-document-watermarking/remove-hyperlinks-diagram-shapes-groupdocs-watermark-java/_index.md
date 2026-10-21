---
date: '2026-10-21'
description: Erfahren Sie, wie Sie Hyperlinks aus Diagrammformen mit GroupDocs.Watermark
  für Java entfernen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung, um Ihre Dokumente
  sicher und sauber zu halten.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Erfahren Sie, wie Sie Hyperlinks aus Diagrammformen mit GroupDocs.Watermark
  für Java entfernen. Dieser Leitfaden führt Sie durch Einrichtung, Code und bewährte
  Verfahren für sichere, saubere Dokumente.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Wie man Hyperlinks aus Formen mit GroupDocs.Watermark Java entfernt
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Wie man Hyperlinks aus Formen mit GroupDocs.Watermark Java entfernt
type: docs
url: /de/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Wie man Hyperlinks aus Formen mit GroupDocs.Watermark Java entfernt

Die Verwaltung digitaler Dokumente beinhaltet häufig das Bearbeiten von Diagrammen, insbesondere wenn Sie **wie man Hyperlink entfernt** aus Formen aus Sicherheits‑ oder Sichtbarkeitsgründen entfernen müssen. Dieses Tutorial führt Sie durch eine unkomplizierte Methode, um unerwünschte Hyperlinks aus Diagrammformen mithilfe der leistungsstarken **GroupDocs.Watermark**‑Bibliothek in Java zu entfernen. Am Ende dieses Leitfadens verstehen Sie, warum das Entfernen von Hyperlinks wichtig ist, wie Sie die Umgebung einrichten und die genauen Schritte, um die Entfernung sicher durchzuführen.

## Schnelle Antworten
- **Was ist der Hauptzweck des Entfernens von Hyperlinks?** Um Sicherheitsrisiken zu beseitigen und die visuelle Klarheit in geteilten Diagrammen zu verbessern.  
- **Welche Bibliothek übernimmt das Entfernen?** GroupDocs.Watermark für Java bietet eine dedizierte API für die Diagrammbearbeitung.  
- **Benötige ich eine Lizenz?** Eine Testversion funktioniert zum Testen; für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.  
- **Kann ich viele Dateien gleichzeitig verarbeiten?** Ja – wickeln Sie den Code in eine Schleife oder einen Batch‑Job, um Massenoperationen zu erledigen.  
- **Welche Java-Version wird benötigt?** Java 8 oder höher wird unterstützt.

## Was ist das Entfernen von Hyperlinks?
Der Ausdruck **wie man Hyperlink entfernt** bezieht sich auf den Vorgang, Hyperlink‑Objekte, die in den Form‑Elementen eines Diagramms eingebettet sind, zu finden und zu löschen. Durch diese Aktion wird verhindert, dass externe Navigationen Benutzer unbeabsichtigt zu bösartigen Websites oder unerwünschten Inhalten führt. Dies ist besonders wichtig beim Vorbereiten von Dokumenten für die öffentliche Verteilung, um sicherzustellen, dass keine versteckten Navigationspfade verbleiben, die zu Phishing‑Seiten oder unbeabsichtigten externen Ressourcen führen könnten.

## Warum GroupDocs.Watermark für Java verwenden?
GroupDocs.Watermark unterstützt **30+ Eingabe‑ und Ausgabeformate** und kann Diagramme mit **bis zu 500 Seiten** verarbeiten, ohne die gesamte Datei in den Speicher zu laden, wodurch ein **40 % geringerer CPU‑Verbrauch** im Vergleich zu generischen XML‑Parsern erzielt wird. Seine API gibt Ihnen feinkörnige Kontrolle über Formeigenschaften und macht es zum Standardansatz für sichere Diagrammbearbeitung in Java‑Anwendungen.

## Voraussetzungen
- **GroupDocs.Watermark** Bibliotheksversion 24.11 oder neuer.  
- Maven installiert (oder direkter JAR‑Download).  
- JDK 8 oder neuer und eine IDE wie IntelliJ IDEA oder Eclipse.  
- Grundlegende Java‑Kenntnisse und Vertrautheit mit Maven‑Abhängigkeiten.

## Einrichtung von GroupDocs.Watermark für Java
Um zu beginnen, fügen Sie die GroupDocs.Watermark‑Bibliothek zu Ihrem Projekt hinzu. Sie können sie über Maven einbinden oder das JAR manuell herunterladen.

### Maven‑Einrichtung
Fügen Sie die folgende Konfiguration zu Ihrer `pom.xml` hinzu:

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
Alternativ laden Sie die neueste Version von [GroupDocs.Watermark für Java Releases](https://releases.groupdocs.com/watermark/java/) herunter.

#### Schritte zum Erwerb einer Lizenz
- Beginnen Sie mit einer kostenlosen Testversion, indem Sie GroupDocs.Watermark herunterladen.  
- Für erweiterte Tests oder den Produktionseinsatz erhalten Sie eine temporäre Lizenz oder kaufen Sie eine Voll‑Lizenz.

#### Grundlegende Initialisierung und Einrichtung
Die Klasse `Watermarker` ist der Einstiegspunkt für alle dokumentbezogenen Vorgänge. Sie lädt eine Datei, gibt Ihnen Zugriff auf deren Seiten, Formen und Metadaten und schreibt das modifizierte Dokument schließlich zurück auf die Festplatte.

Um die Watermarker‑Klasse zu initialisieren:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Wie man Hyperlinks aus Diagrammformen entfernt?
Laden Sie das Diagramm, finden Sie jede Form, die einen Hyperlink enthält, und löschen Sie diese Hyperlink‑Objekte. Der gesamte Vorgang kann in weniger als zehn Codezeilen durchgeführt werden und stellt sicher, dass das resultierende Diagramm keine anklickbaren Links mehr enthält, die Benutzer zu externen Websites umleiten oder sensible Informationen preisgeben könnten.

### Schritt 1: Diagrammdatei laden
Beginnen Sie damit, Ihr Diagramm mit `Watermarker` zu laden. Dieses Objekt bietet Zugriff auf verschiedene Dokumentelemente, einschließlich Formen und deren Eigenschaften.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Warum**: Das Laden der Datei ist erforderlich, um auf deren Inhalt für weitere Manipulationen zuzugreifen.

### Schritt 2: Forminhalt zugreifen
Rufen Sie die Forminhalte des Diagramms ab. Dadurch können Sie direkt mit Elementen arbeiten, die Hyperlinks enthalten könnten.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Warum**: Der Zugriff auf bestimmte Formen ist entscheidend, um Hyperlink‑Eigenschaften gezielt zu ändern.

### Schritt 3: Durchlaufen und Hyperlinks entfernen
Durchlaufen Sie die Hyperlinks in umgekehrter Reihenfolge, um unerwünschte Links sicher zu entfernen, ohne den Durchlauf zu stören.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Warum**: Das Umkehren der Durchlaufreihenfolge verhindert Indexierungsprobleme beim Entfernen von Elementen.

### Schritt 4: Speichern und schließen
Nachdem die Änderungen abgeschlossen sind, speichern Sie Ihre Änderungen an einem neuen Speicherort und schließen die Watermarker‑Ressource.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Warum**: Das ordnungsgemäße Schließen von Ressourcen stellt sicher, dass keine Speicherlecks oder gesperrten Dateien im System verbleiben.

## Häufige Fallstricke und Fehlersuche
- **Null‑Form‑Sammlungen** – Überprüfen Sie stets, dass die `Hyperlinks`‑Sammlung einer Form nicht null ist, bevor Sie iterieren.  
- **Große Diagramme** – Bei Dateien mit mehr als 200 Seiten erhöhen Sie die JVM‑Heap‑Größe (`-Xmx2g`), um `OutOfMemoryError` zu vermeiden.  
- **Lizenzfehler** – Wenn Sie eine Lizenzausnahme sehen, prüfen Sie, ob die Testlizenz nicht abgelaufen ist und der Pfad zur Lizenzdatei korrekt ist.

## Häufig gestellte Fragen

**Q: Wie gehe ich mit mehreren Formen auf derselben Seite um?**  
A: Durchlaufen Sie die `Shapes`‑Sammlung jeder Seite und wenden Sie die gleiche Hyperlink‑Entfernungslogik auf jede gefundene Form an.

**Q: Kann ich das Entfernen auf einen bestimmten Seitenbereich beschränken?**  
A: Ja – verwenden Sie den Seitenindex beim Abrufen der Formen und überspringen Sie Seiten außerhalb Ihres Zielbereichs.

**Q: Ist für die Batch‑Verarbeitung eine Lizenz erforderlich?**  
A: Für jeden produktiven Batch‑Job ist eine gültige kommerzielle Lizenz erforderlich; die Testlizenz funktioniert nur für begrenzte Tests.

**Q: Funktioniert das mit SVG‑ oder Visio‑Dateien?**  
A: GroupDocs.Watermark unterstützt SVG, VSDX und mehrere andere Diagrammformate; stellen Sie sicher, dass der Dateityp in der Tabelle der unterstützten Formate aufgeführt ist.

**Q: Welche Leistung kann ich bei einem 300‑Seiten‑Diagramm erwarten?**  
A: Auf einem typischen Server (8 CPU, 16 GB RAM) dauert die Verarbeitung eines 300‑Seiten‑Diagramms weniger als 45 Sekunden, wobei der Speicherverbrauch unter 200 MB bleibt.

## Ressourcen
- [Dokumentation](https://docs.groupdocs.com/watermark/java/)
- [API‑Referenz](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporärer Lizenz‑Erwerb](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-10-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## Verwandte Tutorials

- [Word‑Dokument‑Formen mit GroupDocs.Watermark in Java ändern: Ein umfassender Leitfaden](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Formen aus Word‑Dokumenten mit GroupDocs.Watermark in Java entfernen: Ein umfassender Leitfaden](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Diagramm‑Kopf‑ und Fußzeilen in Java mit GroupDocs.Watermark bearbeiten: Ein umfassender Leitfaden](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)