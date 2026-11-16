---
date: '2026-01-21'
description: Lär dig hur du ställer in licens för GroupDocs Watermark i Java, inklusive
  hur du applicerar vattenstämpel på PDF och hanterar användning med en mätlicens.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Hur man ställer in licens för GroupDocs Watermark (Mätad) i Java
type: docs
url: /sv/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Så ställer du in licens för GroupDocs Watermark (Metered) i Java

Att skydda immateriella rättigheter är en högsta prioritet för moderna företag, och vattenmärken är ett beprövat sätt att göra det. I den här handledningen lär du dig **hur du ställer in licens** för GroupDocs.Watermark med en metered‑metod, så att du kan **applicera vattenmärke pdf**‑filer samtidigt som du behåller full kontroll över användningen. Vi går igenom allt från förutsättningar till verkliga användningsscenarier och visar exakt var du **använder offentliga privata nycklar** för att aktivera licensen.

## Snabba svar
- **Vad är en metered-licens?** En användningsbaserad licensmodell som spårar varje API‑anrop.  
- **Behöver jag en licensfil?** Nej – du aktiverar med offentliga och privata nycklar.  
- **Vilken Java‑version krävs?** Java 8 eller högre.  
- **Kan jag lägga till vattenmärke i pdf‑dokument?** Ja, API‑et stöder PDF, DOCX, PPTX och bilder.  
- **Är den här metoden säker?** Ja, nycklarna överförs via HTTPS och lagras aldrig i klartext.

## Vad är en Metered‑licens och varför använda den?
En metered‑licens låter dig betala för det du faktiskt konsumerar, vilket gör den idealisk för SaaS‑ eller mikrotjänstarkitekturer. Den erbjuder **document security watermark**‑funktioner utan den extra bördan av att hantera traditionella licensfiler, och du kan skala din användning upp eller ner omedelbart.

## Förutsättningar
1. **GroupDocs.Watermark for Java** ≥ 24.11 (den senaste versionen).  
2. **JDK 8+** installerad och `JAVA_HOME` konfigurerad.  
3. **Offentliga och privata nycklar** hämtade från ditt GroupDocs‑konto (du kommer att använda dem i koden).  

## Konfigurera GroupDocs.Watermark för Java

### Installationsinformation
Integrera GroupDocs.Watermark i ditt Maven‑projekt:

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

> **Tips:** Samma repository‑URL används också för alternativet för direktnedladdning nedan.

#### Direktnedladdning
Hämta den senaste JAR‑filen från den officiella releasesidan: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licensförvärv
För att låsa upp premiumfunktioner behöver du en tillfällig eller provlicens. Registrera dig på [GroupDocs webbplats](https://purchase.groupdocs.com/temporary-license/) och kopiera de offentliga/privata nycklarna som de tillhandahåller.

### Grundläggande initiering
När biblioteket finns på din classpath kan du initiera det:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **Varför detta är viktigt:** Även när du använder en metered‑licens säkerställer initiering av `License`‑objektet att SDK‑et är redo att ta emot nyckelbaserad aktivering senare i arbetsflödet.

## Implementeringsguide

### Ställa in en metered‑licens

#### Steg 1: Definiera de offentliga och privata nycklarna
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
Dessa nycklar **använder offentliga privata nycklar** för att säkert identifiera ditt konto.

#### Steg 2: Skapa en instans av Metered‑klassen
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
`Metered`‑klassen hanterar all användningsspårning i bakgrunden.

#### Steg 3: Ställ in den metered‑licensen med de angivna nycklarna
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
Efter detta anrop är SDK‑et fullt licensierat och du kan börja **lägga till vattenmärke pdf**‑filer eller **skapa vattenmärkta dokument**.

### Varför använda offentliga/privata nycklar istället för en licensfil?
- **Säkerhet:** Nycklarna skrivs aldrig till disk i klartext.  
- **Flexibilitet:** Byt miljöer (dev, test, prod) utan att kopiera filer.  
- **Skalbarhet:** Perfekt för molnbaser containrar äröränderliga.

## Praktiska tillämpningar

1. **Document Security:** Bädda in ett synligt eller osynligt vattenmärke i PDF‑filer för att avskräcka obehörig distribution.  
2. **Usage Tracking:** Övervaka hur många dokument som bearbetas varje månad, vilket hjälper dig att hålla dig inom din metered‑kvot.  
3. **CMS Integration:** Automatisk **apply watermark pdf** till varje uppladdad fil i ett content management‑system.

## Prestandaöverväganden

- **Apply watermark only when needed** footprint low lös‑check that there are no extra spaces or line‑breaks in the strings. |
| License not activated | Ensure you called `metered.setMeteredKey(...)` **before** any watermark operation. |
| Out‑of‑memory errors on big PDFs | Use `WatermarkOptions.setUseMemoryCache |

## Vanliga frågor

**Q: Vad är enanrop, vilket låter dig betala endast för faktisk användning och enkelt skala din applikation.

**Q: Kan jag växla mellan en provlicensfil och en metered‑nyckel?**  
A: Japath/to/file.lic")` för provlicensen, och ersätt den senare med `metered.setMeteredKey(...)`.

**Q: har med** JPEG, PNG, BMP och andra vanliga bildformat.

## Resurser

- [Dokumentation](https://docs.groupdocs.com/watermark/java/)
- [API‑referens](https://reference.groupdocs.com/watermark/java)
- [Nedladdning](https://releases.groupdocs.com/watermark/java/)
- [GitHub‑arkiv](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Gratis supportforum](https://forum.group10)
- [Tillfällig licensförvärv](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:**