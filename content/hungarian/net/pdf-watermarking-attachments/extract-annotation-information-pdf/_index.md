---
title: Kivonat a megjegyzésekkel kapcsolatos információk PDF-ből
linktitle: Kivonat a megjegyzésekkel kapcsolatos információk PDF-ből
second_title: GroupDocs.Watermark .NET API
description: Ebből a részletes, lépésenkénti útmutatóból megtudhatja, hogyan bonthat ki megjegyzésadatokat PDF-dokumentumokból a GroupDocs.Watermark for .NET segítségével.
type: docs
weight: 23
url: /hu/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## Bevezetés
Gyakran előfordul, hogy részletes megjegyzésinformációkat kell kivonnia PDF-dokumentumaiból? Akár dokumentumkezelő rendszerekkel foglalkozó fejlesztő, akár számos PDF-et kezelő üzleti szakember, a megjegyzések hatékony kibontása és feldolgozása döntő fontosságú lehet. A GroupDocs.Watermark for .NET segítségével egy hatékony eszköztár áll rendelkezésére, amely egyszerűvé és hatékonyvá teszi ezt a feladatot.
## Előfeltételek
Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy mindennel rendelkezünk, ami az induláshoz szükséges:
1. Visual Studio: Győződjön meg arról, hogy telepítve van a Visual Studio. Ez lesz a mi IDE-nk a kód írásához és futtatásához.
2.  GroupDocs.Watermark for .NET: rendelkeznie kell a GroupDocs.Watermark for .NET könyvtárral. tudsz[töltse le itt](https://releases.groupdocs.com/Watermark/net/).
3. Alapvető C# ismerete: A C# programozás ismerete szükséges a példák követéséhez.
## Névterek importálása
Először is importálnia kell a szükséges névtereket a projektbe. Ezek a névterek tartalmazzák azokat az osztályokat és metódusokat, amelyek a PDF-fájlok kezeléséhez és a megjegyzések kibontásához szükségesek.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 1. lépés: Állítsa be projektjét
Először is állítsuk be projektünket a Visual Studio-ban. Hozzon létre egy új konzolalkalmazás (.NET Core) projektet. A projekt létrehozása után hozzá kell adni egy hivatkozást a GroupDocs.Watermark for .NET könyvtárhoz.
1. Nyissa meg a NuGet csomagkezelőt.
2.  Keressen rá`GroupDocs.Watermark`.
3.  Telepítse a`GroupDocs.Watermark` csomag.
## 2. lépés: Határozza meg a dokumentum elérési útját
Ezután meg kell adnia a bemeneti PDF-dokumentum elérési útját és azt a kimeneti könyvtárat, ahová a kivonatolt információkat menti. Ez biztosítja, hogy az alkalmazás tudja, hol találja a PDF-fájlt, és hol tárolja az eredményeket.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 3. lépés: Töltse be a PDF-dokumentumot
 A PDF-dokumentum használatához be kell töltenünk a segítségével`PdfLoadOptions`. Ez az osztály lehetőséget biztosít a betöltési folyamat konfigurálására.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ide kerül a megjegyzések kinyeréséhez szükséges kód
}
```
## 4. lépés: Nyissa meg a PDF tartalmat
dokumentum betöltése után hozzáférhetünk a tartalmához. Pontosabban, a PDF-tartalmat szeretnénk megszerezni, hogy az oldalakat és a megjegyzéseket ismételgethessük.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 5. lépés: Ismétlés oldalakon és megjegyzéseken keresztül
A kézben lévő PDF-tartalommal végiglapozhatjuk az egyes oldalakat, majd az egyes oldalakon található megjegyzéseket. Ez lehetővé teszi a szükséges információk kinyerését.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Kivonat a kommentár részleteiről itt
    }
}
```
## 6. lépés: Vegye ki a megjegyzés részleteit
A beágyazott hurkokon belül az egyes megjegyzésekről különféle részleteket gyűjtünk ki. Ez magában foglalja a megjegyzés típusát, a kapcsolódó képeket, szöveget és a helyzetadatokat.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## 7. lépés: Mentse vagy dolgozza fel a kivont adatokat
Végül döntse el, mit szeretne kezdeni a kivont annotációs információval. Igényei szerint kinyomtathatja a konzolra, mentheti fájlba, vagy akár adatbázisban is tárolhatja.
```csharp
// Példa a kivont adatok fájlba mentésére
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Következtetés
kommentárinformációk kinyerése PDF-dokumentumokból a GroupDocs.Watermark for .NET segítségével egyszerű folyamat, amellyel sok időt és erőfeszítést takaríthat meg. Az ebben az útmutatóban ismertetett lépések követésével könnyedén integrálhatja ezt a funkciót projektjeibe, és automatizálhatja az értékes annotációs adatok kinyerését.
 Függetlenül attól, hogy nagy mennyiségű PDF-et kezel, vagy egyszerűen csak bizonyos információkat kell kivonnia, a GroupDocs.Watermark for .NET megbízható és hatékony megoldást kínál. Ne felejtsd el megnézni a[dokumentáció](https://reference.groupdocs.com/Watermark/net/) fejlettebb funkciókért és testreszabási lehetőségekért.
## GYIK
### Mi az a GroupDocs.Watermark for .NET?
A GroupDocs.Watermark for .NET egy átfogó könyvtár, amely lehetővé teszi a fejlesztők számára vízjelek hozzáadását, keresését és eltávolítását különféle dokumentumformátumokból, beleértve a PDF-eket, Word-dokumentumokat és képeket.
### Ingyenesen kipróbálhatom a GroupDocs.Watermark alkalmazást?
 Igen, kaphat a[ingyenes próbaverzió](https://releases.groupdocs.com/) hogy vásárlás előtt tesztelje a könyvtár funkcióit.
### Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat a GroupDocs csapatától, ha ellátogat hozzájuk[támogatói fórum](https://forum.groupdocs.com/c/watermark/19).
### Kapható-e ideiglenes engedély a teszteléshez?
 Igen, kérheti a[ideiglenes engedély](https://purchase.groupdocs.com/temporary-license/)tesztelési célokra.
### Hol tudom megvásárolni a GroupDocs.Watermark .NET teljes verzióját?
 A teljes verziót megvásárolhatja a[GroupDocs webhely](https://purchase.groupdocs.com/buy).