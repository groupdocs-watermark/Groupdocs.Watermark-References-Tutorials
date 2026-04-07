---
date: '2026-04-07'
description: Lär dig hur du söker i e‑postkroppen med Java med GroupDocs.Watermark,
  inklusive hur du söker efter flera nyckelord i e‑post och hur du tar bort e‑postvattenstämplar.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Sök i e‑postkropp med Java och GroupDocs.Watermark: En omfattande guide'
type: docs
url: /sv/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Sök e-postinnehåll Java med GroupDocs.Watermark

Om du snabbt och pålitligt behöver **search email body java** är du på rätt plats. I den här handledningen går vi igenom hur GroupDocs.Watermark för Java låter dig hitta specifik text i e-postämnen, HTML‑kroppar och ren‑text‑kroppar, samt hur du kan rensa bort oönskade vattenmärken efteråt. När du är klar kan du implementera en robust lösning som fungerar med enstaka eller flera nyckelord och även tar bort e-postvattenmärken vid behov.

## Snabba svar
- **Vad betyder “search email body java”?** Det hänvisar till att använda Java‑kod (med GroupDocs.Watermark) för att hitta text i ett e‑postmeddelandes innehåll.  
- **Kan jag söka flera nyckelord i e‑post samtidigt?** Ja – skapa separata `SearchCriteria`‑objekt och kombinera dem.  
- **Hur tar man bort e‑postvattenmärken?** Använd metoden `PossibleWatermarkCollection.clear()` efter en sökning.  
- **Behöver jag en licens?** En gratis provperiod fungerar för testning; en permanent licens krävs för produktion.  
- **Vilken IDE fungerar bäst?** IntelliJ IDEA eller Eclipse stöds fullt ut.

## Vad du kommer att lära dig
- Installera och konfigurera GroupDocs.Watermark för Java.  
- Ställa in sökkriterier för att **search email body java** över ämnen och kroppar.  
- Tekniker för **search multiple keywords email** i ett enda körning.  
- De exakta stegen **how to remove email watermarks** efter att ha hittat dem.  

## Varför söka e-postinnehåll Java med GroupDocs.Watermark?
GroupDocs.Watermark erbjuder ett hög‑nivå API som abstraherar komplexiteten i att parsra .msg‑filer, hantera olika kroppformat och hantera vattenmärken. Detta sparar tid jämfört med att bygga en egen parser och säkerställer konsekventa resultat över stora e‑postbatchar.

## Förutsättningar
- Java Development Kit (JDK) 8 eller nyare.  
- Maven (eller möjlighet att lägga till JAR‑filer manuellt).  
- Grundläggande kunskap om Java och e‑postfilformat (.msg, .eml).  

## Konfigurera GroupDocs.Watermark för Java
GroupDocs.Watermark för Java förenklar vattenmärkning och textsökning i dokument, inklusive e‑post. Nedan följer de två vanligaste sätten att lägga till biblioteket i ditt projekt.

### Maven-inställning
Inkludera följande i din `pom.xml`‑fil för att lägga till GroupDocs.Watermark som ett beroende:
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

### Direktnedladdning
Alternativt kan du ladda ner den senaste versionen direkt från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Steg för att skaffa licens
- **Free Trial:** Starta med en gratis provperiod för att testa grundläggande funktioner.  
- **Temporary License:** Skaffa en tillfällig licens för utökad åtkomst och testning.  
- **Purchase:** Överväg att köpa om GroupDocs.Watermark uppfyller dina behov.

#### Grundläggande initiering
Initiera `Watermarker`‑klassen som visas nedan:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementeringsguide

### Funktion 1: Sök text i e-postinnehåll
Denna funktion möjliggör sökning efter specifik text i ett e‑postmeddelandes ämne och kropp.

#### Översikt
Vi kommer att demonstrera hur man konfigurerar GroupDocs.Watermark för att söka igenom olika delar av ett e‑postmeddelande med Java‑kod.

##### Steg 1: Definiera dokumentvägar
Ställ in dina in- och utdata‑vägar för att hantera e‑post:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Steg 2: Ställ in laddningsalternativ och Watermarker
Initiera `EmailLoadOptions` och `Watermarker` för att arbeta med ditt e‑postdokument.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Steg 3: Skapa sökkriterier
Definiera kriterier för textsökning. Vi använder en skiftläges‑okänslig sökning för nyckelordet **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Steg 4: Ange sökplatser
Konfigurera sökningen så att den täcker både ämnet och kroppen i e‑postmeddelanden:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Steg 5: Utför sökning och rensa vattenmärken
Utför sökningen och ta bort eventuella hittade vattenmärken:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Steg 6: Spara ändringar
Efter bearbetning, spara dina ändringar till ett nytt dokument:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Felsökningstips
- **Common Issue:** Om sökresultaten är tomma, kontrollera att texten finns i e‑postens kropp eller ämne.  
- **Performance Tip:** Optimera genom att begränsa sökningar till endast de sektioner du faktiskt behöver.

### Funktion 2: Ladda e-postdokumentalternativ
Detta avsnitt beskriver hur du kan konfigurera ytterligare alternativ när du laddar ett e‑postdokument för bearbetning med GroupDocs.Watermark.

#### Översikt
Att konfigurera laddningsalternativ ger mer kontroll över hur dokument hanteras, t.ex. att ange lösenordsskydd eller kodningsinställningar.

##### Steg 1: Konfigurera laddningsalternativ
Här är en grundläggande konfiguration för `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Nyckelkonfigurationsalternativ
- **Password Protection:** Ange lösenord om dina e‑postmeddelanden är krypterade.  
- **Encoding Settings:** Definiera specifika kodningstyper efter behov.

## Hur man söker flera nyckelord i e‑post
Om du behöver hitta flera termer i ett pass, skapa flera `SearchCriteria`‑objekt och kombinera dem med logiska **OR**‑ eller **AND**‑operatorer. API‑et låter dig kedja kriterier, så du kan söka efter “invoice” **eller** “receipt” utan att köra separata loopar.

## Hur man tar bort e‑postvattenmärken
Efter att du har hittat vattenmärken (eller någon text som matchar dina kriterier) tar metoden `PossibleWatermarkCollection.clear()` bort dem från e‑postdokumentet. Detta är exakt det steg vi använde i **Steg 5** ovan, och det fungerar för vilket antal träffar som helst.

## Praktiska tillämpningar

### Användningsfall 1: Automatiserad e‑postbehandling
Automatisera filtrering och bearbetning av stora mängder e‑postdata för att effektivt hitta specifikt innehåll.

### Användningsfall 2: Rättsliga efterlevnadskontroller
Säkerställ efterlevnad genom att söka efter känslig information i företags‑e‑post.

### Användningsfall 3: Automatisering av kundsupport
Förenkla supportarbetsflöden genom att snabbt hitta nyckelord eller fraser i kundförfrågningar.

## Prestandaöverväganden
När du använder GroupDocs.Watermark, överväg följande för att optimera prestanda:

- **Resource Management:** Hantera minne och processorkraft effektivt för att hantera stora e‑postdatamängder.  
- **Java Memory Management Best Practices:** Övervaka regelbundet resursanvändning och frigör resurser omedelbart.

## Vanliga frågor

**Q:** Hur kan jag hantera krypterade e‑postmeddelanden med GroupDocs.Watermark?  
**A:** Använd `EmailLoadOptions` för att ange lösenord när du initierar `Watermarker`.

**Q:** Kan jag söka efter flera nyckelord samtidigt?  
**A:** Ja, skapa separata `SearchCriteria`‑instanser och kombinera dem med logiska operationer.

**Q:** Är GroupDocs.Watermark Java gratis att använda?  
**A:** En gratis provperiod finns tillgänglig; överväg att köpa en licens för utökade funktioner.

**Q:** Hur hanterar jag stora volymer av e‑post effektivt?  
**A:** Optimera dina sökningar genom att rikta in dig på specifika e‑postsektioner och hantera resurser effektivt.

**Q:** Var kan jag hitta ytterligare hjälp eller support?  
**A:** Besök [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) för community‑support eller kontakta deras kostnadsfria supportkanal.

## Resurser
- **Documentation:** Utforska detaljerade guider på [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Få tekniska detaljer på [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

**Senast uppdaterad:** 2026-04-07  
**Testad med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs