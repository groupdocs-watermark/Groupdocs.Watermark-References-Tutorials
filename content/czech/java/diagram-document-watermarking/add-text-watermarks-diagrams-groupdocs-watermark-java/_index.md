---
date: '2025-12-19'
description: Naučte se, jak přidat textový vodoznak do diagramů pomocí GroupDocs.Watermark
  pro Javu. Tento průvodce krok za krokem zahrnuje nastavení, nastavení písma vodoznaku
  a praktické příklady použití.
keywords:
- text watermarks in Java
- add text watermark to diagram
- GroupDocs Watermark for Java setup
title: Jak přidat textový vodoznak do diagramů pomocí GroupDocs.Watermark pro Javu
type: docs
url: /cs/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Jak přidat textový vodoznak do diagramů pomocí GroupDocs.Watermark pro Java

Chránit vaše diagramy před neoprávněným použitím je pro mnoho vývojářů a designérů nejvyšší prioritou. V tomto tutoriálu se naučíte **jak přidat textový vodoznak** do souborů diagramů pomocí výkonné knihovny **GroupDocs.Watermark pro Java**. Provedeme vás každým krokem – od nastavení Maven až po aplikaci vlastních nastavení písma vodoznaku – abyste mohli rychle a spolehlivě zabezpečit své vizuální materiály.

## Rychlé odpovědi
- **Co knihovna dělá?** Vkládá textové (nebo obrázkové) vodoznaky do více než 100 formátů dokumentů a diagramů.  
- **Na které hlavní klíčové slovo se mám zaměřit?** *add text watermark* – používá se v celém průvodci.  
- **Potřebuji licenci?** Dočasná zkušební licence stačí pro vývoj; pro produkci je vyžadována plná licence.  
- **Mohu přizpůsobit písmo?** Ano, můžete pomocí nastavení písma vodoznaku ovládat rodinu písma, velikost, barvu a rotaci.  
- **Je kompatibilní s Java‑8?** Naprosto – knihovna podporuje JDK 8 a novější.

## Co znamená „add text watermark“?
Přidání textového vodoznaku znamená překrytí poloprůhledným textem každé stránky nebo tvaru dokumentu, aby byl obsah identifikovatelný. Tato technika se široce používá pro značkování, ochranu autorských práv a spolupráci při úpravách.

## Proč použít GroupDocs.Watermark pro Java?
- **Široká podpora formátů** – funguje s Visio, SVG, PDF, Word a mnoha dalšími.  
- **Detailní kontrola** – můžete nastavit písmo, barvu, rotaci, neprůhlednost a umístění.  
- **Jednoduché API** – několik řádků kódu vyřeší úkol, čímž šetří čas vývoje.  
- **Optimalizovaný výkon** – efektivně zpracovává velké soubory, pokud rychle uvolníte prostředky.

## Požadavky
- JDK 8 nebo vyšší nainstalovaný na vašem počítači.  
- IDE, například IntelliJ IDEA nebo Eclipse.  
- Základní znalost Javy (třídy, objekty a Maven).

### Požadované knihovny a závislosti
Použijeme Maven k načtení knihovny GroupDocs.Watermark. Přidejte úložiště a závislost do souboru `pom.xml` přesně tak, jak je uvedeno:

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

Pokud dáváte přednost ručnímu stažení, navštivte oficiální stránku: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) a postupujte podle instrukcí.

### Získání licence
Začněte s bezplatnou zkušební verzí získáním dočasné licence z portálu pro zkušební verze: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Načtěte soubor licence před jakoukoliv operací vodoznaku:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Průvodce implementací

### Krok 1: Načtěte svůj diagram
Nejprve nasměrujte `Watermarker` na váš zdrojový soubor diagramu. Objekt `DiagramLoadOptions` říká knihovně, aby soubor zacházel jako s formátem diagramu.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Krok 2: Inicializujte textový vodoznak (s vlastními **nastaveními písma vodoznaku**)
Vytvořte instanci `TextWatermark`, kde určíte text, rodinu písma, velikost a jakékoli další požadované stylování.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **Tip:** Upravit `setColor` a `setRotationAngle`, aby odpovídaly vašim pokynům pro značku. Volání `setBackground(false)` zajistí, že vodoznak bude umístěn nad tvary diagramu, nikoli za nimi.

### Krok 3: Vyberte umístění – pozadí vs. popředí
GroupDocs vám umožňuje rozhodnout, zda se vodoznak zobrazí za tvary diagramu (pozadí) nebo nad nimi (popředí). Pro většinu scénářů značkování je nejlepší umístění na pozadí.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Krok 4: Uložte diagram s vodoznakem
Nakonec zapište upravený soubor na disk a uvolněte prostředky.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| **File not found** chyba | Nesprávná `inputFilePath` nebo chybějící oprávnění ke čtení | Ověřte cestu a zajistěte, aby Java proces mohl soubor číst. |
| **Watermark not visible** | Umístění nastaveno na `Foreground` s průhlednou barvou | Použijte umístění `Background` nebo zvolte kontrastní barvu. |
| **Out‑of‑memory exception** při velkých diagramech | Neuzavření `Watermarker` nebo zpracování mnoha souborů ve smyčce | Zavolejte `watermarker.close()` po každém souboru a zvažte zpracování po dávkách. |
| **License not recognized** | Špatná cesta k souboru licence nebo vypršená zkušební verze | Zkontrolujte cestu a použijte aktuální soubor licence. |

## Praktické aplikace
1. **Document Security** – Zabránit konkurenci v krádeži proprietárních vývojových diagramů.  
2. **Branding** – Vložit název společnosti nebo logo na všechny stránky diagramu.  
3. **Collaboration Tracking** – Přidat iniciály uživatele jako vodoznak, který označuje, kdo diagram upravil.  

## Úvahy o výkonu
- Uzavřete `Watermarker` okamžitě po uložení, aby se uvolnily nativní prostředky.  
- Udržujte text vodoznaku stručný; příliš velká písma zvyšují dobu zpracování.  
- Otestujte na reprezentativním vzorku před dávkovým zpracováním tisíců souborů.  

## Závěr
Nyní máte kompletní, připravenou metodu pro **přidání textového vodoznaku** do souborů diagramů pomocí **GroupDocs.Watermark pro Java**. Tento přístup chrání vaše duševní vlastnictví a zároveň vám poskytuje plnou kontrolu nad nastavením písma vodoznaku a jeho umístěním.

### Další kroky
- Prozkoumejte obrázkové vodoznaky pro vizuální značku.  
- Kombinujte více vodoznaků (text + obrázek) pro vrstvenou ochranu.  
- Automatizujte dávkové zpracování pomocí jednoduché smyčky `for` a stejných volání API.

## Často kladené otázky

**Q: Funguje GroupDocs.Watermark s nejnovějšími verzemi Javy?**  
A: Ano, je plně kompatibilní s Java 8 až Java 21.

**Q: Mohu přizpůsobit neprůhlednost textového vodoznaku?**  
A: Rozhodně. Použijte `textWatermark.setOpacity(0.5)` pro nastavení 50 % neprůhlednosti.

**Q: Existuje způsob, jak přidat vodoznaky jen na vybrané tvary diagramu?**  
A: Můžete filtrovat tvary pomocí `DiagramShapeWatermarkOptions` zadáním ID nebo názvů tvarů.

**Q: Jak zacházet se soubory diagramu chráněnými heslem?**  
A: Načtěte soubor pomocí `DiagramLoadOptions`, který obsahuje heslo, a poté aplikujte vodoznak jako obvykle.

**Q: Existují nějaká omezení licence pro komerční použití?**  
A: Pro produkční nasazení je vyžadována komerční licence; zkušební licence slouží pouze k hodnocení.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Stáhnout nejnovější verzi](https://releases.groupdocs.com/watermark/java/)
- [GitHub repozitář](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)

---

**Poslední aktualizace:** 2025-12-19  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs