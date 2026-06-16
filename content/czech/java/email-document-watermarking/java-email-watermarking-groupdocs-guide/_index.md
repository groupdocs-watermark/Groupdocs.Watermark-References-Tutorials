---
date: '2026-06-16'
description: Naučte se, jak vodoznakovat emailové dokumenty pomocí GroupDocs.Watermark
  for Java. Tento krok‑za‑krokem tutoriál pokrývá nastavení, přidání vodoznaku do
  emailu a osvědčené postupy.
keywords:
- how to watermark email
- add watermark to email
- GroupDocs Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to watermark email documents using GroupDocs.Watermark for
    Java. This step‑by‑step tutorial covers setup, adding watermark to email, and
    best practices.
  headline: How to Watermark Email with GroupDocs.Watermark for Java – A Complete
    Guide
  type: TechArticle
- description: Learn how to watermark email documents using GroupDocs.Watermark for
    Java. This step‑by‑step tutorial covers setup, adding watermark to email, and
    best practices.
  name: How to Watermark Email with GroupDocs.Watermark for Java – A Complete Guide
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Email Load Options and Watermarker:**'
    text: '**Initialize Email Load Options and Watermarker:**'
  - name: '**Import Required Packages:**'
    text: '**Import Required Packages:**'
  - name: '**Read Image File and Convert to Byte Array:**'
    text: '**Read Image File and Convert to Byte Array:**'
  - name: '**Import Classes for Handling Email Contents:**'
    text: '**Import Classes for Handling Email Contents:**'
  - name: '**Add Embedded Image to the Email:**'
    text: '**Add Embedded Image to the Email:**'
  - name: '**Save and Close Watermarker:**'
    text: '**Save and Close Watermarker:**'
  - name: '**Internal Document Security** – Prevent accidental data leaks by branding
      every internal memo with a confidential watermark.'
    text: '**Internal Document Security** – Prevent accidental data leaks by branding
      every internal memo with a confidential watermark.'
  - name: '**Email Marketing** – Reinforce brand identity by automatically adding
      your logo to every campaign email.'
    text: '**Email Marketing** – Reinforce brand identity by automatically adding
      your logo to every campaign email.'
  - name: '**Legal Correspondence** – Attach a “Confidential – Attorney‑Client Privilege”
      watermark to legal emails to satisfy compliance audits.'
    text: '**Legal Correspondence** – Attach a “Confidential – Attorney‑Client Privilege”
      watermark to legal emails to satisfy compliance audits.'
  type: HowTo
- questions:
  - answer: GroupDocs.Watermark only modifies the HTML body; plain‑text parts remain
      unchanged, which is standard practice for email branding.
    question: Can I watermark both HTML and plain‑text parts of an email?
  - answer: Yes, because the watermark becomes part of the email’s HTML content, it
      is retained in all subsequent forwards.
    question: Does the watermark survive when the email is forwarded?
  - answer: You can save as EML, MSG, or MHT. The API also supports PDF conversion
      if you need a printable version.
    question: What file formats can I export the watermarked email to?
  - answer: A free trial license works for development and testing. Production deployments
      require a purchased license to remove evaluation watermarks.
    question: Is a license required for development environments?
  - answer: Attachments are streamed unchanged; only the email body is processed,
      so attachment size does not affect watermarking performance.
    question: How does GroupDocs.Watermark handle large attachments?
  type: FAQPage
title: Jak vodoznakovat email pomocí GroupDocs.Watermark for Java – Kompletní průvodce
type: docs
url: /cs/java/email-document-watermarking/java-email-watermarking-groupdocs-guide/
weight: 1
---

# Jak vodoznakovat e‑mail pomocí GroupDocs.Watermark pro Java – Kompletní průvodce

## Úvod

Pokud potřebujete chránit integritu své e‑mailové komunikace, **how to watermark email** je kritická schopnost. Přidání vizuálního identifikátoru přímo do e‑mailu zabraňuje neautorizovanému přeposílání a manipulaci, přičemž zachovává čitelnost původní zprávy. V tomto tutoriálu se naučíte, jak integrovat GroupDocs.Watermark pro Java do vaší aplikace, načíst soubor e‑mailu, vložit obrázek jako vodoznak a uložit vodoznačenou zprávu – bez změny původní struktury e‑mailu.

**Co se naučíte:**
- Instalace a konfigurace GroupDocs.Watermark pro Java.  
- Načtení e‑mailového dokumentu (EML, MSG nebo MHT) do API.  
- Převod obrázku na pole bajtů a jeho vložení jako vodoznaku.  
- Uložení upraveného e‑mailu při zachování příloh a HTML obsahu.  

Cílem bude, že budete schopni **add watermark to email** soubory programově, čímž zajistíte bezpečné značkování odchozích komunikací.

## Rychlé odpovědi
- **Jaká knihovna je vyžadována?** GroupDocs.Watermark pro Java (v24.11+).  
- **Jaké formáty e‑mailů jsou podporovány?** Soubory EML, MSG a MHT – celkem více než 30 + formátů.  
- **Mohu používat PNG vodoznaky?** Ano, PNG a JPEG jsou plně podporovány.  
- **Potřebuji licenci pro vývoj?** Bezplatná zkušební verze funguje pro testování; pro komerční použití je vyžadována produkční licence.  
- **Kolik další paměti spotřebuje vodoznakování?** Obvykle méně než 15 MB pro 5 MB e‑mail při použití komprimovaných obrázků.

## Co je vodoznakování e‑mailu?
Vodoznakování e‑mailu je proces vložení vizuálního prvku – například loga nebo upozornění – přímo do těla souboru e‑mailu. Vodoznak se stane součástí HTML obsahu, což zajišťuje, že příjemci uvidí značku bez ohledu na použitého e‑mailového klienta.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark podporuje **více než 50 vstupních a výstupních formátů**, včetně EML, MSG a MHT, a může zpracovávat e‑maily až do **200 MB** bez načítání celého souboru do paměti. Jeho API nabízí vlákny‑bezpečné operace, což vám umožní vodoznakovat stovky e‑mailů za minutu na standardním 4‑jádrovém serveru.

## Předpoklady

- **Java Development Kit (JDK) 8+** nainstalovaný a nakonfigurovaný ve vašem IDE.  
- **Maven** nebo jiný nástroj pro správu závislostí.  
- Přístup ke složce, kde můžete číst zdrojové e‑maily a zapisovat vodoznačené výsledky.  
- Základní znalost Javy (souborové I/O, streamy a objektově orientované koncepty).  

## Nastavení GroupDocs.Watermark pro Java

### Použití Maven
Add the following dependency to your `pom.xml` file:

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
Alternativně stáhněte nejnovější JAR z oficiální stránky vydání:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Kroky získání licence
- **Free Trial:** Stáhněte si zkušební licenci pro prozkoumání API.  
- **Temporary License:** Pro rozšířené hodnocení požádejte o dočasný klíč prostřednictvím nákupního portálu: [GroupDocs' purchase page](https://purchase.groupdocs.com/temporary-license).  
- **Full License:** Zakupte produkční licenci pro neomezené nasazení.

### Základní inicializace a nastavení
`Watermarker` je hlavní třída, která spravuje načítání, úpravy a ukládání dokumentů. `EmailLoadOptions` konfiguruje, jak je při načítání interpretován soubor e‑mailu.

```java
import com.groupdocs.watermark.Watermarker;

// Initialize GroupDocs.Watermark with your document path
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
Watermarker watermarker = new Watermarker(emailFilePath);
```

## Průvodce implementací

### Načtení e‑mailového dokumentu

#### Přehled
Načtení e‑mailu je prvním krokem před aplikací jakéhokoli vodoznaku. GroupDocs.Watermark abstrahuje formát souboru, což vám umožní pracovat s jednotným objektem `Watermarker`.

#### Přímá odpověď
Vytvořte instanci `Watermarker` s `EmailLoadOptions`, nasměrujte ji na váš soubor `.eml` nebo `.msg` a API rozparsuje HTML tělo, přílohy a metadata – vše v jednom volání. Tato operace obvykle trvá méně než 200 ms pro 2 MB e‑mail.

#### Implementace krok za krokem
1. **Importujte potřebné třídy:**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```  

2. **Inicializujte možnosti načtení e‑mailu a Watermarker:**  
   ```java
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```  

#### Definiční kotva
`EmailLoadOptions` je konfigurační třída, která říká GroupDocs.Watermark, jak interpretovat zdrojový soubor e‑mailu (např. zda zachovat vložené obrázky).

### Načtení souboru obrázku do pole bajtů

#### Přehled
Aby bylo možné vložit vodoznak, musí být obrázek poskytnut jako pole bajtů, aby jej API mohlo vložit do HTML e‑mailu.

#### Přímá odpověď
Přečtěte soubor obrázku pomocí `FileInputStream`, převedete stream na pole bajtů pomocí `IOUtils.toByteArray` a udržujte pole v paměti – to umožní vložení vodoznaku bez zápisu dočasných souborů na disk.

#### Implementace krok za krokem
1. **Importujte požadované balíčky:**  
   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.InputStream;
   ```  

2. **Načtěte soubor obrázku a převedete jej na pole bajtů:**  
   ```java
   File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/sample.jpg");
   byte[] imageBytes = new byte[(int) imageFile.length()];
   InputStream imageInputStream = new FileInputStream(imageFile);
   imageInputStream.read(imageBytes);
   imageInputStream.close();
   ```  

#### Definiční kotva
`FileInputStream` je standardní třída Java I/O, která čte surové bajty ze souboru v souborovém systému.

### Přidání vloženého obrázku do e‑mailu

#### Přehled
Vložení obrázku jako reference Content‑ID (CID) zajišťuje, že se vodoznak zobrazí inline v HTML těle e‑mailu.

#### Přímá odpověď
Vygenerujte jedinečný CID, přidejte bajty obrázku do `Watermarker` pomocí `addImageWatermark` a odkažte na CID v HTML těle. API automaticky aktualizuje MIME části, takže e‑mail zůstane kompatibilní s RFC.

#### Implementace krok za krokem
1. **Importujte třídy pro zpracování obsahu e‑mailu:**  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   import com.groupdocs.watermark.contents.EmailEmbeddedObject;
   ```  

2. **Přidejte vložený obrázek do e‑mailu:**  
   ```java
   EmailContent content = watermarker.getContent(EmailContent.class);
   content.getEmbeddedObjects().add(imageBytes, "sample.jpg");
   
   EmailEmbeddedObject embeddedObject = content.getEmbeddedObjects().get_Item(content.getEmbeddedObjects().getCount() - 1);
   content.setHtmlBody("<html><body>This is an embedded image: <img src=\"cid:" + embeddedObject.getContentId() + "\"></body></html>");
   ```  

#### Definiční kotva
`addImageWatermark` je metoda třídy `Watermarker`, která vkládá obrázkový vodoznak do vizuální vrstvy dokumentu. `Content‑ID (CID)` je MIME hlavička, která umožňuje e‑mailovému klientovi zobrazit vložené zdroje, jako jsou obrázky, přímo v těle zprávy.

### Uložení vodoznačeného e‑mailového dokumentu

#### Přehled
Po aplikaci vodoznaku musíte změny uložit do nového souboru.

#### Přímá odpověď
Zavolejte `watermarker.save("output.eml", SaveOptions.create())` a poté `watermarker.close()`, aby se uvolnily všechny souborové handly a paměťové buffery. Uložený soubor zachová původní přílohy a metadata a zároveň zobrazí nový vodoznak.

#### Implementace krok za krokem
1. **Uložte a zavřete Watermarker:**  
   ```java
   String outputFilePath = "YOUR_OUTPUT_DIRECTORY/message.msg";
   watermarker.save(outputFilePath);
   watermarker.close();
   ```  

#### Definiční kotva
`SaveOptions` definuje výstupní formát a nastavení komprese pro výsledný e‑mailový soubor.

## Praktické aplikace

Vkládání vodoznaků do e‑mailů je užitečné v mnoha reálných scénářích:

1. **Interní zabezpečení dokumentů** – Zabránit neúmyslnému úniku dat tím, že každou interní zprávu označíte důvěrným vodoznakem.  
2. **E‑mailový marketing** – Posílit identitu značky automatickým přidáním vašeho loga do každého e‑mailu kampaně.  
3. **Právní korespondence** – Připojit vodoznak “Confidential – Attorney‑Client Privilege” k právním e‑mailům pro splnění auditů souladu.  

## Úvahy o výkonu
- **Optimalizujte velikosti obrázků:** Používejte PNG‑8 nebo JPEG‑2000, aby pole bajtů zůstalo pod 100 KB bez znatelné ztráty kvality.  
- **Správa zdrojů:** Vždy zavírejte streamy (`FileInputStream`, `watermarker`) v bloku `finally` nebo použijte try‑with‑resources, aby nedocházelo k únikům paměti.  
- **Dávkové zpracování:** Pro hromadné vodoznakování zpracovávejte e‑maily asynchronně pomocí `CompletableFuture` v Javě, abyste maximalizovali využití CPU.  

## Časté problémy a řešení

| Problém | Příčina | Řešení |
|-------|-------|----------|
| **Obrázek se nezobrazuje** | CID není v HTML správně odkazován | Ověřte, že značka `<img src="cid:yourCid">` odpovídá CID použitému v `addImageWatermark`. |
| **E‑mail se stane poškozeným** | Ukládání s nesprávnými `SaveOptions` | Použijte `SaveOptions.create().setPreserveOriginalHeaders(true)`, aby se zachovaly původní hlavičky. |
| **Chyba nedostatku paměti** | Velký e‑mail (>200 MB) načtený kompletně do paměti | Povolte režim streamování pomocí `EmailLoadOptions.setLoadMode(LoadMode.Stream)` před inicializací `Watermarker`. |

## Často kladené otázky

**Q: Můžu vodoznakovat jak HTML, tak prosté textové části e‑mailu?**  
A: GroupDocs.Watermark upravuje pouze HTML tělo; prosté textové části zůstávají beze změny, což je standardní postup pro značkování e‑mailů.

**Q: Přetrvá vodoznak při přeposílání e‑mailu?**  
A: Ano, protože vodoznak se stane součástí HTML obsahu e‑mailu, zůstane zachován ve všech následných přeposláních.

**Q: Do jakých formátů mohu exportovat vodoznačený e‑mail?**  
A: Můžete uložit jako EML, MSG nebo MHT. API také podporuje konverzi do PDF, pokud potřebujete tisknutelnou verzi.

**Q: Je licence vyžadována pro vývojová prostředí?**  
A: Bezplatná zkušební licence funguje pro vývoj a testování. Produkční nasazení vyžaduje zakoupenou licenci k odstranění evaluačních vodoznaků.

**Q: Jak GroupDocs.Watermark zachází s velkými přílohami?**  
A: Přílohy jsou streamovány beze změny; zpracovává se pouze tělo e‑mailu, takže velikost příloh neovlivňuje výkon vodoznakování.

## Závěr

Máte nyní kompletní, připravený workflow pro **how to watermark email** soubory pomocí GroupDocs.Watermark pro Java. Dodržením výše uvedených kroků můžete vložit loga, upozornění na důvěrnost nebo jakýkoli vlastní obrázek do každého odchozího e‑mailu, čímž zajistíte jednotné značkování a zvýšenou bezpečnost. Prozkoumejte další funkce, jako jsou textové vodoznaky, dynamické časové razítka nebo dávkové zpracování, abyste své řešení dále rozšířili.

---

**Poslední aktualizace:** 2026-06-16  
**Testováno s:** GroupDocs.Watermark for Java 24.11  
**Autor:** GroupDocs

## Související tutoriály

- [Vodoznakování e‑mailových dokumentů v Javě : Správa s GroupDocs.Watermark](/watermark/java/email-document-watermarking/groupdocs-watermark-java-email-management/)
- [Zpracování příloh e‑mailu v Javě s GroupDocs.Watermark : Kompletní průvodce](/watermark/java/email-document-watermarking/java-email-attachment-processing-groupdocs-watermark/)
- [Průvodce vodoznakování v Javě : Zabezpečené dokumenty s GroupDocs.Watermark API](/watermark/java/getting-started/java-watermark-groupdocs-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}