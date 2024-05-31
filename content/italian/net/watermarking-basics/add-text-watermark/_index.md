---
title: Aggiungi filigrana di testo
linktitle: Aggiungi filigrana di testo
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di testo ai tuoi documenti utilizzando Groupdocs per .NET con questa guida passo passo.
type: docs
weight: 11
url: /it/net/watermarking-basics/add-text-watermark/
---
## introduzione
GroupDocs.Watermark per .NET è una potente libreria che consente agli sviluppatori di aggiungere, cercare e rimuovere filigrane da vari formati di documenti nelle applicazioni .NET. In questo tutorial, ci concentreremo sull'aggiunta di una filigrana di testo a un documento utilizzando GroupDocs.Watermark.
## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti prerequisiti:
1. Conoscenza base del linguaggio di programmazione C#.
2. Visual Studio installato nel sistema.
3.  Libreria GroupDocs.Watermark per .NET installata. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/Watermark/net/).

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Passaggio 1: definire il percorso del documento e la directory di output
Definire il percorso del documento di input e la directory di output in cui verrà salvato il documento con filigrana.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` con il percorso assoluto o relativo del documento di input, ad esempio:`@"C:\Docs\document.pdf"`. Inoltre, specifica la directory in cui desideri salvare il documento con filigrana.
## Passaggio 2: aggiungi filigrana di testo
 Istanziare il`Watermarker` classe con il percorso del documento di input. Quindi, crea un file`TextWatermark` oggetto con le impostazioni di testo e carattere desiderate.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere una filigrana di testo a un documento utilizzando GroupDocs.Watermark per .NET. Con la sua API intuitiva, gli sviluppatori possono manipolare facilmente le filigrane in vari formati di documenti.
## Domande frequenti
### GroupDocs.Watermark per .NET è compatibile con tutti i formati di documenti?
GroupDocs.Watermark supporta un'ampia gamma di formati di documenti tra cui PDF, Microsoft Word, Excel, PowerPoint e molti altri.
### Posso personalizzare l'aspetto della filigrana del testo?
Sì, puoi personalizzare varie proprietà come carattere, colore, allineamento e opacità della filigrana del testo.
### GroupDocs.Watermark fornisce supporto per la rimozione di filigrane dai documenti?
Sì, GroupDocs.Watermark offre funzionalità per cercare e rimuovere filigrane dai documenti.
### Posso provare GroupDocs.Watermark per .NET prima dell'acquisto?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto tecnico per GroupDocs.Watermark?
 È possibile ottenere supporto tecnico visitando il[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).