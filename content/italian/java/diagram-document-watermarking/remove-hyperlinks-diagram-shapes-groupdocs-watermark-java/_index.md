---
date: '2025-12-19'
description: Scopri come rimuovere i collegamenti ipertestuali dalle forme dei diagrammi
  usando GroupDocs.Watermark Java, un passaggio fondamentale per la sicurezza dei
  documenti Java e per rimuovere in batch i collegamenti ipertestuali.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Come rimuovere i collegamenti ipertestuali dalle forme del diagramma usando
  GroupDocs.Watermark Java
type: docs
url: /it/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Come rimuovere i collegamenti ipertestuali dalle forme dei diagrammi usando GroupDocs.Watermark Java

Gestire documenti digitali spesso comporta la modifica dei diagrammi, soprattutto quando si **rimuovono i collegamenti ipertestuali** per motivi di sicurezza o chiarezza. In questo tutorial imparerai **come rimuovere i collegamenti ipertestuali** dalle forme dei diagrammi con GroupDocs.Watermark per Java, garantendo che i tuoi file rimangano puliti, sicuri e professionali.

## Risposte rapide
- **Qual è lo scopo principale?** Rimuovere i collegamenti ipertestuali indesiderati dalle forme dei diagrammi per una migliore sicurezza del documento.  
- **Quale libreria viene utilizzata?** GroupDocs.Watermark per Java (versione 24.11 o successiva).  
- **È necessaria una licenza?** Una versione di prova funziona per i test; è richiesta una licenza valida per la produzione.  
- **Posso elaborare molti file contemporaneamente?** Sì – la stessa logica può essere inserita in un ciclo batch.  
- **Java 8 è sufficiente?** Java 8+ è supportato; si raccomandano JDK più recenti.

## Cosa significa “come rimuovere i collegamenti ipertestuali” nel contesto dei diagrammi?
Rimuovere i collegamenti ipertestuali significa eliminare i riferimenti URL allegati alle forme all'interno di un file di diagramma (ad esempio, Visio *.vsdx). Questa operazione impedisce navigazioni accidentali a siti esterni e aiuta a soddisfare le normative di conformità o le politiche di sicurezza interne.

## Perché utilizzare GroupDocs.Watermark Java per questa attività?
- **Supporto robusto dei formati** – funziona con un'ampia gamma di tipi di diagrammi.  
- **API fine‑grained** – consente di mirare a forme individuali e alle loro collezioni di collegamenti ipertestuali.  
- **Ottimizzata per le prestazioni** – adatta sia per file singoli sia per elaborazioni in batch.  

## Prerequisiti
- **Libreria GroupDocs.Watermark** versione 24.11 o successiva.  
- Maven o download diretto del JAR (vedi i passaggi di configurazione di seguito).  
- Java Development Kit (JDK 8 o successivo) e un IDE come IntelliJ IDEA o Eclipse.  

## Configurazione di GroupDocs.Watermark per Java
Per iniziare, includi la libreria nel tuo progetto tramite Maven o scaricando il JAR.

### Configurazione Maven
Aggiungi la seguente configurazione al tuo `pom.xml`:

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
- Inizia con una prova gratuita per valutare l'API.  
- Per la produzione, ottieni una licenza temporanea o completa dal portale GroupDocs.

#### Inizializzazione e configurazione di base
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Come rimuovere i collegamenti ipertestuali dalle forme dei diagrammi
Di seguito trovi una guida passo‑passo che ti accompagna nel caricamento di un diagramma, nella localizzazione delle forme e nella rimozione dei collegamenti ipertestuali indesiderati.

### Passo 1: Carica il file del diagramma
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Perché?* Caricare il file ti consente di accedere programmaticamente alla sua struttura interna.

### Passo 2: Accedi al contenuto della forma
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Perché?* Hai bisogno di un riferimento alla forma specifica che può contenere collegamenti ipertestuali.

### Passo 3: Itera e rimuovi i collegamenti ipertestuali
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Perché?* Iterare all'indietro previene errori di indice quando elimini elementi dalla collezione.

