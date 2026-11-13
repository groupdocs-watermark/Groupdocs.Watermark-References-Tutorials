---
date: 2026-11-13
description: Scopri come estrarre i metadati, elencare i formati supportati e recuperare
  le informazioni del documento usando GroupDocs.Watermark per Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Come estrarre i metadati usando GroupDocs.Watermark per Java. Scopri
  come elencare i formati supportati, recuperare le informazioni del documento e estrarre
  gli sfondi delle diapositive in pochi minuti.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Come estrarre i metadati con GroupDocs.Watermark per Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Come estrarre i metadati con GroupDocs.Watermark per Java
type: docs
url: /it/java/document-information/
weight: 14
---

# Come estrarre i metadati con GroupDocs.Watermark per Java

In questa guida scoprirai **come estrarre i metadati** da un'ampia gamma di tipi di documento usando GroupDocs.Watermark per Java. Che tu debba leggere il tipo di file, il conteggio delle pagine, i dettagli dell'autore o le proprietà personalizzate, la libreria ti offre accesso programmatico a queste informazioni così da poter prendere decisioni intelligenti sul posizionamento dei watermark, il routing dei documenti o i controlli di conformità. Il tutorial mostra anche come elencare i formati supportati, estrarre i dati di sfondo delle diapositive e recuperare altre caratteristiche utili del documento.

## Risposte rapide
- **Posso estrarre i metadati da PDF e file Word?** Sì, l'API legge i metadati da oltre 70 formati comuni.  
- **Ho bisogno di una licenza per lo sviluppo?** Una licenza temporanea gratuita funziona per i test; è necessaria una licenza completa per la produzione.  
- **Quale versione di Java è richiesta?** È supportata Java 8 o versioni successive.  
- **La libreria è thread‑safe?** Le classi di estrazione principali sono progettate per l'uso concorrente.  
- **Quanti formati sono riconosciuti?** Più di 70 formati di input e output sono riconosciuti subito.

## Cos'è l'estrazione dei metadati?
L'estrazione dei metadati è il processo di lettura delle informazioni incorporate — come autore, data di creazione, conteggio delle pagine e proprietà personalizzate — da un file documento senza alterarne il contenuto. Consente flussi di lavoro automatizzati che dipendono dagli attributi del documento. Tipicamente include proprietà come titolo, parole chiave e timestamp di modifica, che possono essere sfruttate per l'indicizzazione e la generazione di report di conformità.

## Perché usare GroupDocs.Watermark per Java?
GroupDocs.Watermark per Java supporta **70+ formati di file**, tra cui PDF, DOCX, PPTX, XLSX e tipi di immagine, e può elaborare documenti fino a 500 MB senza caricare l'intero file in memoria. La sua API restituisce i metadati in un unico oggetto coerente, riducendo la necessità di parser specifici per formato e accorciando i tempi di sviluppo fino al 40 %.

## Prerequisiti
- Java 8 o versioni successive installato sulla tua macchina di sviluppo.  
- Maven o Gradle per gestire la dipendenza `groupdocs-watermark`.  
- Un file di licenza temporaneo o completo di GroupDocs.Watermark.

## Come estrarre i metadati passo dopo passo

### Come recuperare le informazioni di base del documento?
La classe `Watermark` rappresenta un documento e fornisce l'accesso ai suoi metadati. Il metodo `getDocumentInfo()` estrae l'oggetto metadati dal documento caricato. Carica il documento con la classe `Watermark`, quindi chiama `getDocumentInfo()` per ottenere un oggetto contenente il tipo di file, la dimensione, il conteggio delle pagine e la data di creazione. Questa singola chiamata restituisce tutti i metadati principali in meno di un secondo per file tipici inferiori a 100 MB. L'oggetto `DocumentInfo` restituito include anche l'autore del documento, la data dell'ultima modifica e eventuali proprietà personalizzate incorporate, fornendo una panoramica completa.

### Come elencare tutti i formati di file supportati?
L'utilità `SupportedFormats` fornisce un catalogo di tutti i tipi di file che l'SDK può elaborare. Usa l'utilità `SupportedFormats` fornita dall'SDK. Restituisce una collezione di identificatori di formato che puoi visualizzare o convalidare prima di caricare i file, garantendo la compatibilità e prevenendo errori di runtime. Ogni voce include il nome del formato, l'estensione tipica del file e una breve descrizione delle sue capacità, aiutando gli sviluppatori a validare gli input prima dell'elaborazione.

### Come estrarre i dettagli dello sfondo delle diapositive da un file PowerPoint?
`SlideInfo` è un oggetto che descrive le proprietà visive di una diapositiva, come l'immagine di sfondo e le dimensioni. `getSlides()` restituisce una collezione di oggetti `SlideInfo` per ogni diapositiva nella presentazione. L'oggetto `SlideInfo` espone le dimensioni dell'immagine di sfondo, la dimensione del file e la profondità di colore. Accedilo tramite la collezione `getSlides()`, quindi itera su ogni diapositiva per leggere le sue proprietà di sfondo — utile per lo styling dinamico o la generazione di miniature. Questi dettagli possono essere usati per generare miniature, applicare uno stile coerente o sostituire gli sfondi in modo programmatico su più presentazioni.

## Problemi comuni e soluzioni
- **Metadati mancanti:** Alcuni file più vecchi potrebbero non contenere proprietà standard. In tal caso, abilita il flag `extractCustomProperties` per estrarre eventuali campi definiti dall'utente.  
- **File di grandi dimensioni causano timeout:** Aumenta l'impostazione `maxMemory` dell'SDK o elabora il documento in modalità streaming per evitare di caricare l'intero file in RAM.  
- **Errore di formato non supportato:** Verifica il formato rispetto all'elenco restituito da `SupportedFormats` prima di tentare l'estrazione.

## Domande frequenti

**D: Posso estrarre i metadati da documenti protetti da password?**  
R: Sì, fornisci la password quando apri il documento; l'API lo decritterà in memoria e poi leggerà i metadati.

**D: La libreria funziona su Android?**  
R: Le funzionalità di estrazione core sono compatibili con Android API 21+ quando distribuite come JAR standard.

**D: Come gestisco i campi di metadati personalizzati?**  
R: Usa il metodo `getCustomProperties()` sull'oggetto `DocumentInfo`; restituisce una mappa di coppie chiave‑valore che puoi iterare.

**D: Esiste un modo per elaborare in batch molti file?**  
R: Avvolgi la logica di estrazione in un ciclo e riutilizza una singola istanza `Watermark`; l'SDK è progettato per scenari ad alto throughput.

**D: Quali opzioni di licenza sono disponibili?**  
R: GroupDocs.Watermark offre licenze perpetue, in abbonamento e temporanee; la licenza temporanea è ideale per valutazioni e pipeline CI.

## Tutorial disponibili

### [Estrai informazioni sul documento usando GroupDocs.Watermark per Java: Guida completa](./extract-document-info-groupdocs-watermark-java/)
Scopri come estrarre in modo efficiente i metadati del documento, come tipo di file, conteggio delle pagine e dimensione, usando GroupDocs.Watermark per Java. Questa guida copre l'installazione, l'implementazione e le applicazioni pratiche.

### [Estrai le dimensioni delle pagine PDF in Java usando GroupDocs.Watermark: Guida completa](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Scopri come estrarre le dimensioni delle pagine PDF con GroupDocs.Watermark per Java. Questa guida copre l'installazione, esempi di codice e applicazioni pratiche.

### [Estrai forme dai documenti Word usando GroupDocs.Watermark in Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Scopri come estrarre e analizzare le forme dai documenti Word usando GroupDocs.Watermark per Java, migliorando l'automazione e la manipolazione dei documenti.

### [Come estrarre le informazioni sullo sfondo delle diapositive usando GroupDocs.Watermark per Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Scopri come estrarre i dettagli dello sfondo delle diapositive, come le dimensioni dell'immagine e la dimensione del file, usando GroupDocs.Watermark per Java. Ideale per personalizzazione, analisi o documentazione.

### [Come elencare i formati di file supportati usando GroupDocs.Watermark per Java: Guida completa](./groupdocs-watermark-java-list-supported-formats/)
Scopri come elencare in modo efficiente i formati di file supportati con GroupDocs.Watermark in Java, garantendo la compatibilità tra vari tipi di documento.

### [Come recuperare le informazioni del documento usando GroupDocs.Watermark per Java: Guida passo‑per‑passo](./retrieve-document-info-groupdocs-watermark-java/)
Scopri come recuperare in modo efficiente le informazioni del documento, come tipo di file, conteggio delle pagine e dimensione, usando GroupDocs.Watermark per Java. Segui la nostra guida dettagliata con esempi di codice.

### [Come recuperare le proprietà di sezione nei documenti Word usando GroupDocs.Watermark per Java](./groupdocs-java-word-section-properties-retrieval/)
Scopri come recuperare e manipolare in modo efficiente le proprietà di sezione nei documenti Word usando GroupDocs.Watermark per Java. Perfetto per gli sviluppatori che desiderano migliorare la gestione dei documenti.

## Risorse aggiuntive

- [Documentazione di GroupDocs.Watermark per Java](https://docs.groupdocs.com/watermark/java/)
- [Riferimento API di GroupDocs.Watermark per Java](https://reference.groupdocs.com/watermark/java/)
- [Scarica GroupDocs.Watermark per Java](https://releases.groupdocs.com/watermark/java/)
- [Forum di GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Supporto gratuito](https://forum.groupdocs.com/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

**Ultimo aggiornamento:** 2026-11-13  
**Testato con:** GroupDocs.Watermark 23.12 per Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Come elencare i formati di file supportati usando GroupDocs.Watermark per Java: Guida completa](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Come recuperare le informazioni del documento usando GroupDocs.Watermark per Java: Guida passo‑per‑passo](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Estrai informazioni sul documento usando GroupDocs.Watermark per Java: Guida completa](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)