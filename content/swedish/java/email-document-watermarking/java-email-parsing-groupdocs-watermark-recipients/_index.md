---
date: '2026-06-16'
description: Lär dig hur du med Java kan parse msg-fil och automatiskt lista mottagarna
  To, CC och BCC med GroupDocs.Watermark för Java. Denna handledning visar hur du
  parse e‑post effektivt.
keywords:
- java parse msg file
- how to parse email
- how to read msg
- retrieve email recipients
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to java parse msg file and automatically list To, CC, and
    BCC recipients using GroupDocs.Watermark for Java. This tutorial shows how to
    parse email efficiently.
  headline: 'Java Parse MSG File: List Recipients with GroupDocs.Watermark'
  type: TechArticle
- description: Learn how to java parse msg file and automatically list To, CC, and
    BCC recipients using GroupDocs.Watermark for Java. This tutorial shows how to
    parse email efficiently.
  name: 'Java Parse MSG File: List Recipients with GroupDocs.Watermark'
  steps:
  - name: Add the Maven Dependency
    text: Add the GroupDocs.Watermark Maven coordinates to your `pom.xml`. This brings
      in all required JARs automatically. Alternatively, download the latest version
      from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).
  - name: Import Required Classes
    text: The `Watermarker` class loads an email document, while `EmailContent` provides
      access to its metadata such as recipients.
  - name: Define the Email Path and Load Options
    text: '`LoadOptions` configures how the file is opened, allowing settings like
      password protection.'
  - name: Open the Document with Resource Management
    text: Using try‑with‑resources ensures the `Watermarker` instance is automatically
      closed.
  - name: Retrieve Direct (To) Recipients
    text: The `EmailContent.getTo()` method returns a list of primary recipient objects.
  - name: List CC Recipients
    text: The `EmailContent.getCc()` method returns a list of carbon‑copy recipient
      objects.
  - name: List BCC Recipients
    text: The `EmailContent.getBcc()` method returns a list of blind‑carbon‑copy recipient
      objects.
  - name: Clean Up
    text: '`watermarker.close()` releases native resources and file handles.'
  type: HowTo
- questions:
  - answer: Use `LoadOptions.setPassword("yourPassword")` before opening the document;
      the API will decrypt the content automatically.
    question: How do I handle encrypted .msg files?
  - answer: Yes—`EmailContent.getBody()` returns the plain‑text or HTML body, which
      you can combine with recipient data for full‑message exports.
    question: Can I extract the email body together with recipients?
  - answer: Absolutely. GroupDocs.Watermark is designed for high‑throughput scenarios;
      just ensure you manage thread pools and close each `Watermarker` instance promptly.
    question: Is it possible to process thousands of emails in one run?
  - answer: It is fully cross‑platform; the same Maven dependency runs on Windows,
      macOS, and Linux Docker images.
    question: Does the library work on Linux containers?
  - answer: The official documentation and API reference contain deeper use‑cases,
      such as watermarking attachments or extracting embedded images.
    question: Where can I find more advanced examples?
  type: FAQPage
title: 'Java Parse MSG-fil: Lista mottagare med GroupDocs.Watermark'
type: docs
url: /sv/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Java Parsning av MSG-fil: Lista mottagare med GroupDocs.Watermark

Att extrahera varje Till-, CC- och BCC-adress från ett `.msg` e‑postmeddelande kan vara tidskrävande när du har hundratals filer. **Java parse msg file** låter dig automatisera detta steg, eliminerar manuellt kopiera‑och‑klistra och minskar mänskliga fel. I den här handledningen lär du dig hur du konfigurerar GroupDocs.Watermark för Java, laddar ett e‑postdokument och hämtar alla mottagarlistor snabbt och pålitligt.

## Snabba svar
- **Vad täcker handledningen?** Laddar en .msg‑fil med GroupDocs.Watermark och extraherar Till-, CC- och BCC-adresser.  
- **Vilket bibliotek krävs?** GroupDocs.Watermark för Java (v24.11 eller senare).  
- **Behöver jag en licens?** En gratis provversion fungerar för testning; en betald licens behövs för produktion.  
- **Kan jag parsra andra format?** Ja – samma API stödjer också .eml och andra e‑posttyper.  
- **Vilken Java-version stöds?** JDK 8 eller nyare.

## Vad är java parse msg file?
Uttrycket **java parse msg file** avser att använda Java‑kod för att läsa Microsoft Outlook `.msg`‑filer och extrahera deras strukturerade data. Denna process gör det möjligt för utvecklare att programatiskt komma åt e‑postmetadata, brödtext och mottagarlistor utan manuell inspektion. Den stödjer även batch‑bearbetning, hanterar Unicode‑tecken och bevarar bilagor, vilket gör den lämplig för företags‑skala e‑postanalys.

## Varför använda GroupDocs.Watermark för e‑postparsning?
GroupDocs.Watermark bearbetar **200 + e‑postformat** och kan hantera filer upp till **500 MB** utan att ladda hela dokumentet i minnet, vilket ger upp till **3× snabbare** extraktion jämfört med generiska fil‑läsningsmetoder. Dess dedikerade `EmailContent`‑API abstraherar den komplexa .msg‑strukturen och ger pålitlig åtkomst till Till-, CC- och BCC‑fält med bara några rader Java‑kod.

## Förutsättningar

- **Java Development Kit (JDK):** 8 eller högre.  
- **IDE:** IntelliJ IDEA, Eclipse eller någon Java‑kompatibel editor.  
- **Byggverktyg:** Maven (rekommenderas) eller manuell JAR‑inkludering.  
- **GroupDocs.Watermark för Java:** version 24.11 (eller nyare).  
- **Grundläggande Java‑kunskaper** och bekantskap med e‑postfilformat.

## Hur man parsar msg‑fil med Java och listar mottagare?
Ladda .msg‑filen med `Watermarker`‑klassen, hämta ett `EmailContent`‑objekt och iterera genom dess mottagarsamlingar. Detta korta svar‑avsnitt förklarar kärnstegen på under 70 ord: **Instansiera `Watermarker` med filsökvägen, anropa `getEmailContent()` för att få åtkomst till mottagarsamlingarna, och loopa sedan genom `getTo()`, `getCc()` och `getBcc()` för att skriva ut varje adress.** API‑et hanterar all parsning internt, så du behöver aldrig själv tolka den råa MIME‑strukturen.

### Steg 1: Lägg till Maven‑beroendet
Lägg till GroupDocs.Watermark Maven‑koordinater i din `pom.xml`. Detta hämtar automatiskt alla nödvändiga JAR‑filer.

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

Alternativt kan du ladda ner den senaste versionen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Steg 2: Importera nödvändiga klasser
`Watermarker`‑klassen laddar ett e‑postdokument, medan `EmailContent` ger åtkomst till dess metadata såsom mottagare.

```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```

### Steg 3: Definiera e‑postens sökväg och laddningsalternativ
`LoadOptions` konfigurerar hur filen öppnas och möjliggör inställningar som lösenordsskydd.

```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```

### Steg 4: Öppna dokumentet med resurshantering
Genom att använda try‑with‑resources försäras du om att `Watermarker`‑instansen stängs automatiskt.

```java
   watermarker.close();
   ```

### Steg 5: Hämta direkta (Till) mottagare
Metoden `EmailContent.getTo()` returnerar en lista med primära mottagarobjekt.

```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```

### Steg 6: Lista CC‑mottagare
Metoden `EmailContent.getCc()` returnerar en lista med kopiamottagarobjekt.

```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### Steg 7: Lista BCC‑mottagare
Metoden `EmailContent.getBcc()` returnerar en lista med blindkopiamottagarobjekt.

```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### Steg 8: Rensa upp
`watermarker.close()` frigör inhemska resurser och filhandtag.

```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Praktiska tillämpningar

- **E‑posthanteringssystem:** Kategorisera automatiskt inkommande e‑post genom att extrahera mottagargrupper.  
- **Efterlevnadsgranskning:** Generera rapporter över alla BCC‑mottagare för att upptäcka potentiella dataläckor.  
- **Customer Relationship Management (CRM):** Synkronisera To/CC‑listor med kontaktdatabaser för riktade utskick.  
- **Säkerhetsövervakning:** Skanna stora e‑postarkiv för oväntade externa mottagare.

## Prestandaöverväganden

- **Batch‑behandling:** Bearbeta e‑post i parallella strömmar (t.ex. `java.util.concurrent.ForkJoinPool`) för att maximera CPU‑användning samtidigt som minnesgränser respekteras.  
- **Minnesavtryck:** Biblioteket strömmar fildata; du kan säkert parsra filer upp till **500 MB** utan OOM‑fel.  
- **Resursrensning:** Stäng alltid `Watermarker`‑objektet; att misslyckas kan lämna fil‑lås på Windows‑system.

## Vanliga problem och lösningar

- **Ogiltig filsökväg:** Verifiera att sökvägen använder framåtsnedstreck (`/`) eller escapade bakåtsnedstreck (`\\`) på Windows.  
- **Ej stödd format:** Säkerställ att filen är en äkta Outlook `.msg` eller `.eml`; andra format kräver andra laddare.  
- **Licensutgång:** En provlicens löper ut efter 30 dagar; ersätt den med en produktionsnyckel för att undvika `LicenseException`.  

## Vanliga frågor

**Q: Hur hanterar jag krypterade .msg‑filer?**  
A: Använd `LoadOptions.setPassword("yourPassword")` innan du öppnar dokumentet; API‑et dekrypterar innehållet automatiskt.

**Q: Kan jag extrahera e‑postens brödtext tillsammans med mottagare?**  
A: Ja—`EmailContent.getBody()` returnerar vanlig text eller HTML‑brödtext, som du kan kombinera med mottagaruppgifter för fullständiga meddelandeexport.

**Q: Är det möjligt att bearbeta tusentals e‑postmeddelanden i ett kör?**  
A: Absolut. GroupDocs.Watermark är designat för hög genomströmning; se bara till att hantera trådpools och stäng varje `Watermarker`‑instans i tid.

**Q: Fungerar biblioteket i Linux‑behållare?**  
A: Det är helt plattformsoberoende; samma Maven‑beroende körs på Windows, macOS och Linux‑Docker‑bilder.

**Q: Var kan jag hitta mer avancerade exempel?**  
A: Den officiella dokumentationen och API‑referensen innehåller djupare användningsfall, såsom vattenmärkning av bilagor eller extrahering av inbäddade bilder.

## Ytterligare resurser
- **Dokumentation:** [GroupDocs Watermark Java-dokumentation](https://docs.groupdocs.com/watermark/java/)  
- **API‑referens:** [GroupDocs API‑referens](https://reference.groupdocs.com/watermark/java)  
- **GroupDocs.Watermark API:** [GroupDocs.Watermark API](https://docs.groupdocs.com/watermark/java/)  
- **Nedladdningar:** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  
- **Support‑forum:** [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  

---

**Senast uppdaterad:** 2026-06-16  
**Testad med:** GroupDocs.Watermark Java 24.11  
**Författare:** GroupDocs

## Relaterade handledningar

- [E‑postdokumentvattenmärkning i Java: Mästarhantering med GroupDocs.Watermark](/watermark/java/email-document-watermarking/groupdocs-watermark-java-email-management/)
- [Hur man extraherar PDF‑bilagor med GroupDocs Watermark i Java för e‑postdokumenthantering](/watermark/java/email-document-watermarking/extract-pdf-attachments-groupdocs-java/)
- [Effektiv borttagning av e‑postbilagor med GroupDocs.Watermark i Java](/watermark/java/email-document-watermarking/remove-email-attachments-groupdocs-watermark-java/)