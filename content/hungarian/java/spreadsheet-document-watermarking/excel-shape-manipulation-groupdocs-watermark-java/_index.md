---
date: '2026-06-01'
description: Ismerje meg, hogyan távolíthatja el a formákat az Excel fájlokból a GroupDocs.Watermark
  Java verziójával. Tartalmazza a lépéseket az Excel betöltéséhez, a munkalapok bejárásához
  és a formázott formák törléséhez.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Hogyan távolítsuk el a formákat az Excelből a GroupDocs.Watermark Java használatával
type: docs
url: /hu/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Hogyan távolítsuk el az alakzatokat az Excelből a GroupDocs.Watermark Java használatával

Excel táblázatok a vállalati jelentéskészítés alapkövei, de a nem kívánt alakzatok – különösen a elavult vagy nem szabványos szövegformázásúak – rendetlenséget okozhatnak a fájlban és megtörhetik a vizuális konzisztenciát. **Az alakzatok eltávolítása az Excelből** gyorsan elengedhetetlenné válik a tiszta, professzionális dokumentumokhoz. Ebben az útmutatóban végigvezetjük a Excel munkafüzet betöltését, a munkalapok bejárását, és a specifikus formázási kritériumoknak megfelelő alakzatok programozott törlését a hatékony GroupDocs.Watermark Java könyvtárral.

## Gyors válaszok
- **Törölhet-e a GroupDocs.Watermark alakzatokat?** Igen, egy `removeShape` metódust biztosít, amely bármely munkalapon működik.  
- **Szükségem van licencre ehhez a funkcióhoz?** A próbaverzió értékelésre használható; a teljes licenc szükséges a termeléshez.  
- **Melyik Java verzió szükséges?** A Java 8 vagy újabb támogatott.  
- **Hány fájlformátumot támogat a GroupDocs.Watermark?** Több mint 30 bemeneti és kimeneti formátum, többek között XLSX, DOCX, PDF és PPTX.  
- **Aggódom a memóriahasználat miatt nagy munkafüzetek esetén?** Használjon try‑with‑resources-t, és kerülje el a teljes lapok memóriába töltését; az API hatékonyan streameli az adatokat.

## Mi az alakzatok eltávolítása az Excelből?
*Az alakzatok eltávolítása az Excelből* azt jelenti, hogy programozottan töröljük a rajzobjektumokat – például szövegdobozokat, ikonokat vagy SmartArt elemeket –, amelyek bizonyos kritériumoknak megfelelnek, mint a betűstílus, szín vagy méret. Ez a művelet megtisztítja a munkafüzetet a kézi szerkesztés nélkül, biztosítja a vizuális konzisztenciát, csökkenti a fájlméretet, és megakadályozza, hogy elavult vagy nem kívánt grafikák jelenjenek meg a terjesztett jelentésekben.

## Miért távolítsuk el az alakzatokat az Excelből?
A GroupDocs.Watermark képes **több száz oldalas munkafüzeteket akár 3 × gyorsabb sebességgel** feldolgozni, mint a kézi szerkesztés, **30+ fájlformátumot** kezelve, miközben a memóriahasználatot 150 MB alatt tartja 50 MB-nál nagyobb fájlok esetén. Az alakzatok eltávolításának automatizálása kiküszöböli az emberi hibákat, és biztosítja a következetes márkajelzést minden generált jelentésben.

## Előkövetelmények
### Szükséges könyvtárak, verziók és függőségek
- **Java Development Kit (JDK)**: 8-as vagy újabb verzió.  
- **GroupDocs.Watermark**: 24.11-es verzió (az írás időpontjában legújabb stabil kiadás).

### Környezet beállítási követelmények
Használjon olyan IDE-t, mint az IntelliJ IDEA vagy az Eclipse, valamint Maven-t a függőségkezeléshez.

### Tudás előkövetelmények
A Java szintaxis és az alapvető Excel koncepciók (munkalapok, cellák és alakzatok) ismerete segíti a példák követését.

## A GroupDocs.Watermark Java beállítása
### Maven függőség
Adja hozzá a következőt a `pom.xml`-hez:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```  

### Közvetlen letöltés
Alternatívaként töltse le a legújabb verziót a [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) oldalról.

### Licenc beszerzési lépések
- **Free Trial** – Kezdje egy ingyenes próbaverzióval a funkciók kiértékeléséhez.  
- **Temporary License** – Szerezzen be egy ideiglenes licencet a kiterjesztett teszteléshez.  
- **Purchase** – Vásároljon teljes licencet a termelési használathoz.

### Alapvető inicializálás és beállítás
Miután a könyvtárat hozzáadta a projekthez, inicializálja az alábbiak szerint:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Hogyan távolítsuk el az alakzatokat az Excelből?
Töltse be a munkafüzetet, járja be minden munkalapot, és hívja meg az alakzat-eltávolító API-t. Ez a kétlépéses minta – *load* majd *iterate* – gyakorlatilag minden olyan helyzetet lefed, ahol egy teljes fájlban kell az alakzatokat megtisztítani. Az egyes alakzatok tulajdonságainak a kritériumokkal való összevetésével eltávolítás előtt biztosítható, hogy csak a nem kívánt elemek kerülnek törlésre, miközben a dokumentum többi része, elrendezése és tartalma megmarad.

## Excel dokumentum betöltése
**Áttekintés**  
Az Excel dokumentum betöltése a kiindulópont minden manipulációs feladathoz. A GroupDocs.Watermark ezt egyszerűsíti intuitív API-jával.  

**Definíció horgony**  
`SpreadsheetDocument` a GroupDocs.Watermark fő osztálya, amely egy Excel munkafüzetet reprezentál a memóriában, és módszereket biztosít a munkalapok, cellák és alakzatok eléréséhez.  

#### Kódrészlet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Munkalapok elérése és bejárása egy táblázatban
**Áttekintés**  
A munkalapok bejárása lehetővé teszi, hogy egyes lapokon külön-külön műveleteket hajtson végre.  

**Definíció horgony**  
`Worksheet` egyetlen lapot képvisel egy `SpreadsheetDocument`-ben; ezen az objektumon keresztül olvashatja, módosíthatja vagy törölheti a tartalmát.  

#### Kódrészlet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Alakzatok eltávolítása meghatározott szövegformázással egy táblázatból
**Áttekintés**  
Ez a funkció azokra az alakzatokra céloz, amelyek bizonyos szövegformázási kritériumoknak megfelelnek, például betűtípus vagy szín.  

**Definíció horgony**  
`Shape` az objektummodell minden rajzelemhez (szövegdoboz, kép vagy SmartArt) egy munkalapon belül; olyan tulajdonságokat tesz elérhetővé, mint a `getText`, `getFont` és a `remove`.  

#### Kódrészlet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Gyakorlati alkalmazások
### Valós példák
1. **Data Validation** – Automatikusan törölje az alakzatokat, amelyek elavult értesítéseket tartalmaznak.  
2. **Template Standardization** – Érvényesítse a vállalati arculatot a nem szabványos szövegdobozok eltávolításával.  
3. **Automated Reporting** – Tisztítsa meg a generált jelentéseket a terjesztés előtt, garantálva a kifinomult megjelenést.

### Integrációs lehetőségek
A GroupDocs.Watermark beágyazható Java‑alapú vállalati folyamatokba, például dokumentum‑generáló mikroszolgáltatásokba, kötegelt feldolgozó feladatokba vagy tartalom‑kezelő rendszerekbe, zökkenőmentes, licenc‑megfelelő módot biztosítva az Excel eszközök kezelésére.

## Teljesítmény szempontok
### Teljesítmény optimalizálása
- **Kerülje a nehéz műveleteket a ciklusokon belül** – szerezze be az alakzatgyűjteményeket egyszer a munkalapon.  
- **Erőforrások gyors felszabadítása** – használjon try‑with‑resources-t a stream-ek automatikus lezárásához.

### Erőforrás használati irányelvek
A `SpreadsheetDocument` objektumot szabadítsa fel amint a feldolgozás befejeződött, hogy natív memóriát szabadítson fel. 100 MB-nál nagyobb fájlok esetén fontolja meg a munkalapok párhuzamos stream‑ekkel történő feldolgozását a többmagos CPU-k kihasználásához.

### Legjobb gyakorlatok a Java memória kezeléshez
Használja a `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` szerkezetet, hogy a `close()` metódus akkor is lefusson, ha kivétel keletkezik.

## Gyakori problémák és megoldások
- **Alakzat nem található** – Győződjön meg róla, hogy a megfelelő munkalap indexet ellenőrzi; az alakzatok laponként vannak definiálva.  
- **Licenc kivétel** – A próbaverzió licenc letiltja a kötegelt feldolgozást; frissítsen teljes licencre a korlátlan műveletekhez.  
- **Váratlan betűtípus értékek** – A betűtípus tulajdonságok öröklődhetnek; használja a `shape.getEffectiveFont()` metódust a feloldott stílus lekéréséhez.

## Gyakran ismételt kérdések

**Q: Eltávolíthatok alakzatokat egy jelszóval védett munkafüzetből?**  
A: Igen. Töltse be a dokumentumot a jelszó paraméterrel, majd futtassa ugyanazt az eltávolító logikát; az API a memóriában dekódolja a fájlt.

**Q: Támogatja a könyvtár a .xls (Excel 97‑2003) fájlokat?**  
A: Teljes mértékben. A GroupDocs.Watermark kezeli a `.xlsx` és a régi `.xls` formátumokat konverzió nélkül.

**Q: Hogyan naplózhatom, hogy melyik alakzatot törölték?**  
A: Járja be az alakzatgyűjteményt, ellenőrizze a formázási kritériumokat, naplózza a `shape.getName()` vagy `shape.getId()` értékét, majd hívja meg a `remove()` metódust.

**Q: Lehet vízjelet hozzáadni az alakzatok eltávolítása után?**  
A: Igen. A tisztítás után hívja meg a `doc.addWatermark(new TextWatermark("Confidential"))` metódust, hogy szöveges vízjelet helyezzen el az összes munkalapon.

**Q: Mi a maximálisan támogatott fájlméret?**  
A: A könyvtár akár **2 GB**-ig képes feldolgozni fájlokat 64‑bit JVM-en, csak a rendelkezésre álló heap memória és az operációs rendszer korlátai korlátozzák.

## Következtetés
Ebben az útmutatóban bemutattuk a teljes, termelésre kész megközelítést a **remove shapes from excel** munkafüzetekhez a GroupDocs.Watermark Java használatával. A dokumentum betöltésével, a munkalapok bejárásával és a pontos formázási szűrők alkalmazásával automatizálhatja a takarítási feladatokat, érvényesítheti a márkajelzést, és skálázhatóan javíthatja a jelentések minőségét. Fedezze fel a további funkciókat, például a vízjel beszúrását, dokumentumkonverziót és kötegelt feldolgozást, hogy tovább bővítse a dokumentum‑automatizálási eszköztárát.

---

**Utoljára frissítve:** 2026-06-01  
**Tesztelve a következővel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs

## Kapcsolódó útmutatók

- [Excel alakzatkezelés a GroupDocs.Watermark Java használatával: Átfogó útmutató](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Képi vízjel hozzáadása Excel táblázathoz a GroupDocs.Watermark Java SDK használatával](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Excel dokumentumkezelés és vízjelezés a GroupDocs.Watermark Java használatával](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)