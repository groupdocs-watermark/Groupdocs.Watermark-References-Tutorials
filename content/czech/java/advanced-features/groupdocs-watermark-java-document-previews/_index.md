---
date: '2026-09-26'
description: Zjistěte, jak převést dokument na obrázek a v Javě generovat miniatury
  pomocí GroupDocs.Watermark. Praktický průvodce krok za krokem pokrývá nastavení,
  preview streams a tipy pro výkon.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Zjistěte, jak převést dokument na obrázek a v Javě generovat miniatury
  pomocí GroupDocs.Watermark. Tento průvodce vás provede instalací, zpracováním streamů
  a optimalizací výkonu pro rychlé vytváření náhledů.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Převod dokumentu na obrázek pomocí GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Převod dokumentu na obrázek pomocí GroupDocs.Watermark Java
type: docs
url: /cs/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Převod dokumentu na obrázek pomocí GroupDocs.Watermark Java

Generování lehkých náhledových obrázků více‑stránkových dokumentů je běžnou potřebou pro portály, systémy pro správu obsahu a cloudové úložiště. **convert document to image** poskytuje koncovým uživatelům rychlou vizuální ukázku bez zátěže načítání celého souboru. Knihovna GroupDocs.Watermark Java nejen přidává vodoznaky, ale také nabízí vysoce výkonný náhledový engine, který může **java generate thumbnails** pro každou stránku v jediném průchodu.

V tomto tutoriálu se naučíte, jak nastavit knihovnu, vytvořit vlastní proudy stránek, bezpečně uvolnit prostředky a nakonec vytvořit náhledové obrázky pro každou stránku zdrojového dokumentu. Pokyny jsou určeny vývojářům se znalostí Javy a objektově orientovaných konceptů a obsahují tipy pro nejlepší postupy při zpracování velkých dávkách souborů.

## Rychlé odpovědi
- **Jaký je první krok?** Přidejte Maven závislost GroupDocs.Watermark a inicializujte `Watermarker` s cestou ke zdrojovému souboru.  
- **Jak se vytvářejí náhledové obrázky?** Implementujte `ICreatePageStream` pro otevření výstupního proudu pro každou stránku a poté zavolejte `generatePreview()` s příslušnými možnostmi.  
- **Potřebuji licenci?** Zkušební verze funguje pro základní scénáře, ale plná licence odstraňuje vodoznaky a odemyká dávkové zpracování.  
- **Mohu zpracovat PDF soubory větší než 200 stránek?** Ano – knihovna streamuje stránky, takže spotřeba paměti zůstává nízká i pro soubory s 500 stránkami.  
- **Jaké formáty obrázků jsou podporovány?** PNG, JPEG, BMP a TIFF jsou k dispozici ihned po instalaci.

## Co je převod dokumentu na obrázek?
Fráze **convert document to image** popisuje proces vykreslení každé stránky zdrojového souboru (PDF, DOCX, PPTX atd.) do rastrového obrázku, například PNG nebo JPEG. Tento převod je užitečný pro galerie miniatur, náhledové panely a mobilní prohlížeče dokumentů.

## Proč použít GroupDocs.Watermark pro generování náhledů?
GroupDocs.Watermark podporuje **30+ vstupních formátů** a může generovat náhledy dokumentů až do **500 stránek** bez načítání celého souboru do paměti. Interně zpracovává stránky sekvenčně, což udržuje využití Java heap pod 50 MB i u velkých PDF. Knihovna také nabízí vestavěnou optimalizaci obrázků, umožňující nastavit DPI, hloubku barev a úroveň komprese, což vede k miniaturám, které jsou typicky **70 % menší** než při naivní rasterizaci.

## Požadavky

Před zahájením se ujistěte, že máte následující:

- **Java Development Kit (JDK) 11 nebo novější** – knihovna je zkompilována pro Java 8+, ale JDK 11 poskytuje dlouhodobou podporu a lepší výkon.
- **Maven 3.6+** – pro správu závislostí.
- **GroupDocs.Watermark pro Java verze 24.11** – nejnovější stabilní vydání v době psaní.
- **Základní znalost Java I/O streamů** – budete vytvářet objekty `FileOutputStream` pro každou náhledovou stránku.
- **Licenční klíč** (volitelně pro produkci) – zkušební verze omezuje velikost náhledu na 5 MB na dokument.

## Jak nastavit GroupDocs.Watermark pro Java

Pro nastavení GroupDocs.Watermark nejprve přidejte Maven repozitář a poté zahrňte knihovnu jako závislost ve vašem souboru `pom.xml`. Tím zajistíte, že Maven stáhne správné artefakty a třídy budou dostupné na classpath pro kompilaci i běh.

### Přidejte Maven závislost
Knihovna je distribuována přes Maven Central. Přidejte následující úryvek do vašeho `pom.xml` uvnitř bloku `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Tip:** Uložte číslo verze do vlastnosti (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`), abyste mohli snadno provádět aktualizace.

### Přímé stažení (alternativa)
Pokud dáváte přednost ruční instalaci, můžete stáhnout JAR z oficiální stránky vydání: [vydání GroupDocs.Watermark pro Java](https://releases.groupdocs.com/watermark/java/).

## Jak získat a použít licenci

Aplikace licence na GroupDocs.Watermark odstraňuje omezení zkušební verze a vypíná výchozí překrytí vodoznakem. Umístěte licenční soubor na známé místo a nasměrujte API na něj, nebo vložte cestu k licenci přímo do kódu před jakýmkoli dalším voláním. Po načtení všechny následující operace běží v režimu plné funkčnosti.

Můžete:

- **Požádat o bezplatnou zkušební verzi** na portálu GroupDocs – poskytne 30‑denní licenční soubor.
- **Vygenerovat dočasnou licenci** pomocí online generátoru licencí pro evaluační prostředí.
- **Zakoupit komerční licenci** pro neomezené produkční použití a prioritu podpory.

Umístěte licenční soubor (`GroupDocs.Watermark.lic`) do kořenového adresáře projektu nebo specifikujte jeho cestu programově pomocí `Watermarker.setLicense("path/to/license.file")`.

## Jak inicializovat Watermarker

Inicializujte `Watermarker` zadáním cesty ke zdrojovému dokumentu, volitelně včetně hesla pro chráněné soubory. Konstruktor ověří formát a připraví interní parsery, což vám umožní okamžitě volat metody pro náhled nebo vodoznak. Po vytvoření si můžete uchovat referenci pro opakované použití instance při více operacích, pokud je to potřeba.

Třída `Watermarker` je jádrem GroupDocs.Watermark, která načítá dokument a poskytuje operace jako vkládání vodoznaku a generování náhledů.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – absolutní nebo relativní cesta ke zdrojovému souboru.
- Konstruktor ověří formát souboru a připraví interní parsery.

> **Definice:** `Watermarker` je vstupní bod pro všechny operace zpracování dokumentů v GroupDocs.Watermark pro Java.

## Jak vytvořit proudy stránek pro generování náhledů

Vytvořte vlastní proudy stránek implementací rozhraní `ICreatePageStream`, které knihovna volá pro každou stránku, kterou vykreslí. Vaše implementace by měla vytvořit čerstvý `OutputStream` – typicky `FileOutputStream` – který ukazuje na jedinečně pojmenovaný soubor založený na čísle stránky. Tento přístup izoluje výstup každé stránky a zabraňuje překrývání dat.

Pro **java generate thumbnails** musíte poskytnout proud pro každou stránku, kam bude vykreslený obrázek zapsán. Implementujte rozhraní `ICreatePageStream`; knihovna zavolá vaši implementaci pro každou zpracovávanou stránku.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** vám umožní vložit číslo stránky přímo do názvu souboru, což usnadňuje dávkové zpracování.
- Metoda vrací nový `OutputStream` pro každou stránku, čímž zajišťuje, že předchozí stránky neovlivní následné zápisy.

> **Definice:** `ICreatePageStream` je zpětné volání, které vám umožňuje definovat, jak jsou vytvářeny výstupní proudy pro každou náhledovou stránku.

## Jak uvolnit proudy stránek po generování náhledů

Po zapsání obrázku stránky knihovna zavolá `IReleasePageStream`, aby vám umožnila uzavřít a vyčistit související výstupní proud. Implementujte toto zpětné volání pro bezpečné uvolnění souborových popisovačů, vyprázdnění bufferů a případné další logování. Správné čištění zabraňuje únikům popisovačů a zajišťuje, že následující stránky mohou být zpracovány bez rušení.

Správná údržba prostředků zabraňuje únikům souborových popisovačů a chrání JVM před vyčerpáním descriptorů. Implementujte `IReleasePageStream` pro uzavření proudů, jakmile knihovna signalizuje, že stránka je dokončena.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definice:** `IReleasePageStream` je zpětné volání, které vám umožňuje definovat vlastní logiku pro uvolnění výstupních prostředků specifických pro stránku.

## Jak generovat náhledy dokumentů (převod dokumentu na obrázek)

Generujte náhledy voláním `generatePreview()` na instanci `Watermarker` a předáním objektu `PreviewOptions`, který určuje rozlišení, formát obrázku a rozsah stránek. Metoda iteruje přes každou stránku, používá vaše tvůrce proudů k zápisu rastrového obrázku a následně uvolní proudy. Tento proces vytvoří sadu souborů obrázků představujících stránky dokumentu.

S připraveným `Watermarker`, `FeatureCreatePageStream` a `FeatureReleasePageStream` můžete spustit náhledový engine. Metoda `generatePreview()` iteruje přes každou stránku, volá vaše tvůrce proudů, zapisuje obrázek a nakonec uvolňuje proudy.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** řídí DPI; 150 DPI je dobrá rovnováha pro webové miniatury.
- **`ImageFormat`** může být PNG, JPEG, BMP nebo TIFF podle vašich následných požadavků.
- Metoda zpracovává stránky sekvenčně, takže spotřeba paměti zůstává nízká i u dokumentů se stovkami stránek.

> **Definice:** `generatePreview()` je API volání, které vykreslí každou stránku načteného dokumentu do obrázku pomocí poskytnutých proudů.

## Praktické aplikace převodu dokumentu na obrázek

Generování náhledových obrázků otevírá mnoho možností:

1. **Prohlížeče dokumentů** – Zobrazte mřížku PNG miniatur, aby uživatelé mohli rychle prolistovat velké PDF bez jejich otevírání.
2. **Ukázky ve výsledcích vyhledávání** – Připojte náhledový obrázek k položkám vyhledávacího indexu pro bohatší UI.
3. **Přílohy e‑mailů** – Vložte malý náhled přiložených PDF do těla e‑mailu.
4. **Mobilní aplikace** – Snižte šířku pásma odesíláním 200 KB PNG náhledů místo kompletních PDF.
5. **Portály pro soulad** – Vygenerujte právně požadované verze smluv s vodoznakem jako obrázky pro auditní stopy.

## Úvahy o výkonu při generování náhledů v Javě

Při hromadném zpracování mějte na paměti následující optimalizační tipy:

- **Bufferování streamu** – Zabalte `FileOutputStream` do `BufferedOutputStream`, aby se minimalizovalo I/O na disku.
- **Paralelní dávkové spouštění** – Použijte `ForkJoinPool` v Javě k souběžnému zpracování více dokumentů; každá úloha by měla vytvořit vlastní instanci `Watermarker`, aby nedocházelo k problémům s thread‑safety.
- **Omezte DPI pro miniatury** – 72–150 DPI stačí pro většinu UI scénářů; vyšší DPI rezervujte pro náhledy připravené k tisku.
- **Znovupoužití licenčních objektů** – Načtení licenčního souboru jednou na JVM snižuje režii.
- **Monitorování paměti** – Knihovna drží v paměti jen aktuální stránku. U extrémně velkých souborů zvažte mírné zvýšení heapu JVM (např. `-Xmx512m`) pro zvládnutí občasných špiček.

## Běžné úskalí a jak se jim vyhnout

| Symptom | Předpokládaná příčina | Řešení |
|---------|-----------------------|--------|
| `OutOfMemoryError` během generování náhledu | Použití `ImageFormat.Jpeg` s 300 DPI na 1000‑stránkovém PDF | Snižte DPI nebo přepněte na PNG s nižší hloubkou barev |
| Prázdné soubory náhledu | `FeatureCreatePageStream` vrací stejný `FileOutputStream` pro každou stránku | Zajistěte vytvoření nového proudu pro každé `pageNumber` |
| Náhledové obrázky jsou otočeny | PDF obsahuje metadata o rotaci, která není respektována | Zavolejte `previewOptions.setRotatePages(true)` (pokud je k dispozici) |
| Zobrazí se varování o licenci | Licenční soubor nebyl nalezen nebo je cesta nesprávná | Ověřte, že `Watermarker.setLicense("path/to/license.file")` běží před jakýmkoli jiným API voláním |

## Často kladené otázky

**Q: Mohu generovat náhledy pro PDF chráněné heslem?**  
A: Ano. Předávejte heslo konstruktoru `Watermarker`: `new Watermarker("file.pdf", "password")`.

**Q: Které formáty obrázků jsou podporovány pro výstup náhledu?**  
A: K dispozici jsou PNG, JPEG, BMP a TIFF. PNG se doporučuje pro bezztrátové miniatury.

**Q: Kolik stránek lze zpracovat v jednom volání?**  
A: Knihovna neklade žádný pevný limit; můžete generovat náhledy dokumentů s tisíci stránkami, omezené jen úložištěm a propustností I/O.

**Q: Potřebuji samostatnou licenci pro každou instanci serveru?**  
A: Jeden licenční soubor může být používán napříč více instancemi, pokud celkové využití odpovídá podmínkám licence.

**Q: Existuje způsob, jak vygenerovat jediný kombinovaný náhled (např. jen první stránku)?**  
A: Ano. Nastavte `previewOptions.setPages(new int[]{1})` pro omezení generování na první stránku.

## Závěr

Nyní máte kompletní, připravený workflow pro **convert document to image** a **java generate thumbnails** pomocí GroupDocs.Watermark. Konfigurací vlastních obslužných funkcí pro proudy stránek udržujete nízkou spotřebu paměti a laděním `PreviewOptions` řídíte kvalitu a velikost souboru. Tyto techniky vám umožní vložit rychlé, vysoce kvalitní náhledy do jakékoli Java‑aplikace – ať už jde o webový portál, desktopového klienta nebo cloud‑nativní mikroservisu.

---

**Poslední aktualizace:** 2026-09-26  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Související tutoriály

- [Jak získat informace o dokumentu pomocí GroupDocs.Watermark pro Java: Průvodce krok za krokem](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Pokročilé tutoriály funkcí vodoznakování pro GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Jak přidat obrázkový vodoznak v Javě pomocí GroupDocs.Watermark: Průvodce krok za krokem](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)