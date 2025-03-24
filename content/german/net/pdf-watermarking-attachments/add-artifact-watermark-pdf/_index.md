---
title: Fügen Sie dem PDF ein Artefakt-Wasserzeichen hinzu
linktitle: Fügen Sie dem PDF ein Artefakt-Wasserzeichen hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs.Watermark für .NET mühelos Artefakt-Wasserzeichen zu PDF-Dateien hinzufügen. Schützen Sie Ihre Dokumente ganz einfach.
weight: 11
url: /de/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Einführung
Das Hinzufügen von Wasserzeichen zu PDF-Dateien ist ein entscheidender Aspekt der Dokumentenverwaltung, insbesondere wenn es um den Schutz geistigen Eigentums oder das Branding von Dokumenten geht. Groupdocs.Watermark für .NET bietet eine robuste Lösung zum mühelosen Hinzufügen von Wasserzeichen zu PDF-Dateien. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess des Hinzufügens eines Artefaktwasserzeichens zu PDF-Dateien.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  Groupdocs.Watermark für .NET: Laden Sie Groupdocs.Watermark für .NET herunter und installieren Sie es von[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Entwicklungsumgebung: Richten Sie eine .NET-Entwicklungsumgebung ein.
3. PDF-Dokument: Bereiten Sie das PDF-Dokument vor, dem Sie das Wasserzeichen hinzufügen möchten.
4. Ausgabeverzeichnis: Erstellen Sie ein Verzeichnis zum Speichern der mit Wasserzeichen versehenen PDF-Datei.

## Namensräume importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using GroupDocs.Watermark.Common;
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
## Schritt 2: Definieren Sie Wasserzeichenoptionen
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Schritt 3: Textwasserzeichen hinzufügen
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Schritt 4: Bildwasserzeichen hinzufügen
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Schritt 5: Speichern Sie das mit Wasserzeichen versehene PDF
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit Groupdocs.Watermark für .NET Artefakt-Wasserzeichen zu PDF-Dateien hinzufügt. Wenn Sie diese Schritte befolgen, können Sie Wasserzeichenfunktionen nahtlos in Ihre .NET-Anwendungen integrieren und so die Sicherheit und Integrität Ihrer Dokumente gewährleisten.
## FAQs
### Kann ich das Erscheinungsbild des Textwasserzeichens anpassen?
Ja, Sie können verschiedene Aspekte wie Schriftart, Größe, Farbe und Ausrichtung des Textwasserzeichens nach Ihren Wünschen anpassen.
### Unterstützt Groupdocs.Watermark das Hinzufügen von Wasserzeichen zu anderen Dokumentformaten?
Ja, Groupdocs.Watermark unterstützt das Hinzufügen von Wasserzeichen zu einer Vielzahl von Dokumentformaten, darunter Word, Excel, PowerPoint und mehr.
### Gibt es eine Testversion für Groupdocs.Watermark für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Wie kann ich Unterstützung bei Problemen oder Fragen im Zusammenhang mit Groupdocs.Watermark erhalten?
 Unterstützung erhalten Sie im Groupdocs-Community-Forum[Hier](https://forum.groupdocs.com/c/watermark/19).
### Kann ich Groupdocs.Watermark für kommerzielle Zwecke nutzen?
Ja, Sie können eine Lizenz für die kommerzielle Nutzung erwerben[Hier](https://purchase.groupdocs.com/buy).