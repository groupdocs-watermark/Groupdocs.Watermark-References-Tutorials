---
title: Vízjel hozzáadása az XObjectshez PDF-ben
linktitle: Vízjel hozzáadása az XObjectshez PDF-ben
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat vízjeleket PDF-ben található XObjects-hez a Groupdocs.Watermark for .NET segítségével. Kövesse lépésről lépésre útmutatónkat az egyszerű megvalósítás érdekében.
type: docs
weight: 20
url: /hu/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Bevezetés
A PDF-fájlok vízjelezése kulcsfontosságú lépés annak biztosításához, hogy a dokumentumokat megvédjük a jogosulatlan használattól. A Groupdocs.Watermark for .NET segítségével még soha nem volt ilyen egyszerű vízjelek hozzáadása a PDF-ben található XObjects-hez. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a folyamaton, biztosítva, hogy magabiztosan alkalmazhasson vízjeleket PDF-dokumentumaira. Kezdjük el!
## Előfeltételek
Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy mindennel rendelkezik, ami a zökkenőmentes követéshez szükséges:
-  Groupdocs.Watermark for .NET: Töltse le és telepítse a legújabb verziót innen[itt](https://releases.groupdocs.com/Watermark/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy a fejlesztői gépen telepítve van a .NET-keretrendszer.
- Fejlesztői környezet: Használja a Visual Studio-t vagy bármely más IDE-t, amely támogatja a .NET-fejlesztést.
-  Ideiglenes engedély: Szerezzen be a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) ha értékeli a terméket.
Ha megvannak ezek az előfeltételek, készen áll a PDF-fájlok vízjelezésének megkezdésére.
## Névterek importálása
Először is importálnia kell a szükséges névtereket a projektbe. Nyissa meg a C# projektet, és direktívák segítségével adja hozzá a következőket:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Állítsa be a dokumentum elérési útját
Az első lépés a dokumentum elérési útjainak beállítása. Határozza meg az elérési utat, ahol a PDF található, és hová szeretné menteni a vízjellel ellátott PDF-fájlt.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` és`"Your Document Directory"` a gépén lévő tényleges útvonalakkal.
## 2. lépés: Inicializálja a PDF-betöltési beállításokat
Ezután inicializálnia kell a PDF-betöltési beállításokat. Ez kulcsfontosságú a PDF-tartalom megfelelő betöltéséhez.
```csharp
var loadOptions = new PdfLoadOptions();
```
## 3. lépés: Töltse be a PDF-dokumentumot
 betöltési beállítások használatával töltse be a PDF dokumentumot a`Watermarker` osztály.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 4. lépés: Hozza létre a vízjelet
Most létre kell hoznia a vízjelet, amely hozzáadódik a PDF-hez. Ehhez az oktatóanyaghoz szöveges vízjelet hozunk létre.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## 5. lépés: Adjon vízjelet az XObjectshez
A vízjel alkalmazásához ismételje meg az egyes oldalakat és minden XObject-et a PDF-ben.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Vízjel hozzáadása a képhez
            xObject.Image.Add(watermark);
        }
    }
}
```
## 6. lépés: Mentse el a vízjellel ellátott PDF-fájlt
Végül mentse a vízjellel ellátott PDF-fájlt a megadott kimeneti fájlba.
```csharp
    watermarker.Save(outputFileName);
}
```
És megvan! A PDF-fájl most már minden XObjectjén vízjelet tartalmaz.
## Következtetés
 Vízjelek hozzáadása a PDF-dokumentumokhoz a Groupdocs Watermark for .NET segítségével egy egyszerű folyamat, amely további biztonságot nyújt. Az oktatóanyagban ismertetett lépések követésével biztosíthatja, hogy dokumentumai védve legyenek a jogosulatlan használat ellen. Ne feledje, mindig hivatkozhat a[dokumentáció](https://reference.groupdocs.com/Watermark/net/) részletesebb információkért és speciális funkciókért.
## GYIK
### Használhatok képet vízjelként szöveg helyett?
Igen, a Groupdocs.Watermark for .NET támogatja a szöveges és képi vízjeleket is.
### Hogyan tesztelhetem a Groupdocs.Watermark alkalmazást vásárlás nélkül?
 Használhatja a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) a termék értékeléséhez.
### Testreszabható a vízjel megjelenése?
Teljesen! Testreszabhatja a betűtípust, a méretet, az elforgatási szöget stb.
### A Groupdocs.Watermark támogat más dokumentumformátumokat?
Igen, különféle formátumokat támogat, beleértve a Word, Excel és PowerPoint.
### Hol kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat a[Groupdocs fórum](https://forum.groupdocs.com/c/watermark/19).