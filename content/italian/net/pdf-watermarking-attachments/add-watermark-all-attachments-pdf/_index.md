---
title: Aggiungi filigrana a tutti gli allegati nel PDF
linktitle: Aggiungi filigrana a tutti gli allegati nel PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane agli allegati PDF utilizzando GroupDocs.Watermark per .NET. Proteggi facilmente i tuoi documenti con filigrane personalizzate.
weight: 16
url: /it/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## introduzione
L'aggiunta di filigrane agli allegati PDF può essere un passaggio cruciale nella gestione dei documenti, soprattutto quando si garantisce la sicurezza o il marchio. GroupDocs.Watermark per .NET offre una soluzione completa per incorporare facilmente filigrane nei file PDF. In questo tutorial ti guideremo attraverso il processo di aggiunta di una filigrana a tutti gli allegati all'interno di un documento PDF utilizzando GroupDocs.Watermark per .NET.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Watermark per .NET: se non lo hai già fatto, scarica e installa GroupDocs.Watermark per .NET dal[sito web](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente di sviluppo: configura un ambiente di sviluppo adatto con Visual Studio o qualsiasi altro IDE compatibile con .NET.
3. Documento PDF: prepara il documento PDF a cui desideri aggiungere filigrane, insieme agli allegati a cui desideri applicare la filigrana.

## Importazione di spazi dei nomi
Prima di immergerti nel codice, assicurati di importare gli spazi dei nomi necessari per accedere alle funzionalità GroupDocs.Watermark per .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: definire il percorso del documento e la directory di output
Innanzitutto, definisci il percorso del documento PDF di input e la directory in cui verrà salvato il documento con filigrana:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Passaggio 2: inizializza le opzioni di caricamento e la filigrana
Successivamente, inizializza le opzioni di caricamento per il documento PDF e crea una filigrana di testo:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Passaggio 3: caricare il documento e gli allegati
Carica il documento PDF e scorri i suoi allegati:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Passaggio 4: verificare il supporto degli allegati
Controlla se il file allegato è supportato da GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Passaggio 5: aggiungi filigrana agli allegati
Carica il documento allegato e aggiungi la filigrana:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Passaggio 6: salva le modifiche
Infine, salva le modifiche al documento PDF con filigrana:
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusione
In questo tutorial, abbiamo esplorato come aggiungere filigrane a tutti gli allegati all'interno di un documento PDF utilizzando GroupDocs.Watermark per .NET. Seguendo la guida passo passo, puoi integrare perfettamente le filigrane nei tuoi file PDF, garantendo la sicurezza e il branding dei documenti.
## Domande frequenti
### Posso personalizzare l'aspetto della filigrana?
Sì, puoi personalizzare vari aspetti come testo, carattere, dimensione, colore e posizione della filigrana in base alle tue esigenze.
### GroupDocs.Watermark supporta altri formati di documenti oltre al PDF?
Sì, GroupDocs.Watermark supporta un'ampia gamma di formati di documenti tra cui Microsoft Word, Excel, PowerPoint, Visio, Outlook e Immagini.
### È disponibile una versione di prova per GroupDocs.Watermark?
Sì, puoi esplorare le funzionalità di GroupDocs.Watermark scaricando la versione di prova gratuita dal sito web.
### Posso aggiungere più filigrane a un singolo documento?
Assolutamente sì, GroupDocs.Watermark ti consente di aggiungere più filigrane tra cui testo, immagine e annotazioni contemporaneamente per migliorare la sicurezza e il marchio dei documenti.
### Il supporto tecnico è disponibile per gli utenti di GroupDocs.Watermark?
Sì, GroupDocs fornisce supporto tecnico completo attraverso forum e canali di supporto dedicati per assistere gli utenti con qualsiasi domanda o problema che potrebbero incontrare.