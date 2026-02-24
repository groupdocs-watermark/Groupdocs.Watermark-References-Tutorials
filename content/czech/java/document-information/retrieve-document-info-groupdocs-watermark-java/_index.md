---
date: '2026-02-24'
description: Naučte se, jak získat stránky, načíst informace o dokumentu a zjistit
  typ souboru v Javě pomocí GroupDocs.Watermark pro Javu. Postupujte podle našeho
  krok‑za‑krokem průvodce s ukázkami kódu.
keywords:
- retrieve document information Java
- GroupDocs Watermark Java setup
- Java document info retrieval
title: Jak získat stránky a načíst informace o dokumentu pomocí GroupDocs.Watermark
  pro Javu
type: docs
url: /cs/java/document-information/retrieve-document-info-groupdocs-watermark-java/
weight: 1
---

# Jak získat stránky a načíst informace o dokumentu pomocí GroupDocs.Watermark pro Java

Extrahování metadat dokumentu — **jak získat stránky**, typ souboru, velikost a další — je běžnou požadavkou při vytváření aplikací v Javě zaměřených na dokumenty. V tomto tutoriálu uvidíte přesně, jak získat stránky a další užitečné informace pomocí **GroupDocs.Watermark for Java**. Provedeme vás nastavením, kódem a praktickými tipy, abyste mohli okamžitě začít číst metadata dokumentu.

## Rychlé odpovědi
- **Jak získat stránky?** Použijte `watermarker.getDocumentInfo().getPageCount()`.
- **Jak získat typ souboru v Javě?** Zavolejte `info.getFileType()` na objektu `IDocumentInfo`.
- **Mohu přečíst velikost dokumentu?** Ano — `info.getSize()` vrací velikost v bajtech.
- **Potřebuji licenci?** Bezplatná zkušební verze nebo dočasná licence funguje pro vývoj; pro produkci je vyžadována plná licence.
- **Je Maven podporován?** Rozhodně — přidejte repozitář GroupDocs a závislost do vašeho `pom.xml`.

## Co je extrakce informací o dokumentu?

Extrakce informací o dokumentu znamená programově číst metadata souboru (typ, počet stránek, velikost atd.) bez jeho otevření pro úpravy. Tato data vám pomáhají rozhodovat, například při směrování, validaci nebo dávkovém zpracování.

## Proč použít GroupDocs.Watermark pro Java?

GroupDocs.Watermark nejen přidává vodoznaky, ale také poskytuje lehké API pro **čtení metadat dokumentu**. Podporuje desítky formátů (DOCX, PDF, PPTX atd.) a funguje na Java 8+.

## Předpoklady

- **GroupDocs.Watermark for Java** ≥ 24.11  
- JDK 8 nebo vyšší  
- Maven (nebo ruční stažení JAR)  
- Základní znalost Java I/O  

## Nastavení GroupDocs.Watermark pro Java

Knihovnu můžete integrovat pomocí Maven nebo stažením JAR souboru přímo.

**Konfigurace Maven**

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

**Přímé stažení**

Alternativně můžete stáhnout nejnovější verzi z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence

1. Navštivte [GroupDocs Purchase page](https://purchase.groupdocs.com/temporary-license/) a požádejte o dočasnou licenci.  
2. Postupujte podle dokumentace a aplikujte licenční soubor ve vašem projektu.

## Základní inicializace

```java
import com.groupdocs.watermark.Watermarker;
import java.io.FileInputStream;

// Initialize FileInputStream with your document path
FileInputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source.docx");

// Create a Watermarker instance
Watermarker watermarker = new Watermarker(stream);
```

## Jak získat stránky pomocí GroupDocs.Watermark pro Java

Níže je stručný, krok za krokem průvodce, který ukazuje **jak získat stránky** a další metadata.

### Krok 1: Otevřete souborový stream

```java
import java.io.FileInputStream;

// Open the FileStream for the input document
FileInputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source.docx");
```

*Proč tento krok?* Poskytuje API odkaz na fyzický soubor, aby mohl číst jeho vlastnosti.

### Krok 2: Inicializujte objekt Watermarker

```java
import com.groupdocs.watermark.Watermarker;

// Initialize a Watermarker with the file stream
Watermarker watermarker = new Watermarker(stream);
```

*Klíčová rada:* Ověřte, že cesta k souboru je správná a že aplikace má oprávnění ke čtení.

### Krok 3: Získejte informace o dokumentu

```java
import com.groupdocs.watermark.common.IDocumentInfo;

// Get document information
IDocumentInfo info = watermarker.getDocumentInfo();
```

Toto volání vrací objekt `IDocumentInfo`, který obsahuje všechna potřebná metadata.

### Krok 4: Získejte konkrétní podrobnosti (Jak získat typ souboru v Javě)

```java
System.out.println("File type: " + info.getFileType());
System.out.println("Number of pages: " + info.getPageCount());
System.out.println("Document size: " + info.getSize() + " bytes");
```

- **Typ souboru** (`info.getFileType()`) vám říká, zda je dokument DOCX, PDF atd.  
- **Počet stránek** (`info.getPageCount()`) je odpovědí na **jak získat stránky**.  
- **Velikost** (`info.getSize()`) vrací velikost souboru v bajtech, užitečná pro výpočty úložiště.

### Krok 5: Uzavřete zdroje

```java
// Always close the Watermarker and FileInputStream
watermarker.close();
stream.close();
```

Uzavření uvolní nativní zdroje a zabrání únikům paměti, což je zvláště důležité při zpracování mnoha souborů.

## Běžné případy použití extrakce informací o dokumentu

1. **Systémy správy dokumentů** – Automaticky kategorizovat soubory podle typu nebo počtu stránek.  
2. **Předzpracovatelská validace** – Odmítnout soubory, které překračují limit počtu stránek před vodoznakováním.  
3. **Audity souladu** – Zaznamenávat metadata pro regulační reportování.  
4. **Dávkové zpracování** – Rychle prohledat složku dokumentů a rozhodnout, které vyžadují další zpracování.  
5. **Integrace s cloudem** – Ověřit limity velikosti před nahráním do úložných služeb.

## Úvahy o výkonu

- **Efektivní streamování:** Použijte `FileInputStream` (jak je ukázáno) místo načítání celého souboru do paměti.  
- **Okamžité uvolnění:** Vždy zavolejte `close()` na `Watermarker` a streamy.  
- **Paralelní zpracování:** Pro velké dávky zvažte použití `ExecutorService` v Javě pro souběžné zpracování více dokumentů.

## Řešení problémů a běžné úskalí

| Problém | Důvod | Řešení |
|-------|--------|-----|
| `FileNotFoundException` | Nesprávná cesta nebo chybějící soubor | Ověřte absolutní/relativní cestu a oprávnění k souboru |
| `UnsupportedFormatException` | Formát dokumentu není podporován | Zkontrolujte seznam podporovaných formátů v dokumentaci GroupDocs |
| Memory spikes on large PDFs | Načítání celého dokumentu do paměti | Držte se přístupu založeného na streamu a objekty okamžitě uzavírejte |

## Často kladené otázky

**Q: Jaké typy souborů jsou podporovány pro extrakci informací o dokumentu?**  
A: GroupDocs.Watermark podporuje DOCX, PDF, PPTX, XLSX a mnoho dalších běžných formátů.

**Q: Jak mohu získat další metadata, například autora nebo datum vytvoření?**  
A: Použijte další vlastnosti objektu `IDocumentInfo`, např. `info.getAuthor()` nebo `info.getCreationDate()`.

**Q: Funguje tato metoda s šifrovanými nebo chráněnými soubory heslem?**  
A: Ano — při inicializaci `Watermarker` poskytněte heslo (viz dokumentace API pro podrobnosti).

**Q: Můžu zpracovávat tisíce souborů, aniž by došlo k nedostatku paměti?**  
A: Rozhodně, pokud po zpracování každého souboru uzavřete každý `Watermarker` a stream.

**Q: Existuje způsob, jak získat počet stránek bez načtení celého dokumentu?**  
A: Volání `getPageCount()` načte pouze potřebné informace z hlavičky, takže je lehké.

## Zdroje

- **Dokumentace**: [GroupDocs Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Reference API**: [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **Stáhnout**: [GroupDocs Watermark Downloads](https://releases.groupdocs.com/watermark/java/)  
- **Repozitář na GitHubu**: [GroupDocs Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Bezplatná podpora**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Dočasná licence**: [Get a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-02-24  
**Testováno s:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs