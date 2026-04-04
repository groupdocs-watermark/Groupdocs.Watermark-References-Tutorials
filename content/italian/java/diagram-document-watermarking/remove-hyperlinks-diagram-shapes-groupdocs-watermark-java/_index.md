---
date: '2026-04-04'
description: Scopri come rimuovere i collegamenti dalle forme dei diagrammi con GroupDocs.Watermark
  Java, garantendo la sicurezza e la chiarezza del documento.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Come rimuovere i collegamenti dalle forme del diagramma usando GroupDocs.Watermark
  Java
type: docs
url: /it/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Come rimuovere i collegamenti dalle forme del diagramma usando GroupDocs.Watermark Java

Gestire documenti digitali spesso comporta la modifica dei diagrammi, specialmente quando è necessario **how to strip links** per motivi di sicurezza o chiarezza. In questo tutorial imparerai un modo semplice, passo‑per‑passo, per rimuovere i collegamenti ipertestuali indesiderati dalle forme del diagramma usando la potente libreria **GroupDocs.Watermark** per Java. Alla fine, avrai diagrammi puliti, privi di collegamenti, sicuri da condividere.

## Risposte rapide
- **What does “how to strip links” mean?** Si riferisce alla rimozione degli oggetti hyperlink incorporati nelle forme del diagramma.  
- **Which library handles this?** GroupDocs.Watermark per Java (versione 24.11 o successive).  
- **Do I need a license?** Una prova gratuita funziona per i test; è necessaria una licenza valida per la produzione.  
- **Can I process many files at once?** Sì – avvolgi il codice in un ciclo o in un lavoro batch.  
- **Is this approach language‑specific?** L'esempio è Java, ma lo stesso concetto si applica ad altre API .NET/Java.

## Cos'è “how to strip links” nella modifica dei diagrammi?
Rimuovere i collegamenti significa individuare gli oggetti hyperlink collegati alle forme all'interno di un diagramma (ad es., Visio *.vsdx) e cancellarli. Questo elimina URL esterni che potrebbero esporre informazioni sensibili o interrompere il flusso della presentazione.

## Perché usare GroupDocs.Watermark per Java?
- **Precision** – Accesso diretto agli oggetti forma e alle loro collezioni di hyperlink.  
- **Performance** – Ottimizzato per diagrammi di grandi dimensioni senza caricare l'intero documento in memoria.  
- **Cross‑format support** – Funziona con molti formati di diagramma (Visio, Draw.io, ecc.).  

## Prerequisiti
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (o inclusione manuale del JAR).  
- Java JDK 8 o superiore.  
- Un IDE come IntelliJ IDEA o Eclipse.

## Configurazione di GroupDocs.Watermark per Java
### Configurazione Maven
Aggiungi il repository e la dipendenza al tuo `pom.xml`:

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
Se preferisci non usare Maven, scarica l'ultimo JAR dal sito ufficiale:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Passaggi per l'acquisizione della licenza
- Inizia con il download della prova gratuita.  
- Per la produzione, ottieni una licenza temporanea o completa dal portale GroupDocs.

#### Inizializzazione e configurazione di base
Crea un'istanza di `Watermarker` che punti alla cartella contenente il tuo diagramma:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Come rimuovere i collegamenti dalle forme del diagramma
Di seguito è riportato un processo conciso in quattro passaggi che mostra **remove hyperlinks java** in azione.

### Passo 1: Carica il file del diagramma
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Perché?* Caricare il file ti fornisce accesso programmatico alle sue pagine, forme e collezioni di hyperlink.

### Passo 2: Accedi al contenuto della forma
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Perché?* Hai bisogno di un riferimento alla forma specifica che può contenere hyperlink.

### Passo 3: Itera e rimuovi gli hyperlink
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Perché?* Iterare al contrario evita problemi di spostamento degli indici quando si eliminano elementi dalla collezione.

### Passo 4: Salva e chiudi
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Perché?* Il salvataggio scrive il diagramma pulito su disco, e la chiusura rilascia i handle dei file per evitare perdite di memoria.

## Applicazioni pratiche della rimozione dei collegamenti
1. **Security** – Rimuovi URL esterni che potrebbero portare a phishing o perdita di dati.  
2. **Compliance** – Assicura che i diagrammi rispettino le politiche interne prima della distribuzione.  
3. **Presentation Cleanliness** – Elimina aree cliccabili non necessarie che distraggono gli spettatori.

## Considerazioni sulle prestazioni
- **Loop Efficiency** – Usa il modello di iterazione inversa mostrato sopra.  
- **Resource Management** – Preferisci `try‑with‑resources` o chiamate esplicite a `close()`.  
- **Large Files** – Monitora CPU/memoria; considera l'elaborazione delle pagine in batch.

## Problemi comuni e soluzioni
- **No hyperlinks found** – Verifica che il diagramma contenga effettivamente oggetti hyperlink; alcuni formati li memorizzano in modo diverso.  
- **IndexOutOfBoundsException** – Itera sempre al contrario quando rimuovi elementi da una collezione.  
- **License errors** – Assicurati che il file di licenza sia posizionato correttamente o passato al costruttore `Watermarker`.

## Domande frequenti

**Q: How do I handle multiple shapes on multiple pages?**  
A: Scorri `content.getPages()` e poi la collezione `getShapes()` di ogni pagina, applicando la stessa logica di rimozione a ogni forma.

**Q: Can I filter links by domain instead of a full URL?**  
A: Sì – modifica il controllo `contains` per cercare la stringa del dominio (ad es., `"example.com"`).

**Q: Is there a way to log which links were removed?**  
A: All'interno del ciclo, cattura `shape.getHyperlinks().get_Item(i).getAddress()` prima della rimozione e scrivilo in un file di log.

**Q: Does this work with PDF diagrams embedded in other documents?**  
A: GroupDocs.Watermark supporta molti formati; assicurati che il tipo di file sia riconosciuto come diagramma (Visio, VDX, ecc.).

**Q: What licensing is required for batch processing?**  
A: È necessaria una licenza di produzione completa per qualsiasi operazione non‑di prova ad alto volume.

## Conclusione
Ora disponi di un metodo completo, pronto per la produzione, per **how to strip links** dalle forme del diagramma usando GroupDocs.Watermark per Java. Integra questo nelle tue pipeline di elaborazione dei documenti per migliorare sicurezza, conformità e qualità visiva.

### Prossimi passi
- Esplora altre funzionalità di manipolazione come l'aggiunta di filigrane o la stampa di testo.  
- Combina questa routine con un servizio di monitoraggio dei file per pulire automaticamente i diagrammi al momento del caricamento.

---

**Ultimo aggiornamento:** 2026-04-04  
**Testato con:** GroupDocs.Watermark 24.11 for Java  
**Autore:** GroupDocs  

## Risorse
- [Documentazione](https://docs.groupdocs.com/watermark/java/)
- [Riferimento API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Acquisizione licenza temporanea](https://purchase.groupdocs.com/temporary-license/)