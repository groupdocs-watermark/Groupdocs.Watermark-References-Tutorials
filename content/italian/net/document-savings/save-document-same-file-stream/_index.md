---
title: Salva il documento nello stesso file o flusso
linktitle: Salva il documento nello stesso file o flusso
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane ai documenti utilizzando Groupdocs.Watermark per .NET. Questa guida fornisce istruzioni per garantire la protezione e l'integrità dei documenti.
type: docs
weight: 10
url: /it/net/document-savings/save-document-same-file-stream/
---
## introduzione
Nell'era digitale di oggi, l'aggiunta di filigrane ai documenti è diventata essenziale per proteggere la proprietà intellettuale e garantire l'integrità del marchio. Groupdocs.Watermark per .NET offre una soluzione solida per gli sviluppatori che desiderano incorporare filigrane nei documenti senza problemi. Questa guida completa ti guiderà attraverso i passaggi per salvare un documento con una filigrana nello stesso file o streaming utilizzando Groupdocs.Watermark per .NET.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di avere quanto segue:
1. Ambiente di sviluppo: Visual Studio installato sul tuo computer.
2. .NET Framework: assicurati di avere .NET Framework 4.0 o versione successiva.
3.  Groupdocs.Watermark per .NET: scarica e installa la versione più recente da[luogo](https://releases.groupdocs.com/Watermark/net/).
4.  Licenza: ottieni una licenza temporanea o permanente da[Qui](https://purchase.groupdocs.com/temporary-license/).
## Importa spazi dei nomi
Per iniziare a utilizzare Groupdocs.Watermark nel tuo progetto .NET, devi importare gli spazi dei nomi necessari:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Passaggio 1: imposta il tuo progetto
Prima di aggiungere filigrane ai nostri documenti, dobbiamo impostare il nostro progetto .NET. Ecco come:
1. Crea un nuovo progetto: apri Visual Studio e crea una nuova applicazione console.
2. Aggiungere riferimento a Groupdocs.Watermark: fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, scegliere "Gestisci pacchetti NuGet" e installare il pacchetto Groupdocs.Watermark.
## Passaggio 2: copia il documento in una nuova posizione
Per evitare di alterare direttamente il documento originale, è buona norma copiarlo prima in una nuova posizione. Ecco come farlo:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Passaggio 3: inizializzare il Watermarker
Ora che abbiamo copiato il nostro documento, possiamo inizializzare la classe Watermarker per aggiungere la nostra filigrana:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // La filigrana va qui
}
```
## Passaggio 4: crea e aggiungi una filigrana di testo
Successivamente, creiamo una filigrana di testo e la aggiungiamo al nostro documento:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Passaggio 5: salva il documento
Infine, salva il documento con la filigrana applicata:
```csharp
watermarker.Save();
```
## Conclusione
Aggiungere filigrane ai tuoi documenti utilizzando Groupdocs per .NET è semplice ed efficiente. Seguendo i passaggi sopra descritti, puoi proteggere i tuoi documenti e mantenerne l'integrità senza sforzo. Per maggiori dettagli è possibile fare riferimento al[documentazione](https://reference.groupdocs.com/Watermark/net/).
## Domande frequenti
### Posso utilizzare un'immagine come filigrana al posto del testo?
Sì, Groupdocs.Watermark ti consente di utilizzare immagini, forme e testo come filigrane.
### Come rimuovo una filigrana da un documento?
 È possibile rimuovere una filigrana accedendo alla raccolta di filigrane nel documento e utilizzando il file`Remove` metodo.
### È possibile personalizzare l'aspetto della filigrana?
Assolutamente. Puoi personalizzare il carattere, la dimensione, il colore e la posizione della filigrana.
### Posso applicare più filigrane a un singolo documento?
 Sì, puoi aggiungere più filigrane chiamando il file`Add` metodo più volte con diversi oggetti filigrana.
### Groupdocs.Watermark è compatibile con tutti i formati di documenti?
Groupdocs.Watermark supporta un'ampia gamma di formati di documenti tra cui PDF, DOCX, PPTX e molti altri.