---
date: '2026-04-07'
description: Naučte se, jak vyhledávat v těle e‑mailu v Javě pomocí GroupDocs.Watermark,
  včetně toho, jak vyhledávat více klíčových slov v e‑mailu a jak odstranit vodoznaky
  z e‑mailu.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Vyhledávání v těle e‑mailu v Javě s GroupDocs.Watermark: komplexní průvodce'
type: docs
url: /cs/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Vyhledávání těla e‑mailu v Javě pomocí GroupDocs.Watermark

Pokud potřebujete **search email body java** rychle a spolehlivě, jste na správném místě. V tomto tutoriálu si projdeme, jak GroupDocs.Watermark pro Javu umožňuje najít konkrétní text v předmětech e‑mailů, HTML tělech a prostých textech, a jak můžete následně odstranit nechtěné vodoznaky. Na konci budete schopni implementovat robustní řešení, které funguje na jedné nebo více klíčových slovech a dokonce odstraňuje vodoznaky e‑mailů podle potřeby.

## Rychlé odpovědi
- **Co znamená “search email body java”?** Odkazuje na použití Java kódu (s GroupDocs.Watermark) k nalezení textu v obsahu e‑mailu.  
- **Mohu najednou vyhledávat více klíčových slov v e‑mailu?** Ano – vytvořte samostatné objekty `SearchCriteria` a spojte je.  
- **Jak odstranit vodoznaky e‑mailu?** Použijte metodu `PossibleWatermarkCollection.clear()` po vyhledávání.  
- **Potřebuji licenci?** Bezplatná zkušební verze stačí pro testování; pro produkci je vyžadována trvalá licence.  
- **Které IDE je nejlepší?** IntelliJ IDEA nebo Eclipse jsou plně podporovány.

## Co se naučíte
- Instalace a konfigurace GroupDocs.Watermark pro Javu.  
- Nastavení kritérií vyhledávání pro **search email body java** napříč předměty a těly.  
- Techniky pro **search multiple keywords email** v jednom běhu.  
- Přesné kroky **how to remove email watermarks** po jejich nalezení.  

## Proč vyhledávat tělo e‑mailu v Javě pomocí GroupDocs.Watermark?
GroupDocs.Watermark poskytuje vysoce úrovňové API, které abstrahuje složitosti parsování souborů .msg, zpracování různých formátů těla a správy vodoznaků. To vám ušetří čas oproti tvorbě vlastního parseru a zajišťuje konzistentní výsledky u velkých šarží e‑mailů.

## Požadavky
- Java Development Kit (JDK) 8 nebo novější.  
- Maven (nebo možnost přidat JAR soubory ručně).  
- Základní znalost Javy a formátů souborů e‑mailů (.msg, .eml).  

## Nastavení GroupDocs.Watermark pro Javu
GroupDocs.Watermark pro Javu zjednodušuje vkládání vodoznaků a vyhledávání textu v dokumentech, včetně e‑mailů. Níže jsou dva nejčastější způsoby, jak přidat knihovnu do vašeho projektu.

### Nastavení Maven
Include the following in your `pom.xml` file to add GroupDocs.Watermark as a dependency:
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
Alternativně můžete stáhnout nejnovější verzi přímo z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Kroky získání licence
- **Free Trial:** Začněte s bezplatnou zkušební verzí pro testování základních funkcí.  
- **Temporary License:** Získejte dočasnou licenci pro rozšířený přístup a testování.  
- **Purchase:** Zvažte zakoupení, pokud GroupDocs.Watermark splňuje vaše potřeby.

#### Základní inicializace
Initialize the `Watermarker` class as shown below:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Průvodce implementací

### Funkce 1: Vyhledávání textu v těle e‑mailu
Tato funkce umožňuje vyhledávat konkrétní text v předmětu a těle e‑mailu.

#### Přehled
Ukážeme, jak nakonfigurovat GroupDocs.Watermark pro prohledávání různých částí e‑mailové zprávy pomocí Java kódu.

