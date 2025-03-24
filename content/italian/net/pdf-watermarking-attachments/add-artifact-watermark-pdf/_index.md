---
title: Aggiungi filigrana artefatto al PDF
linktitle: Aggiungi filigrana artefatto al PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di artefatti ai file PDF senza sforzo utilizzando Groupdocs.Watermark per .NET. Proteggi i tuoi documenti con facilità.
weight: 11
url: /it/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## introduzione
L'aggiunta di filigrane ai file PDF è un aspetto cruciale della gestione dei documenti, soprattutto quando si tratta di proteggere la proprietà intellettuale o i documenti di branding. Groupdocs.Watermark per .NET fornisce una soluzione solida per aggiungere filigrane ai file PDF senza sforzo. In questo tutorial, esamineremo passo dopo passo il processo di aggiunta di una filigrana artefatto ai file PDF.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1.  Groupdocs.Watermark per .NET: scarica e installa Groupdocs.Watermark per .NET da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente di sviluppo: disporre di un ambiente di sviluppo .NET configurato.
3. Documento PDF: prepara il documento PDF a cui desideri aggiungere la filigrana.
4. Directory di output: crea una directory per salvare il file PDF con filigrana.

## Importazione di spazi dei nomi
Per cominciare, importa gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using GroupDocs.Watermark.Common;
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
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Passaggio 3: aggiungi filigrana di testo
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Passaggio 4: aggiungi la filigrana dell'immagine
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Passaggio 5: salva il PDF con filigrana
```csharp
watermarker.Save(outputFileName);
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere filigrane di artefatti ai file PDF utilizzando Groupdocs.Watermark per .NET. Seguendo questi passaggi, puoi integrare perfettamente la funzionalità di filigrana nelle tue applicazioni .NET, garantendo la sicurezza e l'integrità dei tuoi documenti.
## Domande frequenti
### Posso personalizzare l'aspetto della filigrana del testo?
Sì, puoi personalizzare vari aspetti come carattere, dimensione, colore e allineamento della filigrana del testo in base alle tue preferenze.
### Groupdocs.Watermark supporta l'aggiunta di filigrane ad altri formati di documenti?
Sì, Groupdocs.Watermark supporta l'aggiunta di filigrane a un'ampia gamma di formati di documenti tra cui Word, Excel, PowerPoint e altri.
### È disponibile una versione di prova per Groupdocs.Watermark per .NET?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per eventuali problemi o domande relative a Groupdocs.Watermark?
 Puoi ottenere supporto dal forum della community di Groupdocs[Qui](https://forum.groupdocs.com/c/watermark/19).
### Posso utilizzare Groupdocs.Watermark per scopi commerciali?
Sì, puoi acquistare una licenza per uso commerciale da[Qui](https://purchase.groupdocs.com/buy).