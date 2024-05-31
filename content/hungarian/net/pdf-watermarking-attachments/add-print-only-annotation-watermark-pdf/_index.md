---
title: Csak nyomtatási megjegyzés vízjel hozzáadása a PDF-hez
linktitle: Csak nyomtatási megjegyzés vízjel hozzáadása a PDF-hez
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat hozzá csak nyomtatható jegyzetvízjeleket PDF-fájlokhoz a GroupDocs.Watermark for .NET segítségével. Fokozatmentesen fokozza a dokumentumok biztonságát és a márkaépítést.
type: docs
weight: 13
url: /hu/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Watermark for .NET segítségével csak nyomtatható megjegyzés vízjel hozzáadásának folyamatába fogunk bele egy PDF-fájlba. A dokumentumok vízjelezése a dokumentumbiztonság és a márkaépítés kulcsfontosságú eleme, és a GroupDocs.Watermark zökkenőmentes megoldást kínál a .NET-fejlesztők számára ennek eléréséhez.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
- A C# programozási nyelv alapvető ismerete.
- A Visual Studio telepítve van a gépedre.
- GroupDocs.Watermark for .NET könyvtár telepítve a projektben.

## Névterek importálása
A kezdéshez feltétlenül importálja a szükséges névtereket:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
 Először is be kell töltenie a vízjellel ellátni kívánt PDF-dokumentumot. Cserélje ki`"Your Document Path"` a PDF-fájl elérési útjával és`"Your Document Directory"` azzal a könyvtárral, ahová a kimeneti fájlt menteni szeretné.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Itt lesz hozzáadva a vízjel kód
}
```
## 2. lépés: Vízjel hozzáadása
Ezután hozzon létre egy szöveges vízjel objektumot a kívánt szöveggel és betűtípussal. Készlet`isPrintOnly` nak nek`true` annak biztosítása érdekében, hogy a vízjel csak a dokumentum nyomtatásakor legyen látható, nézet módban ne.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## 3. lépés: Konfigurálja a vízjel beállításait
Adja meg a vízjel beállításait, például az oldalindexet, ahová a vízjelet hozzá kell adni, és csak nyomtatásra alkalmas megjegyzésként adja meg.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## 4. lépés: Vízjel alkalmazása
Adja hozzá a vízjelet a dokumentumhoz a megadott beállításokkal, és mentse el a kimeneti fájlt.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk csak nyomtatható megjegyzés vízjelet PDF-dokumentumokhoz a GroupDocs.Watermark for .NET segítségével. Ez lehetővé teszi a fejlesztők számára, hogy könnyedén fokozzák a dokumentumok biztonságát és a márkaépítést.
## GYIK
### A GroupDocs.Watermark kompatibilis a PDF-en kívül más dokumentumformátumokkal is?
Igen, a GroupDocs különféle dokumentumformátumokat támogat, például Word, Excel, PowerPoint és képeket.
### Testreszabhatom a vízjel megjelenését?
Természetesen a GroupDocs.Watermark kiterjedt lehetőségeket kínál a vízjel szövegének, betűtípusának, színének, méretének és elhelyezésének testreszabásához.
### A GroupDocs.Watermark kínál kötegelt feldolgozási lehetőségeket?
Természetesen a fejlesztők egyszerre több dokumentumot is vízjelezhetnek a kötegelt feldolgozási funkciók használatával.
### Elérhető a GroupDocs.Watermark próbaverziója?
Igen, elérheti a GroupDocs.Watermark ingyenes próbaverzióját a megadott linkről.
### Hogyan kaphatok technikai támogatást a GroupDocs.Watermark számára?
Technikai segítséget kérhet a GroupDocs.Watermark fórumon, amely a megadott támogatási linken érhető el.