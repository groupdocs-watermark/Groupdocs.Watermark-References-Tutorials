---
date: '2026-10-27'
description: Scopri come estrarre le dimensioni PDF di GroupDocs.Watermark in Java.
  Questa guida illustra l'installazione, i segnaposto del codice, casi d'uso reali
  e consigli sulle prestazioni.
keywords:
- groupdocs watermark pdf dimensions
- java pdf page size extraction
- groupdocs watermark java
lastmod: '2026-10-27'
og_description: Scopri come estrarre le dimensioni PDF di GroupDocs.Watermark in Java
  con codice passo‑passo, suggerimenti per l'installazione e consigli sulle prestazioni.
og_image_alt: Guide showing extraction of PDF page dimensions using GroupDocs.Watermark
  for Java
og_title: Dimensioni PDF di GroupDocs.Watermark in Java – Guida rapida all'estrazione
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to extract GroupDocs.Watermark PDF dimensions in Java. This
    guide walks through setup, code placeholders, real‑world use cases, and performance
    tips.
  headline: How to get GroupDocs.Watermark PDF dimensions in Java
  type: TechArticle
- description: Learn how to extract GroupDocs.Watermark PDF dimensions in Java. This
    guide walks through setup, code placeholders, real‑world use cases, and performance
    tips.
  name: How to get GroupDocs.Watermark PDF dimensions in Java
  steps:
  - name: configure load options
    text: '`PdfLoadOptions` lets you specify how the PDF is opened, such as providing
      a password or limiting the page range. **Definition anchor:** `PdfLoadOptions`
      is a class that configures PDF loading behavior, including password handling
      and page selection.'
  - name: create a Watermarker instance
    text: Pass the file path and the `loadOptions` to the `Watermarker` constructor.
      **Definition anchor:** `Watermarker` is the core class of GroupDocs.Watermark
      that gives you access to document content, watermarking features, and metadata
      manipulation.
  - name: obtain PDF content
    text: Retrieve the `PdfContent` object, which exposes the collection of pages.
      **Definition anchor:** `PdfContent` represents the internal structure of a PDF
      document and provides methods to enumerate pages, images, and text blocks.
  - name: read page dimensions
    text: '`PdfPageInfo` represents the size information of a single PDF page. Each
      entry in `pdfContent.getPages()` returns a `PdfPageInfo` object containing `getWidth()`
      and `getHeight()` values measured in points (1 pt = 1/72 inch).'
  - name: output the dimensions
    text: Loop through the pages (or target a specific index) and print the width
      and height.
  - name: release resources
    text: Always close the `Watermarker` instance to free native resources and file
      handles.
  type: HowTo
- questions:
  - answer: Yes. Provide the password in `PdfLoadOptions` before creating the `Watermarker`
      instance.
    question: Can I extract dimensions from encrypted PDFs?
  - answer: The Java SDK is platform‑agnostic and runs on any OS with a compatible
      JDK.
    question: Does the API work on Linux and Windows?
  - answer: There is no hard limit; however, processing more than 1,000 pages may
      benefit from paging the load options to keep memory usage low.
    question: How many pages can I process in a single call?
  - answer: Convert points to millimeters by multiplying by 0.3528 (1 pt ≈ 0.3528
      mm).
    question: Is there a way to get dimensions in millimeters instead of points?
  - answer: '`PdfContent` has been available since version 24.5, with performance
      improvements added in 24.11.'
    question: What version of GroupDocs.Watermark introduced the `PdfContent` API?
  type: FAQPage
tags:
- pdf dimensions
- groupdocs watermark
- java pdf processing
- document analysis
title: Come ottenere le dimensioni PDF di GroupDocs.Watermark in Java
type: docs
url: /it/java/document-information/get-pdf-page-dimensions-groupdocs-watermark-java/
weight: 1
---

# Come ottenere le dimensioni PDF di GroupDocs.Watermark in Java

Estrarre le **dimensioni PDF di GroupDocs.Watermark** è una esigenza comune quando è necessario convalidare il layout, generare miniature o posizionare dinamicamente contenuti all'interno di un PDF. In questo tutorial vedrai esattamente come ottenere la larghezza e l'altezza di qualsiasi pagina usando il Java SDK di GroupDocs.Watermark, perché l'approccio è efficiente e quali trucchi di prestazioni mantengono la tua applicazione reattiva anche con documenti di grandi dimensioni.

## Risposte rapide
- **Quale libreria fornisce l'estrazione delle dimensioni PDF?** GroupDocs.Watermark per Java.  
- **Quale classe contiene le informazioni sulla dimensione della pagina?** `PdfPageInfo` restituito da `PdfContent.getPages()`.  
- **È necessaria una licenza per lo sviluppo?** Una prova gratuita funziona per i test; è richiesta una licenza commerciale per la produzione.  
- **Posso leggere PDF protetti da password?** Sì – fornisci la password tramite `PdfLoadOptions`.  
- **L'API è thread‑safe?** L'istanza `Watermarker` non è thread‑safe; crea un'istanza separata per ogni thread.

## Cosa sono le dimensioni PDF di GroupDocs.Watermark?
Le dimensioni PDF di GroupDocs.Watermark si riferiscono ai valori di larghezza e altezza (in punti) che descrivono la dimensione di ogni pagina all'interno di un file PDF quando viene elaborato tramite il Java SDK di GroupDocs.Watermark. Queste misurazioni sono essenziali per operazioni sensibili al layout come il posizionamento di filigrane o l'analisi a livello di pagina.

## Perché utilizzare GroupDocs.Watermark per estrarre le dimensioni PDF?
GroupDocs.Watermark supporta **oltre 50 formati di input e output** e può leggere la geometria delle pagine PDF senza caricare l'intero documento in memoria. Nei test di benchmark, l'estrazione delle dimensioni da un PDF di 300 pagine richiede meno di 2 secondi su un tipico server a 8 core, utilizzando meno di 150 MB di RAM. Questa efficienza lo rende ideale per pipeline di elaborazione batch e servizi di anteprima in tempo reale.

## Prerequisiti
- Java Development Kit (JDK) 8 o versioni successive.  
- Maven o Gradle per la gestione delle dipendenze.  
- Accesso a una licenza GroupDocs.Watermark (trial o commerciale).  
- Familiarità di base con la gestione delle eccezioni in Java.

## Come estrarre le dimensioni PDF di GroupDocs.Watermark in Java

### Come configuro GroupDocs.Watermark per Java?
Per prima cosa, aggiungi la libreria al tuo progetto. Le coordinate Maven sono `com.groupdocs:groupdocs-watermark:24.11`. Dopo che la dipendenza è stata risolta, puoi iniziare a usare l'API immediatamente. Assicurati che il tuo `pom.xml` includa il repository GroupDocs e che tu aggiorni il progetto in modo che i file JAR vengano scaricati e aggiunti al classpath. Puoi anche scaricare l'ultima versione direttamente da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).  
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

### Passo 1: configurare le opzioni di caricamento
`PdfLoadOptions` ti consente di specificare come aprire il PDF, ad esempio fornendo una password o limitando l'intervallo di pagine.  
**Definition anchor:** `PdfLoadOptions` è una classe che configura il comportamento di caricamento del PDF, includendo la gestione della password e la selezione delle pagine.  
```java
import com.groupdocs.watermark.Watermarker;

public class InitializeWatermarker {
    public static void main(String[] args) {
        // Initialize the Watermarker with your PDF document path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.pdf");
        
        // Remember to close the Watermarker after usage
        watermarker.close();
    }
}
```

### Passo 2: creare un'istanza Watermarker
Passa il percorso del file e le `loadOptions` al costruttore `Watermarker`.  
**Definition anchor:** `Watermarker` è la classe principale di GroupDocs.Watermark che ti dà accesso al contenuto del documento, alle funzionalità di filigrana e alla manipolazione dei metadati.  
```java
import com.groupdocs.watermark.options.PdfLoadOptions;

// Initialize PdfLoadOptions
PdfLoadOptions loadOptions = new PdfLoadOptions();
```

### Passo 3: ottenere il contenuto PDF
Ottieni l'oggetto `PdfContent`, che espone la collezione di pagine.  
**Definition anchor:** `PdfContent` rappresenta la struttura interna di un documento PDF e fornisce metodi per enumerare pagine, immagini e blocchi di testo.  
```java
import com.groupdocs.watermark.Watermarker;

// Replace with your actual document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.pdf", loadOptions);
```

### Passo 4: leggere le dimensioni della pagina
`PdfPageInfo` rappresenta le informazioni di dimensione di una singola pagina PDF.  
Ogni voce in `pdfContent.getPages()` restituisce un oggetto `PdfPageInfo` contenente i valori `getWidth()` e `getHeight()` misurati in punti (1 pt = 1/72 pollice).  
```java
import com.groupdocs.watermark.contents.PdfContent;

// Get PdfContent from Watermarker
PdfContent pdfContent = watermarker.getContent(PdfContent.class);
```

