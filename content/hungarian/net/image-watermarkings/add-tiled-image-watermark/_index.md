---
title: Adjon hozzá csempézett kép vízjelet
linktitle: Adjon hozzá csempézett kép vízjelet
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat mozaikszerű vízjeleket a dokumentumokhoz a GroupDocs.Watermark for .NET segítségével. Egyszerű, hatékony és testreszabható.
type: docs
weight: 10
url: /hu/net/image-watermarkings/add-tiled-image-watermark/
---
## Bevezetés
A GroupDocs.Watermark for .NET egy hatékony API, amely lehetővé teszi a fejlesztők számára, hogy programozottan adjanak hozzá, távolítsanak el és keressenek vízjeleket különféle dokumentumformátumokban. Ebben az oktatóanyagban végigvezetjük Önt azon a folyamaton, hogyan adhat hozzá mozaikképes vízjelet a dokumentumokhoz a GroupDocs.Watermark for .NET segítségével.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
- C# programozási nyelv alapismerete.
- A Visual Studio telepítve van a rendszerére.
- GroupDocs.Watermark for .NET könyvtár hozzáadva a projekthez. Letöltheti innen[itt](https://releases.groupdocs.com/Watermark/net/).

## Névterek importálása
Ügyeljen arra, hogy importálja a szükséges névtereket a C# fájl elejére:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1. lépés: Állítsa be a dokumentum elérési útját és a kimeneti könyvtárat
Határozza meg a bemeneti dokumentum elérési útját és azt a könyvtárat, ahová a kimeneti dokumentumot menteni szeretné:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` a bemeneti dokumentum abszolút vagy relatív elérési útjával.
## 2. lépés: Inicializálja a vízjelobjektumot
Hozzon létre egy Watermarker objektumot a bemeneti dokumentum elérési útjával:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Adjon hozzá vízjelet ide
}
```
## 3. lépés: Adjon hozzá csempézett kép vízjelet
Példányosítson egy ImageWatermark objektumot a vízjelként használni kívánt képfájl elérési útjával:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Konfigurálja a csempe opciókat
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
    // Adjon vízjelet a dokumentumhoz
    watermarker.Add(watermark);
    // Mentse el a módosított dokumentumot
    watermarker.Save(outputFileName);
}
```
 Cserélje ki`"Path to Your Image"` a vízjel képfájl tényleges elérési útjával.

## Következtetés
Az alábbi lépések követésével könnyedén hozzáadhat mozaikszerű vízjelet a dokumentumokhoz a GroupDocs.Watermark for .NET segítségével. Kísérletezzen különböző opciókkal és konfigurációkkal a kívánt eredmény elérése érdekében.
## GYIK
### Hozzáadhatok több vízjelet egyetlen dokumentumhoz?
Igen, a GroupDocs.Watermark for .NET segítségével több különböző típusú vízjelet is hozzáadhat egy dokumentumhoz.
### A GroupDocs.Watermark minden dokumentumformátumot támogat?
A GroupDocs.Watermark a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Word, Excel, PowerPoint és még sok mást.
### Elérhető a GroupDocs.Watermark próbaverziója?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Testreszabhatom a vízjel megjelenését?
Igen, testreszabhatja a vízjel különböző szempontjait, például helyzetét, méretét, elforgatását, átlátszóságát stb.
### A GroupDocs.Watermark kínál technikai támogatást?
 Igen, technikai támogatást kaphat a GroupDocs.Watermark fórumon[itt](https://forum.groupdocs.com/c/watermark/19).