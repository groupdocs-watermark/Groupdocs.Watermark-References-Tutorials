---
title: Aggiungi filigrana immagine dallo streaming
linktitle: Aggiungi filigrana immagine dallo streaming
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di immagini ai documenti utilizzando GroupDocs.Watermark per .NET. Segui la nostra guida passo passo per un'integrazione perfetta della filigrana.
weight: 12
url: /it/net/image-watermarkings/add-image-watermark-from-stream/
---

# Aggiungi filigrana immagine dallo streaming

## introduzione
Nel campo della gestione e della sicurezza dei documenti, incorporare filigrane nei file riveste un'importanza fondamentale. Che si tratti di branding, protezione del copyright o mantenimento dell'integrità del documento, le filigrane svolgono un ruolo cruciale. Fortunatamente, GroupDocs.Watermark per .NET fornisce una soluzione solida per aggiungere, rimuovere e cercare filigrane in vari formati di documenti.
## Prerequisiti
Prima di approfondire l'implementazione delle filigrane utilizzando GroupDocs.Watermark per .NET, assicurarsi che siano soddisfatti i seguenti prerequisiti:
1.  Installa GroupDocs.Watermark per .NET: scarica e installa la libreria GroupDocs.Watermark per .NET dalla[Link per scaricare](https://releases.groupdocs.com/Watermark/net/).
2. Accesso al documento: accedi al documento su cui desideri aggiungere o rimuovere filigrane.
3. Conoscenza di base di C#: la familiarità con il linguaggio di programmazione C# è necessaria per comprendere e implementare i frammenti di codice forniti.

## Importa spazi dei nomi
Prima di procedere con l'aggiunta di filigrane di immagini da uno stream, importa gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Passaggio 1: definire il percorso del documento e la directory di output
Innanzitutto, definisci il percorso del documento in cui desideri aggiungere la filigrana e specifica la directory di output per il documento elaborato.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Passaggio 2: aprire il flusso di filigrana
 Apri il file immagine della filigrana come flusso utilizzando il file`File.OpenRead` metodo.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // La logica di elaborazione della filigrana andrà qui
}
```
## Passaggio 3: aggiungi la filigrana al documento
 Inizializzare a`Watermarker` oggetto con il percorso del documento, quindi creare un file`ImageWatermark` oggetto con il flusso di filigrana ottenuto nel passaggio 2. Aggiungi la filigrana al documento utilizzando il file`Add` metodo del`Watermarker` oggetto.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Aggiungi filigrana al documento
        watermarker.Add(watermark);
        // Salva il documento con filigrana
        watermarker.Save(outputFileName);
    }
}
```

## Conclusione
GroupDocs.Watermark per .NET fornisce una soluzione perfetta per aggiungere filigrane ai documenti, garantendo l'identità del marchio, la protezione del copyright e l'integrità dei documenti. Seguendo i passaggi descritti e utilizzando i frammenti di codice forniti, gli utenti possono incorporare facilmente filigrane nei propri documenti.
## Domande frequenti
### GroupDocs.Watermark è compatibile con vari formati di documenti?
Sì, GroupDocs.Watermark supporta un'ampia gamma di formati di documenti tra cui documenti Word, fogli di calcolo Excel, presentazioni PowerPoint, PDF e altro ancora.
### Posso personalizzare l'aspetto e la posizione delle filigrane?
Assolutamente sì, GroupDocs.Watermark offre ampie opzioni per personalizzare l'aspetto, la posizione, la trasparenza, la rotazione e altro della filigrana per soddisfare requisiti specifici.
### GroupDocs.Watermark fornisce API per rimuovere le filigrane esistenti?
Sì, GroupDocs.Watermark consente agli utenti non solo di aggiungere filigrane ma anche di rimuovere facilmente filigrane esistenti dai documenti.
### Il supporto tecnico è disponibile per gli utenti di GroupDocs.Watermark?
 Sì, gli utenti possono usufruire di supporto tecnico e assistenza tramite il servizio dedicato[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### Posso valutare GroupDocs.Watermark prima dell'acquisto?
Certamente, gli utenti possono optare per una prova gratuita di GroupDocs.Watermark per esplorarne caratteristiche e funzionalità prima di prendere una decisione di acquisto.