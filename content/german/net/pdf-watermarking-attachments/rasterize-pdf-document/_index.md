---
title: PDF-Dokument rastern
linktitle: PDF-Dokument rastern
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie PDF-Dokumente mit GroupDocs.Watermark für .NET rastern. Verbessern Sie mühelos die Dokumentensicherheit und die visuelle Attraktivität.
weight: 27
url: /de/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# PDF-Dokument rastern

## Einführung
Im Bereich der Dokumentenverwaltung und -bearbeitung ist GroupDocs.Watermark für .NET ein leistungsstarkes Tool, das robuste Funktionen zum Hinzufügen, Entfernen und Durchsuchen von Wasserzeichen in verschiedenen Dokumentformaten bietet. Ganz gleich, ob es darum geht, Ihre Dokumente mit Urheberrechtshinweisen zu schützen, Firmenlogos für das Branding hinzuzufügen oder Dokumente einfach mit Stempeln zu kommentieren – GroupDocs.Watermark vereinfacht den Prozess mit seiner intuitiven API und seinem umfangreichen Funktionsumfang.
## Voraussetzungen
Bevor Sie mit GroupDocs.Watermark für .NET in die Welt des Wasserzeichens eintauchen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
### 1. Installieren Sie .NET Framework
Stellen Sie sicher, dass das .NET Framework auf Ihrem Entwicklungscomputer installiert ist. Sie können es von der Microsoft-Website herunterladen oder Ihren bevorzugten Paketmanager verwenden.
#### Schritt 1: Laden Sie .NET Framework herunter
Besuchen Sie die Downloadseite für Microsoft .NET Framework.
#### Schritt 2: Installieren Sie .NET Framework
Befolgen Sie die Installationsanweisungen auf der Download-Seite, um das .NET Framework auf Ihrem System zu installieren.
### 2. Besorgen Sie sich die GroupDocs.Watermark-Lizenz
Um den vollen Funktionsumfang von GroupDocs.Watermark nutzen zu können, benötigen Sie eine gültige Lizenz. Sie können entweder eine Lizenz erwerben oder zu Evaluierungszwecken eine temporäre Lizenz erwerben.
#### Schritt 1: Holen Sie sich eine Lizenz
Besuchen Sie die GroupDocs.Watermark-Kaufseite.
#### Schritt 2: Kaufen oder erhalten Sie eine temporäre Lizenz
Wählen Sie je nach Bedarf die passende Lizenzierungsoption – erwerben Sie eine Lizenz für die weitere Nutzung oder erwerben Sie eine temporäre Lizenz für Evaluierungszwecke.

## Namespaces importieren
Bevor Sie mit dem Wasserzeichen Ihrer Dokumente beginnen, stellen Sie sicher, dass Sie die erforderlichen Namespaces importieren, um nahtlos auf die Funktionalität von GroupDocs zugreifen zu können.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Nachdem Sie nun alles eingerichtet haben, beginnen wir mit der Rasterung eines PDF-Dokuments mit GroupDocs.Watermark für .NET. Durch die Rasterung wird jede Seite des PDF-Dokuments in ein Rasterbildformat wie PNG konvertiert.
## Schritt 1: Variablen initialisieren
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Stellen Sie sicher, dass Sie „Ihr Dokumentpfad“ und „Ihr Dokumentverzeichnis“ durch den tatsächlichen Pfad zu Ihrem PDF-Dokument bzw. das gewünschte Ausgabeverzeichnis ersetzen.
## Schritt 2: Dokument laden und Wasserzeichen hinzufügen
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Bild- oder Textwasserzeichen initialisieren
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Fügen Sie zunächst ein beliebiges Wasserzeichen hinzu
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rastern Sie alle Seiten
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Der Inhalt aller Seiten wird durch Rasterbilder ersetzt
    watermarker.Save(outputFileName);
}
```
In diesem Schritt laden wir das PDF-Dokument und initialisieren ein Textwasserzeichen mit angegebenen Eigenschaften wie Text, Schriftart, Ausrichtung, Drehwinkel, Größentyp, Skalierungsfaktor und Deckkraft. Anschließend fügen wir das Wasserzeichen zum Dokument hinzu. Als nächstes rufen wir den Inhalt des PDF-Dokuments ab und rastern alle Seiten in das PNG-Format mit einer Auflösung von 100 DPI. Abschließend speichern wir das geänderte Dokument mit gerastertem Inhalt.

## Abschluss
GroupDocs.Watermark für .NET bietet eine umfassende Lösung zum einfachen Hinzufügen von Wasserzeichen zu verschiedenen Dokumentformaten. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie PDF-Dokumente effektiv rastern und ihre Sicherheit und visuelle Attraktivität verbessern.
## FAQs
### Ist GroupDocs.Watermark mit anderen Dokumentformaten außer PDF kompatibel?
Ja, GroupDocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter Microsoft Word, Excel, PowerPoint, Visio, Outlook und viele mehr.
### Kann ich das Erscheinungsbild von mit GroupDocs.Watermark hinzugefügten Wasserzeichen anpassen?
Absolut! GroupDocs.Watermark bietet umfangreiche Optionen zum Anpassen von Wasserzeicheneigenschaften wie Text, Schriftart, Farbe, Größe, Deckkraft, Drehung und Position.
### Bietet GroupDocs.Watermark Unterstützung für die Stapelverarbeitung?
Ja, Sie können mit GroupDocs Watermark problemlos mehrere Dokumente im Stapelmodus verarbeiten und so Zeit und Aufwand sparen, wenn Sie große Dateimengen mit Wasserzeichen versehen.
### Gibt es eine Testversion für GroupDocs.Watermark?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Watermark von der Website herunterladen, um die Funktionen zu testen, bevor Sie einen Kauf tätigen.
### Wie kann ich Hilfe erhalten, wenn ich auf Probleme stoße oder Fragen zu GroupDocs.Watermark habe?
Sie können das GroupDocs.Watermark-Forum besuchen, um Unterstützung von der Community zu erhalten, oder sich an das GroupDocs-Supportteam wenden, um Hilfe zu erhalten.