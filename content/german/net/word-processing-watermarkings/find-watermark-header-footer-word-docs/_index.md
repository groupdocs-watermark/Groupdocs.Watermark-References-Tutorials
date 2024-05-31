---
title: Suchen Sie nach Wasserzeichen in der Kopf-/Fußzeile von Word-Dokumenten
linktitle: Suchen Sie nach Wasserzeichen in der Kopf-/Fußzeile von Word-Dokumenten
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs Watermark für .NET effizient Wasserzeichen aus Word-Dokumenten finden und entfernen und so die Integrität und Professionalität von Dokumenten gewährleisten.
type: docs
weight: 22
url: /de/net/word-processing-watermarkings/find-watermark-header-footer-word-docs/
---
## Einführung
In der Welt der Dokumentenverwaltung und des Dokumentenschutzes spielen Wasserzeichen eine zentrale Rolle. Ob für Branding-Zwecke, Urheberrechtsschutz oder Dokumentenverfolgung: Das Hinzufügen von Wasserzeichen zu Ihren Dokumenten ist unerlässlich. Allerdings kann das effiziente Auffinden und Entfernen von Wasserzeichen, insbesondere in großen Dokumentensätzen, eine entmutigende Aufgabe sein. Hier kommt GroupDocs.Watermark für .NET ins Spiel. In diesem Tutorial befassen wir uns mit der Suche nach Wasserzeichen in Kopf- und Fußzeilen von Word-Dokumenten mit GroupDocs.Watermark für .NET und schlüsseln jeden Schritt auf, um ein umfassendes Verständnis zu gewährleisten.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. GroupDocs.Watermark für .NET: Stellen Sie sicher, dass die GroupDocs.Watermark für .NET-Bibliothek in Ihrer Entwicklungsumgebung installiert und konfiguriert ist. Sie können die Bibliothek herunterladen unter[Hier](https://releases.groupdocs.com/Watermark/net/).
2. Zugriff auf Word-Dokumente: Sie haben Zugriff auf die Word-Dokumente, die Wasserzeichen enthalten, die Sie bearbeiten möchten.
3. Grundkenntnisse von C#: Machen Sie sich mit den Grundlagen der Programmiersprache C# vertraut, da dieses Tutorial C#-Codefragmente beinhaltet.
## Namespaces importieren
Bevor Sie mit dem Code beginnen, importieren Sie die erforderlichen Namespaces:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Schritt 1: Definieren Sie den Dokumentpfad und den Namen der Ausgabedatei
Definieren Sie zunächst den Pfad des Dokuments, das das Wasserzeichen enthält, und den Namen der Ausgabedatei, in der das geänderte Dokument gespeichert wird.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Schritt 2: Watermarker initialisieren
 Initialisieren Sie die`Watermarker` Objekt mit dem Dokumentpfad und den Ladeoptionen.
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Code für die Wasserzeichenmanipulation finden Sie hier
}
```
## Schritt 3: Suchkriterien definieren
Definieren Sie die Suchkriterien, um das Wasserzeichen zu finden. Dies kann auf Bild oder Text basieren.
```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## Schritt 4: Suchen Sie nach Wasserzeichen
Suchen Sie mithilfe der definierten Suchkriterien nach Wasserzeichen in der primären Kopfzeile des Dokuments.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
PossibleWatermarkCollection possibleWatermarks = content.Sections[0]
                                                        .HeadersFooters[OfficeHeaderFooterType.HeaderPrimary]
                                                        .Search(textSearchCriteria.Or(imageSearchCriteria));
```
## Schritt 5: Wasserzeichen entfernen
Entfernen Sie alle gefundenen Wasserzeichen aus dem Dokument.
```csharp
for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
{
    possibleWatermarks.RemoveAt(i);
}
```
## Schritt 6: Dokument speichern
Speichern Sie das geänderte Dokument mit entfernten Wasserzeichen.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
GroupDocs.Watermark für .NET bietet eine robuste Lösung zum Suchen und Entfernen von Wasserzeichen aus Word-Dokumenten. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Wasserzeichen aus Kopf- und Fußzeilen effizient finden und entfernen und so die Integrität und Professionalität Ihrer Dokumente sicherstellen.
## FAQs
### Ist GroupDocs.Watermark mit anderen Dokumentformaten kompatibel?
Ja, GroupDocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter Word, Excel, PowerPoint, PDF und mehr.
### Kann ich die Suchkriterien für Wasserzeichen anpassen?
Absolut, GroupDocs.Watermark bietet flexible Suchkriterien, die Ihnen die Suche nach Wasserzeichen basierend auf verschiedenen Parametern wie Text, Bild, Form oder Objekteigenschaften ermöglichen.
### Behält GroupDocs.Watermark die ursprüngliche Formatierung von Dokumenten bei?
Ja, GroupDocs.Watermark stellt sicher, dass die ursprüngliche Formatierung von Dokumenten erhalten bleibt und gleichzeitig Wasserzeichen entfernt werden, wodurch die Ästhetik und das Layout des Dokuments erhalten bleiben.
### Ist GroupDocs.Watermark für die Stapelverarbeitung von Dokumenten geeignet?
Natürlich bietet GroupDocs.Watermark APIs für die Stapelverarbeitung, sodass Sie problemlos mehrere Dokumente gleichzeitig bearbeiten können.
### Wo kann ich Hilfe oder Unterstützung für GroupDocs.Watermark suchen?
 Bei Fragen oder Unterstützung zu GroupDocs.Watermark können Sie die besuchen[GroupDocs.Watermark-Forum](https://forum.groupdocs.com/c/watermark/19) oder wenden Sie sich an das Support-Team.