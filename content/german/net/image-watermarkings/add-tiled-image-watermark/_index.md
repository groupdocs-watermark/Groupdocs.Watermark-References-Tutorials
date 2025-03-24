---
title: Fügen Sie ein gekacheltes Bildwasserzeichen hinzu
linktitle: Fügen Sie ein gekacheltes Bildwasserzeichen hinzu
second_title: GroupDocs.Watermark .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Watermark für .NET gekachelte Bildwasserzeichen zu Ihren Dokumenten hinzufügen. Einfach, effizient und anpassbar.
weight: 10
url: /de/net/image-watermarkings/add-tiled-image-watermark/
---
## Einführung
GroupDocs.Watermark für .NET ist eine leistungsstarke API, die es Entwicklern ermöglicht, Wasserzeichen in verschiedenen Dokumentformaten programmgesteuert hinzuzufügen, zu entfernen und zu durchsuchen. In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens eines gekachelten Bildwasserzeichens zu Ihren Dokumenten mithilfe von GroupDocs.Watermark für .NET.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Grundkenntnisse der Programmiersprache C#.
- Visual Studio ist auf Ihrem System installiert.
- GroupDocs.Watermark für .NET-Bibliothek zu Ihrem Projekt hinzugefügt. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/Watermark/net/).

## Namespaces importieren
Stellen Sie sicher, dass Sie die erforderlichen Namespaces am Anfang Ihrer C#-Datei importieren:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Schritt 1: Legen Sie den Dokumentpfad und das Ausgabeverzeichnis fest
Definieren Sie den Pfad Ihres Eingabedokuments und das Verzeichnis, in dem Sie das Ausgabedokument speichern möchten:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Ersetzen`"Your Document Path"` mit dem absoluten oder relativen Pfad zu Ihrem Eingabedokument.
## Schritt 2: Wasserzeichenobjekt initialisieren
Erstellen Sie ein Watermarker-Objekt mithilfe des Pfads des Eingabedokuments:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Fügen Sie hier ein Wasserzeichen hinzu
}
```
## Schritt 3: Fügen Sie ein gekacheltes Bildwasserzeichen hinzu
Instanziieren Sie ein ImageWatermark-Objekt mit dem Pfad zu der Bilddatei, die Sie als Wasserzeichen verwenden möchten:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Konfigurieren Sie Kacheloptionen
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Fügen Sie dem Dokument ein Wasserzeichen hinzu
    watermarker.Add(watermark);
    // Speichern Sie das geänderte Dokument
    watermarker.Save(outputFileName);
}
```
 Ersetzen`"Path to Your Image"` mit dem tatsächlichen Pfad zu Ihrer Wasserzeichen-Bilddatei.

## Abschluss
Wenn Sie diese Schritte befolgen, können Sie mit GroupDocs.Watermark für .NET ganz einfach ein gekacheltes Bildwasserzeichen zu Ihren Dokumenten hinzufügen. Experimentieren Sie mit verschiedenen Optionen und Konfigurationen, um das gewünschte Ergebnis zu erzielen.
## FAQs
### Kann ich einem einzelnen Dokument mehrere Wasserzeichen hinzufügen?
Ja, Sie können einem Dokument mit GroupDocs.Watermark für .NET mehrere Wasserzeichen unterschiedlicher Art hinzufügen.
### Unterstützt GroupDocs.Watermark alle Dokumentformate?
GroupDocs.Watermark unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Word, Excel, PowerPoint und viele mehr.
### Gibt es eine Testversion für GroupDocs.Watermark?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Kann ich das Erscheinungsbild des Wasserzeichens anpassen?
Ja, Sie können verschiedene Aspekte des Wasserzeichens anpassen, z. B. Position, Größe, Drehung, Transparenz usw.
### Bietet GroupDocs.Watermark technischen Support?
 Ja, Sie können technischen Support im GroupDocs.Watermark-Forum erhalten[Hier](https://forum.groupdocs.com/c/watermark/19).