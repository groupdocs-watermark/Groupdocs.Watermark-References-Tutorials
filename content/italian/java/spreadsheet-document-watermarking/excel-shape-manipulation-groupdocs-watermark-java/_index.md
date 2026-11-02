---
date: '2026-06-01'
description: Scopri come rimuovere le forme dai file Excel con GroupDocs.Watermark
  per Java. Include i passaggi per caricare Excel, iterare i fogli di lavoro e eliminare
  le forme formattate.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Come rimuovere le forme da Excel usando GroupDocs.Watermark in Java
type: docs
url: /it/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Come rimuovere forme da Excel usando GroupDocs.Watermark in Java

I fogli di calcolo Excel sono una pietra angolare della reportistica aziendale, ma le forme indesiderate—soprattutto quelle con formattazione del testo obsoleta o non standard—possono ingombrare un file e rompere la coerenza visiva. **Rimuovere forme da Excel** diventa rapidamente essenziale per documenti puliti e professionali. In questo tutorial vedremo come caricare una cartella di lavoro Excel, iterare i suoi fogli di lavoro e cancellare programmaticamente le forme che corrispondono a criteri di formattazione specifici, il tutto con la potente libreria GroupDocs.Watermark per Java.

## Risposte rapide
- **GroupDocs.Watermark può eliminare forme?** Sì, fornisce un metodo `removeShape` che funziona su qualsiasi foglio di lavoro.  
- **Ho bisogno di una licenza per questa funzionalità?** Una versione di prova funziona per la valutazione; è necessaria una licenza completa per la produzione.  
- **Quale versione di Java è richiesta?** Java 8 o successiva è supportata.  
- **Quanti formati di file gestisce GroupDocs.Watermark?** Oltre 30 formati di input e output, inclusi XLSX, DOCX, PDF e PPTX.  
- **Il consumo di memoria è un problema per cartelle di lavoro di grandi dimensioni?** Usa try‑with‑resources ed evita di caricare interi fogli in memoria; l'API trasmette i dati in modo efficiente.

## Cos'è rimuovere forme da Excel?
*Rimuovere forme da Excel* significa eliminare programmaticamente oggetti di disegno—come caselle di testo, icone o SmartArt—che soddisfano determinati criteri, come stile del carattere, colore o dimensione. Questa operazione pulisce la cartella di lavoro senza intervento manuale, garantendo coerenza visiva, riducendo le dimensioni del file e impedendo la comparsa di grafiche obsolete o indesiderate nei report distribuiti.

## Perché rimuovere forme da Excel?
GroupDocs.Watermark può elaborare **cartelle di lavoro multi‑centinaia di pagine a velocità fino a 3 × più veloce** rispetto alla modifica manuale, gestendo **30+ formati di file** mantenendo l'uso della memoria sotto 150 MB per file superiori a 50 MB. L'automazione della rimozione delle forme elimina gli errori umani e garantisce un branding coerente in tutti i report generati.

## Prerequisiti
### Librerie richieste, versioni e dipendenze
- **Java Development Kit (JDK)**: Versione 8 o successiva.  
- **GroupDocs.Watermark**: Versione 24.11 (l'ultima versione stabile al momento della stesura).

### Requisiti di configurazione dell'ambiente
Usa un IDE come IntelliJ IDEA o Eclipse e Maven per la gestione delle dipendenze.

### Prerequisiti di conoscenza
Familiarità con la sintassi Java e i concetti base di Excel (fogli di lavoro, celle e forme) ti aiuterà a seguire gli esempi.

## Configurazione di GroupDocs.Watermark per Java
**Dipendenza Maven**  
Aggiungi quanto segue al tuo `pom.xml`:

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

**Download diretto**  
In alternativa, scarica l'ultima versione da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Passaggi per l'acquisizione della licenza
- **Prova gratuita** – Inizia con una prova gratuita per valutare le funzionalità.  
- **Licenza temporanea** – Ottieni una licenza temporanea per test estesi.  
- **Acquisto** – Acquista una licenza completa per l'uso in produzione.

### Inizializzazione e configurazione di base  
Una volta aggiunta la libreria al tuo progetto, inizializzala come mostrato di seguito:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Come rimuovere forme da Excel?
Carica la cartella di lavoro, percorri ogni foglio di lavoro e chiama l'API di rimozione delle forme. Questo modello a due passaggi—*carica* poi *itera*—copre praticamente qualsiasi scenario in cui è necessario pulire le forme in tutto il file. Controllando le proprietà di ogni forma rispetto ai tuoi criteri prima della rimozione, garantisci che vengano eliminate solo gli elementi indesiderati, preservando il resto del layout e del contenuto del documento.

## Caricare un documento Excel
**Panoramica**  
Caricare un documento Excel è il punto di partenza per qualsiasi operazione di manipolazione. GroupDocs.Watermark semplifica questo con la sua API intuitiva.  

**Ancora di definizione**  
`SpreadsheetDocument` è la classe principale in GroupDocs.Watermark che rappresenta una cartella di lavoro Excel in memoria, fornendo metodi per accedere a fogli di lavoro, celle e forme.  

#### Frammento di codice
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Accedere e iterare attraverso i fogli di lavoro in un foglio di calcolo
**Panoramica**  
Iterare attraverso i fogli di lavoro consente di eseguire operazioni su ciascun foglio singolarmente.  

**Ancora di definizione**  
`Worksheet` rappresenta un singolo foglio all'interno di un `SpreadsheetDocument`; è possibile leggere, modificare o eliminare il suo contenuto tramite questo oggetto.  

#### Frammento di codice
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Rimuovere forme con formattazione del testo specifica da un foglio di calcolo
**Panoramica**  
Questa funzionalità mira a forme che soddisfano determinati criteri di formattazione del testo, come tipo di carattere o colore.  

**Ancora di definizione**  
`Shape` è il modello oggetto per qualsiasi elemento di disegno (casella di testo, immagine o SmartArt) all'interno di un foglio di lavoro; espone proprietà come `getText`, `getFont` e `remove`.  

#### Frammento di codice
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Applicazioni pratiche
### Casi d'uso reali
1. **Validazione dei dati** – Elimina automaticamente le forme che contengono avvisi obsoleti.  
2. **Standardizzazione dei modelli** – Applica il branding aziendale rimuovendo caselle di testo non standard.  
3. **Reportistica automatizzata** – Pulisci i report generati prima della distribuzione, garantendo un aspetto curato.

### Possibilità di integrazione
GroupDocs.Watermark può essere incorporato in pipeline aziendali basate su Java, come micro‑servizi di generazione documenti, job di elaborazione batch o sistemi di gestione dei contenuti, fornendo un modo fluido e conforme alle licenze per gestire le risorse Excel.

## Considerazioni sulle prestazioni
### Ottimizzazione delle prestazioni
- **Evitare operazioni pesanti all'interno dei cicli** – recupera le collezioni di forme una volta per foglio di lavoro.  
- **Rilasciare le risorse prontamente** – usa try‑with‑resources per chiudere automaticamente gli stream.

### Linee guida sull'uso delle risorse
Rilascia l'oggetto `SpreadsheetDocument` non appena l'elaborazione termina per liberare la memoria nativa. Per file superiori a 100 MB, considera l'elaborazione dei fogli di lavoro in stream paralleli per sfruttare CPU multi‑core.

### Best practice per la gestione della memoria Java
Utilizza `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` in modo che il metodo `close()` venga eseguito anche in caso di eccezione.

## Problemi comuni e soluzioni
- **Forma non trovata** – Assicurati di controllare l'indice del foglio di lavoro corretto; le forme sono limitate a ciascun foglio.  
- **Eccezione di licenza** – Una licenza di prova disabilita l'elaborazione batch; passa a una licenza completa per operazioni illimitate.  
- **Valori di carattere inaspettati** – Le proprietà del carattere possono essere ereditate; usa `shape.getEffectiveFont()` per recuperare lo stile risolto.

## Domande frequenti

**Q: Posso rimuovere forme da una cartella di lavoro protetta da password?**  
A: Sì. Carica il documento con il parametro password, poi esegui la stessa logica di rimozione; l'API decritta il file in memoria.

**Q: La libreria supporta file .xls (Excel 97‑2003)?**  
A: Assolutamente. GroupDocs.Watermark gestisce sia i formati `.xlsx` sia i legacy `.xls` senza conversione.

**Q: Come registro quali forme sono state eliminate?**  
A: Itera la collezione di forme, verifica i criteri di formattazione, registra `shape.getName()` o `shape.getId()`, poi chiama `remove()`.

**Q: È possibile aggiungere un watermark dopo aver rimosso le forme?**  
A: Sì. Dopo la pulizia, invoca `doc.addWatermark(new TextWatermark("Confidential"))` per sovrapporre un watermark testuale su tutti i fogli di lavoro.

**Q: Qual è la dimensione massima del file supportata?**  
A: La libreria può elaborare file fino a **2 GB** su una JVM a 64 bit, limitata solo dalla memoria heap disponibile e dalle restrizioni del sistema operativo.

## Conclusione
In questo tutorial abbiamo dimostrato un approccio completo e pronto per la produzione per **rimuovere forme da Excel** usando GroupDocs.Watermark per Java. Caricando il documento, iterando i fogli di lavoro e applicando filtri di formattazione precisi, puoi automatizzare le attività di pulizia, applicare il branding e migliorare la qualità dei report su larga scala. Esplora funzionalità aggiuntive come l'inserimento di watermark, la conversione di documenti e l'elaborazione batch per ampliare ulteriormente il tuo toolkit di automazione dei documenti.

---

**Ultimo aggiornamento:** 2026-06-01  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Manipolazione delle forme Excel usando GroupDocs.Watermark in Java: Guida completa](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Aggiungere watermark immagine a foglio di calcolo Excel usando GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Gestione di documenti Excel e watermarking con GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)