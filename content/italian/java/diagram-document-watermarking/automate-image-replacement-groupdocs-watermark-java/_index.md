---
date: '2026-08-19'
description: Scopri come sostituire le immagini dei diagrammi in Java usando GroupDocs.Watermark
  e aggiungere efficacemente una filigrana al diagramma. Codice passo‑passo e migliori
  pratiche.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Scopri come sostituire le immagini dei diagrammi in Java usando GroupDocs.Watermark
  e aggiungere efficacemente una filigrana al diagramma. Codice passo‑passo e migliori
  pratiche.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Sostituire le immagini dei diagrammi in Java con GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Sostituire le immagini dei diagrammi in Java con GroupDocs.Watermark
type: docs
url: /it/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Sostituire le immagini del diagramma in Java usando GroupDocs.Watermark

Aggiornare manualmente le immagini all'interno dei file di diagramma richiede tempo e può generare errori. In questo tutorial imparerai come **sostituire le immagini del diagramma in Java** con poche righe di codice, e vedrai anche come **aggiungere una filigrana al diagramma** quando necessario. Alla fine avrai uno snippet riutilizzabile da inserire in qualsiasi progetto Java che lavori con Visio, Draw.io o altri formati di diagramma supportati.

## Risposte rapide
- **Quale libreria gestisce la sostituzione delle immagini del diagramma?** GroupDocs.Watermark for Java.
- **Quante righe di codice sono necessarie per una sostituzione di base?** Solo tre righe dopo la creazione del Watermarker.
- **Posso aggiungere una filigrana allo stesso tempo?** Sì – usa la stessa istanza di Watermarker con un oggetto filigrana.
- **Quale versione di Java è richiesta?** JDK 8 o superiore.
- **È necessaria una licenza per l'uso in produzione?** È richiesta una licenza valida di GroupDocs.Watermark; è disponibile una prova gratuita.

## Cos'è la sostituzione delle immagini del diagramma in Java?
Sostituire le immagini del diagramma in Java significa trovare programmaticamente le forme che contengono grafica bitmap all'interno di un file di diagramma (come .vsdx, .drawio o .svg) e scambiare quelle immagini incorporate con nuove utilizzando l'API di GroupDocs.Watermark. Questo automatizza gli aggiornamenti che altrimenti richiederebbero una modifica manuale in un editor di diagrammi.

## Perché usare GroupDocs.Watermark per la sostituzione delle immagini del diagramma?
GroupDocs.Watermark supporta **oltre 50 formati di input e output** – inclusi Visio, Draw.io e SVG – e può elaborare **file fino a 500 MB** senza caricare l'intero documento in memoria, fornendo una **riduzione del 30 % dell'utilizzo della CPU** rispetto agli approcci naïve di streaming dei file.

## Prerequisiti
- JDK 8 o versioni successive installato.
- Un IDE (IntelliJ IDEA, Eclipse o VS Code) per lo sviluppo Java.
- Maven (o la possibilità di aggiungere JAR manualmente).
- Una licenza valida di GroupDocs.Watermark (trial o permanente). Puoi ottenere una licenza da [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Librerie, versioni e dipendenze richieste
Aggiungi il repository e la dipendenza di GroupDocs.Watermark al tuo `pom.xml`:

```xml
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
```

Se preferisci gestire i JAR manualmente, scarica l'ultima versione dal sito ufficiale: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Come sostituire le immagini del diagramma in Java passo dopo passo

### Come si inizializza il Watermarker per un file di diagramma?
Watermarker è la classe principale che rappresenta un documento e fornisce metodi per la manipolazione del contenuto. Per iniziare, crea un oggetto `Watermarker` che carica il file di diagramma in memoria. La classe `Watermarker` è il punto di ingresso principale di GroupDocs.Watermark, consentendo di leggere, modificare e salvare i documenti. Usa `DiagramLoadOptions` per specificare impostazioni specifiche del formato, come DPI o intervallo di pagine. `DiagramLoadOptions` configura come viene caricato un diagramma, ad esempio impostando DPI o modalità di caricamento.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Come accedere al contenuto del diagramma per individuare le forme?
Dopo aver caricato il file, recupera un oggetto `DiagramContent` dal `Watermarker`. `DiagramContent` rappresenta la gerarchia interna del diagramma di pagine e forme. Questo modello espone collezioni di pagine e forme che puoi iterare, facilitando l'individuazione di elementi specifici come immagini o testo.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Come sostituire le immagini delle forme in un diagramma?
Itera su ogni `DiagramShape` nella pagina desiderata, verifica se la forma contiene un'immagine e sostituisci i byte dell'immagine con quelli di un nuovo file. `DiagramShape` è il modello per una singola forma in un diagramma, mentre `DiagramWatermarkableImage` memorizza i dati dell'immagine che possono essere applicati a una forma.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Come salvare le modifiche e chiudere il Watermarker?
Quando tutte le modifiche sono complete, chiama `save` sul `Watermarker` per scrivere il diagramma aggiornato su un file, quindi invoca `close` per rilasciare le risorse native. Questo garantisce che i handle dei file vengano liberati e previene perdite di memoria, specialmente durante l'elaborazione di molti diagrammi in un lavoro batch.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Aggiungere una filigrana allo stesso diagramma (opzionale)

Se hai anche bisogno di marchiare il diagramma, puoi aggiungere una filigrana prima o dopo la sostituzione dell'immagine:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Problemi comuni e risoluzione

| Sintomo | Probabile causa | Correzione |
|---------|----------------|------------|
| Nessuna modifica dell'immagine dopo l'esecuzione del codice | `DiagramShape.hasImage()` restituito false | Verifica il tipo di forma; alcune forme vettoriali memorizzano le immagini in modo diverso. |
| OutOfMemoryError su file di grandi dimensioni | Caricamento dell'intero diagramma in una volta | Usa `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` per elaborare le pagine in sequenza. |
| Filigrana non visibile | Filigrana posizionata dietro il contenuto esistente | Chiama `watermarker.setWatermarkPosition(Position.Foreground)` prima di salvare. |

## Domande frequenti

**Q: Posso sostituire le immagini nei diagrammi protetti da password?**  
A: Sì. Passa la password a `DiagramLoadOptions` quando crei il `Watermarker`.

**Q: La libreria funziona con file .drawio (XML)?**  
A: Assolutamente – GroupDocs.Watermark supporta il formato XML di Draw.io e tratta ogni nodo come una forma.

**Q: Quanti diagrammi posso elaborare in parallelo?**  
A: La libreria è thread‑safe per operazioni di sola lettura; per operazioni di scrittura, limita la concorrenza al numero di core CPU per evitare conflitti di handle dei file.

**Q: Esiste un limite alle dimensioni dell'immagine?**  
A: Sono supportate immagini fino a 100 MB; i file più grandi dovrebbero essere ridimensionati in anticipo per mantenere basso l'uso della memoria.

**Q: Quali opzioni di licenza sono disponibili?**  
A: Puoi iniziare con una prova gratuita di 30 giorni; l'uso in produzione richiede una licenza a pagamento, che può essere ottenuta dallo store di GroupDocs.

---

**Ultimo aggiornamento:** 2026-08-19  
**Testato con:** GroupDocs.Watermark 23.9 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Tutorial di filigrana dei diagrammi per GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Rimuovere i collegamenti ipertestuali dalle forme del diagramma usando GroupDocs.Watermark Java per una maggiore sicurezza dei documenti](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Come aggiungere una filigrana immagine in Java usando GroupDocs.Watermark: Guida passo‑passo](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)