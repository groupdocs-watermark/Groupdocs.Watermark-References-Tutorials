---
date: '2025-12-31'
description: Scopri come cercare il testo delle email usando GroupDocs.Watermark per
  Java, gestendo corpi, oggetti e allegati in modo efficiente.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Come cercare il testo delle email con GroupDocs.Watermark Java – Guida completa
type: docs
url: /it/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Come cercare il testo delle email con GroupDocs.Watermark Java

Trovare una frase specifica nell'oggetto, nel corpo o negli allegati di un'email può diventare un vero grattacapo—soprattutto quando si gestiscono decine o centinaia di messaggi. In questo tutorial scoprirai **come cercare il testo delle email** in modo rapido e preciso usando **GroupDocs.Watermark per Java**. Ti guideremo attraverso l'installazione, il codice e i consigli migliori, così potrai integrare la ricerca di testo nelle email nelle tue applicazioni con sicurezza.

## Risposte rapide
- **Quale libreria mi consente di cercare il testo delle email in Java?** GroupDocs.Watermark per Java.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per i test; per la produzione è richiesta una licenza a pagamento.  
- **Posso cercare sia nell'oggetto che nel corpo?** Sì—configura `EmailSearchableObjects` per includere Subject, HtmlBody e PlainTextBody.  
- **L'API è sensibile al maiuscolo/minuscolo?** Puoi scegliere ricerche case‑insensitive impostando il flag appropriato in `TextSearchCriteria`.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore; Maven è consigliato per la gestione delle dipendenze.

## Che cosa significa “come cercare email” con GroupDocs.Watermark?
GroupDocs.Watermark fornisce un'API unificata per individuare, rimuovere o modificare filigrane e testo semplice su molti tipi di documento—including **messaggi email** (`.msg`, `.eml`). Sfruttando il suo modello di oggetti ricercabili, puoi mirare esattamente alle parti di un'email di tuo interesse, rendendo l'elaborazione in blocco veloce e affidabile.

## Perché usare GroupDocs.Watermark Java per la ricerca nelle email?
- **API unificata** – Funziona con PDF, immagini, file Office e email usando gli stessi schemi di codice.  
- **Ottimizzata per le prestazioni** – Le operazioni di ricerca avvengono in memoria senza necessità di servizi esterni.  
- **Gestione robusta** – Supporta corpi HTML e plain‑text, allegati e anche email protette da password.  
- **Integrazione semplice** – Pronta per Maven/Gradle, con documentazione chiara e supporto attivo.

## Prerequisiti

- **Java Development Kit (JDK)** 8 o più recente.  
- **Maven** (o Gradle) per la gestione delle dipendenze.  
- Un IDE come **IntelliJ IDEA** o **Eclipse**.  
- Familiarità di base con la sintassi Java e i formati di file email (`.msg`, `.eml`).

## Configurare GroupDocs.Watermark per Java

### Configurazione Maven
Aggiungi il repository e la dipendenza al tuo `pom.xml`:

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
In alternativa, puoi scaricare l'ultimo JAR da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza
- **Prova gratuita:** Testa le funzionalità principali senza chiave di licenza.  
- **Licenza temporanea:** Richiedi una chiave a tempo limitato per una valutazione più estesa.  
- **Licenza a pagamento:** Acquista per utilizzo illimitato in produzione.

#### Inizializzazione di base
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guida all'implementazione

### Funzionalità 1: Ricerca di testo nel corpo dell'email

#### Panoramica
Configuriamo l'API per scansionare **oggetto**, **corpo HTML** e **corpo plain‑text** di un'email alla ricerca di una parola chiave specifica.

#### Passo 1: Definire i percorsi dei documenti
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Passo 2: Configurare le opzioni di caricamento e il Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Passo 3: Creare i criteri di ricerca
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Passo 4: Specificare le posizioni di ricerca
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Passo 5: Eseguire la ricerca e rimuovere le filigrane
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Passo 6: Salvare le modifiche
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Consigli per la risoluzione dei problemi
- **Risultati vuoti:** Verifica che la parola chiave compaia effettivamente nelle parti dell'email selezionate.  
- **Prestazioni:** Limita gli oggetti ricercabili solo a quelli necessari (es. Subject + PlainTextBody) per velocizzare l'elaborazione di grandi batch.

### Funzionalità 2: Opzioni di caricamento del documento email

#### Panoramica
`EmailLoadOptions` ti consente di controllare come l'email viene analizzata—utile per messaggi criptati o codifiche personalizzate.

#### Passo 1: Configurare le opzioni di caricamento
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opzioni di configurazione chiave
- **Protezione con password:** Imposta `loadOptions.setPassword("yourPassword")` per file `.msg` criptati.  
- **Impostazioni di codifica:** Regola `loadOptions.setEncoding(Charset.forName("UTF-8"))` quando lavori con set di caratteri non standard.

## Applicazioni pratiche

- **Elaborazione automatizzata delle email:** Scansiona in blocco i ticket di supporto in ingresso per parole chiave come “refund” o “error”.  
- **Controlli di conformità legale:** Individua rapidamente termini riservati (es. SSN, numeri di carta di credito) negli archivi di posta aziendali.  
- **Automazione del supporto clienti:** Instrada le email in base a frasi rilevate al team di supporto corretto.

## Considerazioni sulle prestazioni
- **Gestione delle risorse:** Chiama `watermarker.close()` non appena hai terminato l'elaborazione per liberare le risorse native.  
- **Best practice per la memoria:** Quando gestisci migliaia di messaggi, elabora i file in batch e riutilizza l'istanza `Watermarker` dove possibile.

## Conclusione
Ora disponi di un approccio solido e pronto per la produzione su **come cercare il testo delle email** usando GroupDocs.Watermark Java. La flessibilità dell'API ti permette di mirare parti specifiche di un'email, rimuovere filigrane indesiderate e integrare la logica in flussi di lavoro più ampi.

### Prossimi passi
- Sperimenta con **criteri di ricerca multipli** (es. combina “invoice” + “overdue”).  
- Esplora **l'aggiunta di filigrane** per segnalare le email che contengono dati sensibili.  
- Approfondisci altri tipi di documento (PDF, DOCX) usando lo stesso flusso di lavoro Watermarker.

## Domande frequenti

**D1:** Come posso gestire le email criptate con GroupDocs.Watermark?  
**R1:** Usa `EmailLoadOptions.setPassword("yourPassword")` prima di creare l'istanza `Watermarker`.

**D2:** Posso cercare più parole chiave contemporaneamente?  
**R2:** Sì—crea oggetti `SearchCriteria` separati per ogni parola chiave e combinali con operatori logici (es. `OrSearchCriteria`).

**D3:** GroupDocs.Watermark Java è gratuito?  
**R3:** È disponibile una prova gratuita per la valutazione. Per l'uso in produzione è necessaria una licenza a pagamento.

**D4:** Come gestire grandi volumi di email in modo efficiente?  
**R4:** Limita gli oggetti ricercabili solo a quelli necessari, elabora le email in batch e chiudi sempre il `Watermarker` per rilasciare le risorse.

**D5:** Dove posso trovare ulteriore aiuto o supporto?  
**R5:** Visita il [forum GroupDocs](https://forum.groupdocs.com/c/watermark/10) per assistenza dalla community o contatta direttamente il supporto GroupDocs.

## Risorse
- **Documentazione:** Esplora guide dettagliate su [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Riferimento API:** Accedi ai dettagli tecnici su [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Ultimo aggiornamento:** 2025-12-31  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs  

---