##### Krok 1: Definování cest k dokumentům
Set up your input and output paths for handling emails:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Krok 2: Nastavení možností načtení a Watermarkeru
Initialize the `EmailLoadOptions` and `Watermarker` to work with your email document.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Krok 3: Vytvoření kritérií vyhledávání
Define criteria for searching text. We'll use a case‑insensitive search for the keyword **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Krok 4: Určení míst vyhledávání
Configure the search to cover both the subject and body of emails:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Krok 5: Provedení vyhledávání a vymazání vodoznaků
Perform the search and remove any found watermarks:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Krok 6: Uložení změn
After processing, save your changes to a new document:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tipy pro řešení problémů
- **Common Issue:** Pokud jsou výsledky vyhledávání prázdné, ujistěte se, že text je přítomen v těle e‑mailu nebo v předmětu.  
- **Performance Tip:** Optimalizujte omezením vyhledávání pouze na sekce, které skutečně potřebujete.

### Funkce 2: Možnosti načtení e‑mailového dokumentu
Tato sekce popisuje, jak můžete nastavit další možnosti při načítání e‑mailového dokumentu pro zpracování pomocí GroupDocs.Watermark.

#### Přehled
Konfigurace možností načtení poskytuje větší kontrolu nad tím, jak jsou dokumenty zpracovávány, např. nastavení ochrany heslem nebo kódování.

##### Krok 1: Konfigurace možností načtení
Here's a basic setup for `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Klíčové konfigurační možnosti
- **Password Protection:** Zadejte hesla, pokud jsou vaše e‑maily šifrované.  
- **Encoding Settings:** Definujte konkrétní typy kódování podle potřeby.

## Jak vyhledávat více klíčových slov v e‑mailu
Pokud potřebujete najít několik výrazů najednou, vytvořte více objektů `SearchCriteria` a spojte je pomocí logických operátorů **OR** nebo **AND**. API vám umožňuje řetězit kritéria, takže můžete vyhledávat „invoice“ **or** „receipt“ bez spouštění samostatných smyček.

## Jak odstranit vodoznaky e‑mailu
Po nalezení vodoznaků (nebo jakéhokoli textu odpovídajícího vašim kritériím) metoda `PossibleWatermarkCollection.clear()` je odstraní z e‑mailového dokumentu. Toto je přesný krok, který jsme použili v **Step 5** výše, a funguje pro libovolný počet shod.

## Praktické aplikace

### Případ použití 1: Automatizované zpracování e‑mailů
Automatizujte filtrování a zpracování hromadných e‑mailových dat pro efektivní vyhledávání konkrétního obsahu.

### Případ použití 2: Kontroly právní shody
Zajistěte shodu vyhledáváním citlivých informací v korporátních e‑mailových zprávách.

### Případ použití 3: Automatizace zákaznické podpory
Zjednodušte pracovní postupy podpory rychlým vyhledáváním klíčových slov nebo frází v dotazech zákazníků.

## Úvahy o výkonu
Při používání GroupDocs.Watermark zvažte následující pro optimalizaci výkonu:
- **Resource Management:** Efektivně spravujte paměť a výpočetní výkon pro zpracování velkých datových sad e‑mailů.  
- **Java Memory Management Best Practices:** Pravidelně monitorujte využití zdrojů a uvolňujte je včas.

## Často kladené otázky

**Q:** Jak mohu zpracovat šifrované e‑maily pomocí GroupDocs.Watermark?  
**A:** Použijte `EmailLoadOptions` k zadání hesel při inicializaci `Watermarker`.

**Q:** Mohu vyhledávat více klíčových slov najednou?  
**A:** Ano, vytvořte samostatné instance `SearchCriteria` a spojte je pomocí logických operací.

**Q:** Je GroupDocs.Watermark pro Javu zdarma?  
**A:** K dispozici je bezplatná zkušební verze; zvažte zakoupení licence pro rozšířené funkce.

**Q:** Jak efektivně zpracovat velké objemy e‑mailů?  
**A:** Optimalizujte vyhledávání zaměřením na konkrétní sekce e‑mailů a efektivní správou zdrojů.

**Q:** Kde mohu najít další pomoc nebo podporu?  
**A:** Navštivte [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) pro komunitní podporu nebo kontaktujte jejich bezplatný kanál podpory.

## Zdroje
- **Documentation:** Prozkoumejte podrobné návody na [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Získejte technické podrobnosti na [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Last Updated:** 2026-04-07  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs