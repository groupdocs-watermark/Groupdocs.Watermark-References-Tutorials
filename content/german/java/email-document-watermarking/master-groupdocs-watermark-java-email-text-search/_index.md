---
date: '2026-04-07'
description: Erfahren Sie, wie Sie den E-Mail-Text in Java mit GroupDocs.Watermark
  durchsuchen, einschließlich der Suche nach mehreren Schlüsselwörtern in E-Mails
  und dem Entfernen von E-Mail-Wasserzeichen.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'E-Mail-Text in Java mit GroupDocs.Watermark durchsuchen: Ein umfassender Leitfaden'
type: docs
url: /de/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# E-Mail-Textkörper Java mit GroupDocs.Watermark durchsuchen

Wenn Sie **search email body java** schnell und zuverlässig durchführen möchten, sind Sie hier genau richtig. In diesem Tutorial zeigen wir, wie GroupDocs.Watermark für Java es Ihnen ermöglicht, bestimmten Text in E‑Mail‑Betreffzeilen, HTML‑Bodies und Klartext‑Bodies zu finden und anschließend unerwünschte Wasserzeichen zu entfernen. Am Ende können Sie eine robuste Lösung implementieren, die mit einzelnen oder mehreren Schlüsselwörtern arbeitet und bei Bedarf E‑Mail‑Wasserzeichen entfernt.

## Schnelle Antworten
- **Was bedeutet “search email body java”?** Es bezieht sich auf die Verwendung von Java‑Code (mit GroupDocs.Watermark), um Text im Inhalt einer E‑Mail zu finden.  
- **Kann ich mehrere Schlüsselwörter gleichzeitig in E‑Mails suchen?** Ja – erstellen Sie separate `SearchCriteria`‑Objekte und kombinieren Sie diese.  
- **Wie entferne ich E‑Mail‑Wasserzeichen?** Verwenden Sie nach einer Suche die Methode `PossibleWatermarkCollection.clear()`.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion reicht für Tests; für den Produktionseinsatz ist eine permanente Lizenz erforderlich.  
- **Welche IDE ist am besten geeignet?** IntelliJ IDEA oder Eclipse werden beide vollständig unterstützt.

## Was Sie lernen werden
- Installation und Konfiguration von GroupDocs.Watermark für Java.  
- Einrichtung von Suchkriterien, um **search email body java** in Betreffzeilen und Bodies zu durchsuchen.  
- Techniken für **search multiple keywords email** in einem einzigen Durchlauf.  
- Die genauen Schritte, **how to remove email watermarks** nach deren Auffindung.  

## Warum E‑Mail‑Textkörper Java mit GroupDocs.Watermark durchsuchen?
GroupDocs.Watermark bietet eine High‑Level‑API, die die Komplexität des Parsens von .msg‑Dateien, der Handhabung verschiedener Body‑Formate und der Verwaltung von Wasserzeichen abstrahiert. Das spart Zeit im Vergleich zum Aufbau eines eigenen Parsers und sorgt für konsistente Ergebnisse bei großen E‑Mail‑Stapelungen.

## Voraussetzungen
- Java Development Kit (JDK) 8 oder neuer.  
- Maven (oder die Möglichkeit, JAR‑Dateien manuell hinzuzufügen).  
- Grundlegende Kenntnisse in Java und E‑Mail‑Dateiformaten (.msg, .eml).  

## GroupDocs.Watermark für Java einrichten
GroupDocs.Watermark für Java vereinfacht das Hinzufügen von Wasserzeichen und die Textsuche in Dokumenten, einschließlich E‑Mails. Im Folgenden finden Sie die beiden gängigsten Methoden, die Bibliothek zu Ihrem Projekt hinzuzufügen.

### Maven‑Einrichtung
Fügen Sie das Folgende in Ihre `pom.xml`‑Datei ein, um GroupDocs.Watermark als Abhängigkeit hinzuzufügen:
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
Alternativ können Sie die neueste Version direkt von [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) herunterladen.

### Schritte zum Lizenzieren
- **Kostenlose Testversion:** Beginnen Sie mit einer kostenlosen Testversion, um grundlegende Funktionen zu testen.  
- **Temporäre Lizenz:** Erhalten Sie eine temporäre Lizenz für erweiterten Zugriff und Tests.  
- **Kauf:** Ziehen Sie einen Kauf in Betracht, wenn GroupDocs.Watermark Ihren Anforderungen entspricht.

#### Grundlegende Initialisierung
Initialisieren Sie die Klasse `Watermarker` wie unten gezeigt:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Implementierungs‑Leitfaden

### Feature 1: Text im E‑Mail‑Body suchen
Dieses Feature ermöglicht das Suchen von bestimmtem Text im Betreff und Body einer E‑Mail.

#### Überblick
Wir zeigen, wie Sie GroupDocs.Watermark konfigurieren, um verschiedene Teile einer E‑Mail‑Nachricht mit Java‑Code zu durchsuchen.

##### Schritt 1: Dokumentpfade definieren
Richten Sie Ihre Eingabe‑ und Ausgabe‑Pfade für die Verarbeitung von E‑Mails ein:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Schritt 2: Ladeoptionen und Watermarker einrichten
Initialisieren Sie `EmailLoadOptions` und `Watermarker`, um mit Ihrem E‑Mail‑Dokument zu arbeiten.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Schritt 3: Suchkriterien erstellen
Definieren Sie Kriterien für die Textsuche. Wir verwenden eine case‑insensitive Suche nach dem Schlüsselwort **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Schritt 4: Suchorte festlegen
Konfigurieren Sie die Suche, sodass sowohl Betreff als auch Body von E‑Mails durchsucht werden:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Schritt 5: Suche ausführen und Wasserzeichen entfernen
Führen Sie die Suche durch und entfernen Sie gefundene Wasserzeichen:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Schritt 6: Änderungen speichern
Speichern Sie nach der Verarbeitung Ihre Änderungen in einem neuen Dokument:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Tipps zur Fehlersuche
- **Häufiges Problem:** Wenn die Suchergebnisse leer sind, stellen Sie sicher, dass der Text im E‑Mail‑Body oder Betreff vorhanden ist.  
- **Performance‑Tipp:** Optimieren Sie, indem Sie die Suche auf nur die tatsächlich benötigten Abschnitte beschränken.

### Feature 2: Optionen zum Laden von E‑Mail‑Dokumenten
Dieser Abschnitt beschreibt, wie Sie zusätzliche Optionen beim Laden eines E‑Mail‑Dokuments für die Verarbeitung mit GroupDocs.Watermark festlegen können.

#### Überblick
Durch das Konfigurieren von Ladeoptionen erhalten Sie mehr Kontrolle darüber, wie Dokumente behandelt werden, z. B. das Festlegen von Passwortschutz oder Kodierungseinstellungen.

##### Schritt 1: Ladeoptionen konfigurieren
Hier ein einfaches Setup für `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Wichtige Konfigurationsoptionen
- **Passwortschutz:** Geben Sie Passwörter an, wenn Ihre E‑Mails verschlüsselt sind.  
- **Kodierungseinstellungen:** Definieren Sie bei Bedarf spezifische Kodierungstypen.

## Wie man mehrere Schlüsselwörter in E‑Mails sucht
Wenn Sie mehrere Begriffe in einem Durchlauf finden möchten, erstellen Sie mehrere `SearchCriteria`‑Objekte und kombinieren Sie sie mit logischen **OR**‑ oder **AND**‑Operatoren. Die API ermöglicht das Ketten von Kriterien, sodass Sie nach „invoice“ **oder** „receipt“ suchen können, ohne separate Schleifen auszuführen.

## Wie man E‑Mail‑Wasserzeichen entfernt
Nachdem Sie Wasserzeichen (oder beliebigen Text, der Ihren Kriterien entspricht) gefunden haben, entfernt die Methode `PossibleWatermarkCollection.clear()` diese aus dem E‑Mail‑Dokument. Dies ist exakt der Schritt, den wir in **Schritt 5** oben verwendet haben, und er funktioniert für jede Anzahl von Treffern.

## Praktische Anwendungsfälle

### Anwendungsfall 1: Automatisierte E‑Mail‑Verarbeitung
Automatisieren Sie das Filtern und Verarbeiten großer E‑Mail‑Datenmengen, um spezifische Inhalte effizient zu finden.

### Anwendungsfall 2: Rechtliche Compliance‑Prüfungen
Stellen Sie die Einhaltung sicher, indem Sie nach sensiblen Informationen in Unternehmens‑E‑Mails suchen.

### Anwendungsfall 3: Kunden‑Support‑Automatisierung
Optimieren Sie Support‑Workflows, indem Sie Schlüsselwörter oder Phrasen in Kundenanfragen schnell lokalisieren.

## Leistungsüberlegungen
Bei der Verwendung von GroupDocs.Watermark sollten Sie Folgendes beachten, um die Leistung zu optimieren:

- **Ressourcenmanagement:** Verwalten Sie Speicher und Rechenleistung effizient, um große E‑Mail‑Datensätze zu verarbeiten.  
- **Best Practices für Java‑Speicherverwaltung:** Überwachen Sie regelmäßig den Ressourcenverbrauch und geben Sie Ressourcen zeitnah frei.

## Häufig gestellte Fragen

**F:** Wie gehe ich mit verschlüsselten E‑Mails in GroupDocs.Watermark um?  
**A:** Verwenden Sie `EmailLoadOptions`, um Passwörter beim Initialisieren des `Watermarker` anzugeben.

**F:** Kann ich mehrere Schlüsselwörter gleichzeitig suchen?  
**A:** Ja, erstellen Sie separate `SearchCriteria`‑Instanzen und kombinieren Sie sie mit logischen Operationen.

**F:** Ist GroupDocs.Watermark für Java kostenlos nutzbar?  
**A:** Eine kostenlose Testversion ist verfügbar; für erweiterte Funktionen sollten Sie eine Lizenz erwerben.

**F:** Wie verarbeite ich große Mengen an E‑Mails effizient?  
**A:** Optimieren Sie Ihre Suchen, indem Sie gezielt bestimmte E‑Mail‑Abschnitte anvisieren und Ressourcen effektiv verwalten.

**F:** Wo finde ich weitere Hilfe oder Support?  
**A:** Besuchen Sie das [GroupDocs‑Forum](https://forum.groupdocs.com/c/watermark/10) für Community‑Support oder kontaktieren Sie den kostenlosen Support‑Kanal.

## Ressourcen
- **Dokumentation:** Detaillierte Anleitungen finden Sie unter [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API‑Referenz:** Technische Details erhalten Sie unter [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Zuletzt aktualisiert:** 2026-04-07  
**Getestet mit:** GroupDocs.Watermark 24.11 für Java  
**Autor:** GroupDocs