---
title: Aggiungi filigrana a XObjects nel PDF
linktitle: Aggiungi filigrana a XObjects nel PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane a XObjects in PDF utilizzando Groupdocs.Watermark per .NET. Segui la nostra guida passo passo per una facile implementazione.
weight: 20
url: /it/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# Aggiungi filigrana a XObjects nel PDF

## introduzione
La filigrana dei PDF è un passaggio cruciale per garantire che i tuoi documenti siano protetti dall'uso non autorizzato. Con Groupdocs.Watermark per .NET, aggiungere filigrane a XObjects nei tuoi PDF non è mai stato così facile. In questo tutorial ti guideremo attraverso il processo passo dopo passo, assicurandoti di poter applicare con sicurezza le filigrane ai tuoi documenti PDF. Iniziamo!
## Prerequisiti
Prima di immergerti nel tutorial, assicuriamoci di avere tutto ciò di cui hai bisogno per seguire senza problemi:
-  Groupdocs.Watermark per .NET: scarica e installa la versione più recente da[Qui](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: assicurati di avere .NET Framework installato sul tuo computer di sviluppo.
- Ambiente di sviluppo: utilizza Visual Studio o qualsiasi altro IDE che supporti lo sviluppo .NET.
-  Licenza temporanea: ottenere a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) se stai valutando il prodotto.
Una volta stabiliti questi prerequisiti, sei pronto per iniziare ad applicare la filigrana ai tuoi PDF.
## Importa spazi dei nomi
Innanzitutto, dovrai importare gli spazi dei nomi necessari nel tuo progetto. Apri il tuo progetto C# e aggiungi le seguenti direttive using:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: imposta i percorsi dei documenti
Il primo passaggio prevede l'impostazione dei percorsi per il documento. Definisci il percorso in cui si trova il tuo PDF e dove desideri salvare il PDF con filigrana.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` E`"Your Document Directory"` con i percorsi effettivi sul tuo computer.
## Passaggio 2: inizializza le opzioni di caricamento del PDF
Successivamente, dovrai inizializzare le opzioni di caricamento del PDF. Questo è fondamentale per caricare correttamente il contenuto del PDF.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Passaggio 3: caricare il documento PDF
Utilizzando le opzioni di caricamento, carica il documento PDF con il file`Watermarker` classe.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Passaggio 4: crea la filigrana
Ora devi creare la filigrana che verrà aggiunta al PDF. Per questo tutorial, creeremo una filigrana di testo.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Passaggio 5: aggiungi la filigrana a XObjects
Scorri ogni pagina e ogni XObject all'interno del PDF per applicare la filigrana.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Aggiungi filigrana all'immagine
            xObject.Image.Add(watermark);
        }
    }
}
```
## Passaggio 6: salva il PDF con filigrana
Infine, salva il PDF con filigrana nel file di output specificato.
```csharp
    watermarker.Save(outputFileName);
}
```
E il gioco è fatto! Il tuo PDF ora contiene filigrane su tutti i suoi XObject.
## Conclusione
 Aggiungere filigrane ai tuoi documenti PDF utilizzando Groupdocs per .NET è un processo semplice che fornisce un ulteriore livello di sicurezza. Seguendo i passaggi descritti in questo tutorial, puoi assicurarti che i tuoi documenti siano protetti dall'uso non autorizzato. Ricorda che puoi sempre fare riferimento a[documentazione](https://tutorials.groupdocs.com/Watermark/net/) per informazioni più dettagliate e funzionalità avanzate.
## Domande frequenti
### Posso utilizzare un'immagine come filigrana al posto del testo?
Sì, Groupdocs.Watermark per .NET supporta filigrane sia di testo che di immagini.
### Come posso testare Groupdocs.Watermark senza acquistarlo?
 Puoi usare a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) per valutare il prodotto.
### È possibile personalizzare l'aspetto della filigrana?
Assolutamente! Puoi personalizzare il carattere, la dimensione, l'angolo di rotazione e altro.
### Groupdocs.Watermark supporta altri formati di documenti?
Sì, supporta vari formati, inclusi Word, Excel e PowerPoint.
### Dove posso ottenere supporto se riscontro problemi?
 Puoi ottenere supporto da[Forum dei documenti di gruppo](https://forum.groupdocs.com/c/watermark/19).