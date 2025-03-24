---
title: Adjon hozzá vízjelet egy adott oldalhoz a Word Dokumentumokban
linktitle: Adjon hozzá vízjelet egy adott oldalhoz a Word Dokumentumokban
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat vízjeleket a Word-dokumentumok bizonyos oldalaihoz a GroupDocs Watermark for .NET segítségével. Védje meg tartalmait erőfeszítés nélkül.
weight: 14
url: /hu/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## Bevezetés
A dokumentumok vízjelezése a dokumentumbiztonság és a márkaépítés kulcsfontosságú szempontja. Ebben az oktatóanyagban megvizsgáljuk, hogyan adhatunk vízjelet a Word dokumentumok egy adott oldalához a GroupDocs.Watermark for .NET segítségével.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
- C# programozási alapismeretek.
- Telepített Visual Studio IDE.
- GroupDocs.Watermark for .NET telepítve a projektben.

## Névterek importálása
Mielőtt belemerülne a kódba, feltétlenül importálja a szükséges névtereket:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A kódod ide kerül
}
```
## 2. lépés: Adja hozzá a vízjelet
```csharp
// Határozza meg a vízjel szövegét és stílusát
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Vízjel hozzáadása az utolsó oldalhoz
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## 3. lépés: Mentse el a dokumentumot
```csharp
// Mentse el a dokumentumot vízjellel
watermarker.Save(outputFileName);
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk vízjelet Word-dokumentumok egy adott oldalához a GroupDocs.Watermark for .NET segítségével. Az alábbi lépések követésével hatékonyan megvédheti dokumentumait, és szükség szerint hozzáadhat márkaelemeket.
## GYIK
### Testreszabhatom a vízjel szövegét és stílusát?
Igen, testreszabhatja a vízjel szövegét, betűtípusát, méretét, színét és helyzetét igényei szerint.
### A GroupDocs.Watermark for .NET kompatibilis más dokumentumformátumokkal?
Igen, a GroupDocs.Watermark különféle dokumentumformátumokat támogat, beleértve a Word, Excel, PowerPoint, PDF és egyebeket.
### Hozzáadhatok több vízjelet egyetlen dokumentumhoz?
Természetesen több vízjelet is hozzáadhat különböző tartalommal és stílusokkal ugyanahhoz a dokumentumhoz.
### Elérhető ingyenes próbaverzió a GroupDocs.Watermark for .NET számára?
 Igen, egy ingyenes próbaverzióval felfedezheti a GroupDocs.Watermark szolgáltatásait. A kezdéshez egyszerűen keresse fel a megadott linket[itt](https://releases.groupdocs.com/).
### Hol kaphatok technikai támogatást a GroupDocs.Watermark-hoz?
 Hasznos forrásokat találhat, és technikai támogatást kaphat[itt](https://forum.groupdocs.com/c/watermark/19) GroupDocs.Watermark fórum. Látogassa meg a megadott linket a közösséghez való csatlakozáshoz.