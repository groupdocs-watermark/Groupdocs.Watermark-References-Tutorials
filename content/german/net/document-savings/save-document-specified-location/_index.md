---
title: Dokument am angegebenen Ort speichern
linktitle: Dokument am angegebenen Ort speichern
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit GroupDocs.Watermark für .NET ganz einfach Wasserzeichen zu Ihren Dokumenten hinzufügen. Verbessern Sie die Dokumentensicherheit.
weight: 11
url: /de/net/document-savings/save-document-specified-location/
---
## Einführung
Im digitalen Zeitalter ist die Sicherung von Dokumenten wichtiger denn je. Wasserzeichen sind eine wirksame Möglichkeit, Ihre Dokumente vor unbefugter Nutzung zu schützen. GroupDocs.Watermark für .NET bietet eine robuste Lösung zum Hinzufügen von Wasserzeichen zu Ihren Dokumenten. Egal, ob Sie ein Entwickler sind, der Wasserzeichen in Ihre Anwendung integrieren möchte, oder jemand, der Ihre Dokumente schützen möchte, dieses Tutorial führt Sie Schritt für Schritt durch den Prozess.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- .NET-Entwicklungsumgebung: Stellen Sie sicher, dass Visual Studio oder eine andere .NET-Entwicklungsumgebung installiert ist.
-  GroupDocs.Watermark für .NET-Bibliothek: Laden Sie die Bibliothek herunter und referenzieren Sie sie in Ihrem Projekt.[Laden Sie GroupDocs.Watermark für .NET herunter](https://releases.groupdocs.com/Watermark/net/)
- Grundkenntnisse der C#-Programmierung: Das Verständnis grundlegender C#-Programmierkonzepte ist hilfreich.
- Dokument zum Wasserzeichen: Halten Sie ein Beispieldokument bereit, auf das Sie das Wasserzeichen anwenden möchten.
## Namespaces importieren
Bevor wir mit dem Beispiel beginnen, müssen Sie die notwendigen Namespaces importieren. Fügen Sie oben in Ihrer Codedatei die folgenden using-Anweisungen hinzu:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Lassen Sie uns den Prozess des Hinzufügens eines Wasserzeichens zu einem Dokument mithilfe von GroupDocs.Watermark für .NET in überschaubare Schritte unterteilen. Befolgen Sie diese Schritte, um erfolgreich ein Wasserzeichen anzubringen und Ihr Dokument an einem angegebenen Speicherort zu speichern.
## Schritt 1: Richten Sie Ihr Projekt ein
Beginnen Sie mit der Erstellung eines neuen .NET-Projekts in Visual Studio. Der Einfachheit halber können Sie eine Konsolen-App wählen.
1. Öffnen Sie Visual Studio.
2.  Wählen`File` >`New` >`Project`.
3.  Wählen`Console App (.NET Core)` oder`Console App (.NET Framework)`.
4.  Benennen Sie Ihr Projekt und klicken Sie`Create`.

## Schritt 2: Bereiten Sie Ihr Dokument und Ihren Wasserzeichentext vor
### Geben Sie den Dokumentpfad an
Definieren Sie den Pfad des Dokuments, das Sie mit einem Wasserzeichen versehen möchten. Für dieses Beispiel verwenden wir einen Platzhalterpfad.
```csharp
string documentPath = "Your Document Path";
```
### Ausgabepfad definieren
Richten Sie den Ausgabepfad ein, in dem das mit Wasserzeichen versehene Dokument gespeichert werden soll.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Schritt 3: Laden Sie das Dokument
 Benutzen Sie die`Watermarker` Klasse zum Laden Ihres Dokuments. Diese Klasse stellt Methoden zum Hinzufügen, Entfernen und Bearbeiten von Wasserzeichen bereit.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Fügen Sie hier Wasserzeichenlogik hinzu
}
```
## Schritt 4: Erstellen Sie ein Wasserzeichen und fügen Sie es hinzu

### Erstellen Sie ein Textwasserzeichen
 Instanziieren Sie a`TextWatermark` Objekt mit den gewünschten Text- und Schriftarteigenschaften.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Wasserzeichen zum Dokument hinzufügen
 Fügen Sie das erstellte Wasserzeichen mit dem zu Ihrem Dokument hinzu`Add` Methode der`Watermarker` Klasse.
```csharp
watermarker.Add(watermark);
```
## Schritt 5: Speichern Sie das Dokument
Speichern Sie abschließend das Dokument mit dem Wasserzeichen am angegebenen Speicherort.
```csharp
watermarker.Save(outputFileName);
```
## Abschluss
Das Versehen Ihrer Dokumente mit Wasserzeichen mit GroupDocs für .NET ist ein unkomplizierter Prozess, der die Sicherheit Ihrer Dokumente erheblich verbessern kann. Wenn Sie dieser Schritt-für-Schritt-Anleitung folgen, können Sie ganz einfach Wasserzeichen zu Ihren Dokumenten hinzufügen und diese am gewünschten Ort speichern. Ganz gleich, ob Sie geistiges Eigentum schützen, die Authentizität von Dokumenten sicherstellen oder einfach nur eine professionelle Note hinzufügen möchten: GroupDocs.Watermark für .NET bietet die Tools, die Sie benötigen.
## FAQs
### Kann ich Bilder als Wasserzeichen mit GroupDocs.Watermark für .NET verwenden?
Ja, Sie können mit GroupDocs Watermark für .NET sowohl Text- als auch Bildwasserzeichen verwenden. Die Bibliothek unterstützt je nach Bedarf verschiedene Arten von Wasserzeichen.
### Gibt es eine kostenlose Testversion für GroupDocs.Watermark für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen[Webseite](https://releases.groupdocs.com/).
### Wie kann ich eine Lizenz für GroupDocs.Watermark für .NET erwerben?
 Sie können eine Lizenz bei erwerben[Kaufseite](https://purchase.groupdocs.com/buy).
### Unterstützt GroupDocs.Watermark für .NET Batch-Wasserzeichen?
Ja, Sie können mehrere Dokumente in einem Stapelprozess mit Wasserzeichen versehen, indem Sie eine Liste von Dokumenten durchlaufen und Wasserzeichen anwenden.
### Wo erhalte ich Unterstützung für GroupDocs.Watermark für .NET?
 Support gibt es auf der[GroupDocs-Forum](https://forum.groupdocs.com/c/watermark/19).