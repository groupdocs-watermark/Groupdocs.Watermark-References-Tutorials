---
title: Dokument in derselben Datei oder demselben Stream speichern
linktitle: Dokument in derselben Datei oder demselben Stream speichern
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs.Watermark für .NET Wasserzeichen zu Dokumenten hinzufügen. Dieses Handbuch enthält Anweisungen zur Gewährleistung des Schutzes und der Integrität von Dokumenten.
weight: 10
url: /de/net/document-savings/save-document-same-file-stream/
type: docs
---
# Dokument in derselben Datei oder demselben Stream speichern

## Einführung
Im heutigen digitalen Zeitalter ist das Hinzufügen von Wasserzeichen zu Dokumenten für den Schutz geistigen Eigentums und die Gewährleistung der Markenintegrität unerlässlich geworden. Groupdocs.Watermark für .NET bietet eine robuste Lösung für Entwickler, die Wasserzeichen nahtlos in Dokumente einbetten möchten. Diese umfassende Anleitung führt Sie durch die Schritte zum Speichern eines Dokuments mit einem Wasserzeichen in derselben Datei oder demselben Stream mithilfe von Groupdocs.Watermark für .NET.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Entwicklungsumgebung: Visual Studio auf Ihrem Computer installiert.
2. .NET Framework: Stellen Sie sicher, dass Sie über .NET Framework 4.0 oder höher verfügen.
3.  Groupdocs.Watermark für .NET: Laden Sie die neueste Version von herunter und installieren Sie sie[Website](https://releases.groupdocs.com/Watermark/net/).
4.  Lizenz: Besorgen Sie sich eine temporäre oder dauerhafte Lizenz von[Hier](https://purchase.groupdocs.com/temporary-license/).
## Namespaces importieren
Um Groupdocs.Watermark in Ihrem .NET-Projekt verwenden zu können, müssen Sie die erforderlichen Namespaces importieren:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Schritt 1: Richten Sie Ihr Projekt ein
Bevor wir unseren Dokumenten Wasserzeichen hinzufügen, müssen wir unser .NET-Projekt einrichten. Hier ist wie:
1. Erstellen Sie ein neues Projekt: Öffnen Sie Visual Studio und erstellen Sie eine neue Konsolenanwendung.
2. Groupdocs.Watermark-Referenz hinzufügen: Klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, wählen Sie „NuGet-Pakete verwalten“ und installieren Sie das Groupdocs.Watermark-Paket.
## Schritt 2: Kopieren Sie das Dokument an einen neuen Speicherort
Um eine direkte Änderung des Originaldokuments zu vermeiden, empfiehlt es sich, es zunächst an einen neuen Speicherort zu kopieren. So machen Sie es:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Schritt 3: Initialisieren Sie den Wassermarker
Nachdem wir nun unser Dokument kopiert haben, können wir die Watermarker-Klasse initialisieren, um unser Wasserzeichen hinzuzufügen:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Hier geht es zum Wasserzeichen
}
```
## Schritt 4: Erstellen Sie ein Textwasserzeichen und fügen Sie es hinzu
Als nächstes erstellen wir ein Textwasserzeichen und fügen es unserem Dokument hinzu:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Schritt 5: Speichern Sie das Dokument
Speichern Sie abschließend das Dokument mit dem angewendeten Wasserzeichen:
```csharp
watermarker.Save();
```
## Abschluss
Das Hinzufügen von Wasserzeichen zu Ihren Dokumenten mit Groupdocs für .NET ist unkompliziert und effizient. Indem Sie die oben beschriebenen Schritte befolgen, können Sie Ihre Dokumente mühelos schützen und ihre Integrität wahren. Weitere Einzelheiten finden Sie im[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/).
## FAQs
### Kann ich ein Bild als Wasserzeichen anstelle von Text verwenden?
Ja, mit Groupdocs.Watermark können Sie Bilder, Formen und Text als Wasserzeichen verwenden.
### Wie entferne ich ein Wasserzeichen aus einem Dokument?
 Sie können ein Wasserzeichen entfernen, indem Sie auf die Wasserzeichensammlung im Dokument zugreifen und die verwenden`Remove` Methode.
### Ist es möglich, das Erscheinungsbild des Wasserzeichens anzupassen?
Absolut. Sie können Schriftart, Größe, Farbe und Position des Wasserzeichens anpassen.
### Kann ich mehrere Wasserzeichen auf ein einzelnes Dokument anwenden?
 Ja, Sie können mehrere Wasserzeichen hinzufügen, indem Sie die aufrufen`Add` Methode mehrmals mit verschiedenen Wasserzeichenobjekten.
### Ist Groupdocs.Watermark mit allen Dokumentformaten kompatibel?
Groupdocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, DOCX, PPTX und viele andere.