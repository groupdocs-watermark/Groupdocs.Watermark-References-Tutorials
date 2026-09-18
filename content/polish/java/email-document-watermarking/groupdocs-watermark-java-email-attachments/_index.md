---
date: '2025-12-29'
description: Dowiedz się, jak dodać znak wodny do załączników e‑mail przy użyciu GroupDocs.Watermark
  dla Javy. Ten przewodnik zawiera instrukcje krok po kroku oraz najlepsze praktyki.
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: Dodaj znak wodny do załączników e‑mail przy użyciu GroupDocs.Watermark dla
  Javy
type: docs
url: /pl/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Dodaj znak wodny do załączników e‑mail przy użyciu GroupDocs.Watermark dla Javy

W dzisiejszym cyfrowym krajobrazie ochrona wrażliwych informacji jest kluczowa — szczególnie gdy **dodajesz znak wodny do e‑mail** przed ich opuszczeniem skrzynki odbiorczej. Niezależnie od tego, czy jesteś programistą chcącym zwiększyć bezpieczeństwo dokumentów, czy firmą, która chce oznaczyć każdy wychodzący plik, ten poradnik pokaże, jak używać GroupDocs.Watermark dla Javy do nakładania znaków wodnych tekstowych na wszystkie obsługiwane załączniki w wiadomości e‑mail.

## Szybkie odpowiedzi
- **Co osiąga „dodawanie znaku wodnego do e‑mail”?** Wstawia widoczną lub półprzezroczystą etykietę (np. „Poufne”) do każdego obsługiwanego załącznika, zniechęcając do nieautoryzowanego rozpowszechniania.  
- **Jakiej biblioteki wymaga?** GroupDocs.Watermark for Java (najnowsze wydanie).  
- **Czy potrzebna jest licencja?** Licencja próbna działa w fazie rozwoju; licencja komercyjna jest wymagana w produkcji.  
- **Czy mogę przetwarzać wiele e‑maili jednocześnie?** Tak — otocz kroki pętlą przetwarzającą folder z plikami *.msg*.  
- **Jakie typy plików są obsługiwane?** PDF‑y, Word, Excel, PowerPoint, obrazy i wiele innych (zobacz oficjalną dokumentację).

## Co to jest „dodawanie znaku wodnego do e‑mail”?
Dodawanie znaku wodnego do e‑mail oznacza programowe otwieranie pliku e‑mail, wyodrębnianie każdego załącznika i nanoszenie niestandardowego tekstu (lub obrazu) na te dokumenty przed wysłaniem lub zapisaniem wiadomości. Dzięki temu znak wodny podąża za plikiem, wzmacniając poufność i tożsamość marki.

## Dlaczego warto używać GroupDocs.Watermark dla Javy?
- **Szerokie wsparcie formatów** — działa z PDF‑ami, plikami Office, obrazami i innymi.  
- **Proste API** — kilka linii kodu pozwala tworzyć, nakładać i zapisywać znaki wodne.  
- **Skoncentrowane na wydajności** — małe zużycie pamięci, idealne do przetwarzania po stronie serwera.  
- **Licencjonowanie gotowe dla przedsiębiorstw** — wersja próbna do oceny, płatna licencja do produkcji.

## Wymagania wstępne
- Zainstalowany Java Development Kit (JDK).  
- IDE, takie jak IntelliJ IDEA lub Eclipse.  
- GroupDocs.Watermark for Java dodany do projektu (zobacz kroki konfiguracji poniżej).

## Konfiguracja GroupDocs.Watermark dla Javy

### Konfiguracja Maven
Jeśli używasz Maven, dodaj repozytorium i zależność do swojego `pom.xml`:

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

