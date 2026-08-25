---
date: '2026-08-25'
description: Impara a modificare i file di diagrammi e a rimuovere i collegamenti
  ipertestuali usando GroupDocs.Watermark for Java. Proteggi rapidamente i tuoi diagrammi
  con una guida passo‑passo.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Scopri come modificare i file di diagrammi e rimuovere i collegamenti
  ipertestuali usando GroupDocs.Watermark for Java. Segui passaggi chiari per proteggere
  i tuoi documenti.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Come modificare diagrammi e rimuovere i collegamenti ipertestuali con Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Come modificare diagrammi e rimuovere i collegamenti ipertestuali con Java
type: docs
url: /it/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Come modificare diagrammi e rimuovere i collegamenti ipertestuali con Java  

Gestire i documenti digitali spesso comporta la modifica dei diagrammi, soprattutto quando è necessario **edit diagram** file per rimuovere i collegamenti ipertestuali per motivi di sicurezza o chiarezza visiva. Questo tutorial mostra esattamente come modificare i file diagram e rimuovere i collegamenti ipertestuali indesiderati dalle forme del diagramma utilizzando la potente libreria **GroupDocs.Watermark** per Java. Alla fine di questa guida avrai un diagramma pulito, privo di collegamenti, pronto per la distribuzione.  

## Risposte rapide  
- **Qual è l'obiettivo principale?** Rimuovere tutti i collegamenti ipertestuali dalle forme del diagramma per migliorare sicurezza e presentazione.  
- **Quale libreria è necessaria?** GroupDocs.Watermark per Java, versione 24.11 o successiva.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per i test; è richiesta una licenza commerciale per la produzione.  
- **Posso elaborare molti file contemporaneamente?** Sì – lo stesso codice può essere inserito in un ciclo per gestire i batch.  
- **Quale versione di Java è supportata?** Java 8 o superiore (Java 11 consigliato).  

## Cos'è “how to edit diagram”?  
**How to edit diagram** si riferisce al processo di apertura programmatica di un file diagram, modifica dei suoi elementi interni (come forme, testo o collegamenti ipertestuali) e salvataggio del risultato. Utilizzando GroupDocs.Watermark è possibile modificare i file diagram senza necessità dello strumento di authoring originale.  

## Perché usare GroupDocs.Watermark per Java?  
GroupDocs.Watermark supporta **oltre 30 formati di diagrammi e immagini** (inclusi VSDX, SVG e WMF) e può elaborare file fino a **500 MB** senza caricare l'intero documento in memoria, offrendo una velocità di elaborazione **20 % più veloce** rispetto a molti concorrenti.  

## Prerequisiti  
- **GroupDocs.Watermark** versione 24.11 o successiva.  
- Maven installato (oppure i file JAR se preferisci una configurazione manuale).  
- Java Development Kit 8 o più recente e un IDE come IntelliJ IDEA o Eclipse.  

### Librerie richieste, versioni e dipendenze  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (se utilizzi l'approccio Maven)  

### Requisiti di configurazione dell'ambiente  
Assicurati che la directory `bin` del JDK sia nel tuo `PATH` e che il tuo IDE punti alla versione corretta del JDK.  

### Prerequisiti di conoscenza  
Dovresti sentirti a tuo agio con la sintassi di base di Java, la gestione delle dipendenze Maven e le operazioni di I/O sui file.  

## Come configurare GroupDocs.Watermark per Java?  
La classe `Watermarker` fornisce il punto di ingresso API per caricare e modificare i documenti. Per iniziare a usare GroupDocs.Watermark, aggiungi le sue coordinate Maven al `pom.xml` del tuo progetto. Questo scarica la libreria e le sue dipendenze, consentendoti di istanziare la classe Watermarker e lavorare con i file diagram direttamente dal codice Java. Puoi quindi configurare la licenza e impostare le opzioni di output prima di elaborare qualsiasi documento.  

Aggiungi la dipendenza GroupDocs.Watermark al tuo `pom.xml`.  

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

Se preferisci non usare Maven, scarica l'ultimo JAR dalla pagina ufficiale dei rilasci.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Passaggi per l'acquisizione della licenza  
- Inizia con una prova gratuita per valutare l'API.  
- Per la produzione, ottieni una licenza temporanea o permanente dal portale del fornitore.  

#### Inizializzazione e configurazione di base  

La classe `Watermarker` è il punto di ingresso per tutte le operazioni di elaborazione dei documenti.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Come modificare diagrammi e rimuovere i collegamenti ipertestuali con GroupDocs.Watermark?  
La classe `Watermarker` fornisce il punto di ingresso API per caricare e modificare i documenti. Prima, carica il file diagram in un'istanza di Watermarker. Quindi recupera la collezione di forme, identifica quelle contenenti oggetti hyperlink e itera su di esse in ordine inverso per eliminare in modo sicuro ogni collegamento senza influenzare l'indicizzazione della collezione. Questo garantisce che tutti gli URL incorporati vengano rimossi mantenendo l'integrità visiva del diagramma.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Perché questo passaggio è importante**: Caricare il file ti fornisce l'accesso programmatico a ogni forma e alle sue proprietà associate.  

## Come accedere al contenuto delle forme in un diagramma?  
L'oggetto `DiagramShape` rappresenta una singola forma all'interno di un diagramma, esponendo le sue proprietà e i metadati allegati. Dopo aver caricato il diagramma, chiama `getShapes()` sul Watermarker per ottenere un elenco di oggetti `DiagramShape`. Ogni forma può essere ispezionata per le collezioni di hyperlink, consentendo un targeting preciso dei collegamenti per rimozione o modifica. È inoltre possibile leggere il testo della forma, i colori e la geometria se sono necessari ulteriori aggiustamenti.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Perché questo passaggio è importante**: Targetizzare la forma esatta garantisce che vengano rimossi solo i collegamenti indesiderati senza influenzare altri elementi visivi.  

## Come iterare e rimuovere i collegamenti ipertestuali in modo sicuro?  
Il metodo `removeHyperlink(int index)` elimina un hyperlink nella posizione specificata all'interno della collezione di hyperlink di una forma. Itera sull'elenco di hyperlink dall'ultimo indice fino a zero. Questo ciclo inverso previene lo spostamento degli indici che si verifica quando gli elementi vengono rimossi, garantendo che ogni hyperlink sia elaborato senza essere saltato. Dopo la rimozione, puoi aggiornare lo stato della forma o passare alla forma successiva nel diagramma.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Perché questo passaggio è importante**: Un ciclo inverso garantisce che tutti i collegamenti ipertestuali vengano rimossi senza saltare alcuna voce.  

## Come salvare il diagramma modificato e rilasciare le risorse?  
Il metodo `save(String path)` scrive il documento modificato nella posizione di file specificata, finalizzando tutte le modifiche. Una volta rimossi tutti i collegamenti ipertestuali, invoca il metodo `save` sull'istanza Watermarker, fornendo un nuovo nome file per evitare di sovrascrivere l'originale. Quindi chiama `close()` per rilasciare i handle dei file e liberare la memoria, operazione essenziale per processi batch a lungo termine. Questo garantisce che il file sia correttamente chiuso e pronto per ulteriori utilizzi.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Perché questo passaggio è importante**: Chiudere correttamente le risorse evita perdite di memoria e problemi di blocco dei file sul server.  

## Applicazioni pratiche  

Rimuovere i collegamenti ipertestuali dalle forme dei diagrammi può essere vantaggioso in diversi scenari reali:  

1. **Sicurezza** – Impedire collegamenti esterni che potrebbero portare a siti dannosi.  
2. **Conformità** – Rispettare le politiche aziendali che vietano URL incorporati negli asset condivisi.  
3. **Chiarezza** – Produrre presentazioni più pulite dove i collegamenti sarebbero di distrazione.  

Puoi incorporare questa logica in pipeline di automazione più ampie, come job batch notturni che sanificano tutti i diagrammi prima della loro pubblicazione su un intranet.  

## Considerazioni sulle prestazioni  

### Ottimizzazione delle prestazioni  
- Usa una singola istanza `Watermarker` per file per ridurre l'overhead.  
- Preferisci l'iterazione inversa (come mostrato) per evitare costosi ri‑indicizzamenti della lista.  

### Linee guida sull'uso delle risorse  
- Per diagrammi più grandi di 200 MB, monitora l'uso dell'heap e considera di aumentare il flag JVM `-Xmx`.  
- Strumenti di profiling come VisualVM possono aiutare a identificare i colli di bottiglia in esecuzioni batch su larga scala.  

### Best practice per la gestione della memoria Java  
- Dichiarare gli oggetti all'interno del più piccolo ambito possibile.  
- Usa try‑with‑resources quando lavori con gli stream per garantire la chiusura automatica.  

## Domande frequenti  

**Q: Come gestisco i diagrammi che contengono migliaia di forme?**  
A: Elabora il diagramma pagina per pagina e rilascia le risorse di ogni pagina prima di passare alla successiva per mantenere basso l'uso della memoria.  

**Q: Posso limitare la rimozione dei collegamenti ipertestuali a pagine specifiche?**  
A: Sì – recupera l'indice della pagina desiderata, quindi applica il ciclo di rimozione solo alle forme di quella pagina.  

**Q: È obbligatoria una licenza commerciale per l'elaborazione batch?**  
A: È necessaria una licenza valida per qualsiasi distribuzione a livello di produzione; la prova gratuita è limitata a 30 giorni e 5 documenti.  

**Q: GroupDocs.Watermark supporta i diagrammi SVG?**  
A: Assolutamente – SVG è tra i più di 30 formati supportati, e i collegamenti ipertestuali possono essere rimossi usando le stesse chiamate API.  

**Q: Cosa succede se una forma ha più collegamenti ipertestuali?**  
A: Il ciclo di iterazione inversa rimuove ogni voce di collegamento ipertestuale individualmente, garantendo che tutti i link siano eliminati.  

## Risorse  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**Ultimo aggiornamento:** 2026-08-25  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs  

## Tutorial correlati

- [Tutorial di watermarking diagrammi per GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Modifica intestazioni e piè di pagina dei diagrammi in Java usando GroupDocs.Watermark: Guida completa](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Rimuovi forme dai diagrammi in modo efficiente usando GroupDocs.Watermark per Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)