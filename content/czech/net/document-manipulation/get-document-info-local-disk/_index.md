---
title: Získejte informace o dokumentu z místního disku
linktitle: Získejte informace o dokumentu z místního disku
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat, odebírat a extrahovat vodoznaky v dokumentech pomocí GroupDocs Watermark for .NET s tímto komplexním průvodcem krok za krokem.
weight: 11
url: /cs/net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Získejte informace o dokumentu z místního disku

## Úvod
Vítejte v dokonalém průvodci používáním GroupDocs.Watermark pro .NET! Ať už jste zkušený vývojář nebo teprve začínáte, tento článek vás provede základy vodoznaku dokumentů pomocí tohoto výkonného nástroje. Nakonec budete profesionálem ve vkládání vodoznaků do vašich dokumentů, abyste zajistili, že budou chráněny a označeny podle vašich specifikací.
## Předpoklady
Než se pustíte do podrobného průvodce, musíte splnit několik předpokladů:
1.  .NET Framework: Ujistěte se, že máte v systému nainstalované rozhraní .NET Framework. GroupDocs.Watermark for .NET je kompatibilní s různými verzemi rozhraní .NET Framework, proto zkontrolujte[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) pro podrobnosti o kompatibilitě.
2.  GroupDocs.Watermark for .NET Library: Stáhněte a nainstalujte nejnovější verzi z[stránka ke stažení](https://releases.groupdocs.com/Watermark/net/).
3. Vývojové prostředí: Měli byste mít nastavené vývojové prostředí. Visual Studio je oblíbenou volbou pro vývoj .NET.
4. Základní znalosti C#: Pochopení základů programování v C# vám pomůže postupovat podle příkladů.
## Importovat jmenné prostory
Než budete moci použít GroupDocs.Watermark pro .NET, musíte do projektu importovat potřebné jmenné prostory. Jedná se o přímočarý proces a nezbytný pro přístup k funkcím knihovny.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Pojďme si proces vodoznaku dokumentu rozdělit na jasné, zvládnutelné kroky. Každý krok je navržen tak, aby vám pomohl snadno pochopit a implementovat funkci.
## Krok 1: Vložte svůj dokument
 Prvním krokem je načtení dokumentu, který chcete vodoznakem. To se provádí pomocí`Watermarker` třídy, která vám umožní přístup k dokumentu a manipulaci s ním.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Dokument je nyní načten a připraven k vodoznaku
}
```
 V tomto kroku vyměňte`"Your Document Path"` se skutečnou cestou k vašemu dokumentu. Tím se inicializuje`Watermarker`objekt, který vám umožní přístup k různým funkcím vodoznaku.
## Krok 2: Získejte informace o dokumentu
Před přidáním vodoznaku možná budete chtít získat nějaké informace o dokumentu. To může být užitečné pro přizpůsobení vodoznaku na základě vlastností dokumentu.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 V tomto kroku se`GetDocumentInfo` metoda načte podrobnosti, jako je typ souboru, počet stránek a velikost dokumentu. Tyto informace se vytisknou na konzoli, ale můžete je podle potřeby použít ve své aplikaci.
## Krok 3: Přidejte textový vodoznak
Nyní, když máte dokument načtený a jeho informace po ruce, je čas přidat vodoznak. Začneme jednoduchým textovým vodoznakem.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Zde vytvoříte a`TextWatermark` objekt s požadovaným textem, fontem a stylem. Upravte vlastnosti, jako je barva, krytí a úhel otočení, aby vyhovovaly vašim potřebám. Nakonec je vodoznak přidán do dokumentu a uložen do zadané cesty.
## Krok 4: Přidejte vodoznak obrázku
Textové vodoznaky jsou skvělé, ale co když chcete přidat logo nebo jiný obrázek? Tento krok popisuje, jak přidat vodoznak obrázku.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Nahradit`"Path to Your Image"` s cestou k obrázku vodoznaku. Nastavte vlastnosti, jako je krytí a úhel otočení, abyste přizpůsobili vzhled vodoznaku obrázku. Proces přidávání a ukládání vodoznaku je podobný jako u textového vodoznaku.
## Krok 5: Odstraňte stávající vodoznaky
 Někdy může být nutné odstranit existující vodoznaky z dokumentu. To lze provést pomocí`Remove` metoda poskytovaná společností`Watermarker` třída.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Tady,`Remove` metoda se používá k odstranění textových vodoznaků z dokumentu. V závislosti na vašich potřebách můžete určit různé typy vodoznaků, které chcete odstranit, například obrázek nebo text. Uložte dokument do nové cesty, abyste viděli změny.
## Krok 6: Extrahujte vodoznaky
Pokud potřebujete extrahovat a zkontrolovat vodoznaky z dokumentu, GroupDocs.Watermark for .NET to snadno umožňuje.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Další vlastnosti a logika pro každý vodoznak
    }
}
```
 Tento krok zahrnuje použití`GetWatermarks`metoda pro načtení všech vodoznaků v dokumentu. Poté můžete iterovat seznam vodoznaků a zkontrolovat jejich vlastnosti nebo podle potřeby provést další akce.
## Závěr
 Gratulujeme! Nyní jste se naučili, jak používat GroupDocs.Watermark pro .NET k přidávání, odstraňování a extrahování vodoznaků z vašich dokumentů. S těmito dovednostmi můžete efektivně chránit a označovat své dokumenty. Pamatujte,[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) je vždy k dispozici, pokud potřebujete podrobnější informace nebo pokročilé funkce.
## FAQ
### Mohu použít GroupDocs.Watermark pro .NET s jakoukoli verzí .NET?
 Ano, GroupDocs.Watermark for .NET je kompatibilní s různými verzemi rozhraní .NET Framework. Zkontrolovat[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) pro upřesnění.
### Kde si mohu stáhnout GroupDocs.Watermark pro .NET?
 Nejnovější verzi si můžete stáhnout z[stránka ke stažení](https://releases.groupdocs.com/Watermark/net/).
### Jak získám dočasnou licenci?
 Dočasnou licenci můžete získat od[dočasná licenční stránka](https://purchase.groupdocs.com/temporary-license/).
### Je k dispozici bezplatná zkušební verze?
 Ano, bezplatnou zkušební verzi můžete zahájit návštěvou stránky[zkušební stránka zdarma](https://releases.groupdocs.com/).
### Kde mohu získat podporu, pokud narazím na problémy?
 Podpora je k dispozici na[Fórum o vodoznaku GroupDocs](https://forum.groupdocs.com/c/watermark/19).