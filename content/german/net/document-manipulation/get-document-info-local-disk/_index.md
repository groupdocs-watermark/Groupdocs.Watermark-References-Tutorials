---
title: Holen Sie sich Dokumentinformationen von der lokalen Festplatte
linktitle: Holen Sie sich Dokumentinformationen von der lokalen Festplatte
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit GroupDocs Watermark für .NET Wasserzeichen in Dokumenten hinzufügen, entfernen und extrahieren.
weight: 11
url: /de/net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Holen Sie sich Dokumentinformationen von der lokalen Festplatte

## Einführung
Willkommen beim ultimativen Leitfaden zur Verwendung von GroupDocs.Watermark für .NET! Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieser Artikel führt Sie durch die Grundlagen des Wasserzeichens Ihrer Dokumente mit diesem leistungsstarken Tool. Am Ende sind Sie ein Profi im Einbetten von Wasserzeichen in Ihre Dokumente und stellen so sicher, dass diese geschützt sind und Ihren Vorgaben entsprechen.
## Voraussetzungen
Bevor Sie sich mit der Schritt-für-Schritt-Anleitung befassen, müssen Sie einige Voraussetzungen erfüllen:
1.  .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem System installiert ist. GroupDocs.Watermark für .NET ist mit verschiedenen Versionen von .NET Framework kompatibel. Überprüfen Sie daher die[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) für Kompatibilitätsdetails.
2.  GroupDocs.Watermark für .NET-Bibliothek: Laden Sie die neueste Version von herunter und installieren Sie sie[Download-Seite](https://releases.groupdocs.com/Watermark/net/).
3. Entwicklungsumgebung: Sie sollten eine Entwicklungsumgebung eingerichtet haben. Visual Studio ist eine beliebte Wahl für die .NET-Entwicklung.
4. Grundlegende C#-Kenntnisse: Wenn Sie die Grundlagen der C#-Programmierung verstehen, können Sie die Beispiele leichter nachvollziehen.
## Namespaces importieren
Bevor Sie GroupDocs.Watermark für .NET verwenden können, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Dies ist ein unkomplizierter Vorgang und für den Zugriff auf die Funktionen der Bibliothek unerlässlich.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Lassen Sie uns den Prozess des Wasserzeichens in einem Dokument in klare, überschaubare Schritte unterteilen. Jeder Schritt soll Ihnen dabei helfen, die Funktionalität einfacher zu verstehen und umzusetzen.
## Schritt 1: Laden Sie Ihr Dokument
 Der erste Schritt besteht darin, das Dokument zu laden, das Sie mit einem Wasserzeichen versehen möchten. Dies geschieht mit dem`Watermarker` Klasse, mit der Sie auf Ihr Dokument zugreifen und es bearbeiten können.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Das Dokument ist jetzt geladen und bereit für die Wasserzeichenmarkierung
}
```
 In diesem Schritt ersetzen`"Your Document Path"` mit dem tatsächlichen Pfad zu Ihrem Dokument. Dies initialisiert die`Watermarker`Objekt, das Ihnen Zugriff auf verschiedene Wasserzeichenfunktionen bietet.
## Schritt 2: Dokumentinformationen abrufen
Bevor Sie ein Wasserzeichen hinzufügen, möchten Sie möglicherweise einige Informationen über das Dokument sammeln. Dies kann nützlich sein, um Ihr Wasserzeichen basierend auf Dokumenteigenschaften anzupassen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 In diesem Schritt wird die`GetDocumentInfo` Die Methode ruft Details wie Dateityp, Seitenanzahl und Dokumentgröße ab. Diese Informationen werden auf der Konsole gedruckt, Sie können sie jedoch bei Bedarf in Ihrer Anwendung verwenden.
## Schritt 3: Fügen Sie ein Textwasserzeichen hinzu
Nachdem Sie Ihr Dokument nun geladen und die darin enthaltenen Informationen zur Hand haben, ist es an der Zeit, ein Wasserzeichen hinzuzufügen. Wir beginnen mit einem einfachen Textwasserzeichen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Hier erstellen Sie eine`TextWatermark` Objekt mit dem gewünschten Text, der gewünschten Schriftart und dem gewünschten Stil. Passen Sie Eigenschaften wie Farbe, Deckkraft und Drehwinkel an Ihre Bedürfnisse an. Abschließend wird das Wasserzeichen zum Dokument hinzugefügt und in einem angegebenen Pfad gespeichert.
## Schritt 4: Fügen Sie ein Bildwasserzeichen hinzu
Textwasserzeichen sind großartig, aber was ist, wenn Sie ein Logo oder ein anderes Bild hinzufügen möchten? In diesem Schritt erfahren Sie, wie Sie ein Bildwasserzeichen hinzufügen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Ersetzen`"Path to Your Image"` mit dem Pfad zu Ihrem Wasserzeichenbild. Legen Sie Eigenschaften wie Deckkraft und Drehwinkel fest, um das Erscheinungsbild Ihres Bildwasserzeichens anzupassen. Der Vorgang zum Hinzufügen und Speichern des Wasserzeichens ähnelt dem eines Textwasserzeichens.
## Schritt 5: Vorhandene Wasserzeichen entfernen
 Manchmal müssen Sie möglicherweise vorhandene Wasserzeichen aus einem Dokument entfernen. Dies kann mit der erfolgen`Remove` Methode, die von der bereitgestellt wird`Watermarker` Klasse.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Hier das`Remove` Die Methode wird verwendet, um Textwasserzeichen aus dem Dokument zu entfernen. Sie können je nach Bedarf verschiedene Arten von Wasserzeichen zum Entfernen angeben, z. B. Bilder oder Text. Speichern Sie das Dokument unter einem neuen Pfad, um die Änderungen anzuzeigen.
## Schritt 6: Wasserzeichen extrahieren
Wenn Sie Wasserzeichen aus einem Dokument extrahieren und überprüfen müssen, ist dies mit GroupDocs.Watermark für .NET problemlos möglich.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Zusätzliche Eigenschaften und Logik für jedes Wasserzeichen
    }
}
```
 Dieser Schritt beinhaltet die Verwendung von`GetWatermarks`Methode zum Abrufen aller Wasserzeichen in einem Dokument. Anschließend können Sie die Liste der Wasserzeichen durchgehen und deren Eigenschaften überprüfen oder bei Bedarf zusätzliche Aktionen ausführen.
## Abschluss
 Glückwunsch! Sie haben jetzt gelernt, wie Sie mit GroupDocs.Watermark für .NET Wasserzeichen zu Ihren Dokumenten hinzufügen, entfernen und extrahieren. Mit diesen Fähigkeiten können Sie Ihre Dokumente effektiv schützen und mit einem Branding versehen. Denken Sie daran, die[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) ist immer da, wenn Sie detailliertere Informationen oder erweiterte Funktionen benötigen.
## FAQs
### Kann ich GroupDocs.Watermark für .NET mit jeder .NET-Version verwenden?
 Ja, GroupDocs.Watermark für .NET ist mit verschiedenen .NET Framework-Versionen kompatibel. Überprüf den[Dokumentation](https://tutorials.groupdocs.com/Watermark/net/) für Einzelheiten.
### Wo kann ich GroupDocs.Watermark für .NET herunterladen?
 Sie können die neueste Version von herunterladen[Download-Seite](https://releases.groupdocs.com/Watermark/net/).
### Wie erhalte ich eine temporäre Lizenz?
 Eine temporäre Lizenz erhalten Sie bei der[temporäre Lizenzseite](https://purchase.groupdocs.com/temporary-license/).
### Gibt es eine kostenlose Testversion?
 Ja, Sie können eine kostenlose Testversion starten, indem Sie die besuchen[kostenlose Testseite](https://releases.groupdocs.com/).
### Wo kann ich Unterstützung erhalten, wenn ich auf Probleme stoße?
 Support gibt es auf der[GroupDocs-Wasserzeichen-Forum](https://forum.groupdocs.com/c/watermark/19).