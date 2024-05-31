---
title: Ottieni informazioni sul documento dal disco locale
linktitle: Ottieni informazioni sul documento dal disco locale
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere, rimuovere ed estrarre filigrane nei documenti utilizzando GroupDocs per .NET con questa guida passo passo completa.
type: docs
weight: 11
url: /it/net/document-manipulation/get-document-info-local-disk/
---
## introduzione
Benvenuti nella guida definitiva sull'utilizzo di GroupDocs.Watermark per .NET! Che tu sia uno sviluppatore esperto o che tu abbia appena iniziato, questo articolo ti guiderà attraverso gli elementi essenziali per applicare la filigrana ai tuoi documenti con questo potente strumento. Alla fine, sarai un professionista nell'incorporare filigrane nei tuoi documenti, assicurandoti che siano protetti e marchiati secondo le tue specifiche.
## Prerequisiti
Prima di immergerti nella guida passo passo, devi soddisfare alcuni prerequisiti:
1.  .NET Framework: assicurati di avere .NET Framework installato sul tuo sistema. GroupDocs.Watermark per .NET è compatibile con varie versioni di .NET Framework, quindi controlla il file[documentazione](https://reference.groupdocs.com/Watermark/net/) per i dettagli sulla compatibilità.
2.  GroupDocs.Watermark per .NET Library: scarica e installa la versione più recente da[pagina di download](https://releases.groupdocs.com/Watermark/net/).
3. Ambiente di sviluppo: è necessario disporre di un ambiente di sviluppo configurato. Visual Studio è una scelta popolare per lo sviluppo .NET.
4. Conoscenza di base di C#: comprendere le basi della programmazione C# ti aiuterà a seguire gli esempi.
## Importa spazi dei nomi
Prima di poter utilizzare GroupDocs.Watermark per .NET, è necessario importare gli spazi dei nomi necessari nel progetto. Questo è un processo semplice ed essenziale per accedere alle funzionalità della libreria.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Analizziamo il processo di filigrana di un documento in passaggi chiari e gestibili. Ogni passaggio è progettato per aiutarti a comprendere e implementare facilmente la funzionalità.
## Passaggio 1: carica il documento
 Il primo passo è caricare il documento a cui vuoi applicare la filigrana. Questo viene fatto utilizzando il`Watermarker` class, che ti consente di accedere e manipolare il tuo documento.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Il documento è ora caricato e pronto per la filigrana
}
```
 In questo passaggio, sostituisci`"Your Document Path"` con il percorso effettivo del documento. Questo inizializza il file`Watermarker`oggetto, dandoti accesso a varie funzionalità di filigrana.
## Passaggio 2: ottieni informazioni sul documento
Prima di aggiungere una filigrana, potresti voler raccogliere alcune informazioni sul documento. Questo può essere utile per personalizzare la filigrana in base alle proprietà del documento.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 In questo passaggio, il`GetDocumentInfo` Il metodo recupera dettagli come tipo di file, conteggio delle pagine e dimensioni del documento. Queste informazioni vengono stampate sulla console, ma puoi utilizzarle nella tua applicazione secondo necessità.
## Passaggio 3: aggiungi una filigrana di testo
Ora che hai caricato il documento e le sue informazioni sono a portata di mano, è il momento di aggiungere una filigrana. Inizieremo con una semplice filigrana di testo.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Qui crei un file`TextWatermark` oggetto con il testo, il carattere e lo stile desiderati. Regola proprietà come colore, opacità e angolo di rotazione in base alle tue esigenze. Infine, la filigrana viene aggiunta al documento e salvata in un percorso specificato.
## Passaggio 4: aggiungi una filigrana immagine
Le filigrane di testo sono fantastiche, ma cosa succede se vuoi aggiungere un logo o un'altra immagine? Questo passaggio spiega come aggiungere una filigrana all'immagine.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Sostituire`"Path to Your Image"` con il percorso dell'immagine della filigrana. Imposta proprietà come l'opacità e l'angolo di rotazione per personalizzare l'aspetto della filigrana dell'immagine. Il processo di aggiunta e salvataggio della filigrana è simile a quello di una filigrana di testo.
## Passaggio 5: rimuovere le filigrane esistenti
 A volte potrebbe essere necessario rimuovere le filigrane esistenti da un documento. Questo può essere fatto utilizzando il`Remove` metodo previsto dal`Watermarker` classe.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Ecco, il`Remove` viene utilizzato per rimuovere filigrane di testo dal documento. Puoi specificare diversi tipi di filigrane da rimuovere, come immagini o testo, a seconda delle tue esigenze. Salva il documento in un nuovo percorso per vedere le modifiche.
## Passaggio 6: estrazione delle filigrane
Se hai bisogno di estrarre e controllare filigrane da un documento, GroupDocs.Watermark per .NET lo rende possibile con facilità.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Proprietà e logica aggiuntive per ciascuna filigrana
    }
}
```
 Questo passaggio prevede l'utilizzo di`GetWatermarks`metodo per recuperare tutte le filigrane in un documento. È quindi possibile scorrere l'elenco delle filigrane e ispezionarne le proprietà o eseguire azioni aggiuntive secondo necessità.
## Conclusione
 Congratulazioni! Ora hai imparato come utilizzare GroupDocs.Watermark per .NET per aggiungere, rimuovere ed estrarre filigrane dai tuoi documenti. Con queste competenze, puoi proteggere e marchiare i tuoi documenti in modo efficace. Ricorda il[documentazione](https://reference.groupdocs.com/Watermark/net/) è sempre lì se hai bisogno di informazioni più dettagliate o funzionalità avanzate.
## Domande frequenti
### Posso utilizzare GroupDocs.Watermark per .NET con qualsiasi versione di .NET?
 Sì, GroupDocs.Watermark per .NET è compatibile con varie versioni di .NET Framework. Controlla il[documentazione](https://reference.groupdocs.com/Watermark/net/) per le specifiche.
### Dove posso scaricare GroupDocs.Watermark per .NET?
 È possibile scaricare la versione più recente da[pagina di download](https://releases.groupdocs.com/Watermark/net/).
### Come posso ottenere una licenza temporanea?
 È possibile ottenere una licenza temporanea da[pagina della licenza temporanea](https://purchase.groupdocs.com/temporary-license/).
### È disponibile una prova gratuita?
 Sì, puoi iniziare una prova gratuita visitando il[pagina di prova gratuita](https://releases.groupdocs.com/).
### Dove posso ottenere supporto se riscontro problemi?
 Il supporto è disponibile su[Forum Filigrana GroupDocs](https://forum.groupdocs.com/c/watermark/19).