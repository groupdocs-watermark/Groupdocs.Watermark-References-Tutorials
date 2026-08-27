---
date: '2026-03-20'
description: Naučte se, jak pomocí GroupDocs.Watermark Java SDK přidat obrázkový vodoznak
  do tabulky Excel, což je ideální pro značkování a zabezpečení dokumentů.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'Jak přidat vodoznak: obrázkový vodoznak do tabulky Excel pomocí GroupDocs.Watermark
  Java SDK'
type: docs
url: /cs/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# Jak přidat vodoznak do tabulky Excel pomocí GroupDocs.Watermark Java SDK

Chránit vaše soubory Excel před neoprávněným šířením nebo jednoduše posílit identitu značky lze dosažením přidáním vizuálního označení, které zůstane viditelné bez ohledu na to, jak je soubor zobrazen. V tomto tutoriálu se naučíte **how to add watermark** — konkrétně obrázkový vodoznak — do záhlaví nebo zápatí tabulky Excel pomocí **GroupDocs.Watermark Java SDK**. Na konci průvodce budete schopni vložit logo, štítek důvěrnosti nebo jakýkoli vlastní obrázek přímo do sešitu, aniž byste měnili data buněk.

## Rychlé odpovědi
- **Co znamená „how to add watermark“?** Přidání obrázkového (nebo textového) překrytí, které se zobrazí na každé tištěné stránce nebo v konkrétních částech, jako jsou záhlaví/zápatí.  
- **Která knihovna to podporuje v Javě?** `GroupDocs.Watermark` Java SDK (latest release).  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována komerční licence.  
- **Mohu přidat logo do záhlaví?** Ano – použijte obrázkový vodoznak a nastavte možnost záhlaví (`add logo to header`).  
- **Je možné zpracovat více listů najednou?** Procházejte indexy listů a aplikujte stejný vodoznak na každý list.

## Požadavky

Abyste mohli postupovat, ujistěte se, že máte:

- **GroupDocs.Watermark for Java SDK** (verze 24.11 nebo novější).  
- **Java Development Kit (JDK)** 8 nebo vyšší.  
- Základní znalost Javy a struktury souborů Excel.

## Nastavení GroupDocs.Watermark pro Java SDK

Nejprve přidejte požadované Maven závislosti, aby byl SDK dostupný ve vašem classpath.

### Maven konfigurace

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

Pokud raději nepoužíváte Maven, stáhněte si nejnovější JAR z oficiální stránky vydání: [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

**Získání licence**  
- Získejte bezplatnou zkušební verzi nebo dočasný licenční klíč pro vyzkoušení všech funkcí.  
- Zakupte plnou licenci pro komerční nasazení.

### Inicializace a nastavení

Vytvořte instanci `Watermarker`, která načte soubor Excel a bude vstupním bodem pro všechny operace s vodoznakem.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## Jak přidat vodoznak do záhlaví/zápatí tabulky

Níže je krok‑za‑krokem proces, který demonstruje funkci **java add image watermark** a také ukazuje, jak můžete **add logo to header**.

### Krok 1: Konfigurace možností načítání

Začínáme definováním možností načítání a opětovným vytvořením instance `Watermarker`. Tím zajistíme, že SDK správně načte sešit.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### Krok 2: Vytvoření a konfigurace obrázkového vodoznaku

Vytvořte objekt `ImageWatermark`, který odkazuje na obrázek, který chcete vložit (např. logo nebo štítek „CONFIDENTIAL“). Nastavte jeho zarovnání a měřítko tak, aby se pěkně vešel do oblasti záhlaví/zápatí.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### Krok 3: Konfigurace možností záhlaví/zápatí

Sdělte SDK, který list a která část (záhlaví nebo zápatí) má obdržet vodoznak. Zde můžete **add logo to header** nebo místo toho zvolit zápatí.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### Krok 4: Přidání vodoznaku

Nyní připojte připravený obrázkový vodoznak k vybranému místu záhlaví/zápatí.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### Krok 5: Uložení a uzavření

Uložte změny do nového souboru, aby původní sešit zůstal nedotčený, a poté uvolněte prostředky.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### Tipy pro řešení problémů

- Zkontrolujte cestu k obrázku; špatná cesta vyvolá `FileNotFoundException`.  
- Indexy listů začínají na 0; ujistěte se, že nastavený index skutečně existuje.  
- Pokud se vodoznak zobrazí deformovaný, upravte `setScaleFactor` nebo přepněte `SizingType` na `StretchToParentDimensions`.

## Proč používat GroupDocs.Watermark Java SDK?

- **Cross‑format support** – funguje s Excel, Word, PowerPoint, PDF a obrázky.  
- **No‑loss editing** – původní data buněk zůstávají nedotčena.  
- **Performance‑optimized** – vhodné pro velké sešity a dávkové zpracování.

## Praktické příklady použití

| Scénář | Jak vodoznak pomáhá |
|----------|------------------------|
| **Důvěrné zprávy** | Přidejte obrázek „CONFIDENTIAL“ na každou tištěnou stránku. |
| **Posílení značky** | Umístěte logo vaší společnosti do záhlaví faktur. |
| **Sledování verzí** | Vložte štítek s číslem verze, který se aktualizuje automaticky. |
| **Právní soulad** | Označte regulované tabulky pečetí souladu. |

## Úvahy o výkonu

- **Memory usage** – Sledujte haldu JVM při zpracování velmi velkých tabulek.  
- **Batch processing** – Zpracovávejte soubory ve skupinách, aby se snížila paměťová stopa.  
- **Reuse objects** – Opětovné používání jedné instance `Watermarker` pro více souborů snižuje režii.

## Často kladené otázky

**Q: Mohu přidat více vodoznaků do jednoho dokumentu?**  
A: Ano, vytvořením dalších instancí `ImageWatermark` a jejich konfigurací před voláním `watermarker.add()`.

**Q: Jak mohu odstranit existující vodoznak z tabulky?**  
A: V současné době se GroupDocs.Watermark zaměřuje na přidávání vodoznaků. Pro jeho odstranění budete muset vytvořit sešit znovu bez vodoznaku nebo použít nástroj, který podporuje extrakci vodoznaku.

**Q: Jaké formáty obrázků jsou podporovány pro vodoznaky?**  
A: Běžné formáty jako PNG a JPEG jsou podporovány, ale podívejte se na [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/) pro úplný seznam kompatibilních formátů.

**Q: Je možné vodoznakovat tabulky chráněné heslem?**  
A: Ano, pokud při otevírání souboru zadáte potřebné heslo.

**Q: Jak aplikovat vodoznaky na všechny listy v dokumentu?**  
A: Procházejte každý index listu a opakujte kroky vodoznakování, nastavením `headerFooterOptions.setWorksheetIndex(i)` pro každou iteraci.

## Závěr

Nyní máte kompletní, připravenou metodu pro **java add excel watermark**—konkrétně obrázkový vodoznak—pomocí **GroupDocs.Watermark Java SDK**. Tento přístup přidává značku, upozornění na důvěrnost nebo jakýkoli vizuální prvek přímo do záhlaví nebo zápatí vašich souborů Excel, přičemž ponechává podkladová data nedotčena. Neváhejte prozkoumat další typy vodoznaků (text, tvar) a kombinovat je pro komplexnější ochranu dokumentů.

---

**Poslední aktualizace:** 2026-03-20  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs