---
date: '2025-12-31'
description: Leer hoe u e‑mailtekst kunt doorzoeken met GroupDocs.Watermark voor Java
  en beheer inhoud, onderwerp en bijlagen efficiënt.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Hoe e‑mailtekst te zoeken met GroupDocs.Watermark Java – Een uitgebreide gids
type: docs
url: /nl/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Hoe e‑mailtekst zoeken met GroupDocs.Watermark Java

Het vinden van een specifieke zin in het onderwerp, de inhoud of de bijlagen van een e‑mail kan een hoofdpijn zijn—vooral wanneer je tientallen of honderden berichten verwerkt. In deze tutorial ontdek je **hoe e‑mail te zoeken** inhoud snel en nauwkeurig met **GroupDocs.Watermark for Java**. We lopen de installatie, code en best‑practice tips door zodat je e‑mailtekst zoeken kunt integreren in je eigen applicaties met vertrouwen.

## Snelle antwoorden
- **Welke bibliotheek laat me e‑mailtekst zoeken in Java?** GroupDocs.Watermark for Java.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een betaalde licentie is vereist voor productie.  
- **Kan ik zowel onderwerp als inhoud doorzoeken?** Ja—configureer `EmailSearchableObjects` om Subject, HtmlBody en PlainTextBody op te nemen.  
- **Is de API hoofdlettergevoelig?** Je kunt kiezen voor hoofdletterongevoelige zoekopdrachten door de juiste vlag in `TextSearchCriteria` in te stellen.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger; Maven wordt aanbevolen voor afhankelijkheidsbeheer.

## Wat is “hoe e‑mail te zoeken” met GroupDocs.Watermark?
GroupDocs.Watermark biedt een eendelige API voor het lokaliseren, verwijderen of aanpassen van watermerken en platte tekst over veel documenttypen—waaronder **e‑mailberichten** (`.msg`, `.eml`). Door gebruik te maken van het doorzoekbare objectmodel kun je precies de delen van een e‑mail targeten die je nodig hebt, waardoor bulkverwerking snel en betrouwbaar is.

## Waarom GroupDocs.Watermark Java gebruiken voor e‑mail zoeken?
- **Unified API** – Werkt met PDF’s, afbeeldingen, Office‑bestanden en e‑mails met dezelfde code‑patronen.  
- **Performance‑optimized** – Zoekbewerkingen draaien in het geheugen zonder externe services.  
- **Robust handling** – Ondersteunt HTML‑ en platte‑tekstlichamen, bijlagen en zelfs met wachtwoord beveiligde e‑mails.  
- **Easy integration** – Maven/Gradle klaar, met duidelijke documentatie en actieve ondersteuning.

## Vereisten
- **Java Development Kit (JDK)** 8 of nieuwer.  
- **Maven** (of Gradle) voor afhankelijkheidsbeheer.  
- Een IDE zoals **IntelliJ IDEA** of **Eclipse**.  
- Basiskennis van Java‑syntaxis en e‑mailbestandsformaten (`.msg`, `.eml`).

## GroupDocs.Watermark voor Java instellen

### Maven‑instelling
Voeg de repository en afhankelijkheid toe aan je `pom.xml`:

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

