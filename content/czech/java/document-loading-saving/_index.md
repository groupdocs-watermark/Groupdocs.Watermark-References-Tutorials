---
date: 2026-09-16
description: Naučte se, jak přidat vodoznak do PDF, načíst dokumenty z různých zdrojů
  a uložit soubory s vodoznakem pomocí GroupDocs.Watermark pro Java.
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: Rychle přidejte vodoznak do PDF pomocí GroupDocs.Watermark pro Java.
  Naučte se načítat dokumenty, pracovat s hesly a ukládat soubory s vodoznakem.
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: Přidání vodoznaku do PDF pomocí GroupDocs.Watermark pro Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: Jak přidat vodoznak do PDF pomocí GroupDocs.Watermark pro Java
type: docs
url: /cs/java/document-loading-saving/
weight: 2
---

# Přidat vodoznak do PDF pomocí GroupDocs.Watermark pro Java

V tomto průvodci se naučíte, jak **přidat vodoznak do PDF** souborů pomocí GroupDocs.Watermark Java SDK. Provedeme vás načítáním dokumentů z disku, streamů nebo zdrojů chráněných heslem, aplikací textových nebo obrázkových vodoznaků a nakonec uložením aktualizovaného PDF. Ať už budujete dávkový procesor nebo službu pro jeden soubor, tyto kroky vám poskytnou spolehlivé, produkčně připravené řešení.

## Rychlé odpovědi
- **Mohu přidat vodoznak do PDF chráněného heslem?** Ano – při načítání dokumentu předáte heslo a poté vodoznak aplikujete běžně.  
- **Jaké formáty lze opatřit vodoznakem?** Více než 30 formátů, včetně PDF, DOCX, PPTX a obrázků.  
- **Potřebuji licenci pro vývoj?** Dočasná licence funguje pro testování; pro produkci je vyžadována plná licence.  
- **Jaká verze Javy je požadována?** Java 8 nebo vyšší je podporována.  
- **Je podporováno streamování?** Rozhodně – můžete načíst z `InputStream` a uložit do `OutputStream` bez zásahu do souborového systému.

## Co je přidání vodoznaku do PDF?
*Přidání vodoznaku do PDF* označuje proces překrytí poloprůhledného textu nebo obrázků na každou stránku PDF dokumentu za účelem vyjádření vlastnictví, důvěrnosti nebo značky. GroupDocs.Watermark pro Java poskytuje jednorázové API, které automaticky zvládá umístění, neprůhlednost a výběr rozsahu stránek.

## Proč používat GroupDocs.Watermark pro Java?
GroupDocs.Watermark podporuje **35+ formátů souborů** a dokáže zpracovat **PDF s 500 stránkami za méně než 2 sekundy** na typickém serverovém procesoru. Knihovna pracuje kompletně v paměti, takže nikdy nebudete potřebovat nainstalovaný Microsoft Office nebo Adobe Acrobat. Její API je thread‑safe, což ji činí ideální pro vysoce výkonné webové služby.

## Požadavky
- Java 8 nebo novější nainstalována.  
- Projekt Maven nebo Gradle nakonfigurovaný s závislostí `groupdocs-watermark`.  
- Platná licence GroupDocs.Watermark (dočasná licence pro hodnocení).  
- PDF soubory, které chcete chránit, případně s hesly.

## Jak přidat vodoznak do PDF – krok za krokem

Načtěte zdrojový dokument, aplikujte vodoznak a poté výsledek uložte. Následující sekce odpovídají přímo na každou podúlohu.

### Jak načíst dokument z disku?

`Watermarker` je hlavní třída používaná k načítání a manipulaci s dokumenty pro vodoznakování. Poskytněte úplnou cestu k souboru konstruktoru `Watermarker`; SDK automaticky detekuje formát souboru, ověří obsah a načte dokument do paměti připravený na jakoukoli operaci vodoznakování. Tento přístup funguje pro PDF, Word soubory, obrázky a mnoho dalších podporovaných typů.  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

Po tomto řádku je PDF plně načteno v paměti, připravené na jakoukoli operaci vodoznakování.

### Jak načíst dokument ze streamu?

`Watermarker` může také přijímat `InputStream` pro načtení dokumentů přímo z paměti. Když obdržíte soubor přes HTTP nebo frontu zpráv, zabalte pole bajtů do `ByteArrayInputStream` a předávejte jej konstruktoru `Watermarker`, který přijímá `InputStream`. SDK čte stream bez zápisu na disk, čímž zachovává výkon a bezpečnost, a podporuje velké soubory zpracováním dat po částech. Tato metoda je ideální pro webové služby a mikroservisní architektury.  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

SDK čte stream bez zápisu na disk, čímž zachovává výkon a bezpečnost.

### Jak načíst dokument chráněný heslem?

`Watermarker` podporuje načítání PDF chráněných heslem zadáním hesla jako druhého argumentu. Poskytněte heslo jako druhý argument konstruktoru. SDK dešifruje PDF za běhu, po čemž s ním můžete zacházet jako s jakýmkoli jiným dokumentem. Pokud je heslo správné, všechny stránky jsou přístupné pro vodoznakování; jinak knihovna vyhodí jasnou výjimku, kterou můžete zachytit a zalogovat pro odstraňování problémů.  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

