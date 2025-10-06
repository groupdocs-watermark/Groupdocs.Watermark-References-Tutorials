---
title: Jelszóval védett dokumentum betöltése
linktitle: Jelszóval védett dokumentum betöltése
second_title: GroupDocs.Watermark .NET API
description: Részletes útmutatónkból megtudhatja, hogyan adhat vízjeleket jelszóval védett dokumentumokhoz a Groupdocs Watermark for .NET segítségével. Könnyedén biztonságossá teheti és márkázza fájljait.
weight: 13
url: /hu/net/document-loadings/load-password-protected-document/
type: docs
---
# Jelszóval védett dokumentum betöltése

## Bevezetés
Szeretné megvédeni dokumentumait vízjelek hozzáadásával, még akkor is, ha azok jelszóval védettek? A Groupdocs.Watermark for .NET egy hatékony eszköz, amely lehetővé teszi, hogy ezt megtegye. Ebben az oktatóanyagban végigvezetjük a jelszóval védett dokumentum betöltésének folyamatán, és a Groupdocs.Watermark for .NET segítségével vízjel hozzáadásával. Merüljünk el!
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1. Visual Studio: A Visual Studio bármely verziója, amely telepítve van a gépre.
2. .NET-keretrendszer: Győződjön meg arról, hogy rendelkezik a .NET-keretrendszer 4.6.1-es vagy újabb verziójával.
3. Groupdocs.Watermark for .NET: Töltse le és telepítse a Groupdocs.Watermark for .NET könyvtárat a[letöltési link](https://releases.groupdocs.com/Watermark/net/).
## Névterek importálása
Először is importálnunk kell a szükséges névtereket a projektünkbe. Ez biztosítja, hogy elérjük a Groupdocs.Watermark for .NET által biztosított összes metódust és tulajdonságot.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Most bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre.
## 1. lépés: Állítsa be projektjét
Kezdésként hozzon létre egy új C# konzolalkalmazást a Visual Studioban. A projekt beállítása után telepítse a Groupdocs.Watermark for .NET könyvtárat a NuGet Package Manager segítségével.
1. Nyissa meg a Visual Studio-t, és hozzon létre egy új konzolalkalmazást (.NET-keretrendszer).
2.  Menj`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Keressen rá`GroupDocs.Watermark` és telepítse a csomagot.
## 2. lépés: Határozza meg a dokumentum elérési útját
Ezután meg kell határoznia a jelszóval védett dokumentum elérési útját és a kimeneti fájl elérési útját, ahová a vízjellel ellátott dokumentum mentésre kerül.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` és`"Your Document Directory"` a gépén lévő tényleges útvonalakkal.
## 3. lépés: Állítsa be a betöltési beállításokat a jelszóval
Jelszóval védett dokumentum megnyitásához meg kell adnia a jelszót a betöltési beállításoknál.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Cserélje ki`"P@$w0rd"` a dokumentum tényleges jelszavával.
## 4. lépés: Töltse be a dokumentumot
 Most töltsük be a dokumentumot a`Watermarker` osztály.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A vízjel hozzáadásához szükséges kód ide kerül
}
```
## 5. lépés: Hozzon létre egy vízjelet
Létrehozunk egy szöveges vízjelet, amelyet hozzáadhatunk a dokumentumhoz. Igény szerint testreszabhatja a szöveget, a betűtípust, a méretet és az egyéb tulajdonságokat.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Nyugodtan változtass`"Test watermark"`, `"Arial"` , és`12` a kívánt szövegre, betűtípusra és méretre.
## 6. lépés: Adja hozzá a vízjelet
 Adja hozzá a vízjelet a dokumentumhoz a gombbal`Add` módszere a`Watermarker` osztály.
```csharp
watermarker.Add(watermark);
```
## 7. lépés: Mentse el a vízjellel ellátott dokumentumot
Végül mentse a vízjellel ellátott dokumentumot a megadott kimeneti fájl elérési útjára.
```csharp
watermarker.Save(outputFileName);
```
## Következtetés
Vízjelek hozzáadása a jelszóval védett dokumentumokhoz egyszerű folyamat a Watermark for .NET segítségével. Ezen egyszerű lépések követésével biztosíthatja, hogy dokumentumai az Ön igényei szerint védettek és márkajelzéssel rendelkezzenek. Legyen szó biztonságról, márkaépítésről vagy megfelelőségről, a dokumentumok vízjelezése még soha nem volt ilyen egyszerű.
## GYIK
### Hozzáadhatok képvízjeleket a Groupdocs.Watermark for .NET segítségével?
 Igen, szöveges és képi vízjeleket is hozzáadhat. Egyszerűen használja a`ImageWatermark` osztály helyett`TextWatermark`.
### Eltávolíthatók a vízjelek egy dokumentumból?
Igen, a Groupdocs.Watermark for .NET módszereket biztosít vízjelek keresésére és eltávolítására.
### A Groupdocs.Watermark for .NET támogatja a PDF-eken kívül más dokumentumformátumokat is?
Igen, a formátumok széles skáláját támogatja, beleértve a Word, Excel, PowerPoint és egyebeket.
### Testreszabhatom a vízjel megjelenését?
Teljesen! Testreszabhatja a betűtípust, a méretet, a színt, az átlátszatlanságot stb.
### Hol kaphatok támogatást, ha problémákba ütközöm?
 Meglátogathatja a[Groupdocs támogatási fórum](https://forum.groupdocs.com/c/watermark/19) segítségért és útmutatásért.