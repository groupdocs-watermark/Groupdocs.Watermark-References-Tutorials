---
title: Fügen Sie Wasserzeichen zu Anmerkungsbildern in PDF hinzu
linktitle: Fügen Sie Wasserzeichen zu Anmerkungsbildern in PDF hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie Ihre PDF-Dokumente schützen, indem Sie mit Groupdocs.Watermark für .NET Wasserzeichen zu Anmerkungsbildern hinzufügen.
weight: 17
url: /de/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# Fügen Sie Wasserzeichen zu Anmerkungsbildern in PDF hinzu

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von Groupdocs.Watermark für .NET Wasserzeichen zu Anmerkungsbildern in PDF-Dokumenten hinzufügen. Wasserzeichen sind von entscheidender Bedeutung, um Ihre Dokumente vor unbefugter Nutzung oder Verbreitung zu schützen. Wenn Sie dieser Schritt-für-Schritt-Anleitung folgen, erfahren Sie, wie Sie Textwasserzeichen effektiv auf Anmerkungsbilder in PDFs anwenden.
## Voraussetzungen
Bevor Sie fortfahren, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Grundlegendes Verständnis der Programmiersprache C#.
2. Installierte Groupdocs.Watermark für die .NET-Bibliothek.
3. Zugriff auf eine Entwicklungsumgebung wie Visual Studio.
4. Ein PDF-Dokument mit Anmerkungsbildern zum Wasserzeichen.

## Namensräume importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das PDF-Dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Schritt 2: PDF-Inhalt abrufen und Wasserzeichen initialisieren
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Bild- oder Textwasserzeichen initialisieren
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Schritt 3: Durchlaufen Sie PDF-Seiten und Anmerkungsbilder
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Fügen Sie dem Bild ein Wasserzeichen hinzu
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Schritt 4: Speichern Sie das Dokument mit Wasserzeichen
```csharp
    watermarker.Save(outputFileName);
}
```
Nachdem Sie diese Schritte ausgeführt haben, wird Ihrem PDF-Dokument das angegebene Wasserzeichen zu den Anmerkungsbildern hinzugefügt.

## Abschluss
Das Hinzufügen von Wasserzeichen zu Anmerkungsbildern in PDFs ist wichtig, um die Integrität Ihrer Dokumente zu schützen und sicherzustellen, dass sie nicht missbraucht werden. Mit Groupdocs.Watermark für .NET wird dieser Prozess einfach und effizient, sodass Sie Ihre PDF-Dateien effektiv schützen können.
## FAQs
### Kann ich demselben PDF-Dokument mehrere Wasserzeichen hinzufügen?
Ja, Sie können mit Groupdocs.Watermark für .NET mehrere Wasserzeichen zum selben PDF-Dokument hinzufügen.
### Unterstützt Groupdocs.Watermark neben PDF auch andere Dokumentformate?
Ja, Groupdocs unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Ist es möglich, das Erscheinungsbild des Wasserzeichens anzupassen?
Natürlich können Sie Text, Schriftart, Farbe, Größe und Position des Wasserzeichens nach Ihren Wünschen anpassen.
### Kann ich mit Groupdocs.Watermark Wasserzeichen aus PDF-Dokumenten entfernen?
Ja, Groupdocs.Watermark bietet Funktionen zum mühelosen Entfernen von Wasserzeichen aus PDF-Dokumenten.
### Gibt es eine kostenlose Testversion für Groupdocs.Watermark für .NET?
Ja, Sie können auf der Website eine kostenlose Testversion von Groupdocs.Watermark für .NET nutzen.