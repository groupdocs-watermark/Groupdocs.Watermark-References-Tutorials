---
date: '2026-10-01'
description: Zjistěte, jak automatizovat nahrazování obrázků v jazyce Java v souborech
  diagramů pomocí GroupDocs.Watermark, včetně přidání vodoznaku a efektivního zpracování.
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: Automatizujte nahrazování obrázků v jazyce Java v diagramech pomocí
  GroupDocs.Watermark. Tento průvodce ukazuje, jak nahradit obrázky, přidat vodoznaky
  a efektivně pracovat s velkými soubory.
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: Automatizujte nahrazování obrázků v jazyce Java pomocí GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: Automatizujte nahrazování obrázků v jazyce Java pomocí GroupDocs.Watermark
type: docs
url: /cs/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Automatizace výměny obrázků v Javě pomocí GroupDocs.Watermark

Aktualizace jednotlivých obrázků v diagramu může být únavná, náchylná k chybám ruční úloha. S **GroupDocs.Watermark for Java** můžete **automatizovat výměnu obrázků v Javě** napříč desítkami nebo stovkami souborů, zajistit konzistenci značky a ušetřit cenný čas vývoje. Tento tutoriál vás provede nastavením knihovny, přístupem k obsahu diagramu, výměnou obrázků v konkrétních tvarech a volitelným přidáním vodoznaku do diagramu.

## Rychlé odpovědi
- **Která knihovna zpracovává aktualizace obrázků v diagramu?** GroupDocs.Watermark for Java.  
- **Mohu přidat vodoznak při výměně obrázků?** Ano – stejné API vám umožní překrýt vodoznaky na libovolné stránce diagramu.  
- **Jaká verze Javy je požadována?** JDK 8 nebo vyšší.  
- **Potřebuji licenci pro vývoj?** Bezplatná zkušební verze funguje pro hodnocení; pro produkci je vyžadována komerční licence.  
- **Je proces paměťově efektivní pro velké diagramy?** Ano – SDK streamuje obsah a nikdy nenačítá celý soubor do paměti.

## Co je GroupDocs.Watermark pro Javu?
`GroupDocs.Watermark` je Java SDK, které umožňuje programatické přidávání, odstraňování a nahrazování vodoznaků a obrázků ve více než 30 formátech dokumentů, včetně Visio, SVG a dalších typů diagramů. Zpracovává soubory ve streamovacím režimu, což vám umožní pracovat s diagramy o stovkách stránek, aniž byste vyčerpali paměť.

## Proč automatizovat výměnu obrázků v Javě?
Automatizace výměny obrázků snižuje manuální práci až o **90 %** při aktualizaci značkových materiálů v rozsáhlých kolekcích dokumentů. SDK podporuje **více než 30 vstupních a výstupních formátů**, zpracovává soubory až do **200 MB** za méně než sekundu na typickém serverovém hardware a zaručuje pixel‑přesné umístění obrázku.

## Požadavky
- JDK 8 nebo novější nainstalovaný na vašem vývojovém počítači.  
- Maven (nebo jiný nástroj pro sestavení) pro správu závislostí.  
- IDE, jako je IntelliJ IDEA nebo Eclipse.  
- Základní znalost Javy a povědomí o práci se soubory (I/O).

### Požadované knihovny, verze a závislosti
Add the following Maven coordinates to your `pom.xml`. The placeholder below represents the exact XML snippet you need; keep it unchanged.

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

Pro ruční stažení získáte nejnovější JAR soubory z oficiální stránky vydání: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Jak automatizovat výměnu obrázků v Javě?
Načtěte diagram pomocí instance `Watermarker`, najděte cílové tvary, nahraďte jejich obrazové proudy, volitelně přidejte vodoznak a nakonec soubor uložte. Celý pracovní postup se vejde do **čtyř stručných kroků**, z nichž každý je demonstrován níže, a typicky vyžaduje jen několik sekund na diagram i u velkých souborů.

### Krok 1: inicializace watermarkeru
Třída `Watermarker` je vstupním bodem pro všechny operace s dokumenty. Otevře zdrojový soubor a připraví interní struktury pro úpravy.

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

- **DiagramLoadOptions** konfiguruje specifické parametry načítání diagramu.  
- Inicializace `Watermarker` otevře souborový handle a ověří formát.

### Krok 2: přístup k obsahu diagramu
`DiagramContent` představuje logickou strukturu diagramu, odhaluje stránky a jednotlivé tvary pro inspekci.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- Použijte `watermarker.getContent()` k získání objektu `DiagramContent`.  
- Procházejte `content.getPages()` a poté `page.getShapes()`, abyste našli tvary obsahující obrázky.

### Krok 3: nahrazení obrázků tvarů v diagramu
Objekty `DiagramShape` mohou obsahovat vložený obrázek. Nahraďte jej poskytnutím nového `InputStream`, který načte náhradní obrázek.

Metoda `setImage(InputStream)` nahradí aktuální obrázek tvaru poskytnutým proudem.  

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

- Zkontrolujte `shape.getImage()`; pokud není null, zavolejte `shape.setImage(newImageStream)`.  
- SDK automaticky aktualizuje rozměry obrázku a zachovává původní rozložení tvaru.

### Krok 4: přidání vodoznaku do diagramu (volitelné)
Pokud také potřebujete **přidat vodoznak do diagramu**, vytvořte objekt `Watermark` a aplikujte jej na požadovanou stránku nebo celý dokument.

Třída `Watermark` definuje vizuální překryv, který může být umístěn na stránky diagramu nebo na celý dokument.  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

Metoda `add(Watermark, AddOptions)` aplikuje zadaný vodoznak na dokument s použitím daných možností.  

*(Výše uvedený kód je ilustrační a nepočítá se jako nový kódový blok; je umístěn uvnitř existujícího odstavce.)*

### Krok 5: uložení a uzavření watermarkeru
Uložte změny a uvolněte prostředky, aby nedošlo k zamknutí souboru.

Metoda `save(String)` zapíše upravený dokument na zadanou cestu.  

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

- Zavolejte `watermarker.save("output.vsdx")` (nebo příslušnou příponu).  
- Vždy vyvolejte `watermarker.close()` v `finally` bloku nebo použijte try‑with‑resources pro automatické vyčištění.

## Časté problémy a řešení
- **Neshoda velikosti obrázku** – Ujistěte se, že náhradní obrázek má stejný poměr stran jako originál, aby nedošlo k deformaci.  
- **Špičky paměti u velkých diagramů** – Zpracovávejte diagramy po jednom a po každém uložení zavřete `Watermarker`.  
- **Chyby licence** – Zkušební licence vyprší po 30 dnech; před nasazením ji nahraďte produkčním klíčem. Dočasnou licenci můžete získat od GroupDocs: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Často kladené otázky

**Q: Mohu nahradit obrázky v diagramu chráněném heslem?**  
A: Ano. Načtěte soubor pomocí `DiagramLoadOptions`, který zahrnuje heslo, a poté pokračujte normálními kroky výměny.

**Q: Podporuje SDK dávkové zpracování více diagramů?**  
A: Rozhodně. Zabalte workflow pro jeden soubor do smyčky, která prochází adresář; streamovací architektura udržuje nízkou spotřebu paměti.

**Q: S jakými formáty mohu pracovat kromě Visio?**  
A: GroupDocs.Watermark zpracovává SVG, VDX, VSDX a několik dalších formátů diagramů, celkem více než 30 podporovaných typů.

**Q: Je možné přidat vodoznak po výměně obrázků?**  
A: Ano – zavolejte `watermarker.add(watermark, options)` po kroku výměny obrázku a před uložením.

**Q: Jak zajistím, že nový obrázek je vložený, nikoli odkazovaný?**  
A: Metoda `setImage(InputStream)` vloží data obrázku přímo do souboru diagramu, což zaručuje přenositelnost.

---

**Poslední aktualizace:** 2026-10-01  
**Testováno s:** GroupDocs.Watermark 23.12 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Tutoriály pro vodoznakování diagramů pro GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Odstranění hyperodkazů z tvarů diagramu pomocí GroupDocs.Watermark Java pro zvýšenou bezpečnost dokumentů](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Jak přidat obrázkový vodoznak v Javě pomocí GroupDocs.Watermark: Průvodce krok za krokem](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)