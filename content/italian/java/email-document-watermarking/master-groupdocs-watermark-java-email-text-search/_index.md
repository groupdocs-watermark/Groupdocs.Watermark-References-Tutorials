---
date: '2026-04-07'
description: Impara come cercare il corpo delle email in Java usando GroupDocs.Watermark,
  inclusa la ricerca di più parole chiave nelle email e come rimuovere i watermark
  delle email.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Cerca nel corpo dell''email Java con GroupDocs.Watermark: Guida completa'
type: docs
url: /it/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Cerca nel corpo dell'email Java con GroupDocs.Watermark

Se hai bisogno di **search email body java** rapidamente e in modo affidabile, sei nel posto giusto. In questo tutorial vedremo come GroupDocs.Watermark per Java ti consente di individuare testo specifico all'interno degli oggetti email, dei corpi HTML e dei corpi di testo semplice, e come puoi rimuovere i watermark indesiderati in seguito. Alla fine, sarai in grado di implementare una soluzione robusta che funziona con parole chiave singole o multiple e rimuove anche i watermark delle email quando necessario.

## Risposte rapide
- **What does “search email body java” mean?** Si riferisce all'uso di codice Java (con GroupDocs.Watermark) per trovare testo all'interno del contenuto di un'email.  
- **Can I search multiple keywords email at once?** Sì – crea oggetti `SearchCriteria` separati e combinateli.  
- **How to remove email watermarks?** Come rimuovere i watermark delle email? Usa il metodo `PossibleWatermarkCollection.clear()` dopo una ricerca.  
- **Do I need a license?** Ho bisogno di una licenza? Una prova gratuita è sufficiente per i test; è necessaria una licenza permanente per la produzione.  
- **Which IDE works best?** Quale IDE è il migliore? IntelliJ IDEA o Eclipse sono entrambi pienamente supportati.

## Cosa imparerai
- Installazione e configurazione di GroupDocs.Watermark per Java.  
- Impostazione dei criteri di ricerca per **search email body java** su oggetti e corpi.  
- Tecniche per **search multiple keywords email** in un'unica esecuzione.  
- I passaggi esatti per **how to remove email watermarks** dopo averli individuati.  

## Perché cercare il corpo dell'email Java con GroupDocs.Watermark?
GroupDocs.Watermark fornisce un'API di alto livello che astrae le complessità dell'analisi dei file .msg, della gestione di diversi formati di corpo e della gestione dei watermark. Questo ti fa risparmiare tempo rispetto alla creazione di un parser personalizzato e garantisce risultati coerenti su grandi lotti di email.

## Prerequisiti
- Java Development Kit (JDK) 8 o successivo.  
- Maven (o la possibilità di aggiungere JAR manualmente).  
- Familiarità di base con Java e i formati di file email (.msg, .eml).  

## Configurazione di GroupDocs.Watermark per Java
GroupDocs.Watermark per Java semplifica l'applicazione di watermark e la ricerca di testo all'interno dei documenti, incluse le email. Di seguito le due modalità più comuni per aggiungere la libreria al tuo progetto.

### Configurazione Maven
Include the following in your `pom.xml` file to add GroupDocs.Watermark as a dependency:
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
Alternatively, you can download the latest version directly from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Passaggi per l'acquisizione della licenza
- **Free Trial:** Inizia con una prova gratuita per testare le funzionalità di base.  
- **Temporary License:** Ottieni una licenza temporanea per accesso esteso e test.  
- **Purchase:** Considera l'acquisto se GroupDocs.Watermark soddisfa le tue esigenze.

#### Inizializzazione di base
Initialize the `Watermarker` class as shown below:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guida all'implementazione

### Funzionalità 1: Ricerca testo nel corpo dell'email
Questa funzionalità consente di cercare testo specifico nell'oggetto e nel corpo di un'email.

#### Panoramica
Dimostreremo come configurare GroupDocs.Watermark per cercare attraverso le diverse parti di un messaggio email usando codice Java.

##### Passo 1: Definisci i percorsi dei documenti
Set up your input and output paths for handling emails:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Passo 2: Configura le opzioni di caricamento e Watermarker
Initialize the `EmailLoadOptions` and `Watermarker` to work with your email document.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Passo 3: Crea i criteri di ricerca
Define criteria for searching text. We'll use a case‑insensitive search for the keyword **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Passo 4: Specifica le posizioni di ricerca
Configure the search to cover both the subject and body of emails:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Passo 5: Esegui la ricerca e rimuovi i watermark
Perform the search and remove any found watermarks:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Passo 6: Salva le modifiche
After processing, save your changes to a new document:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Suggerimenti per la risoluzione dei problemi
- **Common Issue:** Se i risultati della ricerca sono vuoti, assicurati che il testo sia presente nel corpo o nell'oggetto dell'email.  
- **Performance Tip:** Ottimizza limitando le ricerche solo alle sezioni necessarie.

### Funzionalità 2: Opzioni di caricamento del documento email
Questa sezione discute come impostare opzioni aggiuntive durante il caricamento di un documento email per l'elaborazione con GroupDocs.Watermark.

#### Panoramica
La configurazione delle opzioni di caricamento consente un maggiore controllo su come i documenti vengono gestiti, ad esempio specificando la protezione con password o le impostazioni di codifica.

##### Passo 1: Configura le opzioni di caricamento
Here's a basic setup for `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opzioni di configurazione chiave
- **Password Protection:** Specifica le password se le tue email sono criptate.  
- **Encoding Settings:** Definisci i tipi di codifica specifici secondo necessità.

## Come cercare più parole chiave nelle email
Se devi individuare diversi termini in un'unica passata, crea più oggetti `SearchCriteria` e combinateli usando operatori logici **OR** o **AND**. L'API ti consente di concatenare i criteri, così puoi cercare “invoice” **or** “receipt” senza eseguire loop separati.

## Come rimuovere i watermark delle email
Dopo aver individuato i watermark (o qualsiasi testo che corrisponde ai tuoi criteri), il metodo `PossibleWatermarkCollection.clear()` li rimuove dal documento email. Questo è il passaggio esatto che abbiamo usato nel **Step 5** sopra, e funziona per qualsiasi numero di corrispondenze.

## Applicazioni pratiche

### Caso d'uso 1: Elaborazione automatizzata delle email
Automatizza il filtraggio e l'elaborazione di grandi volumi di email per trovare contenuti specifici in modo efficiente.

### Caso d'uso 2: Controlli di conformità legale
Garantisci la conformità cercando informazioni sensibili all'interno delle email aziendali.

### Caso d'uso 3: Automazione del supporto clienti
Ottimizza i flussi di lavoro del supporto individuando rapidamente parole chiave o frasi nelle richieste dei clienti.

## Considerazioni sulle prestazioni
Quando usi GroupDocs.Watermark, considera i seguenti aspetti per ottimizzare le prestazioni:
- **Resource Management:** Gestisci in modo efficiente memoria e potenza di elaborazione per gestire grandi set di dati email.  
- **Java Memory Management Best Practices:** Monitora regolarmente l'uso delle risorse e rilascia le risorse tempestivamente.

## Domande frequenti

**Q:** Come posso gestire le email criptate con GroupDocs.Watermark?  
**A:** Usa `EmailLoadOptions` per specificare le password durante l'inizializzazione del `Watermarker`.

**Q:** Posso cercare più parole chiave contemporaneamente?  
**A:** Sì, crea istanze `SearchCriteria` separate e combinile usando operazioni logiche.

**Q:** GroupDocs.Watermark Java è gratuito?  
**A:** È disponibile una prova gratuita; considera l'acquisto di una licenza per funzionalità estese.

**Q:** Come gestire grandi volumi di email in modo efficiente?  
**A:** Ottimizza le ricerche mirandole a sezioni specifiche delle email e gestendo le risorse in modo efficace.

**Q:** Dove posso trovare ulteriore aiuto o supporto?  
**A:** Visita il [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) per il supporto della community o contatta il loro canale di supporto gratuito.

## Risorse
- **Documentation:** Esplora guide dettagliate su [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Accedi ai dettagli tecnici su [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Ultimo aggiornamento:** 2026-04-07  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs