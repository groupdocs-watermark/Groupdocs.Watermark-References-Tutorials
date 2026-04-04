---
date: '2026-04-04'
description: Tanulja meg, hogyan távolíthatja el a hivatkozásokat a diagram alakzatokból
  a GroupDocs.Watermark Java segítségével, biztosítva a dokumentum biztonságát és
  átláthatóságát.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Hogyan távolítsuk el a hivatkozásokat a diagram alakzatokból a GroupDocs.Watermark
  Java segítségével
type: docs
url: /hu/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hogyan távolítsuk el a hivatkozásokat a diagram alakzatokból a GroupDocs.Watermark Java használatával

A digitális dokumentumok kezelése gyakran magában foglalja a diagramok szerkesztését, különösen akkor, amikor **how to strip links**-re van szükség a biztonság vagy az átláthatóság érdekében. Ebben az útmutatóban megtanul egy egyszerű, lépésről‑lépésre módszert a nem kívánt hiperhivatkozások eltávolítására a diagram alakzatokból a hatékony **GroupDocs.Watermark** Java könyvtár segítségével. A végére tiszta, link‑mentes diagramokkal fog rendelkezni, amelyeket biztonságosan megoszthat.

## Gyors válaszok
- **Mi jelenti a “how to strip links” kifejezést?** It refers to removing hyperlink objects embedded in diagram shapes.  
- **Melyik könyvtár kezeli ezt?** GroupDocs.Watermark for Java (version 24.11 vagy újabb).  
- **Szükségem van licencre?** Egy ingyenes próba működik teszteléshez; érvényes licenc szükséges a termeléshez.  
- **Feldolgozhatok sok fájlt egyszerre?** Igen – a kódot egy ciklusba vagy kötegelt feladatba kell ágyazni.  
- **Ez a megközelítés nyelvspecifikus?** A példa Java, de ugyanaz a koncepció más .NET/Java API-kra is alkalmazható.

## Mi a “how to strip links” a diagram szerkesztésben?
A linkek eltávolítása azt jelenti, hogy megtaláljuk a diagramon belül a alakzatokhoz csatolt hiperhivatkozás objektumokat (pl. Visio *.vsdx) és töröljük őket. Ez megszünteti a külső URL-eket, amelyek érzékeny információkat fedhetnek fel vagy megszakíthatják a prezentáció folyamatát.

## Miért használjuk a GroupDocs.Watermark-et Java-ban?
- **Precision** – Közvetlen hozzáférés az alakzat objektumokhoz és azok hiperhivatkozás gyűjteményeihez.  
- **Performance** – Nagy diagramokhoz optimalizált, anélkül, hogy a teljes dokumentumot a memóriába töltené.  
- **Cross‑format support** – Számos diagram formátummal működik (Visio, Draw.io, stb.).

## Előkövetelmények
- **GroupDocs.Watermark** könyvtár ≥ 24.11.  
- Maven (vagy manuális JAR beillesztés).  
- Java JDK 8 vagy újabb.  
- IDE, például IntelliJ IDEA vagy Eclipse.

## A GroupDocs.Watermark beállítása Java-hoz
### Maven beállítás
Adja hozzá a tárolót és a függőséget a `pom.xml`-hez:

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
Ha nem szeretne Maven-t használni, töltse le a legújabb JAR-t a hivatalos oldalról:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Licenc beszerzési lépések
- Kezdje egy ingyenes próba letöltésével.  
- Termeléshez szerezzen be egy ideiglenes vagy teljes licencet a GroupDocs portálról.

#### Alapvető inicializálás és beállítás
Hozzon létre egy `Watermarker` példányt, amely a diagramot tartalmazó mappára mutat:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Hogyan távolítsuk el a hivatkozásokat a diagram alakzatokból
Az alábbiakban egy tömör, négylépéses folyamatot láthat, amely bemutatja a **remove hyperlinks java** működését.

### 1. lépés: A diagram fájl betöltése
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Miért?* A fájl betöltése programozott hozzáférést biztosít az oldalaihoz, alakzataihoz és hiperhivatkozás gyűjteményeihez.

### 2. lépés: Az alakzat tartalmának elérése
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Miért?* Szüksége van egy hivatkozásra a konkrét alakzatra, amely hiperhivatkozásokat tartalmazhat.

