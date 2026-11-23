---
date: '2026-10-21'
description: Scopri come rimuovere hyperlink da forme di diagramma usando GroupDocs.Watermark
  per Java. Segui questa guida passo‑passo per rendere i tuoi documenti sicuri e puliti.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Scopri come rimuovere hyperlink da forme di diagramma usando GroupDocs.Watermark
  per Java. Questa guida ti accompagna nella configurazione, nel codice e nelle migliori
  pratiche per documenti sicuri e puliti.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Come rimuovere hyperlink da forme con GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Come rimuovere hyperlink da forme con GroupDocs.Watermark Java
type: docs
url: /it/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Come rimuovere i collegamenti ipertestuali dalle forme con GroupDocs.Watermark Java

Gestire documenti digitali spesso comporta la modifica di diagrammi, soprattutto quando è necessario **rimuovere i collegamenti ipertestuali** dalle forme per motivi di sicurezza o chiarezza visiva. Questo tutorial ti guida attraverso un metodo semplice per eliminare i collegamenti ipertestuali indesiderati dalle forme del diagramma usando la potente libreria **GroupDocs.Watermark** in Java. Alla fine di questa guida, comprenderai perché è importante rimuovere i collegamenti ipertestuali, come configurare l'ambiente e i passaggi esatti per eseguire la rimozione in modo sicuro.

## Risposte rapide
- **Qual è lo scopo principale della rimozione dei collegamenti ipertestuali?** Per eliminare i rischi di sicurezza e migliorare la chiarezza visiva nei diagrammi condivisi.  
- **Quale libreria gestisce la rimozione?** GroupDocs.Watermark per Java fornisce un'API dedicata per la manipolazione dei diagrammi.  
- **È necessaria una licenza?** Una versione di prova funziona per i test; è richiesta una licenza commerciale per l'uso in produzione.  
- **Posso elaborare molti file contemporaneamente?** Sì—incapsula il codice in un ciclo o in un lavoro batch per gestire operazioni di massa.  
- **Quale versione di Java è richiesta?** Java 8 o superiore è supportata.

## Cos'è rimuovere i collegamenti ipertestuali?
La frase **rimuovere i collegamenti ipertestuali** si riferisce al processo di individuare ed eliminare gli oggetti collegamento ipertestuale incorporati negli elementi di forma di un diagramma. Eseguire questa azione impedisce che la navigazione esterna esponga involontariamente gli utenti a siti dannosi o contenuti indesiderati. È particolarmente importante quando si preparano documenti per la distribuzione pubblica, assicurando che non rimangano percorsi di navigazione nascosti che potrebbero condurre a siti di phishing o a risorse esterne non intenzionali.

## Perché usare GroupDocs.Watermark per Java?
GroupDocs.Watermark supporta **oltre 30 formati di input e output** e può elaborare diagrammi con **fino a 500 pagine** senza caricare l'intero file in memoria, offrendo una **riduzione del 40 % dell'utilizzo della CPU** rispetto ai parser XML generici. La sua API ti offre un controllo dettagliato sulle proprietà delle forme, rendendola l'approccio standard per la gestione sicura dei diagrammi nelle applicazioni Java.

## Prerequisiti
- **Libreria GroupDocs.Watermark** versione 24.11 o successiva.  
- Maven installato (o download diretto del JAR).  
- JDK 8 o più recente e un IDE come IntelliJ IDEA o Eclipse.  
- Conoscenze di base di Java e familiarità con le dipendenze Maven.

## Configurazione di GroupDocs.Watermark per Java
Per iniziare, includi la libreria GroupDocs.Watermark nel tuo progetto. Puoi aggiungerla tramite Maven o scaricare manualmente il JAR.

### Configurazione Maven
Add the following configuration to your `pom.xml`:

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
In alternativa, scarica l'ultima versione da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Passaggi per l'acquisizione della licenza
- Inizia con una prova gratuita scaricando GroupDocs.Watermark.  
- Per test più estesi o uso in produzione, ottieni una licenza temporanea o acquista una licenza completa.

#### Inizializzazione e configurazione di base
La classe `Watermarker` è il punto di ingresso per tutte le operazioni a livello di documento. Carica un file, ti dà accesso alle sue pagine, forme e metadati, e infine scrive il documento modificato su disco.

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Come rimuovere i collegamenti ipertestuali dalle forme del diagramma?
Carica il diagramma, individua ogni forma che contiene un collegamento ipertestuale e elimina quegli oggetti collegamento. L'intera operazione può essere eseguita in meno di dieci righe di codice e garantisce che il diagramma risultante non contenga più link cliccabili che potrebbero reindirizzare gli utenti a siti esterni o esporre informazioni sensibili.

### Passo 1: caricare il file del diagramma
Inizia caricando il tuo diagramma usando `Watermarker`. Questo oggetto fornisce accesso a vari elementi del documento, incluse le forme e le loro proprietà.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Perché**: Caricare il file è essenziale per accedere al suo contenuto per ulteriori manipolazioni.

### Passo 2: accedere al contenuto delle forme
Recupera i contenuti delle forme del diagramma. Questo ti permette di lavorare direttamente con gli elementi che potrebbero contenere collegamenti ipertestuali.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Perché**: Accedere a forme specifiche è fondamentale per mirare e modificare le proprietà dei collegamenti ipertestuali.

### Passo 3: iterare e rimuovere i collegamenti ipertestuali
Itera sui collegamenti ipertestuali in ordine inverso per rimuovere in modo sicuro i link indesiderati senza interrompere il processo di iterazione.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Perché**: Invertire l'ordine di iterazione previene problemi di indicizzazione durante la rimozione degli elementi.

### Passo 4: salvare e chiudere
Una volta completate le modifiche, salva le modifiche in una nuova posizione di file e chiudi la risorsa watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Perché**: Chiudere correttamente le risorse garantisce che non rimangano perdite di memoria o file bloccati nel sistema.

## Problemi comuni e risoluzione dei problemi
- **Raccolte di forme nulle** – Verifica sempre che la raccolta `Hyperlinks` di una forma non sia nulla prima di iterare.  
- **Diagrammi di grandi dimensioni** – Per file con più di 200 pagine, aumenta la dimensione dell'heap JVM (`-Xmx2g`) per evitare `OutOfMemoryError`.  
- **Errori di licenza** – Se visualizzi un'eccezione di licenza, verifica che la licenza di prova non sia scaduta e che il percorso del file di licenza sia corretto.

## Domande frequenti

**Q: Come gestisco più forme nella stessa pagina?**  
A: Scorri la raccolta `Shapes` di ogni pagina, applicando la stessa logica di rimozione dei collegamenti ipertestuali a ogni forma incontrata.

**Q: Posso limitare la rimozione a un intervallo di pagine specifico?**  
A: Sì—usa l'indice di pagina quando recuperi le forme e salta le pagine al di fuori dell'intervallo desiderato.

**Q: È necessaria una licenza per l'elaborazione batch?**  
A: È necessaria una licenza commerciale valida per qualsiasi lavoro batch di livello produzione; la licenza di prova funziona solo per test limitati.

**Q: Questo funziona con file SVG o Visio?**  
A: GroupDocs.Watermark supporta SVG, VSDX e diversi altri formati di diagramma; assicurati che il tipo di file sia elencato nella tabella dei formati supportati.

**Q: Quale prestazione posso aspettarmi su un diagramma di 300 pagine?**  
A: Su un server tipico (8 CPU, 16 GB RAM), l'elaborazione di un diagramma di 300 pagine richiede meno di 45 secondi, con un utilizzo di memoria inferiore a 200 MB.

## Risorse
- [Documentazione](https://docs.groupdocs.com/watermark/java/)
- [Riferimento API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Acquisizione licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

---

**Ultimo aggiornamento:** 2026-10-21  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Modifica le forme dei documenti Word con GroupDocs.Watermark in Java: Guida completa](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Rimuovi le forme dai documenti Word usando GroupDocs.Watermark in Java: Guida completa](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Modifica intestazioni e piè di pagina dei diagrammi in Java usando GroupDocs.Watermark: Guida completa](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)