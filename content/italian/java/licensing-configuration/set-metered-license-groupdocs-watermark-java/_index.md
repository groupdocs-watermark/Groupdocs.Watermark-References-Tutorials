---
date: '2026-07-30'
description: Scopri come impostare la licenza per GroupDocs.Watermark in Java, proteggi
  i tuoi documenti in modo efficace e gestisci l'utilizzo in modo efficiente.
keywords:
- how to set license
- GroupDocs Watermark Java
- metered licensing Java
lastmod: '2026-07-30'
og_description: Come impostare la licenza per GroupDocs.Watermark in Java. Questa
  guida ti accompagna nell'installazione dell'SDK, nell'ottenere una metered key e
  nella configurazione della licenza per proteggere i tuoi documenti.
og_image_alt: 'Guide: Set license for GroupDocs Watermark in Java'
og_title: Come impostare la licenza per GroupDocs Watermark in Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  headline: How to Set License for GroupDocs Watermark in Java
  type: TechArticle
- description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  name: How to Set License for GroupDocs Watermark in Java
  steps:
  - name: Define the public and private keys
    text: Enter the keys you received after registering for a temporary license. `Metered`
      is the GroupDocs.Watermark class that handles metered licensing and usage tracking.
      *Place your keys in a secure location (environment variables, encrypted config,
      etc.) before using them in code.*
  - name: Create an instance of the Metered class
    text: Instantiate the `Metered` object with your keys. This object will be passed
      to the watermark engine during initialization.
  - name: Set the metered license using the provided keys
    text: Call the `setLicense` method (or the equivalent API call) with your public
      and private keys. Once set, all subsequent watermark operations will be billed
      according to your usage. > **Pro tip:** Keep the keys out of source control.
      Use a secrets manager or encrypted properties file to avoid accidenta
  type: HowTo
- questions:
  - answer: A temporary license is time‑limited and ideal for evaluation, while a
      perpetual license provides unlimited use without recurring fees.
    question: What is the difference between a temporary and a perpetual license?
  - answer: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.
    question: Can I switch from a metered license to a perpetual one without code
      changes?
  - answer: The SDK falls back to offline mode; watermarking continues but usage won’t
      be reported until connectivity is restored.
    question: What happens if the metered service is unreachable?
  - answer: The SDK can handle files up to 1 GB; larger files should be split or processed
      in streaming mode.
    question: Are there file‑size limits for watermarking?
  - answer: It works on any platform that supports Java 8+, including Windows, Linux,
      and macOS.
    question: Does the metered license work on all operating systems?
  type: FAQPage
tags:
- set license
- GroupDocs Watermark
- Java licensing
- metered license
- document security
title: Come impostare la licenza per GroupDocs Watermark in Java
type: docs
url: /it/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Come impostare la licenza per GroupDocs Watermark in Java

Proteggere la proprietà intellettuale è una priorità fondamentale per le applicazioni moderne, e i watermark sono un metodo comprovato per scoraggiare la distribuzione non autorizzata. Se utilizzi **GroupDocs.Watermark for Java**, avrai bisogno di una licenza che possa monitorare l'uso e scalare con la domanda. Questo tutorial spiega **come impostare la licenza** per GroupDocs.Watermark in Java, dall'installazione dell'SDK alla configurazione di una chiave a consumo che riporta il consumo al servizio.

## Risposte rapide
- **Che cos'è una licenza a consumo?** È una licenza basata sull'uso che registra ogni chiamata API, consentendoti di pagare solo per ciò che consumi.  
- **Devo prima avere una versione di prova?** Sì, puoi richiedere una licenza temporanea dal sito GroupDocs per valutare il prodotto.  
- **Quale versione di Java è richiesta?** Java 8 o successiva; l'SDK è compilato per JDK 8+.  
- **Posso passare a una licenza perpetua in seguito?** Assolutamente – basta sostituire le chiavi a consumo con un file di licenza permanente.  
- **L'installazione è compatibile con Maven?** Sì, le coordinate Maven sono fornite per una gestione delle dipendenze senza interruzioni.

## Che cos'è una licenza a consumo per GroupDocs Watermark?
Una licenza a consumo è un diritto abilitato al cloud fornito da GroupDocs che registra ogni operazione di watermark eseguita dall'SDK. Ogni chiamata API viene registrata sul server di licenze di GroupDocs, consentendo una fatturazione pay‑as‑you‑go basata sull'uso reale. Questo modello fornisce agli sviluppatori informazioni in tempo reale sul consumo e aiuta a controllare i costi garantendo al contempo l'accesso completo alle funzionalità.

## Perché utilizzare una licenza a consumo con GroupDocs Watermark?
GroupDocs.Watermark supporta più di cinquanta formati di input e output — inclusi PDF, DOCX, PPTX e vari tipi di immagine — e può elaborare file fino a 1 GB senza caricare l'intero documento in memoria, preservando le prestazioni. Utilizzando una licenza a consumo paghi solo per le operazioni che effettivamente esegui, consentendo alla soluzione di scalare in modo economicamente efficiente mantenendo l'accesso completo a tutte le funzionalità.

## Prerequisiti
- **GroupDocs.Watermark for Java** versione 24.11 o successiva.  
- Un Java Development Kit (JDK) 8 o successivo installato e configurato.  
- Familiarità di base con Maven o la gestione manuale dei JAR.  
- Una chiave di licenza temporanea o permanente dal portale GroupDocs.

## Come impostare una licenza a consumo per GroupDocs Watermark in Java?

Carica le tue chiavi pubbliche e private, crea un'istanza `Metered` e applica la licenza — il tutto in tre passaggi concisi. Questo approccio garantisce che ogni richiesta di watermark venga conteggiata sul tuo account, offrendoti piena visibilità sul consumo.

### Passo 1: Definire le chiavi pubblica e privata
Immetti le chiavi che hai ricevuto dopo la registrazione per una licenza temporanea.

`Metered` è la classe GroupDocs.Watermark che gestisce la licenza a consumo e il tracciamento dell'uso.  
*Posiziona le tue chiavi in un luogo sicuro (variabili d'ambiente, configurazione crittografata, ecc.) prima di usarle nel codice.*

### Passo 2: Creare un'istanza della classe Metered
Instanzia l'oggetto `Metered` con le tue chiavi. Questo oggetto verrà passato al motore di watermark durante l'inizializzazione.

```text
Metered metered = new Metered(System.getenv("GROUPDOCS_PUBLIC_KEY"),
                               System.getenv("GROUPDOCS_PRIVATE_KEY"));
```

### Passo 3: Impostare la licenza a consumo usando le chiavi fornite
Chiama il metodo `setLicense` (o l'equivalente chiamata API) con le tue chiavi pubblica e privata. Una volta impostata, tutte le successive operazioni di watermark saranno fatturate in base al tuo utilizzo.

```text
WatermarkEngine engine = new WatermarkEngine();
engine.setMeteredLicense(metered);
```

> **Suggerimento:** Mantieni le chiavi fuori dal controllo del codice sorgente. Usa un gestore di segreti o un file di proprietà crittografato per evitare esposizioni accidentali.

## Configurazione di GroupDocs.Watermark per Java

### Informazioni sull'installazione

Integra GroupDocs.Watermark nel tuo progetto usando Maven o scaricando direttamente il JAR.

**Configurazione Maven:**  
Aggiungi la seguente configurazione nel tuo file `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>watermark</artifactId>
    <version>24.11</version>
</dependency>
```

**Download diretto:**  
Download the latest version from [GroupDocs.Watermark per Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza

Per sbloccare tutte le funzionalità, ottieni una prova gratuita o una licenza temporanea:

- Registrati sul [sito GroupDocs](https://purchase.groupdocs.com/temporary-license/) per iniziare.  
- Dopo aver ottenuto le chiavi, integrale nel tuo progetto come mostrato nella guida di implementazione.

### Inizializzazione e configurazione di base

Una volta aggiunto l'SDK al tuo progetto, importa gli spazi dei nomi necessari e crea l'istanza del motore di watermark come mostrato negli snippet di codice sopra.

## Suggerimenti per la risoluzione dei problemi
- **Chiavi non valide:** Controlla che le chiavi pubblica e privata corrispondano esattamente; un solo errore di battitura impedirà l'attivazione.  
- **Errori nel percorso del file di licenza:** Se preferisci una licenza basata su file, assicurati che il percorso del file sia assoluto o correttamente risolto rispetto alla directory di lavoro.  
- **Problemi di rete:** La licenza a consumo richiede chiamate HTTPS in uscita; verifica che il tuo firewall consenta il traffico verso `api.groupdocs.com`.

## Applicazioni pratiche
1. **Sicurezza dei documenti:** Aggiungi watermark visibili o invisibili a PDF, documenti Word e immagini per proteggere dati aziendali sensibili.  
2. **Tracciamento dell'uso:** Genera report su quanti documenti sono stati watermarked al giorno, utile per budgeting e conformità.  
3. **Integrazione CMS:** Automatizza l'inserimento di watermark durante i flussi di lavoro di pubblicazione dei contenuti, con licenza applicata automaticamente.

## Considerazioni sulle prestazioni

**Ottimizzazione delle prestazioni:**  
- Applica i watermark solo quando necessario; salta l'elaborazione per file già protetti.  
- Per grandi batch, riutilizza la stessa istanza `WatermarkEngine` per evitare il sovraccarico di inizializzazioni ripetute.  

**Buone pratiche:**  
- Monitora l'utilizzo dell'heap JVM durante l'elaborazione di PDF con centinaia di pagine; considera le API di streaming se la memoria diventa un collo di bottiglia.  
- Abilita il logging a livello `INFO` per catturare le chiamate di licenza senza sovraccaricare la console.

## Conclusione

In questa guida abbiamo coperto **come impostare la licenza** per GroupDocs.Watermark in Java, dall'installazione Maven alla configurazione della chiave a consumo. Seguendo i passaggi, ottieni un tracciamento preciso dell'uso, fatturazione flessibile e protezione robusta dei documenti — tutto senza compromettere le prestazioni.

**Prossimi passi:**  
- Sperimenta diversi stili di watermark (testo, immagine, diagonale).  
- Esplora funzionalità avanzate come watermark condizionali basati sui ruoli utente.  
- Consulta la dashboard di analytics di GroupDocs per monitorare le tendenze di consumo.

Pronto a proteggere i tuoi documenti? Implementa la soluzione oggi e goditi la tranquillità sapendo che i tuoi asset sono protetti e i costi di licenza sono trasparenti.

## Domande frequenti

**D: Qual è la differenza tra una licenza temporanea e una licenza perpetua?**  
A: Una licenza temporanea è limitata nel tempo e ideale per la valutazione, mentre una licenza perpetua offre uso illimitato senza costi ricorrenti.

**D: Posso passare da una licenza a consumo a una perpetua senza modifiche al codice?**  
A: Sì — sostituisci l'inizializzazione della chiave a consumo con una chiamata a `engine.setLicense("path/to/license/file")`.

**D: Cosa succede se il servizio a consumo non è raggiungibile?**  
A: L'SDK passa alla modalità offline; il watermarking continua ma l'uso non verrà segnalato finché la connettività non sarà ripristinata.

**D: Ci sono limiti di dimensione dei file per il watermarking?**  
A: L'SDK può gestire file fino a 1 GB; i file più grandi dovrebbero essere suddivisi o elaborati in modalità streaming.

**D: La licenza a consumo funziona su tutti i sistemi operativi?**  
A: Funziona su qualsiasi piattaforma che supporta Java 8+, inclusi Windows, Linux e macOS.

---

**Ultimo aggiornamento:** 2026-07-30  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs  

**Risorse**

- [Documentazione](https://docs.groupdocs.com/watermark/java/)
- [Riferimento API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Acquisizione licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

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

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```

```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```

```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```

## Tutorial correlati

- [Tutorial di licenza e configurazione di GroupDocs.Watermark per Java](/watermark/java/licensing-configuration/)
- [Come configurare la licenza di GroupDocs.Watermark in Java: Guida completa](/watermark/java/licensing-configuration/groupdocs-watermark-licensing-java-guide/)
- [Guida al watermarking Java: Proteggi i documenti con l'API GroupDocs.Watermark](/watermark/java/getting-started/java-watermark-groupdocs-guide/)