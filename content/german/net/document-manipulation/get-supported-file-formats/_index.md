---
title: Erhalten Sie unterstützte Dateiformate
linktitle: Erhalten Sie unterstützte Dateiformate
second_title: GroupDocs.Watermark .NET-API
description: Fügen Sie mit GroupDocs.Watermark für .NET mühelos Wasserzeichen zu Ihren Dokumenten hinzu. Befolgen Sie unsere umfassende Schritt-für-Schritt-Anleitung zum Schutz Ihrer digitalen Vermögenswerte.
weight: 13
url: /de/net/document-manipulation/get-supported-file-formats/
---
## Einführung
Das Anbringen von Wasserzeichen in Ihren Dokumenten ist ein entscheidender Schritt zum Schutz Ihrer digitalen Vermögenswerte. Ob es um den Schutz geistigen Eigentums, die Gewährleistung der Vertraulichkeit oder einfach um die Markenbildung geht, Wasserzeichen spielen eine entscheidende Rolle. Wenn Sie ein .NET-Entwickler sind und Wasserzeichenfunktionen in Ihre Anwendungen integrieren möchten, ist GroupDocs.Watermark für .NET ein leistungsstarkes und vielseitiges Tool, das Sie in Betracht ziehen sollten. Dieses Tutorial führt Sie durch die Grundlagen der Verwendung von GroupDocs.Watermark, von der Installation bis zum Anbringen Ihres ersten Wasserzeichens, und schlüsselt jeden Schritt auf, um sicherzustellen, dass Sie problemlos mitmachen können.
## Voraussetzungen
Bevor wir uns mit den Einzelheiten befassen, stellen wir sicher, dass Sie über alles verfügen, was Sie für den Einstieg benötigen:
1.  Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist. Sie können es hier herunterladen[Visual Studio-Website](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark unterstützt verschiedene Versionen des .NET Framework. Stellen Sie sicher, dass Ihr Projekt auf eine kompatible Version abzielt.
3. GroupDocs.Watermark für .NET: Sie können die neueste Version von herunterladen[Release-Seite](https://releases.groupdocs.com/Watermark/net/).
4. Grundkenntnisse von C#: In diesem Tutorial wird davon ausgegangen, dass Sie über grundlegende Kenntnisse der C#- und .NET-Entwicklung verfügen.
## Namespaces importieren
Importieren wir zunächst die notwendigen Namespaces in Ihr Projekt. Öffnen Sie Ihre C#-Datei und fügen Sie oben die folgenden using-Anweisungen hinzu:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Nachdem diese Namespaces importiert wurden, können Sie mit dem Hinzufügen von Wasserzeichen zu Ihren Dokumenten beginnen.

## Schritt 1: Initialisieren Sie die Wasserzeichen-Engine
 Der erste Schritt besteht darin, die Wasserzeichen-Engine zu initialisieren. Dazu gehört das Erstellen einer Instanz von`Watermarker` Klasse mit dem Dokument, das Sie mit einem Wasserzeichen versehen möchten.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Dieses Code-Snippet richtet das ein`Watermarker` Objekt, mit dem Sie Wasserzeichen auf Ihr Dokument anwenden.
## Schritt 2: Fügen Sie ein Textwasserzeichen hinzu
Fügen wir nun Ihrem Dokument ein einfaches Textwasserzeichen hinzu. Textwasserzeichen eignen sich hervorragend zum Hinzufügen von Beschriftungen wie „Vertraulich“ oder „Entwurf“.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Hier haben wir eine erstellt`TextWatermark`Objekt mit dem Text „Vertraulich“, legen Sie Schriftart und Farbe fest und richten Sie es in der Mitte des Dokuments aus.
## Schritt 3: Fügen Sie ein Bildwasserzeichen hinzu
Wenn Sie lieber ein Bild als Wasserzeichen verwenden möchten, ist dies mit GroupDocs.Watermark ganz einfach.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 In diesem Beispiel erstellen wir eine`ImageWatermark` Legen Sie das Objekt fest, legen Sie seine Abmessungen fest und richten Sie es an der oberen rechten Ecke des Dokuments aus.
## Schritt 4: Speichern Sie das Dokument
Nach dem Hinzufügen der gewünschten Wasserzeichen besteht der letzte Schritt darin, das geänderte Dokument zu speichern.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Dadurch wird das mit Wasserzeichen versehene Dokument im angegebenen Pfad gespeichert und alle von ihm verwendeten Ressourcen freigegeben`Watermarker` Beispiel.
## Schritt 5: Erhalten Sie unterstützte Dateiformate
Um zu sehen, welche Dateiformate von GroupDocs.Watermark unterstützt werden, können Sie den folgenden Codeausschnitt verwenden:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Dadurch werden alle Dateitypen ausgedruckt, die GroupDocs.Watermark verarbeiten kann, sodass Sie einen umfassenden Überblick über seine Funktionen erhalten.
## Abschluss
Das Versehen Ihrer Dokumente mit Wasserzeichen mit GroupDocs für .NET ist unkompliziert und effizient. Durch Befolgen dieses Tutorials haben Sie gelernt, wie Sie die Wasserzeichen-Engine initialisieren, Text- und Bildwasserzeichen hinzufügen, Ihre mit Wasserzeichen versehenen Dokumente speichern und unterstützte Dateiformate auflisten. Mit diesen Tools können Sie Ihre Dokumente zuverlässig schützen.
 Wenn Sie Fragen haben oder weitere Hilfe benötigen, besuchen Sie bitte die[GroupDocs.Watermark-Supportforum](https://forum.groupdocs.com/c/watermark/19).
## FAQs
### Wie installiere ich GroupDocs.Watermark für .NET?
 Sie können es hier herunterladen[Release-Seite](https://releases.groupdocs.com/Watermark/net/) und fügen Sie die DLL zu Ihrem Projekt hinzu.
### Kann ich GroupDocs.Watermark kostenlos testen?
 Ja, Sie können eine beantragen[Kostenlose Testphase](https://releases.groupdocs.com/) um die Software vor dem Kauf zu bewerten.
### Welche Dateiformate werden von GroupDocs.Watermark unterstützt?
Sie können das bereitgestellte Code-Snippet verwenden, um alle unterstützten Dateiformate aufzulisten.
### Wie kann ich eine Lizenz für GroupDocs.Watermark kaufen?
 Lizenzen können direkt bei erworben werden[Kaufseite](https://purchase.groupdocs.com/buy).
### Gibt es Dokumentation für GroupDocs.Watermark?
 Ja, eine umfassende Dokumentation ist vorhanden[Hier](https://tutorials.groupdocs.com/Watermark/net/).