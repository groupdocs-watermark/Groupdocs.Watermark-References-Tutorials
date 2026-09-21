---
date: '2026-01-03'
description: Lär dig hur du listar e‑postmottagare i Java med GroupDocs.Watermark
  – automatisera extrahering av Till, Kopia och Blindkopia från e‑postdokument.
keywords:
- Java email parsing
- GroupDocs.Watermark Java
- listing email recipients
title: Lista e‑postmottagare Java med GroupDocs.Watermark
type: docs
url: /sv/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Lista e‑postmottagare Java med GroupDocs.Watermark

Att extrahera varje **To**, **CC** och **BCC**‑adress från en e‑postfil kan vara tidskrävande när du hanterar dussintals eller hundratals meddelanden. I den här handledningen kommer du att lära dig hur du **list email recipients java** snabbt och pålitligt genom att utnyttja GroupDocs.Watermark Java‑biblioteket. Vi går igenom installation, kodgenomgångar och verkliga användningsfall så att du kan integrera denna funktion i dina egna applikationer.

## Quick Answers
- **Vad gör den här koden?** Den öppnar en e‑postfil och skriver ut alla To‑, CC‑ och BCC‑adresser.  
- **Vilket bibliotek krävs?** GroupDocs.Watermark for Java (version 24.11).  
- **Kan den läsa .msg‑ och .eml‑filer?** Ja – API:et stöder vanliga e‑postformat.  
- **Behöver jag en licens?** En gratis provperiod fungerar för testning; en full licens krävs för produktion.  
- **Är batch‑behandling möjlig?** Absolut – du kan loopa över flera filer med samma mönster.

## Introduction

Är du trött på att manuellt gå igenom e‑postdata för att extrahera mottagarlistor? Att automatisera denna uppgift kan spara tid och minska fel, särskilt när du hanterar stora volymer e‑post. Den här guiden visar hur du utnyttjar det kraftfulla GroupDocs.Watermark Java‑biblioteket för att analysera e‑postdokument och **list email recipients java** effektivt.

**Vad du kommer att lära dig**
- Att konfigurera din miljö för att använda GroupDocs.Watermark för Java  
- Ladda och initiera ett e‑postdokument med GroupDocs.Watermark API  
- Hämta listor över To‑, CC‑ och BCC‑mottagare från e‑postdokument  
- Praktiska tillämpningar och prestandaöverväganden  

Låt oss börja med att gå igenom förutsättningarna.

## Prerequisites

Innan du dyker ner i koden, se till att din miljö är klar:

### Nödvändiga bibliotek, versioner och beroenden

Du behöver ha GroupDocs.Watermark för Java installerat. Denna guide använder version 24.11.

### Krav för miljöinställning

- **Java Development Kit (JDK):** Version 8 eller högre  
- **Integrated Development Environment (IDE):** IntelliJ IDEA eller Eclipse rekommenderas  
- **Dependency Management:** Maven eller direkt nedladdningsuppsättning  

### Kunskapsförutsättningar

En grundläggande förståelse för Java‑programmering och bekantskap med att hantera e‑postformat (som .msg‑filer) är till hjälp.

## Setting Up GroupDocs.Watermark for Java

För att komma igång måste du konfigurera ditt projekt med nödvändiga beroenden. Så här gör du:

**Maven‑inställning**

Lägg till följande konfiguration i din `pom.xml`‑fil för att inkludera GroupDocs.Watermark:

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

**Direkt nedladdning**

Alternativt, ladda ner den senaste versionen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Steg för att skaffa licens

- **Free Trial:** Starta med en gratis provperiod för att utforska funktionerna.  
- **Temporary License:** Ansök om en tillfällig licens om du behöver förlängd åtkomst för teständamål.  
- **Purchase:** Överväg att köpa en licens för produktionsbruk.

När din installation är klar, låt oss initiera och förbereda miljön för att bearbeta e‑postdokument.

## Så listar du e‑postmottagare Java – Implementeringsguide

Detta avsnitt delar upp varje funktion i hanterbara steg så att du kan implementera e‑postparsning effektivt med GroupDocs.Watermark.

### Ladda och initiera e‑postdokument

**Översikt**  
Att ladda ett e‑postdokument är det första steget i vår process. Detta innebär att initiera ett `Watermarker`‑objekt, som fungerar som vår gateway för att interagera med e‑postfiler.

**Implementeringssteg**

1. **Importera nödvändiga klasser**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```
2. **Definiera e‑postfilens sökväg och laddningsalternativ**  
   Ange sökvägen till ditt e‑postdokument. Ersätt `"YOUR_DOCUMENT_DIRECTORY/email.msg"` med den faktiska sökvägen.  
   ```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```
3. **Resurshantering**  
   Kom alltid ihåg att stänga `Watermarker`‑instansen efter användning för att frigöra systemresurser.  
   ```java
   watermarker.close();
   ```

### Lista alla direkta mottagare av ett e‑postmeddelande

**Översikt**  
Att hämta direkta (To) mottagare är enkelt när du har initierat ditt e‑postdokument.

**Implementeringssteg**

1. **Hämta e‑postinnehåll**  
   Se till att `watermarker`‑objektet redan är initierat som visat i föregående avsnitt.  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```
2. **Iterera och lista mottagare**  
   Loopa igenom listan med direkta mottagare och skriv ut varje e‑postadress.  
   ```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### Lista alla CC‑mottagare av ett e‑postmeddelande

**Översikt**  
Att lista CC‑mottagare följer en liknande process som att lista direkta mottagare, vilket ger dig tillgång till ytterligare e‑postadresser som finns i CC‑fältet.

**Implementeringssteg**

1. **Hämta och iterera**  
   Använd `EmailContent`‑objektet från tidigare:  
   ```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### Lista alla BCC‑mottagare av ett e‑postmeddelande

**Översikt**  
Även om BCC‑mottagare inte syns i e‑posthuvudet, kan du ändå hämta dem med hjälp av GroupDocs.Watermark.

**Implementeringssteg**

1. **Åtkomst och visa BCC‑adresser**  
   ```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Praktiska tillämpningar

Dessa funktioner kan integreras i olika system, såsom:

- **Email Management Systems:** Automatisera kategorisering och bearbetning av e‑post baserat på mottagarlistor.  
- **Data Analysis Tools:** Extrahera mottagardata för analys för att identifiera kommunikationsmönster inom en organisation.  
- **Security Software:** Övervaka e‑posttrafik för att upptäcka obehörig delning eller läckor.  

## Prestandaöverväganden

När du hanterar stora volymer e‑post, överväg dessa tips:

- **Optimera resursanvändning:** Stäng `Watermarker`‑objektet omedelbart efter användning.  
- **Memory Management:** Var medveten om Javas skräpsamling och minnesanvändning när du bearbetar flera filer.  
- **Batch Processing:** Hantera e‑post i batcher för att minska belastningen på systemresurser.  

## Vanliga frågor

**Q: Hur hanterar jag fel under e‑postparsning?**  
A: Se till att dina filsökvägar är korrekta, att filerna följer förväntade format, och omslut din kod i try‑catch‑block för att fånga `IOException` eller `GroupDocsException`.

**Q: Kan jag använda detta bibliotek med andra e‑postformat som .eml?**  
A: Ja, GroupDocs.Watermark stöder olika e‑postformat. Kontrollera dokumentationen för format‑specifika laddningsalternativ.

**Q: Vilka är vanliga fallgropar när man listar mottagare?**  
A: Felaktiga filsökvägar, filtyper som inte stöds, eller att glömma att stänga `Watermarker`‑instansen kan leda till resursläckor.

**Q: Hur kan jag förbättra prestanda när jag parsar många e‑postmeddelanden?**  
A: Bearbeta filer parallellt med Javas `ExecutorService`, men övervaka CPU‑ och minnesanvändning för att undvika överbelastning.

**Q: Var kan jag få hjälp om jag stöter på problem?**  
A: Besök [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/watermark/10) för gemenskapsstöd och officiell support.

## Ytterligare resurser

- **Documentation:** [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download:** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  

## Slutsats

Du har nu lärt dig hur du **list email recipients java** effektivt med hjälp av GroupDocs.Watermark för Java. Detta kraftfulla verktyg kan effektivisera dina e‑posthanteringsprocesser och öppna nya möjligheter för dataanalys och automatisering.

**Nästa steg**

- Utforska fler funktioner i [GroupDocs.Watermark API](https://docs.groupdocs.com/watermark/java/).  
- Integrera dessa kodsnuttar i större projekt eller batch‑bearbetningspipelines.  
- Experimentera med olika konfigurationer för att passa dina specifika behov.

---

**Last Updated:** 2026-01-03  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs