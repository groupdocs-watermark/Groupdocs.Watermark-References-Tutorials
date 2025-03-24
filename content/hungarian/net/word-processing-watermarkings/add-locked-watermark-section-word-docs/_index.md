---
title: Zárolt vízjel hozzáadása a Word Dokumentumok szakaszához
linktitle: Zárolt vízjel hozzáadása a Word Dokumentumok szakaszához
second_title: GroupDocs.Watermark .NET API
description: Ebből az átfogó, lépésenkénti útmutatóból megtudhatja, hogyan adhat hozzá zárolt vízjelet egy adott szakaszhoz a Word dokumentumokban a Groupdocs segítségével.
weight: 13
url: /hu/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---
## Bevezetés
Hatékony módot keres arra, hogy zárolt vízjelet adjon a Word-dokumentumok egy szakaszához? Ne keressen tovább! A Groupdocs.Watermark for .NET segítségével zökkenőmentesen illesztheti be a vízjeleket a Word dokumentumokba, miközben biztosíthatja, hogy azok zárolva és hamisításmentesek maradjanak. Ez a hatékony eszköz számos funkciót kínál a vízjelezési igényeinek kielégítésére, legyen szó márkaépítésről, bizalmas kezelésről vagy biztonsági okokból. Ebben a lépésenkénti oktatóanyagban végigvezetjük, hogyan adhat hozzá zárolt vízjelet egy Word-dokumentum adott szakaszához a Groupdocs.Watermark for .NET segítségével. Merüljünk el!
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:
1.  Groupdocs.Watermark for .NET: Győződjön meg arról, hogy telepítve van a Groupdocs.Watermark könyvtár. Letöltheti[itt](https://releases.groupdocs.com/Watermark/net/).
2. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer be van állítva a fejlesztői környezetben.
3. IDE: Használjon integrált fejlesztői környezetet (IDE), például a Visual Studio-t.
4. Dokumentum: Word dokumentum (.docx) a vízjel alkalmazásához.
## Névterek importálása
A kezdéshez importálnia kell a szükséges névtereket a projektbe. Íme, hogyan kell csinálni:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot
 Először is be kell töltenie azt a dokumentumot, amelyhez vízjelet szeretne adni. Ebben a lépésben meg kell adni a dokumentum elérési útját, és a következővel betölteni`Watermarker` osztály.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // A vízjel kódja ide fog kerülni.
}
```
## 2. lépés: Hozza létre a vízjelet
Ezután hozza létre a dokumentumhoz hozzáadni kívánt vízjelet. Ebben a példában szöveges vízjelet fogunk létrehozni meghatározott betűtípus-beállításokkal és színekkel.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 3. lépés: Konfigurálja a vízjel beállításait
Most konfigurálja a vízjel beállításait a szakaszindex és a zárolási beállítások megadásához. Ez biztosítja, hogy a vízjel a megfelelő szakaszhoz kerüljön, és zárolva legyen.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // Hozzáadás az első részhez
options.IsLocked = true; // Zárja le a vízjelet
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // Zár típusa
```
## 4. lépés: Adja hozzá a vízjelet a dokumentumhoz
 A vízjel és a beállítások konfigurálásával itt az ideje hozzáadni a vízjelet a dokumentumhoz a`Add` módszere a`Watermarker` osztály.
```csharp
watermarker.Add(watermark, options);
```
## 5. lépés: Mentse el a módosított dokumentumot
Végül mentse a hozzáadott vízjellel ellátott dokumentumot a kívánt kimeneti helyre.
```csharp
watermarker.Save(outputFileName);
```
## Következtetés
Zárolt vízjel hozzáadása egy Word-dokumentum adott szakaszához a Groupdocs segítségével egyszerű folyamat. Az alábbi lépések követésével fokozhatja dokumentumai biztonságát és integritását, biztosítva a fontos információk védelmét. Legyen szó érzékeny adatok védelméről vagy dokumentumainak professzionális megjelenéséről, a Groupdocs.Watermark for .NET biztosítja a céljai hatékony eléréséhez szükséges eszközöket.
## GYIK
### Mi az a Groupdocs.Watermark for .NET?
Groupdocs.Watermark for .NET egy hatékony könyvtár, amely fejlett testreszabási és biztonsági funkciókkal lehetővé teszi a fejlesztők számára, hogy vízjeleket adjanak különféle dokumentumtípusokhoz, köztük Word-hez, PDF-hez és képekhez.
### Zárolhatok egy vízjelet jelszóval?
 Igen, jelszóval védheti a vízjelet a`options.Password` ingatlan a`WordProcessingWatermarkSectionOptions` osztály.
### Lehetséges-e különböző vízjeleket alkalmazni a dokumentum különböző szakaszaira?
 Teljesen! Más beállítással`SectionIndex` értékek a`WordProcessingWatermarkSectionOptions`, egyedi vízjeleket alkalmazhat a dokumentum különböző részein.
### Milyen típusú vízjeleket adhatok hozzá a Groupdocs.Watermark segítségével?
A Groupdocs.Watermark különféle típusú vízjeleket támogat, beleértve a szöveges, képi és alakzatos vízjeleket, és széles körű testreszabási lehetőségeket kínál minden típushoz.
### Hol találhatok további információt a Groupdocs.Watermark for .NET-ről?
 További információért látogassa meg a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) és[támogatói fórum](https://forum.groupdocs.com/c/watermark/19).