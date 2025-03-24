---
title: Dokumentum előnézetének létrehozása
linktitle: Dokumentum előnézetének létrehozása
second_title: GroupDocs.Watermark .NET API
description: Ebből az útmutatóból megtudhatja, hogyan hozhat létre dokumentum-előnézeteket a GroupDocs.Watermark for .NET használatával. Fokozatmentesen fokozza dokumentumbiztonságát és kezelését.
weight: 10
url: /hu/net/document-manipulation/generate-document-preview/
---

# Dokumentum előnézetének létrehozása

## Bevezetés
A digitális dokumentumkezelés világában a vízjel döntő szerepet játszik a dokumentumok biztonságának és hitelességének biztosításában. A GroupDocs.Watermark for .NET egy hatékony eszköz, amellyel a fejlesztők könnyedén adhatnak vízjeleket a dokumentumokhoz. Ebben az oktatóanyagban végigvezetjük a dokumentum-előnézetek létrehozásának folyamatán a GroupDocs.Watermark for .NET használatával. Akár tapasztalt fejlesztő, akár csak most kezdi, ez az útmutató átfogó lépésről lépésre bemutatja a célját.
## Előfeltételek
Mielőtt belemerülnénk a megvalósításba, győződjünk meg arról, hogy mindennel rendelkezünk, ami az induláshoz szükséges:
- A C# és a .NET keretrendszer alapvető ismerete.
- A Visual Studio telepítve van a gépedre.
- GroupDocs.Watermark a .NET könyvtárhoz. tudsz[töltse le itt](https://releases.groupdocs.com/Watermark/net/).
-  A GroupDocs.Watermark érvényes licence. Akár megvásárolhatja[itt](https://purchase.groupdocs.com/buy) vagy megszerezni a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/) értékelési célokra.
## Névterek importálása
A GroupDocs.Watermark használatának megkezdéséhez a projektben importálnia kell a szükséges névtereket. Ezt úgy teheti meg, hogy a következő direktívák segítségével adja hozzá a kódot:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Ezek a névterek hozzáférést biztosítanak a vízjelezéshez és a dokumentum-előnézetek generálásához szükséges osztályokhoz és metódusokhoz.

Bontsuk le a dokumentum-előnézet létrehozásának folyamatát egyszerű, könnyen követhető lépésekre.
## 1. lépés: Állítsa be projektjét
Először is állítsa be .NET-projektjét a Visual Studióban. Ha még nincs projektje, hozzon létre egy újat az alábbi lépések végrehajtásával:
1. Nyissa meg a Visual Studio-t.
2. Kattintson az "Új projekt létrehozása" gombra.
3. Válassza a „Konzolalkalmazás (.NET Core)” lehetőséget, majd kattintson a „Tovább” gombra.
4. Nevezze el a projektet, és válassza ki a mentési helyet, majd kattintson a "Létrehozás" gombra.
## 2. lépés: Telepítse a GroupDocs.Watermark for .NET alkalmazást
A GroupDocs.Watermark használatához a projektben telepítenie kell a könyvtárat. Ezt a NuGet Package Manager segítségével teheti meg:
1. Kattintson a jobb gombbal a projektre a Solution Explorerben.
2. Válassza a "NuGet-csomagok kezelése" lehetőséget.
3. Keresse meg a "GroupDocs.Watermark" kifejezést a Tallózás lapon.
4. Kattintson a "Telepítés" gombra a könyvtár hozzáadásához a projekthez.
Alternatív megoldásként telepítheti a Package Manager konzolon keresztül:
```powershell
Install-Package GroupDocs.Watermark
```
## 3. lépés: Határozza meg a dokumentum elérési útját és kimeneti könyvtárát
Az előnézet létrehozása előtt meg kell adnia a megtekinteni kívánt dokumentum elérési útját és azt a könyvtárat, ahová az előnézeti képeket menteni kell:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Cserélje ki a "Dokumentum elérési útja" elemet a dokumentum elérési útjával, a "Dokumentumkönyvtár" helyett pedig azt a könyvtárat, ahová az előnézeti képeket menteni szeretné.
## 4. lépés: Inicializálja a vízjelobjektumot
Hozzon létre egy példányt a`Watermarker` osztályt úgy, hogy átadja a dokumentum elérési útját a konstruktorának. Ez az objektum az összes vízjelezési művelet végrehajtására lesz használva:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Itt a kódod
}
```
## 5. lépés: Hozzon létre delegált módszereket az adatfolyamkezeléshez
Az előnézet létrehozásához meg kell határoznia a delegálási módszereket a folyamok létrehozásához és kiadásához. Ezek a módszerek kezelik az adatfolyamok létrehozását és kiadását a dokumentum minden oldalához:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 A`createPageStreamDelegate` metódus létrehoz egy adatfolyamot a dokumentum minden oldalához, míg a`releasePageStreamDelegate` metódus bezárja az adatfolyamot az előnézet létrehozása után.
## 6. lépés: Konfigurálja az előnézeti beállításokat
 Ezután konfigurálja az előnézeti beállításokat a példány létrehozásával`PreviewOptions` osztály. Adja meg a delegálási módszereket, és állítsa az előnézeti formátumot PNG-re. Azt is megadhatja, hogy mely oldalak szerepeljenek az előnézetben:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
Ebben a példában a dokumentum első két oldalához készítünk előnézeteket.
## 7. lépés: A dokumentum előnézetének létrehozása
 Végül hívja a`GeneratePreview` módszer a`Watermarker`objektum, átadva a konfigurált`PreviewOptions`. Ez létrehozza az előnézeti képeket, és elmenti őket a megadott könyvtárba:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Következtetés
A dokumentum-előnézetek generálása a GroupDocs.Watermark for .NET használatával egyszerű folyamat, amely néhány sornyi kóddal végrehajtható. Az ebben az útmutatóban ismertetett lépések követésével könnyedén beállíthatja projektjét, konfigurálhatja a szükséges beállításokat, és előnézeteket hozhat létre a dokumentumokhoz. Ez a hatékony könyvtár nemcsak leegyszerűsíti a vízjelezési folyamatot, hanem robusztus funkciókat is kínál a vízjelek kezeléséhez és manipulálásához.
 Ha bármilyen kérdése van, vagy további segítségre van szüksége, ne habozzon felkeresni a[GroupDocs.Watermark támogatási fórum](https://forum.groupdocs.com/c/watermark/19) vagy hivatkozzon a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/).
## GYIK
### Milyen fájlformátumokat támogat a GroupDocs.Watermark for .NET?
 A GroupDocs.Watermark for .NET fájlformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX, XLSX és még sok más formátumot. A támogatott formátumok teljes listáját a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/).
### Testreszabhatom a vízjelek megjelenését?
Igen, a GroupDocs.Watermark lehetővé teszi a vízjelek megjelenésének teljes testreszabását, beleértve a szöveges, képi és alakzati vízjeleket. Beállíthatja az olyan tulajdonságokat, mint a betűtípus, szín, méret és átlátszóság.
### Létezik próbaverzió?
 Igen, megszerezheti a[ingyenes próbaverzió](https://releases.groupdocs.com/) a GroupDocs.Watermark for .NET-hez, hogy vásárlás előtt értékelje szolgáltatásait.
### Hogyan vásárolhatok licencet a GroupDocs.Watermark számára?
 Vásárolhat licencet a GroupDocs.Watermark számára[itt](https://purchase.groupdocs.com/buy). Különféle licencelési lehetőségek állnak rendelkezésre a különböző igényeknek megfelelően.
### Használhatom a GroupDocs.Watermarkot kereskedelmi projektekben?
 Igen, érvényes licenc birtokában használhatja a GroupDocs.Watermarkot kereskedelmi projektekben. Feltétlenül tekintse át a licencelési feltételeket a[vásárlási oldal](https://purchase.groupdocs.com/buy).