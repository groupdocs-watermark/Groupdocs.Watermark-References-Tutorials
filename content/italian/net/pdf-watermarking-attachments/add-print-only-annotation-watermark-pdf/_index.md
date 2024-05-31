---
title: Aggiungi filigrana di annotazione di sola stampa al PDF
linktitle: Aggiungi filigrana di annotazione di sola stampa al PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di annotazioni di sola stampa ai PDF utilizzando GroupDocs.Watermark per .NET. Migliora la sicurezza e il branding dei documenti senza sforzo.
type: docs
weight: 13
url: /it/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## introduzione
In questo tutorial, approfondiremo il processo di aggiunta di una filigrana di annotazione di sola stampa a un PDF utilizzando GroupDocs.Watermark per .NET. L'applicazione della filigrana ai documenti è un aspetto cruciale della sicurezza e del branding dei documenti e GroupDocs.Watermark fornisce una soluzione perfetta per gli sviluppatori .NET per raggiungere questo obiettivo.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
- Conoscenza base del linguaggio di programmazione C#.
- Visual Studio installato sul tuo computer.
- Libreria GroupDocs.Watermark per .NET installata nel tuo progetto.

## Importa spazi dei nomi
Per iniziare, assicurati di importare gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento
 Innanzitutto, devi caricare il documento PDF a cui desideri applicare la filigrana. Sostituire`"Your Document Path"` con il percorso del file PDF e`"Your Document Directory"` con la directory in cui desideri salvare il file di output.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il codice di filigrana verrà aggiunto qui
}
```
## Passaggio 2: aggiungi filigrana
Successivamente, crea un oggetto filigrana di testo con il testo e il carattere desiderati. Impostato`isPrintOnly` A`true` per garantire che la filigrana sia visibile solo quando il documento viene stampato, non in modalità di visualizzazione.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Passaggio 3: configura le opzioni della filigrana
Definire le opzioni per la filigrana, come l'indice della pagina in cui aggiungere la filigrana e specificarla come annotazione di sola stampa.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Passaggio 4: applica la filigrana
Aggiungi la filigrana al documento utilizzando le opzioni specificate e salva il file di output.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere una filigrana di annotazione di sola stampa a un documento PDF utilizzando GroupDocs.Watermark per .NET. Ciò consente agli sviluppatori di migliorare facilmente la sicurezza e il branding dei documenti.
## Domande frequenti
### GroupDocs.Watermark è compatibile con altri formati di documenti oltre al PDF?
Sì, GroupDocs supporta vari formati di documenti come Word, Excel, PowerPoint e immagini.
### Posso personalizzare l'aspetto della filigrana?
Certamente, GroupDocs.Watermark offre ampie opzioni per personalizzare il testo, il carattere, il colore, la dimensione e il posizionamento della filigrana.
### GroupDocs.Watermark offre funzionalità di elaborazione batch?
Assolutamente, gli sviluppatori possono filigranare più documenti contemporaneamente utilizzando le funzionalità di elaborazione batch.
### È disponibile una versione di prova per GroupDocs.Watermark?
Sì, puoi accedere a una versione di prova gratuita di GroupDocs.Watermark dal collegamento fornito.
### Come posso ottenere supporto tecnico per GroupDocs.Watermark?
È possibile richiedere assistenza tecnica al forum GroupDocs.Watermark disponibile al collegamento di supporto fornito.