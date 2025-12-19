---
date: '2025-12-19'
description: Naučte se, jak pomocí GroupDocs.Watermark Java odstranit hypertextové
  odkazy z tvarů diagramu, což je klíčový krok pro zabezpečení Java dokumentů a hromadné
  odstraňování hypertextových odkazů.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Jak odstranit hypertextové odkazy z tvarů diagramu pomocí GroupDocs.Watermark
  Java
type: docs
url: /cs/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak odstranit hypertextové odkazy z tvarů diagramu pomocí GroupDocs.Watermark Java

Správa digitálních dokumentů často zahrnuje úpravu diagramů, zejména při **odstraňování hypertextových odkazů** z důvodu bezpečnosti nebo přehlednosti. V tomto tutoriálu se naučíte **jak odstranit hypertextové odkazy** z tvarů diagramu pomocí GroupDocs.Watermark pro Java, aby vaše soubory zůstaly čisté, bezpečné a profesionální.

## Rychlé odpovědi
- **Jaký je hlavní účel?** Odstranit nechtěné hypertextové odkazy z tvarů diagramu pro lepší zabezpečení dokumentu.  
- **Která knihovna se používá?** GroupDocs.Watermark pro Java (verze 24.11 nebo novější).  
- **Potřebuji licenci?** Zkušební verze funguje pro testování; pro produkci je vyžadována platná licence.  
- **Mohu zpracovávat mnoho souborů najednou?** Ano – stejnou logiku lze umístit do smyčky pro dávkové zpracování.  
- **Je Java 8 dostačující?** Java 8+ je podporována; doporučují se novější JDK.

## Co znamená „odstranění hypertextových odkazů“ v kontextu diagramů?
Odstranění hypertextových odkazů znamená smazání URL odkazů připojených k tvarům uvnitř souboru diagramu (např. Visio *.vsdx). Tato operace zabraňuje náhodnému přesměrování na externí stránky a pomáhá splnit požadavky na shodu nebo interní bezpečnostní politiky.

## Proč použít GroupDocs.Watermark Java pro tento úkol?
- **Robustní podpora formátů** – funguje s širokou škálou typů diagramů.  
- **Detailní API** – umožňuje cílit na jednotlivé tvary a jejich kolekce hypertextových odkazů.  
- **Optimalizovaný výkon** – vhodný jak pro jednotlivé soubory, tak pro hromadné zpracování.

## Předpoklady
- **Knihovna GroupDocs.Watermark** verze 24.11 nebo novější.  
- Maven nebo přímé stažení JAR (viz kroky nastavení níže).  
- Java Development Kit (JDK 8 nebo novější) a IDE jako IntelliJ IDEA nebo Eclipse.

## Nastavení GroupDocs.Watermark pro Java
Pro začátek zahrňte knihovnu do svého projektu pomocí Maven nebo stažením JAR.

### Nastavení Maven
Add the following configuration to your `pom.xml`:

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
Alternativně stáhněte nejnovější verzi z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Kroky získání licence
- Začněte s bezplatnou zkušební verzí pro vyzkoušení API.  
- Pro produkci získejte dočasnou nebo plnou licenci z portálu GroupDocs.

#### Basic Initialization and Setup
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak odstranit hypertextové odkazy z tvarů diagramu
Níže je podrobný návod, který vás provede načtením diagramu, vyhledáním tvarů a odstraněním nechtěných hypertextových odkazů.

### Step 1: Load the Diagram File
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Proč?* Načtení souboru vám poskytne programový přístup k jeho vnitřní struktuře.

### Step 2: Access Shape Content
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Proč?* Potřebujete odkaz na konkrétní tvar, který může obsahovat hypertextové odkazy.

### Step 3: Iterate and Remove Hyperlinks
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Proč?* Iterace pozpátku zabraňuje chybám indexu při mazání položek ze sbírky.

### Step 4: Save and Close
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Proč?* Uložení změn a uvolnění zdrojů zabraňuje únikům paměti a zamčeným souborům.

## Dávkové odstranění hypertextových odkazů (pokročilý případ použití)
Pokud potřebujete najednou vyčistit mnoho diagramů, zabalte výše uvedenou logiku do smyčky, která iteruje přes seznam cest k souborům. Použijí se stejné API volání; stačí změnit vstupní a výstupní adresáře pro každou iteraci. Tento přístup odpovídá požadavkům na **dávkové odstranění hypertextových odkazů** pro velké úložiště dokumentů.

## Praktické aplikace
Odstranění hypertextových odkazů z tvarů diagramu může být užitečné v několika reálných scénářích:

1. **Bezpečnostní účely** – Zabránit externím odkazům, které by mohly vystavit vaši síť phishingu nebo malwaru.  
2. **Shoda** – Splnit firemní politiky zakazující odchozí URL v sdílených dokumentech.  
3. **Přehlednost** – Vytvořit čistší prezentace, kde jsou hypertextové odkazy zbytečné nebo rušivé.  

## Úvahy o výkonu
### Optimalizace výkonu
- Použijte vzor iterace pozpátku uvedený výše pro udržení efektivity smyček.  
- Uzavřete objekt `Watermarker` co nejdříve po dokončení, aby se uvolnila paměť.

### Pokyny pro využití zdrojů
- Sledujte CPU a RAM při zpracování velkých diagramů.  
- Pro hromadné úlohy zvažte streamování souborů místo načítání všech najednou.

### Nejlepší praktiky pro správu paměti v Javě
- Vyhněte se vytváření objektů uvnitř těsných smyček.  
- Používejte try‑with‑resources tam, kde je to vhodné, pro automatické čištění.

## Často kladené otázky
1. **Jak zacházet s více tvary?**  
   Iterujte přes všechny stránky a jejich tvary a aplikujte stejnou logiku odstraňování hypertextových odkazů na každý tvar.  

2. **Lze tento proces automatizovat pro velké dávky diagramů?**  
   Ano – vložte kód do rutiny pro dávkové zpracování nebo jej integrujte se svým systémem pro správu dokumentů.  

3. **Co když potřebuji odstranit hypertextové odkazy jen z konkrétních stránek?**  
   Přistupte k požadované stránce podle jejího indexu (`content.getPages().get_Item(pageIndex)`) a zaměřte se jen na tvary na této stránce.  

4. **Je pro produkční použití GroupDocs.Watermark potřeba licence?**  
   Platná komerční licence je vyžadována po uplynutí zkušební doby.  

5. **Lze tuto metodu použít s jinými formáty diagramů?**  
   GroupDocs.Watermark podporuje mnoho typů diagramů; ověřte kompatibilitu v oficiální dokumentaci.  

**Další otázky a odpovědi**

**Q:** *Je možné zaznamenat, které hypertextové odkazy byly odstraněny?*  
**A:** Ano – před voláním `removeAt(i)` zachyťte `shape.getHyperlinks().get_Item(i).getAddress()` a zapište jej do souboru protokolu.

**Q:** *Ovlivní odstranění hypertextových odkazů vizuální vzhled tvaru?*  
**A:** Ne. Geometrie tvaru zůstane nezměněna; pouze metadata odkazu jsou odstraněna.

**Q:** *Je potřeba po odstranění znovu aplikovat nějaké stylování?*  
**A:** Obvykle ne. Odstranění hypertextových odkazů nemění výplň, čáru ani textové styly.

## Závěr
Nyní máte kompletní, připravenou metodu pro **odstranění hypertextových odkazů** z tvarů diagramu pomocí GroupDocs.Watermark pro Java. Dodržením výše uvedených kroků můžete zabezpečit své diagramy, splnit politiky a udržet své dokumenty v profesionálním vzhledu.

---

**Poslední aktualizace:** 2025-12-19  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs  

**Zdroje**  
- [Dokumentace](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Stáhnout](https://releases.groupdocs.com/watermark/java/)  
- [GitHub úložiště](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)  
- [Získání dočasné licence](https://purchase.groupdocs.com/temporary-license/)