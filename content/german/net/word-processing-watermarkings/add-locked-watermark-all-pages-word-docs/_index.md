---
title: Fügen Sie allen Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu
linktitle: Fügen Sie allen Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu
second_title: GroupDocs.Watermark .NET-API
description: Sichern Sie Ihre Dokumente, indem Sie mit Groupdocs.Watermark für .NET gesperrte Wasserzeichen hinzufügen. Befolgen Sie unsere Schritt-für-Schritt-Anleitung für eine einfache Implementierung.
weight: 11
url: /de/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Fügen Sie allen Seiten in Word-Dokumenten ein gesperrtes Wasserzeichen hinzu

## Einführung
Das Hinzufügen von Wasserzeichen zu Ihren Dokumenten ist ein wichtiger Schritt zur Sicherung und zum Branding Ihrer Inhalte. Ganz gleich, ob Sie unbefugte Nutzung verhindern oder einfach nur eine professionelle Note verleihen möchten, Wasserzeichen können mehreren Zwecken dienen. In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens eines gesperrten Wasserzeichens zu allen Seiten eines Word-Dokuments mithilfe von Groupdocs.Watermark für .NET.
## Voraussetzungen
Bevor wir uns mit der Schritt-für-Schritt-Anleitung befassen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
1. Groupdocs.Watermark für .NET: Laden Sie die neueste Version herunter von[Hier](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
3. Entwicklungsumgebung: Eine Entwicklungsumgebung wie Visual Studio.
4.  Lizenz: Sie können sich für eine entscheiden[Kostenlose Testphase](https://releases.groupdocs.com/) oder kaufen Sie ein[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/).
## Namespaces importieren
Als Erstes müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Diese sind für den Zugriff auf die von Groupdocs.Watermark bereitgestellten Klassen und Methoden unerlässlich.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Richten Sie Ihr Projekt ein

Öffnen Sie Ihre Entwicklungsumgebung und erstellen Sie ein neues .NET-Projekt. Dies kann eine Konsolenanwendung oder ein anderer Typ sein, der Ihren Anforderungen entspricht.

Sie müssen das Paket Groupdocs.Watermark zu Ihrem Projekt hinzufügen. Dies kann über den NuGet Package Manager erfolgen. Führen Sie den folgenden Befehl in der NuGet Package Manager-Konsole aus:
```sh
Install-Package GroupDocs.Watermark
```
## Schritt 2: Laden Sie das Word-Dokument
### Definieren Sie den Dokumentpfad
Geben Sie den Pfad zu Ihrem Word-Dokument an. Dies ist das Dokument, in dem Sie das Wasserzeichen hinzufügen möchten.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Legen Sie die Ladeoptionen fest
 Erstellen Sie eine Instanz von`WordProcessingLoadOptions` um Ihr Word-Dokument mit bestimmten Optionen zu laden.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Schritt 3: Erstellen Sie das Wasserzeichen
### Wasserzeichen initialisieren
 Verwendung der`Watermarker`Klasse, laden Sie das Dokument mit den angegebenen Ladeoptionen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Weitere Schritte finden Sie in diesem using-Block
}
```
### Definieren Sie Wasserzeicheneigenschaften
 Ein ... kreieren`TextWatermark` Instanz mit dem gewünschten Text, der gewünschten Schriftart und der gewünschten Farbe.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Schritt 4: Wasserzeichen auf alle Seiten anwenden
### Legen Sie die Wasserzeichenoptionen fest
 Definieren`WordProcessingWatermarkPagesOptions` und stellen Sie die ein`IsLocked` Setzen Sie die Eigenschaft auf „true“, um das Wasserzeichen zu sperren. Dadurch wird sichergestellt, dass das Wasserzeichen nicht einfach entfernt werden kann.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Optional: Passwortschutz hinzufügen
Wenn Sie eine zusätzliche Sicherheitsebene hinzufügen möchten, können Sie ein Passwort für das Wasserzeichen festlegen.
```csharp
// Mit Passwort schützen
// Optionen.Passwort = "7654321";
```
### Fügen Sie das Wasserzeichen hinzu
 Benutzen Sie die`Add` Methode der`Watermarker` Klasse, um das Wasserzeichen mit den angegebenen Optionen zum Dokument hinzuzufügen.
```csharp
watermarker.Add(watermark, options);
```
## Schritt 5: Speichern Sie das Dokument
Speichern Sie abschließend das geänderte Dokument in der angegebenen Ausgabedatei.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Wenn Sie diese Schritte befolgen, können Sie mit Groupdocs.Watermark für .NET ganz einfach allen Seiten Ihrer Word-Dokumente ein gesperrtes Wasserzeichen hinzufügen. Dies trägt nicht nur dazu bei, Ihre Dokumente vor unbefugter Nutzung zu schützen, sondern verleiht Ihren Inhalten auch eine professionelle Note. Groupdocs.Watermark bietet eine umfassende Lösung für Wasserzeichenanforderungen und stellt sicher, dass Ihre Dokumente sicher und gebrandet bleiben.
## FAQs
### Kann ich ein Bild als Wasserzeichen anstelle von Text verwenden?
 Ja, Groupdocs unterstützt sowohl Text- als auch Bildwasserzeichen. Sie können ersetzen`TextWatermark` mit`ImageWatermark` und geben Sie Ihr Bild an.
### Ist es möglich, die Position des Wasserzeichens anzupassen?
 Absolut! Sie können die Position des Wasserzeichens mithilfe von Eigenschaften wie festlegen`HorizontalAlignment` Und`VerticalAlignment`.
### Kann ich auf verschiedenen Seiten des Dokuments unterschiedliche Wasserzeichen anwenden?
 Ja, Sie können Wasserzeichen für bestimmte Seiten anpassen`PageIndex` Eigentum in der`WordProcessingWatermarkPagesOptions`.
### Unterstützt Groupdocs.Watermark neben Word auch andere Dokumentformate?
Ja, Groupdocs unterstützt verschiedene Formate, darunter PDF, Excel, PowerPoint und mehr.
### Welche Systemvoraussetzungen gelten für die Nutzung von Groupdocs.Watermark?
Sie benötigen ein System mit installiertem .NET Framework und einer Entwicklungsumgebung wie Visual Studio.