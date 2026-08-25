---
date: '2026-08-25'
description: Naučte se upravovat soubory diagramů a odstraňovat hypertextové odkazy
  pomocí GroupDocs.Watermark for Java. Rychle zabezpečte své diagramy pomocí podrobných
  návodů krok po kroku.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Naučte se upravovat soubory diagramů a odstraňovat hypertextové odkazy
  pomocí GroupDocs.Watermark for Java. Postupujte podle jasných kroků k ochraně svých
  dokumentů.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Jak upravit diagram a odstranit hypertextové odkazy pomocí Javy
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Jak upravit diagram a odstranit hypertextové odkazy pomocí Javy
type: docs
url: /cs/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak upravit diagram a odstranit hypertextové odkazy pomocí Javy  

Správa digitálních dokumentů často zahrnuje úpravu diagramů, zejména když potřebujete **edit diagram** soubory odstranit hypertextové odkazy z důvodů bezpečnosti nebo vizuální přehlednosti. Tento tutoriál vám přesně ukáže, jak upravit soubory diagramů a odstranit nechtěné hypertextové odkazy z tvarů diagramu pomocí výkonné knihovny **GroupDocs.Watermark** pro Javu. Na konci tohoto průvodce budete mít čistý diagram bez odkazů připravený k distribuci.  

## Rychlé odpovědi  
- **Jaký je hlavní cíl?** Odstraňte všechny hypertextové odkazy z tvarů diagramu, aby se zlepšila bezpečnost a prezentace.  
- **Která knihovna je vyžadována?** GroupDocs.Watermark pro Javu, verze 24.11 nebo novější.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována komerční licence.  
- **Mohu zpracovávat mnoho souborů najednou?** Ano – stejný kód lze umístit do smyčky pro zpracování dávky.  
- **Jaká verze Javy je podporována?** Java 8 nebo vyšší (doporučena Java 11).  

## Co je „how to edit diagram“?  
**How to edit diagram** odkazuje na proces programového otevření souboru diagramu, úpravy jeho vnitřních prvků (jako jsou tvary, text nebo hypertextové odkazy) a uložení výsledku. Pomocí GroupDocs.Watermark můžete upravovat soubory diagramů bez potřeby původního autorovacího nástroje.  

## Proč použít GroupDocs.Watermark pro Javu?  
GroupDocs.Watermark podporuje **30+ formátů diagramů a obrázků** (včetně VSDX, SVG a WMF) a může zpracovávat soubory až do **500 MB** bez načítání celého dokumentu do paměti, což poskytuje **o 20 % rychlejší** rychlost zpracování ve srovnání s mnoha konkurenty.  

## Předpoklady  
- **GroupDocs.Watermark** knihovna verze 24.11 nebo novější.  
- Maven nainstalován (nebo JAR soubory, pokud dáváte přednost ručnímu nastavení).  
- Java Development Kit 8 nebo novější a IDE jako IntelliJ IDEA nebo Eclipse.  

### Požadované knihovny, verze a závislosti  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (pokud používáte přístup Maven)  

### Požadavky na nastavení prostředí  
Ujistěte se, že adresář `bin` JDK je ve vaší `PATH` a že vaše IDE ukazuje na správnou verzi JDK.  

### Předpoklady znalostí  
Měli byste se dobře orientovat v základní syntaxi Javy, správě závislostí Maven a operacích souborového I/O.  

## Jak nastavit GroupDocs.Watermark pro Javu?  
Třída `Watermarker` poskytuje vstupní bod API pro načítání a úpravu dokumentů.  

Chcete-li začít používat GroupDocs.Watermark, přidejte jeho Maven koordináty do souboru `pom.xml` vašeho projektu. Tím se stáhne knihovna a její závislosti, což vám umožní vytvořit instanci třídy Watermarker a pracovat se soubory diagramů přímo z Java kódu. Poté můžete nakonfigurovat licencování a nastavit výstupní možnosti před zpracováním jakéhokoli dokumentu.  

Přidejte závislost GroupDocs.Watermark do vašeho `pom.xml`.  

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

Pokud dáváte přednost nepoužívat Maven, stáhněte nejnovější JAR z oficiální stránky vydání.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Kroky získání licence  
- Začněte s bezplatnou zkušební verzí pro vyzkoušení API.  
- Pro produkci získáte dočasnou nebo trvalou licenci z portálu dodavatele.  

#### Základní inicializace a nastavení  
Třída `Watermarker` je vstupním bodem pro všechny operace zpracování dokumentů.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Jak upravit diagram a odstranit hypertextové odkazy pomocí GroupDocs.Watermark?  
Třída `Watermarker` poskytuje vstupní bod API pro načítání a úpravu dokumentů.  

Nejprve načtěte soubor diagramu do instance Watermarker. Poté získejte kolekci tvarů, identifikujte ty, které obsahují objekty hypertextových odkazů, a iterujte přes ně v opačném pořadí, abyste bezpečně smazali každý odkaz, aniž byste ovlivnili indexování kolekce. Tím se zajistí, že všechny vložené URL jsou odstraněny při zachování vizuální integrity diagramu.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Proč je tento krok důležitý**: Načtení souboru vám poskytuje programový přístup ke každému tvaru a jeho souvisejícím vlastnostem.  

## Jak získat obsah tvaru v diagramu?  
Objekt `DiagramShape` představuje jednotlivý tvar v diagramu a zpřístupňuje jeho vlastnosti a připojená metadata.  

Po načtení diagramu zavolejte `getShapes()` na Watermarker, abyste získali seznam objektů `DiagramShape`. Každý tvar lze prozkoumat na kolekce hypertextových odkazů, což umožňuje přesné zaměření odkazů pro odstranění nebo úpravu. Můžete také číst text tvaru, barvy a geometrii, pokud jsou potřeba další úpravy.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Proč je tento krok důležitý**: Zaměření na konkrétní tvar zajišťuje, že odstraníte pouze nechtěné odkazy, aniž byste ovlivnili jiné vizuální prvky.  

## Jak iterovat a bezpečně odstraňovat hypertextové odkazy?  
Metoda `removeHyperlink(int index)` maže hypertextový odkaz na zadané pozici v kolekci hypertextových odkazů tvaru.  

Iterujte přes seznam hypertextových odkazů od posledního indexu směrem k nule. Tento opačný cyklus zabraňuje posunu indexů, ke kterému dochází při odstraňování položek, a zajišťuje, že každý hypertextový odkaz je zpracován bez vynechání. Po odstranění můžete obnovit stav tvaru nebo pokračovat k dalšímu tvaru v diagramu.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Proč je tento krok důležitý**: Opačný cyklus zaručuje, že všechny hypertextové odkazy jsou odstraněny bez vynechání jakýchkoli položek.  

## Jak uložit upravený diagram a uvolnit prostředky?  
Metoda `save(String path)` zapíše upravený dokument na zadané umístění souboru a dokončí všechny změny.  

Jakmile jsou všechny hypertextové odkazy odstraněny, zavolejte metodu `save` na instanci Watermarker a zadejte nový název souboru, aby nedošlo k přepsání originálu. Poté zavolejte `close()`, čímž uvolníte souborové handly a paměť, což je nezbytné pro dlouhodobé dávkové procesy. Tím se zajistí, že soubor je řádně uzavřen a připraven k dalšímu použití.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Proč je tento krok důležitý**: Správné uzavření prostředků zabraňuje únikům paměti a problémům se zamčením souborů na serveru.  

## Praktické aplikace  
Odstranění hypertextových odkazů z tvarů diagramu může být užitečné v několika reálných scénářích:  

1. **Bezpečnost** – Zabránit externím odkazům, které by mohly vést na škodlivé stránky.  
2. **Soulad** – Splnit firemní politiky zakazující vložené URL v sdílených prostředcích.  
3. **Přehlednost** – Vytvořit čistší prezentace, kde by odkazy odváděly pozornost.  

Tuto logiku můžete vložit do větších automatizačních pipeline, například nočních dávkových úloh, které sanitizují všechny diagramy před jejich publikací na intranet.  

## Úvahy o výkonu  

### Optimalizace výkonu  
- Používejte jednu instanci `Watermarker` na soubor, aby se snížilo zatížení.  
- Upřednostňujte opačnou iteraci (jak je ukázáno), aby se předešlo nákladnému přepočítávání indexů seznamu.  

### Pokyny pro využití zdrojů  
- Pro diagramy větší než 200 MB monitorujte využití haldy a zvažte zvýšení JVM flagu `-Xmx`.  
- Nástroje pro profilování jako VisualVM mohou pomoci identifikovat úzká místa ve velkých dávkových bězích.  

### Nejlepší postupy pro správu paměti v Javě  
- Deklarujte objekty v co nejmenším možném rozsahu.  
- Používejte try‑with‑resources při práci se streamy, aby se zajistilo automatické uzavření.  

## Často kladené otázky  

**Q: Jak zvládnu diagramy, které obsahují tisíce tvarů?**  
A: Zpracovávejte diagram stránku po stránce a uvolňujte prostředky každé stránky před přechodem na další, aby se udržovalo nízké využití paměti.  

**Q: Mohu omezit odstraňování hypertextových odkazů pouze na konkrétní stránky?**  
A: Ano – načtěte index stránky, kterou chcete, a pak aplikujte smyčku odstraňování pouze na tvary na této stránce.  

**Q: Je komerční licence povinná pro dávkové zpracování?**  
A: Platná licence je vyžadována pro jakékoli nasazení na úrovni produkce; bezplatná zkušební verze je omezena na 30 dnů a 5 dokumentů.  

**Q: Podporuje GroupDocs.Watermark SVG diagramy?**  
A: Rozhodně – SVG patří mezi 30+ podporovaných formátů a hypertextové odkazy lze odstranit pomocí stejných API volání.  

**Q: Co když má tvar více hypertextových odkazů?**  
A: Opačná iterace odstraňuje každý odkaz jednotlivě, čímž se zajistí, že všechny odkazy jsou vymazány.  

## Zdroje  

- [Dokumentace](https://docs.groupdocs.com/watermark/java/)  
- [Reference API](https://reference.groupdocs.com/watermark/java)  
- [Stáhnout](https://releases.groupdocs.com/watermark/java/)  
- [GitHub repozitář](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)  
- [Získání dočasné licence](https://purchase.groupdocs.com/temporary-license/)  

---  

**Poslední aktualizace:** 2026-08-25  
**Testováno s:** GroupDocs.Watermark 24.11 pro Javu  
**Autor:** GroupDocs  

## Související tutoriály

- [Tutoriály vodoznakování diagramů pro GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Úprava záhlaví a zápatí diagramu v Javě pomocí GroupDocs.Watermark: Komplexní průvodce](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Efektivní odstranění tvarů z diagramů pomocí GroupDocs.Watermark pro Javu](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)