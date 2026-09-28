---
date: '2026-09-26'
description: Scopri come convertire un documento in immagine e generare thumbnail
  in Java usando GroupDocs.Watermark. Guida passo-passo che copre setup, preview streams
  e performance tips.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Scopri come convertire un documento in immagine e generare thumbnail
  in Java usando GroupDocs.Watermark. Questa guida ti accompagna attraverso installation,
  stream handling e performance optimisation per fast preview creation.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Converti documento in immagine con GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Converti documento in immagine con GroupDocs.Watermark Java
type: docs
url: /it/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Converti documento in immagine con GroupDocs.Watermark Java

Generare anteprime immagine leggere di documenti multi‑pagina è una necessità comune per portali, sistemi di gestione dei contenuti e servizi di archiviazione cloud. Con **convert document to image** offri agli utenti finali un rapido indizio visivo senza l’onere di caricare l’intero file. La libreria GroupDocs.Watermark Java non solo aggiunge filigrane, ma fornisce anche un motore di anteprima ad alte prestazioni che può **java generate thumbnails** per ogni pagina in un unico passaggio.

In questo tutorial imparerai come configurare la libreria, creare stream di pagina personalizzati, rilasciare le risorse in modo sicuro e, infine, produrre anteprime immagine per ogni pagina di un documento sorgente. Le istruzioni sono scritte per sviluppatori familiari con Java e i concetti di programmazione orientata agli oggetti, e includono consigli di best‑practice per la gestione di grandi lotti di file.

## Risposte rapide
- **Qual è il primo passo?** Aggiungi la dipendenza Maven di GroupDocs.Watermark e inizializza un `Watermarker` con il percorso del file sorgente.  
- **Come vengono create le immagini di anteprima?** Implementa `ICreatePageStream` per aprire uno stream di output per ogni pagina, quindi chiama `generatePreview()` con le opzioni appropriate.  
- **È necessaria una licenza?** Una versione di prova funziona per scenari di base, ma una licenza completa rimuove le filigrane e sblocca l’elaborazione batch.  
- **Posso elaborare PDF più grandi di 200 pagine?** Sì – la libreria trasmette le pagine in streaming, quindi l’utilizzo della memoria rimane basso anche per file da 500 pagine.  
- **Quali formati immagine sono supportati?** PNG, JPEG, BMP e TIFF sono disponibili subito.

## Cos'è convert document to image?
La frase **convert document to image** descrive il processo di rendering di ogni pagina di un file sorgente (PDF, DOCX, PPTX, ecc.) in un’immagine raster come PNG o JPEG. Questa conversione è utile per gallerie di miniature, pannelli di anteprima e visualizzatori di documenti ottimizzati per dispositivi mobili.

## Perché usare GroupDocs.Watermark per la generazione di anteprime?
GroupDocs.Watermark supporta **30+ input formats** e può generare anteprime per documenti fino a **500 pages** senza caricare l’intero file in memoria. Internamente elabora le pagine in modo sequenziale, mantenendo l’utilizzo dell’heap Java al di sotto dei 50 MB anche per PDF di grandi dimensioni. La libreria offre inoltre ottimizzazione delle immagini integrata, consentendo di specificare DPI, profondità colore e livello di compressione, il che produce miniature tipicamente **70 % più piccole** rispetto a una rasterizzazione ingenua.

## Prerequisiti

- **Java Development Kit (JDK) 11 o più recente** – la libreria è compilata per Java 8+, ma JDK 11 offre supporto a lungo termine e migliori prestazioni.
- **Maven 3.6+** – per la gestione delle dipendenze.
- **GroupDocs.Watermark per Java versione 24.11** – l’ultima versione stabile al momento della stesura.
- **Conoscenza di base degli stream I/O di Java** – creerai oggetti `FileOutputStream` per ogni pagina di anteprima.
- **Una chiave di licenza** (opzionale per la produzione) – la versione di prova limita la dimensione dell’anteprima a 5 MB per documento.

## Come configurare GroupDocs.Watermark per Java

Per configurare GroupDocs.Watermark, aggiungi prima il repository Maven e poi includi la libreria come dipendenza nel `pom.xml` del tuo progetto. Questo garantisce a Maven di scaricare gli artefatti corretti e rende le classi disponibili nel classpath per la compilazione e l’esecuzione.

### Aggiungi la dipendenza Maven
La libreria è distribuita tramite Maven Central. Aggiungi il seguente snippet al tuo `pom.xml` all’interno del blocco `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Suggerimento:** Mantieni il numero di versione in una proprietà (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) così potrai aggiornare facilmente.

### Download diretto (alternativa)
Se preferisci l’installazione manuale, puoi scaricare il JAR dalla pagina ufficiale delle release: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Come ottenere e applicare una licenza

Applicare una licenza a GroupDocs.Watermark rimuove le limitazioni della versione di prova e disabilita la filigrana predefinita. Posiziona il file di licenza in una posizione nota e indica l’API al suo percorso, oppure incorpora direttamente il percorso della licenza nel codice prima di qualsiasi altra chiamata. Una volta caricato, tutte le operazioni successive funzionano in modalità completa.

Puoi:

- **Richiedi una prova gratuita** dal portale GroupDocs – fornisce un file di licenza di 30 giorni.
- **Genera una licenza temporanea** tramite il generatore di licenze online per ambienti di valutazione.
- **Acquista una licenza commerciale** per uso illimitato in produzione e supporto prioritario.

Posiziona il file di licenza (`GroupDocs.Watermark.lic`) nella radice del tuo progetto o specifica il suo percorso programmaticamente con `Watermarker.setLicense("path/to/license.file")`.

## Come inizializzare il Watermarker

Inizializza il `Watermarker` fornendo il percorso del documento sorgente, includendo opzionalmente una password per file protetti. Il costruttore valida il formato e prepara i parser interni, consentendoti di chiamare immediatamente i metodi di anteprima o di filigrana. Dopo la creazione, conserva un riferimento per riutilizzare l’istanza per più operazioni, se necessario.

La classe `Watermarker` è l’oggetto centrale di GroupDocs.Watermark che carica un documento ed espone operazioni come l’inserimento di filigrane e la generazione di anteprime.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – percorso assoluto o relativo del file sorgente.
- Il costruttore valida il formato del file e prepara i parser interni.

> **Ancora di definizione:** `Watermarker` è il punto di ingresso per tutte le azioni di elaborazione dei documenti in GroupDocs.Watermark per Java.

## Come creare stream di pagina per la generazione di anteprime

Crea stream di pagina personalizzati implementando l’interfaccia `ICreatePageStream`, che la libreria invoca per ogni pagina che rende. La tua implementazione dovrebbe generare un nuovo `OutputStream`—tipicamente un `FileOutputStream`—che punti a un file con nome univoco basato sul numero di pagina. Questo approccio isola l’output di ciascuna pagina e impedisce sovrapposizioni di dati.

Per **java generate thumbnails**, devi fornire uno stream per ogni pagina dove verrà scritta l’immagine renderizzata. Implementa l’interfaccia `ICreatePageStream`; la libreria chiama la tua implementazione per ogni pagina elaborata.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** ti consente di inserire il numero di pagina direttamente nel nome del file, rendendo l'elaborazione batch semplice.
- Il metodo restituisce un nuovo `OutputStream` per ogni pagina, garantendo che le pagine precedenti non interferiscano con le scritture successive.

> **Ancora di definizione:** `ICreatePageStream` è un’interfaccia di callback che ti permette di definire come vengono creati gli stream di output per ogni pagina di anteprima.

## Come rilasciare gli stream di pagina dopo la generazione dell'anteprima

Dopo che l’immagine di una pagina è stata scritta, la libreria chiama `IReleasePageStream` per consentirti di chiudere e pulire lo stream di output associato. Implementa questo callback per rilasciare in modo sicuro i handle dei file, svuotare i buffer e registrare eventuali log aggiuntivi. Una pulizia corretta evita perdite di descrittori e garantisce che le pagine successive possano essere elaborate senza interferenze.

Una corretta pulizia delle risorse previene perdite di handle di file e impedisce alla JVM di esaurire i descrittori. Implementa `IReleasePageStream` per chiudere gli stream una volta che la libreria segnala che la pagina è terminata.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Ancora di definizione:** `IReleasePageStream` è un’interfaccia di callback che ti permette di definire una logica personalizzata per lo smaltimento delle risorse di output specifiche per pagina.

## Come generare anteprime di documento (convert document to image)

Genera le anteprime chiamando `generatePreview()` sull’istanza `Watermarker`, fornendo un oggetto `PreviewOptions` che definisce risoluzione, formato immagine e intervallo di pagine. Il metodo itera su ogni pagina, utilizza i tuoi creatori di stream per scrivere l’immagine raster e poi rilascia gli stream. Questo processo produce un set di file immagine che rappresentano le pagine del documento.

Con `Watermarker`, `FeatureCreatePageStream` e `FeatureReleasePageStream` pronti, puoi invocare il motore di anteprima. Il metodo `generatePreview()` itera su ogni pagina, chiama i tuoi creatori di stream, scrive l’immagine e infine rilascia gli stream.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** controlla i DPI; 150 DPI è un buon compromesso per le anteprime web.
- **`ImageFormat`** può essere PNG, JPEG, BMP o TIFF a seconda dei requisiti successivi.
- Il metodo elabora le pagine in sequenza, quindi il consumo di memoria rimane basso anche per documenti con centinaia di pagine.

> **Ancora di definizione:** `generatePreview()` è la chiamata API che rende ogni pagina del documento caricato in un’immagine usando gli stream forniti.

## Applicazioni pratiche di convert document to image

Generare anteprime immagine apre molte possibilità:

1. **Browser di documenti** – Mostra una griglia di miniature PNG così gli utenti possono scorrere grandi PDF senza aprirli.
2. **Snippet dei risultati di ricerca** – Allega un’immagine di anteprima alle voci dell’indice di ricerca per un’interfaccia più ricca.
3. **Allegati email** – Inserisci una piccola anteprima dei PDF allegati nel corpo dell’email.
4. **App mobili** – Riduci la larghezza di banda inviando anteprime PNG da 200 KB invece dei PDF completi.
5. **Portali di conformità** – Renderizza versioni contrattuali con filigrana obbligatoria come immagini per le tracce di audit.

## Considerazioni sulle prestazioni quando si **java generate thumbnails**

Quando ti occupi di elaborazione di massa, tieni presente questi consigli di ottimizzazione:

- **Buffering dello stream** – Avvolgi il `FileOutputStream` in un `BufferedOutputStream` per ridurre al minimo I/O su disco.
- **Esecuzione batch parallela** – Usa `ForkJoinPool` di Java per elaborare più documenti contemporaneamente; ogni task dovrebbe creare la propria istanza di `Watermarker` per evitare problemi di thread‑safety.
- **Limita i DPI per le miniature** – 72–150 DPI sono sufficienti per la maggior parte degli scenari UI; DPI più alti dovrebbero essere riservati a anteprime pronte per la stampa.
- **Riutilizza gli oggetti licenza** – Caricare il file di licenza una volta per JVM riduce l’overhead.
- **Monitora la memoria** – La libreria mantiene in memoria solo la pagina corrente. Per file estremamente grandi, considera di aumentare moderatamente l’heap JVM (es. `-Xmx512m`) per gestire picchi occasionali.

## Problemi comuni e come evitarli

| Sintomo | Probabile causa | Correzione |
|---------|-----------------|------------|
| `OutOfMemoryError` durante la generazione dell'anteprima | Uso di `ImageFormat.Jpeg` a 300 DPI su un PDF di 1000 pagine | Riduci i DPI o passa a PNG con profondità colore inferiore |
| File di anteprima vuoti | `FeatureCreatePageStream` restituisce lo stesso `FileOutputStream` per ogni pagina | Assicurati che venga creato un nuovo stream per ogni `pageNumber` |
| Le immagini di anteprima sono ruotate | Il PDF sorgente contiene metadati di rotazione non rispettati | Chiama `previewOptions.setRotatePages(true)` (se disponibile) |
| Appare un avviso di licenza | File di licenza non trovato o percorso errato | Verifica che `Watermarker.setLicense("path/to/license.file")` venga eseguito prima di qualsiasi altra chiamata API |

## Domande frequenti

**Q: Posso generare anteprime per PDF protetti da password?**  
A: Sì. Passa la password al costruttore `Watermarker`: `new Watermarker("file.pdf", "password")`.

**Q: Quali formati immagine sono supportati per l'output dell'anteprima?**  
A: PNG, JPEG, BMP e TIFF sono disponibili. PNG è consigliato per miniature lossless.

**Q: Quante pagine possono essere elaborate in una singola chiamata?**  
A: La libreria non impone limiti rigidi; puoi generare anteprime per documenti con migliaia di pagine, limitato solo dallo spazio di archiviazione e dalla larghezza di banda I/O.

**Q: È necessaria una licenza separata per ogni istanza del server?**  
A: Un singolo file di licenza può essere riutilizzato su più istanze purché l'uso totale sia conforme ai termini della licenza.

**Q: Esiste un modo per generare una singola miniatura combinata (ad esempio solo la prima pagina)?**  
A: Sì. Imposta `previewOptions.setPages(new int[]{1})` per limitare la generazione alla prima pagina.

## Conclusione

Ora disponi di un flusso di lavoro completo, pronto per la produzione, per **convert document to image** e **java generate thumbnails** usando GroupDocs.Watermark. Configurando gestori di stream di pagina personalizzati, mantieni basso l’utilizzo della memoria, e regolando `PreviewOptions` controlli la qualità dell’immagine e la dimensione del file. Queste tecniche ti consentono di incorporare anteprime rapide e di alta qualità in qualsiasi applicazione basata su Java—sia che si tratti di un portale web, di un client desktop o di un microservizio cloud‑native.

---

**Ultimo aggiornamento:** 2026-09-26  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs

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
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Tutorial correlati

- [Come recuperare le informazioni del documento usando GroupDocs.Watermark per Java: Guida passo passo](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Tutorial avanzati sulle funzionalità di filigrana per GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Come aggiungere una filigrana immagine in Java usando GroupDocs.Watermark: Guida passo passo](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)