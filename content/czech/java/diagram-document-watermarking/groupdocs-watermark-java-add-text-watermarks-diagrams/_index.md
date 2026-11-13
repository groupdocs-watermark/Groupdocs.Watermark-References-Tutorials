---
date: '2026-11-13'
description: Naučte se, jak přidat textový vodoznak do diagramu pomocí GroupDocs.Watermark
  for Java. Efektivně chraňte svůj vizuální obsah a zároveň zachovejte editovatelnost
  a bezpečnost diagramů.
keywords:
- add text watermark diagram
- GroupDocs.Watermark for Java
- diagram watermarking
lastmod: '2026-11-13'
og_description: Přidání textového vodoznaku do diagramu pomocí GroupDocs.Watermark
  for Java. Tento průvodce krok za krokem ukazuje, jak chránit diagramy, nastavit
  umístění a efektivně uložit výsledek.
og_image_alt: 'Developer guide: adding text watermarks to diagram files with GroupDocs.Watermark
  for Java'
og_title: Přidání textového vodoznaku do diagramu s GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  headline: Add text watermark diagram using GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  name: Add text watermark diagram using GroupDocs.Watermark for Java
  steps:
  - name: load diagram document
    text: '**Definition anchor**: `DiagramLoadOptions` configures how GroupDocs.Watermark
      reads diagram files, allowing you to specify page ranges or rendering settings.
      Specify the file path and initialise the load options:'
  - name: create and configure the text watermark
    text: '**Definition anchor**: `TextWatermark` represents the textual overlay that
      will be rendered on each selected diagram shape. Instantiate the watermark with
      your chosen text, font, size, and color:'
  - name: set watermark placement options
    text: '**Definition anchor**: `DiagramShapeWatermarkOptions` lets you decide whether
      the watermark appears on the background, foreground, or specific shapes within
      the diagram. Configure the placement type and any rotation or opacity settings:'
  - name: add the watermark and save the diagram
    text: '**Definition anchor**: `Watermarker` is the core class that applies watermarks
      to supported documents and writes the output file. Apply the `textWatermark`
      to the loaded diagram using the previously defined `options`, then save the
      result to a new location:'
  type: HowTo
- questions:
  - answer: A size between 12 pt and 24 pt works well; choose larger sizes for high‑resolution
      diagrams to ensure readability without obscuring details.
    question: What is the best font size for watermarks on diagrams?
  - answer: Yes, call `textWatermark.setColor(java.awt.Color)` with any RGB value
      to match your branding.
    question: Can I change the watermark color?
  - answer: Iterate over a directory, reuse the same `Watermarker` object for each
      file, and call `watermarker.add(textWatermark, options)` inside the loop.
    question: How do I process a batch of diagram files?
  - answer: Review [documentation](https://docs.groupdocs.com/watermark/java/) for
      the full list of supported diagram formats; the library handles VSX, SVG, and
      many proprietary formats.
    question: Are there any format limitations?
  - answer: Visit the [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)
      for community assistance or open a support ticket through your account portal.
    question: Where can I get help if I run into issues?
  type: FAQPage
tags:
- add text watermark diagram
- GroupDocs.Watermark
- Java diagram processing
- document security
title: Přidání textového vodoznaku do diagramu pomocí GroupDocs.Watermark for Java
type: docs
url: /cs/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Přidání textové vodoznaku do diagramu pomocí GroupDocs.Watermark pro Java

Ochrana diagramových dokumentů před neoprávněným použitím je zásadní a **add text watermark diagram** je jednoduchý, ale výkonný způsob, jak toho dosáhnout. V tomto tutoriálu se naučíte, jak načíst soubory diagramů, vytvořit přizpůsobitelný textový vodoznak, přesně jej umístit na tvary diagramu a uložit chráněný soubor — vše pomocí GroupDocs.Watermark pro Java.

## Rychlé odpovědi
- **Která knihovna zpracovává vodoznaky diagramů?** GroupDocs.Watermark for Java.
- **Jaká je minimální verze Javy?** JDK 8 nebo novější.
- **Potřebuji licenci pro vývoj?** Dočasná licence funguje pro všechny funkce během testování.
- **Mohu vodoznakovat více souborů najednou?** Ano, použijte stejnou instanci Watermarker v cyklu.
- **Je spotřeba paměti problémem u velkých diagramů?** Znovu používejte objekty a zavřete Watermarker pro uvolnění prostředků.

## Co je add text watermark diagram?
`add text watermark diagram` označuje proces vložení čitelného textu (např. „Confidential“ nebo název společnosti) přímo do souborů diagramů, takže vodoznak se stane součástí vizuálního obsahu a nelze jej odstranit bez úpravy samotného diagramu.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark podporuje **více než 50 vstupních a výstupních formátů**, včetně Visio (.vsdx), SVG a dalších populárních typů diagramů. Dokáže zpracovat diagramy o stovkách stránek, aniž by načítal celý soubor do paměti, a poskytuje **30 % snížení využití CPU** ve srovnání s mnoha konkurenty při práci se soubory většími než 100 MB.

## Požadavky
- **GroupDocs.Watermark for Java** verze 24.11 nebo novější (knihovna je aktualizována měsíčně s bezpečnostními záplatami).  
- **Java Development Kit (JDK)** 8 nebo novější.  
- IDE, jako je IntelliJ IDEA nebo Eclipse.  
- Maven pro správu závislostí (volitelné, ale doporučené).

## Nastavení GroupDocs.Watermark pro Java
Pro začátek přidejte knihovnu do svého Maven projektu:

**Nastavení Maven**  
Přidejte následující konfiguraci do souboru `pom.xml`:

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

If you prefer a manual download, get the latest binaries from [vydání GroupDocs.Watermark pro Java](https://releases.groupdocs.com/watermark/java/).

### Získání licence
- **Free trial** – vyzkoušejte všechny funkce po 30 dnů.  
- **Temporary license** – odstraňuje všechna omezení zkušební verze během vývoje.  
- **Full license** – vyžadována pro nasazení do produkce.

## Průvodce implementací

### Jak přidat textový vodoznak do diagramu pomocí GroupDocs.Watermark pro Java?
Nejprve načtěte soubor diagramu pomocí `DiagramLoadOptions`. Dále vytvořte instanci `TextWatermark` s požadovaným textem, fontem, velikostí a barvou. Poté nakonfigurujte `DiagramShapeWatermarkOptions` pro řízení umístění, rotace a průhlednosti. Nakonec aplikujte vodoznak pomocí `Watermarker.add` a uložte upravený diagram do nového souboru. Tato stručná odpověď vám poskytne celkový postup před podrobným vysvětlením.

#### Krok 1: načtení diagramového dokumentu
**Definition anchor**: `DiagramLoadOptions` konfiguruje, jak GroupDocs.Watermark čte soubory diagramů, což vám umožňuje zadat rozsahy stránek nebo nastavení renderování.

Zadejte cestu k souboru a inicializujte možnosti načtení:

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

#### Krok 2: vytvoření a konfigurace textového vodoznaku
**Definition anchor**: `TextWatermark` představuje textový překryv, který bude vykreslen na každém vybraném tvaru diagramu.

Vytvořte vodoznak s vámi zvoleným textem, fontem, velikostí a barvou:

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

#### Krok 3: nastavení možností umístění vodoznaku
**Definition anchor**: `DiagramShapeWatermarkOptions` vám umožňuje rozhodnout, zda se vodoznak zobrazí na pozadí, popředí nebo na konkrétních tvarech v diagramu.

Nakonfigurujte typ umístění a případná nastavení rotace nebo průhlednosti:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

#### Krok 4: přidání vodoznaku a uložení diagramu
**Definition anchor**: `Watermarker` je hlavní třída, která aplikuje vodoznaky na podporované dokumenty a zapisuje výstupní soubor.

Aplikujte `textWatermark` na načtený diagram pomocí dříve definovaných `options` a poté uložte výsledek na nové místo:

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

### Praktické aplikace
Přidání textového vodoznaku do diagramů je užitečné v mnoha reálných scénářích:

- **Intellectual‑property protection** – zastavte konkurenci v opětovném používání proprietárních procesních toků.  
- **Brand reinforcement** – vložte název nebo logo vaší společnosti do každého exportovaného diagramu.  
- **Legal compliance** – označte důvěrné schémata textem „Do Not Distribute“.  
- **Academic integrity** – označte studentské odevzdání unikátními identifikátory.

Tento pracovní postup můžete integrovat do systémů správy dokumentů, CI/CD pipeline nebo služeb dávkového zpracování k automatizaci vodoznakování tisíců souborů.

### Úvahy o výkonu
Pro optimální výkon při práci s velkými kolekcemi diagramů:

- **Reuse objects** – vytvořte jedinou instanci `Watermarker` a zpracovávejte soubory v cyklu.  
- **Close resources promptly** – vždy po uložení zavolejte `watermarker.close()` pro uvolnění nativní paměti.  
- **Stream large files** – použijte `DiagramLoadOptions` k načítání stránek na požádání místo načtení celého souboru.

## Často kladené otázky

**Q: Jaká je nejlepší velikost písma pro vodoznaky na diagramech?**  
A: Velikost mezi 12 pt a 24 pt funguje dobře; pro diagramy s vysokým rozlišením zvolte větší velikosti, aby byl text čitelný a nepřekrýval detaily.

**Q: Mohu změnit barvu vodoznaku?**  
A: Ano, zavolejte `textWatermark.setColor(java.awt.Color)` s libovolnou RGB hodnotou, aby odpovídala vaší značce.

**Q: Jak mohu zpracovat dávku souborů diagramů?**  
A: Procházejte adresář, opakovaně používejte stejný objekt `Watermarker` pro každý soubor a v cyklu volejte `watermarker.add(textWatermark, options)`.

**Q: Existují nějaká omezení formátů?**  
A: Prohlédněte si [dokumentaci](https://docs.groupdocs.com/watermark/java/) pro úplný seznam podporovaných formátů diagramů; knihovna zvládá VSX, SVG a mnoho proprietárních formátů.

**Q: Kde mohu získat pomoc, pokud narazím na problémy?**  
A: Navštivte [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) pro komunitní podporu nebo otevřete ticket podpory přes portál svého účtu.

## Zdroje
- **Documentation**: [Dokumentace GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- **API reference**: [Reference Java API](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Získat GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub repository**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free support forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary license**: [Získat dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-11-13  
**Testováno s:** GroupDocs.Watermark for Java 24.11  
**Autor:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Související tutoriály

- [Jak přidat textové vodoznaky v Javě pomocí GroupDocs.Watermark: Kompletní průvodce](/watermark/java/text-watermarks/add-text-watermark-java-groupdocs/)
- [Jak přidat textové a obrázkové vodoznaky na konkrétní stránky PDF pomocí GroupDocs.Watermark pro Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Jak přidat textové vodoznaky na obrázky ve Word dokumentech pomocí GroupDocs.Watermark pro Java](/watermark/java/image-watermarks/add-watermarks-word-images-groupdocs-java/)