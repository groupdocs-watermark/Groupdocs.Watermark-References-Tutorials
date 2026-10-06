---
date: '2026-02-13'
description: Scopri come estrarre forme e ottenere l'immagine da una forma con GroupDocs.Watermark
  per Java, recuperando in modo efficiente informazioni dettagliate sul diagramma.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Come estrarre forme da diagrammi usando GroupDocs.Watermark in Java
type: docs
url: /it/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Come estrarre forme da diagrammi usando GroupDocs.Watermark in Java

Quando hai bisogno di **come estrarre forme** da un diagramma in stile Visio in modo programmatico, la libreria GroupDocs.Watermark ti offre un modo pulito, orientato a Java, per recuperare ogni dettaglio — dimensioni, posizioni, immagini incorporate e persino il testo all'interno di ogni forma. In questo tutorial vedrai esattamente **come estrarre forme**, perché è importante e il codice passo‑passo che puoi copiare nel tuo progetto.

## Risposte rapide
- **Quale libreria gestisce l'estrazione delle forme?** GroupDocs.Watermark for Java  
- **Quale versione di Java è richiesta?** JDK 8 o superiore  
- **Posso ottenere i dati immagine da una forma?** Sì – usa `shape.getImage()`  
- **Il testo all'interno di una forma è accessibile?** Assolutamente, tramite `shape.getText()`  
- **È necessaria una licenza per la produzione?** È richiesta una licenza valida di GroupDocs.Watermark  

## Introduzione

Gestire diagrammi complessi spesso richiede l'accesso a informazioni dettagliate sui loro componenti, come forme e immagini. Se hai mai dovuto recuperare programmaticamente dati come dimensioni, posizioni o testo associato alle forme di un diagramma usando Java, questo tutorial è per te. Sfruttare la potenza della libreria GroupDocs.Watermark può semplificare questo processo in un'applicazione Java. In questa guida, percorreremo **come estrarre forme** da un file diagramma e ti mostreremo anche come **estrarre immagine da forma** e **estrarre testo da forma**.

## Cos'è “come estrarre forme”?

Estrarre forme significa leggere gli oggetti interni del diagramma (pagine, forme, immagini, testo) così da poterli analizzare, trasformare o riutilizzare in altre applicazioni — perfetto per automazione, reporting o integrazione con strumenti CAD.

## Perché usare GroupDocs.Watermark per l'estrazione delle forme?

- **Supporto completo dei formati** – funziona con VSDX, VDX e molti altri tipi di diagrammi.  
- **Modello di oggetti ricco** – fornisce accesso diretto alla geometria delle forme, alle immagini e al testo.  
- **Nessuna dipendenza esterna** – puro Java, facile da integrare nei progetti Maven.  

## Prerequisiti

- **GroupDocs.Watermark for Java** (versione 24.11 o successiva)  
- Java Development Kit (JDK) 8 o superiore  
- Maven per la gestione delle dipendenze  
- Un IDE come IntelliJ IDEA o Eclipse  

## Configurazione di GroupDocs.Watermark per Java

Aggiungi la libreria al tuo `pom.xml` Maven:

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

Puoi anche scaricare gli ultimi binari da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Passaggi per l'acquisizione della licenza
- **Prova gratuita:** Scarica un pacchetto di prova per valutare l'API.  
- **Licenza temporanea:** Richiedi una chiave temporanea per test estesi.  
- **Acquisto:** Ottieni una licenza completa per l'uso in produzione.  

### Inizializzazione e configurazione di base

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Come estrarre forme – Guida all'implementazione

### Carica e recupera il contenuto

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Itera attraverso le forme

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Come estrarre immagine da forma

La chiamata `shape.getImage()` restituisce un oggetto contenente il bitmap grezzo, le sue dimensioni e l'array di byte. Usa le proprietà mostrates sopra per salvare l'immagine su disco o inserirla in un altro flusso di elaborazione.

### Come estrarre testo da forma

Il metodo `shape.getText()` restituisce il testo semplice all'interno della forma. Se la forma non contiene testo, il metodo restituisce `null`. Il ciclo di esempio stampa già il testo e puoi manipolarlo ulteriormente — ad esempio, creando un indice di tutte le etichette delle forme.

## Suggerimenti per la risoluzione dei problemi
- Verifica il percorso del file e i permessi di lettura.  
- Assicurati di utilizzare un formato di diagramma supportato (VSDX, VDX, ecc.).  
- Se una forma appare senza i dati previsti, controlla le note di rilascio della libreria per particolarità specifiche del formato.  

## Applicazioni pratiche

1. **Analisi del diagramma:** Audita automaticamente i diagrammi per la conformità controllando le dimensioni delle forme o le etichette mancanti.  
2. **Visualizzazione dei dati:** Inserisci le dimensioni estratte in una dashboard di reporting per visualizzare la densità del layout.  
3. **Integrazione CAD:** Combina i dati delle forme con le API CAD per sincronizzare le specifiche di progetto tra gli strumenti.  

## Considerazioni sulle prestazioni

- **Chiudi le risorse:** Chiama `watermarker.close()` quando hai finito per liberare le risorse native.  
- **Gestione della memoria:** I diagrammi grandi possono consumare molta heap; monitora la memoria e aumenta `-Xmx` se necessario.  
- **Elaborazione batch:** Elabora i file in batch e riutilizza una singola istanza di `Watermarker` quando possibile.  

## Conclusione

Seguendo questa guida ora sai **come estrarre forme**, come **estrarre immagine da forma**, e come **estrarre testo da forma** usando GroupDocs.Watermark per Java. Queste tecniche aprono la porta all'analisi automatizzata dei diagrammi, al reporting e all'integrazione con altri sistemi ingegneristici. Come passo successivo, esplora l'API completa consultando la sua [documentazione](https://docs.groupdocs.com/watermark/java/) e prova a combinare l'estrazione delle forme con logica di business personalizzata.

## Sezione FAQ

1. **Cos'è GroupDocs.Watermark?**  
   - Una libreria Java completa progettata per l'applicazione di watermark e l'estrazione di informazioni da vari formati di documenti, inclusi i diagrammi.  

2. **Posso usare questa libreria per elaborare tutti i tipi di file diagramma?**  
   - Sì, ma assicurati che il formato del file sia supportato controllando il [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Come estraggo le dimensioni e le posizioni delle forme da un diagramma usando Java e GroupDocs.Watermark?**  
   - Carica il diagramma, accedi a `DiagramContent`, quindi itera le forme per ottenere proprietà come larghezza, altezza, X e Y.  

4. **GroupDocs.Watermark può estrarre le immagini incorporate nelle forme del diagramma con Java?**  
   - Sì, fornisce metodi per accedere ai dati immagine all'interno delle forme, incluse dimensioni e dati dei pixel, utili per analisi o modifiche.  

5. **Quali sono i prerequisiti per estrarre le informazioni delle forme del diagramma in Java?**  
   - Java JDK 8+, configurazione Maven, libreria GroupDocs.Watermark (24.11+), e conoscenze di base di Java sono essenziali per l'implementazione.  

---

**Ultimo aggiornamento:** 2026-02-13  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs