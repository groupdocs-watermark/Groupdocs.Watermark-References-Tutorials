---
title: Salva il documento nella posizione specificata
linktitle: Salva il documento nella posizione specificata
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere facilmente filigrane ai tuoi documenti utilizzando GroupDocs.Watermark per .NET con questa guida passo passo. Migliora la sicurezza dei documenti.
type: docs
weight: 11
url: /it/net/document-savings/save-document-specified-location/
---
## introduzione
Nell’era digitale, la protezione dei documenti è diventata più cruciale che mai. La filigrana è un modo efficace per proteggere i tuoi documenti dall'uso non autorizzato. GroupDocs.Watermark per .NET offre una soluzione solida per aggiungere filigrane ai tuoi documenti. Che tu sia uno sviluppatore che desidera integrare la filigrana nella tua applicazione o qualcuno interessato a salvaguardare i tuoi documenti, questo tutorial ti guiderà attraverso il processo passo dopo passo.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:
- Ambiente di sviluppo .NET: assicurati di avere Visual Studio o qualsiasi altro ambiente di sviluppo .NET installato.
-  GroupDocs.Watermark per la libreria .NET: scarica e fai riferimento alla libreria nel tuo progetto.[Scarica GroupDocs.Watermark per .NET](https://releases.groupdocs.com/Watermark/net/)
- Conoscenza di base della programmazione C#: sarà utile comprendere i concetti di base della programmazione C#.
- Documento su filigrana: tieni pronto un documento di esempio a cui desideri applicare la filigrana.
## Importa spazi dei nomi
Prima di iniziare con l'esempio, è necessario importare gli spazi dei nomi necessari. Aggiungi le seguenti istruzioni using nella parte superiore del file di codice:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Analizziamo il processo di aggiunta di una filigrana a un documento utilizzando GroupDocs.Watermark per .NET in passaggi gestibili. Segui questi passaggi per applicare correttamente una filigrana e salvare il documento in una posizione specificata.
## Passaggio 1: imposta il tuo progetto
Inizia creando un nuovo progetto .NET in Visual Studio. Puoi scegliere un'app console per semplicità.
1. Apri VisualStudio.
2.  Selezionare`File` >`New` >`Project`.
3.  Scegliere`Console App (.NET Core)` O`Console App (.NET Framework)`.
4.  Dai un nome al tuo progetto e fai clic`Create`.

## Passaggio 2: prepara il documento e il testo della filigrana
### Specificare il percorso del documento
Definisci il percorso del documento a cui desideri applicare la filigrana. Per questo esempio, utilizziamo un percorso segnaposto.
```csharp
string documentPath = "Your Document Path";
```
### Definire il percorso di output
Imposta il percorso di output in cui desideri salvare il documento con filigrana.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Passaggio 3: caricare il documento
 Usa il`Watermarker` class per caricare il documento. Questa classe fornisce metodi per aggiungere, rimuovere e modificare filigrane.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Aggiungi qui la logica della filigrana
}
```
## Passaggio 4: crea e aggiungi una filigrana

### Crea filigrana di testo
 Istanziare a`TextWatermark` oggetto con le proprietà di testo e carattere desiderate.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Aggiungi filigrana al documento
 Aggiungi la filigrana creata al tuo documento utilizzando il file`Add` metodo del`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Passaggio 5: salva il documento
Infine, salva il documento con la filigrana nella posizione specificata.
```csharp
watermarker.Save(outputFileName);
```
## Conclusione
Applicare la filigrana ai tuoi documenti utilizzando GroupDocs per .NET è un processo semplice che può migliorare significativamente la sicurezza dei tuoi documenti. Seguendo questa guida passo passo, puoi facilmente aggiungere filigrane ai tuoi documenti e salvarli nella posizione desiderata. Che tu stia proteggendo la proprietà intellettuale, garantendo l'autenticità del documento o semplicemente aggiungendo un tocco professionale, GroupDocs.Watermark per .NET fornisce gli strumenti di cui hai bisogno.
## Domande frequenti
### Posso utilizzare immagini come filigrane con GroupDocs.Watermark per .NET?
Sì, puoi utilizzare filigrane sia di testo che di immagini con GroupDocs per .NET. La libreria supporta vari tipi di filigrane per soddisfare le tue esigenze.
### È disponibile una prova gratuita per GroupDocs.Watermark per .NET?
 Sì, puoi scaricare una versione di prova gratuita da[sito web](https://releases.groupdocs.com/).
### Come posso acquistare una licenza per GroupDocs.Watermark per .NET?
 È possibile acquistare una licenza da[pagina di acquisto](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark per .NET supporta la filigrana batch?
Sì, puoi filigranare più documenti in un processo batch scorrendo un elenco di documenti e applicando filigrane.
### Dove posso ottenere supporto per GroupDocs.Watermark per .NET?
 Il supporto è disponibile su[Forum di GroupDocs](https://forum.groupdocs.com/c/watermark/19).