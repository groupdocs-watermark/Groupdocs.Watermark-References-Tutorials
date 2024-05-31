---
title: Aggiungi filigrana agli artefatti immagine nel PDF
linktitle: Aggiungi filigrana agli artefatti immagine nel PDF
second_title: API GroupDocs.Watermark .NET
description: Proteggi i tuoi file PDF con filigrane personalizzate utilizzando GroupDocs.Watermark per .NET. Aggiungi facilmente filigrane di testo o immagini agli artefatti immagine nei documenti PDF.
type: docs
weight: 18
url: /it/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## introduzione
In questo tutorial ti guideremo attraverso il processo di aggiunta di una filigrana agli artefatti immagine in un documento PDF utilizzando GroupDocs.Watermark per .NET. Seguendo questi passaggi, puoi proteggere in modo efficiente i tuoi file PDF con filigrane personalizzate.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1.  GroupDocs.Watermark per .NET: scarica e installa la libreria GroupDocs.Watermark per .NET da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Percorso documento: indica il percorso del documento PDF in cui desideri aggiungere la filigrana.
3. Directory di output: crea una directory in cui verrà salvato il documento con filigrana.

## Importa spazi dei nomi
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento e inizializzare Watermarker
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Passaggio 2: ottieni contenuto PDF e aggiungi filigrana
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Inizializza la filigrana dell'immagine o del testo
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Aggiungi filigrana all'immagine
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Passaggio 3: salvare il documento con filigrana
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusione
Con GroupDocs.Watermark per .NET, l'aggiunta di filigrane agli artefatti di immagine nei documenti PDF diventa un processo semplice. Seguendo questo tutorial, potrai proteggere in modo efficace i tuoi file PDF con filigrane personalizzate, garantendone la sicurezza e l'autenticità.
## Domande frequenti
### Posso aggiungere filigrane sia di immagini che di testo al mio documento PDF?
Sì, GroupDocs.Watermark per .NET supporta l'aggiunta simultanea di filigrane di immagini e testo.
### Esiste qualche limite al numero di filigrane che posso aggiungere a un documento?
No, puoi aggiungere più filigrane a un documento senza alcuna limitazione.
### Posso personalizzare l'aspetto e la posizione della filigrana?
Assolutamente, hai il pieno controllo sull'aspetto, sulla posizione e sulle proprietà della filigrana.
### GroupDocs.Watermark per .NET supporta altri formati di documenti oltre al PDF?
Sì, supporta vari formati di documenti tra cui Word, Excel, PowerPoint e altri.
### C'è un modo per rimuovere le filigrane da un documento?
Sì, GroupDocs.Watermark per .NET fornisce metodi per rimuovere filigrane dai documenti, se necessario.