---
title: Dokument aus Stream laden
linktitle: Dokument aus Stream laden
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in dieser Anleitung, wie Sie mit GroupDocs.Watermark für .NET Wasserzeichen zu Dokumenten hinzufügen. Perfekt für Entwickler, die die Dokumentensicherheit verbessern möchten.
weight: 11
url: /de/net/document-loadings/load-document-from-stream/
---

# Dokument aus Stream laden

## Einführung
Möchten Sie Ihren Dokumenten mithilfe von .NET nahtlos Wasserzeichen hinzufügen? Suchen Sie nicht weiter! GroupDocs.Watermark für .NET ist eine leistungsstarke und benutzerfreundliche Bibliothek, mit der Sie Wasserzeichen in verschiedenen Dokumentformaten verwalten können. Egal, ob Sie mit PDFs, Word-Dokumenten oder Bildern arbeiten, mit diesem Tool sind Sie bestens gerüstet. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess des Ladens eines Dokuments aus einem Stream und des Hinzufügens eines Wasserzeichens. Also, lasst uns gleich eintauchen!
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
1. Visual Studio: Jede neuere Version von Visual Studio funktioniert einwandfrei.
2. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework 4.0 oder höher installiert haben.
3.  GroupDocs.Watermark für .NET: Sie können es herunterladen von[Hier](https://releases.groupdocs.com/Watermark/net/).
4. Grundkenntnisse in C#: Vertrautheit mit C# und objektorientierten Programmierkonzepten ist hilfreich.

## Namespaces importieren
Um GroupDocs.Watermark in Ihrem Projekt verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. Dadurch können Sie problemlos auf die Funktionen der Bibliothek zugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Schritt 1: Einrichten Ihres Projekts
Als Erstes müssen Sie Ihr Projekt in Visual Studio einrichten. So machen Sie es:
1. Erstellen Sie ein neues Projekt: Öffnen Sie Visual Studio und erstellen Sie ein neues C#-Konsolenanwendungsprojekt.
2.  GroupDocs.Watermark installieren: Installieren Sie die GroupDocs.Watermark-Bibliothek über den NuGet Package Manager. Einfach suchen`GroupDocs.Watermark` und installieren Sie es.
## Schritt 2: Dokumentpfade definieren
Als Nächstes müssen Sie die Pfade für Ihr Dokument und die Ausgabedatei definieren, in der das mit Wasserzeichen versehene Dokument gespeichert wird.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Ersetzen`"Your Document Path"` mit dem tatsächlichen Pfad des Dokuments, das Sie mit einem Wasserzeichen versehen möchten, und`"Your Document Directory"` mit dem Verzeichnis, in dem Sie das mit Wasserzeichen versehene Dokument speichern möchten.
## Schritt 3: Laden Sie das Dokument aus einem Stream
Laden wir nun das Dokument aus einem Stream. Dazu müssen Sie das Dokument als Stream öffnen und dann verwenden`Watermarker` Klasse aus der GroupDocs.Watermark-Bibliothek, um es zu verwalten.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Hier finden Sie Ihren Code zum Verwalten von Wasserzeichen
}
```
 Dieses Code-Snippet stellt sicher, dass das Dokument als Stream geöffnet wird und die`Watermarker` Die Klasse wird mit diesem Stream initialisiert. Der`using` Erklärungen stellen sicher, dass Ressourcen nach Gebrauch ordnungsgemäß entsorgt werden.
## Schritt 4: Erstellen Sie ein Wasserzeichen und fügen Sie es hinzu
Mit GroupDocs.Watermark ist das Erstellen eines Wasserzeichens ganz einfach. In diesem Beispiel erstellen wir ein einfaches Textwasserzeichen.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Hier erstellen wir eine`TextWatermark` Objekt mit dem Text „Wasserzeichen testen“ und geben Sie die Schriftartdetails an. Anschließend fügen wir dieses Wasserzeichen mithilfe von zum Dokument hinzu`Add` Methode der`Watermarker` Klasse.
## Schritt 5: Speichern Sie das mit Wasserzeichen versehene Dokument
Speichern Sie abschließend das mit Wasserzeichen versehene Dokument im angegebenen Ausgabepfad.
```csharp
watermarker.Save(outputFileName);
```
 Dieser Code speichert das Dokument mit dem neu hinzugefügten Wasserzeichen`outputFileName` Pfad, den Sie zuvor definiert haben.

## Abschluss
Glückwunsch! Sie haben Ihrem Dokument mit GroupDocs.Watermark für .NET erfolgreich ein Wasserzeichen hinzugefügt. Diese Bibliothek macht es unglaublich einfach, Wasserzeichen in einer Vielzahl von Dokumentformaten zu verwalten. Unabhängig davon, ob Sie Text, Bilder oder andere Arten von Wasserzeichen hinzufügen müssen, GroupDocs.Watermark verfügt über die Tools, die Sie benötigen. Vergessen Sie nicht, sich das anzusehen[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) für erweiterte Funktionen und Anpassungsoptionen.
## FAQs
### Welche Arten von Wasserzeichen kann ich mit GroupDocs.Watermark für .NET hinzufügen?
Sie können Textwasserzeichen, Bildwasserzeichen und sogar komplexe Formen und Logos hinzufügen. Die Bibliothek unterstützt eine Vielzahl von Anpassungsoptionen.
### Kann ich mit GroupDocs.Watermark Wasserzeichen aus Dokumenten entfernen?
Ja, mit GroupDocs.Watermark können Sie auch vorhandene Wasserzeichen aus Dokumenten entfernen.
### Gibt es eine kostenlose Testversion für GroupDocs.Watermark?
 Ja, Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.groupdocs.com/).
### Wie erwerbe ich eine Lizenz für GroupDocs.Watermark?
Sie können eine Lizenz direkt bei erwerben[GroupDocs-Website](https://purchase.groupdocs.com/buy).
### Wo kann ich Unterstützung erhalten, wenn ich auf Probleme stoße?
 Für Unterstützung können Sie die besuchen[GroupDocs.Watermark-Supportforum](https://forum.groupdocs.com/c/watermark/19).