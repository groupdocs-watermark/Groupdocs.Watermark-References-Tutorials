---
title: Extrahieren Sie Anmerkungsinformationen aus PDF
linktitle: Extrahieren Sie Anmerkungsinformationen aus PDF
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in dieser detaillierten Schritt-für-Schritt-Anleitung, wie Sie mit GroupDocs.Watermark für .NET Anmerkungsinformationen aus PDF-Dokumenten extrahieren.
weight: 23
url: /de/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
type: docs
---
# Extrahieren Sie Anmerkungsinformationen aus PDF

## Einführung
Müssen Sie häufig detaillierte Anmerkungsinformationen aus Ihren PDF-Dokumenten extrahieren? Unabhängig davon, ob Sie als Entwickler an Dokumentenmanagementsystemen arbeiten oder als Geschäftsmann zahlreiche PDF-Dateien bearbeiten, kann das effiziente Extrahieren und Verarbeiten von Anmerkungen von entscheidender Bedeutung sein. Mit GroupDocs.Watermark für .NET steht Ihnen ein leistungsstarkes Toolkit zur Verfügung, mit dem Sie diese Aufgabe einfach und effizient erledigen können.
## Voraussetzungen
Bevor wir uns mit dem Code befassen, stellen wir sicher, dass Sie über alles verfügen, was Sie für den Einstieg benötigen:
1. Visual Studio: Stellen Sie sicher, dass Visual Studio installiert ist. Dies wird unsere IDE zum Schreiben und Ausführen des Codes sein.
2.  GroupDocs.Watermark für .NET: Sie benötigen die GroupDocs.Watermark für .NET-Bibliothek. Du kannst[hier herunterladen](https://releases.groupdocs.com/Watermark/net/).
3. Grundkenntnisse in C#: Um den Beispielen folgen zu können, sind Kenntnisse in der C#-Programmierung erforderlich.
## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namensräume in Ihr Projekt importieren. Diese Namespaces enthalten die Klassen und Methoden, die zum Arbeiten mit PDF-Dateien und zum Extrahieren von Anmerkungen erforderlich sind.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Schritt 1: Richten Sie Ihr Projekt ein
Lassen Sie uns zunächst unser Projekt in Visual Studio einrichten. Erstellen Sie ein neues Konsolen-App-Projekt (.NET Core). Sobald Ihr Projekt erstellt ist, müssen Sie einen Verweis auf die GroupDocs.Watermark für .NET-Bibliothek hinzufügen.
1. Öffnen Sie den NuGet-Paketmanager.
2.  Suchen nach`GroupDocs.Watermark`.
3.  Installiere das`GroupDocs.Watermark` Paket.
## Schritt 2: Dokumentpfade definieren
Als Nächstes müssen Sie die Pfade für Ihr Eingabe-PDF-Dokument und das Ausgabeverzeichnis angeben, in dem die extrahierten Informationen gespeichert werden. Dadurch wird sichergestellt, dass Ihre Anwendung weiß, wo sich die PDF-Datei befindet und wo die Ergebnisse gespeichert werden müssen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Schritt 3: Laden Sie das PDF-Dokument
 Um mit dem PDF-Dokument arbeiten zu können, müssen wir es mit laden`PdfLoadOptions`. Diese Klasse bietet Optionen zum Konfigurieren des Ladevorgangs.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier finden Sie Code zum Extrahieren von Anmerkungen
}
```
## Schritt 4: Greifen Sie auf PDF-Inhalte zu
Sobald das Dokument geladen ist, können wir auf seinen Inhalt zugreifen. Insbesondere möchten wir den PDF-Inhalt abrufen, damit wir die Seiten und Anmerkungen durchlaufen können.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Schritt 5: Durchlaufen Sie Seiten und Anmerkungen
Mit dem vorliegenden PDF-Inhalt können wir jede Seite und dann jede Anmerkung auf diesen Seiten durchlaufen. Dadurch können wir die Informationen extrahieren, die wir benötigen.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Extrahieren Sie hier Anmerkungsdetails
    }
}
```
## Schritt 6: Anmerkungsdetails extrahieren
Innerhalb der verschachtelten Schleifen extrahieren wir verschiedene Details zu jeder Anmerkung. Dazu gehören die Art der Anmerkung, alle damit verbundenen Bilder, Texte und Positionsdaten.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Schritt 7: Extrahierte Daten speichern oder verarbeiten
Entscheiden Sie abschließend, was Sie mit den extrahierten Anmerkungsinformationen tun möchten. Sie können es je nach Bedarf auf der Konsole ausdrucken, in einer Datei speichern oder sogar in einer Datenbank speichern.
```csharp
// Beispiel für das Speichern der extrahierten Daten in einer Datei
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Abschluss
Das Extrahieren von Anmerkungsinformationen aus PDF-Dokumenten mit GroupDocs.Watermark für .NET ist ein unkomplizierter Vorgang, der Ihnen viel Zeit und Mühe sparen kann. Wenn Sie die in diesem Leitfaden beschriebenen Schritte befolgen, können Sie diese Funktionalität problemlos in Ihre Projekte integrieren und die Extraktion wertvoller Anmerkungsdaten automatisieren.
 Egal, ob Sie große Mengen an PDFs verwalten oder einfach nur bestimmte Informationen extrahieren müssen, GroupDocs.Watermark für .NET bietet eine zuverlässige und effiziente Lösung. Vergessen Sie nicht, sich das anzusehen[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) für erweiterte Funktionen und Anpassungsoptionen.
## FAQs
### Was ist GroupDocs.Watermark für .NET?
GroupDocs.Watermark für .NET ist eine umfassende Bibliothek, die es Entwicklern ermöglicht, Wasserzeichen in verschiedenen Dokumentformaten, einschließlich PDFs, Word-Dokumenten und Bildern, hinzuzufügen, zu suchen und zu entfernen.
### Kann ich GroupDocs.Watermark kostenlos testen?
 Ja, Sie können eine bekommen[Kostenlose Testphase](https://releases.groupdocs.com/) um die Funktionen der Bibliothek vor dem Kauf zu testen.
### Wie erhalte ich Unterstützung, wenn ich auf Probleme stoße?
 Sie können Unterstützung vom GroupDocs-Team erhalten, indem Sie dort vorbeischauen[Hilfeforum](https://forum.groupdocs.com/c/watermark/19).
### Ist es möglich, eine temporäre Lizenz zum Testen zu erhalten?
 Ja, Sie können eine beantragen[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)zu Testzwecken.
### Wo kann ich die Vollversion von GroupDocs.Watermark für .NET kaufen?
 Sie können die Vollversion bei erwerben[GroupDocs-Website](https://purchase.groupdocs.com/buy).