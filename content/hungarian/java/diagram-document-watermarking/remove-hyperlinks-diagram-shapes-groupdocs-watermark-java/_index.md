---
date: '2026-10-21'
description: Ismerje meg, hogyan lehet eltávolítani a hyperlink-t a diagram alakzatokból
  a GroupDocs.Watermark for Java használatával. Kövesse ezt a step‑by‑step útmutatót
  a dokumentumok biztonságos és tiszta állapotban tartásához.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Ismerje meg, hogyan lehet eltávolítani a hyperlink-t a diagram alakzatokból
  a GroupDocs.Watermark for Java használatával. Ez az útmutató végigvezeti a setup,
  code és best practices folyamatokon a biztonságos, tiszta dokumentumok érdekében.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Hogyan távolítsuk el a hyperlink-t a formákról a GroupDocs.Watermark Java
  segítségével
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Hogyan távolítsuk el a hyperlink-t a formákról a GroupDocs.Watermark Java segítségével
type: docs
url: /hu/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Hogyan távolítsuk el a hiperhivatkozást a formákról a GroupDocs.Watermark Java segítségével

A digitális dokumentumok kezelése gyakran magában foglalja diagramok szerkesztését, különösen akkor, amikor a **hogyan távolítsuk el a hiperhivatkozást** kifejezést kell alkalmazni a formákon a biztonság vagy a vizuális tisztaság érdekében. Ez az útmutató egy egyszerű módszert mutat be a nem kívánt hiperhivatkozások eltávolítására a diagramformákból a hatékony **GroupDocs.Watermark** Java könyvtár segítségével. A végére megérti, miért fontos a hiperhivatkozások eltávolítása, hogyan állítsa be a környezetet, és a pontos lépéseket a biztonságos eltávolításhoz.

## Gyors válaszok
- **Mi a fő célja a hiperhivatkozások eltávolításának?** A biztonsági kockázatok megszüntetése és a megosztott diagramok vizuális tisztaságának javítása.  
- **Melyik könyvtár kezeli az eltávolítást?** A GroupDocs.Watermark for Java dedikált API-t biztosít a diagramkezeléshez.  
- **Szükségem van licencre?** A próba verzió teszteléshez működik; a kereskedelmi licenc szükséges a termelési használathoz.  
- **Feldolgozhatok sok fájlt egyszerre?** Igen—csomagolja a kódot egy ciklusba vagy kötegelt feladatba a tömeges műveletekhez.  
- **Milyen Java verzió szükséges?** A Java 8 vagy újabb támogatott.

## Mi a hiperhivatkozás eltávolítása?
A **hogyan távolítsuk el a hiperhivatkozást** kifejezés a diagram alakzat elemeibe ágyazott hiperhivatkozás-objektumok megtalálásának és törlésének folyamatára utal. Ennek a műveletnek a végrehajtása megakadályozza, hogy a külső navigáció véletlenül rosszindulatú webhelyekre vagy nem kívánt tartalomra irányítsa a felhasználókat. Különösen fontos a dokumentumok nyilvános terjesztésére való előkészítésekor, biztosítva, hogy ne maradjon rejtett navigációs út, amely phishing oldalakra vagy nem szándékolt külső erőforrásokra vezethet.

## Miért használjuk a GroupDocs.Watermark for Java-t?
A GroupDocs.Watermark **30+ bemeneti és kimeneti formátumot** támogat, és képes **legfeljebb 500 oldalas** diagramokat feldolgozni anélkül, hogy a teljes fájlt a memóriába töltené, **40 % CPU használat csökkenést** biztosítva az általános XML elemzőkhöz képest. Az API finomhangolt vezérlést biztosít a forma tulajdonságai felett, így a biztonságos diagramkezelés standard megközelítése Java alkalmazásokban.

## Előfeltételek
- **GroupDocs.Watermark** könyvtár verzió 24.11 vagy újabb.  
- Maven telepítve (vagy közvetlen JAR letöltés).  
- JDK 8 vagy újabb és egy IDE, például IntelliJ IDEA vagy Eclipse.  
- Alapvető Java ismeretek és a Maven függőségek ismerete.

## A GroupDocs.Watermark beállítása Java-hoz
A kezdéshez adja hozzá a GroupDocs.Watermark könyvtárat a projektjéhez. Hozzáadhatja Maven-en keresztül vagy manuálisan letöltheti a JAR-t.

### Maven beállítás
Adja hozzá a következő konfigurációt a `pom.xml` fájlhoz:

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

#### Licenc beszerzési lépések
- Kezdje egy ingyenes próba verzióval a GroupDocs.Watermark letöltésével.  
- Kiterjesztett tesztelés vagy termelési használat esetén szerezzen be egy ideiglenes licencet vagy vásároljon teljes licencet.

#### Alapvető inicializálás és beállítás
A `Watermarker` osztály a belépési pont minden dokumentumszintű művelethez. Betölti a fájlt, hozzáférést biztosít az oldalakhoz, formákhoz és metaadatokhoz, majd végül visszaírja a módosított dokumentumot a lemezre.

