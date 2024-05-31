---
title: Aggiungi filigrana immagine affiancata
linktitle: Aggiungi filigrana immagine affiancata
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di immagini affiancate ai tuoi documenti utilizzando GroupDocs.Watermark per .NET. Facile, efficiente e personalizzabile.
type: docs
weight: 10
url: /it/net/image-watermarkings/add-tiled-image-watermark/
---
## introduzione
GroupDocs.Watermark per .NET è una potente API che consente agli sviluppatori di aggiungere, rimuovere e cercare filigrane in vari formati di documenti a livello di codice. In questo tutorial ti guideremo attraverso il processo di aggiunta di una filigrana di immagine affiancata ai tuoi documenti utilizzando GroupDocs.Watermark per .NET.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Conoscenza base del linguaggio di programmazione C#.
- Visual Studio installato nel sistema.
- Libreria GroupDocs.Watermark per .NET aggiunta al tuo progetto. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/Watermark/net/).

## Importa spazi dei nomi
Assicurati di importare gli spazi dei nomi necessari all'inizio del file C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Passaggio 1: impostare il percorso del documento e la directory di output
Definisci il percorso del documento di input e la directory in cui desideri salvare il documento di output:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` con il percorso assoluto o relativo del documento di input.
## Passaggio 2: inizializza l'oggetto filigrana
Crea un oggetto Filigrana utilizzando il percorso del documento di input:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Aggiungi filigrana qui
}
```
## Passaggio 3: aggiungi la filigrana dell'immagine affiancata
Crea un'istanza di un oggetto ImageWatermark con il percorso del file immagine che desideri utilizzare come filigrana:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configura le opzioni del riquadro
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
    // Aggiungi filigrana al documento
    watermarker.Add(watermark);
    // Salva il documento modificato
    watermarker.Save(outputFileName);
}
```
 Sostituire`"Path to Your Image"` con il percorso effettivo del file immagine della filigrana.

## Conclusione
Seguendo questi passaggi, puoi aggiungere facilmente una filigrana di immagine affiancata ai tuoi documenti utilizzando GroupDocs.Watermark per .NET. Sperimenta diverse opzioni e configurazioni per ottenere il risultato desiderato.
## Domande frequenti
### Posso aggiungere più filigrane a un singolo documento?
Sì, puoi aggiungere più filigrane di diverso tipo a un documento utilizzando GroupDocs.Watermark per .NET.
### GroupDocs.Watermark supporta tutti i formati di documenti?
GroupDocs.Watermark supporta un'ampia gamma di formati di documenti, inclusi PDF, Word, Excel, PowerPoint e molti altri.
### È disponibile una versione di prova per GroupDocs.Watermark?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Posso personalizzare l'aspetto della filigrana?
Sì, puoi personalizzare vari aspetti della filigrana, come posizione, dimensione, rotazione, trasparenza, ecc.
### GroupDocs.Watermark offre supporto tecnico?
 Sì, puoi ottenere supporto tecnico dal forum GroupDocs.Watermark[Qui](https://forum.groupdocs.com/c/watermark/19).