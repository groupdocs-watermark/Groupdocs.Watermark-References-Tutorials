---
title: Sostituisci il testo forma con testo formattato nei documenti Word
linktitle: Sostituisci il testo forma con testo formattato nei documenti Word
second_title: API GroupDocs.Watermark .NET
description: Scopri come sostituire il testo forma con testo formattato nei documenti Word utilizzando GroupDocs.Watermark per .NET. Le tue funzionalità di modifica dei documenti senza sforzo.
type: docs
weight: 34
url: /it/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## introduzione
In questo tutorial ti guideremo attraverso il processo di sostituzione del testo forma con testo formattato nei documenti Word utilizzando GroupDocs.Watermark per .NET. Questa libreria fornisce potenti funzionalità per lavorare con le filigrane, inclusa la sostituzione del testo all'interno delle forme.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1.  GroupDocs.Watermark per .NET: assicurati di aver installato e configurato GroupDocs.Watermark per .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Percorso documento: dovresti avere il percorso del documento Word in cui desideri sostituire il testo.

## Importa spazi dei nomi
Prima di scrivere il codice, importa gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
 Caricare il documento Word utilizzando il file`Watermarker` classe:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il tuo codice continua qui...
}
```
## Passaggio 2: ottieni contenuto e sostituisci testo
Una volta caricato il documento, ottieni il contenuto e sostituisci il testo all'interno delle forme:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Passaggio 3: salva il documento
Dopo aver sostituito il testo, salva il documento modificato:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusione
La sostituzione del testo forma con testo formattato nei documenti Word è semplificata con GroupDocs per .NET. Seguendo i passaggi descritti in questo tutorial, puoi gestire e manipolare in modo efficiente il testo all'interno dei tuoi documenti.

## Domande frequenti
### Posso sostituire il testo in altri tipi di documenti utilizzando GroupDocs.Watermark per .NET?
Sì, GroupDocs Watermark supporta vari formati di documenti come PDF, Excel, PowerPoint e altri.
### GroupDocs.Watermark è compatibile con .NET Core?
Sì, GroupDocs.Watermark supporta sia .NET Framework che .NET Core.
### GroupDocs.Watermark fornisce supporto per l'aggiunta di immagini come filigrane?
Assolutamente sì, GroupDocs.Watermark ti consente di aggiungere filigrane di testo e immagini ai tuoi documenti.
### Posso personalizzare l'aspetto delle filigrane aggiunte utilizzando GroupDocs.Watermark?
Sì, hai il pieno controllo sull'aspetto, sulla posizione e su altre proprietà delle filigrane.
### È disponibile una versione di prova per GroupDocs.Watermark per .NET?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).