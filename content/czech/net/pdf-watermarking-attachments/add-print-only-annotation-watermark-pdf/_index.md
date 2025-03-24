---
title: Přidat vodoznak pouze pro tisk do PDF
linktitle: Přidat vodoznak pouze pro tisk do PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky pouze pro tisk do souborů PDF pomocí GroupDocs.Watermark for .NET. Vylepšete zabezpečení dokumentů a branding bez námahy.
weight: 13
url: /cs/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Přidat vodoznak pouze pro tisk do PDF

## Úvod
V tomto tutoriálu se ponoříme do procesu přidávání vodoznaku pouze pro tisk do PDF pomocí GroupDocs.Watermark for .NET. Vodoznakové dokumenty jsou zásadním aspektem zabezpečení dokumentů a brandingu a GroupDocs.Watermark poskytuje vývojářům .NET bezproblémové řešení, jak toho dosáhnout.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
- Základní znalost programovacího jazyka C#.
- Visual Studio nainstalované na vašem počítači.
- Knihovna GroupDocs.Watermark for .NET nainstalovaná ve vašem projektu.

## Importovat jmenné prostory
Nejprve se ujistěte, že jste importovali potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument
 Nejprve musíte načíst dokument PDF, který chcete vodoznakem. Nahradit`"Your Document Path"` s cestou k vašemu souboru PDF a`"Your Document Directory"` s adresářem, kam chcete uložit výstupní soubor.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zde bude přidán kód vodoznaku
}
```
## Krok 2: Přidejte vodoznak
Dále vytvořte objekt textového vodoznaku s požadovaným textem a písmem. Soubor`isPrintOnly` na`true` abyste zajistili, že vodoznak bude viditelný pouze při tisku dokumentu, nikoli v režimu zobrazení.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Krok 3: Nakonfigurujte možnosti vodoznaku
Definujte volby pro vodoznak, jako je index stránky, kam má být vodoznak přidán, a určete jej jako anotaci pouze pro tisk.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Krok 4: Použijte vodoznak
Přidejte vodoznak do dokumentu pomocí zadaných možností a uložte výstupní soubor.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat vodoznak pouze pro tisk do dokumentu PDF pomocí GroupDocs.Watermark for .NET. To umožňuje vývojářům snadno zlepšit zabezpečení dokumentů a branding.
## FAQ
### Je GroupDocs.Watermark kompatibilní s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs podporuje různé formáty dokumentů, jako je Word, Excel, PowerPoint a obrázky.
### Mohu upravit vzhled vodoznaku?
GroupDocs.Watermark samozřejmě poskytuje rozsáhlé možnosti přizpůsobení textu vodoznaku, písma, barvy, velikosti a umístění.
### Nabízí GroupDocs.Watermark možnosti dávkového zpracování?
Vývojáři mohou samozřejmě vodoznakem více dokumentů současně pomocí funkcí dávkového zpracování.
### Je k dispozici zkušební verze pro GroupDocs.Watermark?
Ano, z poskytnutého odkazu máte přístup k bezplatné zkušební verzi GroupDocs.Watermark.
### Jak mohu získat technickou podporu pro GroupDocs.Watermark?
Technickou pomoc můžete vyhledat na fóru GroupDocs.Watermark, které je k dispozici na uvedeném odkazu podpory.