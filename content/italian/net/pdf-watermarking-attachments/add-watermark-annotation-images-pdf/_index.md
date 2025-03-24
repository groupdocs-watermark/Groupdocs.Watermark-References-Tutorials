---
title: Aggiungi filigrana alle immagini di annotazione nel PDF
linktitle: Aggiungi filigrana alle immagini di annotazione nel PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come proteggere i tuoi documenti PDF aggiungendo filigrane alle immagini delle annotazioni utilizzando Groupdocs.Watermark per .NET.
weight: 17
url: /it/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# Aggiungi filigrana alle immagini di annotazione nel PDF

## introduzione
In questo tutorial esploreremo come aggiungere filigrane alle immagini di annotazione nei documenti PDF utilizzando Groupdocs.Watermark per .NET. La filigrana è fondamentale per proteggere i tuoi documenti dall'uso o dalla distribuzione non autorizzata. Seguendo questa guida passo passo imparerai come applicare filigrane di testo alle immagini delle annotazioni nei PDF in modo efficace.
## Prerequisiti
Prima di procedere, assicurati di avere quanto segue:
1. Conoscenza base del linguaggio di programmazione C#.
2. Groupdocs.Watermark installato per la libreria .NET.
3. Accesso a un ambiente di sviluppo come Visual Studio.
4. Un documento PDF con immagini di annotazioni su cui applicare la filigrana.

## Importazione di spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo codice C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## Passaggio 2: ottieni contenuto PDF e inizializza la filigrana
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Inizializza la filigrana dell'immagine o del testo
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Passaggio 3: scorrere le pagine PDF e le immagini delle annotazioni
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Aggiungi filigrana all'immagine
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Passaggio 4: salva il documento con filigrana
```csharp
    watermarker.Save(outputFileName);
}
```
Dopo aver eseguito questi passaggi, il documento PDF avrà la filigrana specificata aggiunta alle immagini delle annotazioni.

## Conclusione
L'aggiunta di filigrane alle immagini delle annotazioni nei PDF è essenziale per proteggere l'integrità dei documenti e garantire che non vengano utilizzati in modo improprio. Con Groupdocs.Watermark per .NET, questo processo diventa semplice ed efficiente, consentendoti di salvaguardare i tuoi file PDF in modo efficace.
## Domande frequenti
### Posso aggiungere più filigrane allo stesso documento PDF?
Sì, puoi aggiungere più filigrane allo stesso documento PDF utilizzando Groupdocs.Watermark per .NET.
### Groupdocs.Watermark supporta altri formati di documenti oltre al PDF?
Sì, Groupdocs supporta vari formati di documenti, tra cui Word, Excel, PowerPoint e altri.
### È possibile personalizzare l'aspetto della filigrana?
Assolutamente, puoi personalizzare il testo, il carattere, il colore, la dimensione e la posizione della filigrana in base alle tue preferenze.
### Posso rimuovere filigrane dai documenti PDF utilizzando Groupdocs.Watermark?
Sì, Groupdocs.Watermark fornisce funzionalità per rimuovere facilmente le filigrane dai documenti PDF.
### È disponibile una prova gratuita per Groupdocs.Watermark per .NET?
Sì, puoi usufruire di una prova gratuita di Groupdocs.Watermark per .NET dal sito web.