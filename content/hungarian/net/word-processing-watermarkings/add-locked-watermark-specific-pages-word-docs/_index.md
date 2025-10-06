---
title: Zárolt vízjel hozzáadása adott oldalakhoz a Word Dokumentumokban
linktitle: Zárolt vízjel hozzáadása adott oldalakhoz a Word Dokumentumokban
second_title: GroupDocs.Watermark .NET API
description: Az egyszerű, lépésenkénti útmutatónk segítségével megtudhatja, hogyan adhat hozzá zárolt vízjelet a Word dokumentumok adott oldalaihoz a GroupDocs.Watermark for .NET segítségével.
weight: 12
url: /hu/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Zárolt vízjel hozzáadása adott oldalakhoz a Word Dokumentumokban

## Bevezetés
Vízjelet szeretne hozzáadni a Word-dokumentumok bizonyos oldalaihoz, de szeretné zárolni, hogy ne lehessen könnyen eltávolítani vagy szerkeszteni? Jó helyen jársz! Ebben az oktatóanyagban végigvezetjük a zárolt vízjel hozzáadásának folyamatán a Word dokumentumok adott oldalaihoz a GroupDocs.Watermark for .NET segítségével. Ez a hatékony könyvtár megkönnyíti a vízjelek alkalmazását, kezelését és testreszabását különféle dokumentumtípusokon. Függetlenül attól, hogy Ön fejlesztő, vagy csak valaki, akinek meg kell őriznie dokumentumait, ez az útmutató minden lépésen átvezeti Önt.
## Előfeltételek
Mielőtt belevágnánk az oktatóanyagba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:
1.  GroupDocs.Watermark for .NET: Megteheti[Letöltés](https://releases.groupdocs.com/Watermark/net/) a legújabb verzió.
2. Fejlesztői környezet: Egy IDE, mint a Visual Studio.
3. Alapvető C# ismerete: Hasznos lesz a C# programozás ismerete.
4. Dokumentum vízjelhez: Word dokumentum (.docx vagy .doc), amelyhez vízjelet szeretne hozzáadni.
## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe. Ezek a névterek hozzáférést biztosítanak a GroupDocs.Watermark használatához szükséges osztályokhoz és metódusokhoz.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Most, hogy az előfeltételeket lefedtük és a szükséges névtereket importáltuk, bontsuk le a folyamatot lépésről lépésre.
## 1. lépés: Töltse be a Word-dokumentumot
 Először is be kell töltenie azt a Word-dokumentumot, amelyhez vízjelet szeretne hozzáadni. Ezt a`Watermarker` osztály együtt`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Folytassa a következő lépésekkel
}
```
## 2. lépés: Hozza létre a szöveges vízjelet
Ezután hozzon létre egy szöveges vízjelet. Igényeinek megfelelően testreszabhatja a szöveget, a betűtípust, a színt és az egyéb tulajdonságokat.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 3. lépés: Konfigurálja a vízjel beállításait
 A vízjel bizonyos oldalakra történő alkalmazásához és zárolásához konfigurálja a`WordProcessingWatermarkPagesOptions`Itt adja meg az oldalszámokat, ahol a vízjelnek meg kell jelennie, és beállíthatja a zárolási beállításokat.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Adja meg az oldalakat
options.IsLocked = true; // Zárja le a vízjelet
options.LockType = WordProcessingLockType.AllowOnlyComments; // Állítsa be a zár típusát
// Jelszóval való védelemre
// options.Password = "7654321";
```
## 4. lépés: Adja hozzá a vízjelet a dokumentumhoz
A vízjel és a beállítások konfigurálásával most már hozzáadhatja a vízjelet a dokumentumhoz.
```csharp
watermarker.Add(watermark, options);
```
## 5. lépés: Mentse el a dokumentumot
Végül mentse el a dokumentumot vízjellel. Válassza ki a megfelelő kimeneti útvonalat, és mentse el a fájlt.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Következtetés
Gratulálunk! Sikeresen hozzáadott egy zárolt vízjelet egy Word-dokumentum bizonyos oldalaihoz a GroupDocs.Watermark for .NET segítségével. Ez az oktatóanyag az összes lényeges lépést lefedte a dokumentum betöltésétől a vízjeles fájl mentéséig. Az alábbi lépések követésével gondoskodhat arról, hogy dokumentumai biztonságosan vízjellel legyenek ellátva, így megvédheti tartalmát a jogosulatlan szerkesztéstől és használattól.
 További információkért tekintse meg a[GroupDocs.Watermark dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) . Ha bármilyen kérdése van, vagy további segítségre van szüksége, keresse fel a[támogatói fórum](https://forum.groupdocs.com/c/watermark/19).
## GYIK
### Mi az a GroupDocs.Watermark for .NET?
GroupDocs.Watermark for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy vízjeleket adjanak különféle típusú dokumentumokhoz, beleértve a Word-t, PDF-t, Excelt és egyebeket.
### Alkalmazhatok vízjelet egy dokumentum több oldalára?
 Igen, több oldalszámot is megadhat a`PageNumbers` tömböt a vízjelek több oldalra történő alkalmazásához.
### Hogyan védhetek jelszóval egy vízjelet?
 A vízjelet jelszóval védheti a`Password` ingatlan a`WordProcessingWatermarkPagesOptions`.
### Testreszabható a vízjel megjelenése?
Teljesen! Igényeinek megfelelően testreszabhatja a vízjel szövegét, betűtípusát, színét, méretét és egyéb tulajdonságait.
### Hol szerezhetek ideiglenes licencet a GroupDocs.Watermark számára?
 Ideiglenes jogosítványt szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).