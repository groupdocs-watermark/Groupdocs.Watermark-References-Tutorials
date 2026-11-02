---
date: '2025-12-31'
description: Naučte se vyhledávat text e‑mailů pomocí GroupDocs.Watermark pro Javu,
  efektivně spravovat těla, předměty a přílohy.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Jak vyhledávat text e‑mailu pomocí GroupDocs.Watermark Java – komplexní průvodce
type: docs
url: /cs/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Jak vyhledávat text e‑mailu pomocí GroupDocs.Watermark Java

Najít konkrétní frázi v předmětu, těle nebo přílohách e‑mailu může být obtížné — obzvláště když pracujete s desítkami či stovkami zpráv. V tomto tutoriálu se dozvíte, **jak vyhledávat text v e‑mailu** rychle a přesně pomocí **GroupDocs.Watermark pro Java**. Provedeme vás nastavením, kódem i tipy na osvědčené postupy, abyste mohli s důvěrou integrovat vyhledávání textu e‑mailu do svých aplikací.

## Rychlé odpovědi
- **Jaká knihovna mi umožní vyhledávat text v e‑mailu v Javě?** GroupDocs.Watermark pro Java.  
- **Potřebuji licenci?** Pro testování stačí bezplatná zkušební verze; pro produkční nasazení je vyžadována placená licence.  
- **Mohu prohledávat jak předmět, tak tělo?** Ano — nastavte `EmailSearchableObjects` tak, aby zahrnoval Subject, HtmlBody i PlainTextBody.  
- **Je API citlivé na velikost písmen?** Můžete zvolit vyhledávání bez rozlišení velkých a malých písmen nastavením příslušného příznaku v `TextSearchCriteria`.  
- **Jaká verze Javy je požadována?** JDK 8 nebo novější; pro správu závislostí se doporučuje Maven.

## Co je „jak vyhledávat e‑mail“ s GroupDocs.Watermark?
GroupDocs.Watermark poskytuje jednotné API pro vyhledávání, odstraňování nebo úpravu vodoznaků a prostého textu napříč mnoha typy dokumentů — včetně **e‑mailových zpráv** (`.msg`, `.eml`). Využitím modelu vyhledávatelných objektů můžete cílit přesně na části e‑mailu, které vás zajímají, a tak urychlit hromadné zpracování.

## Proč použít GroupDocs.Watermark Java pro vyhledávání v e‑mailu?
- **Jednotné API** — funguje s PDF, obrázky, Office soubory i e‑maily pomocí stejných kódových vzorů.  
- **Optimalizovaný výkon** — vyhledávací operace běží v paměti bez nutnosti externích služeb.  
- **Robustní zpracování** — podporuje HTML i prostý text těla, přílohy a dokonce i heslem chráněné e‑maily.  
- **Snadná integrace** — připravené pro Maven/Gradle, s přehlednou dokumentací a aktivní podporou.

## Předpoklady

- **Java Development Kit (JDK)** 8 nebo novější.  
- **Maven** (nebo Gradle) pro správu závislostí.  
- IDE jako **IntelliJ IDEA** nebo **Eclipse**.  
- Základní znalost syntaxe Javy a formátů e‑mailových souborů (`.msg`, `.eml`).

## Nastavení GroupDocs.Watermark pro Java

### Maven Setup
Přidejte repozitář a závislost do svého `pom.xml`:

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
Alternativně můžete stáhnout nejnovější JAR ze [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence
- **Bezplatná zkušební verze:** Otestujte základní funkce bez licenčního klíče.  
- **Dočasná licence:** Požádejte o časově omezený klíč pro rozšířené hodnocení.  
- **Placená licence:** Zakupte pro neomezené používání v produkci.

#### Základní inicializace
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Průvodce implementací

### Funkce 1: Vyhledávání textu v těle e‑mailu

#### Přehled
Nastavíme API tak, aby prohledávalo **předmět**, **HTML tělo** i **prostý text těla** e‑mailu podle zadaného klíčového slova.

#### Krok 1: Definice cest k dokumentům
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Krok 2: Nastavení možností načtení a Watermarkeru
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Krok 3: Vytvoření kritéria vyhledávání
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Krok 4: Specifikace míst vyhledávání
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Krok 5: Provedení vyhledávání a odstranění vodoznaků
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Krok 6: Uložení změn
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tipy pro řešení problémů
- **Prázdné výsledky:** Ověřte, že klíčové slovo se skutečně vyskytuje ve vybraných částech e‑mailu.  
- **Výkon:** Omezte vyhledávatelné objekty jen na ty, které potřebujete (např. Subject + PlainTextBody), aby se urychlilo zpracování velkých dávkách.

### Funkce 2: Možnosti načtení e‑mailového dokumentu

#### Přehled
`EmailLoadOptions` vám umožňuje řídit, jak je e‑mail parsován — užitečné pro šifrované zprávy nebo vlastní kódování.

#### Krok 1: Konfigurace možností načtení
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Klíčové konfigurační možnosti
- **Ochrana heslem:** Nastavte `loadOptions.setPassword("yourPassword")` pro šifrované soubory `.msg`.  
- **Nastavení kódování:** Upravit `loadOptions.setEncoding(Charset.forName("UTF-8"))` při práci s nestandardními znakovámi sadami.

## Praktické aplikace

- **Automatizované zpracování e‑mailů:** Hromadně skenovat příchozí požadavky podpory na klíčová slova jako „refund“ nebo „error“.  
- **Kontrola právní shody:** Rychle najít důvěrné termíny (např. SSN, čísla kreditních karet) v korporátních archivách pošty.  
- **Automatizace zákaznické podpory:** Směrovat e‑maily na základě detekovaných frází k příslušnému týmu podpory.

## Úvahy o výkonu
- **Správa zdrojů:** Zavolejte `watermarker.close()` hned po dokončení zpracování, aby se uvolnily nativní zdroje.  
- **Paměťové osvědčené postupy:** Při zpracování tisíců zpráv pracujte po dávkách a opakovaně používejte instanci `Watermarker`, pokud je to možné.

## Závěr
Nyní máte solidní, připravený přístup pro **jak vyhledávat text v e‑mailu** pomocí GroupDocs.Watermark Java. Flexibilita API vám umožní cílit na konkrétní části e‑mailu, odstraňovat nechtěné vodoznaky a integrovat logiku do větších pracovních toků.

### Další kroky
- Vyzkoušejte **více kritérií vyhledávání** (např. kombinace „invoice“ + „overdue“).  
- Prozkoumejte **přidání vodoznaku** pro označení e‑mailů obsahujících citlivá data.  
- Ponořte se do dalších typů dokumentů (PDF, DOCX) pomocí stejného workflow Watermarkeru.

## Často kladené otázky

**Q1:** Jak mohu zpracovat šifrované e‑maily pomocí GroupDocs.Watermark?  
**A1:** Použijte `EmailLoadOptions.setPassword("yourPassword")` před vytvořením instance `Watermarker`.

**Q2:** Můžu vyhledávat více klíčových slov najednou?  
**A2:** Ano — vytvořte samostatné objekty `SearchCriteria` pro každé klíčové slovo a spojte je pomocí logických operátorů (např. `OrSearchCriteria`).

**Q3:** Je GroupDocs.Watermark Java zdarma?  
**A3:** Pro hodnocení je k dispozici bezplatná zkušební verze. Pro produkční použití je vyžadována placená licence.

**Q4:** Jak efektivně zpracovat velké objemy e‑mailů?  
**A4:** Omezte vyhledávatelné objekty jen na potřebné, zpracovávejte e‑maily po dávkách a vždy zavírejte `Watermarker`, aby se uvolnily zdroje.

**Q5:** Kde najdu další pomoc nebo podporu?  
**A5:** Navštivte [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) pro komunitní asistenci nebo kontaktujte přímo podporu GroupDocs.

## Zdroje
- **Dokumentace:** Prozkoumejte podrobné návody na [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Přístup k technickým detailům na [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Poslední aktualizace:** 2025-12-31  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs  

---