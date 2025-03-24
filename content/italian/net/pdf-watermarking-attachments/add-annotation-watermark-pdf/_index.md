---
title: Aggiungi filigrana di annotazione al PDF
linktitle: Aggiungi filigrana di annotazione al PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di annotazioni ai documenti PDF senza sforzo utilizzando GroupDocs.Watermark per .NET. Migliora facilmente il branding e la sicurezza dei documenti.
weight: 10
url: /it/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---
## introduzione
Nell'ambito della gestione dei documenti, l'aggiunta di filigrane ai file PDF rappresenta un aspetto cruciale, soprattutto per scopi di branding, sicurezza e identificazione dei documenti. GroupDocs.Watermark per .NET è una potente libreria che facilita la perfetta integrazione delle filigrane in vari formati di documenti, inclusi i PDF. In questo tutorial, approfondiremo passo dopo passo il processo di aggiunta di filigrane di annotazione ai documenti PDF, utilizzando le funzionalità fornite da GroupDocs.Watermark per .NET.
## Prerequisiti
Prima di procedere con il tutorial, assicurati di disporre dei seguenti prerequisiti:
1.  Libreria GroupDocs.Watermark per .NET: scaricare e installare la libreria GroupDocs.Watermark per .NET dalla[sito web](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente di sviluppo: configura un ambiente di sviluppo adatto, come Visual Studio o qualsiasi altro IDE .NET.
3. Comprensione di base di C#: si consiglia la familiarità con i fondamenti del linguaggio di programmazione C#.

## Importazione degli spazi dei nomi necessari
Per iniziare, importa gli spazi dei nomi richiesti nel tuo progetto C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Passaggio 2: definire le opzioni della filigrana
```csharp
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## Passaggio 3: aggiungi filigrana di testo
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## Passaggio 4: aggiungi la filigrana dell'immagine
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## Passaggio 5: salva il documento con filigrana
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusione
In conclusione, GroupDocs.Watermark per .NET offre una soluzione completa per aggiungere filigrane di annotazioni ai documenti PDF a livello di codice. Seguendo i passaggi descritti, gli utenti possono integrare perfettamente filigrane di testo e immagini nei propri file PDF, migliorando così il branding e la sicurezza dei documenti.
## Domande frequenti
### GroupDocs.Watermark è compatibile con altri formati di documenti oltre al PDF?
Sì, GroupDocs.Watermark supporta un'ampia gamma di formati di documenti, inclusi Word, Excel, PowerPoint e altri.
### Posso personalizzare l'aspetto della filigrana?
Assolutamente! GroupDocs.Watermark offre ampie opzioni di personalizzazione per filigrane di testo e immagini, consentendo agli utenti di regolare dimensioni, posizione, opacità e altri parametri.
### GroupDocs.Watermark è adatto per l'elaborazione batch di documenti?
Certamente! GroupDocs.Watermark offre efficienti funzionalità di elaborazione batch, consentendo agli utenti di applicare filigrane a più documenti contemporaneamente.
### GroupDocs.Watermark supporta lo sviluppo di .NET Core?
Sì, GroupDocs.Watermark supporta .NET Core, consentendo agli sviluppatori di integrare funzionalità di filigrana in applicazioni multipiattaforma.
### Il supporto tecnico è disponibile per gli utenti di GroupDocs.Watermark?
Sì, GroupDocs fornisce supporto tecnico completo attraverso i suoi forum dedicati e i canali del servizio clienti.