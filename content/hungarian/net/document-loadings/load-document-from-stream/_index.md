---
title: Dokumentum betöltése a Streamből
linktitle: Dokumentum betöltése a Streamből
second_title: GroupDocs.Watermark .NET API
description: Ebből az útmutatóból megtudhatja, hogyan adhat vízjeleket dokumentumokhoz a GroupDocs.Watermark for .NET segítségével. Tökéletes azoknak a fejlesztőknek, akik javítani szeretnék a dokumentumbiztonságot.
weight: 11
url: /hu/net/document-loadings/load-document-from-stream/
---
## Bevezetés
Zökkenőmentesen szeretne vízjeleket hozzáadni dokumentumaihoz a .NET használatával? Ne keressen tovább! A GroupDocs.Watermark for .NET egy hatékony és könnyen használható könyvtár, amely lehetővé teszi a vízjelek kezelését különféle dokumentumformátumokban. Függetlenül attól, hogy PDF-ekkel, Word-dokumentumokkal vagy képekkel dolgozik, ez az eszköz mindent megtalál. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a dokumentum adatfolyamból való betöltésének és vízjel hozzáadásának folyamatán. Szóval, ugorjunk bele!
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy beállította a következőket:
1. Visual Studio: A Visual Studio bármely legújabb verziója jól működik.
2. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer 4.0-s vagy újabb verziója.
3.  GroupDocs.Watermark for .NET: Letöltheti innen[itt](https://releases.groupdocs.com/Watermark/net/).
4. Alapvető C# ismerete: Hasznos lesz a C# és az objektumorientált programozási koncepciók ismerete.

## Névterek importálása
GroupDocs.Watermark projektben való használatához importálnia kell a szükséges névtereket. Ezzel minden probléma nélkül hozzáférhet a könyvtár funkcióihoz.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1. lépés: A projekt beállítása
Először is be kell állítania a projektet a Visual Studióban. Íme, hogyan kell csinálni:
1. Új projekt létrehozása: Nyissa meg a Visual Studio-t, és hozzon létre egy új C# konzolalkalmazás-projektet.
2.  A GroupDocs.Watermark telepítése: Telepítse a GroupDocs.Watermark könyvtárat a NuGet Package Manager segítségével. Egyszerűen keressen`GroupDocs.Watermark` és telepítse.
## 2. lépés: Határozza meg a dokumentum elérési útját
Ezután meg kell határoznia a dokumentum elérési útját és azt a kimeneti fájlt, amelybe a vízjellel ellátott dokumentum mentésre kerül.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Cserélje ki`"Your Document Path"` a vízjellel ellátni kívánt dokumentum tényleges elérési útjával és`"Your Document Directory"` azzal a könyvtárral, ahová menteni szeretné a vízjellel ellátott dokumentumot.
## 3. lépés: Töltse be a dokumentumot egy adatfolyamból
Most töltsük be a dokumentumot egy adatfolyamból. Ez magában foglalja a dokumentum folyamként történő megnyitását, majd a`Watermarker` osztályt a GroupDocs.Watermark könyvtárból kezelni.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // A vízjelek kezeléséhez szükséges kód ide kerül
}
```
 Ez a kódrészlet biztosítja, hogy a dokumentum adatfolyamként nyíljon meg, és a`Watermarker` osztály ezzel az adatfolyammal van inicializálva. A`using` A nyilatkozatok biztosítják az erőforrások megfelelő ártalmatlanítását használat után.
## 4. lépés: Hozzon létre és adjon hozzá egy vízjelet
Vízjel létrehozása egyszerű a GroupDocs.Watermark segítségével. Ebben a példában egy egyszerű szöveges vízjelet fogunk létrehozni.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Itt létrehozunk a`TextWatermark` objektumot a „Vízjel tesztelése” szöveggel, és adja meg a betűtípus részleteit. Ezután adjuk hozzá ezt a vízjelet a dokumentumhoz a`Add` módszere a`Watermarker` osztály.
## 5. lépés: Mentse el a vízjellel ellátott dokumentumot
Végül mentse a vízjellel ellátott dokumentumot a megadott kimeneti útvonalra.
```csharp
watermarker.Save(outputFileName);
```
 Ez a kód elmenti a dokumentumot az újonnan hozzáadott vízjellel`outputFileName` korábban meghatározott útvonalat.

## Következtetés
Gratulálunk! Sikeresen hozzáadott egy vízjelet a dokumentumhoz a GroupDocs.Watermark for .NET segítségével. Ez a könyvtár hihetetlenül egyszerűvé teszi a vízjelek kezelését különféle dokumentumformátumokban. Függetlenül attól, hogy szöveget, képeket vagy más típusú vízjeleket kell hozzáadnia, a GroupDocs.Watermark rendelkezik a szükséges eszközökkel. Ne felejtsd el megnézni a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) fejlettebb funkciókért és testreszabási lehetőségekért.
## GYIK
### Milyen típusú vízjeleket adhatok hozzá a GroupDocs.Watermark for .NET használatával?
Hozzáadhat szöveges vízjeleket, képi vízjeleket, sőt összetett alakzatokat és logókat is. A könyvtár a testreszabási lehetőségek széles skáláját támogatja.
### Eltávolíthatom a vízjeleket a dokumentumokból a GroupDocs.Watermark segítségével?
Igen, a GroupDocs.Watermark lehetővé teszi a meglévő vízjelek eltávolítását a dokumentumokból is.
### Van ingyenes próbaverzió a GroupDocs.Watermark számára?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Hogyan vásárolhatok licencet a GroupDocs.Watermark számára?
Licenc vásárolható közvetlenül a[GroupDocs webhely](https://purchase.groupdocs.com/buy).
### Hol kaphatok támogatást, ha problémákba ütközöm?
 Támogatásért látogassa meg a[GroupDocs.Watermark támogatási fórum](https://forum.groupdocs.com/c/watermark/19).