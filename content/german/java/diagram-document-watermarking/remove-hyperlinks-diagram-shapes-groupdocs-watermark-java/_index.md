---
date: '2026-04-04'
description: Erfahren Sie, wie Sie Links aus Diagrammformen mit GroupDocs.Watermark
  Java entfernen, um die Dokumentensicherheit und Klarheit zu gewährleisten.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Wie man Links aus Diagrammformen mit GroupDocs.Watermark Java entfernt
type: docs
url: /de/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Wie man Links aus Diagrammformen mit GroupDocs.Watermark Java entfernt

Die Verwaltung digitaler Dokumente beinhaltet häufig das Bearbeiten von Diagrammen, insbesondere wenn Sie **how to strip links** aus Sicherheits- oder Klarheitsgründen benötigen. In diesem Tutorial lernen Sie eine einfache, schritt‑für‑schritt Methode, um unerwünschte Hyperlinks aus Diagrammformen mithilfe der leistungsstarken **GroupDocs.Watermark** Bibliothek für Java zu entfernen. Am Ende haben Sie saubere, link‑freie Diagramme, die sicher zu teilen sind.

## Schnelle Antworten
- **What does “how to strip links” mean?** Es bezieht sich auf das Entfernen von Hyperlink-Objekten, die in Diagrammformen eingebettet sind.  
- **Which library handles this?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **Do I need a license?** Eine kostenlose Testversion funktioniert zum Testen; für die Produktion ist eine gültige Lizenz erforderlich.  
- **Can I process many files at once?** Ja – den Code in einer Schleife oder einem Batch‑Job einbinden.  
- **Is this approach language‑specific?** Das Beispiel ist Java, aber das gleiche Konzept gilt für andere .NET/Java APIs.

## Was bedeutet “how to strip links” bei der Diagrammbearbeitung?
Links zu entfernen bedeutet, Hyperlink‑Objekte zu finden, die an Formen innerhalb eines Diagramms (z. B. Visio *.vsdx) angehängt sind, und sie zu löschen. Dadurch werden externe URLs eliminiert, die sensible Informationen preisgeben oder den Präsentationsfluss unterbrechen könnten.

## Warum GroupDocs.Watermark für Java verwenden?
- **Precision** – Direkter Zugriff auf Form‑Objekte und deren Hyperlink‑Sammlungen.  
- **Performance** – Optimiert für große Diagramme, ohne das gesamte Dokument in den Speicher zu laden.  
- **Cross‑format support** – Funktioniert mit vielen Diagrammformaten (Visio, Draw.io usw.).

## Voraussetzungen
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (oder manuelle JAR‑Einbindung).  
- Java JDK 8 oder neuer.  
- Eine IDE wie IntelliJ IDEA oder Eclipse.

## Einrichtung von GroupDocs.Watermark für Java
### Maven‑Einrichtung
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
Wenn Sie Maven nicht verwenden möchten, holen Sie sich das neueste JAR von der offiziellen Seite:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Schritte zum Lizenzieren
- Starten Sie mit einem kostenlosen Testdownload.  
- Für die Produktion erhalten Sie eine temporäre oder vollständige Lizenz über das GroupDocs‑Portal.

#### Grundlegende Initialisierung und Einrichtung
Erstellen Sie eine `Watermarker`‑Instanz, die auf den Ordner mit Ihrem Diagramm zeigt:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Wie man Links aus Diagrammformen entfernt
Unten finden Sie einen prägnanten, vier‑schrittigen Prozess, der **remove hyperlinks java** in Aktion zeigt.

### Schritt 1: Diagrammdatei laden
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Warum?* Das Laden der Datei gibt Ihnen programmatischen Zugriff auf deren Seiten, Formen und Hyperlink‑Sammlungen.

### Schritt 2: Auf Forminhalt zugreifen
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Warum?* Sie benötigen eine Referenz auf die spezifische Form, die Hyperlinks enthalten könnte.

### Schritt 3: Durchlaufen und Hyperlinks entfernen
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Warum?* Das Durchlaufen in umgekehrter Reihenfolge verhindert Index‑Verschiebungsprobleme beim Löschen von Elementen aus der Sammlung.

### Schritt 4: Speichern und Schließen
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Warum?* Das Speichern schreibt das bereinigte Diagramm auf die Festplatte, und das Schließen gibt Dateihandles frei, um Speicherlecks zu vermeiden.

## Praktische Anwendungsfälle für das Entfernen von Links
1. **Security** – Entfernen Sie externe URLs, die zu Phishing oder Datenlecks führen könnten.  
2. **Compliance** – Stellen Sie sicher, dass Diagramme internen Richtlinien vor der Verteilung entsprechen.  
3. **Presentation Cleanliness** – Entfernen Sie unnötige anklickbare Bereiche, die Betrachter ablenken.

## Leistungsüberlegungen
- **Loop Efficiency** – Verwenden Sie das oben gezeigte Reverse‑Iteration‑Muster.  
- **Resource Management** – Bevorzugen Sie `try‑with‑resources` oder explizite `close()`‑Aufrufe.  
- **Large Files** – Überwachen Sie CPU/Arbeitsspeicher; erwägen Sie die Verarbeitung von Seiten in Batches.

## Häufige Probleme und Lösungen
- **No hyperlinks found** – Überprüfen Sie, ob das Diagramm tatsächlich Hyperlink‑Objekte enthält; einige Formate speichern sie anders.  
- **IndexOutOfBoundsException** – Iterieren Sie immer rückwärts, wenn Sie Elemente aus einer Sammlung entfernen.  
- **License errors** – Stellen Sie sicher, dass Ihre Lizenzdatei korrekt platziert oder an den `Watermarker`‑Konstruktor übergeben wird.

## Häufig gestellte Fragen

**Q: Wie gehe ich mit mehreren Formen auf mehreren Seiten um?**  
A: Durchlaufen Sie `content.getPages()` und dann die `getShapes()`‑Sammlung jeder Seite, wobei Sie die gleiche Entferungslogik auf jede Form anwenden.

**Q: Kann ich Links nach Domain statt nach voller URL filtern?**  
A: Ja – ändern Sie die `contains`‑Prüfung, um nach dem Domain‑String zu suchen (z. B. `"example.com"`).

**Q: Gibt es eine Möglichkeit, zu protokollieren, welche Links entfernt wurden?**  
A: Innerhalb der Schleife erfassen Sie `shape.getHyperlinks().get_Item(i).getAddress()` vor dem Entfernen und schreiben es in eine Log‑Datei.

**Q: Funktioniert das mit PDF‑Diagrammen, die in anderen Dokumenten eingebettet sind?**  
A: GroupDocs.Watermark unterstützt viele Formate; stellen Sie sicher, dass der Dateityp als Diagramm (Visio, VDX usw.) erkannt wird.

**Q: Welche Lizenz ist für die Batch‑Verarbeitung erforderlich?**  
A: Eine vollständige Produktionslizenz ist für alle nicht‑Test‑ und hochvolumigen Vorgänge erforderlich.

## Fazit
Sie haben jetzt eine vollständige, produktionsbereite Methode, um **how to strip links** aus Diagrammformen mit GroupDocs.Watermark für Java zu entfernen. Integrieren Sie dies in Ihre Dokumentverarbeitungspipelines, um Sicherheit, Compliance und visuelle Qualität zu steigern.

### Nächste Schritte
- Erkunden Sie weitere Manipulationsfunktionen wie das Hinzufügen von Wasserzeichen oder das Stempeln von Text.  
- Kombinieren Sie diese Routine mit einem File‑Watcher‑Dienst, um Diagramme beim Hochladen automatisch zu bereinigen.

---

**Zuletzt aktualisiert:** 2026-04-04  
**Getestet mit:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Ressourcen
- [Dokumentation](https://docs.groupdocs.com/watermark/java/)
- [API‑Referenz](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporäre Lizenz erwerben](https://purchase.groupdocs.com/temporary-license/)