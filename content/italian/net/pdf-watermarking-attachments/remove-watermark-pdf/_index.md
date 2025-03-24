---
title: Rimuovi la filigrana dal PDF
linktitle: Rimuovi la filigrana dal PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come rimuovere le filigrane dai file PDF utilizzando GroupDocs.Watermark per .NET. Semplici passaggi per la modifica professionale dei documenti.
weight: 34
url: /it/net/pdf-watermarking-attachments/remove-watermark-pdf/
---

# Rimuovi la filigrana dal PDF

## introduzione
Nell'era digitale di oggi, proteggere i documenti sensibili con filigrane è una pratica comune. Tuttavia, in alcuni casi potrebbe essere necessario rimuovere le filigrane dai file PDF per vari motivi. Che tu stia modificando un documento o semplicemente abbia bisogno di una versione pulita per la presentazione, GroupDocs.Watermark per .NET fornisce una soluzione perfetta per rimuovere filigrane dai file PDF.
## Prerequisiti
Prima di approfondire la rimozione delle filigrane dai file PDF utilizzando GroupDocs.Watermark per .NET, assicurati di disporre dei seguenti prerequisiti:
1.  GroupDocs.Watermark per .NET Library: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente di sviluppo: sul tuo sistema è installato Visual Studio o qualsiasi IDE compatibile.
3. Documento con filigrana: prepara un documento PDF contenente la filigrana che desideri rimuovere.

## Importazione di spazi dei nomi
Nel tuo progetto C#, inizia importando gli spazi dei nomi necessari:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Passaggio 1: caricare il documento PDF
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
In questo passaggio, specifica il percorso del tuo documento PDF e la directory in cui desideri salvare il file di output.
## Passaggio 2: inizializza filigrana e criteri di ricerca
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
Inizializza l'oggetto Filigrana con il percorso del documento PDF e le opzioni di caricamento. Quindi, definisci i criteri di ricerca per la filigrana che desideri rimuovere. Puoi cercare filigrane in base a immagini o testo.
## Passaggio 3: cerca e rimuovi filigrane
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // Rimuovi tutte le filigrane trovate
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
Cerca eventuali filigrane sulla prima pagina del documento PDF in base ai criteri di ricerca definiti. Quindi, scorri la raccolta di possibili filigrane e rimuovili uno per uno. Infine, salva il documento PDF modificato senza filigrana.

## Conclusione
Rimuovere le filigrane dai file PDF è un compito cruciale in vari scenari, dalla modifica dei documenti alla preparazione delle presentazioni. Con GroupDocs.Watermark per .NET, puoi rimuovere facilmente le filigrane dai file PDF utilizzando un semplice codice C#, garantendo che i tuoi documenti siano puliti e professionali.
## Domande frequenti
### GroupDocs.Watermark per .NET è compatibile con tutte le versioni di Visual Studio?
Sì, GroupDocs.Watermark per .NET è compatibile con tutte le versioni di Visual Studio, inclusi Visual Studio 2019 e Visual Studio 2022.
### Posso rimuovere più filigrane da un singolo documento PDF utilizzando GroupDocs.Watermark per .NET?
Sì, puoi cercare e rimuovere più filigrane da un singolo documento PDF specificando i criteri di ricerca appropriati.
### GroupDocs.Watermark per .NET supporta altri formati di documenti oltre al PDF?
Sì, GroupDocs.Watermark per .NET supporta un'ampia gamma di formati di documenti, inclusi documenti Word, fogli di calcolo Excel, presentazioni PowerPoint e altro ancora.
### È disponibile una versione di prova per GroupDocs.Watermark per .NET?
 Sì, puoi scaricare una versione di prova gratuita di GroupDocs.Watermark per .NET da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare ulteriore supporto e assistenza per GroupDocs.Watermark per .NET?
 Per ulteriore supporto, puoi visitare il forum GroupDocs.Watermark[Qui](https://forum.groupdocs.com/c/watermark/19).