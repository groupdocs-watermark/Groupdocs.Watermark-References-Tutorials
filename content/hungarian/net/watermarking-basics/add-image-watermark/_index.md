---
title: Kép hozzáadása vízjelhez
linktitle: Kép hozzáadása vízjelhez
second_title: GroupDocs.Watermark .NET API
description: A GroupDocs.Watermark for .NET segítségével könnyedén adjon hozzá képes vízjeleket dokumentumaihoz. Védje meg szellemi tulajdonát könnyedén.
weight: 10
url: /hu/net/watermarking-basics/add-image-watermark/
---

# Kép hozzáadása vízjelhez

## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Watermark for .NET segítségével képes vízjel hozzáadásának folyamatába fogunk belemenni. A vízjelekkel ellátott dokumentumok nélkülözhetetlenek a szellemi tulajdon és a márkanév védelme szempontjából. A GroupDocs.Watermark for .NET segítségével zökkenőmentesen integrálhatja a vízjeleket különböző dokumentumformátumokba, például Word, Excel, PowerPoint, PDF és sok más formátumba.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételeket teljesítette:
1.  GroupDocs.Watermark for .NET Library: Töltse le és telepítse a GroupDocs.Watermark for .NET könyvtárat a[weboldal](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentum: Készítse elő azt a dokumentumot, amelyhez vízjelet szeretne adni.
3. Kép vízjelhez: Készítse elő a vízjelként használni kívánt képfájlt.

## Névterek importálása
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## 1. lépés: Inicializálja a dokumentum elérési útját és kimeneti könyvtárát
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` dokumentum abszolút vagy relatív elérési útjával és`"Your Document Directory"` azzal a könyvtárral, ahová menteni szeretné a vízjellel ellátott dokumentumot.
## 2. lépés: Nyissa meg a Dokumentumfolyamot és inicializálja a vízjelet
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // A vízjelezési folyamat itt fog menni
    }
}
```
 Nyissa meg a dokumentumfolyamot a segítségével`FileStream` és inicializálja a`Watermarker` tárgy.
## 3. lépés: Kép vízjel hozzáadása
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Hozzon létre egy`ImageWatermark` objektumot a vízjelként használni kívánt képfájl elérési útjával. Állítsa be a vízjel vízszintes és függőleges igazítását.
## 4. lépés: Mentse el a vízjeles dokumentumot
```csharp
watermarker.Save(outputFileName);
```
Mentse a vízjellel ellátott dokumentumot a megadott kimeneti könyvtárba a kívánt fájlnévvel.

## Következtetés
Összefoglalva, a GroupDocs.Watermark for .NET átfogó megoldást kínál a különféle dokumentumformátumokhoz történő vízjelek könnyű hozzáadására. Az oktatóanyagban ismertetett lépések követésével hatékonyan adhat hozzá vízjeleket a dokumentumokhoz, és megvédheti szellemi tulajdonát.
## GYIK
### Hozzáadhatok szöveges vízjeleket a GroupDocs.Watermark for .NET segítségével?
Igen, a GroupDocs.Watermark for .NET támogatja kép- és szöveges vízjelek hozzáadását a dokumentumokhoz.
### GroupDocs.Watermark for .NET kompatibilis a különböző dokumentumformátumokkal?
Természetesen a GroupDocs.Watermark for .NET a dokumentumformátumok széles skáláját támogatja, beleértve a Word, Excel, PowerPoint, PDF és egyebeket.
### A GroupDocs.Watermark for .NET biztosít testreszabási lehetőségeket a vízjelekhez?
Igen, testreszabhatja a vízjel különböző szempontjait, például a helyzetet, a méretet, az átlátszatlanságot és az elforgatást.
### Eltávolíthatom a vízjeleket a dokumentumokból a GroupDocs.Watermark for .NET segítségével?
Igen, a GroupDocs.Watermark for .NET funkciót kínál vízjelek észlelésére és eltávolítására a dokumentumokból.
### Elérhető a GroupDocs.Watermark for .NET próbaverziója?
 Igen, igénybe veheti a webhely ingyenes próbaverzióját, hogy vásárlás előtt felfedezze a funkciókat[itt](https://releases.groupdocs.com/).