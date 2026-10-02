---
date: '2026-02-16'
description: Naučte se, jak vodoznakovat konkrétní stránku diagramu pomocí GroupDocs.Watermark
  pro Javu, včetně toho, jak přidat obrázkový vodoznak v Javě a chránit své soubory.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Vodoznak konkrétní stránky diagramu pomocí GroupDocs.Watermark pro Java
type: docs
url: /cs/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Vodoznak konkrétní stránky diagramu pomocí GroupDocs.Watermark for Java

Ochrana vašich diagramů je zásadní, zejména když potřebujete **watermark specific diagram page** pro bezpečnost duševního vlastnictví nebo přiřazení značky. V tomto tutoriálu se krok za krokem naučíte, jak přidat textové i obrazové vodoznaky na vybrané stránky souboru diagramu pomocí **GroupDocs.Watermark for Java**. Na konci budete připraveni zabezpečit své diagramy a přesně kontrolovat, kde se každý vodoznak zobrazí.

## Rychlé odpovědi
- **Jaký je hlavní účel?** Přidávat vodoznaky na vybrané stránky diagramu.  
- **Která knihovna je vyžadována?** GroupDocs.Watermark for Java (Maven nebo přímé stažení).  
- **Mohu v Java přidat obrazový vodoznak?** Ano – použijte `ImageWatermark` s možnostmi specifickými pro stránku.  
- **Potřebuji licenci?** Dočasná zkušební licence funguje pro testování; plná licence je vyžadována pro produkci.  
- **Kolik řádků kódu?** Méně než 30 řádků pro kompletní workflow text + obrazový vodoznak.

## Co je „watermark specific diagram page“?
A **watermark specific diagram page** znamená aplikaci vizuálního značky — textu nebo obrázku — pouze na stránky, které si vyberete v rámci více‑stránkového diagramu (např. Visio . vsdx). To vám poskytuje detailní kontrolu nad značkováním, upozorněními na důvěrnost nebo prohlášením o autorských právech, aniž by to ovlivnilo celý dokument.

## Proč používat GroupDocs.Watermark for Java?
- **Full page control** – cílit na libovolný index stránky, který potřebujete.  
- **Rich styling** – písma, barvy, neprůhlednost, rotace a škálování obrázku jsou všechny konfigurovatelné.  
- **Performance‑optimized** – efektivně zpracovává velké diagramy a hladce se integruje s Maven buildy.  
- **Cross‑format support** – funguje s Visio, SVG a mnoha dalšími formáty diagramů.

## Předpoklady
- **GroupDocs.Watermark for Java** knihovna verze 24.11 nebo novější.  
- Maven nebo přímé stažení JAR souboru.  
- Základní nastavení vývoje v Javě (doporučeno JDK 8+).  

## Nastavení GroupDocs.Watermark for Java
### Použití Maven groupdocs watermark
Zahrňte GroupDocs.Watermark do svého projektu pomocí Maven přidáním následujícího do souboru `pom.xml`:

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
Alternativně stáhněte nejnovější verzi přímo z [vydání GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/).

#### Získání licence
Začněte s bezplatnou zkušební verzí stažením dočasné licence. Možnosti zakoupení jsou k dispozici na jejich oficiálních stránkách, pokud se rozhodnete nadále používat GroupDocs.Watermark.

### Základní inicializace a nastavení
Po instalaci inicializujte třídu `Watermarker` pro operace vodoznakování:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Průvodce implementací
### Přidání textového vodoznaku na konkrétní stránku
Pro přidání textového vodoznaku jej vytvořte a nakonfigurujte před určením cílové stránky.

#### Vytvoření textového vodoznaku
Definujte svůj textový vodoznak s nastavitelným obsahem, stylem písma, velikostí atd.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Nastavení indexu stránky pro vodoznak
Určete, která stránka diagramu bude zobrazovat vodoznak pomocí `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Přidání textového vodoznaku
Přidejte svůj nakonfigurovaný vodoznak do diagramu:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Přidání obrazového vodoznaku na konkrétní stránku
Postupujte podobně pro obrazové vodoznaky pomocí objektu `ImageWatermark`.

#### Vytvoření obrazového vodoznaku
Vytvořte instanci `ImageWatermark` s požadovanou cestou k obrázku vodoznaku:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Nastavení indexu stránky pro vodoznak
Určete, která stránka má zobrazovat obrazový vodoznak:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Přidání obrazového vodoznaku
Přidejte obrázek na určenou stránku diagramu:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Uložení a uzavření zdrojů
Nezapomeňte uložit změny a uzavřít zdroje, aby nedocházelo k únikům:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Praktické aplikace
- **Document Security** – Použijte důvěrné vodoznaky pouze na stránkách, které obsahují citlivé schémata.  
- **Branding** – Umístěte logo vaší společnosti na titulní stránku a nechte vnitřní stránky čisté.  
- **Copyright Protection** – Přidejte upozornění na autorská práva na poslední stránku technického balíčku diagramů.

## Úvahy o výkonu
- **Memory Management** – Po uložení zavřete každý objekt vodoznaku, aby se uvolnily nativní zdroje.  
- **Image Optimization** – Používejte vhodně velikostní PNG/JPEG soubory, aby zpracování zůstalo rychlé.  
- **Batch Processing** – Při zpracování mnoha diagramů opakovaně používejte jedinou instanci `Watermarker`, pokud je to možné.

## Časté problémy a řešení
| Příznak | Předpokládaná příčina | Řešení |
|---------|-----------------------|--------|
| Vodoznak není viditelný | Špatný `pageIndex` (číslování od nuly) | Ověřte, že index odpovídá zamýšlené stránce. |
| Obrázek je deformovaný | Vysoké rozlišení zdrojového obrázku | Změňte velikost obrázku před vytvořením `ImageWatermark`. |
| Chyba licence v produkci | Použití zkušební licence po jejím vypršení | Použijte plný licenční soubor pomocí `License.setLicense("path/to/license.json")`. |

## Často kladené otázky

**Q1: Mohu přidat více vodoznaků na jednu stránku diagramu?**  
A1: Ano, jednoduše zavolejte `watermarker.add()` s různými objekty vodoznaku pro stejný index stránky.

**Q2: Jaké souborové formáty podporuje GroupDocs.Watermark for Java?**  
A2: Podporuje různé formáty diagramů a obrázků. Podívejte se na [API dokumentaci](https://reference.groupdocs.com/watermark/java) pro úplný seznam.

**Q3: Jak řešit licenční problémy při používání zkušební verze?**  
A3: Začněte s bezplatnou dočasnou licencí od GroupDocs. Zakupte plnou licenci pro odemknutí všech funkcí v produkci.

**Q4: Jaké jsou běžné tipy pro odstraňování problémů, pokud se vodoznaky neobjevují podle očekávání?**  
A4: Ujistěte se, že je index stránky správný a dvakrát zkontrolujte cesty k souborům obrázků. Také ověřte, že neprůhlednost vodoznaku není nastavena na 0.

**Q5: Jak mohu dále přizpůsobit vzhled vodoznaku?**  
A5: Upravit velikost písma, neprůhlednost, rotaci a umístění pomocí metod dostupných na `TextWatermark` nebo `ImageWatermark`.

## Zdroje
- [Dokumentace GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)
- [Průvodce referencí API](https://reference.groupdocs.com/watermark/java)
- [Stáhnout knihovnu](https://releases.groupdocs.com/watermark/java/)
- [Úložiště na GitHubu](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)
- [Informace o dočasné licenci](https://purchase.groupdocs.com/temporary-license/)

Prozkoumejte tyto zdroje, abyste prohloubili své znalosti a možnosti práce s GroupDocs.Watermark for Java. Šťastné vodoznakování!

---

**Poslední aktualizace:** 2026-02-16  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs