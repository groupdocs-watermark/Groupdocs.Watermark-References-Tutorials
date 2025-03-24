---
title: Zárolt vízjel hozzáadása a Word Docs összes oldalához
linktitle: Zárolt vízjel hozzáadása a Word Docs összes oldalához
second_title: GroupDocs.Watermark .NET API
description: Biztosítsa dokumentumait zárolt vízjelek hozzáadásával a Groupdocs.Watermark for .NET segítségével. Kövesse lépésről lépésre útmutatónkat az egyszerű megvalósítás érdekében.
weight: 11
url: /hu/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# Zárolt vízjel hozzáadása a Word Docs összes oldalához

## Bevezetés
A vízjelek hozzáadása a dokumentumokhoz létfontosságú lépés a tartalom biztonságának és márkajelzésének kialakításában. Akár megakadályozza a jogosulatlan használatot, akár egyszerűen csak professzionális hatást ad hozzá, a vízjelek többféle célt szolgálhatnak. Ebben az oktatóanyagban végigvezetjük a zárolt vízjel hozzáadásának folyamatán a Word-dokumentum összes oldalához a Groupdocs.Watermark for .NET segítségével.
## Előfeltételek
Mielőtt belemerülnénk a lépésről lépésre szóló útmutatóba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:
1. Groupdocs.Watermark for .NET: Töltse le a legújabb verziót innen[itt](https://releases.groupdocs.com/Watermark/net/).
2. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépen.
3. Fejlesztői környezet: Olyan fejlesztői környezet, mint a Visual Studio.
4.  Licenc: Választhat a[ingyenes próbaverzió](https://releases.groupdocs.com/) vagy vásárolni a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/).
## Névterek importálása
Először is importálnia kell a szükséges névtereket a projektbe. Ezek elengedhetetlenek a Groupdocs.Watermark által biztosított osztályok és metódusok eléréséhez.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Állítsa be projektjét

Nyissa meg fejlesztői környezetét, és hozzon létre egy új .NET-projektet. Ez lehet konzolalkalmazás vagy bármilyen más, az Ön igényeinek megfelelő típus.

Hozzá kell adnia a Groupdocs.Watermark csomagot a projekthez. Ezt a NuGet Package Manager segítségével teheti meg. Futtassa a következő parancsot a NuGet Package Manager konzolon:
```sh
Install-Package GroupDocs.Watermark
```
## 2. lépés: Töltse be a Word-dokumentumot
### Határozza meg a dokumentum elérési útját
Adja meg a Word-dokumentum elérési útját. Ez lesz az a dokumentum, amelyhez a vízjelet hozzá szeretné adni.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Állítsa be a Betöltési beállításokat
 Hozzon létre egy példányt a`WordProcessingLoadOptions` hogy betöltse a Word dokumentumot meghatározott beállításokkal.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3. lépés: Hozza létre a vízjelet
### Inicializálja a vízjelet
 Használni a`Watermarker`osztályba, töltse be a dokumentumot a megadott betöltési lehetőségekkel.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A további lépések ebben a blokkban találhatók
}
```
### Határozza meg a vízjel tulajdonságait
 Hozzon létre egy`TextWatermark` példányt a kívánt szöveggel, betűtípussal és színnel.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 4. lépés: Alkalmazzon vízjelet az összes oldalra
### Állítsa be a vízjel beállításait
 Határozza meg`WordProcessingWatermarkPagesOptions` és állítsa be a`IsLocked` tulajdonságot true értékre a vízjel zárolásához. Ez biztosítja, hogy a vízjel ne távolítható el könnyen.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Választható: Jelszavas védelem hozzáadása
Ha további biztonsági réteget szeretne hozzáadni, beállíthat egy jelszót a vízjelhez.
```csharp
// Jelszóval való védelem
// options.Password = "7654321";
```
### Adja hozzá a vízjelet
 Használja a`Add` módszere a`Watermarker` osztályt a vízjel hozzáadásához a dokumentumhoz a megadott beállításokkal.
```csharp
watermarker.Add(watermark, options);
```
## 5. lépés: Mentse el a dokumentumot
Végül mentse a módosított dokumentumot a megadott kimeneti fájlba.
```csharp
watermarker.Save(outputFileName);
```

## Következtetés
Ha követi ezeket a lépéseket, a Groupdocs.Watermark for .NET segítségével könnyedén hozzáadhat zárolt vízjelet Word-dokumentumai minden oldalához. Ez nemcsak megvédi dokumentumait az illetéktelen használattól, hanem professzionális megjelenést is kölcsönöz a tartalomnak. A Groupdocs.Watermark átfogó megoldást kínál a vízjelezési igényekre, biztosítva, hogy dokumentumai biztonságban és márkajelzéssel rendelkezzenek.
## GYIK
### Használhatok képet vízjelként szöveg helyett?
 Igen, a Groupdocs támogatja a szöveges és képi vízjeleket. Cserélheted`TextWatermark` val vel`ImageWatermark` és adja meg a képét.
### Testreszabható a vízjel helyzete?
 Teljesen! A vízjel helyzetét olyan tulajdonságokkal állíthatja be, mint pl`HorizontalAlignment` és`VerticalAlignment`.
### Alkalmazhatok különböző vízjeleket a dokumentum különböző oldalaira?
 Igen, testreszabhatja a vízjeleket bizonyos oldalakhoz a segítségével`PageIndex` ingatlan a`WordProcessingWatermarkPagesOptions`.
### A Groupdocs.Watermark támogatja a Worden kívül más dokumentumformátumokat is?
Igen, a Groupdocs Watermark különféle formátumokat támogat, beleértve a PDF, Excel, PowerPoint stb.
### Mik a rendszerkövetelmények a Groupdocs.Watermark használatához?
Szüksége van egy telepített .NET-keretrendszerre és egy fejlesztői környezetre, például a Visual Studiora.