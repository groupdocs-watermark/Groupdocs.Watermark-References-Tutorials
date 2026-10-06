---
date: '2026-03-20'
description: Scopri come aggiungere una filigrana utilizzando il GroupDocs.Watermark
  Java SDK per inserire una filigrana immagine in un foglio di calcolo Excel, perfetta
  per il branding e la sicurezza dei documenti.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'Come aggiungere una filigrana: filigrana immagine a un foglio di calcolo Excel
  usando GroupDocs.Watermark Java SDK'
type: docs
url: /it/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# Come aggiungere una filigrana a un foglio di calcolo Excel usando GroupDocs.Watermark Java SDK

Proteggere i tuoi file Excel da distribuzioni non autorizzate o semplicemente rafforzare l'identità del brand può essere ottenuto aggiungendo un segno visivo che rimane visibile indipendentemente dal modo in cui il file viene visualizzato. In questo tutorial imparerai **come aggiungere una filigrana** — specificamente una filigrana immagine — all'intestazione o al piè di pagina di un foglio di calcolo Excel con il **GroupDocs.Watermark Java SDK**. Alla fine della guida sarai in grado di inserire un logo, un badge di riservatezza o qualsiasi immagine personalizzata direttamente nel tuo workbook senza alterare i dati delle celle.

## Risposte rapide
- **A cosa si riferisce “come aggiungere una filigrana”?** Aggiungere una sovrapposizione di immagine (o testo) che appare su ogni pagina stampata o su sezioni specifiche come intestazioni/piè di pagina.  
- **Quale libreria supporta questo in Java?** `GroupDocs.Watermark` Java SDK (ultima versione).  
- **È necessaria una licenza?** Una prova gratuita funziona per lo sviluppo; è richiesta una licenza commerciale per la produzione.  
- **Posso aggiungere un logo all'intestazione?** Sì – usa la filigrana immagine e imposta l'opzione intestazione (`add logo to header`).  
- **È possibile elaborare più fogli contemporaneamente?** Scorri gli indici dei fogli di lavoro e applica la stessa filigrana a ciascun foglio.

## Prerequisiti

Per seguire il tutorial, assicurati di avere:

- **GroupDocs.Watermark per Java SDK** (versione 24.11 o successiva).  
- **Java Development Kit (JDK)** 8 o superiore.  
- Familiarità di base con Java e le strutture dei file Excel.  

## Configurazione di GroupDocs.Watermark per Java SDK

Per prima cosa, aggiungi le dipendenze Maven necessarie affinché l'SDK sia disponibile nel tuo classpath.

### Maven Configuration

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

Se preferisci non usare Maven, scarica l'ultimo JAR dalla pagina di rilascio ufficiale: [Rilasci GroupDocs](https://releases.groupdocs.com/watermark/java/).

**Acquisizione licenza**  
- Ottieni una prova gratuita o una chiave di licenza temporanea per valutare tutte le funzionalità.  
- Acquista una licenza completa per le distribuzioni commerciali.

### Inizializzazione e configurazione

Crea un'istanza `Watermarker` che caricherà il file Excel e fungerà da punto di ingresso per tutte le operazioni di filigrana.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## Come aggiungere una filigrana a un'intestazione/piè di pagina di un foglio di calcolo

Di seguito il processo passo‑per‑passo che dimostra la funzionalità **java add image watermark** e mostra anche come **add logo to header**.

### Passo 1: Configurare le opzioni di caricamento

Iniziamo definendo le opzioni di caricamento e reinstanziando il `Watermarker`. Questo garantisce che l'SDK legga correttamente il workbook.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### Passo 2: Creare e configurare la filigrana immagine

Crea un oggetto `ImageWatermark` che punta all'immagine che desideri incorporare (ad es., un logo o un badge “CONFIDENTIAL”). Regola il suo allineamento e la scala in modo che si adatti bene all'area dell'intestazione/piè di pagina.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### Passo 3: Configurare le opzioni di intestazione/piè di pagina

Indica all'SDK quale foglio di lavoro e quale parte (intestazione o piè di pagina) deve ricevere la filigrana. Qui puoi **add logo to header** o scegliere invece il piè di pagina.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### Passo 4: Aggiungere la filigrana

Ora collega la filigrana immagine preparata alla posizione intestazione/piè di pagina selezionata.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### Passo 5: Salvare e chiudere

Persisti le modifiche in un nuovo file così il workbook originale rimane intatto, quindi rilascia le risorse.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### Suggerimenti per la risoluzione dei problemi

- Verifica il percorso dell'immagine; un percorso errato genera una `FileNotFoundException`.  
- Gli indici dei fogli di lavoro partono da 0; assicurati che l'indice impostato esista realmente.  
- Se la filigrana appare distorta, regola `setScaleFactor` o passa a `SizingType` impostato su `StretchToParentDimensions`.

## Perché utilizzare GroupDocs.Watermark Java SDK?

- **Supporto cross‑format** – funziona con Excel, Word, PowerPoint, PDF e immagini.  
- **Modifica senza perdita** – i dati originali delle celle rimangono intatti.  
- **Ottimizzato per le prestazioni** – adatto a workbook di grandi dimensioni e a elaborazioni batch.  

## Casi d'uso pratici

| Scenario | Come la filigrana aiuta |
|----------|------------------------|
| **Report riservati** | Aggiungere un'immagine “CONFIDENTIAL” a ogni pagina stampata. |
| **Rafforzamento del brand** | Inserire il logo della tua azienda nell'intestazione delle fatture. |
| **Tracciamento della versione** | Incorporare un badge con il numero di versione che si aggiorna automaticamente. |
| **Conformità legale** | Segnare i fogli di calcolo regolamentati con un sigillo di conformità. |

## Considerazioni sulle prestazioni

- **Utilizzo della memoria** – Monitora l'heap JVM quando elabori fogli di calcolo molto grandi.  
- **Elaborazione batch** – Processa i file in gruppi per mantenere basso l'impronta di memoria.  
- **Riutilizzo degli oggetti** – Riutilizzare una singola istanza `Watermarker` per più file riduce l'overhead.

## Domande frequenti

**D: Posso aggiungere più filigrane a un singolo documento?**  
R: Sì, creando ulteriori istanze `ImageWatermark` e configurandole prima di chiamare `watermarker.add()`.

**D: Come rimuovo una filigrana esistente da un foglio di calcolo?**  
R: Attualmente, GroupDocs.Watermark si concentra sull'aggiunta di filigrane. Per rimuoverne una, dovrai ricreare il workbook senza la filigrana o utilizzare uno strumento che supporti l'estrazione delle filigrane.

**D: Quali formati immagine sono supportati per le filigrane?**  
R: Sono supportati formati comuni come PNG e JPEG, ma verifica la [documentazione GroupDocs](https://docs.groupdocs.com/watermark/java/) per l'elenco completo dei formati compatibili.

**D: È possibile filigranare fogli di calcolo protetti da password?**  
R: Sì, purché tu fornisca la password necessaria al momento dell'apertura del file.

**D: Come applico le filigrane a tutti i fogli di lavoro in un documento?**  
R: Scorri ogni indice di foglio di lavoro e ripeti i passaggi di filigranatura, impostando `headerFooterOptions.setWorksheetIndex(i)` per ogni iterazione.

## Conclusione

Ora disponi di un metodo completo e pronto per la produzione per **java add excel watermark**—specificamente una filigrana immagine—utilizzando il **GroupDocs.Watermark Java SDK**. Questo approccio aggiunge branding, avvisi di riservatezza o qualsiasi indicatore visivo direttamente nell'intestazione o nel piè di pagina dei tuoi file Excel, mantenendo intatti i dati sottostanti. Sentiti libero di esplorare altri tipi di filigrana (testo, forma) e combinarli per una protezione documentale più ricca.

---

**Ultimo aggiornamento:** 2026-03-20  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs