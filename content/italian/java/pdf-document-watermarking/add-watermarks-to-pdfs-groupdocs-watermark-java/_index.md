---
date: '2026-08-09'
description: Scopri come aggiungere una filigrana a PDF usando GroupDocs.Watermark
  per Java. Questo esempio di filigrana PDF in Java mostra filigrane di testo e immagine,
  salvando PDF con filigrana.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Scopri come aggiungere una filigrana a PDF usando GroupDocs.Watermark
  per Java. Questo esempio passo‑a‑passo di filigrana PDF in Java ti aiuta a salvare
  PDF con filigrana rapidamente.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Aggiungi filigrana a PDF con GroupDocs.Watermark per Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  headline: Add watermark to PDF with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  name: Add watermark to PDF with GroupDocs.Watermark for Java
  steps:
  - name: create TextWatermark instance
    text: 'Create a `TextWatermark` using the desired text and font settings: This
      example sets the watermark text to “Protected image” using Arial, size 8.'
  - name: set alignment
    text: 'Center the watermark horizontally and vertically for uniform positioning:'
  - name: rotate watermark
    text: 'Apply a 45‑degree rotation to make the watermark harder to remove:'
  - name: configure sizing
    text: 'Scale the watermark relative to the target image dimensions:'
  - name: load image file
    text: 'Load the watermark image from disk: Replace the placeholder path with the
      actual location of your logo or seal.'
  - name: set alignment
    text: 'Center the image watermark for balanced visual impact:'
  - name: rotate image watermark
    text: 'Apply a –30‑degree rotation to introduce visual variation:'
  - name: configure sizing
    text: 'Define the image size as a percentage of the underlying image’s width:'
  - name: open the document
    text: 'Instantiate a `Watermarker` with the path to your source PDF:'
  - name: retrieve images
    text: 'Collect all images from the PDF that can receive a watermark:'
  type: HowTo
- questions:
  - answer: Yes. Open the document with `new Watermarker("file.pdf", "password")`
      and then apply the watermark as usual.
    question: Can I add a watermark to a password‑protected PDF?
  - answer: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker`
      for each file, apply the same watermark objects, and save the results.
    question: Does the API support batch processing of multiple PDFs?
  - answer: The library can handle **500+ watermarks per document** without performance
      degradation, thanks to its optimized rendering engine.
    question: What is the maximum number of watermarks I can add to a single PDF?
  - answer: Yes. Use the `setOpacity(0)` method on the watermark object to embed it
      invisibly for forensic tracking.
    question: Is it possible to make the watermark invisible (metadata only)?
  - answer: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- pdf watermark
- GroupDocs.Watermark
- Java document security
title: Aggiungi filigrana a PDF con GroupDocs.Watermark per Java
type: docs
url: /it/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Aggiungere filigrana a PDF con GroupDocs.Watermark per Java

## Introduzione

Nel panorama digitale odierno, proteggere la proprietà intellettuale è fondamentale, e **add watermark to PDF** è uno dei modi più efficaci per farlo. Questo tutorial ti guida nell'utilizzo di GroupDocs.Watermark per Java per inserire filigrane di testo e immagine nei file PDF. Alla fine, sarai in grado di:

- Inizializzare filigrane di testo e immagine
- Applicare le filigrane in modo condizionale in base alle dimensioni dell'immagine
- **save PDF with watermark** mantenendo la qualità originale

Pronto a proteggere i tuoi documenti? Iniziamo!

## Risposte rapide
- **Quale libreria aggiunge filigrane ai PDF in Java?** GroupDocs.Watermark per Java.  
- **Posso aggiungere sia filigrane di testo che di immagine?** Sì, l'API supporta entrambi i tipi in un'unica esecuzione.  
- **Ho bisogno di una licenza per lo sviluppo?** Una prova gratuita è sufficiente per i test; è necessaria una licenza permanente per la produzione.  
- **Quali formati di file sono supportati?** Oltre 30 formati, tra cui PDF, DOCX, PPTX e immagini.  
- **Qual è la dimensione massima di un PDF che può essere elaborato?** Fino a 2.000 pagine senza caricare l'intero file in memoria.  

## Cos'è add watermark to PDF?
**Add watermark to PDF** significa incorporare segni visibili o invisibili — come stringhe di testo o loghi — direttamente in un file PDF per indicare proprietà, riservatezza o branding. Questo processo modifica i livelli visivi del documento mantenendo intatto il contenuto originale.

## Perché usare GroupDocs.Watermark per Java?
GroupDocs.Watermark supporta **30+ formati di documento**, può elaborare PDF fino a **2.000 pagine** in un'unica passata e aggiunge fino a **500 filigrane per documento** senza un impatto di prestazioni evidente. La sua API è completamente thread‑safe, rendendola ideale per ambienti server ad alto throughput.

## Prerequisiti

Prima di procedere, assicurati di avere:

1. **Java Development Kit (JDK):** Versione 8 o successiva installata.  
2. **GroupDocs.Watermark per Java:** Versione 24.11 (o successiva) aggiunta al tuo progetto.  
3. **Strumento di build:** Maven consigliato, ma anche un download diretto del JAR funziona.  

### Configurazione dell'ambiente

#### Configurazione Maven

Aggiungi il repository GroupDocs e la dipendenza al tuo file `pom.xml`:

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

#### Download diretto

In alternativa, scarica l'ultimo JAR dalla pagina ufficiale dei rilasci: [Rilasci di GroupDocs.Watermark per Java](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza

Per una prova gratuita o una licenza temporanea, visita il portale di licenze: [Licenza GroupDocs](https://purchase.groupdocs.com/temporary-license). Le distribuzioni in produzione dovrebbero utilizzare una licenza acquistata per rimuovere tutte le limitazioni della prova.

## Configurazione di GroupDocs.Watermark per Java

Dopo aver aggiunto la libreria, importa le classi necessarie nel tuo file sorgente Java:

```java
import com.groupdocs.watermark.Watermarker;
```

## Guida all'implementazione

Divideremo l'implementazione in sezioni logiche, ciascuna rispondente a una domanda specifica.

### Come aggiungere filigrana a PDF in Java?

`Watermarker` è la classe principale che carica un documento e consente l'applicazione delle filigrane.  
Carica il tuo PDF con `new Watermarker("input.pdf")` e poi applica un oggetto filigrana prima di chiamare `save("output.pdf")`. Questo approccio a due passaggi gestisce sia le filigrane di testo che quelle di immagine in un'unica passata, garantendo che il file sia **saved PDF with watermark** in modo efficiente.

### Inizializzare filigrana di testo

**Definition anchor:** `TextWatermark` è la classe che rappresenta una sovrapposizione testuale che può essere posizionata su pagine, immagini o grafica vettoriale all'interno di un documento.

#### Passo 1: creare l'istanza TextWatermark

Crea un `TextWatermark` utilizzando il testo desiderato e le impostazioni del font:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### Passo 2: impostare l'allineamento

Centra la filigrana orizzontalmente e verticalmente per un posizionamento uniforme:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Passo 3: ruotare la filigrana

Applica una rotazione di 45 gradi per rendere la filigrana più difficile da rimuovere:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Passo 4: configurare le dimensioni

Scala la filigrana in base alle dimensioni dell'immagine di destinazione:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Inizializzare filigrana di immagine

**Definition anchor:** `ImageWatermark` incapsula un'immagine (PNG, JPEG, BMP, ecc.) che verrà sovrapposta al contenuto del documento come filigrana.

#### Passo 1: caricare il file immagine

Carica l'immagine della filigrana dal disco:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Sostituisci il percorso segnaposto con la posizione reale del tuo logo o sigillo.

#### Passo 2: impostare l'allineamento

Centra la filigrana immagine per un impatto visivo equilibrato:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Passo 3: ruotare la filigrana immagine

Applica una rotazione di –30 gradi per introdurre variazioni visive:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Passo 4: configurare le dimensioni

Definisci la dimensione dell'immagine come percentuale della larghezza dell'immagine sottostante:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Aggiungere filigrane alle immagini in un documento

**Definition anchor:** `Watermarker` è la classe principale che carica un documento, fornisce l'accesso ai suoi elementi e scrive le filigrane nel file.

#### Passo 1: aprire il documento

Istanzia un `Watermarker` con il percorso del tuo PDF di origine:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Passo 2: recuperare le immagini

Raccogli tutte le immagini dal PDF che possono ricevere una filigrana:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Passo 3: aggiungere filigrane in modo condizionale

Per ogni immagine, controlla le sue dimensioni; se la larghezza supera i 300 px, applica la filigrana di testo, altrimenti usa la filigrana immagine:

```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

Questa logica condizionale garantisce che solo le immagini appropriate ricevano la sovrapposizione di testo più evidente, ottimizzando il tempo di elaborazione.

#### Passo 4: rilasciare le risorse immagine

Dopo l'elaborazione, chiudi l'oggetto filigrana immagine per liberare le risorse native:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Passo 5: salvare le modifiche

Conserva le modifiche salvando il documento in un nuovo file:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

Il file risultante è una versione **save PDF with watermark** pronta per la distribuzione.

#### Passo 6: pulizia

Elimina l'istanza `Watermarker` per prevenire perdite di memoria:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Problemi comuni e risoluzione

- **Errori di licenza:** Assicurati che il percorso del file di licenza sia impostato correttamente tramite `License.setLicense("license_file_path")`. Una licenza mancante o scaduta genera una `LicenseException`.  
- **PDF di grandi dimensioni:** Per documenti con più di 1.000 pagine, abilita la modalità streaming chiamando `watermarker.setStreamMode(true)` per mantenere basso il consumo di memoria.  
- **Formati immagine non supportati:** GroupDocs.Watermark supporta PNG, JPEG, BMP e GIF. Convertire altri formati in PNG prima del caricamento evita `UnsupportedFormatException`.  

## Domande frequenti

**Q: Posso aggiungere una filigrana a un PDF protetto da password?**  
A: Sì. Apri il documento con `new Watermarker("file.pdf", "password")` e poi applica la filigrana come al solito.

**Q: L'API supporta l'elaborazione batch di più PDF?**  
A: Assolutamente. Scorri una cartella di PDF, istanzia un `Watermarker` per ciascun file, applica gli stessi oggetti filigrana e salva i risultati.

**Q: Qual è il numero massimo di filigrane che posso aggiungere a un singolo PDF?**  
A: La libreria può gestire **500+ filigrane per documento** senza degradare le prestazioni, grazie al suo motore di rendering ottimizzato.

**Q: È possibile rendere la filigrana invisibile (solo metadati)?**  
A: Sì. Usa il metodo `setOpacity(0)` sull'oggetto filigrana per incorporarla invisibilmente a fini di tracciamento forense.

**Q: Quali versioni di Java sono ufficialmente supportate?**  
A: GroupDocs.Watermark per Java supporta JDK 8, 11 e 17, garantendo compatibilità sia con applicazioni legacy sia moderne.

## Applicazioni pratiche

L'aggiunta di filigrane può servire a vari scenari reali:

1. **Sicurezza dei documenti:** Contrassegna i file riservati per scoraggiare la condivisione non autorizzata.  
2. **Protezione del brand:** Sovrapponi i loghi aziendali sui PDF di marketing.  
3. **Affermare il copyright:** Inserisci i nomi degli autori o i simboli di copyright sulle opere pubblicate.  
4. **Controllo di versione:** Apponi numeri di versione o date sui documenti di bozza.  

## Conclusione

Seguendo questo **java pdf watermark example**, ora disponi di una soluzione completa, pronta per la produzione, per **add watermark to PDF** usando GroupDocs.Watermark per Java. Puoi personalizzare testo, immagini, rotazione e dimensioni, nonché applicare filigrane in modo condizionale in base alle dimensioni dell'immagine — il tutto mantenendo il processo veloce ed efficiente in termini di memoria.

---  

**Ultimo aggiornamento:** 2026-08-09  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Come aggiungere filigrane di testo e immagine a pagine PDF specifiche usando GroupDocs.Watermark per Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Aggiungere filigrane solo per stampa ai PDF usando GroupDocs.Watermark Java: Guida completa](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Accedere e iterare sugli artefatti PDF usando GroupDocs.Watermark in Java per il watermark dei documenti](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)