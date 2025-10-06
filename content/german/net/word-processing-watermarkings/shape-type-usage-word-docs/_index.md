---
title: Verwendung von Formtypen in Word-Dokumenten
linktitle: Verwendung von Formtypen in Word-Dokumenten
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie Formen in Word-Dokumenten mit GroupDocs.Watermark für .NET bearbeiten. Dieses Tutorial bietet Anleitungen für eine effiziente Dokumentenverarbeitung.
weight: 37
url: /de/net/word-processing-watermarkings/shape-type-usage-word-docs/
type: docs
---
# Verwendung von Formtypen in Word-Dokumenten

## Einführung
In diesem Tutorial erfahren Sie, wie Sie Formtypen in Word-Dokumenten mithilfe von GroupDocs.Watermark für .NET verwenden. Formen in Word-Dokumenten können variieren, und das Verständnis, wie man sie manipuliert, kann für verschiedene Dokumentverarbeitungsaufgaben von entscheidender Bedeutung sein.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1.  GroupDocs.Watermark für .NET-Bibliothek: Laden Sie die GroupDocs.Watermark für .NET-Bibliothek von herunter und installieren Sie sie[Download-Link](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentpfad: Halten Sie ein Word-Dokument zur Verarbeitung bereit.
3. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung mit .NET Framework-Unterstützung ein.

## Namespaces importieren
Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Diese Namespaces bieten Zugriff auf die erforderlichen Klassen und Methoden für die Arbeit mit Word-Dokumenten.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Schritt 1: Laden Sie das Dokument
Beginnen Sie mit dem Laden des Word-Dokuments in das Watermarker-Objekt. Stellen Sie sicher, dass Sie den Dokumentpfad und alle zusätzlichen Optionen angeben, die während des Ladevorgangs erforderlich sind.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Hier steht der Dokumentverarbeitungscode
}
```
## Schritt 2: Zugriff auf Dokumentinhalte
 Greifen Sie über den auf den Inhalt des geladenen Word-Dokuments zu`GetContent<WordProcessingContent>()` Methode. Dadurch erhalten Sie Zugriff auf Abschnitte, Absätze und Formen im Dokument.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Schritt 3: Durchlaufen Sie Abschnitte und Formen
Durchlaufen Sie jeden Abschnitt und jede Form im Dokument, um sie nach Bedarf zu überprüfen und zu bearbeiten.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Der Formmanipulationscode kommt hierher
    }
}
```
## Schritt 4: Überprüfen Sie die Formtypen
Suchen Sie innerhalb der Schleife nach bestimmten Formtypen mithilfe von`ShapeType` Eigentum. Dieses Beispiel zeigt die Identifizierung und Handhabung von diagonalen Ecken und abgerundeten Formen.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Hier kommt formspezifischer Manipulationscode zum Einsatz
}
```
## Schritt 5: Formen bearbeiten
Führen Sie Aktionen wie das Hinzufügen von Text, das Ändern der Formatierung oder das Anwenden visueller Änderungen auf die identifizierten Formen aus.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Schritt 6: Speichern Sie das Dokument
Sobald alle erforderlichen Änderungen vorgenommen wurden, speichern Sie das Dokument mit den vorgenommenen Änderungen in der angegebenen Ausgabedatei.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Das Bearbeiten von Formen in Word-Dokumenten kann für verschiedene Dokumentverarbeitungsaufgaben von entscheidender Bedeutung sein. Mit GroupDocs.Watermark für .NET können Sie Formen einfach identifizieren, ändern und manipulieren, um Ihre Anforderungen effizient zu erfüllen.
## FAQs
### Kann GroupDocs.Watermark für .NET neben Word auch andere Dokumentformate verarbeiten?
Ja, GroupDocs.Watermark für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Excel, PowerPoint und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs.Watermark für .NET?
 Ja, Sie können über die auf eine kostenlose Testversion zugreifen[Veröffentlichungsseite](https://releases.groupdocs.com/).
### Bietet GroupDocs.Watermark für .NET technischen Support?
 Ja, Sie können über das Hilfe suchen und mit der Community in Kontakt treten[Hilfeforum](https://forum.groupdocs.com/c/watermark/19).
### Kann ich den Wasserzeichenprozess an bestimmte Dokumentanforderungen anpassen?
Absolut, GroupDocs.Watermark für .NET bietet umfangreiche Anpassungsoptionen, um den Wasserzeichenprozess an Ihre Bedürfnisse anzupassen.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Watermark für .NET erhalten?
 Eine temporäre Lizenz können Sie bei erwerben[Seite zum Kauf einer temporären Lizenz](https://purchase.groupdocs.com/temporary-license/) zu Test- und Evaluierungszwecken.