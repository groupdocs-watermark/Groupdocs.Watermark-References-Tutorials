---
date: '2026-04-04'
description: Naučte se, jak vytvořit textový vodoznak na diagramech Visio pomocí GroupDocs.Watermark
  pro Javu. Obsahuje nastavení, kód a reálné příklady použití.
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: Vytvořte textový vodoznak na diagramech pomocí GroupDocs.Watermark Java
type: docs
url: /cs/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Vytvoření textové vodoznaku na diagramech pomocí GroupDocs.Watermark Java

Ochrana vašich diagramů před neoprávněným opětovným použitím je v dnešních spolupracujících prostředích nutností. V tomto tutoriálu **vytvoříte textový vodoznak** na diagramech ve stylu Visio pomocí **GroupDocs.Watermark for Java**. Provedeme vás vším od nastavení Maven až po uložení souboru s vodoznakem, abyste mohli sebejistě přidávat branding nebo bezpečnostní označení na každou stránku diagramu.

## Rychlé odpovědi
- **Jaká knihovna je potřeba?** GroupDocs.Watermark for Java (Maven artefakt `groupdocs-watermark`).
- **Jaké typy souborů jsou podporovány?** Visio (`.vsdx`, `.vsd`) a také mnoho dalších formátů diagramů.
- **Potřebuji licenci?** Dočasná zkušební licence funguje pro vývoj; plná licence je vyžadována pro produkci.
- **Mohu přizpůsobit písmo, barvu a rotaci?** Ano – třída `TextWatermark` vám umožní nastavit všechny tyto vlastnosti.
- **Jak dlouho proces trvá?** Přidání textového vodoznaku do typického diagramu trvá méně než sekundu na moderním hardware.

## Co je operace „vytvoření textového vodoznaku“?
Vytvoření textového vodoznaku znamená programově překrytí poloprůhledného textu na stránku dokumentu. Vodoznak může být umístěn do popředí nebo pozadí, otočen, obarven a stylizován tak, aby vyhovoval požadavkům na branding nebo zabezpečení.

## Proč používat GroupDocs.Watermark pro Java?
- **Široká podpora formátů** – funguje s Visio, PDF, Word, Excel a dalšími.
- **Detailní kontrola** – vyberte umístění, neprůhlednost, rotaci a vykreslování pozadí/popředí.
- **Jednoduchá integrace** – nastavení založené na Maven a přehledné volání API udržují kód čistý.
- **Optimalizovaný výkon** – prostředky jsou uvolněny automaticky při uzavření `Watermarker`.

## Předpoklady
- Java Development Kit (JDK) 8 nebo vyšší.
- IDE, například IntelliJ IDEA nebo Eclipse.
- Maven pro správu závislostí.

## Nastavení GroupDocs.Watermark pro Java
Přidejte repozitář a závislost do vašeho `pom.xml`:

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

Pokud dáváte přednost ručnímu stažení, stáhněte binární soubory z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) a přidejte je do classpath vašeho projektu.

### Získání licence
Začněte s bezplatnou zkušební licencí z [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Načtěte soubor licence před jakoukoliv operací vodoznaku:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Implementace krok za krokem

### Krok 1: Načtení souboru diagramu
Použijte `DiagramLoadOptions` k otevření souboru Visio (nebo jakéhokoli podporovaného formátu diagramu).

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Krok 2: Vytvoření textového vodoznaku
Nastavte text vodoznaku, písmo, barvu, příznak pozadí a úhel rotace.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### Krok 3: Definování umístění pro diagram
Zvolte, zda se vodoznak zobrazí v pozadí nebo popředí každé stránky diagramu.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Krok 4: Uložení diagramu s vodoznakem
Zapište výsledek do nového souboru a uvolněte prostředky.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Časté problémy a řešení

| Problém | Řešení |
|---------|----------|
| **Soubor nenalezen** | Ověřte absolutní/relativní cesty a zajistěte, aby byl soubor čitelný procesem Java. |
| **Licence nebyla použita** | Potvrďte, že cesta k souboru licence je správná a soubor není poškozen. |
| **Vodoznak není viditelný** | Zkontrolujte `setBackground(false)` a úhel rotace; vyzkoušejte jinou barvu nebo neprůhlednost. |
| **Nepodporovaná verze diagramu** | Použijte nejnovější verzi GroupDocs.Watermark (24.11), která přidává podporu pro novější formáty Visio. |

## Praktické příklady použití
1. **Zabezpečení dokumentů** – Zabránit konkurenci v opětovném používání proprietárních výkresů.
2. **Konzistence značky** – Automaticky vložit název společnosti nebo logo do všech exportovaných diagramů.
3. **Sledování spolupráce** – Přidat iniciály uživatele jako vodoznak pro identifikaci, kdo upravil každý diagram.

## Tipy pro výkon
- Uzavřete `Watermarker` co nejdříve po dokončení, aby se uvolnily nativní prostředky.
- Pro dávkové zpracování opakovaně používejte jednu instanci `Watermarker`, pokud je to možné.
- Udržujte text vodoznaku stručný; velká písma zvyšují dobu vykreslování.

## Závěr
Nyní víte, jak **vytvořit textový vodoznak** na diagramech Visio pomocí GroupDocs.Watermark pro Java. Tento přístup vám poskytuje plnou kontrolu nad vzhledem, umístěním a stylem, což vám pomáhá efektivně chránit a značkovat vaše vizuální aktiva.

### Další kroky
- Experimentujte s obrazovými vodoznaky (`ImageWatermark`) pro branding loga.
- Prozkoumejte selektivní vodoznakování stránek iterací přes `watermarker.getPages()` a podmíněným aplikováním možností.
- Integrovat tuto logiku do vašeho CI/CD pipeline pro automatické zabezpečení diagramů před publikací.

## Sekce FAQ
1. **Mohu používat GroupDocs.Watermark pro jiné formáty souborů?**  
   Ano, podporuje PDF, Word dokumenty, Excel tabulky, PowerPoint prezentace a mnoho dalších.
2. **Existuje limit na počet vodoznaků, které mohu přidat?**  
   Žádný pevný limit, ale přidání mnoha složitých vodoznaků může ovlivnit výkon.
3. **Jak odstraním vodoznak z diagramu?**  
   GroupDocs.Watermark poskytuje API pro detekci a odstranění, které můžete volat podobně jako při přidávání.
4. **Mohou být textové vodoznaky přidány na všechny stránky nebo jen na vybrané?**  
   Můžete konfigurovat `DiagramShapeWatermarkOptions` pro každou stránku nebo použít filtry před voláním `add`.
5. **Co mám dělat, pokud se vodoznak neobjeví podle očekávání?**  
   Dvakrát zkontrolujte nastavení umístění, kontrast barev a ujistěte se, že diagram není po uložení zploštěn.

## Často kladené otázky

**Q: Funguje knihovna s Visio 2003 (`.vsd`) soubory?**  
A: Ano – `DiagramLoadOptions` podporuje jak `.vsdx`, tak starší formáty `.vsd`.

**Q: Můžu změnit neprůhlednost textového vodoznaku?**  
A: Rozhodně. Použijte `textWatermark.setOpacity(0.5);` pro nastavení 50 % průhlednosti.

**Q: Je možné přidat různé vodoznaky na různé stránky diagramu?**  
A: Ano. Procházejte `watermarker.getPages()` a aplikujte odlišné instance `TextWatermark` s vlastními možnostmi pro každou stránku.

**Q: Existují nějaká licenční omezení pro komerční použití?**  
A: Pro produkční nasazení je vyžadována plná komerční licence; zkušební licence je pouze pro hodnocení.

**Q: Jak mohu dávkově zpracovat více diagramů v jednom běhu?**  
A: Zabalte výše uvedené kroky do smyčky, která načte každý soubor, aplikuje vodoznak, uloží a zavře `Watermarker` před přechodem na další soubor.

---

**Poslední aktualizace:** 2026-04-04  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/watermark/java/)
- [Reference API](https://reference.groupdocs.com/watermark/java)
- [Stáhnout nejnovější verzi](https://releases.groupdocs.com/watermark/java/)
- [GitHub úložiště](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)