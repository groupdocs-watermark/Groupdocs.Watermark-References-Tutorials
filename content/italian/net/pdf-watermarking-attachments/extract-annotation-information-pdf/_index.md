---
title: Estrai le informazioni sulle annotazioni dal PDF
linktitle: Estrai le informazioni sulle annotazioni dal PDF
second_title: API GroupDocs.Watermark .NET
description: Scopri come estrarre informazioni sulle annotazioni dai documenti PDF utilizzando GroupDocs.Watermark per .NET in questa guida dettagliata passo passo.
weight: 23
url: /it/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## introduzione
Ti ritrovi spesso a dover estrarre informazioni dettagliate sulle annotazioni dai tuoi documenti PDF? Che tu sia uno sviluppatore che lavora su sistemi di gestione dei documenti o un professionista aziendale che gestisce numerosi PDF, l'estrazione e l'elaborazione efficiente delle annotazioni può essere fondamentale. Con GroupDocs.Watermark per .NET, hai a disposizione un potente kit di strumenti per rendere questa attività semplice ed efficiente.
## Prerequisiti
Prima di immergerci nel codice, assicuriamoci di avere tutto il necessario per iniziare:
1. Visual Studio: assicurati di avere Visual Studio installato. Questo sarà il nostro IDE per scrivere ed eseguire il codice.
2.  GroupDocs.Watermark per .NET: è necessario disporre della libreria GroupDocs.Watermark per .NET. Puoi[scaricalo qui](https://releases.groupdocs.com/Watermark/net/).
3. Conoscenza di base di C#: è necessaria la familiarità con la programmazione C# da seguire insieme agli esempi.
## Importa spazi dei nomi
Per cominciare, devi importare gli spazi dei nomi necessari nel tuo progetto. Questi spazi dei nomi contengono le classi e i metodi necessari per lavorare con file PDF ed estrarre annotazioni.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Passaggio 1: imposta il tuo progetto
Innanzitutto, impostiamo il nostro progetto in Visual Studio. Creare un nuovo progetto di app console (.NET Core). Una volta creato il progetto, è necessario aggiungere un riferimento alla libreria GroupDocs.Watermark per .NET.
1. Aprire Gestione pacchetti NuGet.
2.  Cercare`GroupDocs.Watermark`.
3.  Installa il`GroupDocs.Watermark` pacchetto.
## Passaggio 2: definire i percorsi dei documenti
Successivamente, dovrai specificare i percorsi per il documento PDF di input e la directory di output in cui verranno salvate le informazioni estratte. Ciò garantisce che l'applicazione sappia dove trovare il file PDF e dove archiviare i risultati.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Passaggio 3: caricare il documento PDF
 Per lavorare con il documento PDF, dobbiamo caricarlo utilizzando`PdfLoadOptions`. Questa classe fornisce opzioni per configurare il processo di caricamento.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il codice per estrarre le annotazioni andrà qui
}
```
## Passaggio 4: accedi al contenuto PDF
Una volta caricato il documento, possiamo accedere al suo contenuto. Nello specifico, vogliamo ottenere il contenuto PDF in modo da poter scorrere le pagine e le annotazioni.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Passaggio 5: scorrere le pagine e le annotazioni
Con il contenuto PDF in mano, possiamo scorrere ciascuna pagina e quindi ciascuna annotazione su quelle pagine. Questo ci permette di estrarre le informazioni di cui abbiamo bisogno.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Estrai i dettagli dell'annotazione qui
    }
}
```
## Passaggio 6: estrazione dei dettagli dell'annotazione
All'interno dei cicli annidati, estraiamo vari dettagli su ciascuna annotazione. Ciò include il tipo di annotazione, eventuali immagini associate, testo e dati di posizione.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Passaggio 7: salvare o elaborare i dati estratti
Infine, decidi cosa vuoi fare con le informazioni sull'annotazione estratte. Puoi stamparlo sulla console, salvarlo in un file o persino archiviarlo in un database, a seconda delle tue esigenze.
```csharp
// Esempio di salvataggio dei dati estratti in un file
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Conclusione
L'estrazione delle informazioni sulle annotazioni dai documenti PDF utilizzando GroupDocs.Watermark per .NET è un processo semplice che può farti risparmiare molto tempo e fatica. Seguendo i passaggi descritti in questa guida, puoi facilmente integrare questa funzionalità nei tuoi progetti e automatizzare l'estrazione di preziosi dati di annotazione.
 Che tu stia gestendo grandi volumi di PDF o abbia semplicemente bisogno di estrarre informazioni specifiche, GroupDocs.Watermark per .NET fornisce una soluzione affidabile ed efficiente. Non dimenticare di dare un'occhiata a[documentazione](https://tutorials.groupdocs.com/Watermark/net/) per funzionalità più avanzate e opzioni di personalizzazione.
## Domande frequenti
### Cos'è GroupDocs.Watermark per .NET?
GroupDocs.Watermark per .NET è una libreria completa che consente agli sviluppatori di aggiungere, cercare e rimuovere filigrane da vari formati di documenti, inclusi PDF, documenti Word e immagini.
### Posso provare GroupDocs.Watermark gratuitamente?
 Sì, puoi ottenere un[prova gratuita](https://releases.groupdocs.com/) per testare le funzionalità della libreria prima di effettuare un acquisto.
### Come posso ottenere supporto se riscontro problemi?
 Puoi ottenere supporto dal team di GroupDocs visitandoli[Forum di assistenza](https://forum.groupdocs.com/c/watermark/19).
### È possibile ottenere una licenza temporanea per testare?
 Sì, puoi richiedere a[licenza temporanea](https://purchase.groupdocs.com/temporary-license/) scopo di test.
### Dove posso acquistare la versione completa di GroupDocs.Watermark per .NET?
 È possibile acquistare la versione completa da[Sito web di GroupDocs](https://purchase.groupdocs.com/buy).