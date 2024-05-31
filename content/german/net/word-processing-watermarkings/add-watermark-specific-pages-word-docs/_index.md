---
title: Fügen Sie Wasserzeichen zu bestimmten Seiten in Word-Dokumenten hinzu
linktitle: Fügen Sie Wasserzeichen zu bestimmten Seiten in Word-Dokumenten hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs für .NET mühelos Wasserzeichen zu bestimmten Seiten in Word-Dokumenten hinzufügen. Verbessern Sie die Dokumentensicherheit und das Branding.
type: docs
weight: 18
url: /de/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## Einführung
In diesem Tutorial führen wir den Prozess des Hinzufügens von Wasserzeichen zu bestimmten Seiten in Word-Dokumenten mithilfe von Groupdocs.Watermark für .NET durch. Wasserzeichen sind ein entscheidender Aspekt der Dokumentenverwaltung und sorgen für Sicherheit und Branding Ihrer Dokumente. Mit Groupdocs.Watermark für .NET können Sie ganz einfach und effizient Text- oder Bildwasserzeichen zu Ihren Word-Dokumenten hinzufügen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  Groupdocs.Watermark für .NET: Laden Sie Groupdocs.Watermark für .NET herunter und installieren Sie es von[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Halten Sie das Word-Dokument bereit, das Sie mit einem Wasserzeichen versehen möchten.
3. Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung mit Visual Studio oder einem anderen .NET-Entwicklungstool ein.

## Namespaces importieren
Bevor wir uns mit dem Code befassen, importieren wir die erforderlichen Namespaces:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Schritt 1: Laden Sie das Dokument
Zuerst müssen wir das Word-Dokument in das Wasserzeichenobjekt laden.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier gelangen Sie zum Hinzufügen eines Wasserzeichencodes
}
```
## Schritt 2: Wasserzeichen hinzufügen
Fügen wir nun bestimmten Seiten des Dokuments ein Textwasserzeichen hinzu.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Geben Sie die Seiten an, denen das Wasserzeichen hinzugefügt werden soll
};
watermarker.Add(textWatermark);
```
## Schritt 3: Speichern Sie das Dokument
Speichern Sie abschließend das mit Wasserzeichen versehene Dokument am gewünschten Ort.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit Groupdocs.Watermark für .NET Wasserzeichen zu bestimmten Seiten in Word-Dokumenten hinzufügt. Mit nur wenigen Codezeilen können Sie die Sicherheit und das Branding Ihrer Dokumente mühelos verbessern.
## FAQs
### Kann ich einem einzelnen Dokument mehrere Wasserzeichen hinzufügen?
Ja, Sie können mehrere Wasserzeichen hinzufügen, indem Sie den Vorgang zum Hinzufügen von Wasserzeichen für jedes Wasserzeichen wiederholen.
### Unterstützt Groupdocs.Watermark neben Word auch andere Dokumentformate?
Ja, Groupdocs unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Excel, PowerPoint und mehr.
### Gibt es eine Testversion?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Kann ich das Erscheinungsbild des Wasserzeichens anpassen?
Natürlich können Sie verschiedene Aspekte des Wasserzeichens anpassen, z. B. Schriftart, Größe, Farbe und Deckkraft.
### Ist technischer Support verfügbar?
 Ja, technischen Support und Ressourcen finden Sie im Groupdocs-Forum[Hier](https://forum.groupdocs.com/c/watermark/19).