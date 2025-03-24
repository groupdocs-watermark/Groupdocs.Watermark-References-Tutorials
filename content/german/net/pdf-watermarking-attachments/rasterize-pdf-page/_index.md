---
title: PDF-Seite rastern
linktitle: PDF-Seite rastern
second_title: GroupDocs.Watermark .NET-API
description: Verbessern Sie die Dokumentensicherheit mit GroupDocs für .NET. Fügen Sie Wasserzeichen nahtlos zu PDF und anderen Formaten hinzu.
weight: 28
url: /de/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# PDF-Seite rastern

## Einführung
GroupDocs.Watermark für .NET ist eine leistungsstarke API, die es Entwicklern ermöglicht, nahtlos Wasserzeichen zu verschiedenen Dokumentformaten hinzuzufügen, darunter PDF, Word, Excel, PowerPoint und mehr. Mit seiner intuitiven Benutzeroberfläche und umfangreichen Funktionen vereinfacht GroupDocs.Watermark das Hinzufügen von Text- oder Bildwasserzeichen zu Dokumenten und ermöglicht Benutzern so, ihr geistiges Eigentum zu schützen und die Dokumentensicherheit mühelos zu erhöhen.
## Voraussetzungen
Bevor Sie GroupDocs.Watermark für .NET verwenden, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Installation: Laden Sie GroupDocs.Watermark für .NET von herunter und installieren Sie es[Download-Seite](https://releases.groupdocs.com/Watermark/net/).
2.  Lizenz: Erwerben Sie eine Lizenz für GroupDocs.Watermark für .NET. Eine temporäre Lizenz zu Evaluierungszwecken erhalten Sie bei[Hier](https://purchase.groupdocs.com/temporary-license/) , oder erwerben Sie eine Volllizenz von der[Kaufseite](https://purchase.groupdocs.com/buy).
3. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Entwicklungscomputer installiert ist.
4. Dokument: Bereiten Sie das Dokument vor, dem Sie Wasserzeichen hinzufügen möchten.

## Namespaces importieren
Um GroupDocs.Watermark für .NET zu verwenden, importieren Sie die erforderlichen Namespaces in Ihr Projekt:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ihr Code kommt hierher
}
```
## Schritt 2: Wasserzeichen initialisieren
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Schritt 3: Wasserzeichen hinzufügen
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Schritt 4: Rastern Sie die Seite
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Schritt 5: Speichern Sie das Dokument
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Zusammenfassend bietet GroupDocs.Watermark für .NET eine nahtlose Lösung zum Hinzufügen von Wasserzeichen zu PDF- und anderen Dokumentformaten. Wenn Entwickler die oben beschriebene Schritt-für-Schritt-Anleitung befolgen, können sie PDF-Seiten effizient rastern und die Dokumentensicherheit ganz einfach verbessern.
## FAQs
### Ist GroupDocs.Watermark mit anderen Dokumentformaten außer PDF kompatibel?
Ja, GroupDocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter Word, Excel, PowerPoint, Visio und mehr.
### Kann ich das Erscheinungsbild des dem Dokument hinzugefügten Wasserzeichens anpassen?
Absolut! GroupDocs.Watermark bietet umfangreiche Anpassungsoptionen für Text- und Bildwasserzeichen, sodass Benutzer Schriftart, Größe, Farbe, Deckkraft und Positionierung nach ihren Wünschen anpassen können.
### Ist GroupDocs.Watermark sowohl für den persönlichen als auch für den kommerziellen Gebrauch geeignet?
Ja, GroupDocs.Watermark bietet flexible Lizenzoptionen, um sowohl den individuellen als auch den Unternehmensanforderungen gerecht zu werden, sodass es sowohl für persönliche Projekte als auch für groß angelegte kommerzielle Anwendungen geeignet ist.
### Bietet GroupDocs.Watermark technischen Support für Entwickler?
Ja, Entwickler können über das GroupDocs.Watermark-Forum auf umfassenden technischen Support zugreifen, wo sie Hilfe suchen, Erfahrungen austauschen und mit anderen Entwicklern in Kontakt treten können.
### Kann ich GroupDocs.Watermark testen, bevor ich einen Kauf tätige?
Sicherlich! Sie können eine kostenlose Testversion von GroupDocs.Watermark unter herunterladen[Veröffentlichungsseite](https://releases.groupdocs.com/)So können Sie die Features und Funktionalitäten erkunden, bevor Sie einen Kauf tätigen.