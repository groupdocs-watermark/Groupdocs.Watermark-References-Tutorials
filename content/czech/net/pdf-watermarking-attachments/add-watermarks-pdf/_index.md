---
title: Přidejte vodoznaky do PDF
linktitle: Přidejte vodoznaky do PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat textové a obrazové vodoznaky do souborů PDF pomocí GroupDocs.Watermark for .NET s naším komplexním průvodcem krok za krokem.
weight: 14
url: /cs/net/pdf-watermarking-attachments/add-watermarks-pdf/
---

# Přidejte vodoznaky do PDF

## Úvod
Chcete do svých souborů PDF přidat vodoznaky, abyste chránili své dokumenty nebo je označili svým logem? Už nehledejte! V tomto tutoriálu se ponoříme do procesu použití GroupDocs.Watermark for .NET k přidání textových i obrazových vodoznaků do souborů PDF. Ať už jste zkušený vývojář nebo teprve začínáte, tento průvodce vás provede každým krokem a zajistí, že můžete vodoznaky aplikovat snadno a přesně.
## Předpoklady
Než začneme, ujistěte se, že spolu s tímto návodem máte vše, co potřebujete:
-  GroupDocs.Watermark for .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi. Můžeš[stáhněte si to zde](https://releases.groupdocs.com/Watermark/net/).
- Vývojové prostředí .NET: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
- Základní znalost C#: Pochopení základů programování v C# vám pomůže snadno postupovat podle kroků.
- Dokument PDF: Připravte si vzorový dokument PDF pro vodoznak.
- Obrázek pro vodoznak: Pokud přidáváte vodoznak obrázku, připravte si soubor obrázku.
## Importovat jmenné prostory
Nejprve musíte importovat potřebné jmenné prostory do vašeho projektu C#. To vám umožní přístup k funkci GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Nyní si tento proces rozdělíme na zvládnutelné kroky.
## Krok 1: Načtěte dokument PDF
Prvním krokem je načtení dokumentu PDF do vodoznaku. Můžete to udělat takto:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zde budou přidány další kroky
}
```
## Krok 2: Přidejte textový vodoznak na první stránku
Dále přidáme textový vodoznak na první stránku vašeho PDF. Postupujte podle těchto pokynů:
```csharp
// Přidejte textový vodoznak na první stránku
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Přidání textového vodoznaku může pomoci chránit váš dokument před neoprávněným použitím nebo jej jednoduše označit. Představte si, že svůj dokument orazítkujete neviditelnou pečetí pravosti.
## Krok 3: Přidejte na druhou stránku vodoznak obrázku
Nyní přidáme vodoznak obrázku na druhou stránku. To je užitečné zejména pro loga nebo jakékoli grafické vodoznaky.
```csharp
// Přidejte vodoznak obrázku na druhou stránku
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Obrázkové vodoznaky dodají vašim dokumentům profesionální vzhled a zajistí, že vaše značka bude vždy viditelná. Je to jako přidat svůj podpis na každou stránku.
## Krok 4: Uložte PDF s vodoznakem
Po přidání vodoznaků je posledním krokem uložení PDF s vodoznakem na požadované místo.
```csharp
watermarker.Save(outputFileName);
```
Uložením dokumentu se dokončí všechny provedené změny. Toto je okamžik, kdy se vaše úsilí zpevní do hmatatelného výsledku, připraveného k použití nebo distribuci.
## Závěr
Gratulujeme! Úspěšně jste do souboru PDF přidali textové i obrázkové vodoznaky pomocí GroupDocs.Watermark for .NET. Tento proces je nejen přímočarý, ale také vysoce přizpůsobitelný, aby vyhovoval vašim specifickým potřebám. Ať už chráníte své dokumenty nebo je označujete, vodoznaky jsou mocným nástrojem, který máte k dispozici.
## FAQ
### Mohu přidat více vodoznaků na stejnou stránku?
 Ano, na stejnou stránku můžete přidat více vodoznaků zavoláním na`Add` metoda několikrát s různými objekty vodoznaku.
### Jak mohu upravit vzhled textového vodoznaku?
 Textový vodoznak můžete upravit úpravou vlastností, jako je písmo, velikost, barva a neprůhlednost pomocí`TextWatermark` objekt.
### Je možné vložit vodoznak pouze na konkrétní stránky PDF?
 Ano, můžete určit, které stránky mají být vodoznakem nastaveny`PageIndex` nemovitost v`PdfArtifactWatermarkOptions`.
### Mohu odstranit vodoznaky z PDF?
Ano, GroupDocs.Watermark poskytuje funkce pro vyhledávání a odstraňování vodoznaků z dokumentů PDF.
### Jak získám dočasnou licenci pro GroupDocs.Watermark?
Dočasnou licenci můžete získat návštěvou stránky[dočasná licenční stránka](https://purchase.groupdocs.com/temporary-license/).