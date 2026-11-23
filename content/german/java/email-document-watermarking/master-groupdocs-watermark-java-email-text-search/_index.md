---
date: '2025-12-31'
description: Erfahren Sie, wie Sie E-Mail-Text mit GroupDocs.Watermark für Java durchsuchen
  und Inhalte, Betreffzeilen sowie Anhänge effizient verwalten.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Wie man E‑Mail‑Text mit GroupDocs.Watermark Java durchsucht – ein umfassender
  Leitfaden
type: docs
url: /de/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Wie man E‑Mail‑Text mit GroupDocs.Watermark Java durchsucht

Das Auffinden einer bestimmten Phrase im Betreff, Textkörper oder Anhang einer E‑Mail kann mühsam sein – besonders wenn Sie Dutzende oder Hunderte von Nachrichten verarbeiten. In diesem Tutorial erfahren Sie, **wie man E‑Mail‑Inhalte** schnell und präzise mit **GroupDocs.Watermark für Java** durchsucht. Wir führen Sie durch Einrichtung, Code und bewährte Tipps, damit Sie die E‑Mail‑Textsuche sicher in Ihre eigenen Anwendungen integrieren können.

## Schnelle Antworten
- **Welche Bibliothek ermöglicht das Durchsuchen von E‑Mail‑Text in Java?** GroupDocs.Watermark für Java.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion funktioniert für Tests; für den Produktionseinsatz ist eine kostenpflichtige Lizenz erforderlich.  
- **Kann ich sowohl Betreff als auch Textkörper durchsuchen?** Ja – konfigurieren Sie `EmailSearchableObjects`, um Subject, HtmlBody und PlainTextBody einzuschließen.  
- **Ist die API groß‑/kleinschreibungssensitiv?** Sie können eine case‑insensitive Suche wählen, indem Sie das entsprechende Flag in `TextSearchCriteria` setzen.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher; Maven wird für das Abhängigkeitsmanagement empfohlen.

## Was bedeutet „E‑Mail‑Suche“ mit GroupDocs.Watermark?
GroupDocs.Watermark bietet eine einheitliche API zum Auffinden, Entfernen oder Modifizieren von Wasserzeichen und Klartext in vielen Dokumenttypen – einschließlich **E‑Mail‑Nachrichten** (`.msg`, `.eml`). Durch die Nutzung des Modells für durchsuchbare Objekte können Sie exakt die Teile einer E‑Mail anvisieren, die Sie interessieren, wodurch die Massenverarbeitung schnell und zuverlässig wird.

## Warum GroupDocs.Watermark Java für die E‑Mail‑Suche verwenden?
- **Einheitliche API** – Arbeitet mit PDFs, Bildern, Office‑Dateien und E‑Mails unter Verwendung derselben Code‑Muster.  
- **Leistungsoptimiert** – Suchvorgänge laufen im Speicher, ohne externe Dienste zu benötigen.  
- **Robuste Handhabung** – Unterstützt HTML‑ und Klartext‑Körper, Anhänge und sogar passwortgeschützte E‑Mails.  
- **Einfache Integration** – Maven/Gradle‑bereit, mit klarer Dokumentation und aktivem Support.

## Voraussetzungen
- **Java Development Kit (JDK)** 8 oder neuer.  
- **Maven** (oder Gradle) für das Abhängigkeitsmanagement.  
- Eine IDE wie **IntelliJ IDEA** oder **Eclipse**.  
- Grundlegende Kenntnisse der Java‑Syntax und von E‑Mail‑Dateiformaten (`.msg`, `.eml`).

## Einrichtung von GroupDocs.Watermark für Java

### Maven‑Einrichtung
Fügen Sie das Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

### Direkter Download
Alternativ können Sie das neueste JAR von [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) herunterladen.

### Lizenzbeschaffung
- **Kostenlose Testversion:** Kernfunktionen ohne Lizenzschlüssel testen.  
- **Temporäre Lizenz:** Fordern Sie einen zeitlich begrenzten Schlüssel für eine erweiterte Evaluierung an.  
- **Kostenpflichtige Lizenz:** Für uneingeschränkten Produktionseinsatz erwerben.

#### Grundlegende Initialisierung
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementierungs‑Leitfaden

### Feature 1: Text im E‑Mail‑Körper suchen

#### Überblick
Wir konfigurieren die API, um den **Betreff**, **HTML‑Körper** und **Klartext‑Körper** einer E‑Mail nach einem angegebenen Schlüsselwort zu durchsuchen.

#### Schritt 1: Dokumentpfade definieren
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Schritt 2: Ladeoptionen und Watermarker einrichten
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Schritt 3: Suchkriterien erstellen
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Schritt 4: Suchorte festlegen
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Schritt 5: Suche ausführen und Wasserzeichen entfernen
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Schritt 6: Änderungen speichern
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tipps zur Fehlersuche
- **Leere Ergebnisse:** Stellen Sie sicher, dass das Schlüsselwort tatsächlich in den ausgewählten E‑Mail‑Teilen vorkommt.  
- **Performance:** Beschränken Sie die durchsuchbaren Objekte auf das, was Sie benötigen (z. B. Subject + PlainTextBody), um große Stapel zu beschleunigen.

### Feature 2: Optionen zum Laden von E‑Mail‑Dokumenten

#### Überblick
`EmailLoadOptions` ermöglicht die Kontrolle darüber, wie die E‑Mail geparst wird – nützlich für verschlüsselte Nachrichten oder benutzerdefinierte Codierungen.

#### Schritt 1: Ladeoptionen konfigurieren
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Wichtige Konfigurationsoptionen
- **Passwortschutz:** Setzen Sie `loadOptions.setPassword("yourPassword")` für verschlüsselte `.msg`‑Dateien.  
- **Kodierungseinstellungen:** Passen Sie `loadOptions.setEncoding(Charset.forName("UTF-8"))` an, wenn Sie mit nicht‑standardmäßigen Zeichensätzen arbeiten.

## Praktische Anwendungen
- **Automatisierte E‑Mail‑Verarbeitung:** Stapelweise eingehende Support‑Tickets nach Schlüsselwörtern wie „refund“ oder „error“ scannen.  
- **Prüfungen zur rechtlichen Konformität:** Schnell vertrauliche Begriffe (z. B. SSN, Kreditkartennummern) in Unternehmens‑Mail‑Archiven finden.  
- **Automatisierung des Kundensupports:** E‑Mails basierend auf erkannten Phrasen an das richtige Support‑Team weiterleiten.

## Leistungsüberlegungen
- **Ressourcenverwaltung:** Rufen Sie `watermarker.close()` auf, sobald Sie die Verarbeitung abgeschlossen haben, um native Ressourcen freizugeben.  
- **Speicher‑Best Practices:** Bei der Verarbeitung von Tausenden von Nachrichten verarbeiten Sie diese in Stapeln und verwenden Sie nach Möglichkeit die `Watermarker`‑Instanz erneut.

## Fazit
Sie haben nun einen soliden, produktionsbereiten Ansatz, um **E‑Mail‑Inhalte** mit GroupDocs.Watermark Java zu durchsuchen. Die Flexibilität der API ermöglicht es Ihnen, bestimmte Teile einer E‑Mail zu adressieren, unerwünschte Wasserzeichen zu entfernen und die Logik in größere Workflows zu integrieren.

### Nächste Schritte
- Experimentieren Sie mit **mehreren Suchkriterien** (z. B. „invoice“ + „overdue“ kombinieren).  
- Erkunden Sie **das Hinzufügen von Wasserzeichen**, um E‑Mails mit sensiblen Daten zu kennzeichnen.  
- Tauchen Sie in andere Dokumenttypen (PDF, DOCX) ein, indem Sie denselben Watermarker‑Workflow verwenden.

## Häufig gestellte Fragen

**Q1:** Wie kann ich verschlüsselte E‑Mails mit GroupDocs.Watermark verarbeiten?  
**A1:** Verwenden Sie `EmailLoadOptions.setPassword("yourPassword")`, bevor Sie die `Watermarker`‑Instanz erstellen.

**Q2:** Kann ich mehrere Schlüsselwörter gleichzeitig suchen?  
**A2:** Ja – erstellen Sie separate `SearchCriteria`‑Objekte für jedes Schlüsselwort und kombinieren Sie sie mit logischen Operatoren (z. B. `OrSearchCriteria`).

**Q3:** Ist GroupDocs.Watermark Java kostenlos nutzbar?  
**A3:** Eine kostenlose Testversion steht für die Evaluierung zur Verfügung. Für den Produktionseinsatz ist eine kostenpflichtige Lizenz erforderlich.

**Q4:** Wie gehe ich effizient mit großen Mengen an E‑Mails um?  
**A4:** Beschränken Sie die durchsuchbaren Objekte auf das Notwendige, verarbeiten Sie E‑Mails in Stapeln und schließen Sie stets den `Watermarker`, um Ressourcen freizugeben.

**Q5:** Wo finde ich weitere Hilfe oder Support?  
**A5:** Besuchen Sie das [GroupDocs‑Forum](https://forum.groupdocs.com/c/watermark/10) für Community‑Unterstützung oder kontaktieren Sie den GroupDocs‑Support direkt.

## Ressourcen
- **Dokumentation:** Detaillierte Anleitungen finden Sie unter [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API‑Referenz:** Technische Details erhalten Sie unter [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Zuletzt aktualisiert:** 2025-12-31  
**Getestet mit:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

---