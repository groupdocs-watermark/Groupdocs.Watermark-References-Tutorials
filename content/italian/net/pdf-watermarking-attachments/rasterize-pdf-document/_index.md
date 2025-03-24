---
title: Rasterizza il documento PDF
linktitle: Rasterizza il documento PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come rasterizzare documenti PDF utilizzando GroupDocs.Watermark per .NET. Migliora facilmente la sicurezza dei documenti e l'impatto visivo.
weight: 27
url: /it/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## introduzione
Nel campo della gestione e manipolazione dei documenti, GroupDocs.Watermark per .NET si distingue come uno strumento potente, offrendo solide funzionalità per aggiungere, rimuovere e cercare filigrane in vari formati di documenti. Che si tratti di proteggere i tuoi documenti con avvisi di copyright, aggiungere loghi aziendali per il branding o semplicemente annotare documenti con timbri, GroupDocs.Watermark semplifica il processo con la sua API intuitiva e un ampio set di funzionalità.
## Prerequisiti
Prima di immergerti nel mondo della filigrana con GroupDocs.Watermark per .NET, assicurati di disporre dei seguenti prerequisiti:
### 1. Installa .NET Framework
Assicurati di avere .NET Framework installato sul tuo computer di sviluppo. Puoi scaricarlo dal sito Web Microsoft o utilizzare il tuo gestore di pacchetti preferito.
#### Passaggio 1: scarica .NET Framework
Visita la pagina di download di Microsoft .NET Framework.
#### Passaggio 2: installare .NET Framework
Seguire le istruzioni di installazione fornite nella pagina di download per installare .NET Framework sul sistema.
### 2. Ottieni la licenza GroupDocs.Watermark
Per utilizzare tutte le funzionalità di GroupDocs.Watermark, è necessaria una licenza valida. È possibile acquistare una licenza o ottenerne una temporanea a scopo di valutazione.
#### Passaggio 1: ottieni una licenza
Visita la pagina di acquisto di GroupDocs.Watermark.
#### Passaggio 2: acquista o ottieni una licenza temporanea
Scegli l'opzione di licenza appropriata in base alle tue esigenze: acquista una licenza per un utilizzo continuato o acquisisci una licenza temporanea a scopo di valutazione.

## Importa spazi dei nomi
Prima di iniziare ad applicare la filigrana ai tuoi documenti, assicurati di importare gli spazi dei nomi necessari per accedere senza problemi alla funzionalità di Watermark.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Ora che hai impostato tutto, tuffiamoci nella rasterizzazione di un documento PDF utilizzando GroupDocs.Watermark per .NET. La rasterizzazione converte ogni pagina del documento PDF in un formato immagine raster, come PNG.
## Passaggio 1: inizializza le variabili
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Assicurati di sostituire "Percorso del tuo documento" e "Directory dei tuoi documenti" rispettivamente con il percorso effettivo del documento PDF e con la directory di output desiderata.
## Passaggio 2: carica il documento e aggiungi la filigrana
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Inizializza la filigrana dell'immagine o del testo
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Aggiungi prima la filigrana di qualsiasi tipo
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterizza tutte le pagine
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Il contenuto di tutte le pagine viene sostituito con immagini raster
    watermarker.Save(outputFileName);
}
```
In questo passaggio, carichiamo il documento PDF e inizializziamo una filigrana di testo con proprietà specificate come testo, carattere, allineamento, angolo di rotazione, tipo di ridimensionamento, fattore di scala e opacità. Quindi, aggiungiamo la filigrana al documento. Successivamente, recuperiamo il contenuto del documento PDF e rasterizziamo tutte le pagine in formato PNG con una risoluzione di 100 DPI. Infine, salviamo il documento modificato con contenuto rasterizzato.

## Conclusione
GroupDocs.Watermark per .NET offre una soluzione completa per aggiungere facilmente filigrane a vari formati di documenti. Seguendo i passaggi descritti in questo tutorial, puoi rasterizzare in modo efficace i documenti PDF e migliorarne la sicurezza e l'attrattiva visiva.
## Domande frequenti
### GroupDocs.Watermark è compatibile con altri formati di documenti oltre al PDF?
Sì, GroupDocs.Watermark supporta un'ampia gamma di formati di documenti, tra cui Microsoft Word, Excel, PowerPoint, Visio, Outlook e molti altri.
### Posso personalizzare l'aspetto delle filigrane aggiunte utilizzando GroupDocs.Watermark?
Assolutamente! GroupDocs.Watermark fornisce ampie opzioni per personalizzare le proprietà della filigrana come testo, carattere, colore, dimensione, opacità, rotazione e posizione.
### GroupDocs.Watermark offre supporto per l'elaborazione batch?
Sì, puoi elaborare facilmente più documenti in modalità batch utilizzando GroupDocs, risparmiando tempo e fatica nell'applicazione della filigrana a grandi gruppi di file.
### È disponibile una versione di prova per GroupDocs.Watermark?
Sì, puoi scaricare una versione di prova gratuita di GroupDocs.Watermark dal sito Web per valutarne le funzionalità prima di effettuare un acquisto.
### Come posso ottenere assistenza in caso di problemi o se ho domande su GroupDocs.Watermark?
Puoi visitare il forum GroupDocs.Watermark per chiedere supporto alla community o contattare il team di supporto GroupDocs per assistenza.