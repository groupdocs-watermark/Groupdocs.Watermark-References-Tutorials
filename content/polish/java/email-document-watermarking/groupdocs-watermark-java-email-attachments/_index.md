---
date: '2026-04-07'
description: Dowiedz się, jak tworzyć znak wodny z tekstem dla załączników e‑mail
  przy użyciu GroupDocs.Watermark dla Javy, zabezpieczając załączniki e‑mail i chroniąc
  poufne dane.
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: Utwórz znak wodny tekstowy dla załączników e‑mail przy użyciu GroupDocs Java
type: docs
url: /pl/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Jak dodać znaki wodne do załączników e‑mail przy użyciu GroupDocs.Watermark dla Javy

W tym samouczku **utworzysz obiekty znaków wodnych tekstowych** i zastosujesz je do każdego obsługiwanego załącznika w wiadomości e‑mail. Dodanie znaku wodnego to skuteczny sposób na **zabezpieczenie załączników e‑mail**, sygnalizowanie poufności i wzmocnienie tożsamości marki — wszystko przy użyciu kilku linii kodu Java.

## Wprowadzenie

Ochrona wrażliwych informacji przesyłanych pocztą elektroniczną jest ważniejsza niż kiedykolwiek. Niezależnie od tego, czy musisz oznaczyć wewnętrzne raporty, zaznaczyć umowy prawne, czy po prostu oznaczyć materiały marketingowe, znak wodny tekstowy zapewnia lekką, widoczną warstwę ochronną. Ten przewodnik przeprowadzi Cię przez cały proces użycia **GroupDocs.Watermark for Java** w celu dodania własnego znaku wodnego do każdego załącznika w pliku Outlook `.msg`.

### Czego się nauczysz
- Jak **utworzyć obiekty znaków wodnych tekstowych** z własnymi czcionkami i kolorami.  
- Krok po kroku integracja znakowania wodnego w przepływie przetwarzania e‑mail w Javie.  
- Wskazówki dotyczące optymalizacji wydajności przy obsłudze dużych załączników.  
- Scenariusze z rzeczywistego świata, w których znakowanie wodne załączników e‑mail dodaje wartości.

Sprawdźmy, czy masz wszystko, co potrzebne, zanim przejdziemy dalej.

## Szybkie odpowiedzi
- **Co oznacza „create text watermark”?** Oznacza to utworzenie obiektu `TextWatermark`, który definiuje widoczny tekst, czcionkę, rozmiar i styl nakładane na dokument.  
- **Czy mogę dodać znak wodny do zaszyfrowanych załączników?** Nie – GroupDocs.Watermark nie obsługuje zaszyfrowanych plików ze względów bezpieczeństwa.  
- **Jakie typy plików są obsługiwane?** PDF, Word, Excel, PowerPoint, obrazy i wiele innych – zobacz oficjalną dokumentację, aby uzyskać pełną listę.  
- **Czy potrzebna jest licencja?** Licencja próbna działa w fazie rozwoju; licencja komercyjna jest wymagana w środowisku produkcyjnym.  
- **Jak szybki jest proces?** Dodanie znaku wodnego do typowego załącznika o wielkości 2 MB zajmuje mniej niż sekundę na nowoczesnym sprzęcie.

## Wymagania wstępne

- **Java Development Kit (JDK)** – wersja 8 lub nowsza.  
- IDE, takie jak IntelliJ IDEA lub Eclipse.  
- **GroupDocs.Watermark for Java** dodany do projektu (zobacz kroki konfiguracji poniżej).  
- Dostęp do pliku e‑mail (`.msg`, `.eml` itp.), który zawiera załączniki, które chcesz zabezpieczyć.

## Konfiguracja GroupDocs.Watermark dla Javy

### Maven Setup

Jeśli zarządzasz zależnościami przy użyciu Maven, dodaj repozytorium i zależność do swojego `pom.xml`:

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

### Direct Download

Alternatywnie pobierz najnowszy plik JAR z oficjalnej strony:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Uzyskanie licencji
- **Trial:** Zarejestruj się na stronie GroupDocs i poproś o tymczasową licencję.  
- **Commercial:** Kup pełną licencję tutaj: [purchase page](https://purchase.groupdocs.com/temporary-license/).

### Basic Initialization

Zaimportuj podstawowe klasy, które będą potrzebne w pliku źródłowym Java:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Czym jest znak wodny tekstowy?

**Znak wodny tekstowy** to półprzezroczysty fragment tekstu, który jest renderowany na każdej stronie dokumentu. Dzięki GroupDocs.Watermark możesz kontrolować czcionkę, rozmiar, kolor, obrót i nieprzezroczystość, co daje pełną elastyczność w tworzeniu oznaczenia marki lub powiadomienia o poufności, które naturalnie komponuje się z oryginalną treścią.

## Dlaczego używać GroupDocs.Watermark do załączników e‑mail?

- **Zabezpiecz załączniki e‑mail** poprzez widoczne oznaczenie ich jako poufne.  
- **Utrzymaj spójność marki** we wszystkich wychodzących dokumentach.  
- **Przetwarzaj wsadowo** wiele e‑maili w jednej pętli, oszczędzając czas i redukując błędy ręczne.  
- **Obsługa wielu formatów** – ten sam kod działa dla PDF‑ów, plików Word, obrazów i innych.

## Przewodnik implementacji

Przejdziemy przez każdy krok, wyjaśniając *dlaczego* w kodzie, abyś mógł dostosować go do własnych projektów.

### Krok 1: Utwórz znak wodny tekstowy

Najpierw utwórz instancję `TextWatermark` z tekstem, który ma być wyświetlany, oraz żądanymi ustawieniami czcionki.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **Wskazówka:** Dostosuj rozmiar czcionki lub kolor, aby pasowały do wytycznych stylu korporacyjnego. Możesz także ustawić nieprzezroczystość za pomocą `watermark.setOpacity(0.5)`, jeśli potrzebujesz subtelniejszego efektu.

### Krok 2: Skonfiguruj opcje ładowania e‑mail

`EmailLoadOptions` informuje bibliotekę, jak interpretować przychodzący plik e‑mail.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Krok 3: Zainicjalizuj Watermarker dla pliku e‑mail

Wskaż konstruktorowi `Watermarker` plik `.msg` (lub `.eml`), który chcesz przetworzyć.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Krok 4: Pobierz zawartość e‑mail

Wyodrębnij wewnętrzną strukturę e‑maila, aby móc iterować po jego załącznikach.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Krok 5: Iteruj po załącznikach

Dla każdego załącznika weryfikujemy, czy typ pliku jest obsługiwany i czy nie jest zaszyfrowany.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Krok 6‑9: Dodaj znak wodny do obsługiwanych załączników

Wewnątrz warunkowego bloku tworzymy dedykowany `Watermarker` dla załącznika, nakładamy znak wodny, a następnie wprowadzamy zmodyfikowaną treść z powrotem do e‑maila.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Krok 10: Zapisz e‑mail ze znakiem wodnym

Zapisz zaktualizowany e‑mail do nowego pliku, aby oryginał pozostał niezmieniony.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Krok 11: Sprzątanie

Zawsze zwalniaj zasoby, aby uniknąć wycieków pamięci.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Typowe problemy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|-------|--------|-----|
| **Znak wodny niewidoczny** | Nieprzezroczystość ustawiona zbyt nisko lub kolor czcionki jest podobny do tła. | Zwiększ nieprzezroczystość (`watermark.setOpacity(0.7)`) lub wybierz kontrastowy kolor. |
| **Nieobsługiwany typ załącznika** | Format pliku nie znajduje się na liście obsługiwanej przez GroupDocs. | Najpierw skonwertuj plik do obsługiwanego formatu (np. PDF) lub pomiń go, logując komunikat. |
| **OutOfMemoryError przy dużych PDF‑ach** | Ładowanie bardzo dużych załączników zużywa zbyt dużo pamięci heap. | Zwiększ pamięć heap JVM (`-Xmx2g`) lub przetwarzaj załączniki w mniejszych partiach. |

## Najczęściej zadawane pytania

**Q: Czy mogę dodać znaki wodne do zaszyfrowanych plików?**  
A: Nie, GroupDocs.Watermark nie obsługuje dodawania znaków wodnych do zaszyfrowanych plików ze względu na ograniczenia bezpieczeństwa.

**Q: Jakie typy plików są obsługiwane do znakowania wodnego?**  
A: Obsługiwane typy to PDF‑y, dokumenty Word, arkusze Excel, prezentacje PowerPoint oraz popularne formaty obrazów. Zobacz oficjalną dokumentację, aby uzyskać pełną listę.

**Q: Jak dostosować wygląd mojego znaku wodnego?**  
A: Użyj klasy `Font`, aby ustawić rozmiar, styl i kolor, oraz wywołaj metody takie jak `setOpacity` i `setRotationAngle` na instancji `TextWatermark`.

**Q: Czy przetwarzanie wsadowe wielu e‑maili jest możliwe?**  
A: Tak. Owiń cały przepływ pracy w pętlę iterującą po plikach w katalogu, ponownie używając tej samej instancji `TextWatermark` dla wydajności.

**Q: Mój znak wodny jest obcięty na ostatniej stronie — co jest nie tak?**  
A: Upewnij się, że znak wodny mieści się w marginesach strony. Możesz dostosować jego pozycję za pomocą `watermark.setHorizontalAlignment` i `watermark.setVerticalAlignment`.

## Praktyczne zastosowania

1. **Wewnętrzne udostępnianie dokumentów:** Osadź branding firmy lub powiadomienia o poufności przed rozpowszechnianiem raportów w organizacji.  
2. **Komunikacja z klientami:** Oznacz umowy i propozycje jako „Poufne”, aby przypomnieć odbiorcom o politykach przetwarzania danych.  
3. **E‑mail marketing:** Dodaj subtelny znak wodny marki do promocyjnych PDF‑ów załączonych do newsletterów, wzmacniając rozpoznawalność marki bez zakłócania projektu.

## Rozważania dotyczące wydajności

- **Zarządzanie pamięcią:** Zamykaj każdy `attachedWatermarker` niezwłocznie (jak pokazano w Kroku 9), aby zwolnić zasoby natywne.  
- **Limity rozmiaru plików:** Dla załączników większych niż 10 MB rozważ strumieniowanie pliku lub zwiększenie rozmiaru heap JVM.  
- **Przetwarzanie równoległe:** Użyj `ExecutorService` Javy do jednoczesnego znakowania wielu e‑maili, ale monitoruj użycie CPU, aby uniknąć przeciążeń.

## Podsumowanie

Masz teraz kompletny, gotowy do produkcji przepis, jak **utworzyć obiekty znaków wodnych tekstowych** i zastosować je do każdego obsługiwanego załącznika w pliku e‑mail przy użyciu GroupDocs.Watermark dla Javy. Integrując ten przepływ pracy z istniejącym potokiem przetwarzania e‑maili, zwiększysz bezpieczeństwo dokumentów, wymusisz spójność marki i utrzymasz zgodność przy minimalnym nakładzie.

Gotowy na kolejny krok? Spróbuj rozszerzyć kod, aby przetwarzał cały folder plików `.msg`, lub zbadaj dodatkowe typy znaków wodnych, takie jak obrazy i kody QR.

---

**Ostatnia aktualizacja:** 2026-04-07  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

**Zasoby**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)