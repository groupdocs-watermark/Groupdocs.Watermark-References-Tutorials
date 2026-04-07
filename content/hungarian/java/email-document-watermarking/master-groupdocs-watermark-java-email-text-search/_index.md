---
date: '2026-04-07'
description: Tanulja meg, hogyan kereshet az e‑mail szövegében Java használatával
  a GroupDocs.Watermark segítségével, beleértve, hogyan kereshet több kulcsszót az
  e‑mailben, és hogyan távolíthatja el az e‑mail vízjeleket.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'E-mail szöveg keresése Java-ban a GroupDocs.Watermark segítségével: Átfogó
  útmutató'
type: docs
url: /hu/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# E‑mail törzs keresése Java-val a GroupDocs.Watermark segítségével

Ha gyorsan és megbízhatóan szeretne **search email body java** keresni, jó helyen jár. Ebben az útmutatóban bemutatjuk, hogyan teszi lehetővé a GroupDocs.Watermark for Java, hogy meghatározott szöveget találjon az e‑mail tárgyakban, HTML‑törzsökben és egyszerű szöveges törzsökben, valamint hogyan tisztíthatja meg a nem kívánt vízjeleket később. A végére képes lesz egy robusztus megoldást megvalósítani, amely egyetlen vagy több kulcsszón is működik, és szükség esetén eltávolítja az e‑mail vízjeleket.

## Gyors válaszok
- **What does “search email body java” mean?** Ez azt jelenti, hogy Java kódot (a GroupDocs.Watermark használatával) alkalmazunk az e‑mail tartalmában lévő szöveg megtalálására.  
- **Can I search multiple keywords email at once?** Igen – hozzon létre külön `SearchCriteria` objektumokat, és kombinálja őket.  
- **How to remove email watermarks?** Használja a `PossibleWatermarkCollection.clear()` metódust a keresés után.  
- **Do I need a license?** Egy ingyenes próba a teszteléshez megfelelő; a termeléshez állandó licenc szükséges.  
- **Which IDE works best?** Az IntelliJ IDEA és az Eclipse egyaránt teljesen támogatott.

## Mit fog megtanulni
- A GroupDocs.Watermark for Java telepítése és konfigurálása.  
- Keresési kritériumok beállítása a **search email body java** kereséséhez a tárgyakban és a törzsekben.  
- Technika a **search multiple keywords email** egyetlen futtatásban történő kereséséhez.  
- A pontos lépések a **how to remove email watermarks** megtalálás után.

## Miért keresze az e‑mail törzset Java-val a GroupDocs.Watermark segítségével?
A GroupDocs.Watermark egy magas szintű API-t biztosít, amely elrejti a .msg fájlok elemzésének, a különböző törzsformátumok kezelésének és a vízjelek kezelésének összetettségét. Ez időt takarít meg a saját elemző írásához képest, és biztosítja a konzisztens eredményeket nagy e‑mail kötegek esetén.

## Előfeltételek
- Java Development Kit (JDK) 8 vagy újabb.  
- Maven (vagy a JAR-ok kézi hozzáadásának lehetősége).  
- Alapvető ismeretek a Java és az e‑mail fájlformátumok (.msg, .eml) terén.  

## A GroupDocs.Watermark beállítása Java-hoz
A GroupDocs.Watermark for Java egyszerűsíti a vízjelek elhelyezését és a szövegkeresést a dokumentumokban, beleértve az e‑mail üzeneteket is. Az alábbiakban a két leggyakoribb módot mutatjuk be a könyvtár projektbe való hozzáadásához.

### Maven beállítás
Adja hozzá a következőket a `pom.xml` fájlhoz, hogy a GroupDocs.Watermark függőségként kerüljön be:
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
Alternatívaként letöltheti a legújabb verziót közvetlenül a [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) oldalról.

### Licenc beszerzési lépések
- **Free Trial:** Kezdje egy ingyenes próbaidőszakkal az alapfunkciók teszteléséhez.  
- **Temporary License:** Szerezzen ideiglenes licencet a kiterjesztett hozzáféréshez és teszteléshez.  
- **Purchase:** Fontolja meg a vásárlást, ha a GroupDocs.Watermark megfelel az igényeinek.

#### Alap inicializálás
Inicializálja a `Watermarker` osztályt az alábbi módon:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementációs útmutató

### 1. funkció: Szöveg keresése e‑mail törzsben
Ez a funkció lehetővé teszi a specifikus szöveg keresését egy e‑mail tárgyában és törzsében.

#### Áttekintés
Bemutatjuk, hogyan konfiguráljuk a GroupDocs.Watermark-ot, hogy Java kóddal keresést végezzen egy e‑mail üzenet különböző részeiben.

