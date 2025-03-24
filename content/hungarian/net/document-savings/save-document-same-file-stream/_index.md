---
title: Mentse a dokumentumot ugyanabba a fájlba vagy adatfolyamba
linktitle: Mentse a dokumentumot ugyanabba a fájlba vagy adatfolyamba
second_title: GroupDocs.Watermark .NET API
description: Ismerje meg, hogyan adhat vízjeleket dokumentumokhoz a Groupdocs.Watermark for .NET segítségével. Ez az útmutató utasításokat ad a dokumentumok védelmére és integritására.
weight: 10
url: /hu/net/document-savings/save-document-same-file-stream/
---

# Mentse a dokumentumot ugyanabba a fájlba vagy adatfolyamba

## Bevezetés
Napjaink digitális korában a vízjelek hozzáadása a dokumentumokhoz elengedhetetlenné vált a szellemi tulajdon védelme és a márka integritásának biztosítása érdekében. A Groupdocs.Watermark for .NET robusztus megoldást kínál azoknak a fejlesztőknek, akik zökkenőmentesen szeretnék vízjeleket beágyazni a dokumentumokba. Ez az átfogó útmutató végigvezeti Önt egy vízjellel ellátott dokumentum ugyanabba a fájlba vagy adatfolyamba mentésének lépésein a Groupdocs.Watermark for .NET segítségével.
## Előfeltételek
Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1. Fejlesztési környezet: A Visual Studio telepítve van a gépre.
2. .NET-keretrendszer: Győződjön meg arról, hogy rendelkezik a .NET-keretrendszer 4.0-s vagy újabb verziójával.
3.  Groupdocs.Watermark for .NET: Töltse le és telepítse a legújabb verziót a[webhely](https://releases.groupdocs.com/Watermark/net/).
4.  Licenc: Szerezzen ideiglenes vagy állandó engedélyt a következőtől[itt](https://purchase.groupdocs.com/temporary-license/).
## Névterek importálása
Groupdocs.Watermark használatának megkezdéséhez a .NET-projektben importálnia kell a szükséges névtereket:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1. lépés: Állítsa be projektjét
Mielőtt vízjeleket adnánk a dokumentumainkhoz, be kell állítanunk a .NET projektünket. Itt van, hogyan:
1. Új projekt létrehozása: Nyissa meg a Visual Studio-t, és hozzon létre egy új konzolalkalmazást.
2. Groupdocs.Watermark Reference hozzáadása: Kattintson jobb gombbal a projektre a Solution Explorerben, válassza a "NuGet-csomagok kezelése" lehetőséget, és telepítse a Groupdocs.Watermark csomagot.
## 2. lépés: Másolja át a dokumentumot egy új helyre
Az eredeti dokumentum közvetlen megváltoztatásának elkerülése érdekében célszerű először egy új helyre másolni. Íme, hogyan kell csinálni:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## 3. lépés: Inicializálja a vízjelet
Most, hogy a dokumentumunkat átmásoltuk, inicializálhatjuk a Watermarker osztályt a vízjel hozzáadásához:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // A vízjel ide tartozik
}
```
## 4. lépés: Szöveges vízjel létrehozása és hozzáadása
Ezután létrehozunk egy szöveges vízjelet, és hozzáadjuk a dokumentumunkhoz:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## 5. lépés: Mentse el a dokumentumot
Végül mentse el a dokumentumot vízjellel:
```csharp
watermarker.Save();
```
## Következtetés
Vízjelek hozzáadása a dokumentumokhoz a Groupdocs Watermark for .NET segítségével egyszerű és hatékony. A fent vázolt lépések követésével könnyedén megvédheti dokumentumait és megőrizheti azok sértetlenségét. További részletekért tekintse meg a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/).
## GYIK
### Használhatok képet vízjelként szöveg helyett?
Igen, a Groupdocs.Watermark lehetővé teszi képek, alakzatok és szövegek vízjelként való használatát.
### Hogyan távolíthatok el vízjelet a dokumentumból?
 A vízjel eltávolításához nyissa meg a vízjelgyűjteményt a dokumentumban, és használja a`Remove` módszer.
### Testreszabható a vízjel megjelenése?
Teljesen. Testreszabhatja a vízjel betűtípusát, méretét, színét és helyzetét.
### Alkalmazhatok több vízjelet egyetlen dokumentumra?
 Igen, több vízjelet is hozzáadhat a`Add` módszert többször különböző vízjel objektumokkal.
### A Groupdocs.Watermark kompatibilis az összes dokumentumformátummal?
Groupdocs.Watermark a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX és sok más formátumot.