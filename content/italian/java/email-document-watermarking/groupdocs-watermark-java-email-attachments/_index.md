---
date: '2025-12-29'
description: Scopri come aggiungere filigrane agli allegati email usando GroupDocs.Watermark
  per Java. Questa guida fornisce istruzioni passo‑passo e le migliori pratiche.
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: Aggiungi filigrana agli allegati email con GroupDocs.Watermark per Java
type: docs
url: /it/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Aggiungere filigrana agli allegati email con GroupDocs.Watermark per Java

Nell'odierno panorama digitale, proteggere le informazioni sensibili è fondamentale—soprattutto quando **aggiungi filigrana alle email** prima che gli allegati lascino la tua casella di posta. Che tu sia uno sviluppatore che desidera rafforzare la sicurezza dei documenti o un'azienda che vuole marchiare ogni file in uscita, questo tutorial ti mostra come utilizzare GroupDocs.Watermark per Java per applicare filigrane testuali a tutti gli allegati supportati all'interno di un messaggio email.

## Risposte rapide
- **Cosa fa “add watermark to email”?** Inserisce un'etichetta visibile o semi‑trasparente (ad es., “Confidenziale”) in ogni allegato supportato, scoraggiando la distribuzione non autorizzata.  
- **Quale libreria è necessaria?** GroupDocs.Watermark per Java (ultima versione).  
- **È necessaria una licenza?** Una licenza di prova funziona per lo sviluppo; è necessaria una licenza commerciale per la produzione.  
- **Posso elaborare più email contemporaneamente?** Sì—incapsula i passaggi in un ciclo su una cartella di file *.msg*.  
- **Quali tipi di file sono supportati?** PDF, Word, Excel, PowerPoint, immagini e molti altri (vedi la documentazione ufficiale).

## Cos'è “add watermark to email”?
Aggiungere una filigrana a un'email significa aprire programmaticamente un file email, estrarre ogni allegato e applicare un testo (o immagine) personalizzato su quei documenti prima che l'email venga inviata o archiviata. Questo garantisce che la filigrana viaggi con il file, rafforzando la riservatezza e l'identità del marchio.

## Perché utilizzare GroupDocs.Watermark per Java?
- **Ampio supporto di formati** – funziona con PDF, file Office, immagini e altro.  
- **API semplice** – poche righe di codice ti permettono di creare, applicare e salvare le filigrane.  
- **Orientata alle prestazioni** – basso consumo di memoria, ideale per l'elaborazione lato server.  
- **Licenze pronte per l'impresa** – prova per la valutazione, licenza a pagamento per la produzione.

## Prerequisiti
- Java Development Kit (JDK) installato.  
- Un IDE come IntelliJ IDEA o Eclipse.  
- GroupDocs.Watermark per Java aggiunto al tuo progetto (vedi i passaggi di configurazione di seguito).

## Configurazione di GroupDocs.Watermark per Java

### Configurazione Maven
Se usi Maven, aggiungi il repository e la dipendenza al tuo `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

### Download diretto
In alternativa, scarica l'ultima versione da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Acquisizione della licenza
- Per una prova gratuita, registrati sul sito GroupDocs e richiedi una licenza temporanea.  
- Per uso commerciale, acquista una licenza completa. Visita la [pagina di acquisto](https://purchase.groupdocs.com/temporary-license/) per maggiori informazioni.

### Inizializzazione di base
Importa le classi principali di cui avrai bisogno:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Come aggiungere filigrana agli allegati email – Guida passo‑passo

### Passo 1: Crea una filigrana testuale
Per prima cosa, definisci il testo della filigrana e il suo aspetto.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Passo 2: Configura le opzioni di caricamento email
Configura il loader in modo che GroupDocs possa leggere il file *.msg*.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Passo 3: Inizializza Watermarker per il tuo file email
Indica il `Watermarker` all'email che desideri elaborare.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Passo 4: Recupera il contenuto dell'email
Ottieni la struttura interna dell'email così da poter lavorare con i suoi allegati.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Passo 5: Itera sugli allegati
Scorri ogni allegato e verifica che possa essere filigranato.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Passi 6‑9: Aggiungi filigrana agli allegati supportati
Per ogni file idoneo, aprilo con un nuovo `Watermarker`, applica la filigrana e scrivi le modifiche nell'email.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Passo 10: Salva l'email con filigrana
Scrivi l'email modificata in un nuovo file così l'originale rimane intatto.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Passo 11: Pulizia
Rilascia le risorse chiudendo il `Watermarker` principale.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Applicazioni pratiche
1. **Condivisione interna di documenti** – Inserisci il marchio aziendale o avvisi di riservatezza in ogni allegato prima della distribuzione interna.  
2. **Comunicazioni con i clienti** – Proteggi contratti, proposte e bilanci finanziari con un chiaro avviso “Confidenziale”.  
3. **Campagne di email marketing** – Aggiungi filigrane di branding sottili a PDF o immagini allegate a email promozionali, rafforzando il richiamo del marchio.

## Considerazioni sulle prestazioni
- **Gestione della memoria** – Elabora un allegato alla volta e chiudi prontamente ogni `Watermarker`.  
- **Dimensione dell'allegato** – File di grandi dimensioni aumentano il tempo di elaborazione; considera la compressione o il limite di dimensione prima della filigrana.  
- **Elaborazione batch** – Scorri una directory di file *.msg* per ammortizzare l'overhead quando si gestiscono molte email.

## Domande frequenti

**D: Posso aggiungere filigrane a file crittografati?**  
R: No. GroupDocs.Watermark non supporta la filigrana di documenti crittografati per motivi di sicurezza.

**D: Quali tipi di file sono supportati per la filigrana?**  
R: PDF, Word, Excel, PowerPoint, immagini (PNG, JPEG, BMP) e molti altri formati comuni. Consulta la documentazione ufficiale per l'elenco completo.

**D: Come posso personalizzare l'aspetto della mia filigrana?**  
R: Puoi modificare la famiglia di caratteri, la dimensione, il colore, l'opacità, la rotazione e la posizione usando il costruttore `TextWatermark` e le sue proprietà.

**D: È possibile l'elaborazione batch di più email?**  
R: Sì. Incapsula i passaggi in un ciclo `for` che itera su una cartella di file *.msg* e applica la stessa logica a ciascuno.

**D: La mia filigrana non appare—cosa devo controllare?**  
R: Verifica che il tipo di file dell'allegato sia supportato, assicurati che le dimensioni della filigrana si adattino alle dimensioni della pagina e conferma che il documento non sia protetto da password.

## Risorse
- [Documentazione](https://docs.groupdocs.com/watermark/java/)  
- [Riferimento API](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark per Java](https://releases.groupdocs.com/watermark/java/)

---

**Ultimo aggiornamento:** 2025-12-29  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs