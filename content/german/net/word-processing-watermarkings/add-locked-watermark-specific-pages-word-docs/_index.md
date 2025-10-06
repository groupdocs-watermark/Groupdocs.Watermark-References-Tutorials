---
title: Fügen Sie bestimmten Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu
linktitle: Fügen Sie bestimmten Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in unserer einfachen Schritt-für-Schritt-Anleitung, wie Sie mit GroupDocs.Watermark für .NET bestimmten Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzufügen.
weight: 12
url: /de/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Fügen Sie bestimmten Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu

## Einführung
Möchten Sie bestimmten Seiten in Ihren Word-Dokumenten ein Wasserzeichen hinzufügen, möchten es aber sperren, damit es nicht einfach entfernt oder bearbeitet werden kann? Hier sind Sie richtig! In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens eines gesperrten Wasserzeichens zu bestimmten Seiten in Word-Dokumenten mithilfe von GroupDocs.Watermark für .NET. Diese leistungsstarke Bibliothek erleichtert das Anwenden, Verwalten und Anpassen von Wasserzeichen auf eine Vielzahl von Dokumenttypen. Ganz gleich, ob Sie Entwickler sind oder nur jemand, der seine Dokumente schützen muss, dieser Leitfaden führt Sie auf unkomplizierte Weise durch jeden Schritt.
## Voraussetzungen
Bevor wir uns mit dem Tutorial befassen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
1.  GroupDocs.Watermark für .NET: Das können Sie[herunterladen](https://releases.groupdocs.com/Watermark/net/) Die neueste version.
2. Entwicklungsumgebung: Eine IDE wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind hilfreich.
4. Dokument in Wasserzeichen umwandeln: Ein Word-Dokument (.docx oder .doc), dem Sie ein Wasserzeichen hinzufügen möchten.
## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die für die Arbeit mit GroupDocs.Watermark erforderlich sind.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nachdem wir nun die Voraussetzungen erfüllt und die erforderlichen Namespaces importiert haben, wollen wir den Prozess Schritt für Schritt aufschlüsseln.
## Schritt 1: Laden Sie das Word-Dokument
 Zunächst müssen Sie das Word-Dokument laden, dem Sie ein Wasserzeichen hinzufügen möchten. Dies kann mit der erfolgen`Watermarker` Klasse zusammen mit`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Fahren Sie mit den nächsten Schritten fort
}
```
## Schritt 2: Erstellen Sie das Textwasserzeichen
Als nächstes erstellen Sie ein Textwasserzeichen. Sie können Text, Schriftart, Farbe und andere Eigenschaften entsprechend Ihren Anforderungen anpassen.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Schritt 3: Wasserzeichenoptionen konfigurieren
 Um das Wasserzeichen auf bestimmte Seiten anzuwenden und zu sperren, konfigurieren Sie das`WordProcessingWatermarkPagesOptions`Hier legen Sie die Seitenzahlen fest, auf denen das Wasserzeichen erscheinen soll, und legen die Sperroptionen fest.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Geben Sie die Seiten an
options.IsLocked = true; // Sperren Sie das Wasserzeichen
options.LockType = WordProcessingLockType.AllowOnlyComments; // Sperrtyp einstellen
// Zum Schutz mit einem Passwort
// Optionen.Passwort = "7654321";
```
## Schritt 4: Fügen Sie dem Dokument das Wasserzeichen hinzu
Nachdem Sie Ihr Wasserzeichen und Ihre Optionen konfiguriert haben, können Sie nun das Wasserzeichen zum Dokument hinzufügen.
```csharp
watermarker.Add(watermark, options);
```
## Schritt 5: Speichern Sie das Dokument
Speichern Sie abschließend das Dokument mit dem angewendeten Wasserzeichen. Wählen Sie einen geeigneten Ausgabepfad und speichern Sie die Datei.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Abschluss
Glückwunsch! Sie haben mit GroupDocs.Watermark für .NET erfolgreich ein gesperrtes Wasserzeichen zu bestimmten Seiten in einem Word-Dokument hinzugefügt. In diesem Tutorial wurden alle wesentlichen Schritte vom Laden des Dokuments bis zum Speichern der mit Wasserzeichen versehenen Datei behandelt. Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Dokumente sicher mit Wasserzeichen versehen sind und Ihre Inhalte so vor unbefugter Bearbeitung und Nutzung geschützt sind.
 Weitere Informationen finden Sie im[GroupDocs.Watermark-Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) . Wenn Sie Fragen haben oder weitere Hilfe benötigen, besuchen Sie bitte die[Hilfeforum](https://forum.groupdocs.com/c/watermark/19).
## FAQs
### Was ist GroupDocs.Watermark für .NET?
GroupDocs.Watermark für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Wasserzeichen zu verschiedenen Dokumenttypen hinzuzufügen, darunter Word, PDF, Excel und mehr.
### Kann ich Wasserzeichen auf mehrere Seiten in einem Dokument anwenden?
 Ja, Sie können im Dokument mehrere Seitenzahlen angeben`PageNumbers` Array zum Anwenden von Wasserzeichen auf mehrere Seiten.
### Wie schütze ich ein Wasserzeichen mit einem Passwort?
 Sie können ein Wasserzeichen mit einem Passwort schützen, indem Sie das festlegen`Password` Eigentum in der`WordProcessingWatermarkPagesOptions`.
### Ist es möglich, das Erscheinungsbild des Wasserzeichens anzupassen?
Absolut! Sie können Text, Schriftart, Farbe, Größe und andere Eigenschaften des Wasserzeichens an Ihre Bedürfnisse anpassen.
### Wo kann ich eine temporäre Lizenz für GroupDocs.Watermark erhalten?
 Eine temporäre Lizenz erhalten Sie bei[Hier](https://purchase.groupdocs.com/temporary-license/).