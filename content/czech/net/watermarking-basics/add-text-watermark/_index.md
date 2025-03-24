---
title: Přidat textový vodoznak
linktitle: Přidat textový vodoznak
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat textové vodoznaky do dokumentů pomocí Groupdocs Watermark for .NET pomocí tohoto podrobného průvodce.
weight: 11
url: /cs/net/watermarking-basics/add-text-watermark/
---
## Úvod
GroupDocs.Watermark for .NET je výkonná knihovna, která umožňuje vývojářům přidávat, vyhledávat a odstraňovat vodoznaky z různých formátů dokumentů v aplikacích .NET. V tomto tutoriálu se zaměříme na přidání textového vodoznaku do dokumentu pomocí GroupDocs.Watermark.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. Základní znalost programovacího jazyka C#.
2. Visual Studio nainstalované ve vašem systému.
3.  Nainstalovaná knihovna GroupDocs.Watermark for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).

## Importovat jmenné prostory
Nejprve musíte do projektu C# importovat potřebné jmenné prostory.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Definujte cestu k dokumentu a výstupní adresář
Definujte cestu k vašemu vstupnímu dokumentu a výstupní adresář, kam bude vodoznak uložen.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` s absolutní nebo relativní cestou k vašemu vstupnímu dokumentu, například:`@"C:\Docs\document.pdf"`. Určete také adresář, kam chcete uložit dokument s vodoznakem.
## Krok 2: Přidejte textový vodoznak
 Vytvořte instanci`Watermarker` třídy s cestou vstupního dokumentu. Poté vytvořte a`TextWatermark` objekt s požadovaným nastavením textu a písma.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Závěr
tomto tutoriálu jsme se naučili, jak přidat textový vodoznak do dokumentu pomocí GroupDocs.Watermark for .NET. Díky intuitivnímu rozhraní API mohou vývojáři snadno manipulovat s vodoznaky v různých formátech dokumentů.
## FAQ
### Je GroupDocs.Watermark for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Watermark podporuje širokou škálu formátů dokumentů včetně PDF, Microsoft Word, Excel, PowerPoint a mnoha dalších.
### Mohu upravit vzhled textového vodoznaku?
Ano, můžete přizpůsobit různé vlastnosti, jako je písmo, barva, zarovnání a neprůhlednost vodoznaku textu.
### Poskytuje GroupDocs.Watermark podporu pro odstraňování vodoznaků z dokumentů?
Ano, GroupDocs.Watermark nabízí funkce pro vyhledávání a odstraňování vodoznaků z dokumentů.
### Mohu GroupDocs.Watermark for .NET vyzkoušet před nákupem?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Watermark?
 Technickou podporu získáte na adrese[Fórum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).