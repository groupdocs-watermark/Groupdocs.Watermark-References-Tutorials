---
title: Fügen Sie Wasserzeichen mit Formeinstellungen in Word-Dokumenten hinzu
linktitle: Fügen Sie Wasserzeichen mit Formeinstellungen in Word-Dokumenten hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs Watermark für .NET Wasserzeichen mit Formeinstellungen zu Word-Dokumenten hinzufügen. Schützen Sie Ihre Dokumente effektiv.
weight: 20
url: /de/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# Fügen Sie Wasserzeichen mit Formeinstellungen in Word-Dokumenten hinzu

## Einführung
In diesem Tutorial führen wir den Prozess des Hinzufügens eines Wasserzeichens mit Formeinstellungen zu Word-Dokumenten mithilfe von GroupDocs.Watermark für .NET durch.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Watermark für .NET installiert. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Grundkenntnisse der C#-Programmierung.
3. Ein Verständnis für die Verarbeitung von Word-Dokumenten.

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces importieren, um auf die erforderlichen Klassen und Methoden zuzugreifen.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
Laden Sie das Word-Dokument an der Stelle, an der Sie das Wasserzeichen hinzufügen möchten.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Der Wasserzeichen-Hinzufügungscode kommt hierher
}
```
## Schritt 2: Wasserzeichen hinzufügen
 Instanziieren Sie a`TextWatermark` Objekt und geben Sie den Text an, den Sie als Wasserzeichen verwenden möchten.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Schritt 3: Passen Sie die Wasserzeicheneinstellungen an
Legen Sie verschiedene Einstellungen für das Wasserzeichen fest, z. B. Ausrichtung, Drehwinkel, Farbe und Deckkraft.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Schritt 4: Definieren Sie die Optionen für den Wasserzeichenabschnitt
Definieren Sie Optionen für den Wasserzeichenabschnitt, z. B. den Formnamen und alternativen Text.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Schritt 5: Wasserzeichen zum Dokument hinzufügen
Fügen Sie das Wasserzeichen mit den angegebenen Optionen zum Dokument hinzu.
```csharp
watermarker.Add(watermark, options);
```
## Schritt 6: Speichern Sie das Dokument
Speichern Sie das Dokument mit dem hinzugefügten Wasserzeichen.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Das Hinzufügen von Wasserzeichen mit Formeinstellungen zu Word-Dokumenten mit GroupDocs Watermark für .NET ist ein unkomplizierter Vorgang. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Ihre Dokumente effektiv mit benutzerdefinierten Wasserzeichen schützen.
## FAQs
### Kann ich demselben Dokument mehrere Wasserzeichen hinzufügen?
Ja, Sie können demselben Dokument mehrere Wasserzeichen mit unterschiedlichen Einstellungen hinzufügen.
### Unterstützt GroupDocs.Watermark neben Word auch andere Dokumentformate?
Ja, GroupDocs.Watermark unterstützt verschiedene Dokumentformate, darunter Excel, PowerPoint, PDF und mehr.
### Kann ich das Erscheinungsbild des Wasserzeichens weiter anpassen?
Natürlich können Sie verschiedene Parameter wie Schriftgröße, Stil, Farbe und Position an Ihre Bedürfnisse anpassen.
### Gibt es eine Testversion für GroupDocs.Watermark für .NET?
 Ja, Sie können eine kostenlose Testversion von erhalten[Hier](https://releases.groupdocs.com/).
### Wo finde ich Unterstützung für GroupDocs.Watermark?
 Im GroupDocs-Forum finden Sie Unterstützung und können Fragen stellen[Hier](https://forum.groupdocs.com/c/watermark/19).