---
title: Fügen Sie Wasserzeichen zu XObjects in PDF hinzu
linktitle: Fügen Sie Wasserzeichen zu XObjects in PDF hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs.Watermark für .NET Wasserzeichen zu XObjects in PDF hinzufügen. Befolgen Sie unsere Schritt-für-Schritt-Anleitung für eine einfache Implementierung.
weight: 20
url: /de/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Einführung
Das Anbringen von Wasserzeichen in PDFs ist ein entscheidender Schritt, um sicherzustellen, dass Ihre Dokumente vor unbefugter Nutzung geschützt sind. Mit Groupdocs.Watermark für .NET war das Hinzufügen von Wasserzeichen zu XObjects in Ihren PDFs noch nie so einfach. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess und stellen sicher, dass Sie sicher Wasserzeichen auf Ihre PDF-Dokumente anwenden können. Lass uns anfangen!
## Voraussetzungen
Bevor wir mit dem Tutorial beginnen, stellen wir sicher, dass Sie über alles verfügen, was Sie für einen reibungslosen Ablauf benötigen:
-  Groupdocs.Watermark für .NET: Laden Sie die neueste Version herunter und installieren Sie sie[Hier](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Entwicklungscomputer installiert ist.
- Entwicklungsumgebung: Verwenden Sie Visual Studio oder eine andere IDE, die die .NET-Entwicklung unterstützt.
-  Temporäre Lizenz: Besorgen Sie sich eine[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) wenn Sie das Produkt bewerten.
Sobald Sie diese Voraussetzungen erfüllt haben, können Sie mit dem Wasserzeichen Ihrer PDFs beginnen.
## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Öffnen Sie Ihr C#-Projekt und fügen Sie die folgenden using-Anweisungen hinzu:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Richten Sie Ihre Dokumentpfade ein
Der erste Schritt besteht darin, die Pfade für Ihr Dokument einzurichten. Definieren Sie den Pfad, in dem sich Ihr PDF befindet und wo Sie das mit Wasserzeichen versehene PDF speichern möchten.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Ersetzen`"Your Document Path"` Und`"Your Document Directory"` mit den tatsächlichen Pfaden auf Ihrem Computer.
## Schritt 2: PDF-Ladeoptionen initialisieren
Als Nächstes müssen Sie die PDF-Ladeoptionen initialisieren. Dies ist entscheidend für das korrekte Laden des PDF-Inhalts.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Schritt 3: Laden Sie das PDF-Dokument
Laden Sie mithilfe der Ladeoptionen das PDF-Dokument mit`Watermarker` Klasse.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Schritt 4: Erstellen Sie das Wasserzeichen
Jetzt müssen Sie das Wasserzeichen erstellen, das der PDF-Datei hinzugefügt wird. Für dieses Tutorial erstellen wir ein Textwasserzeichen.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Schritt 5: Wasserzeichen zu XObjects hinzufügen
Durchlaufen Sie jede Seite und jedes XObject innerhalb der PDF-Datei, um das Wasserzeichen anzuwenden.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Fügen Sie dem Bild ein Wasserzeichen hinzu
            xObject.Image.Add(watermark);
        }
    }
}
```
## Schritt 6: Speichern Sie das mit Wasserzeichen versehene PDF
Speichern Sie abschließend die mit Wasserzeichen versehene PDF-Datei in der angegebenen Ausgabedatei.
```csharp
    watermarker.Save(outputFileName);
}
```
Und da haben Sie es! Ihr PDF enthält jetzt Wasserzeichen auf allen seinen XObjects.
## Abschluss
 Das Hinzufügen von Wasserzeichen zu Ihren PDF-Dokumenten mit Groupdocs for .NET ist ein unkomplizierter Vorgang, der eine zusätzliche Sicherheitsebene bietet. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie sicherstellen, dass Ihre Dokumente vor unbefugter Nutzung geschützt sind. Denken Sie daran, Sie können jederzeit auf die verweisen[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) für detailliertere Informationen und erweiterte Funktionen.
## FAQs
### Kann ich ein Bild als Wasserzeichen anstelle von Text verwenden?
Ja, Groupdocs.Watermark für .NET unterstützt sowohl Text- als auch Bildwasserzeichen.
### Wie kann ich Groupdocs.Watermark testen, ohne es zu kaufen?
 Sie können a verwenden[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) um das Produkt zu bewerten.
### Ist es möglich, das Erscheinungsbild des Wasserzeichens anzupassen?
Absolut! Sie können Schriftart, Größe, Drehwinkel und mehr anpassen.
### Unterstützt Groupdocs.Watermark andere Dokumentformate?
Ja, es unterstützt verschiedene Formate, darunter Word, Excel und PowerPoint.
### Wo kann ich Unterstützung erhalten, wenn ich auf Probleme stoße?
 Unterstützung erhalten Sie von der[Groupdocs-Forum](https://forum.groupdocs.com/c/watermark/19).