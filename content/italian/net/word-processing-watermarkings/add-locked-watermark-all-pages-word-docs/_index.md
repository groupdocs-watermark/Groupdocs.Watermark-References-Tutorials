---
title: Aggiungi filigrana bloccata a tutte le pagine in documenti Word
linktitle: Aggiungi filigrana bloccata a tutte le pagine in documenti Word
second_title: API GroupDocs.Watermark .NET
description: Proteggi i tuoi documenti aggiungendo filigrane bloccate utilizzando Groupdocs.Watermark per .NET. Segui la nostra guida passo passo per una facile implementazione.
type: docs
weight: 11
url: /it/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---
## introduzione
L'aggiunta di filigrane ai tuoi documenti è un passaggio fondamentale per proteggere e marchiare i tuoi contenuti. Che tu voglia impedire l'uso non autorizzato o semplicemente aggiungere un tocco professionale, le filigrane possono servire a molteplici scopi. In questo tutorial ti guideremo attraverso il processo di aggiunta di una filigrana bloccata a tutte le pagine di un documento Word utilizzando Groupdocs.Watermark per .NET.
## Prerequisiti
Prima di immergerci nella guida passo passo, assicuriamoci di avere tutto ciò di cui hai bisogno:
1. Groupdocs.Watermark per .NET: scarica la versione più recente da[Qui](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: assicurati di avere .NET Framework installato sul tuo computer.
3. Ambiente di sviluppo: un ambiente di sviluppo come Visual Studio.
4.  Licenza: puoi optare per a[prova gratuita](https://releases.groupdocs.com/) o acquistare un[licenza temporanea](https://purchase.groupdocs.com/temporary-license/).
## Importa spazi dei nomi
Per prima cosa, devi importare gli spazi dei nomi necessari nel tuo progetto. Questi sono essenziali per accedere alle classi e ai metodi forniti da Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passaggio 1: imposta il tuo progetto

Apri il tuo ambiente di sviluppo e crea un nuovo progetto .NET. Può trattarsi di un'applicazione console o di qualsiasi altro tipo adatto alle tue esigenze.

Devi aggiungere il pacchetto Groupdocs.Watermark al tuo progetto. Questa operazione può essere eseguita tramite Gestione pacchetti NuGet. Eseguire il comando seguente nella console di gestione pacchetti NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Passaggio 2: caricare il documento Word
### Definire il percorso del documento
Specifica il percorso del tuo documento Word. Questo sarà il documento in cui desideri aggiungere la filigrana.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Imposta le opzioni di caricamento
 Crea un'istanza di`WordProcessingLoadOptions` per caricare il tuo documento Word con opzioni specifiche.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Passaggio 3: crea la filigrana
### Inizializza filigrana
 Usando il`Watermarker`class, carica il documento con le opzioni di caricamento specificate.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ulteriori passaggi saranno all'interno di questo using block
}
```
### Definire le proprietà della filigrana
 Creare un`TextWatermark` esempio con il testo, il carattere e il colore desiderati.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Passaggio 4: applica la filigrana a tutte le pagine
### Imposta le opzioni della filigrana
 Definire`WordProcessingWatermarkPagesOptions` e impostare il`IsLocked` proprietà su true per bloccare la filigrana. Ciò garantisce che la filigrana non possa essere rimossa facilmente.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Facoltativo: aggiungi la protezione tramite password
Se desideri aggiungere un ulteriore livello di sicurezza, puoi impostare una password per la filigrana.
```csharp
// Da proteggere con password
// opzioni.Password = "7654321";
```
### Aggiungi la filigrana
 Usa il`Add` metodo del`Watermarker` classe per aggiungere la filigrana al documento con le opzioni specificate.
```csharp
watermarker.Add(watermark, options);
```
## Passaggio 5: salva il documento
Infine, salva il documento modificato nel file di output specificato.
```csharp
watermarker.Save(outputFileName);
```

## Conclusione
Seguendo questi passaggi, puoi facilmente aggiungere una filigrana bloccata a tutte le pagine dei tuoi documenti Word utilizzando Groupdocs.Watermark per .NET. Questo non solo aiuta a proteggere i tuoi documenti dall'uso non autorizzato, ma aggiunge anche un tocco professionale ai tuoi contenuti. Groupdocs.Watermark offre una soluzione completa per le esigenze di filigrana, garantendo che i tuoi documenti rimangano sicuri e marchiati.
## Domande frequenti
### Posso utilizzare un'immagine come filigrana al posto del testo?
 Sì, Groupdocs supporta filigrane sia di testo che di immagini. Puoi sostituire`TextWatermark` con`ImageWatermark` e specifica la tua immagine.
### È possibile personalizzare la posizione della filigrana?
 Assolutamente! Puoi impostare la posizione della filigrana utilizzando proprietà come`HorizontalAlignment` E`VerticalAlignment`.
### Posso applicare filigrane diverse a pagine diverse del documento?
 Sì, puoi personalizzare le filigrane per pagine specifiche utilizzando il file`PageIndex` proprietà nel`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark supporta altri formati di documenti oltre a Word?
Sì, Groupdocs supporta vari formati tra cui PDF, Excel, PowerPoint e altri.
### Quali sono i requisiti di sistema per l'utilizzo di Groupdocs.Watermark?
È necessario un sistema con .NET Framework installato e un ambiente di sviluppo come Visual Studio.