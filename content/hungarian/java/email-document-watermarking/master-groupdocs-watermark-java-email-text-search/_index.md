---
date: '2025-12-31'
description: Ismerje meg, hogyan kereshet e‑mail szöveget a GroupDocs.Watermark for
  Java használatával, és kezelje hatékonyan a törzseket, tárgyakat és mellékleteket.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Hogyan keressünk e‑mail szöveget a GroupDocs.Watermark Java‑val – Átfogó útmutató
type: docs
url: /hu/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Hogyan keressünk e‑mail szöveget a GroupDocs.Watermark Java segítségével

Az e‑mail tárgyában, törzsében vagy mellékleteiben egy adott kifejezés megtalálása fejfájást okozhat – különösen, ha tucatnyi vagy akár több száz üzenettel dolgozol. Ebben az útmutatóban megtanulod, hogyan **keressünk e‑mail** tartalmat gyorsan és pontosan a **GroupDocs.Watermark for Java** segítségével. Végigvezetünk a telepítésen, a kódon és a legjobb gyakorlatokon, hogy magabiztosan integrálhasd az e‑mail szövegkeresést saját alkalmazásaidba.

## Gyors válaszok
- **Melyik könyvtár teszi lehetővé az e‑mail szöveg keresését Java‑ban?** GroupDocs.Watermark for Java.  
- **Szükségem van licencre?** A ingyenes próba a teszteléshez elegendő; a termeléshez fizetett licenc szükséges.  
- **Kereshetek a tárgyban és a törzsben is?** Igen – állítsd be az `EmailSearchableObjects`‑t, hogy tartalmazza a Subject, HtmlBody és PlainTextBody elemeket.  
- **Az API kis‑ és nagybetű érzékeny?** Beállíthatod a kis‑betű érzéketlen keresést a `TextSearchCriteria` megfelelő flag‑jének beállításával.  
- **Milyen Java verzió szükséges?** JDK 8 vagy újabb; Maven ajánlott a függőségek kezeléséhez.

## Mi az a „hogyan keressünk e‑mail” a GroupDocs.Watermark‑dal?
GroupDocs.Watermark egységes API‑t biztosít vízjelek és egyszerű szöveg keresésére, eltávolítására vagy módosítására számos dokumentumtípusban – beleértve az **e‑mail üzeneteket** (`.msg`, `.eml`). A kereshető objektumok modelljének használatával pontosan az e‑mail azon részeit célozhatod meg, amelyek érdekelnek, így a tömeges feldolgozás gyors és megbízható.

## Miért használjuk a GroupDocs.Watermark Java‑t e‑mail kereséshez?
- **Egységes API** – PDF‑ekkel, képekkel, Office fájlokkal és e‑mail‑ekkel egyaránt működik ugyanazzal a kódmintával.  
- **Teljesítmény‑optimalizált** – A keresési műveletek memóriában futnak, külső szolgáltatások nélkül.  
- **Robusztus kezelés** – Támogatja a HTML és egyszerű szöveg törzseket, mellékleteket, sőt a jelszóval védett e‑mail‑eket is.  
- **Könnyű integráció** – Maven/Gradle kész, világos dokumentációval és aktív támogatással.

## Előfeltételek

- **Java Development Kit (JDK)** 8 vagy újabb.  
- **Maven** (vagy Gradle) a függőségek kezeléséhez.  
- **IntelliJ IDEA** vagy **Eclipse** IDE.  
- Alapvető ismeretek a Java szintaxisról és az e‑mail fájlformátumokról (`.msg`, `.eml`).

## A GroupDocs.Watermark Java beállítása

### Maven beállítás
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

### Közvetlen letöltés
Alternatívaként letöltheted a legújabb JAR‑t a [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) oldalról.

### Licenc beszerzése
- **Ingyenes próba:** A fő funkciók tesztelése licenckulcs nélkül.  
- **Ideiglenes licenc:** Kérj időkorlátos kulcsot a hosszabb értékeléshez.  
- **Fizetett licenc:** Vásárolj korlátlan termelési használatra.

#### Alapvető inicializálás
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementációs útmutató

### Funkció 1: Szöveg keresése az e‑mail törzsben

#### Áttekintés
Az API-t úgy konfiguráljuk, hogy egy megadott kulcsszóra keresve átvizsgálja az e‑mail **tárgyát**, **HTML törzsét** és **egyszerű szöveg törzsét**.

