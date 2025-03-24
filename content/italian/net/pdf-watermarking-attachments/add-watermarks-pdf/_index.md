---
title: Aggiungi filigrane al PDF
linktitle: Aggiungi filigrane al PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di testo e immagini ai tuoi PDF utilizzando GroupDocs.Watermark per .NET con la nostra guida passo passo completa.
weight: 14
url: /it/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## introduzione
Stai cercando di aggiungere filigrane ai tuoi PDF per proteggere i tuoi documenti o marchiarli con il tuo logo? Non guardare oltre! In questo tutorial, approfondiremo il processo di utilizzo di GroupDocs.Watermark per .NET per aggiungere filigrane di testo e immagini ai tuoi file PDF. Che tu sia uno sviluppatore esperto o che tu abbia appena iniziato, questa guida ti guiderà attraverso ogni passaggio, assicurandoti di poter applicare le filigrane con facilità e precisione.
## Prerequisiti
Prima di iniziare, assicuriamoci di avere tutto ciò di cui hai bisogno per seguire questo tutorial:
-  GroupDocs.Watermark per .NET: assicurati di avere installata la versione più recente. Puoi[scaricalo qui](https://releases.groupdocs.com/Watermark/net/).
- Ambiente di sviluppo .NET: Visual Studio o qualsiasi altro IDE che supporti .NET.
- Conoscenza di base di C#: comprendere le basi della programmazione C# ti aiuterà a seguire i passaggi con facilità.
- Documento PDF: tieni pronto un documento PDF di esempio per la filigrana.
- Immagine per filigrana: se stai aggiungendo una filigrana immagine, tieni pronto il file immagine.
## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto C#. Ciò ti consentirà di accedere alla funzionalità GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Ora suddividiamo il processo in passaggi gestibili.
## Passaggio 1: carica il documento PDF
Il primo passo è caricare il documento PDF nella filigrana. Ecco come puoi farlo:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ulteriori passaggi verranno aggiunti qui
}
```
## Passaggio 2: aggiungi una filigrana di testo alla prima pagina
Successivamente, aggiungeremo una filigrana di testo alla prima pagina del tuo PDF. Segui queste istruzioni:
```csharp
// Aggiungi una filigrana di testo alla prima pagina
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

L'aggiunta di una filigrana di testo può aiutare a proteggere il documento dall'uso non autorizzato o semplicemente a marchiarlo. Immagina di timbrare il tuo documento con un sigillo di autenticità invisibile.
## Passaggio 3: aggiungi una filigrana immagine alla seconda pagina
Ora aggiungiamo una filigrana immagine alla seconda pagina. Ciò è particolarmente utile per i loghi o qualsiasi filigrana grafica.
```csharp
// Aggiungi la filigrana dell'immagine alla seconda pagina
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Le filigrane delle immagini possono conferire ai tuoi documenti un aspetto professionale e garantire che il tuo marchio sia sempre visibile. È come aggiungere la tua firma su ogni pagina.
## Passaggio 4: salva il PDF con filigrana
Dopo aver aggiunto le filigrane, il passaggio finale è salvare il PDF con filigrana nella posizione desiderata.
```csharp
watermarker.Save(outputFileName);
```
Il salvataggio del documento finalizza tutte le modifiche apportate. Questo è il momento in cui i tuoi sforzi si concretizzano in un risultato tangibile, pronto per l'uso o la distribuzione.
## Conclusione
Congratulazioni! Hai aggiunto con successo filigrane di testo e immagini al tuo PDF utilizzando GroupDocs.Watermark per .NET. Questo processo non è solo semplice ma anche altamente personalizzabile per soddisfare le tue esigenze specifiche. Che tu stia proteggendo i tuoi documenti o marchiandoli, le filigrane sono un potente strumento a tua disposizione.
## Domande frequenti
### Posso aggiungere più filigrane alla stessa pagina?
 Sì, puoi aggiungere più filigrane alla stessa pagina chiamando il comando`Add` metodo più volte con diversi oggetti filigrana.
### Come posso personalizzare l'aspetto della filigrana del testo?
 È possibile personalizzare la filigrana del testo regolando proprietà quali carattere, dimensione, colore e opacità utilizzando il file`TextWatermark` oggetto.
### È possibile filigranare solo pagine specifiche di un PDF?
 Sì, puoi specificare a quali pagine applicare la filigrana impostando il file`PageIndex` proprietà nel`PdfArtifactWatermarkOptions`.
### Posso rimuovere filigrane da un PDF?
Sì, GroupDocs.Watermark fornisce funzionalità per cercare e rimuovere filigrane dai documenti PDF.
### Come posso ottenere una licenza temporanea per GroupDocs.Watermark?
Puoi ottenere una licenza temporanea visitando il sito[pagina della licenza temporanea](https://purchase.groupdocs.com/temporary-license/).