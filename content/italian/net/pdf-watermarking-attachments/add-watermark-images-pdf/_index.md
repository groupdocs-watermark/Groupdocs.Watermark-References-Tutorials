---
title: Aggiungi filigrana alle immagini in PDF
linktitle: Aggiungi filigrana alle immagini in PDF
second_title: API GroupDocs.Watermark .NET
description: Impara ad aggiungere filigrane alle immagini nei documenti PDF utilizzando GroupDocs.Watermark per .NET con il nostro tutorial dettagliato passo dopo passo. Proteggi facilmente i tuoi PDF.
weight: 19
url: /it/net/pdf-watermarking-attachments/add-watermark-images-pdf/
type: docs
---
# Aggiungi filigrana alle immagini in PDF

## introduzione
Aggiungere filigrane alle immagini all'interno di un documento PDF può essere essenziale per proteggere la tua proprietà intellettuale o garantire l'autenticità dei tuoi documenti. Utilizzando GroupDocs.Watermark per .NET, questa attività può essere eseguita in modo efficiente e semplice. Questo tutorial ti guiderà attraverso ogni fase del processo, dalla configurazione del tuo ambiente all'aggiunta di filigrane fino al salvataggio del documento finale. Immergiamoci!
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. Visual Studio: installa Visual Studio, l'ambiente di sviluppo integrato (IDE) per le applicazioni .NET.
2.  GroupDocs.Watermark per .NET: scaricare e installare la libreria GroupDocs.Watermark per .NET dal[pagina di rilascio](https://releases.groupdocs.com/Watermark/net/).
3. Un documento PDF: disponi di un documento PDF con immagini pronto per testare la funzionalità di filigrana.
4.  Licenza temporanea: ottenere a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) se stai valutando il prodotto.
## Importa spazi dei nomi
Innanzitutto, assicurati di avere importati gli spazi dei nomi necessari nel tuo progetto. Ciò includerà gli spazi dei nomi principali necessari per lavorare con documenti PDF e filigrane.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: impostare il percorso del documento e la directory di output
Per iniziare, definire i percorsi per il documento di input e la directory di output in cui verrà salvato il documento con filigrana. Questo passaggio è fondamentale per garantire che il tuo programma sappia dove trovare il documento sorgente e dove archiviare il file elaborato.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Passaggio 2: carica il documento PDF
 Successivamente, dovrai caricare il documento PDF utilizzando`PdfLoadOptions`. Questa classe consente di specificare le opzioni per il caricamento del PDF, come la protezione tramite password, se necessario.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il tuo codice per la filigrana andrà qui
}
```
## Passaggio 3: crea la filigrana
Ora inizializza la filigrana. In questo esempio, stiamo creando una filigrana di testo con la scritta "Immagine protetta". Personalizza il carattere, l'allineamento, la rotazione e il ridimensionamento in base alle tue esigenze.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Passaggio 4: accedi al contenuto PDF
Recuperare il contenuto del documento PDF. Nello specifico, dobbiamo accedere alle immagini all'interno del PDF. Qui ci concentreremo sulla prima pagina, ma puoi estenderla ad altre pagine secondo necessità.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Ottieni tutte le immagini dalla prima pagina
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Passaggio 5: applica la filigrana alle immagini
Passa in rassegna ogni immagine trovata nella prima pagina e applica la filigrana. Ciò garantisce che a tutte le immagini sulla pagina specificata verrà applicata la filigrana.
```csharp
// Aggiungi filigrana a tutte le immagini trovate
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Passaggio 6: salvare il documento con filigrana
Infine, salva il PDF con filigrana nella directory di output specificata. Questo passaggio finalizza il processo scrivendo le modifiche in un nuovo file.
```csharp
watermarker.Save(outputFileName);
```
## Conclusione
E il gioco è fatto! Aggiungere una filigrana alle immagini all'interno di un PDF utilizzando GroupDocs per .NET è un processo semplice che può migliorare notevolmente la sicurezza e l'autenticità dei tuoi documenti. Seguendo questi passaggi, puoi assicurarti che la tua proprietà intellettuale sia protetta e che i tuoi documenti siano al sicuro.
## Domande frequenti
### Cos'è GroupDocs.Watermark per .NET?
GroupDocs.Watermark per .NET è una libreria completa che consente agli sviluppatori di aggiungere, cercare e rimuovere filigrane in vari formati di documenti, inclusi i PDF.
### Posso aggiungere filigrane sia di testo che di immagini utilizzando GroupDocs.Watermark?
Sì, GroupDocs.Watermark supporta filigrane sia di testo che di immagini, offrendo flessibilità per diversi tipi di esigenze di filigrana.
### È possibile filigranare più pagine in un PDF?
Assolutamente! Puoi scorrere ciascuna pagina del PDF e applicare filigrane alle immagini su ciascuna pagina.
### Ho bisogno di una licenza per utilizzare GroupDocs.Watermark per .NET?
 Sì, è necessaria una licenza. Puoi ottenere a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) a fini di valutazione.
### Dove posso trovare ulteriore documentazione su GroupDocs.Watermark per .NET?
 È possibile trovare una documentazione completa su[Pagina della documentazione GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).