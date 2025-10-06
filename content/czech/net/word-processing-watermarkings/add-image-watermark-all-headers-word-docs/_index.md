---
title: Přidat vodoznak obrázku do všech záhlaví v dokumentech aplikace Word
linktitle: Přidat vodoznak obrázku do všech záhlaví v dokumentech aplikace Word
second_title: GroupDocs.Watermark .NET API
description: Pomocí GroupDocs.Watermark for .NET můžete snadno přidat vodoznaky obrázku do všech záhlaví v dokumentech aplikace Word. Postupujte podle našeho podrobného průvodce s podrobnými příklady kódu.
weight: 10
url: /cs/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
type: docs
---
# Přidat vodoznak obrázku do všech záhlaví v dokumentech aplikace Word

## Úvod
Vodoznaky mohou být nezbytnou součástí správy dokumentů a poskytují způsob, jak do dokumentů vkládat informace, jako je vlastnictví, důvěrnost nebo branding. V tomto tutoriálu si projdeme kroky pro přidání vodoznaku obrázku do všech záhlaví v dokumentech aplikace Word pomocí GroupDocs.Watermark for .NET. Ať už jste v programování noví nebo zkušení vývojáři, tato příručka vám pomůže snadno dosáhnout vašich cílů v oblasti vodoznaků.
## Předpoklady
Než se ponoříme do kódu, ujistíme se, že máme vše, co potřebujeme. Zde je kontrolní seznam, jak začít:
1.  GroupDocs.Watermark for .NET: Stáhněte si nejnovější verzi z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. .NET Framework: Ujistěte se, že máte nainstalovaný .NET Framework.
4. Ukázkový dokument aplikace Word: Dokument aplikace Word, do kterého chcete přidat vodoznak.
5. Obrázek pro vodoznak: Soubor obrázku, který chcete použít jako vodoznak.
Jakmile je budete mít připravené, můžeme začít s přípravou našeho projektu.
## Importovat jmenné prostory
Nejprve importujme potřebné jmenné prostory. Tyto jmenné prostory obsahují třídy a metody, které nám pomohou pracovat s vodoznaky v našich dokumentech.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Nastavení vašeho projektu
Chcete-li začít, vytvořte novou konzolovou aplikaci v sadě Visual Studio. Přidejte odkazy na GroupDocs.Watermark DLL v projektu. To lze provést instalací balíčku GroupDocs.Watermark NuGet.
```bash
Install-Package GroupDocs.Watermark
```
## Krok 2: Vložte svůj dokument
 Prvním krokem při přidávání vodoznaku je načtení dokumentu, kam bude vodoznak přidán. Zde použijeme`WordProcessingLoadOptions` k načtení dokumentu aplikace Word.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kód pro přidání vodoznaku bude umístěn zde
}
```
## Krok 3: Vytvořte vodoznak obrázku
Dále vytvoříme vodoznak obrázku. To zahrnuje určení souboru obrázku, který chcete použít jako vodoznak.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Kód pro použití vodoznaku bude umístěn zde
}
```
## Krok 4: Přidejte vodoznak do záhlaví prvního oddílu
 Vodoznak musíme přidat do všech záhlaví v první části dokumentu aplikace Word. K tomu používáme`WordProcessingWatermarkSectionOptions` a zadejte index sekce.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Krok 5: Propojte záhlaví a zápatí
Abychom zajistili, že se vodoznak objeví v záhlavích všech oddílů, propojíme všechna ostatní záhlaví a zápatí se záhlavími a zápatími prvního oddílu.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Krok 6: Uložte dokument
Nakonec dokument s vodoznakem uložíme do zadané cesty. Tento krok zajistí, že vaše změny budou zapsány do nového souboru, přičemž se zachová původní dokument.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Závěr
A tady to máte! Úspěšně jste přidali vodoznak obrázku do všech záhlaví v dokumentu aplikace Word pomocí GroupDocs.Watermark for .NET. Tato výkonná knihovna usnadňuje správu a aplikaci vodoznaků na různé typy dokumentů, čímž zajišťuje ochranu vašeho obsahu a profesionální označení.
## FAQ
### Mohu použít jiné typy vodoznaků kromě obrázků?
Ano, GroupDocs podporuje text, obrázek a dokonce i složené vodoznaky.
### Je možné vodoznakem vytvořit i jiné části dokumentu kromě záhlaví?
Absolutně! Vodoznakem můžete vytvořit zápatí, tělo a dokonce i konkrétní stránky nebo sekce.
### Podporuje GroupDocs.Watermark jiné formáty dokumentů?
Ano, podporuje širokou škálu formátů včetně PDF, Excel, PowerPoint a dalších.
### Mohu upravit polohu a vzhled vodoznaku?
Ano, můžete upravit velikost, polohu, neprůhlednost a mnoho dalších vlastností vodoznaku.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Watermark?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).