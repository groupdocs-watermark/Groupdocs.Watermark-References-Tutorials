---
date: '2025-12-19'
description: Naučte se, jak pomocí GroupDocs Watermark Maven spravovat vodoznaky v
  diagramových souborech, jako je .vsdx, s využitím Javy, čímž zvýšíte integritu dokumentů
  a ochráníte duševní vlastnictví.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Správa vodoznaků diagramů v Javě
type: docs
url: /cs/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Správa vodoznaků diagramů v Javě

Správa vodoznaků v dokumentech je nezbytná pro ochranu duševního vlastnictví a zachování integrity dokumentu. **V tomto tutoriálu vám ukážeme, jak použít groupdocs watermark maven k efektivnímu načtení, vyhledání a odstranění vodoznaků ze souborů diagramů, jako je `.vsdx`**. Ať už vytváříte podnikovou software nebo automatizujete pracovní postupy s dokumenty, zvládnutí těchto technik vám poskytne plnou kontrolu nad správou vodoznaků diagramů.

## Rychlé odpovědi
- **Jaká knihovna je potřeba?** GroupDocs.Watermark for Java (k dispozici přes Maven).  
- **Jaké formáty diagramů jsou podporovány?** `.vsdx`, `.vdx` a další formáty Visio.  
- **Mohu vyhledávat jak textové, tak obrazové vodoznaky?** Ano – kombinujte kritéria vyhledávání pomocí `or()`.  
- **Je pro produkci vyžadována licence?** Je vyžadována platná licence GroupDocs.Watermark.  
- **Jak to integrovat do Maven?** Přidejte úložiště a závislost uvedenou níže.

## Co je groupdocs watermark maven?
`groupdocs watermark maven` označuje integraci založenou na Maven pro knihovnu GroupDocs.Watermark pro Java. Deklarací knihovny ve vašem `pom.xml` Maven automaticky vyřeší všechny potřebné binární soubory, což vám umožní soustředit se na kód, který načítá diagramy, vyhledává vodoznaky a odstraňuje je programově.

## Proč použít GroupDocs.Watermark pro správu vodoznaků diagramů?
- **Plnohodnotné API** – podporuje textové, obrazové a tvarové vodoznaky napříč mnoha typy diagramů.  
- **Přesné odstranění** – eliminuje vodoznaky bez poškození původního rozvržení diagramu.  
- **Škálovatelné** – vhodné pro dávkové zpracování velkých kolekcí diagramů.  
- **Maven‑přátelské** – jednoduchá správa závislostí, udržuje projekt čistý.

## Předpoklady
1. **Java Development Kit (JDK) 8+** – zajišťuje kompatibilitu s knihovnou.  
2. **IDE** – IntelliJ IDEA, Eclipse nebo jakýkoli editor kompatibilní s Javou.  
3. **GroupDocs.Watermark for Java** – přidáno přes Maven (doporučeno) nebo přímé stažení JAR.  

### Požadované knihovny a závislosti
#### Nastavení Maven
Add the following configuration to your `pom.xml` file:

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

#### Přímé stažení
Alternativně stáhněte nejnovější verzi z [vydání GroupDocs.Watermark pro Java](https://releases.groupdocs.com/watermark/java/).

### Získání licence
- **Bezplatná zkušební verze:** Otestujte knihovnu s trial licencí.  
- **Dočasná licence:** Požádejte o krátkodobý klíč pro hodnocení.  
- **Koupě:** Získejte produkční licenci pro neomezené používání.

## Použití groupdocs watermark maven k načtení diagramového dokumentu
Načtení diagramového dokumentu je prvním krokem před jakoukoliv operací s vodoznakem. Níže je minimální příklad, který vytváří instanci `Watermarker` s `DiagramLoadOptions`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

- **Parametry:**  
  - `inputFilePath` – cesta k vašemu souboru `.vsdx`.  
  - `loadOptions` – umožňuje kontrolovat, jak je diagram parsován (např. ochrana heslem).

## Vyhledávání vodoznaků pomocí groupdocs watermark maven
### Textové vodoznaky
Pro nalezení textových vodoznaků definujte `TextSearchCriteria` a dotazujte první stránku diagramu.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

- **Klíčové metody:**  
  - `TextSearchCriteria` – určuje přesný text, který hledáte.  
  - `PossibleWatermarkCollection` – ukládá nalezené shody.

### Obrazové vodoznaky
Pokud váš diagram obsahuje logo nebo obrázkové vodoznaky, použijte `ImageDctHashSearchCriteria` pro porovnání s referenčním obrázkem.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

- **Klíčové metody:**  
  - `ImageDctHashSearchCriteria` – vytváří percepční hash referenčního obrázku pro robustní porovnání.

## Odstraňování vodoznaků
Jakmile identifikujete nechtěné vodoznaky, můžete je vymazat a uložit čistou kopii diagramu.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

- **Klíčová metoda:** `clear()` odstraňuje každý vodoznak nalezený kombinovanými kritérii a ponechává diagram neporušený.

## Praktické aplikace
1. **Integrace podnikového softwaru** – Vložte správu vodoznaků do obchodních aplikací pro ochranu proprietárních diagramů.  
2. **Systémy pro správu obsahu (CMS)** – Automatizujte detekci a odstraňování neautorizovaných log a před publikací.  
3. **Pracovní postupy právních dokumentů** – Přidávejte nebo odstraňujte vodoznaky v různých fázích zpracování smluv.  

## Časté problémy a řešení
- **Chyby licence:** Ujistěte se, že soubor licence je správně odkazován před vytvořením `Watermarker`.  
- **Velké soubory:** Použijte streaming API nebo zvýšte velikost haldy JVM (`-Xmx2g`) pro diagramy > 100 MB.  
- **Chybějící vodoznaky:** Ověřte, že kritéria vyhledávání (rozlišování velikosti písmen, práh podobnosti obrázku) odpovídají skutečnému obsahu vodoznaku.

## Často kladené otázky

**Q: Mohu vyhledávat současně text i obrázky?**  
A: Ano. Kombinujte kritéria pomocí `or()` jak je ukázáno v příkladu odstraňování.

**Q: Je bezpečné odstraňovat vodoznaky bez změny rozvržení diagramu?**  
A: Rozhodně. API přesně cílí na objekty vodoznaku a zachovává všechny ostatní prvky diagramu.

**Q: Jaké formáty diagramů GroupDocs.Watermark podporuje?**  
A: Podporuje formáty Visio jako `.vsdx`, `.vdx` a také další vektorové typy diagramů.

**Q: Jak mohu efektivně zpracovat stovky diagramů?**  
A: Implementujte dávkový cyklus, opakovaně používejte jednu instanci `Watermarker`, pokud je to možné, a zvažte paralelní zpracování pomocí `ExecutorService` v Javě.

**Q: Mohu integrovat detekci vodoznaků do CI/CD pipeline?**  
A: Ano. Zahrňte Java úryvky do svých skriptů pro sestavení (např. Maven pluginy nebo Gradle úlohy) pro validaci diagramů před nasazením.

## Závěr
Využitím **groupdocs watermark maven** získáte výkonný, Maven‑spravovaný způsob, jak načítat, vyhledávat a odstraňovat vodoznaky z diagramových souborů pomocí Javy. Tato schopnost posiluje zabezpečení dokumentů, zjednodušuje pracovní postupy s obsahem a snadno škáluje napříč velkými kolekcemi dokumentů.

---

**Poslední aktualizace:** 2025-12-19  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs