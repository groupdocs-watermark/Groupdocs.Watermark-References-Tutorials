---
title: Aggiungi filigrana immagine a tutte le intestazioni nei documenti Word
linktitle: Aggiungi filigrana immagine a tutte le intestazioni nei documenti Word
second_title: API GroupDocs.Watermark .NET
description: Aggiungi facilmente filigrane di immagini a tutte le intestazioni nei documenti Word utilizzando GroupDocs.Watermark per .NET. Segui la nostra guida passo passo con esempi di codice dettagliati.
weight: 10
url: /it/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

# Aggiungi filigrana immagine a tutte le intestazioni nei documenti Word

## introduzione
Le filigrane possono rappresentare una parte essenziale della gestione dei documenti, poiché forniscono un modo per incorporare informazioni come proprietà, riservatezza o marchio nei documenti. In questo tutorial, esamineremo i passaggi per aggiungere una filigrana di immagine a tutte le intestazioni nei documenti di Word utilizzando GroupDocs.Watermark per .NET. Che tu sia un principiante nella programmazione o uno sviluppatore esperto, questa guida ti aiuterà a raggiungere facilmente i tuoi obiettivi di filigrana.
## Prerequisiti
Prima di immergerci nel codice, assicuriamoci di avere tutto ciò di cui abbiamo bisogno. Ecco una lista di controllo per iniziare:
1.  GroupDocs.Watermark per .NET: scarica la versione più recente da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE compatibile con .NET.
3. .NET Framework: assicurati di avere installato .NET Framework.
4. Documento Word di esempio: un documento Word in cui desideri aggiungere la filigrana.
5. Immagine per filigrana: un file immagine che desideri utilizzare come filigrana.
Una volta pronti, possiamo iniziare a impostare il nostro progetto.
## Importa spazi dei nomi
Per prima cosa importiamo gli spazi dei nomi necessari. Questi spazi dei nomi contengono classi e metodi che ci aiuteranno a lavorare con le filigrane nei nostri documenti.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: impostazione del progetto
Per iniziare, crea una nuova applicazione console in Visual Studio. Aggiungi riferimenti alla DLL GroupDocs.Watermark nel tuo progetto. Questa operazione può essere eseguita installando il pacchetto NuGet GroupDocs.Watermark.
```bash
Install-Package GroupDocs.Watermark
```
## Passaggio 2: carica il documento
 Il primo passo per aggiungere una filigrana è caricare il documento in cui verrà aggiunta la filigrana. Qui useremo il file`WordProcessingLoadOptions` per caricare un documento Word.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il codice per aggiungere la filigrana andrà qui
}
```
## Passaggio 3: crea la filigrana dell'immagine
Successivamente, creeremo una filigrana dell'immagine. Ciò implica specificare il file immagine che desideri utilizzare come filigrana.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Il codice per applicare la filigrana andrà qui
}
```
## Passaggio 4: aggiungi la filigrana alle intestazioni della prima sezione
 Dobbiamo aggiungere la filigrana a tutte le intestazioni nella prima sezione del documento Word. Per questo usiamo`WordProcessingWatermarkSectionOptions` e specificare l'indice della sezione.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Passaggio 5: collega intestazioni e piè di pagina
Per garantire che la filigrana venga visualizzata nelle intestazioni di tutte le sezioni, colleghiamo tutte le altre intestazioni e piè di pagina alle intestazioni e ai piè di pagina della prima sezione.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Passaggio 6: salva il documento
Infine, salviamo il documento con filigrana in un percorso specificato. Questo passaggio garantisce che le modifiche vengano scritte in un nuovo file, preservando il documento originale.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusione
E il gioco è fatto! Hai aggiunto correttamente una filigrana immagine a tutte le intestazioni in un documento Word utilizzando GroupDocs.Watermark per .NET. Questa potente libreria semplifica la gestione e l'applicazione di filigrane a vari tipi di documenti, garantendo che i tuoi contenuti siano protetti e con marchio professionale.
## Domande frequenti
### Posso utilizzare altri tipi di filigrane oltre alle immagini?
Sì, GroupDocs supporta filigrane di testo, immagini e persino composite.
### È possibile filigranare altre parti del documento oltre alle intestazioni?
Assolutamente! Puoi filigranare piè di pagina, corpo e persino pagine o sezioni specifiche.
### GroupDocs.Watermark supporta altri formati di documenti?
Sì, supporta un'ampia gamma di formati tra cui PDF, Excel, PowerPoint e altri.
### Posso personalizzare la posizione e l'aspetto della filigrana?
Sì, puoi personalizzare le dimensioni, la posizione, l'opacità e molte altre proprietà della filigrana.
### È disponibile una prova gratuita per GroupDocs.Watermark?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).