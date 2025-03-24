---
title: Ottieni formati di file supportati
linktitle: Ottieni formati di file supportati
second_title: API GroupDocs.Watermark .NET
description: Aggiungi facilmente filigrane ai tuoi documenti utilizzando GroupDocs.Watermark per .NET. Segui la nostra guida completa passo dopo passo per proteggere le tue risorse digitali.
weight: 13
url: /it/net/document-manipulation/get-supported-file-formats/
---

# Ottieni formati di file supportati

## introduzione
La filigrana dei tuoi documenti è un passaggio cruciale per salvaguardare le tue risorse digitali. Che si tratti di proteggere la proprietà intellettuale, garantire la riservatezza o semplicemente marchiare, le filigrane svolgono un ruolo fondamentale. Se sei uno sviluppatore .NET che desidera integrare funzionalità di filigrana nelle tue applicazioni, GroupDocs.Watermark per .NET è uno strumento potente e versatile che dovresti prendere in considerazione. Questo tutorial ti guiderà attraverso gli elementi essenziali dell'utilizzo di GroupDocs.Watermark, dall'installazione all'applicazione della prima filigrana, suddividendo ogni passaggio per assicurarti di poterlo seguire facilmente.
## Prerequisiti
Prima di entrare nello specifico, assicuriamoci di avere tutto il necessario per iniziare:
1.  Visual Studio: assicurati di avere Visual Studio installato sul tuo computer. Puoi scaricarlo da[Sito Web di Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark supporta varie versioni di .NET Framework. Assicurati che il tuo progetto abbia come target una versione compatibile.
3. GroupDocs.Watermark per .NET: è possibile scaricare la versione più recente da[pagina di rilascio](https://releases.groupdocs.com/Watermark/net/).
4. Conoscenza di base di C#: questa esercitazione presuppone una conoscenza fondamentale dello sviluppo C# e .NET.
## Importa spazi dei nomi
Innanzitutto, importiamo gli spazi dei nomi necessari nel tuo progetto. Apri il file C# e aggiungi le seguenti direttive using in alto:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Una volta importati questi spazi dei nomi, sei pronto per iniziare ad aggiungere filigrane ai tuoi documenti.

## Passaggio 1: inizializzare il motore di filigrana
 Il primo passo è inizializzare il motore di watermarking. Ciò comporta la creazione di un'istanza del file`Watermarker` classe con il documento a cui desideri applicare la filigrana.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Questo frammento di codice configura il file`Watermarker` oggetto, che utilizzerai per applicare filigrane al tuo documento.
## Passaggio 2: aggiungi una filigrana di testo
Ora aggiungiamo una semplice filigrana di testo al tuo documento. Le filigrane di testo sono ottime per aggiungere etichette come "Riservato" o "Bozza".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Qui, abbiamo creato un file`TextWatermark`oggetto con il testo "Confidenziale", impostane il carattere e il colore e allinealo al centro del documento.
## Passaggio 3: aggiungi una filigrana immagine
Se preferisci utilizzare un'immagine come filigrana, GroupDocs.Watermark ti consente di farlo facilmente.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 In questo esempio creiamo un file`ImageWatermark` oggetto, impostarne le dimensioni e allinearlo all'angolo in alto a destra del documento.
## Passaggio 4: salva il documento
Dopo aver aggiunto le filigrane desiderate, il passaggio finale è salvare il documento modificato.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Ciò salverà il documento con filigrana nel percorso specificato e rilascerà tutte le risorse da esso utilizzate`Watermarker` esempio.
## Passaggio 5: ottieni i formati di file supportati
Per vedere quali formati di file sono supportati da GroupDocs.Watermark, puoi utilizzare il seguente snippet di codice:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Verranno stampati tutti i tipi di file che GroupDocs.Watermark può gestire, offrendoti una visione completa delle sue capacità.
## Conclusione
Applicare la filigrana ai tuoi documenti con GroupDocs per .NET è semplice ed efficiente. Seguendo questo tutorial, hai imparato come inizializzare il motore di filigrana, aggiungere filigrane di testo e immagini, salvare i documenti con filigrana ed elencare i formati di file supportati. Con questi strumenti puoi proteggere i tuoi documenti in tutta sicurezza.
 Se hai domande o hai bisogno di ulteriore assistenza, non esitare a visitare il[Forum di supporto GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## Domande frequenti
### Come installo GroupDocs.Watermark per .NET?
 Puoi scaricarlo da[pagina di rilascio](https://releases.groupdocs.com/Watermark/net/) e aggiungi la DLL al tuo progetto.
### Posso provare GroupDocs.Watermark gratuitamente?
 Sì, puoi richiedere a[prova gratuita](https://releases.groupdocs.com/) valutare il software prima dell'acquisto.
### Quali formati di file sono supportati da GroupDocs.Watermark?
Puoi utilizzare lo snippet di codice fornito per elencare tutti i formati di file supportati.
### Come posso acquistare una licenza per GroupDocs.Watermark?
 Le licenze possono essere acquistate direttamente da[pagina di acquisto](https://purchase.groupdocs.com/buy).
### È disponibile documentazione per GroupDocs.Watermark?
 Sì, è disponibile una documentazione completa[Qui](https://tutorials.groupdocs.com/Watermark/net/).