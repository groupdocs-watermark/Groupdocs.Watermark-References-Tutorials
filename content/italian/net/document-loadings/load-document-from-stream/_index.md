---
title: Carica documento dal flusso
linktitle: Carica documento dal flusso
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane ai documenti utilizzando GroupDocs.Watermark per .NET con questa guida. Perfetto per gli sviluppatori che desiderano migliorare la sicurezza dei documenti.
type: docs
weight: 11
url: /it/net/document-loadings/load-document-from-stream/
---
## introduzione
Desideri aggiungere filigrane ai tuoi documenti senza problemi utilizzando .NET? Non guardare oltre! GroupDocs.Watermark per .NET è una libreria potente e facile da usare che ti consente di gestire filigrane in vari formati di documenti. Che tu stia lavorando con PDF, documenti Word o immagini, questo strumento ti copre. In questo tutorial ti guideremo passo dopo passo attraverso il processo di caricamento di un documento da uno stream e di aggiunta di una filigrana. Quindi, tuffiamoci subito!
## Prerequisiti
Prima di iniziare, assicurati di avere la seguente configurazione:
1. Visual Studio: qualsiasi versione recente di Visual Studio funzionerà correttamente.
2. .NET Framework: assicurati di avere .NET Framework 4.0 o versione successiva installata.
3.  GroupDocs.Watermark per .NET: puoi scaricarlo da[Qui](https://releases.groupdocs.com/Watermark/net/).
4. Conoscenza di base di C#: sarà utile la familiarità con C# e i concetti di programmazione orientata agli oggetti.

## Importa spazi dei nomi
Per utilizzare GroupDocs.Watermark nel tuo progetto, dovrai importare gli spazi dei nomi necessari. Ciò ti consentirà di accedere alle funzionalità della libreria senza problemi.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Passaggio 1: impostazione del progetto
Per prima cosa, devi configurare il tuo progetto in Visual Studio. Ecco come farlo:
1. Crea un nuovo progetto: apri Visual Studio e crea un nuovo progetto di applicazione console C#.
2.  Installa GroupDocs.Watermark: installa la libreria GroupDocs.Watermark tramite NuGet Package Manager. Basta cercare`GroupDocs.Watermark` e installarlo.
## Passaggio 2: definire i percorsi dei documenti
Successivamente, è necessario definire i percorsi per il documento e il file di output in cui verrà salvato il documento con filigrana.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` con il percorso effettivo del documento a cui desideri applicare la filigrana e`"Your Document Directory"` con la directory in cui desideri salvare il documento con filigrana.
## Passaggio 3: caricare il documento da uno stream
Ora carichiamo il documento da uno stream. Ciò comporta l'apertura del documento come flusso e quindi l'utilizzo del file`Watermarker` classe dalla libreria GroupDocs.Watermark per gestirlo.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Il tuo codice per gestire le filigrane andrà qui
}
```
 Questo frammento di codice garantisce che il documento venga aperto come flusso e il file`Watermarker` la classe viene inizializzata con questo flusso. IL`using` Le dichiarazioni garantiscono che le risorse vengano smaltite correttamente dopo l'uso.
## Passaggio 4: crea e aggiungi una filigrana
Creare una filigrana è semplice con GroupDocs.Watermark. In questo esempio creeremo una semplice filigrana di testo.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Qui creiamo un file`TextWatermark` oggetto con il testo "Filigrana di prova" e specificare i dettagli del carattere. Quindi, aggiungiamo questa filigrana al documento utilizzando il file`Add` metodo del`Watermarker` classe.
## Passaggio 5: salvare il documento con filigrana
Infine, salva il documento con filigrana nel percorso di output specificato.
```csharp
watermarker.Save(outputFileName);
```
 Questo codice salva il documento con la filigrana appena aggiunta`outputFileName` percorso che hai definito in precedenza.

## Conclusione
Congratulazioni! Hai aggiunto correttamente una filigrana al tuo documento utilizzando GroupDocs.Watermark per .NET. Questa libreria semplifica incredibilmente la gestione delle filigrane in una varietà di formati di documenti. Se devi aggiungere testo, immagini o altri tipi di filigrane, GroupDocs.Watermark ha gli strumenti di cui hai bisogno. Non dimenticare di dare un'occhiata a[documentazione](https://reference.groupdocs.com/Watermark/net/) per funzionalità più avanzate e opzioni di personalizzazione.
## Domande frequenti
### Quali tipi di filigrane posso aggiungere utilizzando GroupDocs.Watermark per .NET?
Puoi aggiungere filigrane di testo, filigrane di immagini e persino forme e loghi complessi. La libreria supporta un'ampia gamma di opzioni di personalizzazione.
### Posso rimuovere filigrane dai documenti utilizzando GroupDocs.Watermark?
Sì, GroupDocs.Watermark ti consente di rimuovere anche le filigrane esistenti dai documenti.
### È disponibile una prova gratuita per GroupDocs.Watermark?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso acquistare una licenza per GroupDocs.Watermark?
È possibile acquistare una licenza direttamente da[Sito web di GroupDocs](https://purchase.groupdocs.com/buy).
### Dove posso ottenere supporto se riscontro problemi?
 Per supporto è possibile visitare il[Forum di supporto GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).