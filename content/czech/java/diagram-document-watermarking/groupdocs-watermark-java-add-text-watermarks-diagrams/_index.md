---
date: '2025-12-19'
description: Naučte se, jak přidat textový vodoznak do diagramů pomocí GroupDocs.Watermark
  pro Javu. Efektivně chraňte svůj vizuální obsah a zajistěte integritu dokumentu.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: Přidání textové vodoznaku do diagramů pomocí GroupDocs.Watermark pro Javu –
  komplexní průvodce
type: docs
url: /cs/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Přidání textové vodoznaku do diagramů pomocí GroupDocs.Watermark pro Java: Komplexní průvodce

## Úvod
Ochrana diagramových dokumentů před neoprávněným použitím je zásadní a **přidání textového vodoznaku** poskytuje jednoduché, ale účinné řešení. V tomto tutoriálu se dozvíte, jak načíst soubory diagramů, vytvořit přizpůsobitelný textový vodoznak a aplikovat jej na pozadí stránek nebo konkrétní tvary pomocí **GroupDocs.Watermark pro Java**. Na konci průvodce budete schopni chránit své vizuální aktiva a zároveň zachovat původní vzhled a pocit.

### Rychlé odpovědi
- **Co znamená „přidání textového vodoznaku“?**  
  Znamená to vložení poloprůhledného textového překryvu do dokumentu za účelem označení vlastnictví nebo důvěrnosti.  
- **Která knihovna podporuje vodoznakování diagramů?**  
  GroupDocs.Watermark pro Java poskytuje nativní podporu formátů diagramů (např. Visio, VSDX).  
- **Potřebuji licenci?**  
  Pro produkční použití je vyžadována dočasná nebo plná licence; k vyzkoušení je k dispozici bezplatná zkušební verze.  
- **Mohu umístit vodoznak na pozadí stránek?**  
  Ano – použijte možnost `DiagramWatermarkPlacementType.SeparateBackgrounds` pro **vodoznak na pozadí stránky**.  
- **Je kód kompatibilní s Java 8+?**  
  Naprosto – knihovna funguje s JDK 8 a novějšími.

## Co je textový vodoznak pro diagramy?
Textový vodoznak je kus čitelného textu (často poloprůhledný), který je vykreslen nad nebo pod elementy diagramu. Může být použit pro značkování, ochranu autorských práv nebo pro označení důvěrných návrhů.

## Proč použít GroupDocs.Watermark pro Java?
- **Široká podpora formátů** – funguje s Visio, VSDX a mnoha dalšími typy diagramů.  
- **Precizní umístění** – vyberte vodoznak v popředí, pozadí nebo na konkrétní tvar.  
- **Jednoduché API** – vytvořte a aplikujte vodoznaky pomocí několika řádků Java kódu.  

## Prerequisites
- **GroupDocs.Watermark pro Java** (v24.11 nebo novější)  
- **Java Development Kit (JDK)** 8 nebo vyšší  
- Maven (nebo ruční zahrnutí JAR souboru)  

## Setting Up GroupDocs.Watermark for Java
### Nastavení Maven
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

### Přímé stažení
Stáhněte nejnovější verzi z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence
- **Bezplatná zkušební verze** – vyzkoušejte všechny funkce bez licenčního klíče.  
- **Dočasná licence** – použijte během vývoje k odemknutí plné funkčnosti.  
- **Nákup** – získat produkční licenci pro komerční projekty.  

### Základní inicializace a nastavení
Ujistěte se, že následující importy jsou ve vaší Java třídě:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Implementace krok za krokem

### Krok 1: Načtení diagramového dokumentu
Nejprve nasměrujte knihovnu na svůj diagramový soubor a inicializujte možnosti načtení.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Vysvětlení*: `DiagramLoadOptions` vám umožňuje řídit, jak je diagram parsován před vodoznakem.

### Krok 2: Vytvoření textového vodoznaku
Nyní vytvořte text vodoznaku a definujte jeho vizuální styl.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Vysvětlení*: Toto vytvoří `TextWatermark` s frází **„Test watermark 1“** pomocí fontu Calibri o velikosti 19.

### Krok 3: Nastavení umístění – Vodoznak na pozadí stránky
Vyberte, kde se má vodoznak zobrazit. Pro **vodoznak na pozadí stránky** použijte následující možnost:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Vysvětlení*: `DiagramShapeWatermarkOptions` řídí přesné umístění. Nastavením typu umístění na `SeparateBackgrounds` přidáte vodoznak na každou pozadí stránku diagramu.

### Krok 4: Aplikace vodoznaku a uložení
Nakonec přidejte vodoznak do dokumentu, uložte výsledek a uvolněte prostředky.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Vysvětlení*: Metoda `add` aplikuje nakonfigurovaný `textWatermark` pomocí možností umístění, poté je upravený diagram uložen do `outputPath`.

## Praktické aplikace
- **Ochrana duševního vlastnictví** – Zabránit konkurenci v opětovném použití proprietárních diagramů.  
- **Posílení značky** – Vložte název společnosti nebo logo jako textový vodoznak na všechny exportované diagramy.  
- **Právní dokumentace** – Označte důvěrné návrhy technických schémat.  
- **Akademické podání** – Přidejte ID studentů nebo kódy kurzů k diagramům pro sledování plagiátorství.  

## Úvahy o výkonu
- **Správa paměti** – Zavřete instanci `Watermarker` (`watermarker.close()`) pro uvolnění nativních prostředků, zejména při zpracování velkých souborů.  
- **Dávkové zpracování** – Procházejte kolekci cest k diagramům a kde je to možné, znovu použijte jedinou instanci `Watermarker`, abyste snížili režii.  

## Časté problémy a řešení

| Problém | Řešení |
|-------|----------|
| **OutOfMemoryError u velkých diagramů** | Zvyšte velikost haldy JVM (`-Xmx2g`) a zpracovávejte soubory po jednom. |
| **Vodoznak není viditelný** | Ujistěte se, že barva vodoznaku má dostatečný kontrast; nastavte neprůhlednost pomocí `textWatermark.setOpacity(0.5)`. |
| **Nepodporovaný formát diagramu** | Ověřte, že formát je uveden v dokumentaci podporovaných formátů GroupDocs.Watermark. |

## Často kladené otázky

**Q: Jaká je nejlepší velikost písma pro vodoznaky?**  
A: Optimální velikost závisí na rozměrech diagramu; 12‑20 pt funguje dobře ve většině případů.

**Q: Mohu přizpůsobit barvy vodoznaku?**  
A: Ano, použijte `textWatermark.setColor(Color.GRAY)` (nebo libovolnou `java.awt.Color`).

**Q: Jak zvládnout velké dávky dokumentů?**  
A: Využijte dávkové API knihovny nebo napište smyčku, která znovu používá objekty `Watermarker` ke snížení režie.

**Q: Existují nějaká omezení GroupDocs.Watermark?**  
A: Knihovna podporuje většinu běžných formátů diagramů, ale některé proprietární rozšíření nemusí být plně vykresleny. Podívejte se do [dokumentace](https://docs.groupdocs.com/watermark/java/) pro podrobnosti.

**Q: Jak získám podporu, pokud narazím na problémy?**  
A: Navštivte [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) pro komunitní pomoc nebo kontaktujte přímo podporu GroupDocs.

## Další zdroje
- **Dokumentace**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Reference API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Stažení**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub repozitář**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Bezplatné fórum podpory**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Dočasná licence**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**Poslední aktualizace:** 2025-12-19  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

---