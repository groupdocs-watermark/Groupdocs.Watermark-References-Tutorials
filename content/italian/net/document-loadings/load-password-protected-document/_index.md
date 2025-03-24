---
title: Carica documento protetto da password
linktitle: Carica documento protetto da password
second_title: API GroupDocs.Watermark .NET
description: Scopri come aggiungere filigrane ai documenti protetti da password utilizzando Groupdocs per .NET con la nostra guida passo passo. Proteggi e personalizza facilmente i tuoi file.
weight: 13
url: /it/net/document-loadings/load-password-protected-document/
---

# Carica documento protetto da password

## introduzione
Desideri proteggere i tuoi documenti aggiungendo filigrane, anche se sono protetti da password? Groupdocs.Watermark per .NET è un potente strumento che ti consente di fare proprio questo. In questo tutorial ti guideremo attraverso il processo di caricamento di un documento protetto da password e di aggiunta di una filigrana utilizzando Groupdocs.Watermark per .NET. Immergiamoci!
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. Visual Studio: qualsiasi versione di Visual Studio installata nel computer.
2. .NET Framework: assicurarsi di disporre di .NET Framework 4.6.1 o versione successiva.
3. Groupdocs.Watermark per .NET: scarica e installa la libreria Groupdocs.Watermark per .NET dal[Link per scaricare](https://releases.groupdocs.com/Watermark/net/).
## Importa spazi dei nomi
Per prima cosa dobbiamo importare gli spazi dei nomi necessari nel nostro progetto. Ciò garantisce che possiamo accedere a tutti i metodi e le proprietà forniti da Groupdocs.Watermark per .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Ora suddividiamo il processo in passaggi semplici e facili da seguire.
## Passaggio 1: imposta il tuo progetto
Per iniziare, crea una nuova applicazione console C# in Visual Studio. Una volta configurato il progetto, installa la libreria Groupdocs.Watermark per .NET tramite NuGet Package Manager.
1. Apri Visual Studio e crea una nuova app console (.NET Framework).
2.  Vai a`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Cercare`GroupDocs.Watermark` e installare il pacchetto.
## Passaggio 2: definire i percorsi dei documenti
Successivamente, dovrai definire il percorso del documento protetto da password e il percorso del file di output in cui verrà salvato il documento con filigrana.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Sostituire`"Your Document Path"` E`"Your Document Directory"` con i percorsi effettivi sul tuo computer.
## Passaggio 3: imposta le opzioni di caricamento con password
Per aprire un documento protetto da password, è necessario fornire la password nelle opzioni di caricamento.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Sostituire`"P@$w0rd"` con la password effettiva del tuo documento.
## Passaggio 4: caricare il documento
 Ora carichiamo il documento utilizzando il file`Watermarker` classe.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Il tuo codice per aggiungere la filigrana andrà qui
}
```
## Passaggio 5: crea una filigrana
Creeremo una filigrana di testo che possiamo aggiungere al documento. Puoi personalizzare il testo, il carattere, la dimensione e altre proprietà secondo necessità.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Sentiti libero di cambiare`"Test watermark"`, `"Arial"` , E`12` al testo, carattere e dimensione preferiti.
## Passaggio 6: aggiungi la filigrana
 Aggiungi la filigrana al documento utilizzando il file`Add` metodo del`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Passaggio 7: salvare il documento con filigrana
Infine, salva il documento con filigrana nel percorso del file di output specificato.
```csharp
watermarker.Save(outputFileName);
```
## Conclusione
Aggiungere filigrane ai tuoi documenti protetti da password è un processo semplice con Groupdocs per .NET. Seguendo questi semplici passaggi, puoi assicurarti che i tuoi documenti siano protetti e marchiati secondo le tue esigenze. Che si tratti di sicurezza, branding o conformità, applicare la filigrana ai tuoi documenti non è mai stato così facile.
## Domande frequenti
### Posso aggiungere filigrane di immagini utilizzando Groupdocs.Watermark per .NET?
 Sì, puoi aggiungere filigrane sia di testo che di immagini. Usa semplicemente il`ImageWatermark` classe invece di`TextWatermark`.
### È possibile rimuovere la filigrana da un documento?
Sì, Groupdocs.Watermark per .NET fornisce metodi per cercare e rimuovere filigrane.
### Groupdocs.Watermark per .NET supporta altri formati di documenti oltre ai PDF?
Sì, supporta un'ampia gamma di formati tra cui Word, Excel, PowerPoint e altri.
### Posso personalizzare l'aspetto della filigrana?
Assolutamente! Puoi personalizzare il carattere, la dimensione, il colore, l'opacità e altro.
### Dove posso ottenere supporto se riscontro problemi?
 Puoi visitare il[Forum di supporto di Groupdocs](https://forum.groupdocs.com/c/watermark/19) per aiuto e guida.