Pokud je heslo nesprávné, SDK vyhodí informativní výjimku, kterou můžete zachytit a zalogovat.

### Jak aplikovat textový vodoznak?

`TextWatermark` představuje textový vodoznak, který lze aplikovat na stránky s přizpůsobitelným stylem. Vytvořte objekt `TextWatermark` s požadovaným textem, fontem, velikostí a barvou. Pak zavolejte `add` na instanci `Watermarker`, případně specifikujte rozsahy stránek. Vodoznak je vykreslen s určenou neprůhledností a rotací a může být umístěn pomocí předdefinovaných lokací nebo vlastních souřadnic, což zajišťuje konzistentní vzhled na všech stránkách.  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

Toto volání umístí vodoznak na každou stránku ve výchozím nastavení; pokud potřebujete omezení, můžete použít `new PageRange(1, 5)`.

### Jak aplikovat obrázkový vodoznak?

`ImageWatermark` představuje obrázkový vodoznak, například logo nebo pečeť. Vytvořte `ImageWatermark` s cestou nebo streamem vašeho loga a poté jej přidejte podobně jako textový vodoznak. SDK automaticky škáluje obrázek tak, aby pasoval na stránku při zachování poměru stran, a můžete upravit neprůhlednost, rotaci a umístění pro dosažení požadovaného vizuálního efektu bez deformace původního obsahu.  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

SDK škáluje obrázek tak, aby pasoval na stránku při zachování poměru stran.

### Jak uložit dokument s vodoznakem?

`save` zapíše upravený dokument na zadané místo ve zvoleném formátu. Zavolejte `save` s výstupní cestou a požadovaným formátem. Pokud parametr formátu vynecháte, použije se stejný formát jako u zdroje. Metoda zapíše upravené PDF na disk, zachová veškerý původní obsah kromě nově přidaných vrstev vodoznaku, a podporuje ukládání do streamů pro další zpracování.  
```java
watermarker.save("C:/files/output.pdf");
```

Metoda zapíše upravené PDF na disk, zachová veškerý původní obsah kromě nově přidaných vrstev vodoznaku.

## Dostupné tutoriály

### [Jak načíst dokumenty chráněné heslem v Javě pomocí GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-documents/)
Naučte se, jak načíst a spravovat vodoznaky v dokumentech chráněných heslem pomocí GroupDocs.Watermark pro Java. Tento průvodce poskytuje krok‑za‑krokem instrukce, praktické příklady a tipy pro řešení problémů.

### [Jak načíst a opatřit vodoznakem Word dokumenty chráněné heslem v Javě pomocí GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-word-docs/)
Naučte se efektivně používat GroupDocs.Watermark s Javou k načtení, správě a vodoznakování Word dokumentů chráněných heslem.

## Další zdroje

- [Dokumentace GroupDocs.Watermark pro Java](https://docs.groupdocs.com/watermark/java/)
- [Reference API GroupDocs.Watermark pro Java](https://reference.groupdocs.com/watermark/java/)
- [Stáhnout GroupDocs.Watermark pro Java](https://releases.groupdocs.com/watermark/java/)
- [Fórum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Bezplatná podpora](https://forum.groupdocs.com/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)

## Časté problémy a řešení
- **Chyba neplatného hesla** – zkontrolujte řetězec hesla; musí být kódován v UTF‑8.  
- **Nedostatek paměti u velkých PDF** – povolte režim streamování pomocí konstruktorů `Watermarker`, které přijímají `InputStream` a `OutputStream`.  
- **Vodoznak není viditelný** – ujistěte se, že průhlednost vodoznaku je nastavená nad 0,1 a že barva kontrastuje s pozadím stránky.

## Často kladené otázky

**Q: Mohu přidat více vodoznaků do stejného PDF?**  
A: Ano. Opakovaně zavolejte `watermarker.add()` s různými objekty `TextWatermark` nebo `ImageWatermark`; každý bude vrstvený v pořadí, ve kterém byl přidán.

**Q: Zachovává knihovna existující anotace?**  
A: Rozhodně. Všechny původní PDF objekty, včetně anotací, formulářových polí a metadat, zůstávají nedotčeny, pokud je výslovně nezměníte.

**Q: Je možné vodoznakovat pouze vybrané stránky?**  
A: Ano. Předávejte `PageRange` (např. `new PageRange(2, 4)`) metodě `add`, aby se vodoznak omezil na konkrétní stránky.

**Q: Jaká je maximální podporovaná velikost souboru?**  
A: SDK zvládne soubory až do **2 GB** bez načítání celého dokumentu do paměti díky své streamovací architektuře.

**Q: Jak mohu odstranit vodoznak po jeho přidání?**  
A: Použijte `watermarker.remove(watermarkId)`, kde `watermarkId` je identifikátor vrácený při původním přidání vodoznaku.

**Last Updated:** 2026-09-16  
**Tested with:** GroupDocs.Watermark 23.9 for Java  
**Author:** GroupDocs

## Související tutoriály

- [Jak přidat textový vodoznak do PDF pomocí GroupDocs.Watermark pro Java (průvodce 2023)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [Jak přidat textové a obrázkové vodoznaky na konkrétní stránky PDF pomocí GroupDocs.Watermark pro Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Jak načíst dokumenty chráněné heslem v Javě pomocí GroupDocs.Watermark](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)