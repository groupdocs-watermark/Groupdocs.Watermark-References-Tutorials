---
title: Dokumentuminformációk lekérése a helyi lemezről
linktitle: Dokumentuminformációk lekérése a helyi lemezről
second_title: GroupDocs.Watermark .NET API
description: Ezzel az átfogó, lépésenkénti útmutatóval megtudhatja, hogyan adhat hozzá, távolíthat el és bonthat ki vízjeleket a .NET-hez készült GroupDocs segítségével.
weight: 11
url: /hu/net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Dokumentuminformációk lekérése a helyi lemezről

## Bevezetés
Üdvözöljük a GroupDocs.Watermark for .NET használatának végső útmutatójában! Akár tapasztalt fejlesztő, akár csak most kezdi, ez a cikk végigvezeti Önt a dokumentumok vízjellel való ellátásának alapvető részletein ezzel a hatékony eszközzel. A végére profi lesz a vízjelek dokumentumaiba való beágyazásában, biztosítva, hogy azok védettek legyenek, és az Ön specifikációinak megfelelő márkajelzéssel rendelkezzenek.
## Előfeltételek
Mielőtt belevágna a lépésről lépésre szóló útmutatóba, meg kell felelnie néhány előfeltételnek:
1.  .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszeren. A GroupDocs.Watermark for .NET kompatibilis a .NET-keretrendszer különböző verzióival, ezért ellenőrizze a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) a kompatibilitási részletekért.
2.  GroupDocs.Watermark for .NET Library: Töltse le és telepítse a legújabb verziót a[letöltési oldal](https://releases.groupdocs.com/Watermark/net/).
3. Fejlesztési környezet: Be kell állítania egy fejlesztői környezetet. A Visual Studio népszerű választás .NET-fejlesztéshez.
4. Alapvető C# ismeretek: A C# programozás alapjainak megértése segít a példák követésében.
## Névterek importálása
A GroupDocs.Watermark for .NET használata előtt importálnia kell a szükséges névtereket a projektbe. Ez egy egyszerű folyamat, és elengedhetetlen a könyvtár funkcióinak eléréséhez.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Bontsuk le a dokumentum vízjelezésének folyamatát világos, kezelhető lépésekre. Minden egyes lépést úgy terveztek, hogy segítsen megérteni és könnyen megvalósítani a funkcionalitást.
## 1. lépés: Töltse be a dokumentumot
 Az első lépés a vízjellel ellátni kívánt dokumentum betöltése. Ez a`Watermarker` osztály, amely lehetővé teszi a dokumentum elérését és kezelését.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // A dokumentum betöltődött, és készen áll a vízjelezésre
}
```
 Ebben a lépésben cserélje ki`"Your Document Path"` a dokumentum tényleges elérési útjával. Ez inicializálja a`Watermarker`objektumot, hozzáférést biztosítva különféle vízjel-funkciókhoz.
## 2. lépés: Dokumentuminformációk lekérése
Vízjel hozzáadása előtt érdemes összegyűjteni néhány információt a dokumentumról. Ez hasznos lehet a vízjel személyre szabásához a dokumentum tulajdonságai alapján.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Ebben a lépésben a`GetDocumentInfo` módszer olyan részleteket kér le, mint a fájltípus, az oldalak száma és a dokumentum mérete. Ezeket az információkat a rendszer kinyomtatja a konzolra, de szükség szerint felhasználhatja az alkalmazásban.
## 3. lépés: Szöveges vízjel hozzáadása
Most, hogy a dokumentumot betöltötte, és a hozzá tartozó információkat kéznél van, ideje hozzáadni egy vízjelet. Kezdjük egy egyszerű szöveges vízjellel.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Itt létrehoz egy`TextWatermark` objektumot a kívánt szöveggel, betűtípussal és stílussal. Igényeinek megfelelően állítsa be az olyan tulajdonságokat, mint a szín, az átlátszatlanság és az elforgatási szög. Végül a vízjelet hozzáadja a dokumentumhoz, és elmenti egy megadott elérési útra.
## 4. lépés: Kép vízjel hozzáadása
szöveges vízjelek nagyszerűek, de mi van, ha logót vagy másik képet szeretne hozzáadni? Ez a lépés a kép vízjelének hozzáadását ismerteti.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Cserélje ki`"Path to Your Image"` a vízjelkép elérési útjával. Állítsa be a tulajdonságokat, például az átlátszatlanságot és az elforgatási szöget a kép vízjelének testreszabásához. A vízjel hozzáadásának és mentésének folyamata hasonló a szöveges vízjelhez.
## 5. lépés: Távolítsa el a meglévő vízjeleket
 Néha előfordulhat, hogy el kell távolítania a meglévő vízjeleket egy dokumentumból. Ezt a`Remove` által biztosított módszer`Watermarker` osztály.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Itt, a`Remove` módszer a szöveges vízjelek eltávolítására szolgál a dokumentumból. Igényeitől függően különböző típusú vízjeleket határozhat meg, amelyeket eltávolítani szeretne, például képet vagy szöveget. A módosítások megtekintéséhez mentse a dokumentumot egy új elérési útra.
## 6. lépés: Vízjelek kibontása
Ha vízjeleket kell kivonnia és ellenőriznie kell egy dokumentumból, a GroupDocs.Watermark for .NET ezt könnyedén lehetővé teszi.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // További tulajdonságok és logika minden vízjelhez
    }
}
```
 Ez a lépés magában foglalja a`GetWatermarks`módszer a dokumentumban lévő összes vízjel lekéréséhez. Ezután ismételheti a vízjelek listáját, és ellenőrizheti a tulajdonságaikat, vagy szükség szerint további műveleteket hajthat végre.
## Következtetés
 Gratulálunk! Most már megtanulta, hogyan használhatja a GroupDocs.Watermark for .NET szolgáltatást vízjelek hozzáadására, eltávolítására és kivonására a dokumentumokból. Ezekkel a készségekkel hatékonyan védheti meg és védheti meg dokumentumait. Ne feledje, a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) mindig ott van, ha részletesebb információra vagy speciális funkciókra van szüksége.
## GYIK
### Használhatom a GroupDocs.Watermark for .NET-et bármely .NET-verzióval?
 Igen, a GroupDocs.Watermark for .NET kompatibilis a .NET-keretrendszer különféle verzióival. Ellenőrizd a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) konkrétumokhoz.
### Honnan tölthetem le a GroupDocs.Watermark for .NET programot?
 A legújabb verziót letöltheti a[letöltési oldal](https://releases.groupdocs.com/Watermark/net/).
### Hogyan szerezhetek ideiglenes engedélyt?
 Ideiglenes engedélyt szerezhet a[ideiglenes licenc oldal](https://purchase.groupdocs.com/temporary-license/).
### Van ingyenes próbaverzió?
 Igen, ingyenes próbaverziót indíthat, ha felkeresi a[ingyenes próbaoldal](https://releases.groupdocs.com/).
### Hol kaphatok támogatást, ha problémákba ütközöm?
 A támogatás elérhető a[GroupDocs Watermark fórum](https://forum.groupdocs.com/c/watermark/19).