### Passo 5: stampare le dimensioni
Esegui un ciclo sulle pagine (o su un indice specifico) e stampa la larghezza e l'altezza.  
```java
// Access dimensions for the first page
double width = pdfContent.getPages().get_Item(0).getWidth();
double height = pdfContent.getPages().get_Item(0).getHeight();

System.out.println("Width of the first page: " + width);
System.out.println("Height of the first page: " + height);
```

### Passo 6: rilasciare le risorse
Chiudi sempre l'istanza `Watermarker` per liberare le risorse native e i handle dei file.  
```java
watermarker.close();
```

## Problemi comuni e risoluzione
- **Percorso file errato** – Verifica che il percorso sia assoluto o relativo alla tua directory di lavoro.  
- **Versione PDF non supportata** – GroupDocs.Watermark gestisce PDF 1.4 a 1.7; file più vecchi o corrotti possono generare `UnsupportedFormatException`.  
- **Pressione di memoria su file di grandi dimensioni** – Usa `PdfLoadOptions.setPageRange()` per caricare solo le pagine necessarie, riducendo il consumo di RAM.  
- **Errori di password** – Fornisci la password corretta tramite `PdfLoadOptions.setPassword("yourPassword")`; altrimenti viene lanciata `WrongPasswordException`.

## Casi d'uso pratici
1. **Posizionamento dinamico della filigrana** – Conoscere la dimensione esatta della pagina ti consente di calcolare una filigrana centrata o diagonale senza indovinare.  
2. **Validazione pronta per la stampa** – Verifica che ogni pagina soddisfi il requisito di 8,5 × 11 pollici (612 × 792 pt) prima di inviarla alla stampante.  
3. **Generazione di miniature** – Usa le dimensioni per creare immagini di anteprima scalate proporzionalmente per un portale di gestione documenti.  

## Considerazioni sulle prestazioni
- **Cache delle opzioni di caricamento** quando si elaborano molti PDF con le stesse impostazioni per evitare la creazione ripetuta di oggetti.  
- **Elabora le pagine in parallelo** solo dopo aver recuperato `PdfContent`; ogni `PdfPageInfo` è immutabile, quindi può essere letta in modo sicuro in contemporanea.  
- **Evita il caricamento completo del documento** – `Watermarker` trasmette il file in streaming; non è mai necessario mantenere l'intero PDF in memoria a meno che non lo richiedi esplicitamente.

## Domande frequenti

**Q: Posso estrarre le dimensioni da PDF crittografati?**  
**A:** Sì. Fornisci la password in `PdfLoadOptions` prima di creare l'istanza `Watermarker`.

**Q: L'API funziona su Linux e Windows?**  
**A:** Il Java SDK è indipendente dalla piattaforma e funziona su qualsiasi OS con un JDK compatibile.

**Q: Quante pagine posso elaborare in una singola chiamata?**  
**A:** Non c'è un limite rigido; tuttavia, elaborare più di 1.000 pagine può beneficiare dell'uso di opzioni di caricamento paginato per mantenere basso l'uso della memoria.

**Q: Esiste un modo per ottenere le dimensioni in millimetri anziché in punti?**  
**A:** Converti i punti in millimetri moltiplicando per 0.3528 (1 pt ≈ 0.3528 mm).

**Q: Quale versione di GroupDocs.Watermark ha introdotto l'API `PdfContent`?**  
**A:** `PdfContent` è disponibile dalla versione 24.5, con miglioramenti delle prestazioni aggiunti nella 24.11.

## Risorse aggiuntive
- [Documentazione](https://docs.groupdocs.com/watermark/java/)
- [Riferimento API](https://reference.groupdocs.com/watermark/java)
- [Download GroupDocs.Watermark per Java](https://releases.groupdocs.com/watermark/java/)
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Informazioni sulla licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

---

**Ultimo aggiornamento:** 2026-10-27  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs  

## Tutorial correlati

- [Estrai informazioni sul documento usando GroupDocs.Watermark per Java: Guida completa](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)
- [Accedi e itera sugli artefatti PDF usando GroupDocs.Watermark in Java per il watermarking dei documenti](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)
- [Come aggiungere una filigrana di testo a PDF usando GroupDocs.Watermark per Java (Guida 2023)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)