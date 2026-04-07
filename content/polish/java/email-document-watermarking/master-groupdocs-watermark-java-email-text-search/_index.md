---
date: '2026-04-07'
description: Dowiedz się, jak przeszukiwać treść e‑maili w Javie przy użyciu GroupDocs.Watermark,
  w tym jak wyszukiwać wiele słów kluczowych w e‑mailu oraz jak usuwać znaki wodne
  z e‑maili.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Wyszukiwanie treści e‑mail w Javie z GroupDocs.Watermark: Kompletny przewodnik'
type: docs
url: /pl/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Wyszukiwanie treści e‑mail w Java z GroupDocs.Watermark

Jeśli potrzebujesz **search email body java** szybko i niezawodnie, trafiłeś we właściwe miejsce. W tym samouczku pokażemy, jak GroupDocs.Watermark dla Javy pozwala zlokalizować określony tekst w tematach e‑maili, ciałach HTML i czystych tekstach, oraz jak później usunąć niechciane znaki wodne. Po zakończeniu będziesz w stanie wdrożyć solidne rozwiązanie działające na pojedynczych lub wielokrotnych słowach kluczowych i nawet usuwać znaki wodne e‑maili w razie potrzeby.

## Szybkie odpowiedzi
- **What does “search email body java” mean?** Oznacza użycie kodu Java (z GroupDocs.Watermark) do znajdowania tekstu w treści e‑maila.  
- **Can I search multiple keywords email at once?** Tak – utwórz osobne obiekty `SearchCriteria` i połącz je.  
- **How to remove email watermarks?** Użyj metody `PossibleWatermarkCollection.clear()` po wyszukiwaniu.  
- **Do I need a license?** Darmowa wersja próbna działa do testów; stała licencja jest wymagana w środowisku produkcyjnym.  
- **Which IDE works best?** IntelliJ IDEA lub Eclipse są w pełni obsługiwane.

## Czego się nauczysz
- Instalacja i konfiguracja GroupDocs.Watermark dla Javy.  
- Ustawianie kryteriów wyszukiwania **search email body java** w tematach i treściach.  
- Techniki **search multiple keywords email** w jednym przebiegu.  
- Dokładne kroki **how to remove email watermarks** po ich zlokalizowaniu.  

## Dlaczego wyszukiwać treść e‑mail w Java z GroupDocs.Watermark?
GroupDocs.Watermark oferuje wysokopoziomowe API, które ukrywa złożoność parsowania plików .msg, obsługi różnych formatów treści oraz zarządzania znakami wodnymi. To oszczędza czas w porównaniu do tworzenia własnego parsera i zapewnia spójne wyniki przy przetwarzaniu dużych partii e‑maili.

## Wymagania wstępne
- Java Development Kit (JDK) 8 lub nowszy.  
- Maven (lub możliwość ręcznego dodania plików JAR).  
- Podstawowa znajomość Javy oraz formatów plików e‑mail (.msg, .eml).  

## Konfiguracja GroupDocs.Watermark dla Javy
GroupDocs.Watermark dla Javy upraszcza dodawanie znaków wodnych i wyszukiwanie tekstu w dokumentach, w tym e‑mailach. Poniżej znajdują się dwa najczęstsze sposoby dodania biblioteki do projektu.

