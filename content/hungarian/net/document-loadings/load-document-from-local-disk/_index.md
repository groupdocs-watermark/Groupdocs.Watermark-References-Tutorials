---
title: Töltse be a dokumentumot a helyi lemezről
linktitle: Töltse be a dokumentumot a helyi lemezről
second_title: GroupDocs.Watermark .NET API
description: Védje és kezelje dokumentumait a Groupdocs Watermark for .NET segítségével. Kövesse részletes útmutatónkat a vízjelek zökkenőmentes hozzáadásához.
weight: 10
url: /hu/net/document-loadings/load-document-from-local-disk/
type: docs
---
# Töltse be a dokumentumot a helyi lemezről

## Bevezetés
vízjelekkel ellátott dokumentumok elengedhetetlenek a mai digitális korban a tartalomvédelem, a tulajdonjog érvényesítése és a titoktartás biztosítása érdekében. A Groupdocs.Watermark for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára vízjelek hozzáadását, keresését és kezelését különféle dokumentumformátumokban. Ebben az oktatóanyagban lépésről lépésre bemutatjuk a Groupdocs.Watermark for .NET használatának folyamatát, amellyel vízjeleket adhat a dokumentumokhoz.
## Előfeltételek
Mielőtt belemerülne a megvalósításba, győződjön meg arról, hogy rendelkezik a következőkkel:
1. Visual Studio telepítve: Visual Studio vagy más kompatibilis .NET IDE-re lesz szüksége.
2.  Groupdocs.Watermark for .NET: Töltse le a könyvtárat a[letöltési link](https://releases.groupdocs.com/Watermark/net/).
3. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer 4.6.1-es vagy újabb verziója.
4. Mintadokumentum: Készítsen mintadokumentumot a vízjelezési folyamat teszteléséhez.
## Névterek importálása
kezdéshez importálnia kell a szükséges névtereket a projektbe. Ezek elengedhetetlenek a vízjelezéshez szükséges osztályok és metódusok eléréséhez.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot a helyi lemezről
Először is be kell töltenie a dokumentumot a helyi lemezről. Ez a dokumentum lesz az, amelyhez vízjelet ad hozzá.
Határozza meg a vízjellel ellátni kívánt dokumentum elérési útját.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 2. lépés: Inicializálja a Betöltési beállításokat
 Ezután inicializálja a betöltési beállításokat. Például, ha Word-dokumentummal dolgozik, akkor használja`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3. lépés: Vízjel létrehozása és konfigurálása
 Most létrehoz egy példányt a`Watermarker` osztály. Ez a példány a vízjelek kezelésére és alkalmazására lesz használva a dokumentumban.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ez a blokk további lépéseket tartalmaz a vízjel hozzáadásához és mentéséhez
}
```
## 4. lépés: Hozzon létre egy vízjelet
Hozzon létre egy szöveges vízjelet. Ez a vízjel bármilyen kiválasztott szöveget tartalmazhat. Itt a "Teszt vízjelet" fogjuk használni.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## 5. lépés: Adjon hozzá vízjelet a dokumentumhoz
Adja hozzá a létrehozott vízjelet a dokumentumhoz a`Add` módszere a`Watermarker` osztály.
```csharp
watermarker.Add(watermark);
```
## 6. lépés: Mentse el a vízjellel ellátott dokumentumot
Végül mentse a vízjellel ellátott dokumentumot a megadott elérési útra.
```csharp
watermarker.Save(outputFileName);
```

## Következtetés
Vízjelek hozzáadása a dokumentumokhoz a Groupdocs Watermark for .NET segítségével egyszerű és hatékony. Ez az útmutató végigvezeti a teljes folyamaton a környezet beállításától a vízjeles dokumentum mentéséig. Ezzel a hatékony eszközzel biztosíthatja dokumentumai védelmét és szellemi tulajdonának biztonságát. 
 További részletekért tekintse meg a[dokumentáció](https://tutorials.groupdocs.com/Watermark/net/) , és ha bármilyen problémába ütközik, a[támogatói fórum](https://forum.groupdocs.com/c/watermark/19) kiváló hely a segítségnyújtásra. 
## GYIK
### Használhatok egyéni betűtípusokat vízjelekhez?
Igen, a Groupdocs támogatja az egyéni betűtípusokat. Megadhat bármilyen, a rendszerére telepített betűtípust.
### Milyen típusú dokumentumok támogatottak?
Groupdocs.Watermark a dokumentumformátumok széles skáláját támogatja, beleértve a Word, Excel, PDF, PowerPoint és egyebeket.
### Hogyan távolíthatok el vízjelet egy dokumentumból?
 Használhatja a`Remove` által biztosított módszer`Watermarker` osztályt a vízjelek eltávolításához.
### Lehetséges vízjeleket hozzáadni a képhez?
 Igen, a kép segítségével vízjeleket adhat hozzá`ImageWatermark` osztály.
### Ingyenesen kipróbálhatom a Groupdocs.Watermark szolgáltatást?
 Természetesen letöltheti a[ingyenes próbaverzió](https://releases.groupdocs.com/) hogy vásárlás előtt értékelje a könyvtárat.