---
title: Aggiungi filigrana con margine di pagina nel PDF
linktitle: Aggiungi filigrana con margine di pagina nel PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane con il tipo di margine della pagina in PDF utilizzando Groupdocs per .NET. Proteggi i tuoi documenti senza sforzo.
weight: 21
url: /it/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---

# Aggiungi filigrana con margine di pagina nel PDF

## introduzione
Nell'era digitale di oggi, la protezione dei documenti è più cruciale che mai. Un modo per garantire l'integrità e l'autenticità dei tuoi documenti è aggiungere filigrane. Groupdocs.Watermark per .NET è uno strumento eccezionale progettato per semplificare questo processo. In questo tutorial ti guideremo attraverso i passaggi per aggiungere una filigrana con il tipo di margine di pagina in un PDF utilizzando Groupdocs.Watermark per .NET.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:
-  Groupdocs.Watermark per .NET: scarica e installa il file[ultima versione](https://releases.groupdocs.com/Watermark/net/) di Groupdocs.Watermark per .NET.
- Ambiente di sviluppo: un ambiente di sviluppo .NET come Visual Studio.
- Conoscenza di base di C#: familiarità con il linguaggio di programmazione C#.
- Documento PDF: un documento PDF a cui desideri aggiungere una filigrana.
## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C#. Questi spazi dei nomi forniranno l'accesso alle funzionalità Groupdocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Ora suddividiamo il processo in passaggi gestibili. Segui attentamente ogni passaggio per aggiungere una filigrana al tuo documento PDF.
## Passaggio 1: imposta il percorso del documento e la directory di output
Innanzitutto, dovrai specificare il percorso del documento e la directory di output in cui verrà salvato il PDF con filigrana.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Passaggio 2: carica il documento PDF
 Successivamente, caricherai il tuo documento PDF utilizzando il file`PdfLoadOptions` classe. Questa classe ti consente di specificare tutte le opzioni necessarie per caricare il tuo PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Passaggio 3: crea la filigrana di testo
Ora è il momento di creare la filigrana. In questo esempio creeremo una filigrana di testo con proprietà specifiche come carattere, dimensione e allineamento.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Passaggio 4: imposta il tipo di margine della pagina
 Per posizionare la filigrana in modo appropriato, dovrai impostare il tipo di margine della pagina. Qui impostiamo il tipo di margine della pagina su`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Passaggio 5: aggiungi e salva la filigrana
Infine, aggiungi la filigrana al tuo documento e salva il PDF modificato nella directory di output specificata.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Conclusione
il gioco è fatto! Seguendo questi passaggi, puoi aggiungere facilmente una filigrana con un tipo di margine di pagina specifico ai tuoi documenti PDF utilizzando Groupdocs.Watermark per .NET. Questo non solo aiuta a proteggere i tuoi documenti, ma ne garantisce anche l'autenticità. Che tu abbia a che fare con rapporti riservati, documenti legali o lavori creativi, la filigrana è un modo semplice ma efficace per salvaguardare i tuoi contenuti.
## Domande frequenti
### Cos'è Groupdocs.Watermark per .NET?
Groupdocs.Watermark per .NET è una potente libreria per aggiungere filigrane a vari formati di documenti a livello di codice. Supporta immagini, testo e altro, consentendo un'ampia personalizzazione.
### Posso utilizzare questo metodo per filigranare altri tipi di documenti?
Sì, Groupdocs.Watermark per .NET supporta un'ampia gamma di formati di documenti, inclusi Word, Excel, PowerPoint e immagini. Il processo è simile ma può comportare opzioni e classi diverse.
### Come posso ottenere una prova gratuita di Groupdocs.Watermark per .NET?
 Puoi[Scarica una prova gratuita](https://releases.groupdocs.com/) dal sito Web Groupdocs per esplorare le caratteristiche e le funzionalità della libreria.
### È possibile personalizzare l'aspetto della filigrana?
Assolutamente! Puoi personalizzare il carattere, la dimensione, il colore, l'opacità, l'allineamento e altre proprietà della filigrana in base alle tue esigenze.
### Dove posso ottenere supporto per Groupdocs.Watermark per .NET?
 Per supporto è possibile visitare il[Forum di supporto di Groupdocs Watermark](https://forum.groupdocs.com/c/watermark/19) dove puoi porre domande e ottenere assistenza dalla comunità e dal team di Groupdocs.