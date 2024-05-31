---
title: Přidat vodoznak obrázku ze streamu
linktitle: Přidat vodoznak obrázku ze streamu
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat obrázkové vodoznaky do dokumentů pomocí GroupDocs.Watermark for .NET. Postupujte podle našeho podrobného průvodce pro bezproblémovou integraci vodoznaku.
type: docs
weight: 12
url: /cs/net/image-watermarkings/add-image-watermark-from-stream/
---
## Úvod
V oblasti správy dokumentů a zabezpečení má začlenění vodoznaků do souborů prvořadý význam. Vodoznaky hrají zásadní roli, ať už jde o branding, ochranu autorských práv nebo zachování integrity dokumentu. Naštěstí GroupDocs.Watermark for .NET poskytuje robustní řešení pro přidávání, odstraňování a vyhledávání vodoznaků v různých formátech dokumentů.
## Předpoklady
Než se pustíte do implementace vodoznaků pomocí GroupDocs.Watermark for .NET, ujistěte se, že jsou splněny následující předpoklady:
1.  Instalace GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark for .NET z[odkaz ke stažení](https://releases.groupdocs.com/Watermark/net/).
2. Přístup k dokumentu: Získejte přístup k dokumentu, do kterého chcete přidat nebo odebrat vodoznak.
3. Základní znalost C#: Pro pochopení a implementaci poskytnutých úryvků kódu je nezbytná znalost programovacího jazyka C#.

## Importovat jmenné prostory
Než budete pokračovat s přidáváním vodoznaků obrázku ze streamu, importujte potřebné jmenné prostory:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Krok 1: Definujte cestu k dokumentu a výstupní adresář
Nejprve definujte cestu k dokumentu, kam chcete vodoznak přidat, a zadejte výstupní adresář pro zpracovávaný dokument.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Otevřete stream vodoznaku
 Otevřete soubor obrázku vodoznaku jako proud pomocí`File.OpenRead` metoda.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Logika zpracování vodoznaku bude zde
}
```
## Krok 3: Přidejte do dokumentu vodoznak
 Inicializovat a`Watermarker` objekt s cestou dokumentu a poté vytvořte soubor`ImageWatermark` objekt s proudem vodoznaku získaným v kroku 2. Přidejte vodoznak do dokumentu pomocí`Add` metoda`Watermarker` objekt.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Přidejte do dokumentu vodoznak
        watermarker.Add(watermark);
        // Uložte dokument s vodoznakem
        watermarker.Save(outputFileName);
    }
}
```

## Závěr
GroupDocs.Watermark for .NET poskytuje bezproblémové řešení pro přidávání vodoznaků do dokumentů, zajišťuje identitu značky, ochranu autorských práv a integritu dokumentů. Dodržením nastíněných kroků a využitím poskytnutých úryvků kódu mohou uživatelé bez námahy začlenit vodoznaky do svých dokumentů.
## FAQ
### Je GroupDocs.Watermark kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Watermark podporuje širokou škálu formátů dokumentů včetně dokumentů Word, tabulek Excel, prezentací PowerPoint, PDF a dalších.
### Mohu upravit vzhled a umístění vodoznaků?
Rozhodně, GroupDocs.Watermark nabízí rozsáhlé možnosti pro přizpůsobení vzhledu, polohy, průhlednosti, rotace a dalších vodoznaků tak, aby vyhovovaly konkrétním požadavkům.
### Poskytuje GroupDocs.Watermark rozhraní API pro odstranění stávajících vodoznaků?
Ano, GroupDocs.Watermark umožňuje uživatelům nejen přidávat vodoznaky, ale také snadno odstranit stávající vodoznaky z dokumentů.
### Je pro uživatele GroupDocs.Watermark k dispozici technická podpora?
 Ano, uživatelé mohou využívat technickou podporu a pomoc prostřednictvím vyhrazených[Fórum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### Mohu vyhodnotit GroupDocs.Watermark před nákupem?
Uživatelé se samozřejmě mohou rozhodnout pro bezplatnou zkušební verzi GroupDocs.Watermark, aby prozkoumali její vlastnosti a funkce před rozhodnutím o nákupu.