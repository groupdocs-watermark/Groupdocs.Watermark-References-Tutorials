---
title: Fügen Sie Wasserzeichen zu Bildartefakten in PDF hinzu
linktitle: Fügen Sie Wasserzeichen zu Bildartefakten in PDF hinzu
second_title: GroupDocs.Watermark .NET-API
description: Schützen Sie Ihre PDF-Dateien mit personalisierten Wasserzeichen mit GroupDocs.Watermark für .NET. Fügen Sie ganz einfach Text- oder Bildwasserzeichen zu Bildartefakten in PDF-Dokumenten hinzu.
weight: 18
url: /de/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens eines Wasserzeichens zu Bildartefakten in einem PDF-Dokument mithilfe von GroupDocs.Watermark für .NET. Wenn Sie diese Schritte befolgen, können Sie Ihre PDF-Dateien effizient mit personalisierten Wasserzeichen schützen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Watermark für .NET: Laden Sie die GroupDocs.Watermark für .NET-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentpfad: Geben Sie den Pfad zum PDF-Dokument an, dem Sie das Wasserzeichen hinzufügen möchten.
3. Ausgabeverzeichnis: Erstellen Sie ein Verzeichnis, in dem das mit Wasserzeichen versehene Dokument gespeichert wird.

## Namespaces importieren
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument und initialisieren Sie den Wasserzeichen
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Schritt 2: PDF-Inhalt abrufen und Wasserzeichen hinzufügen
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Bild- oder Textwasserzeichen initialisieren
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Fügen Sie dem Bild ein Wasserzeichen hinzu
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Schritt 3: Speichern Sie das mit Wasserzeichen versehene Dokument
```csharp
	watermarker.Save(outputFileName);
}
```

## Abschluss
Mit GroupDocs.Watermark für .NET wird das Hinzufügen von Wasserzeichen zu Bildartefakten in PDF-Dokumenten zu einem nahtlosen Prozess. Wenn Sie diesem Tutorial folgen, können Sie Ihre PDF-Dateien effizient mit benutzerdefinierten Wasserzeichen schützen und so deren Sicherheit und Authentizität gewährleisten.
## FAQs
### Kann ich meinem PDF-Dokument sowohl Bild- als auch Textwasserzeichen hinzufügen?
Ja, GroupDocs.Watermark für .NET unterstützt das gleichzeitige Hinzufügen von Bild- und Textwasserzeichen.
### Gibt es eine Beschränkung hinsichtlich der Anzahl der Wasserzeichen, die ich einem Dokument hinzufügen kann?
Nein, Sie können einem Dokument ohne Einschränkungen mehrere Wasserzeichen hinzufügen.
### Kann ich das Aussehen und die Position des Wasserzeichens anpassen?
Sie haben absolut die volle Kontrolle über das Aussehen, die Position und die Eigenschaften des Wasserzeichens.
### Unterstützt GroupDocs.Watermark für .NET neben PDF auch andere Dokumentformate?
Ja, es unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Gibt es eine Möglichkeit, Wasserzeichen aus einem Dokument zu entfernen?
Ja, GroupDocs.Watermark für .NET bietet Methoden zum Entfernen von Wasserzeichen aus Dokumenten bei Bedarf.