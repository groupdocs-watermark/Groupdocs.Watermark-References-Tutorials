---
title: Fügen Sie Wasserzeichen zu Formbildern in Word-Dokumenten hinzu
linktitle: Fügen Sie Wasserzeichen zu Formbildern in Word-Dokumenten hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET Wasserzeichen hinzufügen, um Bilder in Word-Dokumenten zu formen. Erhöhen Sie die Dokumentensicherheit mit diesem Tutorial.
type: docs
weight: 17
url: /de/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET ein Wasserzeichen hinzufügen, um Bilder in Word-Dokumenten zu formen. Wasserzeichen sind ein entscheidender Aspekt des Dokumentenschutzes, insbesondere beim Umgang mit sensiblen oder vertraulichen Informationen. Durch das Hinzufügen von Wasserzeichen zur Gestaltung von Bildern können Sie die Integrität und Sicherheit Ihrer Dokumente gewährleisten.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Watermark für .NET: Laden Sie die GroupDocs.Watermark-Bibliothek von herunter und installieren Sie sie[Download-Seite](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Bereiten Sie das Word-Dokument vor, in das Sie das Wasserzeichen einfügen möchten.
3. Entwicklungsumgebung: Richten Sie Ihre bevorzugte .NET-Entwicklungsumgebung ein.
## Namespaces importieren
Stellen Sie vor dem Schreiben des Codes sicher, dass Sie die erforderlichen Namespaces importieren:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
Definieren Sie zunächst den Pfad zu Ihrem Dokument und geben Sie den Namen der Ausgabedatei an:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Schritt 2: Watermarker initialisieren
 Instanziieren Sie a`Watermarker` Objekt durch Angabe des Dokumentpfads und optionaler Ladeoptionen:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Fügen Sie hier Wasserzeichenlogik hinzu
}
```
## Schritt 3: Textwasserzeichen erstellen
Definieren Sie das Textwasserzeichen mit den gewünschten Eigenschaften wie Text, Schriftart, Ausrichtung, Drehung, Größe usw.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Schritt 4: Wasserzeichen auf Formbilder anwenden
Durchlaufen Sie die Dokumentabschnitte und Formen, um Formbilder zu identifizieren und das Wasserzeichen hinzuzufügen:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Schritt 5: Speichern Sie das Dokument
Speichern Sie das Dokument mit dem hinzugefügten Wasserzeichen in der angegebenen Ausgabedatei:
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Watermark für .NET Wasserzeichen hinzufügt, um Bilder in Word-Dokumenten zu formen. Indem Sie der Schritt-für-Schritt-Anleitung folgen und die leistungsstarken Funktionen von GroupDocs.Watermark nutzen, können Sie die Sicherheit und den Schutz Ihrer Dokumente effektiv verbessern.
## FAQs
### Kann ich das Erscheinungsbild des Wasserzeichentextes anpassen?
Ja, Sie können verschiedene Eigenschaften wie Schriftart, Größe, Farbe, Drehwinkel und Ausrichtung anpassen, um das Wasserzeichen Ihren Wünschen entsprechend anzupassen.
### Unterstützt GroupDocs.Watermark neben Word auch andere Dokumentformate?
Ja, GroupDocs.Watermark bietet Unterstützung für eine Vielzahl von Dokumentformaten, darunter PDF, Excel, PowerPoint und mehr.
### Ist es möglich, einem einzelnen Dokument mehrere Wasserzeichen hinzuzufügen?
Sie können auf jeden Fall mehrere Wasserzeichen mit unterschiedlichen Inhalten, Stilen und Positionen innerhalb desselben Dokuments hinzufügen.
### Kann ich mit GroupDocs.Watermark Wasserzeichen aus Dokumenten entfernen?
Ja, GroupDocs.Watermark bietet Funktionen zum effizienten Erkennen und Entfernen von Wasserzeichen aus Dokumenten.
### Bietet GroupDocs.Watermark plattformübergreifende Kompatibilität?
Ja, GroupDocs.Watermark ist mit .NET Framework, .NET Core und .NET Standard kompatibel und gewährleistet so eine nahtlose Integration über verschiedene Plattformen hinweg.