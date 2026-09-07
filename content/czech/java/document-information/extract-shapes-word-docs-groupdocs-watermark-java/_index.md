---
date: '2026-02-05'
description: Naučte se, jak extrahovat tvary z dokumentů Word pomocí GroupDocs.Watermark
  pro Javu, včetně toho, jak načíst dokument Word v Javě a manipulovat s daty tvarů.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Jak extrahovat tvary z dokumentů Word pomocí GroupDocs.Watermark Java
type: docs
url: /cs/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Jak extrahovat tvary z dokumentů Word pomocí GroupDocs.Watermark v Javě

V tomto tutoriálu se dozvíte **jak extrahovat tvary** z dokumentů Word pomocí knihovny GroupDocs.Watermark pro Javu. Ať už potřebujete analyzovat diagramy, získat vložené obrázky nebo automatizovat generování reportů, extrahování metadat tvarů vám poskytne kontrolu pro vytváření inteligentnějších pipeline pro zpracování dokumentů. Provedeme vás nastavením knihovny, načtením dokumentu Word a získáním podrobných informací o tvarech – vše v přehledném, krok‑za‑krokem Java kódu.

## Rychlé odpovědi
- **Co znamená „extrahovat tvary“?** Získání metadat (typ, velikost, pozice, text, obrázky) pro každý kreslicí objekt v souboru Word.  
- **Která knihovna to řeší?** GroupDocs.Watermark pro Javu.  
- **Potřebuji licenci?** Zkušební verze funguje pro vývoj; plná licence odstraňuje omezení používání.  
- **Mohu také získat obrázky ze tvarů?** Ano – API poskytuje bajty obrázku pro tvary typu picture.  
- **Jaká verze Javy je vyžadována?** JDK 8 nebo novější.

## Co znamená „Jak extrahovat tvary“ v kontextu dokumentů Word?
Extrahování tvarů znamená programově přistupovat ke každému kreslicímu prvku – obrázkům, WordArt, automatickým tvarům, grafům a dokonce i tvarům vloženým do hlaviček nebo zápatí. Tyto informace lze využít pro validaci, migraci nebo analytiku založenou na obsahu.

## Proč použít GroupDocs.Watermark pro Javu?
GroupDocs.Watermark poskytuje high‑level, paměťově efektivní API, které abstrahuje složitost podkladového formátu Office Open XML. Umožňuje vám:
- Rychle načíst dokumenty (`WordProcessingLoadOptions`).  
- Procházet sekce a tvary bez nutnosti pracovat s nízkoúrovňovým XML.  
- Získat data obrázku, text, zarovnání a rotaci jedním voláním.  
- Bezproblémově integrovat do existujících Java služeb nebo mikro‑servis.

## Předpoklady
- **Java Development Kit (JDK)** 8 nebo vyšší.  
- **IDE**, například IntelliJ IDEA nebo Eclipse.  
- Základní znalost Java I/O.  
- Přístup k licenci nebo zkušební verzi **GroupDocs.Watermark pro Javu**.

## Nastavení GroupDocs.Watermark pro Javu
Integrujte knihovnu pomocí Maven nebo přímého stažení.

### Použití Maven
Přidejte repozitář a závislost do souboru `pom.xml`:

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
Alternativně stáhněte nejnovější JAR z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Získání licence
Bezplatná zkušební verze je dostačující pro testování. Pro produkci požádejte o trvalou licenci, která odemkne všechny funkce.

## Průvodce implementací
Rozdělíme implementaci do dvou jasných kroků: **načtení dokumentu Word** a **extrahování informací o tvarech**.

### Krok 1: Načíst dokument Word (load word document java)
Nejprve nakonfigurujte možnosti načtení a vytvořte instanci `Watermarker`. Tím připravíte dokument k dalšímu zkoumání.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Tip:** Uchovávejte instanci `Watermarker` v co nejmenším rozsahu; její včasné uzavření uvolní nativní zdroje a zabrání únikům paměti.

### Krok 2: Extrahovat informace o tvarech (extract images from shapes)
Nyní získáme podrobnosti o každém tvaru, včetně vložených obrázků. Kód prochází každou sekci a každý tvar a vypisuje užitečná metadata.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**Co tento kód dělá:**  
- Získává **typ** každého tvaru (např. picture, WordArt).  
- Vypisuje hodnoty **velikosti**, **pozice** a **rotace**.  
- Zobrazuje **alternativní text** a **název**, což je užitečné pro kontrolu přístupnosti.  
- Pokud tvar obsahuje obrázek, vypíše **rozměry v pixelech** a **velikost v bajtech** obrázku – ideální pro extrahování obrázků ze tvarů.  

### Časté problémy a jak je vyřešit
| Problém | Příčina | Řešení |
|---|---|---|
| `FileNotFoundException` | Nesprávná cesta k souboru nebo chybějící oprávnění | Ověřte absolutní/relativní cestu a zajistěte, že je soubor čitelný. |
| Null `shape.getImage()` | Tvar není obrázek (např. auto‑shape) | Ošetřete pomocí `if (shape.getImage() != null)`, jak je ukázáno. |
| Vysoké využití paměti u velkých dokumentů | Načítání celého dokumentu najednou | Zpracovávejte sekce po jedné nebo zvětšete heap JVM (`-Xmx`). |
| Chybějící tvary v hlavičce/zápatí | Nekontroluje se `shape.getHeaderFooter()` | Vzorek již zaznamenává, když tvar patří do hlavičky nebo zápatí. |

## Praktické aplikace
1. **Automatizovaná tvorba reportů** – získání grafů a diagramů pro vložení do následných PDF.  
2. **Audit shody** – ověření, že všechny tvary obsahují vhodný alternativní text pro přístupnost.  
3. **Migrace obsahu** – export vložených obrázků ze starých Word souborů do systému pro správu digitálních aktiv.  

## Úvahy o výkonu
- **Uvolnění zdrojů**: Vždy zavolejte `watermarker.close()` v bloku `finally` nebo použijte try‑with‑resources, pokud obalujete API.  
- **Zpracování po částech**: Pro dokumenty větší než 50 MB zvažte zpracování každé sekce zvlášť, aby byl paměťový otisk nízký.  
- **Bezpečnost vláken**: Instance `Watermarker` nejsou thread‑safe; vytvořte novou instanci pro každé vlákno.

## Závěr
Nyní víte **jak extrahovat tvary** z dokumentů Word pomocí GroupDocs.Watermark pro Javu, od načtení souboru po čtení metadat každého tvaru a vložených dat obrázku. Tato schopnost otevírá dveře k pokročilé analytice dokumentů, automatizovaným obsahovým pipeline a validaci přístupnosti.

### Další kroky
- Experimentujte s úpravou vlastností tvarů (např. změna velikosti nebo pozice).  
- Kombinujte tento přístup s **GroupDocs.Parser** pro extrahování okolního textu.  
- Integrovat logiku extrakce do REST služby pro zpracování na požádání.

## Často kladené otázky
**Q: Co je GroupDocs.Watermark pro Javu?**  
A: Jedná se o komplexní knihovnu určenou pro správu vodoznaků a obsahu dokumentů napříč formáty, umožňující úkoly jako extrahování tvarů, získávání obrázků a manipulaci s textem.

**Q: Mohu extrahovat obrázky ze tvarů bez licence?**  
A: Zkušební verze umožňuje extrakci, ale plná licence odstraňuje omezení používání a umožňuje komerční nasazení.

**Q: Funguje to i se soubory `.doc` (binárními)?**  
A: Ano, API podporuje jak formáty `.docx`, tak i starší formát `.doc`.

**Q: Jak zacházet s dokumenty chráněnými heslem?**  
A: Zadejte heslo pomocí `WordProcessingLoadOptions.setPassword("yourPassword")` před vytvořením `Watermarker`.

**Q: Existuje způsob, jak exportovat extrahovaná data tvarů do JSON?**  
A: Můžete mapovat vytištěné hodnoty na POJO a použít libovolnou JSON knihovnu (např. Jackson) k serializaci kolekce.

---

**Poslední aktualizace:** 2026-02-05  
**Testováno s:** GroupDocs.Watermark 24.11 pro Javu  
**Autor:** GroupDocs