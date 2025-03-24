---
title: Přidat vodoznak dlaždicového obrázku
linktitle: Přidat vodoznak dlaždicového obrázku
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak přidat vodoznaky s dlaždicovými obrázky do vašich dokumentů pomocí GroupDocs.Watermark for .NET. Snadné, efektivní a přizpůsobitelné.
weight: 10
url: /cs/net/image-watermarkings/add-tiled-image-watermark/
---
## Úvod
GroupDocs.Watermark for .NET je výkonné rozhraní API, které umožňuje vývojářům programově přidávat, odstraňovat a vyhledávat vodoznaky v různých formátech dokumentů. V tomto tutoriálu vás provedeme procesem přidávání vodoznaku dlaždicového obrázku do vašich dokumentů pomocí GroupDocs.Watermark for .NET.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
- Základní znalost programovacího jazyka C#.
- Visual Studio nainstalované ve vašem systému.
- Do vašeho projektu byla přidána knihovna GroupDocs.Watermark for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/Watermark/net/).

## Importovat jmenné prostory
Ujistěte se, že jste na začátku svého souboru C# importovali potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Nastavte cestu k dokumentu a výstupní adresář
Definujte cestu ke svému vstupnímu dokumentu a adresář, kam chcete výstupní dokument uložit:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` s absolutní nebo relativní cestou k vašemu vstupnímu dokumentu.
## Krok 2: Inicializujte objekt vodoznaku
Vytvořte objekt Watermarker pomocí vstupní cesty dokumentu:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Zde přidejte vodoznak
}
```
## Krok 3: Přidejte vodoznak dlaždicového obrázku
Vytvořte instanci objektu ImageWatermark s cestou k souboru obrázku, který chcete použít jako vodoznak:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Nakonfigurujte možnosti dlaždic
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Přidejte do dokumentu vodoznak
    watermarker.Add(watermark);
    // Uložte upravený dokument
    watermarker.Save(outputFileName);
}
```
 Nahradit`"Path to Your Image"` se skutečnou cestou k souboru obrázku vodoznaku.

## Závěr
Podle těchto kroků můžete snadno přidat vodoznak dlaždicového obrázku do svých dokumentů pomocí GroupDocs.Watermark for .NET. Experimentujte s různými možnostmi a konfiguracemi, abyste dosáhli požadovaného výsledku.
## FAQ
### Mohu přidat více vodoznaků do jednoho dokumentu?
Ano, pomocí GroupDocs.Watermark for .NET můžete do dokumentu přidat více vodoznaků různých typů.
### Podporuje GroupDocs.Watermark všechny formáty dokumentů?
GroupDocs.Watermark podporuje širokou škálu formátů dokumentů, včetně PDF, Word, Excel, PowerPoint a mnoha dalších.
### Je k dispozici zkušební verze pro GroupDocs.Watermark?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Mohu upravit vzhled vodoznaku?
Ano, můžete přizpůsobit různé aspekty vodoznaku, jako je poloha, velikost, otočení, průhlednost atd.
### Nabízí GroupDocs.Watermark technickou podporu?
 Ano, technickou podporu můžete získat na fóru GroupDocs.Watermark[tady](https://forum.groupdocs.com/c/watermark/19).