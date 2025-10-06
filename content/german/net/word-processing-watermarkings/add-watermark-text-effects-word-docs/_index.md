---
title: Fügen Sie Wasserzeichen mit Texteffekten in Word-Dokumenten hinzu
linktitle: Fügen Sie Wasserzeichen mit Texteffekten in Word-Dokumenten hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET benutzerdefinierte Wasserzeichen mit Texteffekten zu Word-Dokumenten hinzufügen. Dokumentensicherheit und optische Attraktivität mühelos.
weight: 21
url: /de/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
type: docs
---
# Fügen Sie Wasserzeichen mit Texteffekten in Word-Dokumenten hinzu

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET ein Wasserzeichen mit Texteffekten zu Word-Dokumenten hinzufügen. Wenn Sie diese Schritt-für-Schritt-Anleitung befolgen, können Sie Ihre Dokumente mit benutzerdefinierten Wasserzeichen mit verschiedenen Texteffekten aufwerten.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Watermark für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie[Webseite](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentpfad: Informieren Sie sich über den Pfad des Word-Dokuments, dem Sie das Wasserzeichen hinzufügen möchten.
3. Ausgabeverzeichnis: Legen Sie ein Verzeichnis fest, in dem Sie das geänderte Dokument speichern möchten.

## Namespaces importieren
Stellen Sie sicher, dass Sie die erforderlichen Namespaces importieren, um auf die erforderlichen Klassen und Methoden zuzugreifen:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
Laden Sie das Word-Dokument, dem Sie das Wasserzeichen hinzufügen möchten.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Code für das Hinzufügen von Wasserzeichen finden Sie hier
}
```
## Schritt 2: Wasserzeichen mit Texteffekten hinzufügen
Erstellen Sie ein Textwasserzeichen mit dem gewünschten Text und der gewünschten Schriftart und definieren Sie dann Texteffekte wie das Linienformat.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Schritt 3: Passen Sie die Wasserzeichenoptionen an
Definieren Sie Optionen für Wasserzeichenabschnitte, z. B. Texteffekte, und weisen Sie diese dem Wasserzeichen zu.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Schritt 4: Speichern Sie das Dokument
Speichern Sie das geänderte Dokument mit dem hinzugefügten Wasserzeichen.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Das Hinzufügen von Wasserzeichen mit Texteffekten zu Word-Dokumenten kann deren visuelle Attraktivität und den Schutz erheblich verbessern. Mit GroupDocs.Watermark für .NET wird dieser Prozess rationalisiert und anpassbar, sodass Sie professionell aussehende Dokumente effizient erstellen können.
## FAQs
### Kann ich Schriftart und Größe des Wasserzeichentextes anpassen?
Ja, Sie können beim Erstellen des TextWatermark-Objekts Schriftart und -größe angeben.
### Ist es möglich, einem einzelnen Dokument mehrere Wasserzeichen hinzuzufügen?
Auf jeden Fall unterstützt GroupDocs.Watermark für .NET das Hinzufügen mehrerer Wasserzeichen mit unterschiedlichen Einstellungen zu einem einzelnen Dokument.
### Unterstützt GroupDocs.Watermark neben Word auch andere Dokumentformate?
Ja, es unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Excel, PowerPoint und mehr.
### Kann ich ein Wasserzeichen entfernen, nachdem es einem Dokument hinzugefügt wurde?
Ja, die Bibliothek bietet Methoden zum einfachen Entfernen von Wasserzeichen aus Dokumenten.
### Gibt es zu Testzwecken eine Testversion?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).