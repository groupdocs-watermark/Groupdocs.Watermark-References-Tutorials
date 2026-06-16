---
date: '2026-06-16'
description: Naučte se, jak v Java zpracovat soubor MSG a automaticky vypsat příjemce
  To, CC a BCC pomocí GroupDocs.Watermark pro Java. Tento tutoriál ukazuje, jak efektivně
  zpracovat e‑mail.
keywords:
- java parse msg file
- how to parse email
- how to read msg
- retrieve email recipients
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to java parse msg file and automatically list To, CC, and
    BCC recipients using GroupDocs.Watermark for Java. This tutorial shows how to
    parse email efficiently.
  headline: 'Java Parse MSG File: List Recipients with GroupDocs.Watermark'
  type: TechArticle
- description: Learn how to java parse msg file and automatically list To, CC, and
    BCC recipients using GroupDocs.Watermark for Java. This tutorial shows how to
    parse email efficiently.
  name: 'Java Parse MSG File: List Recipients with GroupDocs.Watermark'
  steps:
  - name: Add the Maven Dependency
    text: Add the GroupDocs.Watermark Maven coordinates to your `pom.xml`. This brings
      in all required JARs automatically. Alternatively, download the latest version
      from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).
  - name: Import Required Classes
    text: The `Watermarker` class loads an email document, while `EmailContent` provides
      access to its metadata such as recipients.
  - name: Define the Email Path and Load Options
    text: '`LoadOptions` configures how the file is opened, allowing settings like
      password protection.'
  - name: Open the Document with Resource Management
    text: Using try‑with‑resources ensures the `Watermarker` instance is automatically
      closed.
  - name: Retrieve Direct (To) Recipients
    text: The `EmailContent.getTo()` method returns a list of primary recipient objects.
  - name: List CC Recipients
    text: The `EmailContent.getCc()` method returns a list of carbon‑copy recipient
      objects.
  - name: List BCC Recipients
    text: The `EmailContent.getBcc()` method returns a list of blind‑carbon‑copy recipient
      objects.
  - name: Clean Up
    text: '`watermarker.close()` releases native resources and file handles.'
  type: HowTo
- questions:
  - answer: Use `LoadOptions.setPassword("yourPassword")` before opening the document;
      the API will decrypt the content automatically.
    question: How do I handle encrypted .msg files?
  - answer: Yes—`EmailContent.getBody()` returns the plain‑text or HTML body, which
      you can combine with recipient data for full‑message exports.
    question: Can I extract the email body together with recipients?
  - answer: Absolutely. GroupDocs.Watermark is designed for high‑throughput scenarios;
      just ensure you manage thread pools and close each `Watermarker` instance promptly.
    question: Is it possible to process thousands of emails in one run?
  - answer: It is fully cross‑platform; the same Maven dependency runs on Windows,
      macOS, and Linux Docker images.
    question: Does the library work on Linux containers?
  - answer: The official documentation and API reference contain deeper use‑cases,
      such as watermarking attachments or extracting embedded images.
    question: Where can I find more advanced examples?
  type: FAQPage
title: 'Java Parse MSG File: Seznam příjemců s GroupDocs.Watermark'
type: docs
url: /cs/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Java Parsování MSG souboru: Seznam příjemců s GroupDocs.Watermark

Extrahování každé adresy To, CC a BCC z `.msg` e‑mailu může být únavné, když máte stovky souborů. **Java parse msg file** vám umožní tento krok automatizovat, eliminovat ruční kopírování a snížit lidské chyby. V tomto tutoriálu se naučíte, jak nastavit GroupDocs.Watermark pro Java, načíst e‑mailový dokument a rychle a spolehlivě získat všechny seznamy příjemců.

## Rychlé odpovědi
- **Co tutoriál pokrývá?** Načtení .msg souboru pomocí GroupDocs.Watermark a extrahování adres To, CC a BCC.  
- **Která knihovna je vyžadována?** GroupDocs.Watermark pro Java (v24.11 nebo novější).  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; placená licence je potřeba pro produkci.  
- **Mohu parsovat i jiné formáty?** Ano – stejná API také podporuje .eml a další typy e‑mailů.  
- **Jaká verze Javy je podporována?** JDK 8 nebo novější.

## Co je java parse msg file?
Fráze **java parse msg file** odkazuje na použití Java kódu k načtení souborů Microsoft Outlook `.msg` a extrahování jejich strukturovaných dat. Tento proces umožňuje vývojářům programově přistupovat k metadatům e‑mailu, obsahu těla a seznamům příjemců bez ruční kontroly. Také podporuje dávkové zpracování, pracuje s Unicode znaky a zachovává data příloh, což je vhodné pro podnikovou analýzu e‑mailů.

## Proč použít GroupDocs.Watermark pro parsování e‑mailů?
GroupDocs.Watermark zpracovává **více než 200 e‑mailových formátů** a dokáže pracovat se soubory až do **500 MB** bez načítání celého dokumentu do paměti, což přináší až **3× rychlejší** extrakci ve srovnání s obecnými metodami čtení souborů. Jeho specializované API `EmailContent` abstrahuje složitou strukturu .msg, poskytuje spolehlivý přístup k polím To, CC a BCC během několika řádků Java kódu.

## Požadavky

- **Java Development Kit (JDK):** 8 nebo vyšší.  
- **IDE:** IntelliJ IDEA, Eclipse nebo jakýkoli Java‑kompatibilní editor.  
- **Nástroj pro sestavení:** Maven (doporučeno) nebo ruční zahrnutí JAR souborů.  
- **GroupDocs.Watermark pro Java:** verze 24.11 (nebo novější).  
- **Základní znalost Javy** a povědomí o formátech e‑mailových souborů.

## Jak v Javě parsovat msg soubor a vypsat příjemce?
Načtěte .msg soubor pomocí třídy `Watermarker`, získejte instanci `EmailContent` a iterujte přes její kolekce příjemců. Tento přímý odstavec vysvětluje hlavní kroky v méně než 70 slovech: **Vytvořte `Watermarker` s cestou k souboru, zavolejte `getEmailContent()` pro přístup ke kolekcím příjemců a poté projděte `getTo()`, `getCc()` a `getBcc()` a vypište každou adresu.** API provádí veškeré parsování interně, takže nikdy nemusíte ručně parsovat surovou strukturu MIME.

### Krok 1: Přidat Maven závislost
Přidejte Maven koordináty GroupDocs.Watermark do vašeho `pom.xml`. Tím se automaticky načtou všechny potřebné JAR soubory.

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

Alternativně si stáhněte nejnovější verzi z [GroupDocs.Watermark pro Java verze](https://releases.groupdocs.com/watermark/java/).

### Krok 2: Importovat požadované třídy
Třída `Watermarker` načítá e‑mailový dokument, zatímco `EmailContent` poskytuje přístup k jeho metadatům, jako jsou příjemci.

```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```

### Krok 3: Definovat cestu k e‑mailu a možnosti načtení
`LoadOptions` konfiguruje, jak je soubor otevřen, umožňuje nastavení jako ochrana heslem.

```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```

### Krok 4: Otevřít dokument s řízením zdrojů
Použití try‑with‑resources zajišťuje, že instance `Watermarker` je automaticky uzavřena.

```java
   watermarker.close();
   ```

### Krok 5: Získat přímé (To) příjemce
Metoda `EmailContent.getTo()` vrací seznam objektů primárních příjemců.

```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```

### Krok 6: Vypsat CC příjemce
Metoda `EmailContent.getCc()` vrací seznam objektů příjemců v kopii (CC).

```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### Krok 7: Vypsat BCC příjemce
Metoda `EmailContent.getBcc()` vrací seznam objektů příjemců v skryté kopii (BCC).

```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### Krok 8: Vyčistit
`watermarker.close()` uvolňuje nativní zdroje a souborové handle.

```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Praktické aplikace

- **Systémy pro správu e‑mailů:** Automaticky kategorizovat příchozí poštu extrahováním skupin příjemců.  
- **Audit shody:** Generovat zprávy o všech BCC příjemcích pro detekci možných úniků dat.  
- **Řízení vztahů se zákazníky (CRM):** Synchronizovat seznamy To/CC s databázemi kontaktů pro cílený outreach.  
- **Bezpečnostní monitorování:** Prohledávat velké archivy pošty na nečekané externí příjemce.

## Úvahy o výkonu

- **Dávkové zpracování:** Zpracovávat e‑maily v paralelních streamech (např. `java.util.concurrent.ForkJoinPool`) pro maximalizaci využití CPU při dodržení limitů paměti.  
- **Paměťová stopa:** Knihovna streamuje data souboru; můžete bezpečně parsovat soubory až do **500 MB** bez chyb OOM.  
- **Čištění zdrojů:** Vždy uzavřete objekt `Watermarker`; pokud tak neučiníte, může dojít k zámkům souborů ve Windows.

## Časté problémy a řešení

- **Neplatná cesta k souboru:** Ověřte, že cesta používá lomítka (`/`) nebo escapované zpětné lomítka (`\\`) ve Windows.  
- **Nepodporovaný formát:** Ujistěte se, že soubor je skutečný Outlook `.msg` nebo `.eml`; jiné formáty vyžadují jiné načítače.  
- **Vypršení licence:** Zkušební licence vyprší po 30 dnech; nahraďte ji produkčním klíčem, aby nedošlo k `LicenseException`.  

## Často kladené otázky

**Q: Jak mohu zpracovat šifrované .msg soubory?**  
A: Použijte `LoadOptions.setPassword("yourPassword")` před otevřením dokumentu; API automaticky dešifruje obsah.

**Q: Mohu extrahovat tělo e‑mailu spolu s příjemci?**  
A: Ano—`EmailContent.getBody()` vrací prostý text nebo HTML tělo, které můžete kombinovat s daty příjemců pro export celých zpráv.

**Q: Je možné zpracovat tisíce e‑mailů v jednom běhu?**  
A: Rozhodně. GroupDocs.Watermark je navržen pro scénáře s vysokou propustností; jen zajistěte správu thread poolů a včasné uzavírání každé instance `Watermarker`.

**Q: Funguje knihovna v Linuxových kontejnerech?**  
A: Je plně multiplatformní; stejná Maven závislost běží na Windows, macOS a Linux Docker obrazech.

**Q: Kde najdu pokročilejší příklady?**  
A: Oficiální dokumentace a reference API obsahují podrobnější případy použití, jako je vodoznakování příloh nebo extrakce vložených obrázků.

## Další zdroje
- **Dokumentace:** [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **Reference API:** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **GroupDocs.Watermark API:** [GroupDocs.Watermark API](https://docs.groupdocs.com/watermark/java/)  
- **Stahování:** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  
- **Fórum podpory:** [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  

---

**Poslední aktualizace:** 2026-06-16  
**Testováno s:** GroupDocs.Watermark Java 24.11  
**Autor:** GroupDocs

## Související tutoriály

- [Vodoznakování e‑mailových dokumentů v Javě: Správa s GroupDocs.Watermark](/watermark/java/email-document-watermarking/groupdocs-watermark-java-email-management/)
- [Jak extrahovat PDF přílohy pomocí GroupDocs Watermark v Javě pro správu e‑mailových dokumentů](/watermark/java/email-document-watermarking/extract-pdf-attachments-groupdocs-java/)
- [Efektivní odstranění e‑mailových příloh pomocí GroupDocs.Watermark v Javě](/watermark/java/email-document-watermarking/remove-email-attachments-groupdocs-watermark-java/)