### Passo 4: Salva e chiudi
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Perché?* Persistere le modifiche e rilasciare le risorse evita perdite di memoria e file bloccati.

## Rimozione batch di collegamenti ipertestuali (caso d'uso avanzato)
Se devi pulire molti diagrammi contemporaneamente, avvolgi la logica sopra in un ciclo che itera su un elenco di percorsi file. Le stesse chiamate API si applicano; basta cambiare le directory di input e output per ogni iterazione. Questo approccio soddisfa i requisiti di **rimozione batch di collegamenti ipertestuali** per grandi repository di documenti.

## Applicazioni pratiche
Rimuovere i collegamenti ipertestuali dalle forme dei diagrammi può essere vantaggioso in diversi scenari reali:

1. **Scopi di sicurezza** – Impedire link esterni che potrebbero esporre la tua rete a phishing o malware.  
2. **Conformità** – Rispettare le politiche aziendali che vietano URL in uscita nei documenti condivisi.  
3. **Chiarezza** – Produrre presentazioni più pulite dove i collegamenti ipertestuali sono inutili o distraenti.  

## Considerazioni sulle prestazioni
### Ottimizzazione delle prestazioni
- Usa il pattern di iterazione inversa mostrato sopra per mantenere i cicli efficienti.  
- Chiudi l'oggetto `Watermarker` non appena hai finito per liberare memoria.

### Linee guida sull'uso delle risorse
- Monitora CPU e RAM durante l'elaborazione di diagrammi di grandi dimensioni.  
- Per lavori in batch, considera lo streaming dei file invece di caricarli tutti contemporaneamente.

### Best practice per la gestione della memoria in Java
- Evita di creare oggetti all'interno di cicli stretti.  
- Usa try‑with‑resources dove possibile per la pulizia automatica.

## Domande frequenti
1. **Come gestisco più forme?**  
   Itera su tutte le pagine e le loro forme, applicando la stessa logica di rimozione dei collegamenti ipertestuali a ciascuna forma.  

2. **Questo processo può essere automatizzato per grandi batch di diagrammi?**  
   Sì – incorpora il codice in una routine di elaborazione batch o integralo con il tuo sistema di gestione documenti.  

3. **E se devo rimuovere i collegamenti ipertestuali solo da pagine specifiche?**  
   Accedi alla pagina desiderata tramite il suo indice (`content.getPages().get_Item(pageIndex)`) e mira solo alle forme su quella pagina.  

4. **È necessaria una licenza per l'uso in produzione di GroupDocs.Watermark?**  
   È richiesta una licenza commerciale valida oltre il periodo di prova.  

5. **Questo metodo funziona con altri formati di diagramma?**  
   GroupDocs.Watermark supporta molti tipi di diagrammi; verifica la compatibilità nella documentazione ufficiale.  

**Domande aggiuntive**

**D:** *È possibile registrare quali collegamenti ipertestuali sono stati rimossi?*  
**R:** Sì – prima di chiamare `removeAt(i)`, cattura `shape.getHyperlinks().get_Item(i).getAddress()` e scrivilo in un file di log.

**D:** *La rimozione dei collegamenti ipertestuali influirà sull'aspetto visivo della forma?*  
**R:** No. La geometria della forma rimane invariata; solo i metadati del collegamento vengono rimossi.

**D:** *Devo riapplicare qualche stile dopo la rimozione?*  
**R:** Di solito no. La rimozione dei collegamenti ipertestuali non altera i riempimenti, le linee o gli stili del testo.

## Conclusione
Ora disponi di un metodo completo, pronto per la produzione, per **rimuovere i collegamenti ipertestuali** dalle forme dei diagrammi usando GroupDocs.Watermark per Java. Seguendo i passaggi sopra, puoi proteggere i tuoi diagrammi, rispettare le politiche e mantenere i documenti dall'aspetto curato.

## Risorse
- [Documentazione](https://docs.groupdocs.com/watermark/java/)  
- [Riferimento API](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)  
- [Acquisizione licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  
