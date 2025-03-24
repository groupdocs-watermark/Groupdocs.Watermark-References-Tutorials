---
title: Dokumentvorschau generieren
linktitle: Dokumentvorschau generieren
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in diesem Handbuch, wie Sie mit GroupDocs.Watermark für .NET Dokumentvorschauen erstellen. Verbessern Sie mühelos die Sicherheit und Verwaltung Ihrer Dokumente.
weight: 10
url: /de/net/document-manipulation/generate-document-preview/
---

# Dokumentvorschau generieren

## Einführung
In der Welt des digitalen Dokumentenmanagements spielen Wasserzeichen eine entscheidende Rolle bei der Gewährleistung der Sicherheit und Authentizität von Dokumenten. GroupDocs.Watermark für .NET ist ein leistungsstarkes Tool, mit dem Entwickler mühelos Wasserzeichen zu Dokumenten hinzufügen können. In diesem Tutorial führen wir Sie durch den Prozess der Erstellung von Dokumentvorschauen mit GroupDocs.Watermark für .NET. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieser Leitfaden bietet Ihnen einen umfassenden Schritt-für-Schritt-Prozess, um Ihr Ziel zu erreichen.
## Voraussetzungen
Bevor wir uns mit der Implementierung befassen, stellen wir sicher, dass Sie über alles verfügen, was Sie für den Einstieg benötigen:
- Ein grundlegendes Verständnis von C# und .NET Framework.
- Visual Studio ist auf Ihrem Computer installiert.
- GroupDocs.Watermark für .NET-Bibliothek. Du kannst[hier herunterladen](https://releases.groupdocs.com/Watermark/net/).
-  Eine gültige Lizenz für GroupDocs.Watermark. Sie können es entweder kaufen[Hier](https://purchase.groupdocs.com/buy) oder besorgen Sie sich ein[temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) zu Auswertungszwecken.
## Namespaces importieren
Um GroupDocs.Watermark in Ihrem Projekt verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. Dies können Sie erreichen, indem Sie die folgenden using-Anweisungen zu Ihrem Code hinzufügen:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die zum Markieren von Wasserzeichen und zum Generieren von Dokumentvorschauen erforderlich sind.

Lassen Sie uns den Prozess der Erstellung einer Dokumentvorschau in einfache, leicht verständliche Schritte unterteilen.
## Schritt 1: Richten Sie Ihr Projekt ein
Das Wichtigste zuerst: Richten Sie Ihr .NET-Projekt in Visual Studio ein. Wenn Sie noch kein Projekt haben, erstellen Sie ein neues, indem Sie die folgenden Schritte ausführen:
1. Öffnen Sie Visual Studio.
2. Klicken Sie auf „Neues Projekt erstellen“.
3. Wählen Sie „Konsolen-App (.NET Core)“ und klicken Sie auf „Weiter“.
4. Benennen Sie Ihr Projekt, wählen Sie einen Speicherort aus und klicken Sie dann auf „Erstellen“.
## Schritt 2: Installieren Sie GroupDocs.Watermark für .NET
Um GroupDocs.Watermark in Ihrem Projekt verwenden zu können, müssen Sie die Bibliothek installieren. Dies kann mit dem NuGet Package Manager erfolgen:
1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt.
2. Wählen Sie „NuGet-Pakete verwalten“.
3. Suchen Sie auf der Registerkarte „Durchsuchen“ nach „GroupDocs.Watermark“.
4. Klicken Sie auf „Installieren“, um die Bibliothek zu Ihrem Projekt hinzuzufügen.
Alternativ können Sie es über die Package Manager-Konsole installieren:
```powershell
Install-Package GroupDocs.Watermark
```
## Schritt 3: Definieren Sie den Dokumentpfad und das Ausgabeverzeichnis
Bevor Sie die Vorschau erstellen, müssen Sie den Pfad des Dokuments angeben, das Sie in der Vorschau anzeigen möchten, sowie das Verzeichnis, in dem die Vorschaubilder gespeichert werden:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Ersetzen Sie „Ihr Dokumentpfad“ durch den Pfad zu Ihrem Dokument und „Ihr Dokumentverzeichnis“ durch das Verzeichnis, in dem Sie die Vorschaubilder speichern möchten.
## Schritt 4: Wasserzeichenobjekt initialisieren
Erstellen Sie eine Instanz von`Watermarker` Klasse, indem Sie den Dokumentpfad an seinen Konstruktor übergeben. Dieses Objekt wird verwendet, um alle Wasserzeichen-Vorgänge auszuführen:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Ihr Code hier
}
```
## Schritt 5: Erstellen Sie Delegate-Methoden für die Stream-Verarbeitung
Um die Vorschau zu generieren, müssen Sie Delegate-Methoden zum Erstellen und Freigeben von Streams definieren. Diese Methoden übernehmen die Erstellung und Freigabe von Streams für jede Seite des Dokuments:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 Der`createPageStreamDelegate` Die Methode erstellt einen Stream für jede Seite des Dokuments, während die`releasePageStreamDelegate` Die Methode schließt den Stream, nachdem die Vorschau generiert wurde.
## Schritt 6: Vorschauoptionen konfigurieren
 Konfigurieren Sie als Nächstes die Vorschauoptionen, indem Sie eine Instanz davon erstellen`PreviewOptions` Klasse. Geben Sie die Delegatenmethoden an und legen Sie das Vorschauformat auf PNG fest. Sie können auch angeben, welche Seiten in die Vorschau einbezogen werden sollen:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
In diesem Beispiel erstellen wir Vorschauen für die ersten beiden Seiten des Dokuments.
## Schritt 7: Generieren Sie die Dokumentvorschau
 Rufen Sie abschließend die an`GeneratePreview` Methode auf der`Watermarker`Objekt und übergibt das konfigurierte Objekt`PreviewOptions`. Dadurch werden die Vorschaubilder generiert und im angegebenen Verzeichnis gespeichert:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Abschluss
Das Generieren von Dokumentvorschauen mit GroupDocs.Watermark für .NET ist ein unkomplizierter Vorgang, der mit nur wenigen Codezeilen durchgeführt werden kann. Wenn Sie die in dieser Anleitung beschriebenen Schritte befolgen, können Sie Ihr Projekt ganz einfach einrichten, die erforderlichen Optionen konfigurieren und Vorschauen für Ihre Dokumente erstellen. Diese leistungsstarke Bibliothek vereinfacht nicht nur den Wasserzeichenprozess, sondern bietet auch robuste Funktionen zum Verwalten und Bearbeiten von Wasserzeichen.
 Wenn Sie Fragen haben oder weitere Hilfe benötigen, besuchen Sie bitte die[GroupDocs.Watermark-Supportforum](https://forum.groupdocs.com/c/watermark/19) oder beziehen Sie sich auf die[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/).
## FAQs
### Welche Dateiformate werden von GroupDocs.Watermark für .NET unterstützt?
 GroupDocs.Watermark für .NET unterstützt eine Vielzahl von Dateiformaten, darunter PDF, DOCX, PPTX, XLSX und viele mehr. Eine vollständige Liste der unterstützten Formate finden Sie im[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/).
### Kann ich das Erscheinungsbild von Wasserzeichen anpassen?
Ja, mit GroupDocs.Watermark können Sie das Erscheinungsbild von Wasserzeichen, einschließlich Text-, Bild- und Formwasserzeichen, vollständig anpassen. Sie können Eigenschaften wie Schriftart, Farbe, Größe und Transparenz anpassen.
### Gibt es eine Testversion?
 Ja, Sie können eine erhalten[Kostenlose Testphase](https://releases.groupdocs.com/) von GroupDocs.Watermark für .NET, um die Funktionen vor dem Kauf zu testen.
### Wie kann ich eine Lizenz für GroupDocs.Watermark erwerben?
 Sie können eine Lizenz für GroupDocs.Watermark erwerben[Hier](https://purchase.groupdocs.com/buy). Je nach Bedarf stehen verschiedene Lizenzoptionen zur Verfügung.
### Kann ich GroupDocs.Watermark in einem kommerziellen Projekt verwenden?
 Ja, mit einer gültigen Lizenz können Sie GroupDocs.Watermark in kommerziellen Projekten verwenden. Lesen Sie unbedingt die Lizenzbedingungen auf der[Kaufseite](https://purchase.groupdocs.com/buy).