---
date: '2026-01-21'
description: Naučte se, jak nastavit licenci pro GroupDocs Watermark v Javě, včetně
  toho, jak aplikovat vodoznak na PDF a spravovat používání pomocí měřené licence.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Jak nastavit licenci pro GroupDocs Watermark (měřený) v Javě
type: docs
url: /cs/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Jak nastavit licenci pro GroupDocs Watermark (měřenou) v Javě

Ochrana duševního vlastnictví je pro moderní podniky nejvyšší prioritou a vodoznaky jsou osvědčený způsob, jak toho dosáhnout. V tomto tutoriálu se naučíte **jak nastavit licenci** pro GroupDocs.Watermark pomocí měřeného přístupu, takže můžete **přidávat vodoznak do PDF** souborů a mít plnou kontrolu nad jejich používáním. Provedeme vás všemi kroky od předpokladů až po reálné scénáře použití a ukážeme vám přesně, kde **použít veřejné a soukromé klíče** k aktivaci licence.

## Rychlé odpovědi
- **Co je měřená licence?** Model licencování založený na využití, který sleduje každé volání API.  
- **Potřebuji licenční soubor?** Ne – aktivujete pomocí veřejných a soukromých klíčů.  
- **Jaká verze Javy je vyžadována?** Java 8 nebo vyšší.  
- **Mohu přidávat vodoznaky do PDF dokumentů?** Ano, API podporuje PDF, DOCX, PPTX a obrázky.  
- **Je tato metoda bezpečná?** Ano, klíče jsou přenášeny přes HTTPS a nikdy nejsou uloženy v prostém textu.

## Co je měřená licence a proč ji používat?
Měřená licence vám umožňuje platit jen za to, co skutečně spotřebujete, což ji činí ideální pro SaaS nebo mikro‑službové architektury. Poskytuje funkce **vodoznaku pro zabezpečení dokumentů** bez zátěže správy tradičních licenčních souborů a můžete okamžitě škálovat své využití nahoru i dolů.

## Předpoklady
Předtím, než začnete, ujistěte se, že máte:

1. **GroupDocs.Watermark for Java** ≥ 24.11 (nejnovější verze).  
2. **JDK 8+** nainstalovaný a `JAVA_HOME` nastavený.  
3. **Veřejné a soukromé klíče** získané z vašeho GroupDocs účtu (použijete je v kódu).  

## Nastavení GroupDocs.Watermark pro Java

### Informace o instalaci
Integrujte GroupDocs.Watermark do svého Maven projektu:

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

> **Tip:** Stejná URL repozitáře se používá i pro možnost přímého stažení níže.

#### Přímé stažení
Stáhněte nejnovější JAR z oficiální stránky vydání: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence
Pro odemknutí prémiových funkcí potřebujete dočasnou nebo zkušební licenci. Zaregistrujte se na [webu GroupDocs](https://purchase.groupdocs.com/temporary-license/) a zkopírujte veřejný/soukromý klíč, který vám poskytnou.

### Základní inicializace
Jakmile je knihovna ve vaší classpath, můžete ji inicializovat:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **Proč je to důležité:** I když používáte měřenou licenci, inicializace objektu `License` zajišťuje, že SDK je připraveno přijmout aktivaci založenou na klíčích později v pracovním postupu.

## Průvodce implementací

### Nastavení měřené licence

#### Krok 1: Definujte veřejný a soukromý klíč
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
Tyto klíče **používají veřejné a soukromé klíče** k bezpečné identifikaci vašeho účtu.

#### Krok 2: Vytvořte instanci třídy Metered
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
Třída `Metered` zajišťuje veškeré sledování využití na pozadí.

#### Krok 3: Nastavte měřenou licenci pomocí poskytnutých klíčů
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
 **přid:** zapisovány na disk v prostém textu.  
- **Flexibilita:** Přepínání prostředí (dev, test, prod) bez kopírování souborů.  
- **Škálovatelnost:** Ideální pro cloud‑native nasazení, kde jsou kontejnery neměnné.

## Praktické aplikace
1. **Zabezpečení dokumentů:** Vložte viditelný nebo neviditelný vodoznak do PDF, aby se odradila neautorizovaná distribuce.  
2. **Sledování využití:** Sledujte, kolik dokumentů je zpracováno každý měsíc, což vám pomůže zůstat v rámci vaší měřené kvóty.  
3. **Integrace CMS:** Automaticky **přidávejte vodoznak do PDF** ke každému nahranému souboru v systému pro správu obsahu.

## Úvahy o výkonu
- **Přidávejte vodoznak jen když je potřeba** – vyhněte se zbytečnému zpracování velkých dávek.  
- **Znovu použijte instanci `Metered`** napříč požadavky, aby se snížila zátěž tvorby objektů.  
- **Sledujte paměť** při zpracování vysoce rozlišených obrázků; SDK poskytuje streamingové API pro udržení nízké paměťové stopy.

## Časté problémy a řešení
| Problém | Řešení |
|-------|----------|
| Klíče jsou odmítnuty | Zkontrolujte, že v řetězcích nejsou žádné nadbytečné mezery nebo zalomení řádků. |
| Licence není aktivována | Ujistěte se, že jste zavolali `metered.setMeteredKey(...)` **před** jakoukoliv operací vodoznaku. |
| Chyby nedostatku paměti u velkých PDF | Použijte `WatermarkOptions.setUseMemoryCache(true)`, aby se zpracování přesunulo na disk. |

## Často kladené otázky

**á licence a proč bych ji měl používat?**  
A: Měřená licence sleduje každé volání API, což vám umožní platit jen za skutečné využití a snadno škálovat vaši aplikaci.

**Q: Mohu přepínat mezi zkušebním licenčním souborem a měřeným klíčem?**  
A: Ano. Stačí zavolat `license.setLicense("path/to/file.lic")` pro zkušební verzi a později ji nahradit voláním `metered.setMeteredKey(...)`.

**Q: Co se stane, pokud je veřejný nebo soukromý klíč zadán nesprávně?**  
A: SDK vyhodí výjimku autentizace a zablokuje přístup k prémiovým funkcím.

**Q: Existují omezení, kolik vodoznaků mohu přidat za měsíc?**  
A: Omezení závisí na smlouvě s GroupDocs; podívejte se na svůj dashboard pro přesné kvóty.

**Q: Funguje to i s obrázkovými soubory, nejen s PDF?**  
A: Rozhodně. Stejné API podporuje JPEG, PNG, BMP a další běžné formáty obrázků.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/watermark/java/)
- [Reference API](https://reference.groupdocs.com/watermark/java)
- [Stažení](https://releases.groupdocs.com/watermark/java/)
- [Úložiště GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/watermark/10)
- [Získání dočasné licence](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-01-21  
**Testováno s:** GroupDocs.Watermark 24.11 pro Java  
**Autor:** GroupDocs