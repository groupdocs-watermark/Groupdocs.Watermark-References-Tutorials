---
date: '2026-04-07'
description: Leer hoe je e-mailinhoud in Java kunt doorzoeken met GroupDocs.Watermark,
  inclusief hoe je meerdere trefwoorden in e-mail kunt zoeken en hoe je e-mailwatermerken
  kunt verwijderen.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Zoek e-mailtekst Java met GroupDocs.Watermark: Een uitgebreide gids'
type: docs
url: /nl/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Zoek e-mailinhoud Java met GroupDocs.Watermark

Als je snel en betrouwbaar **search email body java** wilt uitvoeren, ben je hier aan het juiste adres. In deze tutorial laten we zien hoe GroupDocs.Watermark voor Java je in staat stelt specifieke tekst te vinden in e-mailonderwerpen, HTML‑lichamen en platte‑tekst‑lichamen, en hoe je ongewenste watermerken daarna kunt verwijderen. Aan het einde kun je een robuuste oplossing implementeren die werkt met één of meerdere zoekwoorden en zelfs e‑mailwatermerken verwijdert wanneer dat nodig is.

## Snelle antwoorden
- **Wat betekent “search email body java”?** Het verwijst naar het gebruik van Java‑code (met GroupDocs.Watermark) om tekst binnen de inhoud van een e‑mail te vinden.  
- **Kan ik meerdere zoekwoorden e‑mail tegelijk zoeken?** Ja – maak afzonderlijke `SearchCriteria`‑objecten aan en combineer ze.  
- **Hoe verwijder ik e‑mailwatermerken?** Gebruik de `PossibleWatermarkCollection.clear()`‑methode na een zoekopdracht.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een permanente licentie is vereist voor productie.  
- **Welke IDE werkt het beste?** IntelliJ IDEA of Eclipse worden beide volledig ondersteund.

## Wat je zult leren
- Installeren en configureren van GroupDocs.Watermark voor Java.  
- Het instellen van zoekcriteria om **search email body java** te doorzoeken in onderwerpen en lichamen.  
- Technieken voor **search multiple keywords email** in één enkele uitvoering.  
- De exacte stappen **how to remove email watermarks** na het vinden ervan.  

## Waarom e‑mailinhoud Java zoeken met GroupDocs.Watermark?
GroupDocs.Watermark biedt een high‑level API die de complexiteit van het parseren van .msg‑bestanden, het verwerken van verschillende lichaamformaten en het beheren van watermerken abstraheert. Dit bespaart je tijd vergeleken met het bouwen van een eigen parser en zorgt voor consistente resultaten bij grote e‑mail‑batches.

## Vereisten
- Java Development Kit (JDK) 8 of nieuwer.  
- Maven (of de mogelijkheid om JAR‑bestanden handmatig toe te voegen).  
- Basiskennis van Java en e‑mailbestandsformaten (.msg, .eml).  

## GroupDocs.Watermark voor Java instellen
GroupDocs.Watermark voor Java vereenvoudigt watermerken en tekst zoeken binnen documenten, inclusief e‑mails. Hieronder staan de twee meest voorkomende manieren om de bibliotheek aan je project toe te voegen.

### Maven‑configuratie
Voeg het volgende toe aan je `pom.xml`‑bestand om GroupDocs.Watermark als afhankelijkheid toe te voegen:
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
Je kunt ook de nieuwste versie rechtstreeks downloaden van [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Stappen voor licentie‑acquisitie
- **Free Trial:** Begin met een gratis proefversie om basisfunctionaliteit te testen.  
- **Temporary License:** Verkrijg een tijdelijke licentie voor uitgebreide toegang en testen.  
- **Purchase:** Overweeg aankoop als GroupDocs.Watermark aan je behoeften voldoet.

#### Basisinitialisatie
Initialiseer de `Watermarker`‑klasse zoals hieronder weergegeven:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementatie‑gids

### Functie 1: Tekst zoeken in e‑mailinhoud
Deze functie maakt het mogelijk om specifieke tekst te zoeken in het onderwerp en de inhoud van een e‑mail.

#### Overzicht
We laten zien hoe je GroupDocs.Watermark configureert om verschillende delen van een e‑mailbericht te doorzoeken met Java‑code.

##### Stap 1: Documentpaden definiëren
Stel je invoer‑ en uitvoer‑paden in voor het verwerken van e‑mails:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Stap 2: Laadopties en Watermarker instellen
Initialiseer de `EmailLoadOptions` en `Watermarker` om met je e‑maildocument te werken.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Stap 3: Zoekcriteria maken
Definieer criteria voor het zoeken naar tekst. We gebruiken een hoofdletter‑onafhankelijke zoekopdracht voor het trefwoord **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Stap 4: Zoeklocaties specificeren
Configureer de zoekopdracht om zowel het onderwerp als de inhoud van e‑mails te doorzoeken:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Stap 5: Zoekopdracht uitvoeren en watermerken wissen
Voer de zoekopdracht uit en verwijder eventuele gevonden watermerken:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Stap 6: Wijzigingen opslaan
Sla na verwerking je wijzigingen op in een nieuw document:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tips voor probleemoplossing
- **Common Issue:** Als de zoekresultaten leeg zijn, controleer dan of de tekst aanwezig is in de e‑mailinhoud of het onderwerp.  
- **Performance Tip:** Optimaliseer door de zoekopdrachten te beperken tot alleen de secties die je daadwerkelijk nodig hebt.

### Functie 2: Opties voor het laden van e‑maildocumenten
Deze sectie bespreekt hoe je extra opties kunt instellen bij het laden van een e‑maildocument voor verwerking met GroupDocs.Watermark.

#### Overzicht
Het configureren van laadopties biedt meer controle over hoe documenten worden verwerkt, bijvoorbeeld het opgeven van wachtwoordbeveiliging of coderingsinstellingen.

##### Stap 1: Laadopties configureren
Hier is een basisconfiguratie voor `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Belangrijke configuratie‑opties
- **Password Protection:** Geef wachtwoorden op als je e‑mails versleuteld zijn.  
- **Encoding Settings:** Definieer specifieke coderingssoorten indien nodig.

## Hoe meerdere zoekwoorden e‑mail zoeken
Als je meerdere termen in één keer wilt vinden, maak dan meerdere `SearchCriteria`‑objecten aan en combineer ze met logische **OR**‑ of **AND**‑operatoren. De API laat je criteria combineren, zodat je kunt zoeken naar “invoice” **of** “receipt” zonder aparte loops uit te voeren.

## Hoe e‑mailwatermerken verwijderen
Nadat je watermerken (of enige tekst die aan je criteria voldoet) hebt gevonden, verwijdert de `PossibleWatermarkCollection.clear()`‑methode ze uit het e‑maildocument. Dit is de exacte stap die we in **Stap 5** hierboven gebruikten, en het werkt voor elk aantal overeenkomsten.

## Praktische toepassingen

### Gebruikssituatie 1: Geautomatiseerde e‑mailverwerking
Automatiseer het filteren en verwerken van bulk‑e‑mailgegevens om specifieke inhoud efficiënt te vinden.

### Gebruikssituatie 2: Controle op wettelijke naleving
Zorg voor naleving door te zoeken naar gevoelige informatie in bedrijfs‑e‑mails.

### Gebruikssituatie 3: Automatisering van klantenondersteuning
Stroomlijn ondersteuningsprocessen door snel trefwoorden of zinnen in klantvragen te vinden.

## Prestatie‑overwegingen
Houd bij het gebruik van GroupDocs.Watermark het volgende in gedachten om de prestaties te optimaliseren:

- **Resource Management:** Beheer geheugen en verwerkingskracht efficiënt om grote e‑mail‑datasets te verwerken.  
- **Java Memory Management Best Practices:** Houd het gebruik van bronnen regelmatig in de gaten en maak bronnen tijdig vrij.

## Veelgestelde vragen

**Q:** Hoe kan ik versleutelde e‑mails verwerken met GroupDocs.Watermark?  
**A:** Gebruik de `EmailLoadOptions` om wachtwoorden op te geven bij het initialiseren van de `Watermarker`.

**Q:** Kan ik meerdere trefwoorden tegelijk zoeken?  
**A:** Ja, maak afzonderlijke `SearchCriteria`‑instanties aan en combineer ze met logische bewerkingen.

**Q:** Is GroupDocs.Watermark Java gratis te gebruiken?  
**A:** Een gratis proefversie is beschikbaar; overweeg een licentie aan te schaffen voor uitgebreide functies.

**Q:** Hoe verwerk ik grote hoeveelheden e‑mails efficiënt?  
**A:** Optimaliseer je zoekopdrachten door specifieke e‑mailsecties te targeten en bronnen effectief te beheren.

**Q:** Waar kan ik extra hulp of ondersteuning vinden?  
**A:** Bezoek het [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) voor community‑ondersteuning of neem contact op met hun gratis ondersteuningskanaal.

## Bronnen
- **Documentation:** Verken gedetailleerde handleidingen op [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Bekijk technische details op [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Laatst bijgewerkt:** 2026-04-07  
**Getest met:** GroupDocs.Watermark 24.11 for Java  
**Auteur:** GroupDocs