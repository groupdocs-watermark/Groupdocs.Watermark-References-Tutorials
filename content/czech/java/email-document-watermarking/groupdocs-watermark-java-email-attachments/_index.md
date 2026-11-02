---
date: '2025-12-29'
description: Naučte se, jak přidat vodoznak k e‑mailovým přílohám pomocí GroupDocs.Watermark
  pro Javu. Tento průvodce poskytuje krok za krokem instrukce a osvědčené postupy.
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: Přidejte vodoznak do e‑mailových příloh pomocí GroupDocs.Watermark pro Javu
type: docs
url: /cs/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Přidání vodoznaku k přílohám e‑mailu pomocí GroupDocs.Watermark pro Java

## Rychlé odpovědi
- **Co dosahuje “přidání vodoznaku k e‑mailu”?** Vkládá viditelný nebo poloprůhledný štítek (např. „Důvěrné“) do každé podporované přílohy, čímž odrazuje neoprávněné šíření.  
- **Která knihovna je vyžadována?** GroupDocs.Watermark pro Java (nejnovější verze).  
- **Potřebuji licenci?** Zkušební licence funguje pro vývoj; pro produkci je potřeba komerční licence.  
- **Mohu zpracovávat více e‑mailů najednou?** Ano — zabalte kroky do smyčky přes složku se soubory *.msg*.  
- **Jaké typy souborů jsou podporovány?** PDF, Word, Excel, PowerPoint, obrázky a mnoho dalších (viz oficiální dokumentace).

## Co znamená “přidání vodoznaku k e‑mailu”?
Přidání vodoznaku k e‑mailu znamená programově otevřít soubor e‑mailu, extrahovat každou přílohu a nanést na tyto dokumenty vlastní text (nebo obrázek) před odesláním nebo uložením e‑mailu. Tím se zajistí, že vodoznak cestuje se souborem a posiluje důvěrnost i identitu značky.

## Proč použít GroupDocs.Watermark pro Java?
- **Široká podpora formátů** — funguje s PDF, Office soubory, obrázky a dalšími.  
- **Jednoduché API** — pár řádků kódu vám umožní vytvořit, aplikovat a uložit vodoznaky.  
- **Výkonnost‑orientované** — nízká paměťová náročnost, ideální pro serverové zpracování.  
- **Enterprise‑licencování** — zkušební verze pro hodnocení, placená licence pro produkci.

## Předpoklady
- Nainstalovaný Java Development Kit (JDK).  
- IDE, např. IntelliJ IDEA nebo Eclipse.  
- GroupDocs.Watermark pro Java přidaný do vašeho projektu (viz kroky nastavení níže).

## Nastavení GroupDocs.Watermark pro Java

### Maven nastavení
Pokud používáte Maven, přidejte repozitář a závislost do souboru `pom.xml`:

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
Alternativně stáhněte nejnovější verzi z [GroupDocs.Watermark pro Java releases](https://releases.groupdocs.com/watermark/java/).

#### Získání licence
- Pro bezplatnou zkušební verzi se zaregistrujte na webu GroupDocs a požádejte o dočasnou licenci.  
- Pro komerční použití zakupte plnou licenci. Navštivte [purchase page](https://purchase.groupdocs.com/temporary-license/) pro více informací.

### Základní inicializace
Importujte základní třídy, které budete potřebovat:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Jak přidat vodoznak k přílohám e‑mailu — průvodce krok za krokem

### Krok 1: Vytvoření textového vodoznaku
Nejprve definujte text vodoznaku a jeho vzhled.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Krok 2: Nastavení možností načtení e‑mailu
Nakonfigurujte načítač, aby GroupDocs mohl číst soubor *.msg*.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Krok 3: Inicializace Watermarkeru pro váš soubor e‑mailu
Ukazatel `Watermarker` nasměrujte na e‑mail, který chcete zpracovat.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Krok 4: Získání obsahu e‑mailu
Získejte vnitřní strukturu e‑mailu, abyste mohli pracovat s jeho přílohami.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Krok 5: Procházení příloh
Projděte každou přílohu a ověřte, zda ji lze označit vodoznakem.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Krok 6‑9: Přidání vodoznaku k podporovaným přílohám
Pro každý oprávněný soubor otevřete nový `Watermarker`, aplikujte vodoznak a změny zapište zpět do e‑mailu.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Krok 10: Uložení e‑mailu s vodoznakem
Zapište upravený e‑mail do nového souboru, aby originál zůstal nedotčený.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Krok 11: Vyčištění
Uvolněte prostředky uzavřením hlavního `Watermarker`.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Praktické aplikace
1. **Interní sdílení dokumentů** — vložit firemní branding nebo upozornění na důvěrnost do každé přílohy před interním rozesíláním.  
2. **Komunikace s klienty** — ochránit smlouvy, nabídky a finanční výkazy jasným štítkem „Důvěrné“.  
3. **E‑mailové marketingové kampaně** — přidat decentní brandingové vodoznaky do PDF nebo obrázků připojených k propagačním e‑mailům, čímž posílíte povědomí o značce.

## Úvahy o výkonu
- **Správa paměti** — zpracovávejte jednu přílohu najednou a každou `Watermarker` okamžitě uzavírejte.  
- **Velikost přílohy** — velké soubory prodlužují dobu zpracování; před vodoznakováním zvažte kompresi nebo omezení velikosti.  
- **Dávkové zpracování** — procházejte adresář se soubory *.msg* a tak snížíte režii při práci s mnoha e‑maily.

## Často kladené otázky

**Q: Mohu přidávat vodoznaky do šifrovaných souborů?**  
A: Ne. GroupDocs.Watermark nepodporuje vodoznakování šifrovaných dokumentů z bezpečnostních důvodů.

**Q: Jaké typy souborů jsou podporovány pro vodoznakování?**  
A: PDF, Word, Excel, PowerPoint, obrázky (PNG, JPEG, BMP) a mnoho dalších běžných formátů. Viz oficiální dokumentace pro úplný seznam.

**Q: Jak mohu přizpůsobit vzhled mého vodoznaku?**  
A: Můžete změnit rodinu písma, velikost, barvu, neprůhlednost, rotaci a pozici pomocí konstruktoru `TextWatermark` a jeho vlastností.

**Q: Je možné dávkové zpracování více e‑mailů?**  
A: Ano. Zabalte kroky do `for` smyčky, která iteruje přes složku se soubory *.msg*, a aplikujte stejnou logiku na každý z nich.

**Q: Můj vodoznak se nezobrazuje — co mám zkontrolovat?**  
A: Ověřte, že typ souboru přílohy je podporován, že velikost vodoznaku odpovídá rozměrům stránky, a že dokument není chráněn heslem.

## Zdroje
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark pro Java](https://releases.groupdocs.com/watermark/java/)

---

**Poslední aktualizace:** 2025-12-29  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs