---
title: Textwasserzeichen hinzufügen
linktitle: Textwasserzeichen hinzufügen
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Groupdocs Watermark für .NET Textwasserzeichen zu Ihren Dokumenten hinzufügen.
weight: 11
url: /de/net/watermarking-basics/add-text-watermark/
---

# Textwasserzeichen hinzufügen

## Einführung
GroupDocs.Watermark für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Wasserzeichen in verschiedenen Dokumentformaten in .NET-Anwendungen hinzuzufügen, zu suchen und zu entfernen. In diesem Tutorial konzentrieren wir uns auf das Hinzufügen eines Textwasserzeichens zu einem Dokument mithilfe von GroupDocs.Watermark.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Grundkenntnisse der Programmiersprache C#.
2. Visual Studio ist auf Ihrem System installiert.
3.  GroupDocs.Watermark für .NET-Bibliothek installiert. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/Watermark/net/).

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Schritt 1: Dokumentpfad und Ausgabeverzeichnis definieren
Definieren Sie den Pfad zu Ihrem Eingabedokument und das Ausgabeverzeichnis, in dem das mit Wasserzeichen versehene Dokument gespeichert wird.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Ersetzen`"Your Document Path"` mit dem absoluten oder relativen Pfad zu Ihrem Eingabedokument, zum Beispiel:`@"C:\Docs\document.pdf"`. Geben Sie außerdem das Verzeichnis an, in dem Sie das mit Wasserzeichen versehene Dokument speichern möchten.
## Schritt 2: Textwasserzeichen hinzufügen
 Instanziieren Sie die`Watermarker` Klasse mit dem Eingabedokumentpfad. Erstellen Sie dann eine`TextWatermark` Objekt mit den gewünschten Text- und Schriftarteinstellungen.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Watermark für .NET einem Dokument ein Textwasserzeichen hinzufügt. Mit seiner intuitiven API können Entwickler Wasserzeichen in verschiedenen Dokumentformaten einfach bearbeiten.
## FAQs
### Ist GroupDocs.Watermark für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und viele mehr.
### Kann ich das Erscheinungsbild des Textwasserzeichens anpassen?
Ja, Sie können verschiedene Eigenschaften wie Schriftart, Farbe, Ausrichtung und Deckkraft des Textwasserzeichens anpassen.
### Bietet GroupDocs.Watermark Unterstützung für das Entfernen von Wasserzeichen aus Dokumenten?
Ja, GroupDocs.Watermark bietet Funktionen zum Suchen und Entfernen von Wasserzeichen aus Dokumenten.
### Kann ich GroupDocs.Watermark für .NET vor dem Kauf testen?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Watermark?
 Sie können technischen Support erhalten, indem Sie die besuchen[GroupDocs.Watermark-Forum](https://forum.groupdocs.com/c/watermark/19).