---
title: Vízjel hozzáadása a PDF-beli képekhez
linktitle: Vízjel hozzáadása a PDF-beli képekhez
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat vízjeleket PDF-dokumentumokban lévő képekhez a GroupDocs.Watermark for .NET segítségével részletes, lépésenkénti oktatóanyagunk segítségével. Biztonságos PDF-fájlokat egyszerűen.
type: docs
weight: 19
url: /hu/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Bevezetés
Vízjelek hozzáadása a PDF-dokumentumban lévő képekhez elengedhetetlen lehet a szellemi tulajdon védelme vagy a dokumentumok hitelességének biztosítása érdekében. A GroupDocs.Watermark for .NET használatával ez a feladat hatékonyan és egyszerűen elvégezhető. Ez az oktatóanyag végigvezeti Önt a folyamat minden lépésén, a környezet beállításától a vízjelek hozzáadásán át a végleges dokumentum mentéséig. Merüljünk el!
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1. Visual Studio: Telepítse a Visual Studio-t, az integrált fejlesztői környezetet (IDE) .NET-alkalmazásokhoz.
2.  GroupDocs.Watermark for .NET: Töltse le és telepítse a GroupDocs.Watermark for .NET könyvtárat a[kiadási oldal](https://releases.groupdocs.com/Watermark/net/).
3. PDF-dokumentum: Készítsen PDF-dokumentumot képeket a vízjel funkció teszteléséhez.
4.  Ideiglenes engedély: Szerezzen be a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) ha értékeli a terméket.
## Névterek importálása
Először győződjön meg arról, hogy a szükséges névtereket importálta a projektbe. Ez magában foglalja a PDF-dokumentumok és vízjelek kezeléséhez szükséges alapvető névtereket.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Állítsa be a dokumentum elérési útját és kimeneti könyvtárát
Kezdésként határozza meg a bemeneti dokumentum elérési útját és azt a kimeneti könyvtárat, ahová a vízjellel ellátott dokumentum mentésre kerül. Ez a lépés kulcsfontosságú annak biztosításához, hogy a program tudja, hol találja a forrásdokumentumot, és hol tárolja a feldolgozott fájlt.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2. lépés: Töltse be a PDF-dokumentumot
 Ezután be kell töltenie a PDF-dokumentumot a segítségével`PdfLoadOptions`. Ez az osztály lehetővé teszi a PDF betöltésére vonatkozó beállítások megadását, például szükség esetén a jelszavas védelmet.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A vízjelezés kódja ide kerül
}
```
## 3. lépés: Hozza létre a vízjelet
Most inicializálja a vízjelet. Ebben a példában szöveges vízjelet hozunk létre, amely így szól: „Védett kép”. Igényeinek megfelelően testreszabhatja a betűtípust, az igazítást, az elforgatást és a méretezést.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4. lépés: Nyissa meg a PDF tartalmat
PDF-dokumentum tartalmának lekérése. Pontosabban, el kell érnünk a képeket a PDF-ben. Itt az első oldalra koncentrálunk, de szükség szerint ezt kiterjesztheti más oldalakra is.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Töltse le az összes képet az első oldalról
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## 5. lépés: Alkalmazza a vízjelet a képekre
Lapozzon át minden, az első oldalon található képet, és alkalmazza a vízjelet. Ez biztosítja, hogy a megadott oldalon lévő összes képen vízjel kerüljön alkalmazásra.
```csharp
// Vízjel hozzáadása az összes talált képhez
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## 6. lépés: Mentse el a vízjellel ellátott dokumentumot
Végül mentse a vízjellel ellátott PDF-fájlt a megadott kimeneti könyvtárba. Ez a lépés a módosítások új fájlba írásával zárja le a folyamatot.
```csharp
watermarker.Save(outputFileName);
```
## Következtetés
És megvan! Vízjel hozzáadása a PDF-ben található képekhez a GroupDocs Watermark for .NET használatával egyszerű folyamat, amely nagymértékben növelheti a dokumentumok biztonságát és hitelességét. Az alábbi lépések követésével biztosíthatja szellemi tulajdonának védelmét és dokumentumai biztonságát.
## GYIK
### Mi az a GroupDocs.Watermark for .NET?
GroupDocs.Watermark for .NET egy átfogó könyvtár, amely lehetővé teszi a fejlesztők számára vízjelek hozzáadását, keresését és eltávolítását különféle dokumentumformátumokban, beleértve a PDF-eket is.
### Hozzáadhatok szöveges és képi vízjeleket is a GroupDocs.Watermark segítségével?
Igen, a GroupDocs.Watermark támogatja a szöveges és képi vízjeleket is, rugalmasságot biztosítva a különböző típusú vízjelezési igényekhez.
### Lehetséges több oldalt vízjellel ellátni egy PDF-ben?
Teljesen! A PDF minden egyes oldalát végigpörgetheti, és minden oldalon vízjelet helyezhet a képekre.
### Szükségem van licencre a GroupDocs.Watermark for .NET használatához?
 Igen, engedély szükséges. Megszerezheti a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) értékelési célokra.
### Hol találok további dokumentációt a GroupDocs.Watermark for .NET-hez?
 Részletes dokumentációt találhat a[GroupDocs.Watermark dokumentációs oldal](https://reference.groupdocs.com/Watermark/net/).