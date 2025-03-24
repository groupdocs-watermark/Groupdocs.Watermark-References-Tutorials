---
title: Dokument von der lokalen Festplatte laden
linktitle: Dokument von der lokalen Festplatte laden
second_title: GroupDocs.Watermark .NET-API
description: Schützen und verwalten Sie Ihre Dokumente mit Groupdocs für .NET. Befolgen Sie unsere detaillierte Anleitung, um Wasserzeichen nahtlos hinzuzufügen.
weight: 10
url: /de/net/document-loadings/load-document-from-local-disk/
---
## Einführung
Das Anbringen von Wasserzeichen an Dokumenten ist im heutigen digitalen Zeitalter unerlässlich, um den Schutz von Inhalten, die Geltendmachung von Eigentumsrechten und die Vertraulichkeit sicherzustellen. Groupdocs.Watermark für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Wasserzeichen in verschiedenen Dokumentformaten hinzuzufügen, zu suchen und zu verwalten. In diesem Tutorial führen wir Sie mit detaillierten Schritt-für-Schritt-Anleitungen durch den Prozess der Verwendung von Groupdocs.Watermark für .NET zum Hinzufügen von Wasserzeichen zu Ihren Dokumenten.
## Voraussetzungen
Bevor Sie mit der Implementierung beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Visual Studio installiert: Sie benötigen Visual Studio oder eine andere kompatible .NET-IDE.
2.  Groupdocs.Watermark für .NET: Laden Sie die Bibliothek von herunter[Download-Link](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework 4.6.1 oder höher installiert haben.
4. Ein Beispieldokument: Bereiten Sie ein Beispieldokument vor, um den Wasserzeichenprozess zu testen.
## Namespaces importieren
Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Diese sind für den Zugriff auf die für die Wasserzeichenmarkierung erforderlichen Klassen und Methoden unerlässlich.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Schritt 1: Dokument von der lokalen Festplatte laden
Zuerst müssen Sie das Dokument von Ihrer lokalen Festplatte laden. Dieses Dokument wird dasjenige sein, dem Sie ein Wasserzeichen hinzufügen.
Definieren Sie den Pfad des Dokuments, das Sie mit einem Wasserzeichen versehen möchten.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Schritt 2: Ladeoptionen initialisieren
 Als nächstes initialisieren Sie die Ladeoptionen. Wenn Sie beispielsweise mit einem Word-Dokument arbeiten, verwenden Sie`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Schritt 3: Wasserzeichen erstellen und konfigurieren
 Jetzt erstellen Sie eine Instanz von`Watermarker` Klasse. Diese Instanz wird zum Verwalten und Anwenden von Wasserzeichen auf Ihr Dokument verwendet.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dieser Block enthält weitere Schritte zum Hinzufügen und Speichern des Wasserzeichens
}
```
## Schritt 4: Erstellen Sie ein Wasserzeichen
Erstellen Sie ein Textwasserzeichen. Dieses Wasserzeichen kann einen beliebigen Text Ihrer Wahl enthalten. Hier verwenden wir „Wasserzeichen testen“.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Schritt 5: Fügen Sie dem Dokument ein Wasserzeichen hinzu
Fügen Sie das erstellte Wasserzeichen mithilfe von zum Dokument hinzu`Add` Methode der`Watermarker` Klasse.
```csharp
watermarker.Add(watermark);
```
## Schritt 6: Speichern Sie das mit Wasserzeichen versehene Dokument
Speichern Sie abschließend das mit Wasserzeichen versehene Dokument im angegebenen Pfad.
```csharp
watermarker.Save(outputFileName);
```

## Abschluss
Das Hinzufügen von Wasserzeichen zu Ihren Dokumenten mit Groupdocs für .NET ist unkompliziert und effizient. Dieser Leitfaden hat Sie durch den gesamten Prozess geführt, von der Einrichtung Ihrer Umgebung bis zum Speichern eines mit Wasserzeichen versehenen Dokuments. Mit diesem leistungsstarken Tool können Sie sicherstellen, dass Ihre Dokumente geschützt und Ihr geistiges Eigentum geschützt sind. 
 Weitere Einzelheiten finden Sie unter[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) , und wenn Sie auf Probleme stoßen, wird die[Hilfeforum](https://forum.groupdocs.com/c/watermark/19) ist ein ausgezeichneter Ort für Hilfe. 
## FAQs
### Kann ich benutzerdefinierte Schriftarten für Wasserzeichen verwenden?
Ja, Groupdocs unterstützt benutzerdefinierte Schriftarten. Sie können jede auf Ihrem System installierte Schriftart angeben.
### Welche Arten von Dokumenten werden unterstützt?
Groupdocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter Word, Excel, PDF, PowerPoint und mehr.
### Wie kann ich ein Wasserzeichen aus einem Dokument entfernen?
 Du kannst den ... benutzen`Remove` Methode, die von der bereitgestellt wird`Watermarker` Klasse zum Entfernen von Wasserzeichen.
### Ist es möglich, Bildwasserzeichen hinzuzufügen?
 Ja, Sie können Bildwasserzeichen mit hinzufügen`ImageWatermark` Klasse.
### Kann ich Groupdocs.Watermark kostenlos testen?
 Auf jeden Fall können Sie eine herunterladen[Kostenlose Testphase](https://releases.groupdocs.com/) um die Bibliothek vor dem Kauf zu bewerten.