### Konfiguracja Maven
Umieść poniższy kod w pliku `pom.xml`, aby dodać GroupDocs.Watermark jako zależność:
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
Alternatywnie możesz pobrać najnowszą wersję bezpośrednio ze strony [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Kroki uzyskania licencji
- **Free Trial:** Rozpocznij od wersji próbnej, aby przetestować podstawowe funkcje.  
- **Temporary License:** Uzyskaj tymczasową licencję dla rozszerzonego dostępu i testów.  
- **Purchase:** Rozważ zakup, jeśli GroupDocs.Watermark spełnia Twoje potrzeby.

#### Podstawowa inicjalizacja
Zainicjalizuj klasę `Watermarker` jak pokazano poniżej:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Przewodnik implementacji

### Funkcja 1: Wyszukiwanie tekstu w treści e‑maila
Ta funkcja umożliwia wyszukiwanie określonego tekstu w temacie i treści e‑maila.

#### Przegląd
Pokażemy, jak skonfigurować GroupDocs.Watermark do przeszukiwania różnych części wiadomości e‑mail przy użyciu kodu Java.

##### Krok 1: Definiowanie ścieżek dokumentów
Ustaw ścieżki wejścia i wyjścia do obsługi e‑maili:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Krok 2: Konfiguracja opcji ładowania i Watermarker
Zainicjalizuj `EmailLoadOptions` oraz `Watermarker`, aby pracować z dokumentem e‑mail.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Krok 3: Tworzenie kryteriów wyszukiwania
Zdefiniuj kryteria wyszukiwania tekstu. Użyjemy wyszukiwania nieczułego na wielkość liter dla słowa kluczowego **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Krok 4: Określenie miejsc wyszukiwania
Skonfiguruj wyszukiwanie, aby obejmowało zarówno temat, jak i treść e‑maili:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Krok 5: Wykonanie wyszukiwania i usunięcie znaków wodnych
Wykonaj wyszukiwanie i usuń znalezione znaki wodne:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Krok 6: Zapisz zmiany
Po przetworzeniu zapisz zmiany do nowego dokumentu:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Porady rozwiązywania problemów
- **Common Issue:** Jeśli wyniki wyszukiwania są puste, upewnij się, że tekst znajduje się w treści lub temacie e‑maila.  
- **Performance Tip:** Optymalizuj, ograniczając wyszukiwanie tylko do potrzebnych sekcji.

### Funkcja 2: Opcje ładowania dokumentu e‑mail
Ta sekcja omawia, jak skonfigurować dodatkowe opcje przy ładowaniu dokumentu e‑mail do przetwarzania za pomocą GroupDocs.Watermark.

#### Przegląd
Konfiguracja opcji ładowania zapewnia większą kontrolę nad obsługą dokumentów, np. określenie ochrony hasłem lub ustawień kodowania.

##### Krok 1: Konfiguracja opcji ładowania
Oto podstawowa konfiguracja `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Kluczowe opcje konfiguracji
- **Password Protection:** Określ hasła, jeśli Twoje e‑maile są zaszyfrowane.  
- **Encoding Settings:** Zdefiniuj konkretne typy kodowania w razie potrzeby.

## Jak wyszukiwać wiele słów kluczowych w e‑mailu
Jeśli musisz znaleźć kilka terminów w jednym przebiegu, utwórz wiele obiektów `SearchCriteria` i połącz je przy użyciu logicznych operatorów **OR** lub **AND**. API pozwala łączyć kryteria, więc możesz wyszukać „invoice” **or** „receipt” bez uruchamiania oddzielnych pętli.

## Jak usunąć znaki wodne e‑maili
Po zlokalizowaniu znaków wodnych (lub dowolnego tekstu pasującego do kryteriów), metoda `PossibleWatermarkCollection.clear()` usuwa je z dokumentu e‑mail. To dokładny krok, którego użyliśmy w **Step 5** powyżej i działa dla dowolnej liczby dopasowań.

## Praktyczne zastosowania

### Przypadek użycia 1: Zautomatyzowane przetwarzanie e‑maili
Zautomatyzuj filtrowanie i przetwarzanie dużych ilości e‑maili, aby efektywnie znajdować określoną treść.

### Przypadek użycia 2: Kontrole zgodności prawnej
Zapewnij zgodność, wyszukując wrażliwe informacje w firmowych e‑mailach.

### Przypadek użycia 3: Automatyzacja wsparcia klienta
Usprawnij procesy wsparcia, szybko znajdując słowa kluczowe lub frazy w zapytaniach klientów.

## Rozważania dotyczące wydajności
Podczas korzystania z GroupDocs.Watermark, weź pod uwagę poniższe, aby zoptymalizować wydajność:
- **Resource Management:** Efektywnie zarządzaj pamięcią i mocą obliczeniową, aby obsługiwać duże zestawy danych e‑mail.  
- **Java Memory Management Best Practices:** Regularnie monitoruj zużycie zasobów i zwalniaj je niezwłocznie.

## Najczęściej zadawane pytania

**Q:** Jak mogę obsłużyć zaszyfrowane e‑maile za pomocą GroupDocs.Watermark?  
**A:** Użyj `EmailLoadOptions`, aby określić hasła przy inicjalizacji `Watermarker`.

**Q:** Czy mogę wyszukiwać wiele słów kluczowych jednocześnie?  
**A:** Tak, utwórz osobne instancje `SearchCriteria` i połącz je przy użyciu operacji logicznych.

**Q:** Czy GroupDocs.Watermark Java jest darmowy?  
**A:** Dostępna jest wersja próbna; rozważ zakup licencji dla rozszerzonych funkcji.

**Q:** Jak efektywnie obsługiwać duże wolumeny e‑maili?  
**A:** Optymalizuj wyszukiwania, celując w konkretne sekcje e‑maili i skutecznie zarządzając zasobami.

**Q:** Gdzie mogę znaleźć dodatkową pomoc lub wsparcie?  
**A:** Odwiedź [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) w celu uzyskania wsparcia społeczności lub skontaktuj się z ich bezpłatnym kanałem wsparcia.

## Zasoby
- **Documentation:** Przeglądaj szczegółowe przewodniki na [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Uzyskaj szczegóły techniczne na [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Last Updated:** 2026-04-07  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs