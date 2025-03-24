---
title: Szöveg vízjel hozzáadása
linktitle: Szöveg vízjel hozzáadása
second_title: GroupDocs.Watermark .NET API
description: Ebből a lépésenkénti útmutatóból megtudhatja, hogyan adhat szöveges vízjeleket a dokumentumokhoz a Groupdocs Watermark for .NET segítségével.
weight: 11
url: /hu/net/watermarking-basics/add-text-watermark/
---

# Szöveg vízjel hozzáadása

## Bevezetés
GroupDocs.Watermark for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára vízjelek hozzáadását, keresését és eltávolítását különféle dokumentumformátumokból .NET-alkalmazásokban. Ebben az oktatóanyagban arra összpontosítunk, hogy szöveges vízjelet adjunk egy dokumentumhoz a GroupDocs.Watermark segítségével.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1. C# programozási nyelv alapismerete.
2. A Visual Studio telepítve van a rendszerére.
3.  GroupDocs.Watermark for .NET könyvtár telepítve. Letöltheti innen[itt](https://releases.groupdocs.com/Watermark/net/).

## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1. lépés: Határozza meg a dokumentum elérési útját és kimeneti könyvtárát
Határozza meg a bemeneti dokumentum elérési útját és azt a kimeneti könyvtárat, ahová a vízjellel ellátott dokumentum mentésre kerül.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` a bemeneti dokumentum abszolút vagy relatív elérési útjával, például:`@"C:\Docs\document.pdf"`. Adja meg azt a könyvtárat is, ahová menteni kívánja a vízjellel ellátott dokumentumot.
## 2. lépés: Szöveg vízjel hozzáadása
 Példányosítsa a`Watermarker` osztályt a bemeneti dokumentum elérési útjával. Ezután hozzon létre a`TextWatermark` objektumot a kívánt szöveg- és betűtípus-beállításokkal.
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

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk szöveges vízjelet egy dokumentumhoz a GroupDocs.Watermark for .NET segítségével. Intuitív API-jával a fejlesztők könnyen kezelhetik a vízjeleket különféle dokumentumformátumokban.
## GYIK
### A GroupDocs.Watermark for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Watermark a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Microsoft Word, Excel, PowerPoint és sok más formátumot.
### Testreszabhatom a szöveges vízjel megjelenését?
Igen, testreszabhatja a szöveges vízjel különféle tulajdonságait, például a betűtípust, a színt, az igazítást és az átlátszóságot.
### A GroupDocs.Watermark támogatja a vízjelek eltávolítását a dokumentumokból?
Igen, a GroupDocs.Watermark lehetőséget kínál vízjelek keresésére és eltávolítására a dokumentumokból.
### Kipróbálhatom a GroupDocs.Watermark for .NET szolgáltatást vásárlás előtt?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok technikai támogatást a GroupDocs.Watermark számára?
 Technikai támogatást kaphat, ha ellátogat a[GroupDocs.Watermark fórum](https://forum.groupdocs.com/c/watermark/19).