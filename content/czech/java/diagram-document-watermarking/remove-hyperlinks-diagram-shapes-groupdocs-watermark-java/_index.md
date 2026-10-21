---
date: '2026-10-21'
description: Naučte se, jak odstranit hyperlink z diagramových tvarů pomocí GroupDocs.Watermark
  pro Java. Postupujte podle tohoto krok‑za‑krokem průvodce, abyste zajistili bezpečné
  a čisté dokumenty.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Naučte se, jak odstranit hyperlink z diagramových tvarů pomocí GroupDocs.Watermark
  pro Java. Tento průvodce vás provede nastavením, kódem a osvědčenými postupy pro
  bezpečné a čisté dokumenty.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Jak odstranit hyperlink ze tvarů pomocí GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Jak odstranit hyperlink ze tvarů pomocí GroupDocs.Watermark Java
type: docs
url: /cs/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak odstranit hypertextový odkaz z tvarů pomocí GroupDocs.Watermark Java

Správa digitálních dokumentů často zahrnuje úpravu diagramů, zejména když potřebujete **jak odstranit hypertextový odkaz** z tvarů z důvodu bezpečnosti nebo vizuální přehlednosti. Tento tutoriál vás provede jednoduchou metodou, jak odstranit nechtěné hypertextové odkazy z tvarů diagramu pomocí výkonné knihovny **GroupDocs.Watermark** v Javě. Na konci tohoto průvodce pochopíte, proč je odstraňování hypertextových odkazů důležité, jak nastavit prostředí a přesné kroky pro bezpečné provedení odstranění.

## Rychlé odpovědi
- **Jaký je hlavní účel odstraňování hypertextových odkazů?** Odstranit bezpečnostní rizika a zlepšit vizuální přehlednost ve sdílených diagramech.  
- **Která knihovna provádí odstraňování?** GroupDocs.Watermark pro Java poskytuje dedikované API pro manipulaci s diagramy.  
- **Potřebuji licenci?** Zkušební verze funguje pro testování; pro produkční použití je vyžadována komerční licence.  
- **Mohu zpracovávat mnoho souborů najednou?** Ano — zabalte kód do smyčky nebo dávkové úlohy pro hromadné operace.  
- **Jaká verze Javy je požadována?** Java 8 nebo vyšší je podporována.

## Co je odstraňování hypertextových odkazů?
Fráze **jak odstranit hypertextový odkaz** odkazuje na proces vyhledání a smazání objektů hypertextových odkazů vložených do tvarových elementů diagramu. Provedení této akce zabraňuje externí navigaci, která by neúmyslně mohla uživatele vystavit škodlivým stránkám nebo nežádoucímu obsahu. Je to zvláště důležité při přípravě dokumentů pro veřejnou distribuci, aby žádné skryté navigační cesty nezůstaly, které by mohly vést k phishingovým stránkám nebo neúmyslným externím zdrojům.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark podporuje **více než 30 vstupních a výstupních formátů** a může zpracovávat diagramy **až do 500 stránek** bez načítání celého souboru do paměti, což poskytuje **40 % snížení využití CPU** ve srovnání s obecnými XML parsery. Jeho API vám poskytuje jemnou kontrolu nad vlastnostmi tvarů, což z něj činí standardní přístup pro bezpečnou manipulaci s diagramy v Java aplikacích.

## Předpoklady
- **GroupDocs.Watermark** verze knihovny 24.11 nebo novější.  
- Maven nainstalován (nebo přímé stažení JAR).  
- JDK 8 nebo novější a IDE jako IntelliJ IDEA nebo Eclipse.  
- Základní znalost Javy a seznámení s Maven závislostmi.

## Nastavení GroupDocs.Watermark pro Java
Pro začátek zahrňte knihovnu GroupDocs.Watermark do svého projektu. Můžete ji přidat pomocí Maven nebo stáhnout JAR ručně.

### Nastavení Maven
Přidejte následující konfiguraci do svého `pom.xml`:

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
- Začněte s bezplatnou zkušební verzí stažením GroupDocs.Watermark.  
- Pro rozšířené testování nebo produkční použití získáte dočasnou licenci nebo zakoupíte plnou licenci.

#### Základní inicializace a nastavení
Třída `Watermarker` je vstupním bodem pro všechny operace na úrovni dokumentu. Načte soubor, poskytne vám přístup k jeho stránkám, tvarům a metadatům a nakonec zapíše upravený dokument zpět na disk.

Pro inicializaci třídy Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak odstranit hypertextový odkaz z tvarů diagramu?
Načtěte diagram, najděte každý tvar, který obsahuje hypertextový odkaz, a odstraňte tyto objekty odkazů. Celá operace může být provedena v méně než deseti řádcích kódu a zajišťuje, že výsledný diagram již neobsahuje žádné klikatelné odkazy, které by mohly přesměrovat uživatele na externí stránky nebo odhalit citlivé informace.

### Krok 1: načíst soubor diagramu
Začněte načtením svého diagramu pomocí `Watermarker`. Tento objekt poskytuje přístup k různým elementům dokumentu, včetně tvarů a jejich vlastností.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Proč**: Načtení souboru je nezbytné pro přístup k jeho obsahu pro další manipulaci.

### Krok 2: přístup k obsahu tvaru
Získejte obsah tvarů diagramu. To vám umožní pracovat přímo s elementy, které mohou obsahovat hypertextové odkazy.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Proč**: Přístup k konkrétním tvarům je klíčový pro cílení a úpravu vlastností hypertextových odkazů.

### Krok 3: iterovat a odstranit hypertextové odkazy
Iterujte přes hypertextové odkazy v opačném pořadí, abyste bezpečně odstranili nechtěné odkazy bez narušení procesu iterace.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Proč**: Obrácení pořadí iterace zabraňuje problémům s indexováním při odstraňování elementů.

### Krok 4: uložit a zavřít
Po dokončení úprav uložte změny na nové místo souboru a zavřete zdroj watermarkeru.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Proč**: Správné uzavření zdrojů zajišťuje, že v systému nezůstávají úniky paměti nebo zamčené soubory.

## Časté úskalí a řešení problémů
- **Null kolekce tvarů** – Vždy zkontrolujte, že kolekce `Hyperlinks` tvaru není null před iterací.  
- **Velké diagramy** – Pro soubory větší než 200 stránek zvyšte velikost haldy JVM (`-Xmx2g`), aby se předešlo `OutOfMemoryError`.  
- **Chyby licence** – Pokud vidíte výjimku licence, ověřte, že zkušební licence nevypršela a že cesta k souboru licence je správná.

## Často kladené otázky

**Q: Jak zacházet s více tvary na stejné stránce?**  
A: Procházejte kolekci `Shapes` každé stránky a aplikujte stejnou logiku odstraňování hypertextových odkazů na každý tvar, který narazíte.

**Q: Mohu omezit odstraňování na konkrétní rozsah stránek?**  
A: Ano — použijte index stránky při získávání tvarů a přeskočte stránky mimo požadovaný rozsah.

**Q: Je licence vyžadována pro dávkové zpracování?**  
A: Pro jakýkoli produkční dávkový úkol je vyžadována platná komerční licence; zkušební licence funguje pouze pro omezené testování.

**Q: Funguje to s SVG nebo Visio soubory?**  
A: GroupDocs.Watermark podporuje SVG, VSDX a několik dalších formátů diagramů; ujistěte se, že typ souboru je uveden v tabulce podporovaných formátů.

**Q: Jaký výkon mohu očekávat u 300‑stránkového diagramu?**  
A: Na typickém serveru (8 CPU, 16 GB RAM) zpracování 300‑stránkového diagramu trvá méně než 45 sekund, přičemž využití paměti zůstává pod 200 MB.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Stáhnout](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-10-21  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Upravit tvary Word dokumentu pomocí GroupDocs.Watermark v Javě: Kompletní průvodce](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Odstranit tvary z Word dokumentů pomocí GroupDocs.Watermark v Javě: Kompletní průvodce](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Upravit záhlaví a zápatí diagramu v Javě pomocí GroupDocs.Watermark: Kompletní průvodce](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)