### 3. lépés: Iterálás és hiperhivatkozások eltávolítása
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Miért?* A fordított irányú ciklus megakadályozza az indexeltolódási problémákat a gyűjtemény elemeinek törlésekor.

### 4. lépés: Mentés és bezárás
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Miért?* A mentés a megtisztított diagramot a lemezre írja, a bezárás pedig felszabadítja a fájlkezelőket a memória szivárgás elkerülése érdekében.

## A linkek eltávolításának gyakorlati alkalmazásai
1. **Security** – Távolítsa el a külső URL-eket, amelyek phishinghez vagy adatszivárgáshoz vezethetnek.  
2. **Compliance** – Biztosítsa, hogy a diagramok megfeleljenek a belső irányelveknek a terjesztés előtt.  
3. **Presentation Cleanliness** – Szüntesse meg a felesleges kattintható területeket, amelyek elvonják a nézők figyelmét.

## Teljesítmény szempontok
- **Loop Efficiency** – Használja a fent bemutatott fordított iterációs mintát.  
- **Resource Management** – Részesítse előnyben a `try‑with‑resources` vagy a kifejezett `close()` hívásokat.  
- **Large Files** – Figyelje a CPU/tárhely használatot; fontolja meg az oldalak kötegelt feldolgozását.

## Gyakori problémák és megoldások
- **No hyperlinks found** – Ellenőrizze, hogy a diagram valóban tartalmaz-e hiperhivatkozás objektumokat; egyes formátumok másként tárolják őket.  
- **IndexOutOfBoundsException** – Mindig iteráljon fordított irányban, amikor elemeket távolít el egy gyűjteményből.  
- **License errors** – Győződjön meg róla, hogy a licencfájl megfelelően van elhelyezve vagy átadva a `Watermarker` konstruktorának.

## Gyakran feltett kérdések

**Q: Hogyan kezelem a több alakzatot több oldalon?**  
A: Iteráljon a `content.getPages()`-en, majd minden oldal `getShapes()` gyűjteményén, és alkalmazza ugyanazt az eltávolítási logikát minden alakzatra.

**Q: Szűrhetek linkeket domain szerint a teljes URL helyett?**  
A: Igen – módosítsa a `contains` ellenőrzést, hogy a domain karakterláncot keresse (pl. `"example.com"`).

**Q: Van mód arra, hogy naplózzam, mely linkek lettek eltávolítva?**  
A: A cikluson belül rögzítse a `shape.getHyperlinks().get_Item(i).getAddress()` értéket a törlés előtt, és írja egy naplófájlba.

**Q: Működik ez más dokumentumokba beágyazott PDF diagramokkal?**  
A: A GroupDocs.Watermark sok formátumot támogat; győződjön meg arról, hogy a fájltípus diagramként (Visio, VDX, stb.) van felismerve.

**Q: Milyen licenc szükséges kötegelt feldolgozáshoz?**  
A: Teljes termelési licenc szükséges minden nem próba, nagy mennyiségű művelethez.

## Következtetés
Most már rendelkezik egy teljes, termelésre kész módszerrel a **how to strip links** diagram alakzatokból történő eltávolítására a GroupDocs.Watermark for Java használatával. Integrálja ezt a dokumentumfeldolgozó csővezetékekbe a biztonság, a megfelelőség és a vizuális minőség növelése érdekében.

### Következő lépések
- Fedezze fel a többi manipulációs funkciót, például a vízjelek hozzáadását vagy a szöveg pecsételését.  
- Kombinálja ezt a rutinot egy fájlfigyelő szolgáltatással, hogy automatikusan tisztítsa meg a diagramokat feltöltéskor.

---

**Utoljára frissítve:** 2026-04-04  
**Tesztelve ezzel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs  

## Erőforrások
- [Dokumentáció](https://docs.groupdocs.com/watermark/java/)
- [API referencia](https://reference.groupdocs.com/watermark/java)
- [Letöltés](https://releases.groupdocs.com/watermark/java/)
- [GitHub tároló](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ingyenes támogatási fórum](https://forum.groupdocs.com/c/watermark/10)
- [Ideiglenes licenc beszerzése](https://purchase.groupdocs.com/temporary-license/)