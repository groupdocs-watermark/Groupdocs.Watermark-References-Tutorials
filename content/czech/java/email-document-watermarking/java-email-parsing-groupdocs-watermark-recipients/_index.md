---
date: '2026-01-03'
description: Naučte se, jak v Javě vypsat příjemce e‑mailu pomocí GroupDocs.Watermark
  – automatizujte extrakci polí To, CC a BCC z e‑mailových dokumentů.
keywords:
- Java email parsing
- GroupDocs.Watermark Java
- listing email recipients
title: Seznam e‑mailových příjemců v Javě s GroupDocs.Watermark
type: docs
url: /cs/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Seznam příjemců e‑mailů v Javě s GroupDocs.Watermark

Extrahování každé adresy **To**, **CC** a **BCC** z e‑mailového souboru může být únavné, když zpracováváte desítky nebo stovky zpráv. V tomto tutoriálu se naučíte, jak **list email recipients java** rychle a spolehlivě pomocí knihovny GroupDocs.Watermark pro Javu. Provedeme vás nastavením, ukázkami kódu a reálnými příklady, abyste tuto funkci mohli začlenit do svých aplikací.

## Quick Answers
- **Co tento kód dělá?** Otevře e‑mailový soubor a vypíše všechny adresy To, CC a BCC.  
- **Která knihovna je vyžadována?** GroupDocs.Watermark pro Javu (verze 24.11).  
- **Umí číst soubory .msg a .eml?** Ano – API podporuje běžné e‑mailové formáty.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována plná licence.  
- **Je možný hromadný (batch) processing?** Rozhodně – můžete iterovat přes více souborů pomocí stejného vzoru.

## Introduction

Už vás nebaví ručně procházet e‑mailová data a získávat seznamy příjemců? Automatizace tohoto úkolu může ušetřit čas a snížit chyby, zejména při práci s velkým objemem e‑mailů. Tento průvodce vám ukáže, jak využít výkonnou knihovnu GroupDocs.Watermark proavu k analýze e‑mailových dokumentů a **list email recipients java** efektivně.

**What You'll Learn**
- Nastavení prostředí pro používání GroupDocs.Watermark pro Javu  
- Načtení a inicializace e‑mailového dokumentu pomocí API GroupDocs.Watermark  
- Získání seznamů příjemců To, CC a BCC z e‑mailových dokumentů  
- Praktické aplikace a úvahy o výkonu  

Začněme s pokrytím předpokladů.

## Prerequisites

Než se ponoříte do kódu, ujistěte se, že je vaše prostředí připravené:

### Required Libraries, Versions, and Dependencies

Budete potřebovat nainstalovaný GroupDocs.Watermark pro Javu. Tento průvodce používá verzi 24.11.

### Environment Setup Requirements

- **Java Development Kit (JDK):** Verze 8 nebo vyšší  
- **Integrované vývojové prostředí (IDE):** Doporučeno IntelliJ IDEA nebo Eclipse  
- **Správa závislostí:** Maven nebo přímé stažení  

### Knowledge Prerequisites

Základní znalost programování v Javě a povědomí o práci s e‑mailovými formáty (např. soubory .msg) bude užitečné.

## Setting Up GroupDocs.Watermark for Java

Pro začátek musíte nastavit svůj projekt s potřebnými závislostmi. Zde je návod, jak na to:

**Maven Setup**

Přidejte následující konfiguraci do souboru `pom.xml`, aby se zahrnul GroupDocs.Watermark:

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

**Direct Download**

Alternativně stáhněte nejnovější verzi z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition Steps

- **Bezplatná zkušební verze:** Začněte s bezplatnou zkušební verzí a prozkoumejte funkce.  
- **Dočasná licence:** Požádejte o dočasnou licenci, pokud potřebujete prodloužený přístup pro testovací účely.  
- **Nákup:** Zvažte zakoupení licence pro produkční použití.

Jakmile je nastavení připravené, inicializujme a připravme prostředí pro zpracování e‑mailových dokumentů.

## How to List Email Recipients Java – Implementation Guide

Tato sekce rozděluje každou funkci na zvládnutelné kroky, abyste mohli efektivně implementovat analýzu e‑mailů pomocí GroupDocs.Watermark.

### Load and Initialize Email Document

**Přehled**  
Načtení e‑mailového dokumentu je prvním krokem naší cesty. Tento proces zahrnuje inicializaci objektu `Watermarker`, který slouží jako brána k interakci se soubory e‑mailů.

**Kroky implementace**

1. **Import Required Classes**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```
2. **Define Email File Path and Load Options**  
   Zadejte cestu k vašemu e‑mailovému dokumentu. Nahraďte `"YOUR_DOCUMENT_DIRECTORY/email.msg"` skutečnou cestou.  
   ```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```
3. **Resource Management**  
   Vždy nezapomeňte po použití zavřít instanci `Watermarker`, aby se uvolnily systémové prostředky.  
   ```java
   watermarker.close();
   ```

### List All Direct Recipients of an Email

**Přehled**  
Získání přímých (To) příjemců je jednoduché, jakmile máte e‑mailový dokument inicializovaný.

**Kroky implementace**

1. **Retrieve Email Content**  
   Ujistěte se, že objekt `watermarker` je již inicializován, jak bylo ukázáno v předchozí sekci.  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```
2. **Iterate and List Recipients**  
   Projděte seznam přímých příjemců a vytiskněte každou e‑mailovou adresu.  
   ```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### List All CC Recipients of an Email

**Přehled**  
Výpis CC příjemců následuje podobný proces jako výpis přímých příjemců, což vám umožní přístup k dalším e‑mailovým adresám zahrnutým v poli CC.

**Kroky implementace**

1. **Retrieve and Iterate**  
   Použijte objekt `EmailContent` z předchozího kroku:  
   ```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### List All BCC Recipients of an Email

**Přehled**  
I když BCC příjemci nejsou viditelní v hlavičce e‑mailu, můžete je stále získat pomocí GroupDocs.Watermark.

**Kroky implementace**

1. **Access and Display BCC Addresses**  
   ```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Practical Applications

Tyto funkce lze integrovat do různých systémů, například:

- **Systémy pro správu e‑mailů:** Automatizujte kategorizaci a zpracování e‑mailů na základě seznamů příjemců.  
- **Nástroje pro analýzu dat:** Extrahujte data o příjemcích pro analytiku a identifikaci komunikačních vzorců v organizaci.  
- **Bezpečnostní software:** Monitorujte e‑mailový provoz k detekci neoprávněného sdílení nebo úniků.

## Performance Considerations

Při práci s velkým objemem e‑mailů zvažte následující tipy:

- **Optimalizace využití zdrojů:** Po použití co nejdříve zavřete objekt `Watermarker`.  
- **Správa paměti:** Dbejte na garbage collection Javy a využití paměti při zpracování více souborů.  
- **Hromadné zpracování:** Zpracovávejte e‑maily po dávkách, aby se snížilo zatížení systémových zdrojů.

## Frequently Asked Questions

**Q: Jak mohu řešit chyby při analýze e‑mailů?**  
A: Ujistěte se, že cesty k souborům jsou správné, soubory odpovídají očekávaným formátům, a obalte kód do bloků try‑catch pro zachycení `IOException` nebo `GroupDocsException`.

**Q: Můžu tuto knihovnu použít s jinými e‑mailovými formáty, jako je .eml?**  
A: Ano, GroupDocs.Watermark podporuje různé e‑mailové formáty. Podívejte se do dokumentace na možnosti načítání specifické pro formát.

**Q: Jaké jsou běžné úskalí při výpisu příjemců?**  
A: Nesprávné cesty k souborům, nepodporované typy souborů nebo zapomenutí zavřít instanci `Watermarker` mohou způsobit úniky zdrojů.

**Q: Jak mohu zlepšit výkon při analýze mnoha e‑mailů?**  
A: Zpracovávejte soubory paralelně pomocí `ExecutorService` v Javě, ale sledujte využití CPU a paměti, aby nedošlo k přetížení.

**Q: Kde mohu získat pomoc, pokud narazím na problémy?**  
A: Navštivte [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/watermark/10) pro komunitní pomoc a oficiální podporu.

## Additional Resources

- **Dokumentace:** [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Stáhnout:** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  

## Conclusion

Nyní jste se naučili, jak efektivně **list email recipients java** pomocí GroupDocs.Watermark pro Javu. Tento výkonný nástroj může zjednodušit procesy správy e‑mailů a otevřít nové možnosti pro analýzu dat a automatizaci.

**Další kroky**

- Prozkoumejte další funkce v [GroupDocs.Watermark API](https://docs.groupdocs.com/watermark/java/).  
- Integrovat tyto úryvky do větších projektů nebo pipeline pro hromadné zpracování.  
- Experimentujte s různými konfiguracemi, aby vyhovovaly vašim konkrétním potřebám.

---

**Last Updated:** 2026-01-03  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs