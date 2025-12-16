---
date: '2025-12-16'
description: Scopri come visualizzare in anteprima i documenti usando GroupDocs.Watermark
  per Java e genera facilmente miniature con l'integrazione Maven di GroupDocs Watermark.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 'Come visualizzare in anteprima i documenti con GroupDocs.Watermark in Java:
  Guida avanzata'
type: docs
url: /it/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Come visualizzare in anteprima i documenti con GroupDocs.Watermark in Java: Guida avanzata

## Introduzione

In questa guida, imparerai **come visualizzare in anteprima i documenti** in modo efficiente usando la libreria GroupDocs.Watermark per Java. Creare anteprime dei documenti è una funzionalità cruciale per le applicazioni che gestiscono grandi volumi di file, consentendo agli utenti di dare un'occhiata al contenuto senza aprire l'intero documento. Seguendo i passaggi seguenti, vedrai anche come **java generate thumbnail** immagini e integrare la libreria tramite **maven groupdocs watermark**. Iniziamo preparando il tuo ambiente di sviluppo.

## Risposte rapide
- **Qual è lo scopo principale?** Generare anteprime leggere pagina‑per‑pagina (thumbnail) di qualsiasi documento supportato.  
- **Quale libreria è necessaria?** GroupDocs.Watermark per Java (versione 24.11).  
- **Come aggiungo la libreria?** Usa lo snippet Maven fornito nella sezione di configurazione.  
- **Posso generare anteprime per tutte le pagine?** Sì – l'API trasmette ogni pagina in un file immagine.  
- **È necessaria una licenza?** Una versione di prova funziona per test di base; è necessaria una licenza completa per l'uso in produzione.  

## Cos'è la generazione di anteprime dei documenti?
La generazione di anteprime dei documenti converte ogni pagina di un file sorgente (PDF, DOCX, VDX, ecc.) in un formato immagine come PNG. Queste immagini di anteprima fungono da thumbnail che possono essere visualizzate nei browser di file, nei portali web o nelle app mobili, migliorando notevolmente l'esperienza dell'utente e riducendo i tempi di caricamento.

## Perché usare GroupDocs.Watermark per Java?
- **Velocità e scalabilità** – Il codice nativo ottimizzato gestisce rapidamente documenti di grandi dimensioni.  
- **Ampio supporto di formati** – Funziona con oltre 100 tipi di file pronti all'uso.  
- **Watermark integrato** – Puoi aggiungere filigrane durante la generazione delle anteprime, mantenendo i tuoi asset protetti.  
- **API semplice** – È necessario un codice minimo per produrre thumbnail di alta qualità.

## Prerequisiti

1. **Java Development Kit (JDK)** – JDK 8 o versioni successive installate.  
2. **IDE** – IntelliJ IDEA, Eclipse o qualsiasi editor tu preferisca.  
3. **Maven** – Per la gestione delle dipendenze (vedi la configurazione Maven di seguito).  
4. **Conoscenze di base di Java** – Familiarità con I/O di file e programmazione orientata agli oggetti.

## Configurazione di GroupDocs.Watermark per Java

Per iniziare a usare GroupDocs.Watermark nel tuo progetto, aggiungilo come dipendenza Maven:

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

In alternativa, puoi scaricare l'ultimo JAR direttamente dalla pagina di rilascio ufficiale:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### Acquisizione della licenza

- **Prova gratuita** – Testa la libreria con funzionalità limitate.  
- **Licenza temporanea** – Ottieni una chiave a breve termine per la valutazione completa delle funzionalità.  
- **Licenza completa** – Acquista per uso illimitato e supporto prioritario.

## Guida all'implementazione

### Inizializzare Watermarker

#### Panoramica
Il primo passo è creare un'istanza di `Watermarker` che punti al documento sorgente.

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

*Punto chiave:* Sostituisci `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` con il percorso reale del file che desideri visualizzare in anteprima.

### Creare uno stream di pagina per la generazione dell'anteprima

#### Panoramica
Un creatore di stream personalizzato indica all'API dove scrivere l'immagine di anteprima di ogni pagina.

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

Il `fileNameTemplate` utilizza un segnaposto (`%s`) che l'API sostituisce con il numero della pagina corrente, producendo file come `page1.png`, `page2.png`, ecc.

### Rilasciare lo stream di pagina

#### Panoramica
Dopo che un'immagine di anteprima è stata scritta, lo stream deve essere chiuso per liberare le risorse di sistema.

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

Rilasciare correttamente gli stream previene perdite di memoria, specialmente durante l'elaborazione di grandi lotti di documenti.

### Generare l'anteprima del documento

#### Panoramica
Con il `Watermarker`, il creatore di stream e il gestore di rilascio pronti, puoi generare anteprime per ogni pagina.

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

*Spiegazione degli oggetti chiave:*
- `createPageStream` – decide dove salvare ogni file PNG.  
- `releasePageStream` – garantisce che il handle del file sia chiuso dopo la scrittura.  
- `previewOptions` – raggruppa i due gestori per la chiamata `generatePreview`.

## Applicazioni pratiche

Generare anteprime dei documenti è utile in molti scenari reali:

1. **App visualizzatori PDF** – Mostra strisce di thumbnail senza caricare l'intero PDF.  
2. **Sistemi di gestione dei contenuti (CMS)** – Consente agli editor di sfogliare rapidamente i documenti.  
3. **Servizi di archiviazione cloud** – Fornisce thumbnail visivi per i file archiviati, migliorando la navigazione.

## Considerazioni sulle prestazioni

- **Gestione della memoria** – Usa il pattern di rilascio dello stream mostrato sopra per mantenere basso l'utilizzo di memoria.  
- **Ottimizzazione I/O** – Gli stream bufferizzati possono ridurre ulteriormente la latenza del disco quando si gestiscono migliaia di pagine.  
- **Elaborazione parallela** – Per operazioni di massa, considera l'elaborazione simultanea di più documenti usando `ExecutorService` di Java.

## Problemi comuni e soluzioni

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| Nessun file di anteprima generato | Percorso della directory di output errato o permessi di scrittura mancanti | Verifica che `YOUR_OUTPUT_DIRECTORY` esista e sia scrivibile |
| Errore di out‑of‑memory su PDF di grandi dimensioni | Stream non rilasciati tempestivamente | Assicurati che `FeatureReleasePageStream` sia implementato correttamente |
| Formato file non supportato | Tipo di documento non coperto da GroupDocs.Watermark | Controlla la lista di supporto dei formati della libreria; converti a un tipo supportato se necessario |

## Domande frequenti

**D: Posso generare anteprime per documenti protetti da password?**  
R: Sì. Carica il documento con la password appropriata usando il costruttore `Watermarker` che accetta un parametro password, quindi procedi con la generazione dell'anteprima come mostrato.

**D: La libreria supporta altri formati immagine oltre PNG?**  
R: L'API di anteprima genera PNG di default, ma puoi convertire gli stream risultanti in JPEG o BMP usando le librerie immagine standard di Java, se necessario.

**D: Quante pagine posso anteporre in un'unica esecuzione?**  
R: Non c'è un limite rigido; tuttavia, l'elaborazione di documenti estremamente grandi può beneficiare del batch processing o dell'aumento della dimensione dell'heap JVM.

**D: È necessaria una licenza per la generazione di anteprime?**  
R: Una licenza di prova funziona per la valutazione, ma è necessaria una licenza completa per le distribuzioni in produzione per rimuovere le filigrane e sbloccare tutte le funzionalità.

**D: Posso personalizzare la risoluzione dell'immagine delle anteprime?**  
R: Sì. `PreviewOptions` fornisce proprietà come `setResolution` dove puoi specificare le impostazioni DPI prima di chiamare `generatePreview`.

## Conclusione

Ora disponi di un flusso di lavoro completo e pronto per la produzione per **come visualizzare in anteprima i documenti** usando GroupDocs.Watermark in Java. Inizializzando il `Watermarker`, gestendo gli stream delle pagine e rilasciando correttamente le risorse, puoi generare thumbnail di alta qualità su larga scala. Applica queste tecniche per migliorare l'esperienza dell'utente in qualsiasi applicazione con molti documenti.

---

**Ultimo aggiornamento:** 2025-12-16  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs