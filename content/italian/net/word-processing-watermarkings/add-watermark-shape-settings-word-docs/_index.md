---
title: Aggiungi filigrana con impostazioni di forma in documenti Word
linktitle: Aggiungi filigrana con impostazioni di forma in documenti Word
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane con impostazioni di forma ai documenti Word utilizzando GroupDocs per .NET. Proteggi i tuoi documenti in modo efficace.
weight: 20
url: /it/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## introduzione
In questo tutorial, esamineremo il processo di aggiunta di una filigrana con impostazioni di forma ai documenti di Word utilizzando GroupDocs.Watermark per .NET.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Watermark per .NET installato. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Conoscenza base della programmazione C#.
3. Una comprensione dell'elaborazione dei documenti Word.

## Importa spazi dei nomi
Innanzitutto è necessario importare gli spazi dei nomi necessari per accedere alle classi e ai metodi richiesti.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
Carica il documento Word nel punto in cui desideri aggiungere la filigrana.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il codice per l'aggiunta della filigrana va qui
}
```
## Passaggio 2: aggiungi filigrana
 Istanziare a`TextWatermark` oggetto e specifica il testo che desideri utilizzare come filigrana.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Passaggio 3: personalizza le impostazioni della filigrana
Configura varie impostazioni per la filigrana, come allineamento, angolo di rotazione, colore e opacità.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Passaggio 4: definire le opzioni della sezione filigrana
Definire le opzioni per la sezione della filigrana, come il nome della forma e il testo alternativo.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Passaggio 5: aggiungi la filigrana al documento
Aggiungi la filigrana al documento con le opzioni specificate.
```csharp
watermarker.Add(watermark, options);
```
## Passaggio 6: salva il documento
Salva il documento con la filigrana aggiunta.
```csharp
watermarker.Save(outputFileName);
```

## Conclusione
L'aggiunta di filigrane con impostazioni di forma ai documenti di Word utilizzando GroupDocs per .NET è un processo semplice. Seguendo i passaggi descritti in questo tutorial, puoi proteggere efficacemente i tuoi documenti con filigrane personalizzate.
## Domande frequenti
### Posso aggiungere più filigrane allo stesso documento?
Sì, puoi aggiungere più filigrane con impostazioni diverse allo stesso documento.
### GroupDocs.Watermark supporta altri formati di documenti oltre a Word?
Sì, GroupDocs.Watermark supporta vari formati di documenti, tra cui Excel, PowerPoint, PDF e altri.
### Posso personalizzare ulteriormente l'aspetto della filigrana?
Assolutamente, puoi regolare vari parametri come dimensione, stile, colore e posizione del carattere in base alle tue esigenze.
### È disponibile una versione di prova per GroupDocs.Watermark per .NET?
 Sì, puoi ottenere una prova gratuita da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare supporto per GroupDocs.Watermark?
 Puoi trovare supporto e porre domande sul forum GroupDocs[Qui](https://forum.groupdocs.com/c/watermark/19).