### Directe download
Alternatief kun je de nieuwste JAR downloaden van [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licentie‑acquisitie
- **Free Trial:** Test kernfuncties zonder licentiesleutel.  
- **Temporary License:** Vraag een tijd‑beperkte sleutel aan voor uitgebreide evaluatie.  
- **Paid License:** Aankoop voor onbeperkt productiegebruik.

#### Basisinitialisatie
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementatie‑gids

### Functie 1: Tekst zoeken in e‑mailinhoud

#### Overzicht
We configureren de API om het **onderwerp**, **HTML‑inhoud** en **platte‑tekst‑inhoud** van een e‑mail te scannen op een opgegeven trefwoord.

#### Stap 1: Documentpaden definiëren
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Stap 2: Laadopties en Watermarker instellen
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Stap 3: Zoekcriteria maken
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Stap 4: Zoeklocaties specificeren
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Stap 5: Zoekopdracht uitvoeren en watermerken wissen
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Stap 6: Wijzigingen opslaan
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tips voor probleemoplossing
- **Lege resultaten:** Controleer of het trefwoord daadwerkelijk voorkomt in de geselecteerde e‑mailonderdelen.  
- **Performance:** Beperk de doorzoekbare objecten tot alleen die je nodig hebt (bijv. Subject + PlainTextBody) om grote batches te versnellen.

### Functie 2: E‑mail Documentopties Laden

#### Overzicht
`EmailLoadOptions` stelt je in staat te bepalen hoe de e‑mail wordt geparseerd—handig voor versleutelde berichten of aangepaste coderingen.

#### Stap 1: Laadopties configureren
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Belangrijke configuratie‑opties
- **Password Protection:** Stel `loadOptions.setPassword("yourPassword")` in voor versleutelde `.msg`‑bestanden.  
- **Encoding Settings:** Pas `loadOptions.setEncoding(Charset.forName("UTF-8"))` aan bij niet‑standaard tekensets.

## Praktische toepassingen
- **Automated Email Processing:** Bulk‑scan binnenkomende support‑tickets op trefwoorden zoals “refund” of “error”.  
- **Legal Compliance Checks:** Snel vertrouwelijke termen (bijv. SSN, credit‑card nummers) vinden in bedrijfs‑mailarchieven.  
- **Customer Support Automation:** Route e‑mails op basis van gedetecteerde zinnen naar het juiste supportteam.

## Prestatie‑overwegingen
- **Resource Management:** Roep `watermarker.close()` aan zodra je klaar bent met verwerken om native resources vrij te geven.  
- **Memory Best Practices:** Verwerk duizenden berichten in batches en hergebruik de `Watermarker`‑instantie waar mogelijk.

## Conclusie
Je hebt nu een solide, productie‑klare aanpak voor **hoe e‑mail te zoeken** inhoud met GroupDocs.Watermark Java. De flexibiliteit van de API laat je specifieke delen van een e‑mail targeten, ongewenste watermerken verwijderen en de logica integreren in grotere workflows.

### Volgende stappen
- Experimenteer met **meerdere zoekcriteria** (bijv. combineer “invoice” + “overdue”).  
- Verken **watermerk‑toevoeging** om e‑mails met gevoelige data te markeren.  
- Duik in andere documenttypen (PDF, DOCX) met dezelfde Watermarker‑workflow.

## Veelgestelde vragen

**Q1:** Hoe kan ik versleutelde e‑mails verwerken met GroupDocs.Watermark?  
**A1:** Gebruik `EmailLoadOptions.setPassword("yourPassword")` vóór het aanmaken van de `Watermarker`‑instantie.

**Q2:** Kan ik meerdere trefwoorden tegelijk zoeken?  
**A2:** Ja—maak afzonderlijke `SearchCriteria`‑objecten voor elk trefwoord en combineer ze met logische operatoren (bijv. `OrSearchCriteria`).

**Q3:** Is GroupDocs.Watermark Java gratis te gebruiken?  
**A3:** Een gratis proefversie is beschikbaar voor evaluatie. Voor productiegebruik is een betaalde licentie vereist.

**Q4:** Hoe ga ik efficiënt om met grote hoeveelheden e‑mails?  
**A4:** Beperk de doorzoekbare objecten tot alleen de benodigde, verwerk e‑mails in batches en sluit altijd de `Watermarker` om resources vrij te geven.

**Q5:** Waar kan ik extra hulp of ondersteuning vinden?  
**A5:** Bezoek het [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) voor community‑ondersteuning of neem rechtstreeks contact op met GroupDocs support.

## Resources
- **Documentation:** Verken gedetailleerde handleidingen op [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Bekijk technische details op [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Laatst bijgewerkt:** 2025-12-31  
**Getest met:** GroupDocs.Watermark 24.11 for Java  
**Auteur:** GroupDocs