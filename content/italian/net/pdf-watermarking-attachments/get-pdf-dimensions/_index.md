---
title: Ottieni dimensioni PDF
linktitle: Ottieni dimensioni PDF
second_title: API GroupDocs.Watermark .NET
description: Proteggi i tuoi documenti con facilità utilizzando Groupdocs.Watermark per .NET. Aggiungi filigrane, timbri e annotazioni senza sforzo.
weight: 26
url: /it/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## introduzione
Nell'era digitale di oggi, salvaguardare i tuoi documenti è fondamentale. Che tu sia un professionista, un esperto legale o un artista creativo, proteggere la tua proprietà intellettuale è essenziale. Groupdocs.Watermark per .NET offre una soluzione solida per aggiungere filigrane, timbri e annotazioni ai tuoi documenti, garantendone la sicurezza e l'autenticità.
## Prerequisiti
Prima di immergerti nel mondo di Groupdocs.Watermark per .NET, assicurati di disporre dei seguenti prerequisiti:
1.  Installazione di Groupdocs.Watermark per .NET: scaricare e installare Groupdocs.Watermark per .NET dal[Link per scaricare](https://releases.groupdocs.com/Watermark/net/).
2.  Chiave di licenza (facoltativa): sebbene Groupdocs.Watermark per .NET offra una prova gratuita, puoi optare per una licenza temporanea o acquistare una licenza completa da[Qui](https://purchase.groupdocs.com/buy) per funzionalità estese.
3. Familiarità con C#: Si consiglia una conoscenza base del linguaggio di programmazione C# per comprendere e realizzare gli esempi forniti.
4. Documento da proteggere: tieni pronto un documento di esempio (ad esempio PDF, Word, Excel) sul tuo computer locale per sperimentarlo.

## Importa spazi dei nomi
Per iniziare a lavorare con Groupdocs.Watermark per .NET, devi importare gli spazi dei nomi necessari nel tuo progetto C#.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Passaggio 1: dichiarare le variabili
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Passaggio 2: caricare il documento
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Passaggio 3: ottieni contenuto PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Passaggio 4: recuperare le dimensioni
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Conclusione
In conclusione, Groupdocs.Watermark per .NET offre una soluzione completa per proteggere i tuoi documenti dall'uso e dalla distribuzione non autorizzati. Seguendo i passaggi sopra descritti e sfruttando la potenza di Groupdocs.Watermark per .NET, puoi garantire la sicurezza e l'integrità delle tue preziose risorse digitali.
## Domande frequenti
### Posso utilizzare Groupdocs.Watermark per .NET gratuitamente?
Sì, Groupdocs.Watermark per .NET offre una versione di prova gratuita a scopo di valutazione. Tuttavia, per funzionalità estese, potresti prendere in considerazione l'acquisto di una licenza completa.
### Groupdocs.Watermark supporta più formati di documenti?
Sì, Groupdocs supporta un'ampia gamma di formati di documenti tra cui PDF, Word, Excel, PowerPoint e altri.
### Posso personalizzare filigrane e timbri con Groupdocs.Watermark?
Assolutamente! Groupdocs.Watermark offre ampie opzioni di personalizzazione per filigrane, timbri e annotazioni per soddisfare le tue esigenze specifiche.
### Il supporto tecnico è disponibile per gli utenti di Groupdocs.Watermark?
 Sì, puoi ottenere assistenza tecnica e interagire con la community di Groupdocs tramite il[Forum di assistenza](https://forum.groupdocs.com/c/watermark/19).
### Come posso ottenere una licenza temporanea per Groupdocs.Watermark?
 È possibile ottenere una licenza temporanea per Groupdocs.Watermark da[Qui](https://purchase.groupdocs.com/temporary-license/).