---
date: '2026-04-04'
description: Scopri come estrarre gli allegati Excel e gli oggetti incorporati utilizzando
  GroupDocs.Watermark per Java. Ottimizza la gestione dei documenti in modo efficiente.
keywords:
- how to extract excel
- extract embedded objects
- java attachment extraction
title: Come estrarre gli allegati Excel con GroupDocs Watermark Java
type: docs
url: /it/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# Come estrarre gli allegati Excel con GroupDocs.Watermark Java

L'estrazione di file incorporati da una cartella di lavoro Excel può rappresentare un vero collo di bottiglia quando si automatizzano pipeline di dati o si costruiscono soluzioni di archiviazione. In questo tutorial imparerai **come estrarre gli allegati Excel** rapidamente e in modo affidabile usando la libreria GroupDocs.Watermark per Java. Ti guideremo attraverso la configurazione dell'ambiente, la revisione del codice e consigli pratici così potrai integrare questa funzionalità nelle tue applicazioni subito.

## Risposte rapide
- **Quale libreria gestisce gli allegati Excel?** GroupDocs.Watermark for Java  
- **Metodo principale usato?** `Watermarker` with `SpreadsheetLoadOptions`  
- **È necessaria una licenza?** Una versione di prova gratuita funziona per lo sviluppo; è necessaria una licenza completa per la produzione  
- **Versione Java supportata?** Java 8 o superiore  
- **Posso estrarre immagini di anteprima?** Sì, tramite `getPreviewImageContent()`  

## Cos'è “come estrarre excel” nel contesto dell'automazione dei documenti?

Quando diciamo *come estrarre excel* ci riferiamo all'estrazione programmatica di qualsiasi oggetto incorporato — come PDF, immagini o altri fogli di calcolo — memorizzato all'interno di un file `.xlsx`. Questo consente processi a valle come l'analisi dei dati, l'archiviazione per conformità o la generazione dinamica di report senza l'intervento manuale dell'utente.

## Perché usare GroupDocs.Watermark per Java?

GroupDocs.Watermark fornisce un'API di alto livello che astrae la gestione low‑level di OpenXML, offrendoti:

- **Modello di oggetti semplice** per fogli di lavoro, allegati e metadati  
- **Estrazione di anteprime integrata** per controlli visivi rapidi  
- **Licenza robusta** che scala dalla versione di prova all'impresa  

## Prerequisiti

- **Java Development Kit (JDK) 8+** – installato e aggiunto al tuo `PATH`  
- **IDE** – IntelliJ IDEA, Eclipse o qualsiasi editor preferisci  
- **Maven** – per la gestione delle dipendenze (in alternativa puoi scaricare il JAR)  

### Librerie e dipendenze richieste

Avrai bisogno della libreria GroupDocs.Watermark per Java. Questo tutorial utilizza la versione 24.11, che puoi ottenere da Maven Central o dal repository ufficiale di GroupDocs.

### Link di download diretto (preservato)

In alternativa, scarica l'ultima versione da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Configurazione di GroupDocs.Watermark per Java

### Configurazione Maven

Add the following configuration to your `pom.xml` file:

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

### Passaggi per l'acquisizione della licenza

- **Prova gratuita:** Inizia con una prova gratuita per esplorare le funzionalità della libreria.  
- **Licenza temporanea:** Ottieni una licenza temporanea per un uso di sviluppo esteso.  
- **Acquisto:** Aggiorna a una licenza completa per le distribuzioni in produzione.  

### Inizializzazione e configurazione di base

```java
import com.groupdocs.watermark.Watermarker;

public class DocumentSetup {
    public static void main(String[] args) {
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        Watermarker watermarker = new Watermarker(filePath);
        
        // Your code to manipulate the document goes here
        
        watermarker.close();
    }
}
```

## Come estrarre gli allegati Excel usando GroupDocs.Watermark

### Carica e prepara il foglio di calcolo

**Panoramica:** Carica la tua cartella di lavoro con `SpreadsheetLoadOptions` per controllare l'uso della memoria e il comportamento di caricamento.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.Watermarker;

public class ExtractAttachments {
    public static void extract() {
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### Accedi al contenuto del foglio di calcolo

**Panoramica:** Recupera il modello di contenuto di alto livello che ti dà accesso ai fogli di lavoro e agli oggetti incorporati.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### Itera attraverso i fogli di lavoro

**Panoramica:** Scorri ogni foglio di lavoro e poi ogni allegato per elaborarli singolarmente.

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### Estrai i dettagli dell'allegato

**Panoramica:** Per ogni allegato, estrai metadati utili come testo alternativo, posizione, dimensione e i byte effettivi del file.

```java
import com.groupdocs.watermark.contents.SpreadsheetAttachment;

// Display alternative text and frame details of each attachment.
System.out.println("Alternative text: " + attachment.getAlternativeText());
System.out.println("Attachment frame x-coordinate: " + attachment.getX());
System.out.println("Attachment frame y-coordinate: " + attachment.getY());
System.out.println("Attachment frame width: " + attachment.getWidth());
System.out.println("Attachment frame height: " + attachment.getHeight());

// Check if a preview image is available and display its size.
int imageSize = (attachment.getPreviewImageContent() != null) ? attachment.getPreviewImageContent().length : 0;
System.out.println("Preview image size: " + imageSize);

if (attachment.isLink()) {
    System.out.println("Full path to the attached file: " + attachment.getSourceFullName());
} else {
    System.out.println("File type: " + attachment.getDocumentInfo().getFileType());
    System.out.println("Name of the source file: " + attachment.getSourceFullName());
    System.out.println("File size: " + attachment.getContent().length);
}
```

### Chiudi le risorse

**Panoramica:** Chiudi sempre l'istanza `Watermarker` per liberare le risorse native ed evitare perdite di memoria.

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## Applicazioni pratiche (Perché è importante)

1. **Consolidamento dati automatizzato** – Estrai ogni PDF o immagine allegata da un batch di report per un'unica esecuzione analitica.  
2. **Archiviazione per conformità** – Conserva i file estratti insieme al foglio di lavoro originale per soddisfare i requisiti di audit.  
3. **Generazione dinamica di report** – Riutilizza grafici o documenti incorporati come risorse separate in un motore di reporting personalizzato.  

## Considerazioni sulle prestazioni

- **Gestione della memoria:** Chiudi il `Watermarker` non appena hai finito di elaborare ogni file.  
- **Elaborazione batch:** Elabora i fogli di lavoro in blocchi (ad es., 10‑20 file per thread) per mantenere stabile l'uso della CPU.  
- **Ottimizzazione delle opzioni di caricamento:** Usa `SpreadsheetLoadOptions` per limitare il numero di righe/colonne caricate quando ti servono solo gli allegati.  

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **`NullPointerException` su `getPreviewImageContent()`** | Verifica che l'allegato contenga effettivamente un'anteprima; non tutti i tipi di file ne generano una. |
| **File Excel di grandi dimensioni causano OutOfMemoryError** | Aumenta la dimensione dell'heap JVM (`-Xmx2g`) o elabora i file in sequenza con `close()` esplicito dopo ciascuno. |
| **LicenseException in produzione** | Assicurati di aver applicato un file di licenza completa valido tramite `License.setLicense("path/to/license.json")`. |

## Domande frequenti

**D: Posso estrarre gli allegati da file Excel protetti da password?**  
R: Sì. Carica la cartella di lavoro con `SpreadsheetLoadOptions` che includa la password, quindi procedi come mostrato.

**D: L'API supporta l'estrazione di grafici incorporati come immagini?**  
R: I grafici sono trattati come oggetti separati; è possibile recuperare la loro immagine di anteprima tramite `getPreviewImageContent()`.

**D: Quali formati di file possono essere estratti come allegati?**  
R: Qualsiasi tipo di file incorporato nella cartella di lavoro — PDF, DOCX, PNG, JPG, ecc. — è accessibile tramite l'API `SpreadsheetAttachment`.

**D: Esiste un modo per salvare automaticamente i file estratti?**  
R: Puoi scrivere `attachment.getContent()` in un `FileOutputStream` a tua scelta. Il tutorial si concentra sulla stampa dei metadati, ma lo stesso array di byte può essere salvato.

**D: Devo gestire le formule Excel quando estraggo gli allegati?**  
R: No. Gli allegati sono indipendenti dalle formule delle celle; sono memorizzati come oggetti OLE all'interno della cartella di lavoro.

## Conclusione

Ora hai una guida completa, pronta per la produzione, su **come estrarre gli allegati Excel** usando GroupDocs.Watermark per Java. Integrando questi passaggi nei tuoi pipeline di automazione, puoi semplificare la raccolta dei dati, migliorare la conformità e sbloccare nuove possibilità di reporting. Esplora altre funzionalità della libreria — come il watermarking o la redazione — per migliorare ulteriormente il tuo flusso di lavoro di elaborazione dei documenti.

---

**Ultimo aggiornamento:** 2026-04-04  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs