---
title: Fügen Sie Wasserzeichen zu Bildern in PDF hinzu
linktitle: Fügen Sie Wasserzeichen zu Bildern in PDF hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in unserem ausführlichen Schritt-für-Schritt-Tutorial, wie Sie mithilfe von GroupDocs.Watermark für .NET Wasserzeichen zu Bildern in PDF-Dokumenten hinzufügen. Sichern Sie Ihre PDFs ganz einfach.
type: docs
weight: 19
url: /de/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Einführung
Das Hinzufügen von Wasserzeichen zu Bildern in einem PDF-Dokument kann für den Schutz Ihres geistigen Eigentums oder die Gewährleistung der Authentizität Ihrer Dokumente von entscheidender Bedeutung sein. Mit GroupDocs.Watermark für .NET kann diese Aufgabe effizient und einfach erledigt werden. Dieses Tutorial führt Sie durch jeden Schritt des Prozesses, von der Einrichtung Ihrer Umgebung über das Hinzufügen von Wasserzeichen bis hin zum Speichern des endgültigen Dokuments. Lass uns eintauchen!
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Visual Studio: Installieren Sie Visual Studio, die integrierte Entwicklungsumgebung (IDE) für .NET-Anwendungen.
2.  GroupDocs.Watermark für .NET: Laden Sie die GroupDocs.Watermark für .NET-Bibliothek von herunter und installieren Sie sie[Release-Seite](https://releases.groupdocs.com/Watermark/net/).
3. Ein PDF-Dokument: Halten Sie ein PDF-Dokument mit Bildern bereit, um die Wasserzeichenfunktion zu testen.
4.  Temporäre Lizenz: Besorgen Sie sich eine[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) wenn Sie das Produkt bewerten.
## Namespaces importieren
Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Dazu gehören die Kern-Namespaces, die für die Arbeit mit PDF-Dokumenten und Wasserzeichen erforderlich sind.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Richten Sie den Dokumentpfad und das Ausgabeverzeichnis ein
Definieren Sie zunächst die Pfade für das Eingabedokument und das Ausgabeverzeichnis, in dem das mit Wasserzeichen versehene Dokument gespeichert wird. Dieser Schritt ist entscheidend, um sicherzustellen, dass Ihr Programm weiß, wo sich das Quelldokument befindet und wo die verarbeitete Datei gespeichert werden soll.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Schritt 2: Laden Sie das PDF-Dokument
 Als nächstes müssen Sie das PDF-Dokument mit laden`PdfLoadOptions`. Mit dieser Klasse können Sie Optionen zum Laden der PDF-Datei festlegen, z. B. bei Bedarf einen Passwortschutz.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier finden Sie Ihren Code für das Wasserzeichen
}
```
## Schritt 3: Erstellen Sie das Wasserzeichen
Initialisieren Sie nun das Wasserzeichen. In diesem Beispiel erstellen wir ein Textwasserzeichen mit der Aufschrift „Geschütztes Bild“. Passen Sie Schriftart, Ausrichtung, Drehung und Skalierung entsprechend Ihren Anforderungen an.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Schritt 4: Greifen Sie auf PDF-Inhalte zu
Rufen Sie den Inhalt des PDF-Dokuments ab. Insbesondere müssen wir auf die Bilder im PDF zugreifen. Hier konzentrieren wir uns auf die erste Seite, Sie können dies jedoch bei Bedarf auf andere Seiten erweitern.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Holen Sie sich alle Bilder von der ersten Seite
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Schritt 5: Anwenden des Wasserzeichens auf Bilder
Gehen Sie jedes auf der ersten Seite gefundene Bild durch und wenden Sie das Wasserzeichen an. Dadurch wird sichergestellt, dass auf alle Bilder auf der angegebenen Seite das Wasserzeichen angewendet wird.
```csharp
// Fügen Sie allen gefundenen Bildern ein Wasserzeichen hinzu
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Schritt 6: Speichern Sie das mit Wasserzeichen versehene Dokument
Speichern Sie abschließend die mit Wasserzeichen versehene PDF-Datei im angegebenen Ausgabeverzeichnis. Dieser Schritt schließt den Vorgang ab, indem die Änderungen in eine neue Datei geschrieben werden.
```csharp
watermarker.Save(outputFileName);
```
## Abschluss
Und da haben Sie es! Das Hinzufügen eines Wasserzeichens zu Bildern in einer PDF-Datei mit GroupDocs Watermark für .NET ist ein unkomplizierter Vorgang, der die Sicherheit und Authentizität Ihrer Dokumente erheblich verbessern kann. Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihr geistiges Eigentum geschützt und Ihre Dokumente sicher sind.
## FAQs
### Was ist GroupDocs.Watermark für .NET?
GroupDocs.Watermark für .NET ist eine umfassende Bibliothek, die es Entwicklern ermöglicht, Wasserzeichen in verschiedenen Dokumentformaten, einschließlich PDFs, hinzuzufügen, zu suchen und zu entfernen.
### Kann ich mit GroupDocs.Watermark sowohl Text- als auch Bildwasserzeichen hinzufügen?
Ja, GroupDocs.Watermark unterstützt sowohl Text- als auch Bildwasserzeichen und bietet so Flexibilität für verschiedene Arten von Wasserzeichenanforderungen.
### Ist es möglich, mehrere Seiten in einer PDF-Datei mit Wasserzeichen zu versehen?
Absolut! Sie können jede Seite im PDF durchlaufen und den Bildern auf jeder Seite Wasserzeichen hinzufügen.
### Benötige ich eine Lizenz, um GroupDocs.Watermark für .NET zu verwenden?
 Ja, eine Lizenz ist erforderlich. Sie können eine erhalten[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) zu Auswertungszwecken.
### Wo finde ich weitere Dokumentation zu GroupDocs.Watermark für .NET?
 Eine umfassende Dokumentation finden Sie hier[GroupDocs.Watermark-Dokumentationsseite](https://reference.groupdocs.com/Watermark/net/).