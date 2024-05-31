---
title: Alakzatszöveg cseréje formázott szövegre a Word Dokumentumokban
linktitle: Alakzatszöveg cseréje formázott szövegre a Word Dokumentumokban
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan cserélheti le az alakzat szövegét formázott szöveggel a Word dokumentumokban a GroupDocs.Watermark for .NET segítségével. Az Ön dokumentumszerkesztési lehetőségei könnyedén.
type: docs
weight: 34
url: /hu/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük az alakzat szövegének formázott szöveggel való helyettesítésén a Word dokumentumokban a GroupDocs.Watermark for .NET segítségével. Ez a könyvtár hatékony funkciókat kínál a vízjelekkel való munkavégzéshez, beleértve a szöveg alakzatokon belüli cseréjét.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  GroupDocs.Watermark for .NET: Győződjön meg arról, hogy telepítette és beállította a GroupDocs.Watermark for .NET-et. Letöltheti innen[itt](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentum elérési útja: Meg kell adnia annak a Word-dokumentumnak az elérési útját, ahol le szeretné cserélni a szöveget.

## Névterek importálása
A kód megírása előtt importálja a szükséges névtereket:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
 Töltse be a Word dokumentumot a`Watermarker` osztály:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A kód itt folytatódik...
}
```
## 2. lépés: Szerezzen be tartalmat és cserélje ki a szöveget
A dokumentum betöltése után szerezze be a tartalmat, és cserélje ki a szöveget az alakzatokon belül:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## 3. lépés: Mentse el a dokumentumot
A szöveg cseréje után mentse el a módosított dokumentumot:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Következtetés
.NET-hez készült GroupDocs egyszerűvé teszi az alakzat szövegének formázott szöveggel való helyettesítését. Az oktatóanyagban ismertetett lépések követésével hatékonyan kezelheti és kezelheti a dokumentumokon belüli szöveget.

## GYIK
### Cserélhetem-e szöveget más típusú dokumentumokban a GroupDocs.Watermark for .NET használatával?
Igen, a GroupDocs különféle dokumentumformátumokat támogat, például PDF, Excel, PowerPoint stb.
### A GroupDocs.Watermark kompatibilis a .NET Core programmal?
Igen, a GroupDocs.Watermark támogatja a .NET-keretrendszert és a .NET Core-t is.
### A GroupDocs.Watermark támogatja a képek vízjelként történő hozzáadását?
A GroupDocs.Watermark természetesen lehetővé teszi szöveges és képi vízjelek hozzáadását a dokumentumokhoz.
### Testreszabhatom a hozzáadott vízjelek megjelenését a GroupDocs.Watermark segítségével?
Igen, teljes mértékben Ön szabályozhatja a vízjelek megjelenését, helyzetét és egyéb tulajdonságait.
### Elérhető a GroupDocs.Watermark for .NET próbaverziója?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).