---
date: '2026-04-04'
description: Naučte se, jak odstranit odkazy z tvarů diagramu pomocí GroupDocs.Watermark
  Java, a zajistit tak bezpečnost a přehlednost dokumentu.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Jak odstranit odkazy z tvarů diagramu pomocí GroupDocs.Watermark Java
type: docs
url: /cs/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak odstranit odkazy z tvarů diagramu pomocí GroupDocs.Watermark Java

Správa digitálních dokumentů často zahrnuje úpravu diagramů, zejména když potřebujete **jak odstranit odkazy** z důvodu bezpečnosti nebo přehlednosti. V tomto tutoriálu se naučíte jednoduchý, krok‑za‑krokem postup, jak odstranit nechtěné hypertextové odkazy z tvarů diagramu pomocí výkonné knihovny **GroupDocs.Watermark** pro Java. Na konci budete mít čisté diagramy bez odkazů, které jsou bezpečné ke sdílení.

## Rychlé odpovědi
- **Co znamená “how to strip links”?** Odkazuje na odstranění objektů hypertextových odkazů vložených do tvarů diagramu.  
- **Která knihovna to řeší?** GroupDocs.Watermark pro Java (verze 24.11 nebo novější).  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována platná licence.  
- **Mohu zpracovávat mnoho souborů najednou?** Ano – zabalte kód do smyčky nebo dávkového úkolu.  
- **Je tento přístup jazykově specifický?** Příklad je v Javě, ale stejný koncept platí i pro jiné .NET/Java API.

## Co znamená “how to strip links” při úpravě diagramu?
Odstranění odkazů znamená vyhledání objektů hypertextových odkazů připojených k tvarům uvnitř diagramu (např. Visio *.vsdx) a jejich smazání. Tím se odstraní externí URL, které by mohly odhalit citlivé informace nebo narušit tok prezentace.

## Proč použít GroupDocs.Watermark pro Java?
- **Přesnost** – Přímý přístup k objektům tvarů a jejich kolekcím hypertextových odkazů.  
- **Výkon** – Optimalizováno pro velké diagramy bez načítání celého dokumentu do paměti.  
- **Podpora napříč formáty** – Funguje s mnoha formáty diagramů (Visio, Draw.io, atd.).  

## Požadavky
- **GroupDocs.Watermark** knihovna ≥ 24.11.  
- Maven (nebo ruční zahrnutí JAR).  
- Java JDK 8 nebo novější.  
- IDE, např. IntelliJ IDEA nebo Eclipse.

## Nastavení GroupDocs.Watermark pro Java
### Nastavení Maven
Add the repository and dependency to your `pom.xml`:

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
If you prefer not to use Maven, grab the latest JAR from the official site:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Kroky získání licence
- Začněte stažením bezplatné zkušební verze.  
- Pro produkci získáte dočasnou nebo plnou licenci z portálu GroupDocs.

#### Základní inicializace a nastavení
Create a `Watermarker` instance that points to the folder containing your diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak odstranit odkazy z tvarů diagramu
Below is a concise, four‑step process that shows **remove hyperlinks java** in action.

### Krok 1: Načíst soubor diagramu
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Proč?* Načtení souboru vám poskytne programový přístup k jeho stránkám, tvarům a kolekcím hypertextových odkazů.

### Krok 2: Přístup k obsahu tvaru
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Proč?* Potřebujete odkaz na konkrétní tvar, který může obsahovat hypertextové odkazy.

### Krok 3: Procházet a odstraňovat hypertextové odkazy
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Proč?* Procházení v opačném směru zabraňuje problémům s posunem indexu při mazání položek z kolekce.

### Krok 4: Uložit a zavřít
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Proč?* Uložení zapíše vyčištěný diagram na disk a zavření uvolní souborové handly, aby nedošlo k únikům paměti.

## Praktické aplikace odstraňování odkazů
1. **Bezpečnost** – Odstraňte externí URL, které by mohly vést k phishingu nebo úniku dat.  
2. **Shoda** – Zajistěte, aby diagramy splňovaly interní zásady před distribucí.  
3. **Čistota prezentace** – Odstraňte zbytečné klikatelné oblasti, které ruší diváky.

## Úvahy o výkonu
- **Efektivita smyčky** – Použijte vzor opačného procházení uvedený výše.  
- **Správa zdrojů** – Upřednostněte `try‑with‑resources` nebo explicitní volání `close()`.  
- **Velké soubory** – Sledujte CPU/paměť; zvažte zpracování stránek po dávkách.

## Časté problémy a řešení
- **Nebyly nalezeny žádné hypertextové odkazy** – Ověřte, že diagram skutečně obsahuje objekty hypertextových odkazů; některé formáty je ukládají jinak.  
- **IndexOutOfBoundsException** – Vždy procházejte v opačném směru při odstraňování položek z kolekce.  
- **Chyby licence** – Ujistěte se, že soubor licence je správně umístěn nebo předán konstruktoru `Watermarker`.

## Často kladené otázky

**Q: Jak zvládnout více tvarů na více stránkách?**  
A: Procházejte `content.getPages()` a poté každou stránku pomocí kolekce `getShapes()`, přičemž na každý tvar použijete stejnou logiku odstraňování.

**Q: Mohu filtrovat odkazy podle domény místo celé URL?**  
A: Ano – změňte kontrolu `contains` tak, aby hledala řetězec domény (např. `"example.com"`).

**Q: Existuje způsob, jak zaznamenat, které odkazy byly odstraněny?**  
A: V rámci smyčky zachyťte `shape.getHyperlinks().get_Item(i).getAddress()` před odstraněním a zapište jej do logovacího souboru.

**Q: Funguje to s PDF diagramy vloženými v jiných dokumentech?**  
A: GroupDocs.Watermark podporuje mnoho formátů; ujistěte se, že typ souboru je rozpoznán jako diagram (Visio, VDX, atd.).

**Q: Jaká licence je potřebná pro dávkové zpracování?**  
A: Pro jakékoli ne‑zkušební, vysokokapacitní operace je vyžadována plná produkční licence.

## Závěr
Nyní máte kompletní, produkčně připravenou metodu pro **jak odstranit odkazy** z tvarů diagramu pomocí GroupDocs.Watermark pro Java. Začleňte ji do svých pipeline pro zpracování dokumentů, abyste zvýšili bezpečnost, shodu a vizuální kvalitu.

### Další kroky
- Prozkoumejte další funkce manipulace, jako je přidávání vodoznaků nebo razítkování textu.  
- Kombinujte tuto rutinu se službou sledování souborů, aby se diagramy automaticky čistily při nahrávání.

---

**Last Updated:** 2026-04-04  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

## Zdroje
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)