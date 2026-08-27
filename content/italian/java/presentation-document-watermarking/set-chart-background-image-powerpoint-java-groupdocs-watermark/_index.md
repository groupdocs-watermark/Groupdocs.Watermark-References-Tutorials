---
date: '2026-03-17'
description: Scopri come salvare le immagini dei grafici PowerPoint e impostare lo
  sfondo del grafico usando Java e GroupDocs.Watermark. Segui questa guida passo passo
  per una visualizzazione dei dati migliorata.
keywords:
- set chart background image PowerPoint
- Java GroupDocs.Watermark
- PowerPoint presentation enhancement
title: Salva l'immagine del grafico PowerPoint con Java e GroupDocs.Watermark
type: docs
url: /it/java/presentation-document-watermarking/set-chart-background-image-powerpoint-java-groupdocs-watermark/
weight: 1
---

.

# Salva l'immagine del grafico PowerPoint usando Java & GroupDocs.Watermark

In questo tutorial imparerai **come salvare le immagini del grafico PowerPoint** e applicare uno sfondo personalizzato, conferendo alle tue presentazioni un aspetto curato e coerente con il brand. Ti guideremo attraverso l’intero processo con Java e GroupDocs.Watermark, dalla configurazione della libreria alla definizione di trasparenza e opzioni di tiling.

## Risposte rapide
- **Cosa significa “salvare il grafico PowerPoint”?** Indica l’esportazione del grafico come parte di un file PowerPoint dopo aver applicato personalizzazioni visive.  
- **Quale libreria aggiunge un’immagine di sfondo al grafico?** GroupDocs.Watermark per Java fornisce un’API semplice per impostare immagini di sfondo sui grafici.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per la valutazione; è richiesta una licenza completa per l’uso in produzione.  
- **Posso ripetere l’immagine di sfondo?** Sì – usa il metodo `setTileAsTexture(true)` per ripetere l’immagine come texture.  
- **Java 8 è sufficiente?** La libreria supporta JDK 8 e versioni successive.

## Cos’è “salvare il grafico PowerPoint”?
Salvare un grafico PowerPoint significa incorporare un grafico all’interno di una diapositiva e mantenere eventuali modifiche visive — come un’immagine di sfondo personalizzata — nel file finale `.pptx`. Questo consente di distribuire presentazioni che già contengono l’aspetto desiderato.

## Perché impostare uno sfondo al grafico con GroupDocs.Watermark?
- **Coerenza del brand:** Applica loghi aziendali o texture tematiche direttamente dietro i dati del grafico.  
- **Migliore leggibilità:** Regola la trasparenza in modo che i punti dati rimangano chiari mentre lo sfondo aggiunge contesto visivo.  
- **Automazione:** Integra il processo in servizi back‑end, pipeline di elaborazione batch o workflow CI/CD.  
- **Prestazioni:** GroupDocs.Watermark gestisce presentazioni di grandi dimensioni in modo efficiente, soprattutto se segui i consigli di ottimizzazione più avanti in questa guida.

## Prerequisiti

### Librerie richieste
- **GroupDocs.Watermark per Java** (ultima versione)  
- Java Development Kit (JDK) installato sulla tua macchina

### Configurazione dell’ambiente
- Un IDE come IntelliJ IDEA o Eclipse configurato con il JDK.  
- Maven per la gestione delle dipendenze.

### Conoscenze preliminari
- Programmazione Java di base e I/O di file.  
- Familiarità con la struttura di diapositive e grafici di PowerPoint.

## Configurazione di GroupDocs.Watermark per Java

### Installazione tramite Maven
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
In alternativa, scarica l’ultima versione direttamente da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza
- **Prova gratuita:** Esplora tutte le funzionalità senza costi.  
- **Licenza temporanea:** Utilizzabile per periodi di valutazione prolungati.  
- **Acquisto:** Ottieni una licenza completa per uso illimitato in produzione.

## Guida all’implementazione

### Caricamento del file di presentazione
Per prima cosa, carica il file PowerPoint che contiene il grafico da modificare:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\presentation.pptx", loadOptions);
```
- **Perché:** Questo crea un’istanza `Watermarker` che ti consente di accedere programmaticamente al contenuto della presentazione.

### Recupero e modifica delle proprietà del grafico
Successivamente, individua il grafico e carica l’immagine da usare come sfondo:

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);

// Load image to be set as background for chart.
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY\\test_image.png");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```
- **Perché:** Convertire l’immagine in un array di byte permette a GroupDocs.Watermark di incorporarla direttamente nel formato di riempimento del grafico.

### Impostazione dell’immagine di sfondo
Ora associa l’immagine al primo grafico della prima diapositiva:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setBackgroundImage(new PresentationWatermarkableImage(imageBytes));
```
- **Perché:** Questa chiamata sostituisce lo sfondo predefinito del grafico con la tua immagine personalizzata, ottenendo l’effetto **set chart background**.

### Configurazione di trasparenza e tiling
Affina l’aspetto con trasparenza e tiling della texture:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTransparency(0.5);
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTileAsTexture(true);
```
- **Perché:** La trasparenza (`0.5`) mantiene i dati visibili, mentre `setTileAsTexture(true)` **tile chart background** per creare un pattern continuo.

### Salvataggio e chiusura delle risorse
Infine, scrivi la presentazione modificata su disco e rilascia le risorse:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY\\updated_presentation.pptx");
watermarker.close();
```
- **Perché:** Persistendo le modifiche si crea un nuovo file distribuibile, e chiudere il `Watermarker` libera le risorse di sistema.

## Applicazioni pratiche

1. **Report aziendali:** Inserisci loghi o colori aziendali come sfondo dei grafici.  
2. **Diapositive educative:** Usa immagini tematiche (es. mappe, molecole) per rendere i dati più coinvolgenti.  
3. **Presentazioni di marketing:** Aggiungi texture o grafiche in stile watermark per distinguere le tue slide dalla concorrenza.

## Considerazioni sulle prestazioni

- **Ridimensiona le immagini** prima di incorporarle per mantenere la dimensione del file gestibile.  
- **Usa try‑with‑resources** per gli stream per garantire la pulizia automatica.  
- **Evita di caricare presentazioni molto grandi** interamente in memoria; elabora le diapositive in modo incrementale quando possibile.

## Problemi comuni & Risoluzione

| Problema | Soluzione |
|----------|-----------|
| `OutOfMemoryError` durante la gestione di immagini grandi | Ridimensiona l’immagine o utilizza il caricamento basato su `InputStream` anziché leggere l’intero file in un array di byte. |
| L’immagine di sfondo non è visibile | Verifica che l’`ImageFillFormat` del grafico non venga sovrascritto successivamente nel codice. |
| La trasparenza appare troppo scura | Regola il valore passato a `setTransparency()` (intervallo 0.0–1.0). |

## Domande frequenti

**D: Qual è la differenza tra `setBackgroundImage` e `add watermark chart`?**  
R: `setBackgroundImage` sostituisce il riempimento del grafico con un’immagine, mentre `add watermark chart` sovrappone testo o grafiche semi‑trasparenti sopra i dati del grafico.

**D: Posso applicare lo stesso sfondo a più grafici contemporaneamente?**  
R: Sì—itera su `content.getSlides().get_Item(i).getCharts()` e applica lo stesso `PresentationWatermarkableImage` a ciascun `ImageFillFormat` del grafico.

**D: GroupDocs.Watermark supporta GIF animate come sfondo dei grafici?**  
R: La libreria tratta le GIF come immagini statiche; viene utilizzato solo il primo fotogramma.

**D: Come garantire che lo sfondo si adatti correttamente a diverse dimensioni di diapositiva?**  
R: Usa `setTileAsTexture(true)` per ripetere l’immagine oppure calcola le dimensioni appropriate in base alla larghezza e altezza della diapositiva prima di impostare lo sfondo.

**D: Esiste un modo per verificare programmaticamente se un grafico ha già un’immagine di sfondo?**  
R: Puoi ispezionare `getImageFillFormat().getBackgroundImage()`; se restituisce `null`, nessuna immagine è impostata.

## Risorse
- **Documentazione:** [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- **Riferimento API:** [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/java)
- **Download:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)
- **Repository GitHub:** [GroupDocs.Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **Forum di supporto gratuito:** [GroupDocs Watermark Forum](https://forum.groupdocs.com/c/watermark/10)
- **Licenza temporanea:** [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Ultimo aggiornamento:** 2026-03-17  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs