---
title: Adjon hozzá vízjelet az alakzatképekhez a Word Dokumentumokban
linktitle: Adjon hozzá vízjelet az alakzatképekhez a Word Dokumentumokban
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat hozzá vízjeleket Word-dokumentumok képeinek formázásához a GroupDocs.Watermark for .NET segítségével. Növelje a dokumentumok biztonságát ezzel az oktatóanyaggal.
weight: 17
url: /hu/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet vízjelet hozzáadni a Word-dokumentumok képeinek formázásához a GroupDocs.Watermark for .NET segítségével. A vízjelezés kulcsfontosságú szempont a dokumentumvédelemben, különösen érzékeny vagy bizalmas információk kezelésekor. Vízjelek hozzáadásával a képek formázásához biztosíthatja dokumentumai integritását és biztonságát.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1.  GroupDocs.Watermark for .NET: Töltse le és telepítse a GroupDocs.Watermark könyvtárat a[letöltési oldal](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentum: Készítse elő a Word-dokumentumot, amelyhez a vízjelet hozzá kívánja adni.
3. Fejlesztői környezet: Állítsa be a kívánt .NET fejlesztői környezetet.
## Névterek importálása
A kód megírása előtt feltétlenül importálja a szükséges névtereket:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
Először határozza meg a dokumentum elérési útját, és adja meg a kimeneti fájl nevét:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 2. lépés: Inicializálja a Watermarkert
 Példányosítás a`Watermarker` objektumot a dokumentum elérési útjának és az opcionális betöltési beállítások megadásával:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Adja hozzá a vízjelezési logikát
}
```
## 3. lépés: Szöveges vízjel létrehozása
Határozza meg a szöveges vízjelet a kívánt tulajdonságokkal, például szöveggel, betűtípussal, igazítással, elforgatással, méretezéssel stb.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4. lépés: Vigyen fel vízjelet a képek alakzatára
Ismételje meg a dokumentumrészeket és alakzatokat az alakzatképek azonosításához, és adja hozzá a vízjelet:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## 5. lépés: Mentse el a dokumentumot
Mentse el a hozzáadott vízjellel ellátott dokumentumot a megadott kimeneti fájlba:
```csharp
watermarker.Save(outputFileName);
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk vízjeleket Word-dokumentumok képeinek formázásához a GroupDocs.Watermark for .NET segítségével. A lépésenkénti útmutató követésével és a GroupDocs.Watermark hatékony funkcióinak kiaknázásával hatékonyan fokozhatja dokumentumai biztonságát és védelmét.
## GYIK
### Testreszabhatom a vízjel szövegének megjelenését?
Igen, beállíthat különféle tulajdonságokat, például a betűtípust, a méretet, a színt, az elforgatási szöget és az igazítást, hogy testreszabhassa a vízjelet saját igényei szerint.
### A GroupDocs.Watermark a Word mellett más dokumentumformátumokat is támogat?
Igen, a GroupDocs.Watermark a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Excel, PowerPoint és egyebeket.
### Lehetséges több vízjelet hozzáadni egyetlen dokumentumhoz?
Természetesen több vízjelet is hozzáadhat különböző tartalommal, stílusokkal és pozíciókkal ugyanabban a dokumentumban.
### Eltávolíthatom a vízjeleket a dokumentumokból a GroupDocs.Watermark segítségével?
Igen, a GroupDocs.Watermark funkciókat kínál a vízjelek hatékony észlelésére és eltávolítására a dokumentumokból.
### A GroupDocs.Watermark platformok közötti kompatibilitást biztosít?
Igen, a GroupDocs.Watermark kompatibilis a .NET Framework, a .NET Core és a .NET Standard technológiával, biztosítva a zökkenőmentes integrációt a különböző platformokon.