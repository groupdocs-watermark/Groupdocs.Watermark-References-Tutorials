---
date: '2025-12-20'
description: Impara come estrarre immagini da documenti Word ed estrarre forme usando
  GroupDocs.Watermark per Java, perfetto per l'automazione e la manipolazione dei
  documenti.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Come estrarre immagini da documenti Word usando GroupDocs.Watermark in Java
type: docs
url: /it/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Come estrarre immagini da documenti Word usando GroupDocs.Watermark in Java

Nelle moderne applicazioni di elaborazione dei documenti, **estrarre immagini da Word** è una necessità frequente—sia che tu debba riutilizzare grafiche, eseguire OCR o semplicemente verificare il contenuto. Questo tutorial ti mostra, passo dopo passo, come caricare un documento Word in Java con GroupDocs.Watermark e poi **estrarre immagini da Word** file, dimostrando anche **come estrarre forme**. Alla fine avrai uno snippet di codice riutilizzabile che si integra perfettamente nella tua pipeline di automazione.

## Risposte rapide
- **Quale libreria gestisce l'estrazione delle immagini?** GroupDocs.Watermark for Java  
- **Posso estrarre sia immagini che forme vettoriali?** Sì – l'API fornisce accesso a immagini e metadati delle forme.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore.  
- **È necessaria una licenza per la produzione?** È consigliata una licenza commerciale; una prova gratuita funziona per la valutazione.  
- **Il processo è efficiente in termini di memoria per file di grandi dimensioni?** Sì, è possibile rilasciare le risorse prontamente e processare le sezioni in modo incrementale.

## Cos'è “Estrarre immagini da Word”?
Estrarre immagini da Word significa individuare programmaticamente ogni immagine, disegno o grafica incorporata all'interno di un file `.docx` e recuperare i suoi dati binari o i metadati. Questo consente attività successive come analisi delle immagini, migrazione dei contenuti o generazione di report dinamici.

## Perché usare GroupDocs.Watermark per questo compito?
GroupDocs.Watermark offre un'API di alto livello che astrae le complessità del formato OpenXML. Ti consente di **caricare documenti Word java** progetti con poche righe di codice, esponendo anche informazioni dettagliate sulle forme—perfetto per gli sviluppatori che necessitano sia dell'estrazione delle immagini sia dell'analisi delle forme.

## Prerequisiti
- **Java Development Kit (JDK)** 8 o più recente  
- **IDE** – IntelliJ IDEA, Eclipse o qualsiasi editor compatibile con Java  
- Conoscenze di base di Java I/O  
- Accesso a una licenza GroupDocs.Watermark (la versione di prova funziona per i test)

## Configurare GroupDocs.Watermark per Java
Integra la libreria tramite Maven o download diretto.

### Utilizzo di Maven
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
In alternativa, scarica l'ultimo JAR da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Ottenimento della licenza
Per la piena funzionalità, ottieni una chiave di licenza dal portale GroupDocs. È possibile richiedere una licenza di prova temporanea per esplorare tutte le funzionalità senza restrizioni.

## Guida all'implementazione
Divideremo l'implementazione in due parti logiche:

1. **Come caricare un documento Word in Java**  
2. **Come estrarre forme e immagini (cioè estrarre immagini da Word)**

### Caricamento di un documento Word
Per prima cosa, configura le opzioni di caricamento e istanzia il `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Consiglio:** Sostituisci `"YOUR_DOCUMENT_DIRECTORY/document.docx"` con un percorso assoluto o relativo che punti al file che desideri elaborare.

### Estrarre informazioni su forme e immagini
Ora che il documento è caricato, puoi iterare attraverso ogni sezione e ogni forma, estraendo sia i dati delle forme vettoriali sia i dettagli delle immagini incorporate.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Perché è importante:** La chiamata `shape.getImage()` ti fornisce accesso diretto alla rappresentazione binaria di ogni immagine, consentendoti di salvarla su disco, inviarla su una rete o passarla a una libreria di elaborazione delle immagini.

## Problemi comuni e soluzioni
| Problema | Soluzione |
|---------|----------|
| **FileNotFoundException** – percorso errato | Verifica il percorso del file e assicurati che l'applicazione abbia i permessi di lettura. |
| **OutOfMemoryError** su documenti di grandi dimensioni | Processa le sezioni una alla volta e chiama `watermarker.close()` non appena hai terminato un batch. |
| Le forme restituiscono `null` per `getImage()` | Non tutte le forme sono immagini; alcune sono oggetti di disegno. Controlla `shape.getShapeType()` prima di accedere all'immagine. |
| Licenza non applicata | Aggiungi `License.setLicense("path/to/license/file.lic");` prima di creare il `Watermarker`. |

## Applicazioni pratiche
- **Generazione automatica di report:** Estrai grafici e loghi dai modelli per riutilizzarli nei cruscotti.  
- **Audit dei contenuti:** Scansiona i documenti aziendali alla ricerca di grafiche proibite.  
- **Progetti di migrazione:** Esporta le immagini incorporate prima di trasferire i contenuti a un nuovo CMS.

## Considerazioni sulle prestazioni
- Rilascia prontamente l'istanza `Watermarker` (`watermarker.close()`).  
- Per file molto grandi (>50 MB), considera lo streaming delle sezioni anziché caricare l'intero documento in memoria.  
- Usa l'ultima versione di GroupDocs.Watermark per miglioramenti delle prestazioni.

## Conclusione
Ora disponi di un approccio completo e pronto per la produzione per **estrarre immagini da Word** documenti e recuperare i metadati delle forme usando GroupDocs.Watermark per Java. Questa capacità sblocca scenari di automazione potenti, dalla generazione di report dinamici all'esecuzione di audit di documenti su larga scala.

### Prossimi passi
- Sperimenta salvando le immagini estratte su disco (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Esplora API aggiuntive come la rimozione o l'aggiunta di watermark.  
- Integra questa logica nel tuo flusso di lavoro di gestione dei documenti esistente.

## Sezione FAQ
**D: Cos'è GroupDocs.Watermark per Java?**  
R: È una libreria completa progettata per gestire i watermark e estrarre elementi visivi da vari formati di documento, migliorando l'automazione delle attività di manipolazione dei documenti.

**D: Posso estrarre immagini da file Word protetti da password?**  
R: Sì. Carica il documento con `WordProcessingLoadOptions` che include la password, quindi procedi con la stessa logica di estrazione.

**D: L'API supporta anche i file .doc (binari)?**  
R: La libreria è principalmente rivolta al formato OpenXML `.docx`, ma può anche aprire file legacy `.doc` dopo la conversione.

**D: Come salvo le immagini estratte nel file system?**  
R: Usa `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` all'interno del ciclo dove `shape.getImage()` non è null.

**D: Esiste un limite al numero di forme che posso processare?**  
R: Non c'è un limite rigido, ma il consumo di memoria aumenta con la dimensione del documento; processa le sezioni in modo sequenziale per file molto grandi.

---

**Ultimo aggiornamento:** 2025-12-20  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs