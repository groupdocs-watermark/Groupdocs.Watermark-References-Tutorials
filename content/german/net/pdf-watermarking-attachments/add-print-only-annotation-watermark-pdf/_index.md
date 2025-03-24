---
title: Fügen Sie dem PDF ein „Nur drucken“-Anmerkungswasserzeichen hinzu
linktitle: Fügen Sie dem PDF ein „Nur drucken“-Anmerkungswasserzeichen hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET nur druckfähige Anmerkungswasserzeichen zu PDFs hinzufügen. Verbessern Sie mühelos die Dokumentensicherheit und das Branding.
weight: 13
url: /de/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## Einführung
In diesem Tutorial befassen wir uns mit dem Prozess des Hinzufügens eines Nur-Druck-Anmerkungswasserzeichens zu einer PDF-Datei mithilfe von GroupDocs.Watermark für .NET. Das Versehen von Dokumenten mit Wasserzeichen ist ein entscheidender Aspekt der Dokumentensicherheit und des Brandings, und GroupDocs.Watermark bietet eine nahtlose Lösung für .NET-Entwickler, um dies zu erreichen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
- Grundlegendes Verständnis der Programmiersprache C#.
- Visual Studio ist auf Ihrem Computer installiert.
- GroupDocs.Watermark für .NET-Bibliothek in Ihrem Projekt installiert.

## Namespaces importieren
Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces importieren:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Laden Sie das Dokument
 Zunächst müssen Sie das PDF-Dokument laden, das Sie mit einem Wasserzeichen versehen möchten. Ersetzen`"Your Document Path"` mit dem Pfad zu Ihrer PDF-Datei und`"Your Document Directory"` mit dem Verzeichnis, in dem Sie die Ausgabedatei speichern möchten.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Wasserzeichencode wird hier hinzugefügt
}
```
## Schritt 2: Wasserzeichen hinzufügen
Erstellen Sie als Nächstes ein Textwasserzeichenobjekt mit dem gewünschten Text und der gewünschten Schriftart. Satz`isPrintOnly` Zu`true` um sicherzustellen, dass das Wasserzeichen nur sichtbar ist, wenn das Dokument gedruckt wird, nicht im Ansichtsmodus.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Schritt 3: Wasserzeichenoptionen konfigurieren
Definieren Sie Optionen für das Wasserzeichen, z. B. den Seitenindex, an dem das Wasserzeichen hinzugefügt werden soll, und geben Sie es als Nur-Druck-Anmerkung an.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Schritt 4: Wasserzeichen anwenden
Fügen Sie das Wasserzeichen mit den angegebenen Optionen zum Dokument hinzu und speichern Sie die Ausgabedatei.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Watermark für .NET ein Anmerkungswasserzeichen nur zum Drucken zu einem PDF-Dokument hinzufügt. Dies ermöglicht Entwicklern eine einfache Verbesserung der Dokumentensicherheit und des Brandings.
## FAQs
### Ist GroupDocs.Watermark mit anderen Dokumentformaten außer PDF kompatibel?
Ja, GroupDocs unterstützt verschiedene Dokumentformate wie Word, Excel, PowerPoint und Bilder.
### Kann ich das Erscheinungsbild des Wasserzeichens anpassen?
Natürlich bietet GroupDocs.Watermark umfangreiche Optionen zum Anpassen von Wasserzeichentext, Schriftart, Farbe, Größe und Positionierung.
### Bietet GroupDocs.Watermark Stapelverarbeitungsfunktionen?
Auf jeden Fall können Entwickler mithilfe der Stapelverarbeitungsfunktionen mehrere Dokumente gleichzeitig mit Wasserzeichen versehen.
### Gibt es eine Testversion für GroupDocs.Watermark?
Ja, Sie können über den bereitgestellten Link auf eine kostenlose Testversion von GroupDocs.Watermark zugreifen.
### Wie erhalte ich technischen Support für GroupDocs.Watermark?
Sie können technische Unterstützung im GroupDocs.Watermark-Forum anfordern, das unter dem bereitgestellten Support-Link verfügbar ist.