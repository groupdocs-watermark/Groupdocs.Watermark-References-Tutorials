---
date: '2025-12-17'
description: Naučte se, jak přidat vodoznak na konkrétní stránku diagramu pomocí GroupDocs.Watermark
  pro Javu, přidat vodoznak do diagramu a přidat obrázkový vodoznak v Javě. Krok za
  krokem průvodce, jak chránit vaše duševní vlastnictví.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Vodoznak konkrétní stránky diagramu pomocí GroupDocs.Watermark pro Javu
type: docs
url: /cs/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Vodoznak konkrétní stránky diagramu pomocí GroupDocs.Watermark pro Java

Ochrana vašich diagramů je zásadní, zejména když jde o zabezpečení duševního vlastnictví nebo zajištění řádného přiřazení. V tomto tutoriálu se naučíte **jak přidat vodoznak na konkrétní stránku diagramu** pomocí GroupDocs.Watermark pro Java, ať už potřebujete **přidat vodoznak do diagramu** jako text nebo **přidat obrázkový vodoznak java**‑stylové loga. Na konci tohoto průvodce budete schopni:

- Bez problémů přidávat textové vodoznaky na vybrané stránky diagramu.  
- Vkládat obrázkové vodoznaky do určených částí diagramů.  
- Zvýšit výkon při používání GroupDocs.Watermark.

Ujistěme se, že je prostředí připravené, než se ponoříme do kódu.

## Rychlé odpovědi
- **Co znamená „watermark specific diagram page“?** Jedná se o aplikaci vodoznaku pouze na vybrané stránky souboru diagramu, zatímco ostatní stránky zůstávají nedotčeny.  
- **Jaká verze knihovny je vyžadována?** GroupDocs.Watermark 24.11 nebo novější.  
- **Mohu použít textové i obrázkové vodoznaky na stejné stránce?** Ano – zavolejte `watermarker.add()` pro každý typ vodoznaku.  
- **Potřebuji licenci pro vývoj?** Dočasná zkušební licence funguje pro testování; pro produkci je vyžadována plná licence.  
- **Je Maven jediný způsob, jak přidat knihovnu?** Ne – můžete také stáhnout JAR přímo (viz „Direct Download“ níže).

## Co je „watermark specific diagram page“?
Operace **watermark specific diagram page** cílí na jednu stránku (nebo sadu stránek) uvnitř dokumentu diagramu (např. Visio *.vsdx*) a překryje ji textovou nebo obrázkovou vrstvou. To je užitečné pro důvěrné koncepty, branding nebo upozornění na autorská práva, aniž by se měnil celý soubor.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark poskytuje vysoce úrovňové API, které abstrahuje složitosti formátů diagramů, podporuje dávkové zpracování a nabízí jemnozrnné řízení průhlednosti, umístění a výběru stránek. Navíc se hladce integruje s Mavenem a standardními nástroji pro sestavování Java.

## Předpoklady
- **GroupDocs.Watermark pro Java** verze 24.11 nebo novější nainstalovaná.  
- Vývojové prostředí s Mavenem (nebo možností přidat JAR ručně).  
- Základní znalost Javy a přístup k souborovému systému.  

## Nastavení GroupDocs.Watermark pro Java

### Použití Maven
Přidejte GroupDocs.Watermark do svého projektu pomocí Mavenu vložením následujícího do souboru `pom.xml`:

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
Alternativně si stáhněte nejnovější verzi přímo z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Získání licence
Začněte s bezplatnou zkušební licencí stažením dočasné licence. Možnosti zakoupení jsou k dispozici na jejich oficiálním webu, pokud se rozhodnete pokračovat v používání GroupDocs.Watermark.

### Základní inicializace a nastavení
Jakmile je knihovna k dispozici, vytvořte instanci `Watermarker`, která ukazuje na diagram, který chcete chránit:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Jak **add watermark to diagram** – Textový vodoznak

### Vytvoření textového vodoznaku
Definujte text, font, barvu a průhlednost, které chcete použít:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

### Nastavení indexu stránky pro vodoznak
Určete přesnou stránku, kterou chcete opatřit vodoznakem. Indexy stránek jsou nulové‑základní:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

### Přidání textového vodoznaku
Aplikujte vodoznak na vybranou stránku:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

## Jak **add image watermark java** – Obrázkový vodoznak

### Vytvoření obrázkového vodoznaku
Načtěte obrázek, který chcete překrýt (např. firemní logo):

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

### Nastavení indexu stránky pro obrázkový vodoznak
Vyberte stránku, na které se obrázkový vodoznak zobrazí:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

### Přidání obrázkového vodoznaku
Vložte obrázkový vodoznak na zvolenou stránku:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

## Uložení a uzavření zdrojů
Po přidání všech požadovaných vodoznaků uložte změny a vyčistěte prostředky:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Praktické aplikace
- **Zabezpečení dokumentů** – Přidejte štítek „Confidential“ na koncepty diagramů před sdílením s partnery.  
- **Branding** – Razte své logo na konkrétní stránky technických schémat.  
- **Ochrana autorských práv** – Vložte upozornění na autorská práva na vysoce hodnotné diagramy, aby se odradilo jejich zneužití.

## Úvahy o výkonu
- Spravujte paměť efektivně, zejména u velkých souborů.  
- Optimalizujte velikosti obrázků před jejich použitím jako vodoznaků, aby se urychlilo zpracování.  
- Využijte garbage collection v Javě tím, že po uložení uzavřete všechny objekty vodoznaku.

## Časté problémy a řešení
| Problém | Pravděpodobná příčina | Oprava |
|---|---|---|
| Vodoznak není vidět | Nesprávný index stránky | Ověřte, že nulové‑základní index odpovídá zamýšlené stránce. |
| Obrázek je zkreslený | Obrázek s vysokým rozlišením | Změňte velikost obrázku na rozumnou dimenzi (např. 300 × 300 px). |
| Chyba licence v produkci | Používáte pouze zkušební licenci | Použijte plný licenční soubor pomocí `License.setLicense("path/to/license.file")`. |
| Pomalé zpracování velkých diagramů | Velikost souboru & neuzavřené zdroje | Uzavřete `Watermarker` a jednotlivé objekty vodoznaku okamžitě. |

## Často kladené otázky

**Q1: Mohu přidat více vodoznaků na jednu stránku diagramu?**  
A: Ano, stačí zavolat `watermarker.add()` s různými objekty vodoznaku pro stejnou `DiagramPageWatermarkOptions`.

**Q2: Jaké formáty souborů jsou podporovány GroupDocs.Watermark pro Java?**  
A: Podporuje různé formáty diagramů a obrázků. Kompletní seznam najdete v [API documentation](https://reference.groupdocs.com/watermark/java).

**Q3: Jak řešit licenční problémy při používání zkušební verze?**  
A: Začněte s bezplatnou dočasnou licencí od GroupDocs. Pro produkci zakupte plnou licenci, která odemkne všechny funkce.

**Q4: Jaké jsou běžné tipy pro odstraňování problémů, pokud se vodoznaky neobjevují podle očekávání?**  
A: Ujistěte se, že je správný index stránky, ověřte cesty k souborům obrázků a potvrďte, že nastavení průhlednosti není nastaveno na 0.

**Q5: Jak mohu dále přizpůsobit vzhled vodoznaku?**  
A: Upravit velikost písma, průhlednost, rotaci a umístění pomocí metod na `TextWatermark` nebo `ImageWatermark`.

**Q6: Je možné vodoznakovat více stránek v jednom volání?**  
A: Ano – můžete vytvořit instanci `DiagramPageWatermarkOptions`, nastavit seznam indexů stránek a předat ji do `watermarker.add()`.

**Q7: Podporuje GroupDocs.Watermark soubory diagramů chráněné heslem?**  
A: Ano, můžete před načtením poskytnout heslo pomocí `DiagramLoadOptions.setPassword("yourPassword")`.

## Zdroje
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference Guide](https://reference.groupdocs.com/watermark/java)
- [Download Library](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)

Prozkoumejte tyto zdroje, abyste prohloubili své znalosti a schopnosti s GroupDocs.Watermark pro Java. Šťastné vodoznakování!

---

**Poslední aktualizace:** 2025-12-17  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs