---
title: Rasterizza la pagina PDF
linktitle: Rasterizza la pagina PDF
second_title: API GroupDocs.Watermark .NET
description: Migliora la sicurezza dei documenti con GroupDocs per .NET. Aggiungi filigrane a PDF e altri formati senza problemi.
type: docs
weight: 28
url: /it/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## introduzione
GroupDocs.Watermark per .NET è una potente API che consente agli sviluppatori di aggiungere facilmente filigrane a vari formati di documenti, inclusi PDF, Word, Excel, PowerPoint e altri. Con la sua interfaccia intuitiva e funzionalità estese, GroupDocs.Watermark semplifica il processo di aggiunta di filigrane di testo o immagini ai documenti, consentendo agli utenti di proteggere la propria proprietà intellettuale e migliorare la sicurezza dei documenti senza sforzo.
## Prerequisiti
Prima di immergerti nell'utilizzo di GroupDocs.Watermark per .NET, assicurati di disporre dei seguenti prerequisiti:
1. Installazione: scaricare e installare GroupDocs.Watermark per .NET dal file[pagina di download](https://releases.groupdocs.com/Watermark/net/).
2.  Licenza: acquisisci una licenza per GroupDocs.Watermark per .NET. È possibile ottenere una licenza temporanea a scopo di valutazione da[Qui](https://purchase.groupdocs.com/temporary-license/) oppure acquista una licenza completa da[pagina di acquisto](https://purchase.groupdocs.com/buy).
3. .NET Framework: assicurati di avere .NET Framework installato sul tuo computer di sviluppo.
4. Documento: prepara il documento a cui desideri aggiungere filigrane.

## Importa spazi dei nomi
Per iniziare a utilizzare GroupDocs.Watermark per .NET, importa gli spazi dei nomi necessari nel tuo progetto:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il tuo codice va qui
}
```
## Passaggio 2: inizializza la filigrana
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Passaggio 3: aggiungi filigrana
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Passaggio 4: rasterizza la pagina
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Passaggio 5: salva il documento
```csharp
watermarker.Save(outputFileName);
```

## Conclusione
In conclusione, GroupDocs.Watermark per .NET offre una soluzione perfetta per aggiungere filigrane a PDF e altri formati di documenti. Seguendo la guida passo passo sopra descritta, gli sviluppatori possono rasterizzare in modo efficiente le pagine PDF e migliorare facilmente la sicurezza dei documenti.
## Domande frequenti
### GroupDocs.Watermark è compatibile con altri formati di documenti oltre al PDF?
Sì, GroupDocs.Watermark supporta un'ampia gamma di formati di documenti, tra cui Word, Excel, PowerPoint, Visio e altri.
### Posso personalizzare l'aspetto della filigrana aggiunta al documento?
Assolutamente! GroupDocs.Watermark offre ampie opzioni di personalizzazione per filigrane di testo e immagini, consentendo agli utenti di regolare carattere, dimensione, colore, opacità e posizionamento in base alle proprie preferenze.
### GroupDocs.Watermark è adatto sia per uso personale che commerciale?
Sì, GroupDocs.Watermark offre opzioni di licenza flessibili per soddisfare le esigenze sia individuali che aziendali, rendendolo adatto a progetti personali e ad applicazioni commerciali su larga scala.
### GroupDocs.Watermark offre supporto tecnico per gli sviluppatori?
Sì, gli sviluppatori possono accedere al supporto tecnico completo tramite il forum GroupDocs.Watermark, dove possono chiedere assistenza, condividere esperienze e interagire con altri sviluppatori.
### Posso provare GroupDocs.Watermark prima di effettuare un acquisto?
Certamente! Puoi usufruire di una versione di prova gratuita di GroupDocs.Watermark da[pagina delle uscite](https://releases.groupdocs.com/), permettendoti di esplorarne caratteristiche e funzionalità prima di impegnarti in un acquisto.