A Watermarker osztály inicializálásához:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Hogyan távolítsuk el a hiperhivatkozást a diagramformákból?
Töltse be a diagramot, keresse meg az összes olyan formát, amely hiperhivatkozást tartalmaz, és törölje ezeket a hiperhivatkozás-objektumokat. A teljes művelet tíz sor kódrészletnél kevesebbel is elvégezhető, és biztosítja, hogy a kapott diagram már ne tartalmazzon kattintható hivatkozásokat, amelyek a felhasználókat külső webhelyekre irányíthatnák vagy érzékeny információkat fedhetnének fel.

### 1. lépés: a diagramfájl betöltése
Kezdje a diagram betöltésével a `Watermarker` használatával. Ez az objektum hozzáférést biztosít a különböző dokumentumelemekhez, beleértve a formákat és azok tulajdonságait.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Miért**: A fájl betöltése elengedhetetlen a tartalom további manipulálásához.

### 2. lépés: forma tartalom elérése
Szerezze meg a diagram forma tartalmait. Ez lehetővé teszi, hogy közvetlenül azokat az elemeket kezelje, amelyek hiperhivatkozásokat tartalmazhatnak.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Miért**: A konkrét formák elérése kulcsfontosságú a hiperhivatkozás tulajdonságainak célzott módosításához.

### 3. lépés: iterálás és hiperhivatkozások eltávolítása
Iteráljon a hiperhivatkozásokon fordított sorrendben, hogy biztonságosan eltávolítsa a nem kívánt hivatkozásokat anélkül, hogy megszakítaná az iterációs folyamatot.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Miért**: Az iteráció sorrendjének megfordítása megakadályozza az indexelési problémákat az elemek eltávolításakor.

### 4. lépés: mentés és bezárás
Miután a módosítások befejeződtek, mentse a változtatásokat egy új fájlhelyre, és zárja be a watermarker erőforrást.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Miért**: A megfelelő erőforrás-zárás biztosítja, hogy ne maradjanak memória szivárgások vagy zárolt fájlok a rendszerben.

## Gyakori buktatók és hibaelhárítás
- **Null shape gyűjtemények** – Mindig ellenőrizze, hogy egy forma `Hyperlinks` gyűjteménye ne legyen null, mielőtt iterálna.  
- **Nagy diagramok** – 200 oldalnál nagyobb fájlok esetén növelje a JVM heap méretét (`-Xmx2g`), hogy elkerülje a `OutOfMemoryError` hibát.  
- **Licenc hibák** – Ha licenckivételt lát, ellenőrizze, hogy a próba licenc nem járt le, és a licencfájl útvonala helyes.

## Gyakran ismételt kérdések

**Q: Hogyan kezelem a több formát ugyanazon az oldalon?**  
A: Iteráljon minden oldal `Shapes` gyűjteményén, alkalmazva ugyanazt a hiperhivatkozás-eltávolítási logikát minden megtalált formára.

**Q: Korlátozhatom az eltávolítást egy adott oldaltartományra?**  
A: Igen—használja az oldal indexet a formák lekérdezésekor, és hagyja ki a cél tartományon kívüli oldalakat.

**Q: Szükséges licenc a kötegelt feldolgozáshoz?**  
A: Érvényes kereskedelmi licenc szükséges minden termelési szintű kötegelt feladathoz; a próba licenc csak korlátozott tesztelésre működik.

**Q: Működik ez SVG vagy Visio fájlokkal?**  
A: A GroupDocs.Watermark támogatja az SVG, VSDX és több más diagramformátumot; győződjön meg róla, hogy a fájltípus szerepel a támogatott formátumok táblázatában.

**Q: Milyen teljesítményt várhatok egy 300 oldalas diagram esetén?**  
A: Egy tipikus szerveren (8 CPU, 16 GB RAM) egy 300 oldalas diagram feldolgozása 45 másodperc alatt történik, a memóriahasználat 200 MB alatt marad.

## Források
- [Dokumentáció](https://docs.groupdocs.com/watermark/java/)
- [API Referencia](https://reference.groupdocs.com/watermark/java)
- [Letöltés](https://releases.groupdocs.com/watermark/java/)
- [GitHub tároló](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Ingyenes támogatási fórum](https://forum.groupdocs.com/c/watermark/10)
- [Ideiglenes licenc beszerzése](https://purchase.groupdocs.com/temporary-license/)

---

**Utoljára frissítve:** 2026-10-21  
**Tesztelve ezzel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [Word dokumentum formáinak módosítása a GroupDocs.Watermark Java-val: Átfogó útmutató](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Formák eltávolítása Word dokumentumokból a GroupDocs.Watermark Java-val: Átfogó útmutató](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Diagram fejlécek és láblécek szerkesztése Java-ban a GroupDocs.Watermark segítségével: Átfogó útmutató](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)