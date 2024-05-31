---
title: Aggiungi filigrana per dare forma alle immagini nei documenti Word
linktitle: Aggiungi filigrana per dare forma alle immagini nei documenti Word
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane per dare forma alle immagini nei documenti Word utilizzando GroupDocs.Watermark per .NET. Migliora la sicurezza dei documenti con questo tutorial.
type: docs
weight: 17
url: /it/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## introduzione
In questo tutorial esploreremo come aggiungere una filigrana per modellare le immagini all'interno dei documenti Word utilizzando GroupDocs.Watermark per .NET. La filigrana è un aspetto cruciale della protezione dei documenti, soprattutto quando si tratta di informazioni sensibili o riservate. Aggiungendo filigrane per dare forma alle immagini, puoi garantire l'integrità e la sicurezza dei tuoi documenti.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Watermark per .NET: scarica e installa la libreria GroupDocs.Watermark da[pagina di download](https://releases.groupdocs.com/Watermark/net/).
2. Documento: prepara il documento Word in cui desideri aggiungere la filigrana.
3. Ambiente di sviluppo: configura il tuo ambiente di sviluppo .NET preferito.
## Importa spazi dei nomi
Prima di scrivere il codice, assicurati di importare gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
Innanzitutto, definisci il percorso del tuo documento e specifica il nome del file di output:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Passaggio 2: inizializza Watermarker
 Istanziare a`Watermarker` oggetto fornendo il percorso del documento e le opzioni di caricamento facoltative:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Aggiungi qui la logica della filigrana
}
```
## Passaggio 3: crea una filigrana di testo
Definisci la filigrana del testo con le proprietà desiderate come testo, carattere, allineamento, rotazione, ridimensionamento, ecc.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Passaggio 4: applica la filigrana alle immagini di forma
Scorrere le sezioni e le forme del documento per identificare le immagini delle forme e aggiungere la filigrana:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Passaggio 5: salva il documento
Salva il documento con la filigrana aggiunta nel file di output specificato:
```csharp
watermarker.Save(outputFileName);
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere filigrane per modellare le immagini nei documenti Word utilizzando GroupDocs.Watermark per .NET. Seguendo la guida passo passo e sfruttando le potenti funzionalità di GroupDocs.Watermark, puoi migliorare la sicurezza e la protezione dei tuoi documenti in modo efficace.
## Domande frequenti
### Posso personalizzare l'aspetto del testo della filigrana?
Sì, puoi regolare varie proprietà come carattere, dimensione, colore, angolo di rotazione e allineamento per personalizzare la filigrana in base alle tue preferenze.
### GroupDocs.Watermark supporta altri formati di documenti oltre a Word?
Sì, GroupDocs.Watermark fornisce supporto per un'ampia gamma di formati di documenti tra cui PDF, Excel, PowerPoint e altri.
### È possibile aggiungere più filigrane a un singolo documento?
Assolutamente, puoi aggiungere più filigrane con contenuti, stili e posizioni diversi all'interno dello stesso documento.
### Posso rimuovere filigrane dai documenti utilizzando GroupDocs.Watermark?
Sì, GroupDocs.Watermark offre funzionalità per rilevare e rimuovere filigrane dai documenti in modo efficiente.
### GroupDocs.Watermark fornisce compatibilità multipiattaforma?
Sì, GroupDocs.Watermark è compatibile con .NET Framework, .NET Core e .NET Standard, garantendo un'integrazione perfetta tra piattaforme diverse.