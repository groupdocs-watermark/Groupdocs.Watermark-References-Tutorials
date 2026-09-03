---
date: '2026-03-20'
description: Scopri come aggiungere una filigrana ai fogli di calcolo Excel usando
  GroupDocs.Watermark per Java, coprendo le tecniche per aggiungere filigrana di testo
  a Excel e per aggiungere filigrana a Excel con Java.
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: Come aggiungere una filigrana a Excel con GroupDocs.Watermark Java
type: docs
url: /it/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# Come aggiungere una filigrana a un foglio di calcolo Excel usando GroupDocs.Watermark per Java

Aggiungere una funzionalità **how to add watermark** ai tuoi file Excel è un modo pratico per proteggere dati sensibili e affermare la proprietà. In questa guida passo‑passo imparerai come aggiungere una filigrana a un foglio di calcolo Excel, personalizzarne l'aspetto e posizionarla nelle intestazioni o nei piè di pagina — tutto con GroupDocs.Watermark per Java.

## Risposte rapide
- **Quale libreria è necessaria?** GroupDocs.Watermark for Java (24.11 o più recente).  
- **Posso personalizzare il font e il colore?** Sì, usando le classi `Font` e `Color`.  
- **Dove appare la filigrana?** Nell'intestazione o nel piè di pagina del foglio di lavoro selezionato.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza GroupDocs valida per l'uso non‑trial.  
- **Funziona con cartelle di lavoro di grandi dimensioni?** Sì, ma chiudi l'oggetto `Watermarker` per liberare le risorse.

## Introduzione

Stai cercando di migliorare la sicurezza dei tuoi fogli di calcolo Excel aggiungendo filigrane di testo? Che si tratti di proteggere dati riservati o di affermare la proprietà, inserire una filigrana nelle intestazioni o nei piè di pagina del tuo foglio di calcolo può essere inestimabile. In questo tutorial, ti guideremo nell'implementare questa funzionalità usando GroupDocs.Watermark per Java.

**Cosa imparerai**
- Come aggiungere una filigrana di testo ai fogli di calcolo Excel  
- Configurare le filigrane con font e colori personalizzati  
- Impostare l'allineamento intestazione/piè di pagina nei tuoi documenti  

Con queste competenze, sarai ben attrezzato per proteggere efficacemente i tuoi fogli di calcolo. Ora, immergiamoci nei prerequisiti necessari per iniziare.

## Cos'è “how to add watermark” in Excel?

Una filigrana è un testo o un'immagine tenue e semi‑trasparente che appare dietro (o davanti) al contenuto principale. In Excel, le filigrane sono tipicamente posizionate nell'area dell'intestazione o del piè di pagina in modo che compaiano su ogni pagina stampata senza interferire con i dati delle celle.

## Perché usare GroupDocs.Watermark per Java?

- **Cross‑platform**: Funziona su qualsiasi OS che supporta Java.  
- **Full control**: Personalizza font, dimensione, colore e allineamento.  
- **Performance‑focused**: Gestione efficiente di cartelle di lavoro di grandi dimensioni.  

## Prerequisiti

- **GroupDocs.Watermark for Java** (24.11 o successivo)  
- **Java Development Kit (JDK)** installato e configurato  
- IDE come IntelliJ IDEA o Eclipse  
- Maven (se preferisci la gestione delle dipendenze)  

### Librerie richieste

- **GroupDocs.Watermark for Java** – fornisce l'API di filigranatura.  

### Prerequisiti di conoscenza

- Programmazione Java di base  
- Familiarità con Maven o gestione manuale dei JAR  

## Configurazione di GroupDocs.Watermark per Java

Puoi installare la libreria tramite Maven o scaricare direttamente il JAR.

**Installazione Maven**

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

**Download diretto**  
In alternativa, puoi scaricare l'ultima versione da [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisizione della licenza
- **Free Trial** – esplora l'API senza costi.  
- **Temporary License** – periodo di valutazione esteso.  
- **Purchase** – funzionalità complete, utilizzo illimitato.

Per inizializzare GroupDocs.Watermark, includi la dichiarazione di importazione:

```java
import com.groupdocs.watermark.Watermarker;
```

## Come aggiungere una filigrana ai fogli di calcolo Excel

Di seguito trovi il codice completo e eseguibile suddiviso in passaggi chiari. Ogni passaggio include una breve spiegazione prima del blocco di codice, così non vedrai mai uno snippet senza contesto.

### Passo 1: Caricare il foglio di calcolo

Per prima cosa, carica la cartella di lavoro con le opzioni di caricamento appropriate.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**Spiegazione**: Questo crea un'istanza `Watermarker` collegata al tuo file Excel, pronta per le operazioni di filigrana.

### Passo 2: Creare la filigrana di testo

Configura l'aspetto visivo della filigrana.

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**Spiegazione**: Impostiamo il testo della filigrana, scegliamo un font **Segoe UI** in grassetto e applichiamo colori di primo piano e sfondo contrastanti.

### Passo 3: Configurare il posizionamento della filigrana

Decidi quale foglio di lavoro e quale parte della pagina (intestazione/piè di pagina) riceverà la filigrana.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**Spiegazione**: L'oggetto `SpreadsheetWatermarkHeaderFooterOptions` indica all'API di applicare la filigrana all'intestazione/piè di pagina del primo foglio.

### Passo 4: Aggiungere la filigrana e salvare

Applica la filigrana e scrivi il risultato in un nuovo file.

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**Spiegazione**: Il metodo `add` inserisce la filigrana, `save` scrive la cartella di lavoro modificata e `close` libera le risorse.

## Aggiungere una filigrana di testo a Excel – Suggerimenti avanzati

- **Multiple Worksheets**: Itera sugli indici dei fogli di lavoro e chiama `options.setWorksheetIndex(i)` per ciascuno.  
- **Dynamic Text**: Preleva il testo della filigrana da un database o file di configurazione per personalizzare ogni documento.  
- **Opacity Control**: Usa `watermark.setOpacity(0.5)` per rendere la filigrana più sottile.  

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **File non trovato** | Verifica che le stringhe di percorso (`YOUR_DOCUMENT_DIRECTORY/...`) siano corrette e usa percorsi assoluti durante i test. |
| **Licenza non trovata** | Posiziona il file `GroupDocs.Watermark.lic` nella radice del progetto o imposta la licenza programmaticamente con `License license = new License(); license.setLicense("path/to/license.lic");`. |
| **Formato non supportato** | Assicurati che la cartella di lavoro sia salvata come `.xlsx` o `.xls`. I formati più vecchi potrebbero richiedere una conversione preliminare. |
| **Ritardo di prestazioni su file di grandi dimensioni** | Elabora un foglio di lavoro alla volta e chiama `watermarker.close()` appena termini con ogni file. |

## Applicazioni pratiche

1. **Protezione dei dati riservati** – Disincentiva la copia non autorizzata marcando visibilmente ogni pagina stampata.  
2. **Affermare la proprietà** – Inserisci il nome dell'azienda o il logo come filigrana per dimostrare la provenienza del documento.  
3. **Tracciamento dei documenti** – Includi identificatori unici nella filigrana per tracciare i percorsi di distribuzione.  

## Considerazioni sulle prestazioni

- Riduci al minimo il numero di filigrane per sessione.  
- Chiudi prontamente l'oggetto `Watermarker` per rilasciare i handle dei file.  
- Per cartelle di lavoro molto grandi, considera di aumentare la dimensione dell'heap JVM (`-Xmx2g`).  

## Domande frequenti

**D: Posso cambiare lo stile del font della mia filigrana?**  
R: Sì, personalizza l'oggetto `Font` con qualsiasi famiglia di font installata, dimensione e `FontStyle` (Bold, Italic, ecc.).

**D: È possibile aggiungere filigrane a più fogli?**  
R: Assolutamente. Itera sugli indici dei fogli di lavoro e applica lo stesso `SpreadsheetWatermarkHeaderFooterOptions` per ogni foglio.

**D: Quali formati di file supporta GroupDocs.Watermark per i file Excel?**  
R: XLS, XLSX e altri formati di fogli di calcolo Office Open XML sono pienamente supportati.

**D: Come gestire in modo efficiente documenti molto grandi?**  
R: Elabora una cartella di lavoro alla volta, chiudi il `Watermarker` dopo il salvataggio e monitora l'uso della memoria JVM.

**D: È possibile rimuovere le filigrane in seguito, se necessario?**  
R: La rimozione diretta non è fornita, ma è possibile rigenerare il file originale senza applicare una filigrana o conservare una copia non filigranata per uso futuro.

## Risorse

- [Documentazione GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- [Riferimento API](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark per Java](https://releases.groupdocs.com/watermark/java/)  
- [Repository GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/watermark/10)  
- [Informazioni sulla licenza temporanea](https://purchase.groupdocs.com/temporary-license/)  

---

**Ultimo aggiornamento:** 2026-03-20  
**Testato con:** GroupDocs.Watermark 24.11 per Java  
**Autore:** GroupDocs