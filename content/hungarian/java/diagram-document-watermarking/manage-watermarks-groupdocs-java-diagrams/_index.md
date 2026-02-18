---
date: '2026-02-18'
description: Tudja meg, hogyan adhat hozzá vízjelet és hogyan távolíthatja el a vízjelet
  .vsdx diagramfájlokban a GroupDocs.Watermark for Java segítségével. Védje meg a
  dokumentum integritását a GroupDocs Watermark Java-val.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Hogyan adjon vízjelet diagramokhoz a GroupDocs.Watermark for Java használatával
type: docs
url: /hu/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

 keep bold formatting.

Now produce final answer.# Hogyan adjunk vízjelet diagramokhoz a GroupDocs.Watermark for Java segítségével

A diagramfájlok vízjeleinek kezelése alapvető része a szellemi tulajdon védelmének és a dokumentumok tiszta nyilvános terjesztésének. Ebben az útmutatóban megtanulja, **hogyan adjon vízjelet** egy Visio diagramhoz, valamint **hogyan távolítsa el a vízjelet**, amikor már nincs rá szükség, mindezt a **groupdocs watermark java** könyvtárral. Akár vállalati szintű dokumentumcsővezetéket épít, akár egy gyors segédprogramot ír, ezek a lépések teljes irányítást biztosítanak a diagramok vízjelezéséhez.

## Gyors válaszok
- **Melyik könyvtár kezeli a diagramok vízjeleit Java-ban?** GroupDocs.Watermark for Java.  
- **Hozzáadhatok és eltávolíthatok vízjeleket ugyanabban a futtatásban?** Igen – töltsön be egy diagramot egyszer, és alkalmazza mind a hozzáadást, mind az eltávolítást.  
- **Mely fájlformátumok támogatottak?** Visio formátumok, például `.vsdx`, `.vdx`, valamint más diagramtípusok.  
- **Szükség van licencre?** A próbaverzió licenc fejlesztéshez működik; teljes licenc szükséges a termeléshez.  
- **Melyik Java verzió szükséges?** JDK 8 vagy újabb.

## Mi a „vízjel hozzáadása” a diagramok kontextusában?
A vízjel hozzáadása azt jelenti, hogy egy látható vagy láthatatlan jelzőt – szöveget, logót vagy képet – ágyazunk be egy diagramfájlba. Ez a jelző a fájllal együtt utazik, megkönnyítve a tulajdonjog bizonyítását vagy a vázlat verziók jelzését.

## Miért használjuk a GroupDocs.Watermark for Java-t?
* **Gazdag API** – Keressen, adjon hozzá és töröljön szöveges és képes vízjeleket néhány kódsorral.  
* **Kereszt‑formátum támogatás** – Működik Visio-val (`.vsdx`, `.vdx`) és számos más diagramtípussal.  
* **Teljesítmény‑központú** – Csak a vízjel műveletekhez szükséges diagramrészeket tölti be, alacsony memóriahasználatot biztosítva.

## Előfeltételek
1. **Java Development Kit (JDK) 8+** – Győződjön meg róla, hogy a `java -version` 1.8 vagy újabb verziót jelez.  
2. **IDE** – IntelliJ IDEA, Eclipse vagy bármely kedvelt szerkesztő.  
3. **GroupDocs.Watermark for Java** – Adja hozzá a projektjéhez Maven-en vagy közvetlen JAR letöltéssel.  

### Szükséges könyvtárak és függőségek
Add the repository and dependency to your `pom.xml`:

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

*Ha nem szeretné Maven-t használni, letöltheti a legújabb JAR-t a [GroupDocs.Watermark for Java kiadások](https://releases.groupdocs.com/watermark/java/)-ból.*

### Licenc beszerzése
- **Ingyenes próba:** Tesztelje az összes funkciót licenckulcs nélkül.  
- **Ideiglenes licenc:** Kérjen időkorlátos kulcsot értékeléshez.  
- **Teljes licenc:** Vásároljon előfizetést korlátlan termelési használathoz.

## A GroupDocs.Watermark for Java beállítása
1. **Adja hozzá a könyvtárat** a projektjéhez (Maven vagy manuális JAR).  
2. **Hozzon létre egy `Watermarker` példányt** – ez az objektum a belépési pont a diagramok betöltéséhez, kereséshez, hozzáadáshoz és a vízjelek eltávolításához.

## Implementációs útmutató

### Diagramdokumentum betöltése
Loading is the first step before you can **add watermark** or **remove watermark**. The code below shows how to open a `.vsdx` file with custom load options.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Szöveges vízjelek keresése
Before you add a new watermark, you might want to verify whether a text watermark already exists. This snippet searches for the phrase “Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Képes vízjelek keresése
If you need to locate a logo or any image that was used as a watermark, use the `ImageDctHashSearchCriteria`. This is handy when you want to **remove watermark** that matches a known logo.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Vízjelek eltávolítása
Once you have identified watermarks—text, image, or both—you can clear them from the diagram. The example below demonstrates a combined removal operation.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Gyakorlati alkalmazások
1. **Vállalati szoftverintegráció** – Ágyazza be a vízjelkezelést az ERP vagy dokumentum‑generáló platformjába a márka érvényesítéséhez.  
2. **Tartalomkezelő rendszerek (CMS)** – Automatikusan vizsgálja a feltöltött diagramokat jogosulatlan logók után, és távolítsa el azokat.  
3. **Jogi dokumentumkezelés** – Adjon hozzá egy „Bizalmas” szöveges vízjelet a vázlatfázisokban, majd később **távolítsa el a vízjelet** a végleges benyújtás előtt.

## Gyakori problémák és megoldások

| Tünet | Valószínű ok | Megoldás |
|---------|--------------|-----|
| Nem található vízjel | A keresett szöveg/kép nem egyezik pontosan | Használja az `or()`-t a kritériumok kombinálásához, vagy állítsa be a kis- és nagybetű érzékenységet. |
| `OutOfMemoryError` nagy fájloknál | A diagram teljes egészében a memóriába töltődik | Használja a `DiagramLoadOptions.setLoadPages()`-t, hogy csak a szükséges oldalakat töltse be. |
| A mentett fájl sérült | `watermarker.save()` hívás a vízjelek teljes törlése előtt | Győződjön meg róla, hogy a `possibleWatermarks.clear()` befejeződik, és a `watermarker.close()` a mentés után kerül meghívásra. |

## Gyakran ismételt kérdések

**K: Kereshetek egyszerre szöveget és képeket is?**  
V: Igen. Kombinálja a `TextSearchCriteria` és az `ImageDctHashSearchCriteria`-t az `or()` metódussal, ahogy a eltávolítási példában látható.

**K: Lehet a vízjeleket eltávolítani anélkül, hogy a diagramot károsítanánk?**  
V: Teljesen. A könyvtár elkülöníti a vízjel objektumokat, így a `clear()` hívás csak a vízjel rétegeket távolítja el, miközben az eredeti diagram tartalma megmarad.

**K: A GroupDocs.Watermark támogat több diagramformátumot is?**  
V: Igen. Olyan formátumok, mint a `.vsdx`, `.vdx`, és más Visio‑kompatibilis fájlok teljes mértékben támogatottak.

**K: Hogyan kezeljem hatékonyan a nagy mennyiségű dokumentumot?**  
V: Valósítson meg kötegelt feldolgozási ciklusokat, ahol lehetséges, használjon egyetlen `Watermarker` példányt újra, és korlátozza az oldalbetöltést a `DiagramLoadOptions` segítségével.

**K: Van mód a vízjel felismerés automatizálására CI/CD csővezetékben?**  
V: Beágyazhatja a megadott Java kódrészleteket a build szkriptekbe (pl. Maven vagy Gradle), hogy ellenőrizze, hogy nincs jogosulatlan vízjel a kiadott artefaktok előtt.

**Utolsó frissítés:** 2026-02-18  
**Tesztelve:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs