---
title: Aggiungi filigrana a una pagina specifica in documenti Word
linktitle: Aggiungi filigrana a una pagina specifica in documenti Word
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane a pagine specifiche nei documenti Word utilizzando GroupDocs per .NET. Proteggi i tuoi contenuti senza sforzo.
weight: 14
url: /it/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---

# Aggiungi filigrana a una pagina specifica in documenti Word

## introduzione
La filigrana dei documenti è un aspetto cruciale della sicurezza e del branding dei documenti. In questo tutorial esploreremo come aggiungere una filigrana a una pagina specifica nei documenti di Word utilizzando GroupDocs.Watermark per .NET.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
- Conoscenza base della programmazione C#.
- IDE di Visual Studio installato.
- GroupDocs.Watermark per .NET installato nel tuo progetto.

## Importazione di spazi dei nomi
Prima di immergerti nel codice, assicurati di importare gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il tuo codice andrà qui
}
```
## Passaggio 2: aggiungi la filigrana
```csharp
// Definire il testo e lo stile della filigrana
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Aggiungi filigrana all'ultima pagina
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Passaggio 3: salva il documento
```csharp
// Salva il documento con la filigrana
watermarker.Save(outputFileName);
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere una filigrana a una pagina specifica nei documenti di Word utilizzando GroupDocs.Watermark per .NET. Seguendo questi passaggi, puoi proteggere efficacemente i tuoi documenti e aggiungere elementi di branding secondo necessità.
## Domande frequenti
### Posso personalizzare il testo e lo stile della filigrana?
Sì, puoi personalizzare il testo, il carattere, la dimensione, il colore e la posizione della filigrana in base alle tue esigenze.
### GroupDocs.Watermark per .NET è compatibile con altri formati di documenti?
Sì, GroupDocs.Watermark supporta vari formati di documenti, tra cui Word, Excel, PowerPoint, PDF e altri.
### Posso aggiungere più filigrane a un singolo documento?
Assolutamente, puoi aggiungere più filigrane con contenuti e stili diversi allo stesso documento.
### È disponibile una prova gratuita per GroupDocs.Watermark per .NET?
 Sì, puoi esplorare le funzionalità di GroupDocs.Watermark con una prova gratuita. Per iniziare è sufficiente visitare il collegamento fornito[Qui](https://releases.groupdocs.com/).
### Dove posso ottenere supporto tecnico per GroupDocs.Watermark?
 È possibile trovare risorse utili e ottenere supporto tecnico da[Qui](https://forum.groupdocs.com/c/watermark/19)il forum GroupDocs.Watermark. Visita il collegamento fornito per unirti alla community.