#### 1. lépés: Dokumentum útvonalak meghatározása
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### 2. lépés: Betöltési beállítások és Watermarker létrehozása
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### 3. lépés: Keresési feltételek létrehozása
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### 4. lépés: Keresési helyek megadása
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### 5. lépés: Keresés végrehajtása és vízjelek törlése
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### 6. lépés: Módosítások mentése
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Hibaelhárítási tippek
- **Üres eredmény:** Ellenőrizd, hogy a kulcsszó valóban megjelenik-e a kiválasztott e‑mail részekben.  
- **Teljesítmény:** Szűkítsd a kereshető objektumokat csak a szükségesekre (pl. Subject + PlainTextBody), hogy felgyorsítsd a nagy kötegeket.

### Funkció 2: E‑mail dokumentum betöltési beállításai

#### Áttekintés
`EmailLoadOptions` lehetővé teszi az e‑mail feldolgozásának vezérlését – hasznos titkosított üzenetek vagy egyedi kódolások esetén.

#### 1. lépés: Betöltési beállítások konfigurálása
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Kulcsfontosságú konfigurációs beállítások
- **Jelszóvédelem:** Állítsd be a `loadOptions.setPassword("yourPassword")`‑t titkosított `.msg` fájlokhoz.  
- **Kódolás beállítása:** Állítsd be a `loadOptions.setEncoding(Charset.forName("UTF-8"))`‑t nem szabványos karakterkészletek esetén.

## Gyakorlati alkalmazások

- **Automatizált e‑mail feldolgozás:** Tömegesen átvizsgálja a bejövő támogatási jegyeket olyan kulcsszavakra, mint a „refund” vagy „error”.  
- **Jogi megfelelőség ellenőrzés:** Gyorsan megtalálja a bizalmas kifejezéseket (pl. SSN, hitelkártya számok) a vállalati e‑mail archívumokban.  
- **Ügyfélszolgálati automatizálás:** A felismert kifejezések alapján a megfelelő támogatási csapatnak irányítja az e‑mail‑eket.

## Teljesítménybeli megfontolások
- **Erőforrás-kezelés:** Hívd meg a `watermarker.close()`‑t, amint befejezted a feldolgozást, hogy felszabadítsd a natív erőforrásokat.  
- **Memória legjobb gyakorlatok:** Több ezer üzenet kezelésekor dolgozd fel őket kötegekben, és ahol lehetséges, újrahasználd a `Watermarker` példányt.

## Következtetés
Most már egy stabil, termelésre kész megközelítést birtokolsz a **e‑mail tartalom keresésére** a GroupDocs.Watermark Java segítségével. Az API rugalmassága lehetővé teszi, hogy az e‑mail konkrét részeit célozd, eltávolítsd a nem kívánt vízjeleket, és a logikát nagyobb munkafolyamatokba integráld.

### Következő lépések
- Kísérletezz **több keresési feltétellel** (pl. „invoice” + „overdue” kombinálása).  
- Fedezd fel a **vízjel hozzáadását**, hogy megjelöld a bizalmas adatokat tartalmazó e‑mail‑eket.  
- Merülj el más dokumentumtípusokban (PDF, DOCX) ugyanazzal a Watermarker munkafolyammal.

## Gyakran ismételt kérdések

**Q1:** Hogyan kezelhetek titkosított e‑mail‑eket a GroupDocs.Watermark‑dal?  
**A1:** Használd a `EmailLoadOptions.setPassword("yourPassword")`‑t a `Watermarker` példány létrehozása előtt.

**Q2:** Kereshetek egyszerre több kulcsszót?  
**A2:** Igen – hozz létre külön `SearchCriteria` objektumokat minden kulcsszóhoz, és kombináld őket logikai operátorokkal (pl. `OrSearchCriteria`).

**Q3:** Ingyenesen használható a GroupDocs.Watermark Java?  
**A3:** Van ingyenes próba a kiértékeléshez. Termelési használathoz fizetett licenc szükséges.

**Q4:** Hogyan kezeljem hatékonyan a nagy mennyiségű e‑mail‑t?  
**A4:** Szűkítsd a kereshető objektumokat csak a szükségesekre, dolgozd fel az e‑mail‑eket kötegekben, és mindig zárd le a `Watermarker`‑t az erőforrások felszabadításához.

**Q5:** Hol találok további segítséget vagy támogatást?  
**A5:** Látogasd meg a [GroupDocs fórumot](https://forum.groupdocs.com/c/watermark/10) a közösségi segítségért, vagy vedd fel közvetlenül a kapcsolatot a GroupDocs támogatással.

## Források
- **Dokumentáció:** Részletes útmutatókat találsz a [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) oldalon.  
- **API referencia:** Technikai részleteket a [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) oldalon érhetsz el.

---

**Last Updated:** 2025-12-31  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs