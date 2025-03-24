---
title: Adjon hozzá vízjelet az alakbeállításokkal a Word Dokumentumokban
linktitle: Adjon hozzá vízjelet az alakbeállításokkal a Word Dokumentumokban
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat hozzá vízjeleket alakbeállításokkal Word-dokumentumokhoz a GroupDocs Watermark for .NET segítségével. Védje hatékonyan dokumentumait.
weight: 20
url: /hu/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---

# Adjon hozzá vízjelet az alakbeállításokkal a Word Dokumentumokban

## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Watermark for .NET használatával vízjel alakbeállításokkal történő hozzáadásának folyamatát mutatjuk be Word-dokumentumokhoz.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1.  GroupDocs.Watermark for .NET telepítve. Letöltheti innen[itt](https://releases.groupdocs.com/Watermark/net/).
2. C# programozási alapismeretek.
3. A Word dokumentumfeldolgozás megértése.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a szükséges osztályok és metódusok eléréséhez.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
Töltse be a Word-dokumentumot, ahová a vízjelet fel szeretné venni.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A vízjel hozzáadási kódja ide kerül
}
```
## 2. lépés: Vízjel hozzáadása
 Példányosítás a`TextWatermark` objektumot, és adja meg a vízjelként használni kívánt szöveget.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## 3. lépés: A vízjel beállításainak testreszabása
Állítson be különféle beállításokat a vízjelhez, például igazítást, elforgatási szöget, színt és átlátszóságot.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## 4. lépés: Adja meg a Vízjel szakasz beállításait
Adja meg a vízjel szakasz beállításait, például az alakzat nevét és az alternatív szöveget.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## 5. lépés: Vízjel hozzáadása a dokumentumhoz
Adja hozzá a vízjelet a dokumentumhoz a megadott beállításokkal.
```csharp
watermarker.Add(watermark, options);
```
## 6. lépés: Mentse el a dokumentumot
Mentse el a dokumentumot a hozzáadott vízjellel.
```csharp
watermarker.Save(outputFileName);
```

## Következtetés
Az alakbeállításokkal rendelkező vízjelek hozzáadása a Word-dokumentumokhoz a GroupDocs segítségével egyszerű folyamat. Az oktatóanyagban ismertetett lépések követésével hatékonyan védheti dokumentumait testreszabott vízjelekkel.
## GYIK
### Hozzáadhatok több vízjelet ugyanahhoz a dokumentumhoz?
Igen, ugyanahhoz a dokumentumhoz több vízjelet is hozzáadhat különböző beállításokkal.
### A GroupDocs.Watermark a Word mellett más dokumentumformátumokat is támogat?
Igen, a GroupDocs.Watermark különféle dokumentumformátumokat támogat, beleértve az Excel, PowerPoint, PDF és egyebeket.
### Tovább szabhatom a vízjel megjelenését?
Mindenképpen beállíthat különféle paramétereket, például a betűméretet, stílust, színt és pozíciót az igényeinek megfelelően.
### Elérhető a GroupDocs.Watermark for .NET próbaverziója?
 Igen, ingyenes próbaverziót kaphat a webhelyen[itt](https://releases.groupdocs.com/).
### Hol találok támogatást a GroupDocs.Watermark számára?
 Támogatást találhat és kérdéseket tehet fel a GroupDocs fórumon[itt](https://forum.groupdocs.com/c/watermark/19).