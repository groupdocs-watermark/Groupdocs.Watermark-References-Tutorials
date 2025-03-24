---
title: Aggiungi filigrana immagine
linktitle: Aggiungi filigrana immagine
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane di immagini ai tuoi documenti utilizzando GroupDocs.Watermark per .NET con il nostro tutorial dettagliato passo dopo passo.
weight: 11
url: /it/net/image-watermarkings/add-image-watermark/
---
## introduzione
Benvenuti in questa guida completa sull'aggiunta di filigrane di immagini utilizzando GroupDocs.Watermark per .NET! La filigrana è un modo efficace per proteggere i tuoi documenti e le tue immagini dall'uso non autorizzato, garantendo che la tua proprietà intellettuale rimanga al sicuro. In questo tutorial ti guideremo attraverso l'intero processo, dalla configurazione del tuo ambiente all'applicazione di una filigrana ai tuoi documenti. Che tu sia uno sviluppatore esperto o che tu abbia appena iniziato, troverai questa guida utile e facile da seguire.
## Prerequisiti
Prima di immergerci nel tutorial, assicuriamoci di avere tutto ciò di cui hai bisogno:
- Ambiente di sviluppo: Visual Studio o qualsiasi IDE compatibile con .NET
- .NET Framework: .NET Framework 4.0 o versione successiva
-  GroupDocs.Watermark per .NET: puoi scaricarlo dal file[Sito web di GroupDocs](https://releases.groupdocs.com/Watermark/net/)
-  File immagine: un file immagine da utilizzare come filigrana (ad esempio,`watermark.jpg`)
- File documento: un documento a cui si desidera aggiungere la filigrana (ad esempio,`presentation.pptx`)
## Importa spazi dei nomi
Per iniziare, dovrai importare gli spazi dei nomi necessari nel tuo progetto. Questo è essenziale per accedere alle funzionalità GroupDocs.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
In questa sezione, suddivideremo il processo di aggiunta di una filigrana immagine in passaggi chiari e gestibili. Segui attentamente ogni passaggio per filigranare correttamente il tuo documento.
## Passaggio 1: configura il tuo ambiente
 Innanzitutto, assicurati che il tuo ambiente di sviluppo sia configurato correttamente. Installa la libreria GroupDocs.Watermark scaricandola dal file[Sito web di GroupDocs](https://releases.groupdocs.com/Watermark/net/).
1. Apri il tuo progetto in Visual Studio.
2. Fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.
3. Seleziona "Gestisci pacchetti NuGet..."
4.  Cercare`GroupDocs.Watermark` e installarlo.
## Passaggio 2: definire i percorsi dei file
Successivamente, dovrai definire i percorsi per il tuo documento di input e la directory di output. Ciò aiuta il programma a individuare i file con cui deve lavorare.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` E`"Your Document Directory"` con i percorsi effettivi del documento e della directory di output desiderata.
## Passaggio 3: inizializza Watermarker
Ora inizializza il file`Watermarker` class con il percorso del documento. Questa classe è responsabile della gestione del processo di filigrana.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Procedere ai passaggi successivi all'interno di questo blocco utilizzando
}
```
## Passaggio 4: crea una filigrana immagine
 All'interno del`Watermarker` blocco, crea un'istanza del file`ImageWatermark` class utilizzando il percorso dell'immagine della filigrana. Questa classe rappresenta l'immagine che desideri utilizzare come filigrana.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Continuare al passaggio successivo all'interno di questo blocco utilizzando
}
```
## Passaggio 5: aggiungi la filigrana al documento
 Con il`ImageWatermark` istanza pronta, aggiungila al tuo documento utilizzando il file`Add` metodo del`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Passaggio 6: salva il documento
Infine, salva il documento con filigrana nella directory di output specificata. Questo passaggio garantisce che le modifiche vengano scritte in un nuovo file.
```csharp
watermarker.Save(outputFileName);
```
## Conclusione
Congratulazioni! Hai aggiunto correttamente una filigrana immagine al tuo documento utilizzando GroupDocs.Watermark per .NET. Seguendo questa guida passo passo, puoi proteggere facilmente i tuoi documenti con filigrane personalizzate. Ricorda, la filigrana è un passaggio cruciale per salvaguardare le tue risorse digitali dall'uso non autorizzato.

## Domande frequenti
### Quali formati di file sono supportati da GroupDocs.Watermark?
GroupDocs.Watermark supporta un'ampia gamma di formati di file, inclusi PDF, DOCX, PPTX, XLSX e file di immagine come JPEG e PNG.
### Posso usare GroupDocs.Watermark con .NET Core?
Sì, GroupDocs.Watermark è compatibile sia con .NET Framework che con .NET Core.
### Come posso ottenere una licenza temporanea per GroupDocs.Watermark?
 È possibile ottenere una licenza temporanea da[Sito web di GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### È possibile aggiungere più filigrane a un singolo documento?
 Assolutamente! Puoi aggiungere più filigrane chiamando il comando`Add` metodo più volte con diverse istanze di filigrana.
### Dove posso trovare altri esempi e documentazione?
 Per ulteriori esempi e documentazione dettagliata, visitare il[Documentazione GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).