### Bezpośrednie pobranie
Alternatywnie, pobierz najnowszą wersję z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Uzyskanie licencji
- Aby uzyskać darmową wersję próbną, zarejestruj się na stronie GroupDocs i poproś o tymczasową licencję.  
- W przypadku komercyjnego użycia, zakup pełną licencję. Odwiedź [stronę zakupu](https://purchase.groupdocs.com/temporary-license/) po więcej informacji.

### Podstawowa inicjalizacja
Zaimportuj podstawowe klasy, których będziesz potrzebować:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Jak dodać znak wodny do załączników e‑mail — przewodnik krok po kroku

### Krok 1: Utwórz znak wodny tekstowy
Najpierw zdefiniuj tekst znaku wodnego oraz jego wygląd.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Krok 2: Skonfiguruj opcje ładowania e‑mail
Skonfiguruj loader, aby GroupDocs mógł odczytać plik *.msg*.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Krok 3: Zainicjalizuj Watermarker dla pliku e‑mail
Wskaż `Watermarker` na e‑mail, który chcesz przetworzyć.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Krok 4: Pobierz zawartość e‑mail
Pobierz wewnętrzną strukturę e‑mail, aby móc pracować z jego załącznikami.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Krok 5: Iteruj po załącznikach
Iteruj po każdym załączniku i sprawdź, czy można na nim nałożyć znak wodny.

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
Dla każdego kwalifikującego się pliku otwórz go za pomocą nowego `Watermarker`, zastosuj znak wodny i zapisz zmiany z powrotem do e‑mail.

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

### Krok 10: Zapisz e‑mail z nałożonym znakiem wodnym
Zapisz zmodyfikowany e‑mail do nowego pliku, aby oryginał pozostał niezmieniony.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Krok 11: Sprzątanie
Zwolnij zasoby, zamykając główny `Watermarker`.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Praktyczne zastosowania
1. **Wewnętrzne udostępnianie dokumentów** — osadź branding firmy lub informacje o poufności w każdym załączniku przed wewnętrzną dystrybucją.  
2. **Komunikacja z klientami** — zabezpiecz umowy, propozycje i sprawozdania finansowe wyraźną etykietą „Poufne”.  
3. **Kampanie e‑mail marketingowe** — dodaj subtelne znaki wodne z brandingiem do PDF‑ów lub obrazów dołączonych do wiadomości promocyjnych, wzmacniając rozpoznawalność marki.

## Rozważania dotyczące wydajności
- **Zarządzanie pamięcią** — przetwarzaj jeden załącznik na raz i niezwłocznie zamykaj każdy `Watermarker`.  
- **Rozmiar załącznika** — duże pliki wydłużają czas przetwarzania; rozważ kompresję lub ograniczenie rozmiaru przed nałożeniem znaku wodnego.  
- **Przetwarzanie wsadowe** — iteruj po katalogu z plikami *.msg*, aby rozłożyć narzut przy obsłudze wielu e‑maili.

## Najczęściej zadawane pytania

**P: Czy mogę dodać znaki wodne do zaszyfrowanych plików?**  
O: Nie. GroupDocs.Watermark nie obsługuje znaków wodnych w zaszyfrowanych dokumentach ze względów bezpieczeństwa.

**P: Jakie typy plików są obsługiwane do znakowania?**  
O: PDF‑y, Word, Excel, PowerPoint, obrazy (PNG, JPEG, BMP) i wiele innych popularnych formatów. Zobacz oficjalną dokumentację po pełną listę.

**P: Jak mogę dostosować wygląd mojego znaku wodnego?**  
O: Możesz zmienić rodzinę czcionki, rozmiar, kolor, przezroczystość, obrót i pozycję przy użyciu konstruktora `TextWatermark` oraz jego właściwości.

**P: Czy przetwarzanie wsadowe wielu e‑maili jest możliwe?**  
O: Tak. Otocz kroki pętlą `for`, która iteruje po folderze z plikami *.msg* i zastosuj tę samą logikę do każdego.

**P: Mój znak wodny się nie wyświetla — co sprawdzić?**  
O: Zweryfikuj, czy typ pliku załącznika jest obsługiwany, upewnij się, że rozmiar znaku wodnego pasuje do wymiarów strony oraz że dokument nie jest chroniony hasłem.

## Zasoby
- [Dokumentacja](https://docs.groupdocs.com/watermark/java/)
- [Referencja API](https://reference.groupdocs.com/watermark/java)
- [Pobierz GroupDocs.Watermark dla Javy](https://releases.groupdocs.com/watermark/java/)

---

**Ostatnia aktualizacja:** 2025-12-29  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs