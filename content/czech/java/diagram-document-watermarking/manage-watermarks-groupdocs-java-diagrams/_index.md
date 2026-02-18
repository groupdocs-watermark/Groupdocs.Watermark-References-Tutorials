---
date: '2026-02-18'
description: Naučte se, jak přidat vodoznak a jak odstranit vodoznak v diagramových
  souborech, jako je .vsdx, pomocí GroupDocs.Watermark pro Javu. Chraňte integritu
  dokumentu pomocí GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Jak přidat vodoznak do diagramů pomocí GroupDocs.Watermark pro Javu
type: docs
url: /cs/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Jak přidat vodoznak do diagramů pomocí GroupDocs.Watermark pro Java

Správa vodoznaků v souborech diagramů je základní součástí ochrany duševního vlastnictví a udržování dokumentů čistých pro veřejné šíření. V tomto průvodci se naučíte **jak přidat vodoznak** do diagramu Visio, stejně jako **jak odstranit vodoznak**, když již není potřeba, a to vše pomocí knihovny **groupdocs watermark java**. Ať už budujete podnikové řešení pro zpracování dokumentů nebo rychlý utilitní skript, tyto kroky vám poskytnou plnou kontrolu nad vodoznakováním diagramů.

## Quick Answers
- **Jaká knihovna zpracovává vodoznaky diagramů v Javě?** GroupDocs.Watermark for Java.  
- **Mohu přidávat a odstraňovat vodoznaky ve stejném běhu?** Ano – načtěte diagram jednou a aplikujte jak operaci přidání, tak odstraňování.  
- **Které formáty souborů jsou podporovány?** Formáty Visio jako `.vsdx`, `.vdx` a další typy diagramů.  
- **Potřebuji licenci?** Zkušební licence funguje pro vývoj; plná licence je vyžadována pro produkci.  
- **Jaká verze Javy je vyžadována?** JDK 8 nebo vyšší.

## Co znamená „jak přidat vodoznak“ v kontextu diagramů?
Přidání vodoznaku znamená vložení viditelného nebo neviditelného značky — textu, loga nebo obrázku — do souboru diagramu. Tato značka cestuje se souborem, což usnadňuje prokázání vlastnictví nebo označení návrhových verzí.

## Proč použít GroupDocs.Watermark pro Java?
* **Rich API** – Vyhledávejte, přidávejte a odstraňujte textové i obrazové vodoznaky pomocí několika řádků kódu.  
* **Cross‑format support** – Funguje s Visio (`.vsdx`, `.vdx`) a mnoha dalšími typy diagramů.  
* **Performance‑focused** – Načítá pouze části diagramu potřebné pro operace s vodoznaky, čímž udržuje nízkou spotřebu paměti.

## Prerequisites
1. **Java Development Kit (JDK) 8+** – Ujistěte se, že `java -version` hlásí 1.8 nebo novější.  
2. **IDE** – IntelliJ IDEA, Eclipse nebo jakýkoli editor, který preferujete.  
3. **GroupDocs.Watermark for Java** – Přidejte ji do svého projektu pomocí Maven nebo přímého stažení JAR.

### Required Libraries and Dependencies
Přidejte repozitář a závislost do svého `pom.xml`:

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

*Pokud nechcete používat Maven, můžete stáhnout nejnovější JAR z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Získání licence
- **Free Trial:** Otestujte všechny funkce bez licenčního klíče.  
- **Temporary License:** Požádejte o časově omezený klíč pro hodnocení.  
- **Full License:** Zakupte předplatné pro neomezené používání v produkci.

## Nastavení GroupDocs.Watermark pro Java
1. **Add the library** do svého projektu (Maven nebo manuální JAR).  
2. **Create a `Watermarker` instance** – tento objekt je vstupním bodem pro načítání diagramů, vyhledávání, přidávání a odstraňování vodoznaků.

## Průvodce implementací

### Loading a Diagram Document
Načítání je první krok, než můžete **add watermark** nebo **remove watermark**. Níže uvedený kód ukazuje, jak otevřít soubor `.vsdx` s vlastními možnostmi načítání.

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

### Searching for Text Watermarks
Než přidáte nový vodoznak, možná budete chtít ověřit, zda již textový vodoznak existuje. Tento úryvek vyhledává frázi „Company Name“.

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

### Searching for Image Watermarks
Pokud potřebujete najít logo nebo jakýkoli obrázek, který byl použit jako vodoznak, použijte `ImageDctHashSearchCriteria`. To je užitečné, když chcete **remove watermark**, který odpovídá známému logu.

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

### Removing Watermarks
Jakmile identifikujete vodoznaky – textové, obrázkové nebo oba – můžete je z diagramu odstranit. Níže uvedený příklad demonstruje kombinovanou operaci odstraňování.

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

## Praktické aplikace
1. **Enterprise Software Integration** – Vložte správu vodoznaků do svého ERP nebo platformy pro generování dokumentů, aby byla vynucena značka.  
2. **Content Management Systems (CMS)** – Automaticky skenujte nahrané diagramy na neautorizovaná loga a odstraňujte je.  
3. **Legal Document Handling** – Přidejte textový vodoznak „Confidential“ během návrhových fází a později **remove watermark** před finálním podáním.

## Běžné problémy a řešení
| Symptom | Příčina | Řešení |
|---------|--------------|-----|
| Nebyly nalezeny žádné vodoznaky | Vyhledávaný text/obrázek se přesně neshoduje | Použijte `or()` pro kombinaci kritérií nebo upravte nastavení citlivosti na velikost písmen. |
| `OutOfMemoryError` u velkých souborů | Diagram byl načten celý do paměti | Použijte `DiagramLoadOptions.setLoadPages()` pro načtení pouze potřebných stránek. |
| Uložený soubor je poškozen | `watermarker.save()` byl zavolán před vymazáním všech vodoznaků | Ujistěte se, že `possibleWatermarks.clear()` dokončí a `watermarker.close()` je voláno po uložení. |

## Často kladené otázky

**Q: Mohu vyhledávat současně text i obrázky?**  
A: Ano. Kombinujte `TextSearchCriteria` a `ImageDctHashSearchCriteria` pomocí metody `or()`, jak je ukázáno v příkladu odstraňování.

**Q: Je možné odstranit vodoznaky bez poškození diagramu?**  
A: Rozhodně. Knihovna izoluje objekty vodoznaku, takže volání `clear()` odstraní pouze vrstvy vodoznaku a zachová původní obsah diagramu.

**Q: Podporuje GroupDocs.Watermark více formátů diagramů?**  
A: Ano. Formáty jako `.vsdx`, `.vdx` a další soubory kompatibilní s Visio jsou plně podporovány.

**Q: Jak efektivně zpracovat velké objemy dokumentů?**  
A: Implementujte smyčky dávkového zpracování, opakovaně používejte jedinou instanci `Watermarker`, kde je to možné, a omezte načítání stránek pomocí `DiagramLoadOptions`.

**Q: Existuje způsob, jak automatizovat detekci vodoznaků v CI/CD pipeline?**  
A: Můžete vložit poskytnuté úryvky Java do svých skriptů pro sestavení (např. Maven nebo Gradle), abyste ověřili, že před vydáním artefaktů nejsou přítomny neautorizované vodoznaky.

---

**Poslední aktualizace:** 2026-02-18  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs