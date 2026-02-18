---
date: '2026-02-18'
description: Scopri come sostituire le immagini dei diagrammi in Java usando GroupDocs.Watermark
  per Java—automatizza gli aggiornamenti, aumenta l'efficienza e garantisci la precisione
  nel tuo flusso di lavoro.
keywords:
- GroupDocs Watermark Java
- automate image replacement
- Java diagram watermarking
title: Come sostituire le immagini dei diagrammi Java con GroupDocs.Watermark
type: docs
url: /it/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# sostituire le immagini del diagramma java con GroupDocs.Watermark per Java

Aggiornare le immagini all'interno di diagrammi in stile Visio può essere un compito tedioso e soggetto a errori, soprattutto quando si hanno dozzine di file da mantenere allineati alle linee guida del brand o alle revisioni di prodotto. In questo tutorial imparerai **come sostituire le immagini del diagramma java** utilizzando la potente libreria GroupDocs.Watermark. Ti guideremo passo passo nella configurazione dell'ambiente, nell'accesso alle forme del diagramma, nella sostituzione delle immagini e nel salvataggio del risultato, il tutto con spiegazioni chiare e conversazionali.

## Risposte rapide
- **Quale libreria può sostituire le immagini dei diagrammi in Java?** GroupDocs.Watermark for Java.  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per lo sviluppo; è necessaria una licenza di produzione per l'uso commerciale.  
- **Quali formati di file sono supportati?** Visio (.vsdx, .vsd) e altri tipi di diagrammi supportati dalla libreria.  
- **Quanto tempo richiede l'implementazione?** Circa 15 minuti per uno script di base di sostituzione dell'immagine.  
- **Posso elaborare più diagrammi in batch?** Sì—basta iterare sui file con la stessa logica Watermarker.

## Cos'è “replace diagram images java”?
“replace diagram images java” si riferisce al processo di individuare programmaticamente le forme che contengono immagini all'interno di un file di diagramma e sostituire il bitmap incorporato con uno nuovo, il tutto dal codice Java. Questo elimina la necessità di modifiche manuali in Visio o strumenti simili e garantisce coerenza su grandi collezioni di documenti.

## Perché usare GroupDocs.Watermark per questo compito?
- **Automazione‑prima**: gestisce migliaia di file con poche righe di codice.  
- **Nessuna UI richiesta**: funziona in modalità head‑less su server, pipeline CI o applicazioni desktop.  
- **Modello di contenuto ricco**: fornisce astrazioni potenti (DiagramContent, DiagramShape) che consentono di mirare esattamente alle forme necessarie.  
- **Cross‑platform**: funziona su qualsiasi ambiente compatibile con JVM (Windows, Linux, macOS).  

## Prerequisiti
- JDK 8 o superiore installato.  
- Maven (o gestione manuale dei JAR) per la gestione delle dipendenze.  
- Conoscenza di base di Java e familiarità con I/O di file.  

### Librerie richieste, versioni e dipendenze
Aggiungi il repository GroupDocs e la dipendenza Watermark al tuo `pom.xml`:

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

Puoi anche scaricare l'ultimo JAR direttamente da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

Una licenza di prova gratuita è disponibile, e una licenza permanente può essere acquistata da [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Implementazione passo‑passo

### 1. Inizializzare il Watermarker
Per prima cosa, crea un'istanza `Watermarker` che punti al diagramma che desideri modificare.

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

*Perché è importante*: caricare il file con `DiagramLoadOptions` indica alla libreria di trattare la sorgente come un diagramma, abilitando l'accesso a livello di forma.

### 2. Accedere al contenuto del diagramma
Recupera la rappresentazione interna (`DiagramContent`) così da poter enumerare pagine e forme.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

*Consiglio professionale*: mantieni viva l'istanza `Watermarker` mentre lavori con `DiagramContent`; chiuderla troppo presto invaliderà l'oggetto contenuto.

### 3. Sostituire le immagini delle forme
Itera sulle forme della prima pagina (puoi estendere l'operazione a tutte le pagine) e sostituisci ogni immagine esistente con un nuovo PNG.

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

*Spiegazione*:  
- `shape.getImage()` verifica se la forma contiene già un'immagine.  
- Leggiamo il PNG di sostituzione in un array di byte e lo avvolgiamo in `DiagramWatermarkableImage`.  
- `shape.setImage(...)` scambia l'immagine vecchia con quella nuova.

### 4. Salvare le modifiche e pulire
Dopo tutte le sostituzioni, persisti il diagramma e rilascia le risorse.

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

Il salvataggio scrive il diagramma aggiornato su disco, e `close()` previene perdite di handle di file—critico per l'elaborazione in batch.

## Applicazioni pratiche
- **Branding aziendale** – Aggiorna i loghi su tutti gli organigrammi con un unico script.  
- **Documentazione prodotto** – Aggiorna le immagini dei componenti quando viene rilasciato nuovo hardware.  
- **Risorse educative** – Sostituisci diagrammi obsoleti con le ultime illustrazioni scientifiche.

## Prestazioni e migliori pratiche
- **Elabora un file alla volta** quando si gestiscono diagrammi grandi per mantenere basso l'uso di memoria.  
- **Rilascia gli stream prontamente** (come mostrato) per evitare problemi di blocco dei file.  
- **Profilare I/O** se si gestiscono centinaia di file; considerare un thread‑pool con concorrenza controllata.

## Problemi comuni e soluzioni

| Sintomo | Causa probabile | Risoluzione |
|---------|-----------------|-------------|
| `NullPointerException` on `shape.getImage()` | Indice della pagina del diagramma fuori intervallo | Assicurarsi che la pagina esista (`content.getPages().size() > 0`) prima di iterare. |
| L'immagine appare distorta dopo la sostituzione | L'immagine di input ha DPI diverso | Usare un PNG con dimensioni/DPI simili all'originale, o ridimensionare prima del caricamento. |
| LicenseException at runtime | Trial scaduto o licenza mancante | Applicare un file di licenza valido tramite `License.setLicense("path/to/license.json");` prima di creare `Watermarker`. |

## Domande frequenti

**D: Posso sostituire le immagini in tutte le pagine di un diagramma?**  
R: Sì—itera su `content.getPages()` e applica la stessa logica di sostituzione a ciascuna pagina.

**D: La libreria supporta altri formati immagine (ad es., JPEG, BMP)?**  
R: Assolutamente. Fornisci i byte dell'immagine in qualsiasi formato supportato; l'API gestirà la conversione.

**D: È possibile sostituire solo forme specifiche (ad es., quelle con un certo nome)?**  
R: Sì. Ogni `DiagramShape` dispone di proprietà come `getName()` o metadati personalizzati su cui puoi filtrare prima di scambiare l'immagine.

**D: Come eseguo questo codice su un server Linux senza GUI?**  
R: GroupDocs.Watermark è completamente head‑less; non sono richiesti componenti GUI. Basta assicurarsi che il JDK e i JAR necessari siano nel classpath.

**D: Quale versione di GroupDocs.Watermark è necessaria?**  
R: L'esempio utilizza la versione 24.11, l'ultima release stabile al momento della stesura.

## Conclusione
Ora disponi di un flusso di lavoro completo e pronto per la produzione per **replace diagram images java** usando GroupDocs.Watermark. Integra questi snippet nel tuo pipeline di build, elabora in batch le cartelle di diagrammi o espone la logica tramite un servizio REST per automatizzare gli aggiornamenti di branding in tutta l'organizzazione.

---

**Ultimo aggiornamento:** 2026-02-18  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs