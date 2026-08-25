---
date: '2026-08-25'
description: Ismerd meg, hogyan szerkesztheted a diagramfájlokat és távolíthatod el
  a hiperlinkeket a GroupDocs.Watermark for Java használatával. Biztonságosan védheted
  diagramjaidat gyorsan, lépésről‑lépésre útmutatóval.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Ismerd meg, hogyan szerkesztheted a diagramfájlokat és távolíthatod
  el a hiperlinkeket a GroupDocs.Watermark for Java segítségével. Kövesd a világos
  lépéseket a dokumentumaid védelméhez.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Hogyan szerkessz diagramot és távolíts el hiperlinkeket Java-val
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Hogyan szerkessz diagramot és távolíts el hiperlinkeket Java-val
type: docs
url: /hu/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hogyan szerkesszünk diagramot és távolítsunk el hiperhivatkozásokat Java-val  

A digitális dokumentumok kezelése gyakran magában foglalja diagramok szerkesztését, különösen akkor, amikor **edit diagram** fájlokat kell módosítani a hiperhivatkozások eltávolítása érdekében a biztonság vagy a vizuális tisztaság miatt. Ez az útmutató pontosan megmutatja, hogyan szerkesszünk diagram fájlokat és távolítsunk el nem kívánt hiperhivatkozásokat a diagram alakzatokból a hatékony **GroupDocs.Watermark** Java könyvtár segítségével. A útmutató végére egy tiszta, link‑mentes diagramot kapunk, amely készen áll a terjesztésre.  

## Gyors válaszok  
- **What is the main goal?** Távolítsa el az összes hiperhivatkozást a diagram alakzatokból a biztonság és a megjelenés javítása érdekében.  
- **Which library is required?** GroupDocs.Watermark for Java, version 24.11 vagy újabb.  
- **Do I need a license?** Egy ingyenes próba működik teszteléshez; a kereskedelmi licenc szükséges a termeléshez.  
- **Can I process many files at once?** Igen – ugyanaz a kód egy ciklusba helyezhető a kötegelt feldolgozáshoz.  
- **What Java version is supported?** Java 8 vagy újabb (Java 11 ajánlott).  

## Mi az a „how to edit diagram”?  
**How to edit diagram** a programozott módon egy diagram fájl megnyitásának, belső elemeinek (például alakzatok, szöveg vagy hiperhivatkozások) módosításának és az eredmény mentésének folyamatát jelenti. A GroupDocs.Watermark segítségével szerkesztheti a diagram fájlokat anélkül, hogy az eredeti szerkesztőeszközre lenne szükség.  

## Miért használjuk a GroupDocs.Watermark for Java-t?  
A GroupDocs.Watermark **30+ diagram és képformátumot** támogat (beleértve a VSDX, SVG és WMF formátumokat), és akár **500 MB** méretű fájlokat is feldolgozhat anélkül, hogy a teljes dokumentumot a memóriába töltené, így **20 % gyorsabb** feldolgozási sebességet biztosít sok versenytárshoz képest.  

## Előkövetelmények  
- **GroupDocs.Watermark** könyvtár verzió 24.11 vagy újabb.  
- Maven telepítve (vagy a JAR fájlok, ha manuális beállítást részesít előnyben).  
- Java Development Kit 8 vagy újabb és egy IDE, például IntelliJ IDEA vagy Eclipse.  

### Szükséges könyvtárak, verziók és függőségek  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (ha a Maven megközelítést használja)  

### Környezet beállítási követelmények  
Győződjön meg arról, hogy a JDK `bin` könyvtára szerepel a `PATH` környezeti változóban, és hogy az IDE a megfelelő JDK verzióra mutat.  

### Tudás előkövetelmények  
Jól kell ismernie az alapvető Java szintaxist, a Maven függőségkezelést és a fájl I/O műveleteket.  

## Hogyan állítsuk be a GroupDocs.Watermark for Java-t?  
A `Watermarker` osztály biztosítja az API belépési pontját a dokumentumok betöltéséhez és módosításához.  
A GroupDocs.Watermark használatának megkezdéséhez adja hozzá Maven koordinátáit a projekt `pom.xml` fájljához. Ez letölti a könyvtárat és annak függőségeit, lehetővé téve a Watermarker osztály példányosítását és a diagram fájlok közvetlen Java kódból történő kezelését. Ezután beállíthatja a licencelést és a kimeneti opciókat, mielőtt bármely dokumentumot feldolgozná.  

Adja hozzá a GroupDocs.Watermark függőséget a `pom.xml` fájlhoz.  

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

Ha nem szeretne Maven-t használni, töltse le a legújabb JAR-t a hivatalos kiadási oldalról.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Licenc beszerzési lépések  
- Kezdje egy ingyenes próbaidőszakkal az API értékeléséhez.  
- Termeléshez szerezzen be ideiglenes vagy állandó licencet a szállító portáljáról.  

#### Alapvető inicializálás és beállítás  
A `Watermarker` osztály a belépési pont minden dokumentum‑feldolgozó művelethez.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Hogyan szerkesszünk diagramot és távolítsunk el hiperhivatkozásokat a GroupDocs.Watermark segítségével?  
A `Watermarker` osztály biztosítja az API belépési pontját a dokumentumok betöltéséhez és módosításához.  
Először töltse be a diagram fájlt egy Watermarker példányba. Ezután szerezze be az alakzatok gyűjteményét, azonosítsa azokat, amelyek hiperhivatkozás objektumokat tartalmaznak, és iteráljon rajtuk fordított sorrendben, hogy biztonságosan törölje minden hivatkozást anélkül, hogy befolyásolná a gyűjtemény indexelését. Ez biztosítja, hogy az összes beágyazott URL eltávolításra kerüljön, miközben megőrzi a diagram vizuális integritását.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Why this step matters**: A fájl betöltése programozott hozzáférést biztosít minden alakzathoz és annak kapcsolódó tulajdonságaihoz.  

## Hogyan érjük el az alakzat tartalmát egy diagramon?  
A `DiagramShape` objektum egy egyedi alakzatot képvisel egy diagramon, és feltárja annak tulajdonságait és csatolt metaadatait.  
A diagram betöltése után hívja meg a `getShapes()` metódust a Watermarker-en, hogy `DiagramShape` objektumok listáját kapja. Minden alakzatot ellenőrizhet a hiperhivatkozás gyűjtemények szempontjából, lehetővé téve a hivatkozások pontos célzását eltávolítás vagy módosítás céljából. Olvashatja továbbá az alakzat szövegét, színeit és geometriáját, ha további módosításokra van szükség.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Why this step matters**: A pontos alakzat kiválasztása biztosítja, hogy csak a nem kívánt hivatkozásokat távolítsa el, anélkül, hogy más vizuális elemeket befolyásolna.  

## Hogyan iteráljunk és távolítsunk el hiperhivatkozásokat biztonságosan?  
A `removeHyperlink(int index)` metódus egy hiperhivatkozást töröl a megadott pozícióban az alakzat hiperhivatkozás gyűjteményén belül.  
Iteráljon a hiperhivatkozás listán az utolsó indexről nulláig. Ez a fordított ciklus megakadályozza az indexeltolódást, amely akkor fordul elő, amikor elemeket távolítanak el, biztosítva, hogy minden hiperhivatkozás feldolgozásra kerüljön anélkül, hogy kihagynák. A törlés után frissítheti az alakzat állapotát vagy folytathatja a következő alakzattal a diagramon.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Why this step matters**: A fordított ciklus garantálja, hogy minden hiperhivatkozás eltávolításra kerüljön anélkül, hogy bármely bejegyzést kihagynának.  

## Hogyan mentjük a szerkesztett diagramot és szabadítsuk fel az erőforrásokat?  
A `save(String path)` metódus a módosított dokumentumot a megadott fájlhelyre írja, befejezve minden változást.  
Miután az összes hiperhivatkozás eltávolításra került, hívja meg a `save` metódust a Watermarker példányon, egy új fájlnév megadásával, hogy elkerülje az eredeti felülírását. Ezután hívja a `close()` metódust a fájlkezelők felszabadításához és a memória felszabadításához, ami elengedhetetlen a hosszú távú kötegelt folyamatokhoz. Ez biztosítja, hogy a fájl megfelelően legyen lezárva és készen álljon a további használatra.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Why this step matters**: A megfelelő erőforrások lezárása elkerüli a memória szivárgásokat és a fájl‑zárolási problémákat a szerveren.  

## Gyakorlati alkalmazások  
A hiperhivatkozások diagram alakzatokból történő eltávolítása több valós helyzetben is előnyös lehet:  

1. **Security** – Megakadályozza a külső hivatkozásokat, amelyek rosszindulatú webhelyekre vezethetnek.  
2. **Compliance** – Megfelel a vállalati szabályzatoknak, amelyek tiltják a beágyazott URL-eket a megosztott eszközökben.  
3. **Clarity** – Tisztább prezentációkat eredményez, ahol a hivatkozások zavaróak lennének.  

Beágyazhatja ezt a logikát nagyobb automatizálási csővezetékekbe, például éjszakai kötegelt feladatokba, amelyek minden diagramot tisztítanak, mielőtt az intranetre kerülnek.  

## Teljesítmény szempontok  

### Teljesítmény optimalizálása  
- Használjon egyetlen `Watermarker` példányt fájlonként a terhelés csökkentése érdekében.  
- Részesítse előnyben a fordított iterációt (ahogy látható), hogy elkerülje a költséges lista újra‑indexelést.  

### Erőforrás használati irányelvek  
- 200 MB-nál nagyobb diagramok esetén figyelje a heap használatot, és fontolja meg a JVM `-Xmx` zászló növelését.  
- A VisualVM-hez hasonló profilozó eszközök segíthetnek azonosítani a szűk keresztmetszeteket nagyméretű kötegelt futtatások során.  

### Legjobb gyakorlatok a Java memória kezeléshez  
- Deklarálja az objektumokat a lehető legkisebb hatókörön belül.  
- Használjon try‑with‑resources szerkezetet az adatfolyamokkal való munka során az automatikus lezárás biztosításához.  

## Gyakran ismételt kérdések  

**Q: Hogyan kezeljem az ezrek alakzatot tartalmazó diagramokat?**  
A: A diagramot oldalanként dolgozza fel, és minden oldal erőforrásait szabadítsa fel, mielőtt a következőre lépne, hogy alacsony memóriahasználatot biztosítson.  

**Q: Korlátozhatom a hiperhivatkozás eltávolítást csak bizonyos oldalakra?**  
A: Igen – szerezze meg a kívánt oldal indexét, majd alkalmazza a eltávolító ciklust csak az adott oldal alakzataira.  

**Q: Kereskedelmi licenc kötelező a kötegelt feldolgozáshoz?**  
A: Érvényes licenc szükséges minden termelési szintű telepítéshez; az ingyenes próba 30 napra és 5 dokumentumra korlátozódik.  

**Q: Támogatja a GroupDocs.Watermark az SVG diagramokat?**  
A: Teljes mértékben – az SVG a 30+ támogatott formátum közé tartozik, és a hiperhivatkozásokat ugyanazzal az API hívással lehet eltávolítani.  

**Q: Mi van, ha egy alakzat több hiperhivatkozást tartalmaz?**  
A: A fordított iterációs ciklus minden hiperhivatkozás bejegyzést egyenként eltávolít, biztosítva, hogy minden hivatkozás törlésre kerüljön.  

## Erőforrások  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**Utolsó frissítés:** 2026-08-25  
**Tesztelve ezzel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs  

## Kapcsolódó oktatóanyagok

- [Diagram vízjelezési oktatóanyagok a GroupDocs.Watermark Java-hoz](/watermark/java/diagram-document-watermarking/)  
- [Diagram fejlécek és láblécek szerkesztése Java-ban a GroupDocs.Watermark használatával: Átfogó útmutató](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Alakzatok hatékony eltávolítása diagramokból a GroupDocs.Watermark for Java használatával](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)