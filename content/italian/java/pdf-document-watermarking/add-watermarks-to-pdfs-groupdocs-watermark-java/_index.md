---
date: '2026-01-23'
description: Scopri come aggiungere filigrane testuali e immagine ai file PDF usando
  GroupDocs.Watermark per Java – una guida completa per la sicurezza dei documenti
  PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Come aggiungere una filigrana a PDF usando GroupDocs.Watermark per Java
type: docs
url: /it/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Come aggiungere filigrane a PDF usando GroupDocs.Watermark per Java

Nel mondo digitale di oggi, **come aggiungere filigrane a PDF** è una domanda comune per chiunque abbia bisogno di proteggere la proprietà intellettuale o i beni del marchio. Aggiungere filigrane — sia di testo che di immagini — ti aiuta a rafforzare la **sicurezza dei documenti PDF** e rende molto più difficile la distribuzione non autorizzata. In questo tutorial, imparerai passo‑passo come utilizzare **GroupDocs.Watermark for Java** per aggiungere sia filigrane di testo che di immagine ai documenti PDF.

## Risposte rapide
- **Quale libreria aggiunge filigrane a PDF in Java?** GroupDocs.Watermark for Java.  
- **Posso aggiungere sia filigrane di testo che di immagine?** Yes, the API supports both types.  
- **Ho bisogno di una licenza?** A free trial works for evaluation; a paid license removes limitations.  
- **Quale versione di Java è richiesta?** JDK 8 or higher.  
- **Maven è supportato?** Absolutely – just add the repository and dependency.

## Cos'è la filigrana PDF e perché usarla?
Applicare una filigrana a un PDF inserisce un marcatore visibile o invisibile che identifica la proprietà, la riservatezza o il branding. È un metodo leggero ma potente per scoraggiare la copia, dimostrare la paternità e rispettare le politiche aziendali.

## Prerequisiti

Prima di iniziare, assicurati di avere:

1. **Java Development Kit (JDK) 8+** installato sulla tua macchina.  
2. **GroupDocs.Watermark for Java** (l'ultima versione).  
3. **Maven** (o la possibilità di aggiungere un JAR manualmente).

### Configurazione dell'ambiente

#### Configurazione Maven
Aggiungi il repository GroupDocs e la dipendenza watermark al tuo `pom.xml`:

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
Se preferisci non usare Maven, puoi scaricare il JAR direttamente da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza
Per iniziare con una prova gratuita o ottenere una licenza temporanea, visita [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Per l'uso in produzione, acquista un abbonamento per sbloccare tutte le funzionalità.

## Configurazione di GroupDocs.Watermark per Java

Importa la classe principale che gestisce tutte le operazioni di filigrana:

```java
import com.groupdocs.watermark.Watermarker;
```

Questa importazione ti dà accesso alla classe `Watermarker`, che è il punto di ingresso per aggiungere filigrane a qualsiasi tipo di documento supportato.

## Implementazione passo‑passo

Di seguito suddividiamo il processo in sezioni logiche: creazione di filigrane di testo, creazione di filigrane di immagine e, infine, applicarle alle immagini all'interno di un PDF.

### 1. Inizializzare una filigrana di testo

**Perché una filigrana di testo?** È leggera, ricercabile e perfetta per aggiungere avvisi di copyright o dichiarazioni di riservatezza.

#### 1.1 Crea l'istanza TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Imposta l'allineamento
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Ruota la filigrana
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Configura le dimensioni
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Inizializzare una filigrana di immagine

**Quando usare una filigrana di immagine?** Ideale per il branding con loghi o per aggiungere pattern visivi complessi.

#### 2.1 Carica il file immagine
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Imposta l'allineamento
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Ruota la filigrana immagine
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Configura le dimensioni
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Aggiungere filigrane alle immagini all'interno di un PDF

Ora metteremo tutto insieme: aprire un PDF, individuare ogni immagine e applicare la filigrana di testo o di immagine in base alle dimensioni.

#### 3.1 Apri il documento PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Recupera tutte le immagini
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Applica le filigrane in modo condizionale
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

#### 3.4 Rilascia le risorse immagine
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Salva il PDF modificato
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Pulizia
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Applicazioni pratiche della filigrana PDF

| Caso d'uso | Come aiuta la filigrana |
|------------|--------------------------|
| **Sicurezza dei documenti** | Contrassegna i file riservati, scoraggiando le perdite Inserisce loghi nei PDF di marketing, rafforzando l'identità del marchio. |
| **Affermazione del copyright** | Aggiunge il di versione o date direttamente sullaire errori OutOfMemory.
- **Limiti della licenza:** La versione di prova può limitare il numero di pagine elaborate; effettua l'upgrade per utilizzo illimitato.
- **Confusione sulla rotazione:** Ricorda che `setenti

**D: Posso aggiungere filigrane a PDF protetti da password?**  
 documento con la password usando il costruttore `Watermarker` che accetta una stringa password.

**D: La libreria supporta altri formati come DOCX o PPTX?**  
R: Assolutamente. GroupDocs.Watermark funziona anche con Word, PowerPoint, Excel e file immagine.

**D: Come modifico l'opacità di una filigrana?**  
R: Usa `setOpacity(float opacity)` sull'oggetto filigrana (valore compreso tra 0.0 e 1 bucket cloud?**  
R: Carica il PDF in un `InputStream` e passalo al costruttore `Watermarker`; dopo l'elaborovamente nel cloud.

## Conclusione

Ora hai a disposizione un metodobinando filigrane di testo e di immagine, puoi ottenere una **sicurezza dei documenti PDF** robusta che soddisfa sia le esigenze di branding sia i requisiti di conformità. Esplora le altre funzionalità della libreria — come la rimozione delle filigrane o l'elaborazione batch — per estendere ulteriormente il tuo flusso di lavoro documentale.

---

**Ultimo aggiornamento:** 2026 con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs