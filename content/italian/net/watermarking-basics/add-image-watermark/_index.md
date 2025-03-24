---
title: Aggiungi filigrana immagine
linktitle: Aggiungi filigrana immagine
second_title: API GroupDocs.Watermark .NET
description: Aggiungi facilmente filigrane di immagini ai tuoi documenti utilizzando GroupDocs.Watermark per .NET. Proteggi la tua proprietà intellettuale con facilità.
weight: 10
url: /it/net/watermarking-basics/add-image-watermark/
---
## introduzione
In questo tutorial, approfondiremo il processo di aggiunta di una filigrana immagine ai tuoi documenti utilizzando GroupDocs.Watermark per .NET. La filigrana sui documenti è essenziale per proteggere la proprietà intellettuale e il marchio. Con GroupDocs.Watermark per .NET, puoi integrare perfettamente le filigrane in vari formati di documenti come Word, Excel, PowerPoint, PDF e molti altri.
## Prerequisiti
Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:
1.  Libreria GroupDocs.Watermark per .NET: scaricare e installare la libreria GroupDocs.Watermark per .NET dalla[sito web](https://releases.groupdocs.com/Watermark/net/).
2. Documento: tieni pronto il documento a cui desideri aggiungere la filigrana.
3. Immagine per filigrana: prepara il file immagine che desideri utilizzare come filigrana.

## Importa spazi dei nomi
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Passaggio 1: inizializzare il percorso del documento e la directory di output
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"`con il percorso assoluto o relativo del documento e`"Your Document Directory"` con la directory in cui desideri salvare il documento con filigrana.
## Passaggio 2: aprire il flusso di documenti e inizializzare Watermarker
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Il processo di filigrana andrà qui
    }
}
```
 Apri il flusso di documenti utilizzando`FileStream` e inizializzare il`Watermarker` oggetto.
## Passaggio 3: aggiungi la filigrana dell'immagine
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Creare un`ImageWatermark` oggetto con il percorso del file immagine che desideri utilizzare come filigrana. Imposta l'allineamento orizzontale e verticale della filigrana.
## Passaggio 4: salva il documento con filigrana
```csharp
watermarker.Save(outputFileName);
```
Salva il documento con filigrana nella directory di output specificata con il nome file desiderato.

## Conclusione
In conclusione, GroupDocs.Watermark per .NET fornisce una soluzione completa per aggiungere filigrane a vari formati di documenti senza sforzo. Seguendo i passaggi descritti in questo tutorial, puoi aggiungere in modo efficiente filigrane di immagini ai tuoi documenti e proteggere la tua proprietà intellettuale.
## Domande frequenti
### Posso aggiungere filigrane di testo utilizzando GroupDocs.Watermark per .NET?
Sì, GroupDocs.Watermark per .NET supporta l'aggiunta di filigrane di immagini e testo ai documenti.
### GroupDocs.Watermark per .NET è compatibile con diversi formati di documenti?
Assolutamente, GroupDocs.Watermark per .NET supporta un'ampia gamma di formati di documenti tra cui Word, Excel, PowerPoint, PDF e altri.
### GroupDocs.Watermark per .NET fornisce opzioni di personalizzazione per le filigrane?
Sì, puoi personalizzare vari aspetti della filigrana come posizione, dimensione, opacità e rotazione.
### Posso rimuovere filigrane dai documenti utilizzando GroupDocs.Watermark per .NET?
Sì, GroupDocs.Watermark per .NET offre funzionalità per rilevare e rimuovere filigrane dai documenti.
### È disponibile una versione di prova per GroupDocs.Watermark per .NET?
 Sì, puoi usufruire di una versione di prova gratuita dal sito Web per esplorare le funzionalità prima dell'acquisto[Qui](https://releases.groupdocs.com/).