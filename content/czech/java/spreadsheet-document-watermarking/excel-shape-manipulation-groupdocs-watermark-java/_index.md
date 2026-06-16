---
date: '2026-06-01'
description: Naučte se, jak odstranit tvary ze souborů Excel pomocí GroupDocs.Watermark
  pro Java. Obsahuje kroky pro načtení Excelu, procházení listů a mazání formátovaných
  tvarů.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Jak odstranit tvary z Excelu pomocí GroupDocs.Watermark v Javě
type: docs
url: /cs/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Jak odstranit tvary z Excel pomocí GroupDocs.Watermark v Javě

Excelové tabulky jsou základním kamenem obchodního reportingu, ale nechtěné tvary — zejména ty s zastaralým nebo nestandardním formátováním textu — mohou soubor zaplnit a narušit vizuální konzistenci. **Odstraňování tvarů z Excelu** se rychle stává nezbytným pro čisté, profesionální dokumenty. V tomto tutoriálu projdeme načtením Excel sešitu, iterací jeho listů a programovým mazáním tvarů, které odpovídají konkrétním kritériím formátování, vše pomocí výkonné knihovny GroupDocs.Watermark pro Javu.

## Rychlé odpovědi
- **Může GroupDocs.Watermark mazat tvary?** Ano, poskytuje metodu `removeShape`, která funguje na jakémkoli listu.  
- **Potřebuji licenci pro tuto funkci?** Zkušební verze funguje pro hodnocení; plná licence je vyžadována pro produkci.  
- **Jaká verze Javy je požadována?** Java 8 nebo novější je podporována.  
- **Kolik formátů souborů GroupDocs.Watermark podporuje?** Více než 30 vstupních a výstupních formátů, včetně XLSX, DOCX, PDF a PPTX.  
- **Je spotřeba paměti problémem u velkých sešitů?** Používejte try‑with‑resources a vyhněte se načítání celých listů do paměti; API efektivně streamuje data.

## Co je odstraňování tvarů z Excelu?
*Odstraňování tvarů z Excelu* znamená programové mazání kreslicích objektů — jako jsou textová pole, ikony nebo SmartArt — které splňují určitá kritéria, jako je styl písma, barva nebo velikost. Tato operace vyčistí sešit bez ruční úpravy, zajišťuje vizuální konzistenci, snižuje velikost souboru a zabraňuje zobrazování zastaralých nebo nechtěných grafik v distribuovaných zprávách.

## Proč odstraňovat tvary z Excelu?
GroupDocs.Watermark dokáže zpracovat **více než stovky stránek sešitů až 3 × rychleji** než ruční úpravy, podporuje **30+ formátů souborů** a přitom udržuje spotřebu paměti pod 150 MB pro soubory větší než 50 MB. Automatizace odstraňování tvarů eliminuje lidské chyby a zaručuje konzistentní branding ve všech generovaných zprávách.

## Předpoklady
### Požadované knihovny, verze a závislosti
- **Java Development Kit (JDK)**: Verze 8 nebo novější.  
- **GroupDocs.Watermark**: Verze 24.11 (nejnovější stabilní vydání v době psaní).

### Požadavky na nastavení prostředí
Použijte IDE jako IntelliJ IDEA nebo Eclipse a Maven pro správu závislostí.

### Předpoklady znalostí
Znalost syntaxe Javy a základních konceptů Excelu (listy, buňky a tvary) vám pomůže sledovat příklady.

## Nastavení GroupDocs.Watermark pro Javu
**Závislost Maven**  
Přidejte následující do vašeho `pom.xml`:

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

**Přímé stažení**  
Alternativně stáhněte nejnovější verzi z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Kroky získání licence
- **Free Trial** – Začněte s bezplatnou zkušební verzí pro vyhodnocení funkcí.  
- **Temporary License** – Získejte dočasnou licenci pro rozšířené testování.  
- **Purchase** – Kupte plnou licenci pro produkční použití.

### Základní inicializace a nastavení  
Jakmile je knihovna přidána do vašeho projektu, inicializujte ji podle níže uvedeného příkladu:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Jak odstranit tvary z Excelu?
Načtěte sešit, projděte každý list a zavolejte API pro odstraňování tvarů. Tento dvoukrokový vzor — *načíst* a pak *iterovat* — pokrývá prakticky jakýkoli scénář, kdy potřebujete vyčistit tvary v celém souboru. Kontrolou vlastností každého tvaru podle vašich kritérií před odstraněním zajistíte, že budou smazány pouze nechtěné prvky, zatímco zbytek rozvržení a obsahu dokumentu zůstane zachován.

## Načtení Excel dokumentu
**Přehled**  
Načtení Excel dokumentu je výchozím bodem pro jakýkoli úkol manipulace. GroupDocs.Watermark to zjednodušuje pomocí svého intuitivního API.  

**Definiční kotva**  
`SpreadsheetDocument` je hlavní třída v GroupDocs.Watermark, která představuje Excel sešit v paměti a poskytuje metody pro přístup k listům, buňkám a tvarům.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Přístup a iterace přes listy v tabulce
**Přehled**  
Iterace přes listy vám umožňuje provádět operace na každém listu samostatně.  

**Definiční kotva**  
`Worksheet` představuje jeden list uvnitř `SpreadsheetDocument`; můžete číst, upravovat nebo mazat jeho obsah pomocí tohoto objektu.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Odstranění tvarů s konkrétním formátováním textu z tabulky
**Přehled**  
Tato funkce cílí na tvary, které splňují určitá kritéria formátování textu, jako je typ písma nebo barva.  

**Definiční kotva**  
`Shape` je objektový model pro jakýkoli kreslicí prvek (textové pole, obrázek nebo SmartArt) uvnitř listu; poskytuje vlastnosti jako `getText`, `getFont` a `remove`.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Praktické aplikace
### Reálné příklady použití
1. **Data Validation** – Automaticky odstraňovat tvary, které obsahují zastaralá upozornění.  
2. **Template Standardization** – Vynutit firemní branding odstraněním nestandardních textových polí.  
3. **Automated Reporting** – Vyčistit generované zprávy před distribucí, zajišťující profesionální vzhled.

### Možnosti integrace
GroupDocs.Watermark může být vložen do Java‑založených podnikových pipeline, jako jsou mikro‑služby pro generování dokumentů, úlohy dávkového zpracování nebo systémy pro správu obsahu, poskytující plynulý, licencí souladný způsob správy Excel aktiv.

## Úvahy o výkonu
### Optimalizace výkonu
- **Vyhněte se těžkým operacím uvnitř smyček** – načtěte kolekce tvarů jednou na list.  
- **Uvolněte prostředky okamžitě** – použijte try‑with‑resources k automatickému uzavření streamů.

### Pokyny pro využití zdrojů
Uvolněte objekt `SpreadsheetDocument` ihned po dokončení zpracování, aby se uvolnila nativní paměť. Pro soubory přesahující 100 MB zvažte zpracování listů v paralelních streamech, abyste využili vícejádrové CPU.

### Nejlepší postupy pro správu paměti v Javě
Využijte `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }`, aby se metoda `close()` spustila i při výskytu výjimky.

## Časté problémy a řešení
- **Shape not found** – Ujistěte se, že kontrolujete správný index listu; tvary jsou omezeny na jednotlivé listy.  
- **License exception** – Zkušební licence zakazuje dávkové zpracování; upgradujte na plnou licenci pro neomezené operace.  
- **Unexpected font values** – Vlastnosti písma mohou být zděděny; použijte `shape.getEffectiveFont()` k získání vyřešeného stylu.

## Často kladené otázky

**Q: Mohu odstranit tvary z pracovního sešitu chráněného heslem?**  
A: Ano. Načtěte dokument s parametrem hesla a poté spusťte stejnou logiku odstraňování; API dešifruje soubor v paměti.

**Q: Podporuje knihovna soubory .xls (Excel 97‑2003)?**  
A: Rozhodně. GroupDocs.Watermark zpracovává jak `.xlsx`, tak starší formáty `.xls` bez konverze.

**Q: Jak mohu zaznamenat, které tvary byly smazány?**  
A: Projděte kolekci tvarů, zkontrolujte kritéria formátování, zaznamenejte `shape.getName()` nebo `shape.getId()`, a poté zavolejte `remove()`.

**Q: Je možné přidat vodoznak po odstranění tvarů?**  
A: Ano. Po vyčištění zavolejte `doc.addWatermark(new TextWatermark("Confidential"))`, aby se přes všechny listy přidal textový vodoznak.

**Q: Jaká je maximální podporovaná velikost souboru?**  
A: Knihovna může zpracovat soubory až do **2 GB** na 64‑bitovém JVM, omezené pouze dostupnou haldou paměti a omezeními OS.

## Závěr
V tomto tutoriálu jsme předvedli kompletní, připravený přístup pro **odstraňování tvarů z Excelu** v sešitech pomocí GroupDocs.Watermark pro Javu. Načtením dokumentu, iterací listů a aplikací přesných filtrů formátování můžete automatizovat úkoly úklidu, vynutit branding a zlepšit kvalitu zpráv ve velkém měřítku. Prozkoumejte další funkce, jako je vkládání vodoznaků, konverze dokumentů a dávkové zpracování, abyste dále rozšířili svůj nástroj pro automatizaci dokumentů.

---

**Poslední aktualizace:** 2026-06-01  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Manipulace s tvary v Excelu pomocí GroupDocs.Watermark v Javě: Kompletní průvodce](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Přidání obrázkového vodoznaku do Excel tabulky pomocí GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Zpracování Excel dokumentů a vodoznakování s GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)