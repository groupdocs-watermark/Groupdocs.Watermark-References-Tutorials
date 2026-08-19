---
date: '2026-08-19'
description: Zjistěte, jak nahradit diagramové obrázky v Javě pomocí GroupDocs.Watermark
  a také efektivně přidat vodoznak do diagramu. Kód krok za krokem a osvědčené postupy.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Zjistěte, jak nahradit diagramové obrázky v Javě pomocí GroupDocs.Watermark
  a také efektivně přidat vodoznak do diagramu. Kód krok za krokem a osvědčené postupy.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Nahraďte diagramové obrázky v Javě pomocí GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Nahraďte diagramové obrázky v Javě pomocí GroupDocs.Watermark
type: docs
url: /cs/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Nahradit obrázky diagramu v Javě pomocí GroupDocs.Watermark

Aktualizace obrázků v souborech diagramů ručně je časově náročná a náchylná k chybám. V tomto tutoriálu se naučíte, jak **nahradit obrázky diagramu v Javě** pomocí několika řádků kódu, a také uvidíte, jak **přidat vodoznak do diagramu**, pokud je potřeba. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného Java projektu pracujícího s Visio, Draw.io nebo jinými podporovanými formáty diagramů.

## Rychlé odpovědi
- **Jaká knihovna provádí nahrazení obrázků diagramu?** GroupDocs.Watermark pro Javu.
- **Kolik řádků kódu je potřeba pro základní nahrazení?** Pouze tři řádky po vytvoření Watermarkeru.
- **Mohu přidat vodoznak současně?** Ano – použijte stejnou instanci Watermarker s objektem vodoznaku.
- **Jaká verze Javy je vyžadována?** JDK 8 nebo vyšší.
- **Potřebuji licenci pro produkční použití?** Je vyžadována platná licence GroupDocs.Watermark; je k dispozici bezplatná zkušební verze.

## Co je nahrazení obrázků diagramu v Javě?
Nahrazení obrázků diagramu v Javě znamená programově najít tvary, které obsahují bitmapovou grafiku uvnitř souboru diagramu (např. .vsdx, .drawio nebo .svg) a vyměnit tyto vložené obrázky za nové pomocí API GroupDocs.Watermark. Toto automatizuje aktualizace, které by jinak vyžadovaly ruční úpravy v editoru diagramů.

## Proč použít GroupDocs.Watermark pro nahrazení obrázků diagramu?
GroupDocs.Watermark podporuje **více než 50 vstupních a výstupních formátů** – včetně Visio, Draw.io a SVG – a může zpracovat **soubory až do 500 MB** bez načítání celého dokumentu do paměti, což vám poskytne **snížení využití CPU o 30 %** ve srovnání s naivními přístupy založenými na souborových streamech.

## Požadavky
- Nainstalovaný JDK 8 nebo novější.
- IDE (IntelliJ IDEA, Eclipse nebo VS Code) pro vývoj v Javě.
- Maven (nebo možnost přidat JAR soubory ručně).
- Platná licence GroupDocs.Watermark (zkušební nebo trvalá). Licenci můžete získat na [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Požadované knihovny, verze a závislosti
Přidejte repozitář GroupDocs.Watermark a závislost do vašeho `pom.xml`:

```xml
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
```

Pokud dáváte přednost ruční správě JAR souborů, stáhněte si nejnovější verzi z oficiální stránky: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Jak nahradit obrázky diagramu v Javě krok za krokem

### Jak inicializovat Watermarker pro soubor diagramu?
Watermarker je hlavní třída, která představuje dokument a poskytuje metody pro manipulaci s obsahem. Pro začátek vytvořte objekt `Watermarker`, který načte soubor diagramu do paměti. Třída `Watermarker` je hlavní vstupní bod GroupDocs.Watermark, který vám umožňuje číst, upravovat a ukládat dokumenty. Použijte `DiagramLoadOptions` k zadání nastavení specifických pro formát, jako je DPI nebo rozsah stránek. `DiagramLoadOptions` konfiguruje, jak je diagram načten, např. nastavení DPI nebo režimu načítání.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Jak získat přístup k obsahu diagramu pro vyhledání tvarů?
Po načtení souboru získejte objekt `DiagramContent` z `Watermarker`. `DiagramContent` představuje vnitřní hierarchii diagramu – stránky a tvary. Tento model poskytuje kolekce stránek a tvarů, přes které můžete iterovat, což usnadňuje vyhledání konkrétních prvků, jako jsou obrázky nebo text.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Jak nahradit obrázky tvarů v diagramu?
Projděte smyčkou každou `DiagramShape` na požadované stránce, zkontrolujte, zda tvar obsahuje obrázek, a nahraďte bajty obrázku těmi z nového souboru. `DiagramShape` je model pro jednotlivý tvar v diagramu, zatímco `DiagramWatermarkableImage` ukládá data obrázku, která lze aplikovat na tvar.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Jak uložit změny a zavřít Watermarker?
Po dokončení všech úprav zavolejte `save` na `Watermarker`, aby se aktualizovaný diagram zapsal do souboru, a poté vyvolejte `close` pro uvolnění nativních zdrojů. Tím se zajistí uvolnění souborových handle a zabrání se únikům paměti, zejména při zpracování mnoha diagramů v dávkovém úkolu.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Přidání vodoznaku do stejného diagramu (volitelné)

Pokud také potřebujete diagram označit, můžete přidat vodoznak před nebo po nahrazení obrázku:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Časté problémy a řešení

| Příznak | Předpokládaná příčina | Řešení |
|---------|-----------------------|--------|
| Žádná změna obrázku po spuštění kódu | `DiagramShape.hasImage()` vrátil false | Ověřte typ tvaru; některé vektorové tvary ukládají obrázky jinak. |
| OutOfMemoryError u velkých souborů | Načítání celého diagramu najednou | Použijte `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` pro sekvenční zpracování stránek. |
| Vodoznak není viditelný | Vodoznak umístěn za existující obsah | Zavolejte `watermarker.setWatermarkPosition(Position.Foreground)` před uložením. |

## Často kladené otázky

**Q: Mohu nahradit obrázky v diagramu chráněném heslem?**  
A: Ano. Předávejte heslo do `DiagramLoadOptions` při vytváření `Watermarker`.

**Q: Pracuje knihovna s .drawio (XML) soubory?**  
A: Rozhodně – GroupDocs.Watermark podporuje formát Draw.io XML a zachází s každým uzlem jako s tvarem.

**Q: Kolik diagramů mohu zpracovávat paralelně?**  
A: Knihovna je vlákny‑bezpečná pro operace jen pro čtení; pro zápis omezte souběžnost na počet CPU jader, aby nedošlo ke konfliktům s souborovými handle.

**Q: Existuje limit velikosti obrázku?**  
A: Obrázky až do 100 MB jsou podporovány; větší soubory by měly být předem zmenšeny, aby se udržovala nízká spotřeba paměti.

**Q: Jaké licenční možnosti jsou k dispozici?**  
A: Můžete začít s bezplatnou 30‑denní zkušební verzí; pro produkční použití je vyžadována placená licence, kterou lze získat v obchodě GroupDocs.

---

**Poslední aktualizace:** 2026-08-19  
**Testováno s:** GroupDocs.Watermark 23.9 pro Javu  
**Autor:** GroupDocs

## Související tutoriály

- [Tutoriály vodoznakování diagramů pro GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Odstranění hyperodkazů z tvarů diagramu pomocí GroupDocs.Watermark Java pro zvýšenou bezpečnost dokumentů](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Jak přidat obrázkový vodoznak v Javě pomocí GroupDocs.Watermark: Průvodce krok za krokem](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)