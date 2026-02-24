---
date: '2026-02-24'
description: Lär dig hur du hämtar sidor, hämtar dokumentinformation och får filtypen
  java med GroupDocs.Watermark för Java. Följ vår steg‑för‑steg‑guide med kodexempel.
keywords:
- retrieve document information Java
- GroupDocs Watermark Java setup
- Java document info retrieval
title: Hur du hämtar sidor och hämtar dokumentinformation med GroupDocs.Watermark
  för Java
type: docs
url: /sv/java/document-information/retrieve-document-info-groupdocs-watermark-java/
weight: 1
---

# Så får du sidor och hämtar dokumentinformation med GroupDocs.Watermark för Java

Att extrahera dokumentmetadata—**hur man får sidor**, filtyp, storlek och mer—är ett vanligt krav när man bygger dokument‑centrerade Java‑applikationer. I den här handledningen kommer du att se exakt hur man får sidor och annan användbar information med **GroupDocs.Watermark för Java**. Vi går igenom installation, kod och praktiska tips så att du kan börja läsa dokumentmetadata omedelbart.

## Snabba svar
- **Hur får man sidor?** Använd `watermarker.getDocumentInfo().getPageCount()`.
- **Hur får man filtyp i Java?** Anropa `info.getFileType()` på `IDocumentInfo`‑objektet.
- **Kan jag läsa dokumentets storlek?** Ja—`info.getSize()` returnerar storleken i byte.
- **Behöver jag en licens?** En gratis provperiod eller tillfällig licens fungerar för utveckling; en full licens krävs för produktion.
- **Stöds Maven?** Absolut—lägg till GroupDocs‑arkivet och beroendet i din `pom.xml`.

## Vad är extrahering av dokumentinformation?

Extrahering av dokumentinformation innebär att programmässigt läsa ett fils metadata (typ, sidantal, storlek osv.) utan att öppna det för redigering. Dessa data hjälper dig att fatta beslut som routning, validering eller batch‑behandling.

## Varför använda GroupDocs.Watermark för Java?

GroupDocs.Watermark lägger inte bara till vattenstämplar utan erbjuder också ett lättviktigt API för **läsa dokumentmetadata**. Det stöder dussintals format (DOCX, PDF, PPTX osv.) och fungerar på Java 8+.

## Förutsättningar

- **GroupDocs.Watermark for Java** ≥ 24.11  
- JDK 8 eller högre  
- Maven (eller manuell JAR‑nedladdning)  
- Grundläggande kunskap om Java I/O  

## Installera GroupDocs.Watermark för Java

Du kan integrera biblioteket via Maven eller genom att ladda ner JAR‑filen direkt.

**Maven‑konfiguration**

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

**Direktnedladdning**

Alternativt kan du ladda ner den senaste versionen från [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Licensanskaffning

1. Besök [GroupDocs Purchase page](https://purchase.groupdocs.com/temporary-license/) för att begära en tillfällig licens.  
2. Följ dokumentationen för att tillämpa licensfilen i ditt projekt.

## Grundläggande initiering

```java
import com.groupdocs.watermark.Watermarker;
import java.io.FileInputStream;

// Initialize FileInputStream with your document path
FileInputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source.docx");

// Create a Watermarker instance
Watermarker watermarker = new Watermarker(stream);
```

## Så får du sidor med GroupDocs.Watermark för Java

Nedan följer en kort, steg‑för‑steg‑genomgång som visar **hur man får sidor** och annan metadata.

### Steg 1: Öppna filströmmen

```java
import java.io.FileInputStream;

// Open the FileStream for the input document
FileInputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source.docx");
```

*Varför detta steg?* Det ger API:et en referens till den fysiska filen så att den kan läsa dess egenskaper.

### Steg 2: Initiera Watermarker‑objektet

```java
import com.groupdocs.watermark.Watermarker;

// Initialize a Watermarker with the file stream
Watermarker watermarker = new Watermarker(stream);
```

*Viktigt tips:* Verifiera att filvägen är korrekt och att applikationen har läsbehörighet.

### Steg 3: Hämta dokumentinformation

```java
import com.groupdocs.watermark.common.IDocumentInfo;

// Get document information
IDocumentInfo info = watermarker.getDocumentInfo();
```

Detta anrop returnerar ett `IDocumentInfo`‑objekt som innehåller all metadata du behöver.

### Steg 4: Hämta specifika detaljer (Hur man får filtyp i Java)

```java
System.out.println("File type: " + info.getFileType());
System.out.println("Number of pages: " + info.getPageCount());
System.out.println("Document size: " + info.getSize() + " bytes");
```

- **Filtyp** (`info.getFileType()`) visar om dokumentet är DOCX, PDF osv.  
- **Antal sidor** (`info.getPageCount()`) är svaret på **hur man får sidor**.  
- **Storlek** (`info.getSize()`) returnerar filens storlek i byte, användbart för lagringsberäkningar.

### Steg 5: Stäng resurser

```java
// Always close the Watermarker and FileInputStream
watermarker.close();
stream.close();
```

Stängning frigör inhemska resurser och förhindrar minnesläckor, vilket är särskilt viktigt vid bearbetning av många filer.

## Vanliga användningsfall för extrahering av dokumentinformation

1. **Dokumenthanteringssystem** – Auto‑kategorisera filer efter typ eller sidantal.  
2. **Förbehandlingsvalidering** – Avvisa filer som överskrider en sidgräns innan vattenstämpling.  
3. **Efterlevnadsrevisioner** – Logga metadata för regulatorisk rapportering.  
4. **Batch‑pipelines** – Skanna snabbt en mapp med dokument för att avgöra vilka som behöver vidare bearbetning.  
5. **Molnintegration** – Validera storleksgränser innan uppladdning till lagringstjänster.

## Prestandaöverväganden

- **Strömma effektivt:** Använd `FileInputStream` (som visas) istället för att ladda hela filen i minnet.  
- **Avsluta snabbt:** Anropa alltid `close()` på `Watermarker` och strömmar.  
- **Parallell bearbetning:** För stora batcher, överväg Java:s `ExecutorService` för att hantera flera dokument samtidigt.

## Felsökning & vanliga fallgropar

| Issue | Reason | Fix |
|-------|--------|-----|
| `FileNotFoundException` | Felaktig sökväg eller saknad fil | Verifiera den absoluta/relativa sökvägen och filbehörigheterna |
| `UnsupportedFormatException` | Dokumentformatet stöds inte | Kontrollera listan över stödda format i GroupDocs‑dokumentationen |
| Memory spikes on large PDFs | Laddar hela dokumentet i minnet | Håll dig till den ström‑baserade metoden och stäng objekt omedelbart |

## Vanliga frågor

**Q: Vilka filtyper stöds för extrahering av dokumentinformation?**  
A: GroupDocs.Watermark stöder DOCX, PDF, PPTX, XLSX och många fler vanliga format.

**Q: Hur kan jag hämta ytterligare metadata såsom författare eller skapelsedatum?**  
A: Använd andra egenskaper på `IDocumentInfo`‑objektet, t.ex. `info.getAuthor()` eller `info.getCreationDate()`.

**Q: Fungerar denna metod med krypterade eller lösenordsskyddade filer?**  
A: Ja—ange lösenordet när du initierar `Watermarker` (se API‑dokumentationen för detaljer).

**Q: Kan jag bearbeta tusentals filer utan att få slut på minne?**  
A: Absolut, så länge du stänger varje `Watermarker` och ström efter att ha bearbetat varje fil.

**Q: Finns det ett sätt att få sidantalet utan att ladda hela dokumentet?**  
A: `getPageCount()`‑anropet läser bara den nödvändiga headerinformationen, så det är lättviktigt.

## Resurser

- **Dokumentation**: [GroupDocs Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API‑referens**: [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **Nedladdning**: [GroupDocs Watermark Downloads](https://releases.groupdocs.com/watermark/java/)  
- **GitHub‑arkiv**: [GroupDocs Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Gratis support**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Tillfällig licens**: [Get a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Senast uppdaterad:** 2026-02-24  
**Testat med:** GroupDocs.Watermark 24.11 för Java  
**Författare:** GroupDocs  

---