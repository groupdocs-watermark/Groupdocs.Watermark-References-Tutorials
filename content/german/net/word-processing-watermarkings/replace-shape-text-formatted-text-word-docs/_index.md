---
title: Ersetzen Sie Formtext durch formatierten Text in Word-Dokumenten
linktitle: Ersetzen Sie Formtext durch formatierten Text in Word-Dokumenten
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET Formtext durch formatierten Text in Word-Dokumenten ersetzen. Ihre Dokumentbearbeitungsfunktionen mühelos.
type: docs
weight: 34
url: /de/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Ersetzens von Formtext durch formatierten Text in Word-Dokumenten mithilfe von GroupDocs.Watermark für .NET. Diese Bibliothek bietet leistungsstarke Funktionen für die Arbeit mit Wasserzeichen, einschließlich des Ersetzens von Text innerhalb von Formen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Watermark für .NET: Stellen Sie sicher, dass Sie GroupDocs.Watermark für .NET installiert und eingerichtet haben. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentpfad: Sie sollten den Pfad zu dem Word-Dokument haben, in dem Sie den Text ersetzen möchten.

## Namespaces importieren
Importieren Sie vor dem Schreiben des Codes die erforderlichen Namespaces:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
 Laden Sie das Word-Dokument mit`Watermarker` Klasse:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ihr Code wird hier fortgesetzt ...
}
```
## Schritt 2: Inhalt abrufen und Text ersetzen
Sobald das Dokument geladen ist, rufen Sie den Inhalt ab und ersetzen Sie den Text innerhalb der Formen:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Schritt 3: Speichern Sie das Dokument
Speichern Sie nach dem Ersetzen des Textes das geänderte Dokument:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Abschluss
Mit GroupDocs für .NET wird das Ersetzen von Formtext durch formatierten Text in Word-Dokumenten vereinfacht. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Text in Ihren Dokumenten effizient verwalten und bearbeiten.

## FAQs
### Kann ich Text in anderen Dokumenttypen mit GroupDocs.Watermark für .NET ersetzen?
Ja, GroupDocs unterstützt verschiedene Dokumentformate wie PDF, Excel, PowerPoint und mehr.
### Ist GroupDocs.Watermark mit .NET Core kompatibel?
Ja, GroupDocs.Watermark unterstützt sowohl .NET Framework als auch .NET Core.
### Bietet GroupDocs.Watermark Unterstützung für das Hinzufügen von Bildern als Wasserzeichen?
Absolut, mit GroupDocs.Watermark können Sie Ihren Dokumenten sowohl Text- als auch Bildwasserzeichen hinzufügen.
### Kann ich das Erscheinungsbild der mit GroupDocs.Watermark hinzugefügten Wasserzeichen anpassen?
Ja, Sie haben die volle Kontrolle über das Aussehen, die Position und andere Eigenschaften der Wasserzeichen.
### Gibt es eine Testversion für GroupDocs.Watermark für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.groupdocs.com/).