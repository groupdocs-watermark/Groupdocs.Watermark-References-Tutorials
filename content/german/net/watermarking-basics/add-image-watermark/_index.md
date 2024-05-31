---
title: Bildwasserzeichen hinzufügen
linktitle: Bildwasserzeichen hinzufügen
second_title: GroupDocs.Watermark .NET-API
description: Fügen Sie mit GroupDocs.Watermark für .NET mühelos Bildwasserzeichen zu Ihren Dokumenten hinzu. Schützen Sie Ihr geistiges Eigentum ganz einfach.
type: docs
weight: 10
url: /de/net/watermarking-basics/add-image-watermark/
---
## Einführung
In diesem Tutorial befassen wir uns mit dem Prozess des Hinzufügens eines Bildwasserzeichens zu Ihren Dokumenten mithilfe von GroupDocs.Watermark für .NET. Das Versehen von Dokumenten mit Wasserzeichen ist für den Schutz des geistigen Eigentums und der Marke unerlässlich. Mit GroupDocs.Watermark für .NET können Sie Wasserzeichen nahtlos in verschiedene Dokumentformate wie Word, Excel, PowerPoint, PDF und viele mehr integrieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1.  GroupDocs.Watermark für .NET-Bibliothek: Laden Sie die GroupDocs.Watermark für .NET-Bibliothek von herunter und installieren Sie sie[Webseite](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Halten Sie das Dokument bereit, dem Sie das Wasserzeichen hinzufügen möchten.
3. Bild für Wasserzeichen: Bereiten Sie die Bilddatei vor, die Sie als Wasserzeichen verwenden möchten.

## Namespaces importieren
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Schritt 1: Dokumentpfad und Ausgabeverzeichnis initialisieren
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Ersetzen`"Your Document Path"`mit dem absoluten oder relativen Pfad zu Ihrem Dokument und`"Your Document Directory"` mit dem Verzeichnis, in dem Sie das mit Wasserzeichen versehene Dokument speichern möchten.
## Schritt 2: Öffnen Sie Document Stream und initialisieren Sie Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Hier wird der Wasserzeichenprozess durchgeführt
    }
}
```
 Öffnen Sie den Dokumentstream mit`FileStream` und initialisieren Sie die`Watermarker` Objekt.
## Schritt 3: Bildwasserzeichen hinzufügen
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Erstelle ein`ImageWatermark` Objekt mit dem Pfad zu der Bilddatei, die Sie als Wasserzeichen verwenden möchten. Legen Sie die horizontale und vertikale Ausrichtung des Wasserzeichens fest.
## Schritt 4: Dokument mit Wasserzeichen speichern
```csharp
watermarker.Save(outputFileName);
```
Speichern Sie das mit Wasserzeichen versehene Dokument im angegebenen Ausgabeverzeichnis unter dem gewünschten Dateinamen.

## Abschluss
Zusammenfassend bietet GroupDocs.Watermark für .NET eine umfassende Lösung zum mühelosen Hinzufügen von Wasserzeichen zu verschiedenen Dokumentformaten. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Ihren Dokumenten effizient Bildwasserzeichen hinzufügen und Ihr geistiges Eigentum schützen.
## FAQs
### Kann ich mit GroupDocs.Watermark für .NET Textwasserzeichen hinzufügen?
Ja, GroupDocs.Watermark für .NET unterstützt das Hinzufügen von Bild- und Textwasserzeichen zu Dokumenten.
### Ist GroupDocs.Watermark für .NET mit verschiedenen Dokumentformaten kompatibel?
Absolut, GroupDocs.Watermark für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter Word, Excel, PowerPoint, PDF und mehr.
### Bietet GroupDocs.Watermark für .NET Anpassungsoptionen für Wasserzeichen?
Ja, Sie können verschiedene Aspekte des Wasserzeichens anpassen, z. B. Position, Größe, Deckkraft und Drehung.
### Kann ich mit GroupDocs.Watermark für .NET Wasserzeichen aus Dokumenten entfernen?
Ja, GroupDocs.Watermark für .NET bietet Funktionen zum Erkennen und Entfernen von Wasserzeichen aus Dokumenten.
### Gibt es eine Testversion für GroupDocs.Watermark für .NET?
 Ja, Sie können auf der Website eine kostenlose Testversion nutzen, um die Funktionen vor dem Kauf zu erkunden[Hier](https://releases.groupdocs.com/).