##### 1. lépés: Dokumentum útvonalak meghatározása
Állítsa be a bemeneti és kimeneti útvonalakat az e‑mail-ek kezeléséhez:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### 2. lépés: Betöltési beállítások és Watermarker konfigurálása
Inicializálja az `EmailLoadOptions` és a `Watermarker` osztályokat, hogy az e‑mail dokumentummal dolgozhasson.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### 3. lépés: Keresési kritérium létrehozása
Határozza meg a szöveg keresésének kritériumait. Egy kis‑nagybetű érzéketlen keresést fogunk használni a **"test"** kulcsszóra:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### 4. lépés: Keresési helyek megadása
Állítsa be a keresést úgy, hogy mind a tárgyat, mind a törzset lefedje az e‑mail-ekben:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### 5. lépés: Keresés végrehajtása és vízjelek törlése
Végezze el a keresést, és távolítsa el a megtalált vízjeleket:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### 6. lépés: Változások mentése
A feldolgozás után mentse a változásokat egy új dokumentumba:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Hibaelhárítási tippek
- **Common Issue:** Ha a keresési eredmények üresek, ellenőrizze, hogy a szöveg jelen van-e az e‑mail törzsben vagy tárgyban.  
- **Performance Tip:** Optimalizálja a keresést úgy, hogy csak a ténylegesen szükséges szakaszokra korlátozza.

### 2. funkció: E‑mail dokumentum betöltési beállítások
Ez a szakasz azt tárgyalja, hogyan állíthat be további opciókat egy e‑mail dokumentum betöltésekor a GroupDocs.Watermark feldolgozásához.

#### Áttekintés
A betöltési beállítások konfigurálása nagyobb irányítást biztosít a dokumentumok kezelésében, például jelszóvédelem vagy kódolási beállítások megadásával.

##### 1. lépés: Betöltési beállítások konfigurálása
Alább egy alap beállítás a `EmailLoadOptions` számára:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Kulcsfontosságú konfigurációs opciók
- **Password Protection:** Adja meg a jelszavakat, ha az e‑mailjei titkosítottak.  
- **Encoding Settings:** Határozza meg a szükséges kódolási típusokat.

## Hogyan keressen több kulcsszót egy e‑mail-ben
Ha egyetlen átfutás során több kifejezést szeretne megtalálni, hozzon létre több `SearchCriteria` objektumot, és kombinálja őket logikai **OR** vagy **AND** operátorokkal. Az API lehetővé teszi a kritériumok láncolását, így kereshet „invoice” **or** „receipt” anélkül, hogy külön ciklusokat futtatna.

## Hogyan távolítsa el az e‑mail vízjeleket
Miután megtalálta a vízjeleket (vagy bármely, a kritériumainak megfelelő szöveget), a `PossibleWatermarkCollection.clear()` metódus eltávolítja azokat az e‑mail dokumentumból. Ez a pontos lépés, amelyet a fenti **5. lépésben** használtunk, és bármennyi egyezésre működik.

## Gyakorlati alkalmazások

### Használati eset 1: Automatizált e‑mail feldolgozás
Automatizálja a tömeges e‑mail adatok szűrését és feldolgozását a specifikus tartalom hatékony megtalálásához.

### Használati eset 2: Jogi megfelelőség ellenőrzése
Biztosítsa a megfelelőséget úgy, hogy érzékeny információkat keres a vállalati e‑mail-ekben.

### Használati eset 3: Ügyfélszolgálati automatizálás
Egyszerűsítse a támogatási munkafolyamatokat azáltal, hogy gyorsan megtalálja a kulcsszavakat vagy kifejezéseket az ügyfél megkereséseiben.

## Teljesítménybeli megfontolások
A GroupDocs.Watermark használatakor vegye figyelembe a következőket a teljesítmény optimalizálásához:
- **Resource Management:** Hatékonyan kezelje a memóriát és a feldolgozási kapacitást a nagy e‑mail adatkészletek kezeléséhez.  
- **Java Memory Management Best Practices:** Rendszeresen ellenőrizze az erőforrás-használatot, és gyorsan szabadítsa fel az erőforrásokat.

## Gyakran ismételt kérdések

**Q:** Hogyan kezelhetem a titkosított e‑mail-eket a GroupDocs.Watermark segítségével?  
**A:** Használja az `EmailLoadOptions`-t a jelszavak megadásához a `Watermarker` inicializálásakor.

**Q:** Kereshetek több kulcsszót egyszerre?  
**A:** Igen, hozzon létre külön `SearchCriteria` példányokat, és kombinálja őket logikai műveletekkel.

**Q:** Ingyenesen használható a GroupDocs.Watermark Java?  
**A:** Elérhető egy ingyenes próba; fontolja meg a licenc vásárlását a kiterjesztett funkciókért.

**Q:** Hogyan kezeljem hatékonyan a nagy mennyiségű e‑mail-t?  
**A:** Optimalizálja a kereséseket úgy, hogy konkrét e‑mail szakaszokra céloz, és hatékonyan kezelje az erőforrásokat.

**Q:** Hol találok további segítséget vagy támogatást?  
**A:** Látogassa meg a [GroupDocs fórumot](https://forum.groupdocs.com/c/watermark/10) a közösségi támogatásért, vagy vegye fel a kapcsolatot ingyenes támogatási csatornájukkal.

## Források
- **Documentation:** Tekintse meg a részletes útmutatókat a [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) oldalon.  
- **API Reference:** Tekintse meg a technikai részleteket a [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) oldalon.  

---

**Utolsó frissítés:** 2026-04-07  
**Tesztelve a következővel:** GroupDocs.Watermark 24.11 for Java  
**Szerző:** GroupDocs