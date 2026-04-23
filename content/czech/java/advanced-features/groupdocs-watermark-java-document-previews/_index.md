---
date: '2026-02-03'
description: Naučte se, jak zobrazovat náhledy dokumentů pomocí GroupDocs.Watermark
  pro Javu – rychlý průvodce pro vývojáře Java zaměřené na náhledy dokumentů.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: Jak zobrazit náhled dokumentů pomocí GroupDocs.Watermark pro Javu
type: docs
url: /cs/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Jak zobrazit náhledy dokumentů pomocí GroupDocs.Watermark v Javě

Vy dokumentů** je nezbytnaci S GroupDocs.Watermark pro Java můžete generovat rychlé, vysoce‑kvalitní náhledy, aniž byste načítali celý dokument do paměti. V tomto průvodci se krok za krokem dozvíte, jak nastavit knihovnu, spravovat proudy náhledů pro každovna je doporuč.11)  
- **Na jaké prim slovo je tento tutoriál zaměřen?** *how to preview documents*  
- **Potřebuji licenci?** Zkušební verze stačí pro hodnoceníohu přizpůsobit výstupní formát?** Ano – můžete změnit příponu souboru v šabloně page‑stream.  
- **Je kód thread‑safe?** Instance Watermarker není thread‑safe; vytvořte samostatnou instanci pro každý vlákno.

## Co je náhled dokumentu v Javě?
Náhled dokumentu je lehký obrázek (často PNG nebo JPEG), který představuje jednu stránku souboru. Umožňuje uživatelům rychle nahlédnout do obsahu, čímž zlepšuje UX v prohlížečích souborů, CMS platformách a cloudových úložištích.

## Proč použít GroupDocs.Watermark pro generování náhledů?
- **Zaměřeno na výkon**: Generuje obrázky stránek bez nutnosti renderovat celý dokument.  
- **Podpora napříč formáty**: Funguje s PDF, Office soubory, Visio a mnoha dalšími.  
- **Vestavěná správa proudů**: Poskytuje rozhraní `ICreatePageStream` a `IReleasePage Předpoklady

Než začnete, ujistěte se, že máte:

.ní verzi.** a IDE jako IntelliJ IDEA nebo Eclipse.  
3. Základní znalosti Javy (sou Nastavení GroupDocs.Watermark pro Java

P:

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

Nebo si stáhněte JAR přímo z oficiální stránky:  
[GroupDocs.Water](https://releases.groupdocs.com/watermarká funkčnost, vhodná pro testování.  
- **Temporary License** – plná sada funkcí na krátkou evaluační dobu.  
- **Full License** – neomezené použití a priorita v podpoře.

## Průvodce implementací

### Inicializace Watermarker

Prvním krokem je vytvořit instanci `Watermarker`, která ukazuje na zdrojový dokument.

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

> **Tip:** Nahraďte `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` skutečnou cestou k souboru, který chcete náhlednout.

### Vytvoření page streamu pro generování náhledů

Implementujte `ICreatePageStream`, aby knihovna věděla, kde a jak uložit každý obrázek stránky.

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

*`page%s.png`* je **page stream java** vzor, který automaticky pojmenuje každý soubor náhledu (např. `page1.png`, `page2.png`).

### Uvolnění page streamu

Správné uzavření proudů zabraňuje únikům paměti.

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

### Generování náhledu dokumentu

Nyní spojte vše a zavolejte `generatePreview` s **preview options java**.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

- `createPageStream` zajišťuje **page stream java** tvorbu pro každý obrázek náhledu.  
- `releasePageStream` uvolňuje prostředky po zápisu každé stránky.  

## Praktické aplikace

- **PDF Viewer Apps** – zobrazují miniatury před otevřením celého souboru.  
- **Content Management Systems** – umožňují editorům rychle procházet obsah dokumentů.  
- **Cloud Storage běhu pro jak.

## Úvahy o výkonu

- **Využití paměti** – Používejte rozhraní streamů, abyste se vyhnuli načítání celých dokumentů do RAM.  
- **Optimalizace I/O** – Zabalte `FileOutputStream` do `BufferedOutputStream`, pokud zpracováváte mnoho stránek.  
štějte generování náneastšení |
tené najednou | Použijte rozhraní streamů (jak je ukázáno) pro zpracování po stránkách. |
| **FileNotFoundException** | Nesprávná cesta výstupního adresáře | OYOUR_OUTPUT_DIRECTORY` existuje a je zapisovatelný. |
| **Preview images are blank** | Nepodporovaný formát souboru | Ujistěte se, že typ dokumentu je podporován GroupDocs.Watermark (např. PDF, DOCX, VDX). |

## Často kladenhledy pro dokumenty chráněné heslem?**  
A: Ano. Předávejte heslo dotoru `Watermarker JakéA: PNG je výchozí, ale můžete změnit příponu souboru vStream` na JPEG, BMP atd.

**Qled na konkrétní stránky?**  
A: Použijte `PreviewOptions.setPageNumber(int pageNumber)` pro generování náhledu jedné stránky.

**Q: Funguje knihovna na Linuxu/macOS?**  
A: Rozhodně. GroupDocs.Watermark je platformně nezávislý, pokud je k dispozici Java runtime.

**Q: Jak vyčistit dočasné soubory po dávkovém zpracování?**  
A: Smažte vygenerované součně nebo implementujte naplánlední aktualizace:**.Watermark Java 24.11  
**Autor:** GroupDocs