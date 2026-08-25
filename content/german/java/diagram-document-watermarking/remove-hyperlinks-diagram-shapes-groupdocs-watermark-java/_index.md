---
date: '2026-08-25'
description: Erfahren Sie, wie Sie Diagrammdateien bearbeiten und Hyperlinks mit GroupDocs.Watermark
  for Java entfernen. Sichern Sie Ihre Diagramme schnell mit einer Schritt‑für‑Schritt‑Anleitung.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Erfahren Sie, wie Sie Diagrammdateien bearbeiten und Hyperlinks mit
  GroupDocs.Watermark for Java entfernen. Befolgen Sie klare Schritte, um Ihre Dokumente
  zu schützen.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Wie man Diagramme bearbeitet und Hyperlinks mit Java entfernt
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Wie man Diagramme bearbeitet und Hyperlinks mit Java entfernt
type: docs
url: /de/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Wie man Diagramme bearbeitet und Hyperlinks mit Java entfernt  

Die Verwaltung digitaler Dokumente beinhaltet häufig das Bearbeiten von Diagrammen, insbesondere wenn Sie **edit diagram**-Dateien von Hyperlinks befreien müssen, um Sicherheit oder visuelle Klarheit zu gewährleisten. Dieses Tutorial zeigt Ihnen genau, wie Sie Diagrammdateien bearbeiten und unerwünschte Hyperlinks aus Diagrammformen mithilfe der leistungsstarken **GroupDocs.Watermark**-Bibliothek für Java entfernen. Am Ende dieses Leitfadens haben Sie ein sauberes, link‑freies Diagramm, das bereit für die Verteilung ist.  

## Schnelle Antworten  
- **Was ist das Hauptziel?** Entfernen Sie alle Hyperlinks aus Diagrammformen, um Sicherheit und Präsentation zu verbessern.  
- **Welche Bibliothek wird benötigt?** GroupDocs.Watermark für Java, Version 24.11 oder neuer.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion funktioniert für Tests; für die Produktion ist eine kommerzielle Lizenz erforderlich.  
- **Kann ich viele Dateien gleichzeitig verarbeiten?** Ja – derselbe Code kann in einer Schleife platziert werden, um Stapel zu verarbeiten.  
- **Welche Java-Version wird unterstützt?** Java 8 oder höher (Java 11 empfohlen).  

## Was bedeutet „how to edit diagram“?  
**How to edit diagram** bezieht sich auf den Prozess, eine Diagrammdatei programmgesteuert zu öffnen, ihre internen Elemente (wie Formen, Text oder Hyperlinks) zu ändern und das Ergebnis zu speichern. Mit GroupDocs.Watermark können Sie Diagrammdateien bearbeiten, ohne das ursprüngliche Autorentool zu benötigen.  

## Warum GroupDocs.Watermark für Java verwenden?  
GroupDocs.Watermark unterstützt **30+ Diagramm- und Bildformate** (einschließlich VSDX, SVG und WMF) und kann Dateien bis zu **500 MB** verarbeiten, ohne das gesamte Dokument in den Speicher zu laden, und liefert eine **20 % schnellere** Verarbeitungsgeschwindigkeit im Vergleich zu vielen Wettbewerbern.  

## Voraussetzungen  
- **GroupDocs.Watermark**-Bibliothek Version 24.11 oder neuer.  
- Maven installiert (oder die JAR-Dateien, wenn Sie eine manuelle Einrichtung bevorzugen).  
- Java Development Kit 8 oder neuer und eine IDE wie IntelliJ IDEA oder Eclipse.  

### Erforderliche Bibliotheken, Versionen und Abhängigkeiten  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (wenn Sie den Maven-Ansatz verwenden)  

### Anforderungen an die Umgebungseinrichtung  
Stellen Sie sicher, dass das JDK‑`bin`‑Verzeichnis in Ihrem `PATH` enthalten ist und dass Ihre IDE auf die korrekte JDK‑Version verweist.  

### Wissensvoraussetzungen  
Sie sollten mit grundlegender Java‑Syntax, Maven‑Abhängigkeitsverwaltung und Datei‑I/O‑Operationen vertraut sein.  

## Wie richtet man GroupDocs.Watermark für Java ein?  
Die Klasse `Watermarker` stellt den API‑Einstiegspunkt zum Laden und Ändern von Dokumenten bereit.  
Um GroupDocs.Watermark zu verwenden, fügen Sie dessen Maven‑Koordinaten zu Ihrer Projekt‑`pom.xml` hinzu. Dadurch wird die Bibliothek und ihre Abhängigkeiten geladen, sodass Sie die Klasse Watermarker instanziieren und direkt aus Java‑Code mit Diagrammdateien arbeiten können. Anschließend können Sie die Lizenzierung konfigurieren und Ausgaboptionen festlegen, bevor Sie ein Dokument verarbeiten.  

Fügen Sie die GroupDocs.Watermark‑Abhängigkeit zu Ihrer `pom.xml` hinzu.  

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

Wenn Sie Maven nicht verwenden möchten, laden Sie das neueste JAR von der offiziellen Release‑Seite herunter.  

[GroupDocs.Watermark für Java Releases](https://releases.groupdocs.com/watermark/java/)  

#### Schritte zur Lizenzbeschaffung  
- Beginnen Sie mit einer kostenlosen Testversion, um die API zu evaluieren.  
- Für die Produktion erhalten Sie eine temporäre oder permanente Lizenz über das Anbieter‑Portal.  

#### Grundlegende Initialisierung und Einrichtung  
Die Klasse `Watermarker` ist der Einstiegspunkt für alle Dokumentverarbeitungs‑Operationen.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Wie bearbeitet man Diagramme und entfernt Hyperlinks mit GroupDocs.Watermark?  
Die `Watermarker`‑Klasse stellt den API‑Einstiegspunkt zum Laden und Ändern von Dokumenten bereit.  
Laden Sie zunächst die Diagrammdatei in eine Watermarker‑Instanz. Dann rufen Sie die Sammlung von Formen ab, identifizieren diejenigen, die Hyperlink‑Objekte enthalten, und iterieren sie in umgekehrter Reihenfolge, um jeden Link sicher zu löschen, ohne die Indizierung der Sammlung zu beeinflussen. Dadurch werden alle eingebetteten URLs entfernt, während die visuelle Integrität des Diagramms erhalten bleibt.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Warum dieser Schritt wichtig ist**: Das Laden der Datei gibt Ihnen programmatischen Zugriff auf jede Form und deren zugehörige Eigenschaften.  

## Wie greift man auf den Inhalt von Formen in einem Diagramm zu?  
Das Objekt `DiagramShape` repräsentiert eine einzelne Form innerhalb eines Diagramms und stellt deren Eigenschaften sowie angehängte Metadaten bereit.  
Nach dem Laden des Diagramms rufen Sie `getShapes()` auf dem Watermarker auf, um eine Liste von `DiagramShape`‑Objekten zu erhalten. Jede Form kann auf Hyperlink‑Sammlungen untersucht werden, was ein präzises Anvisieren von Links zum Entfernen oder Ändern ermöglicht. Sie können zudem den Text, die Farben und die Geometrie der Form auslesen, falls weitere Anpassungen erforderlich sind.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Warum dieser Schritt wichtig ist**: Das gezielte Anvisieren der genauen Form stellt sicher, dass Sie nur unerwünschte Links entfernen, ohne andere visuelle Elemente zu beeinflussen.  

## Wie iteriert man sicher und entfernt Hyperlinks?  
Die Methode `removeHyperlink(int index)` löscht einen Hyperlink an der angegebenen Position innerhalb der Hyperlink‑Sammlung einer Form.  
Iterieren Sie über die Hyperlink‑Liste vom letzten Index bis null. Diese umgekehrte Schleife verhindert das Index‑Verschieben, das beim Entfernen von Elementen auftritt, und stellt sicher, dass jeder Hyperlink verarbeitet wird, ohne übersprungen zu werden. Nach dem Entfernen können Sie den Zustand der Form aktualisieren oder zur nächsten Form im Diagramm fortfahren.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Warum dieser Schritt wichtig ist**: Eine umgekehrte Schleife garantiert, dass alle Hyperlinks entfernt werden, ohne Einträge zu überspringen.  

## Wie speichert man das bearbeitete Diagramm und gibt Ressourcen frei?  
Die Methode `save(String path)` schreibt das modifizierte Dokument an den angegebenen Dateipfad und finalisiert alle Änderungen.  
Nachdem alle Hyperlinks entfernt wurden, rufen Sie die `save`‑Methode auf der Watermarker‑Instanz auf und geben einen neuen Dateinamen an, um das Original nicht zu überschreiben. Anschließend rufen Sie `close()` auf, um Dateihandles freizugeben und Speicher zu leeren, was für langlaufende Batch‑Prozesse essenziell ist. Dadurch wird sichergestellt, dass die Datei ordnungsgemäß geschlossen ist und für die weitere Verwendung bereitsteht.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Warum dieser Schritt wichtig ist**: Das ordnungsgemäße Schließen von Ressourcen verhindert Speicherlecks und Dateisperr‑Probleme auf dem Server.  

## Praktische Anwendungen  
Das Entfernen von Hyperlinks aus Diagrammformen kann in mehreren realen Szenarien vorteilhaft sein:  

1. **Sicherheit** – Verhindern Sie externe Links, die zu bösartigen Websites führen könnten.  
2. **Compliance** – Erfüllen Sie Unternehmensrichtlinien, die eingebettete URLs in freigegebenen Assets verbieten.  
3. **Klarheit** – Erstellen Sie sauberere Präsentationen, bei denen Links ablenken würden.  

Sie können diese Logik in größere Automatisierungspipelines einbetten, z. B. nächtliche Batch‑Jobs, die alle Diagramme bereinigen, bevor sie im Intranet veröffentlicht werden.  

## Leistungsüberlegungen  

### Optimierung der Leistung  
- Verwenden Sie pro Datei eine einzelne `Watermarker`‑Instanz, um den Overhead zu reduzieren.  
- Bevorzugen Sie die umgekehrte Iteration (wie gezeigt), um teure Neuinindexierung von Listen zu vermeiden.  

### Richtlinien zur Ressourcennutzung  
- Bei Diagrammen größer als 200 MB sollten Sie die Heap‑Nutzung überwachen und erwägen, das JVM‑Flag `-Xmx` zu erhöhen.  
- Profiling‑Tools wie VisualVM können helfen, Engpässe bei groß angelegten Batch‑Durchläufen zu identifizieren.  

### Best Practices für das Java‑Speichermanagement  
- Deklarieren Sie Objekte im kleinstmöglichen Gültigkeitsbereich.  
- Verwenden Sie try‑with‑resources beim Arbeiten mit Streams, um eine automatische Schließung sicherzustellen.  

## Häufig gestellte Fragen  

**Q: Wie gehe ich mit Diagrammen um, die Tausende von Formen enthalten?**  
A: Verarbeiten Sie das Diagramm seitenweise und geben Sie die Ressourcen jeder Seite frei, bevor Sie zur nächsten wechseln, um den Speicherverbrauch gering zu halten.  

**Q: Kann ich das Entfernen von Hyperlinks auf bestimmte Seiten beschränken?**  
A: Ja – rufen Sie den gewünschten Seitenindex ab und wenden Sie die Entfernschleife nur auf Formen auf dieser Seite an.  

**Q: Ist eine kommerzielle Lizenz für die Stapelverarbeitung zwingend erforderlich?**  
A: Eine gültige Lizenz ist für jede produktions‑level Bereitstellung erforderlich; die kostenlose Testversion ist auf 30 Tage und 5 Dokumente begrenzt.  

**Q: Unterstützt GroupDocs.Watermark SVG‑Diagramme?**  
A: Absolut – SVG gehört zu den 30+ unterstützten Formaten, und Hyperlinks können mit denselben API‑Aufrufen entfernt werden.  

**Q: Was ist, wenn eine Form mehrere Hyperlinks hat?**  
A: Die umgekehrte Iterationsschleife entfernt jeden Hyperlink‑Eintrag einzeln und stellt sicher, dass alle Links gelöscht werden.  

## Ressourcen  

- [Dokumentation](https://docs.groupdocs.com/watermark/java/)  
- [API‑Referenz](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub‑Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporäre Lizenzbeschaffung](https://purchase.groupdocs.com/temporary-license/)  

---  

**Zuletzt aktualisiert:** 2026-08-25  
**Getestet mit:** GroupDocs.Watermark 24.11 für Java  
**Autor:** GroupDocs  

## Verwandte Tutorials  

- [Diagramm‑Wasserzeichen‑Tutorials für GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Diagramm‑Kopf‑ und Fußzeilen in Java mit GroupDocs.Watermark bearbeiten: Ein umfassender Leitfaden](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Effizientes Entfernen von Formen aus Diagrammen mit GroupDocs.Watermark für Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)