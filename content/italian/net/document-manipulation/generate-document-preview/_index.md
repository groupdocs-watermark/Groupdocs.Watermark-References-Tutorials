---
title: Genera anteprima del documento
linktitle: Genera anteprima del documento
second_title: API GroupDocs.Watermark .NET
description: Scopri come generare anteprime di documenti utilizzando GroupDocs.Watermark per .NET con questa guida. Migliora la sicurezza e la gestione dei tuoi documenti senza sforzo.
weight: 10
url: /it/net/document-manipulation/generate-document-preview/
---

# Genera anteprima del documento

## introduzione
Nel mondo della gestione dei documenti digitali, la filigrana svolge un ruolo cruciale nel garantire la sicurezza e l'autenticità dei documenti. GroupDocs.Watermark per .NET è un potente strumento che consente agli sviluppatori di aggiungere filigrane ai documenti senza sforzo. In questo tutorial ti guideremo attraverso il processo di generazione di anteprime dei documenti utilizzando GroupDocs.Watermark per .NET. Che tu sia uno sviluppatore esperto o che tu abbia appena iniziato, questa guida ti fornirà un processo completo passo dopo passo per raggiungere il tuo obiettivo.
## Prerequisiti
Prima di immergerci nell'implementazione, assicuriamoci di avere tutto il necessario per iniziare:
- Una conoscenza di base di C# e .NET framework.
- Visual Studio installato sul tuo computer.
- GroupDocs.Watermark per la libreria .NET. Puoi[scaricalo qui](https://releases.groupdocs.com/Watermark/net/).
-  Una licenza valida per GroupDocs.Watermark. Puoi acquistarlo[Qui](https://purchase.groupdocs.com/buy) o ottenere a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) a fini di valutazione.
## Importa spazi dei nomi
Per iniziare a utilizzare GroupDocs.Watermark nel tuo progetto, dovrai importare gli spazi dei nomi necessari. Questo può essere fatto aggiungendo le seguenti direttive using al codice:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Questi spazi dei nomi forniranno l'accesso alle classi e ai metodi richiesti per la filigrana e la generazione di anteprime dei documenti.

Analizziamo il processo di generazione di un'anteprima del documento in passaggi semplici e facili da seguire.
## Passaggio 1: imposta il tuo progetto
Per prima cosa, configura il tuo progetto .NET in Visual Studio. Se non hai già un progetto, creane uno nuovo seguendo questi passaggi:
1. Apri VisualStudio.
2. Fare clic su "Crea un nuovo progetto".
3. Selezionare "App console (.NET Core)" e fare clic su "Avanti".
4. Dai un nome al tuo progetto e scegli una posizione in cui salvarlo, quindi fai clic su "Crea".
## Passaggio 2: installare GroupDocs.Watermark per .NET
Per utilizzare GroupDocs.Watermark nel tuo progetto, devi installare la libreria. Questa operazione può essere eseguita utilizzando Gestione pacchetti NuGet:
1. Fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.
2. Seleziona "Gestisci pacchetti NuGet".
3. Cerca "GroupDocs.Watermark" nella scheda Sfoglia.
4. Fai clic su "Installa" per aggiungere la libreria al tuo progetto.
In alternativa, puoi installarlo tramite la Console di gestione pacchetti:
```powershell
Install-Package GroupDocs.Watermark
```
## Passaggio 3: definire il percorso del documento e la directory di output
Prima di generare l'anteprima, è necessario specificare il percorso del documento che si desidera visualizzare in anteprima e la directory in cui verranno salvate le immagini di anteprima:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Sostituisci "Percorso documento" con il percorso del documento e "Directory documenti" con la directory in cui desideri salvare le immagini di anteprima.
## Passaggio 4: inizializza l'oggetto filigrana
Crea un'istanza di`Watermarker` class passando il percorso del documento al suo costruttore. Questo oggetto verrà utilizzato per eseguire tutte le operazioni di watermarking:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Il tuo codice qui
}
```
## Passaggio 5: creare metodi delegati per la gestione del flusso
Per generare l'anteprima, è necessario definire metodi delegati per la creazione e il rilascio dei flussi. Questi metodi gestiranno la creazione e il rilascio di flussi per ogni pagina del documento:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 IL`createPageStreamDelegate` crea uno stream per ogni pagina del documento, mentre il metodo`releasePageStreamDelegate` Il metodo chiude il flusso dopo la generazione dell'anteprima.
## Passaggio 6: configura le opzioni di anteprima
 Successivamente, configura le opzioni di anteprima creando un'istanza di`PreviewOptions` classe. Specificare i metodi delegati e impostare il formato di anteprima su PNG. Puoi anche specificare quali pagine includere nell'anteprima:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
In questo esempio, stiamo generando anteprime per le prime due pagine del documento.
## Passaggio 7: genera l'anteprima del documento
 Infine, chiama il`GeneratePreview` metodo sul`Watermarker`oggetto, passando nel configurato`PreviewOptions`. Questo genererà le immagini di anteprima e le salverà nella directory specificata:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Conclusione
La generazione di anteprime dei documenti utilizzando GroupDocs.Watermark per .NET è un processo semplice che può essere eseguito con poche righe di codice. Seguendo i passaggi descritti in questa guida, puoi facilmente impostare il tuo progetto, configurare le opzioni necessarie e generare anteprime per i tuoi documenti. Questa potente libreria non solo semplifica il processo di filigrana, ma fornisce anche robuste funzionalità per la gestione e la manipolazione delle filigrane.
 Se hai domande o hai bisogno di ulteriore assistenza, non esitare a visitare il[Forum di supporto GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) o fare riferimento a[documentazione](https://tutorials.groupdocs.com/Watermark/net/).
## Domande frequenti
### Quali formati di file sono supportati da GroupDocs.Watermark per .NET?
 GroupDocs.Watermark per .NET supporta un'ampia gamma di formati di file, inclusi PDF, DOCX, PPTX, XLSX e molti altri. Per un elenco completo dei formati supportati, fare riferimento a[documentazione](https://tutorials.groupdocs.com/Watermark/net/).
### Posso personalizzare l'aspetto delle filigrane?
Sì, GroupDocs.Watermark ti consente di personalizzare completamente l'aspetto delle filigrane, incluse filigrane di testo, immagini e forme. Puoi regolare proprietà come carattere, colore, dimensione e trasparenza.
### È disponibile una versione di prova?
 Sì, puoi ottenere un[prova gratuita](https://releases.groupdocs.com/) di GroupDocs.Watermark for .NET per valutarne le caratteristiche prima di effettuare un acquisto.
### Come posso acquistare una licenza per GroupDocs.Watermark?
 È possibile acquistare una licenza per GroupDocs.Watermark[Qui](https://purchase.groupdocs.com/buy). Sono disponibili varie opzioni di licenza per soddisfare le diverse esigenze.
### Posso utilizzare GroupDocs.Watermark in un progetto commerciale?
 Sì, con una licenza valida puoi utilizzare GroupDocs.Watermark in progetti commerciali. Assicurati di rivedere i termini e le condizioni di licenza sul[pagina di acquisto](https://purchase.groupdocs.com/buy).