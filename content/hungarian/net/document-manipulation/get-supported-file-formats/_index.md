---
title: Szerezze be a támogatott fájlformátumokat
linktitle: Szerezze be a támogatott fájlformátumokat
second_title: GroupDocs.Watermark .NET API
description: A GroupDocs.Watermark for .NET segítségével könnyedén adhat hozzá vízjeleket dokumentumaihoz. Kövesse átfogó, lépésenkénti útmutatónkat digitális eszközei védelméhez.
weight: 13
url: /hu/net/document-manipulation/get-supported-file-formats/
---

# Szerezze be a támogatott fájlformátumokat

## Bevezetés
dokumentumok vízjelezése kulcsfontosságú lépés digitális eszközei védelmében. Legyen szó a szellemi tulajdon védelméről, a titoktartásról vagy egyszerűen a márkaépítésről, a vízjelek létfontosságú szerepet játszanak. Ha Ön .NET-fejlesztő, aki a vízjelezési képességeket szeretné integrálni alkalmazásaiba, a GroupDocs.Watermark for .NET egy hatékony és sokoldalú eszköz, amelyet érdemes megfontolni. Ez az oktatóanyag végigvezeti Önt a GroupDocs.Watermark használatának lényegein, a telepítéstől az első vízjel felhelyezéséig, az egyes lépéseket lebontva, hogy könnyen követhesse.
## Előfeltételek
Mielőtt belemerülnénk a részletekbe, győződjünk meg arról, hogy mindennel rendelkezünk, ami az induláshoz szükséges:
1.  Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen. Letöltheti a[Visual Studio webhely](https://visualstudio.microsoft.com/).
2. .NET-keretrendszer: A GroupDocs.Watermark a .NET-keretrendszer különféle verzióit támogatja. Győződjön meg arról, hogy projektje kompatibilis verziót céloz meg.
3. GroupDocs.Watermark for .NET: Letöltheti a legújabb verziót a[kiadási oldal](https://releases.groupdocs.com/Watermark/net/).
4. Alapvető C# ismerete: Ez az oktatóanyag feltételezi, hogy alapjaiban ismeri a C# és .NET fejlesztését.
## Névterek importálása
Először is importáljuk a szükséges névtereket a projektbe. Nyissa meg a C# fájlt, és a tetején lévő direktívák segítségével adja hozzá a következőket:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Az importált névterek után készen áll arra, hogy vízjeleket adjon a dokumentumokhoz.

## 1. lépés: Inicializálja a Watermarking Engine-t
 Az első lépés a vízjel-motor inicializálása. Ez magában foglalja egy példány létrehozását a`Watermarker` osztályt a vízjellel ellátni kívánt dokumentummal.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Ez a kódrészlet beállítja a`Watermarker` objektum, amellyel vízjeleket alkalmazhat a dokumentumban.
## 2. lépés: Szöveges vízjel hozzáadása
Most adjunk hozzá egy egyszerű szöveges vízjelet a dokumentumhoz. A szöveges vízjelek kiválóan alkalmasak olyan címkék hozzáadására, mint a „Bizalmas” vagy a „Piszkozat”.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Itt létrehoztunk egy`TextWatermark` „Bizalmas” szövegű objektumot, állítsa be a betűtípust és a színt, és igazítsa a dokumentum közepéhez.
## 3. lépés: Kép vízjel hozzáadása
Ha inkább egy képet szeretne vízjelként használni, a GroupDocs.Watermark megkönnyíti ezt.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Ebben a példában létrehozunk egy`ImageWatermark` objektumot, állítsa be a méreteit, és igazítsa a dokumentum jobb felső sarkához.
## 4. lépés: Mentse el a dokumentumot
A kívánt vízjelek hozzáadása után az utolsó lépés a módosított dokumentum mentése.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Ezzel elmenti a vízjellel ellátott dokumentumot a megadott útvonalra, és felszabadítja az általa használt erőforrásokat`Watermarker` példa.
## 5. lépés: Szerezze be a támogatott fájlformátumokat
A GroupDocs.Watermark által támogatott fájlformátumok megtekintéséhez használja a következő kódrészletet:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Ez kinyomtatja az összes fájltípust, amelyet a GroupDocs.Watermark képes kezelni, így átfogó képet kaphat a képességeiről.
## Következtetés
Watermark for .NET segítségével egyszerűen és hatékonyan helyezheti el a dokumentumokat. Ennek az oktatóanyagnak a követésével megtanulta, hogyan inicializálhatja a vízjelkészítő motort, hogyan adhat hozzá szöveges és képi vízjeleket, mentheti el a vízjellel ellátott dokumentumokat, és hogyan sorolhatja fel a támogatott fájlformátumokat. Ezekkel az eszközökkel magabiztosan védheti dokumentumait.
 Ha bármilyen kérdése van, vagy további segítségre van szüksége, ne habozzon felkeresni a[GroupDocs.Watermark támogatási fórum](https://forum.groupdocs.com/c/watermark/19).
## GYIK
### Hogyan telepíthetem a GroupDocs.Watermark for .NET programot?
 Letöltheti a[kiadási oldal](https://releases.groupdocs.com/Watermark/net/) és adja hozzá a DLL-t a projekthez.
### Ingyenesen kipróbálhatom a GroupDocs.Watermark alkalmazást?
 Igen, kérheti a[ingyenes próbaverzió](https://releases.groupdocs.com/) hogy vásárlás előtt értékelje a szoftvert.
### Milyen fájlformátumokat támogat a GroupDocs.Watermark?
A mellékelt kódrészlet segítségével felsorolhatja az összes támogatott fájlformátumot.
### Hogyan vásárolhatok licencet a GroupDocs.Watermark számára?
 A licencek közvetlenül a szolgáltatótól vásárolhatók meg[vásárlási oldal](https://purchase.groupdocs.com/buy).
### Elérhető a GroupDocs.Watermark dokumentációja?
 Igen, átfogó dokumentáció áll rendelkezésre[itt](https://tutorials.groupdocs.com/Watermark/net/).