---
date: '2026-03-27'
description: Scopri come aggiungere una filigrana ai file Excel usando GroupDocs.Watermark
  per Java. Questa guida illustra l'installazione, il codice e le migliori pratiche
  per applicare filigrane ai fogli di calcolo.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: Aggiungi filigrana a Excel usando GroupDocs.Watermark Java
type: docs
url: /it/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# Aggiungi filigrana a Excel usando GroupDocs.Watermark Java

Applicare filigrane ai tuoi file Excel può fare la differenza — che tu debba proteggere dati sensibili, marchiare i tuoi report o semplicemente aggiungere un tocco professionale. In questo tutorial imparerai **come aggiungere filigrana a excel** ai fogli di calcolo usando GroupDocs.Watermark per Java, con spiegazioni chiare, casi d'uso reali e consigli per evitare gli errori più comuni.

## Risposte rapide
- **Quale libreria è necessaria?** GroupDocs.Watermark for Java (ultima versione).  
- **Quali formati Excel sono supportati?** file .xlsx e .xls (non crittografati).  
- **Posso aggiungere filigrane immagine?** Sì — l'SDK supporta sia filigrane di testo che di immagine.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza commerciale per le distribuzioni non‑di prova.  
- **Quanto tempo richiede l'implementazione?** Circa 10‑15 minuti per una filigrana di testo di base.

## Cos'è **add watermark to excel**?
Aggiungere una filigrana a una cartella di lavoro Excel significa applicare un testo o un'immagine visibile (o semitrasparente) su ogni foglio di lavoro o documento incorporato. Questo ti aiuta a rivendicare la proprietà, indicare la riservatezza o rafforzare il branding su tutto il file.

## Perché usare GroupDocs.Watermark per Java?
GroupDocs.Watermark offre un'API di alto livello che astrae la complessità della gestione delle strutture Office Open XML. Consente di:
- Applicare filigrane a più fogli di lavoro in una singola chiamata.  
- Gestire gli allegati incorporati (ad es., PDF incorporati) automaticamente.  
- Conservare la formattazione e le formule originali.  
- Lavorare sia con filigrane di testo che di immagine (ad es., **add image watermark java**).

## Prerequisiti

- **Ambiente di sviluppo Java** – Java 8 o superiore (JDK).  
- **GroupDocs.Watermark per Java SDK** – scarica l'ultima versione da [here](https://releases.groupdocs.com/watermark/java/).  
- **IDE** – IntelliJ IDEA, Eclipse o qualsiasi editor compatibile con Java.  
- **Foglio di calcolo di esempio** – un file .xlsx che desideri proteggere.

Puoi aggiungere l'SDK al tuo progetto tramite Maven, Gradle o posizionando manualmente i file JAR nel classpath.

## Importa pacchetti

Queste importazioni ti danno accesso alle classi core per le filigrane, alla gestione dei fogli di calcolo e alle utility dei font.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## Come **watermark spreadsheet** – Guida passo‑passo

Di seguito trovi una guida pratica, numerata, che mostra esattamente **how to watermark spreadsheet** files with Java. Ogni passo include una breve spiegazione seguita dal blocco di codice originale (invariato).

### Passo 1: Configura il tuo oggetto Watermark  
**Perché?** Questo oggetto definisce l'aspetto visivo del timbro che applicherai.

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Passo 2: Carica il foglio di calcolo  
**Perché?** Aprire la cartella di lavoro fornisce all'SDK un handle per modificare.

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### Passo 3: Accedi al contenuto del foglio di calcolo e ai fogli di lavoro  
**Perché?** I file Excel possono contenere molti fogli; è necessario iterare su ciascuno.

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### Passo 4: Scorri gli allegati in ciascun foglio di lavoro  
**Perché?** Alcuni fogli di lavoro incorporano altri documenti (ad es., PDF). Gestirli garantisce una filigrana coerente su tutto il file.

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### Passo 5: Applica la filigrana a ogni documento allegato  
**Perché?** Vuoi lo stesso timbro “Confidenziale” su ogni file incorporato.

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### Passo 6: Salva tutte le modifiche  
**Perché?** Persisti le modifiche in una nuova cartella di lavoro.

```java
watermarker.save("your-output-file.xlsx");
```

### Passo 7: Chiudi le risorse  
**Perché?** Liberare le risorse previene perdite di memoria, soprattutto durante l'elaborazione di cartelle di lavoro di grandi dimensioni.

```java
watermarker.close();
```

## Metti tutto insieme: Esempio completo

La classe seguente combina tutti i passaggi in un unico programma eseguibile. **Non modificare il blocco di codice** – è identico all'esempio originale.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## Problemi comuni e soluzioni

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Cartella di lavoro crittografata viene ignorata** | L'SDK non può leggere file crittografati senza una password. | Decrittografa prima il file o fornisci la password tramite `SpreadsheetLoadOptions.setPassword("pwd")`. |
| **Filigrana non visibile su alcuni fogli** | Il foglio potrebbe avere una vista personalizzata o una protezione che nasconde gli oggetti di disegno. | Disabilita la protezione del foglio prima di aggiungere la filigrana, quindi riapplicala se necessario. |
| **Rallentamento delle prestazioni su file grandi** | Caricare l'intera cartella di lavoro in memoria può essere pesante. | Elabora i fogli di lavoro in batch o aumenta la dimensione dell'heap JVM (`-Xmx2g`). |
| **La filigrana immagine appare distorta** | Impostazioni di scala errate. | Usa `ImageWatermark` con parametri espliciti di larghezza/altezza per mantenere le proporzioni. |

## Domande frequenti

**Q: Posso aggiungere una filigrana immagine invece di testo?**  
A: Sì. Usa `ImageWatermark` dall'SDK e passa un'istanza `java.awt.Image`. Questo copre lo scenario **add image watermark java**.

**Q: Come controllo la posizione della filigrana?**  
A: La classe `TextWatermark` (o `ImageWatermark`) fornisce proprietà come `setHorizontalAlignment`, `setVerticalAlignment` e `setOpacity` per regolare finemente il posizionamento e la trasparenza.

**Q: È possibile applicare filigrane a più file Excel in un'unica esecuzione?**  
A: Assolutamente. Avvolgi l'intero flusso di lavoro in un ciclo `for` che itera su una directory di file, riutilizzando la stessa istanza `TextWatermark`.

**Q: Cosa succede se il foglio di calcolo contiene grafici?**  
A: I grafici sono trattati come oggetti di disegno separati; la filigrana viene applicata sulla tela del foglio di lavoro, quindi i grafici rimangono inalterati ma sono comunque coperti dal timbro traslucido.

**Q: Posso rimuovere una filigrana aggiunta in precedenza?**  
A: L'SDK include i metodi `watermarker.remove(watermark)`, ma è necessario mantenere un riferimento all'oggetto filigrana originale o cercare per testo/contenuto per identificarlo.

---

**Ultimo aggiornamento:** 2026-03-27  
**Testato con:** GroupDocs.Watermark 23.12 (Java)  
**Autore:** GroupDocs