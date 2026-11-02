---
date: '2025-12-31'
description: Dowiedz się, jak wyszukiwać tekst w wiadomościach e‑mail przy użyciu
  GroupDocs.Watermark dla Javy, efektywnie zarządzać treścią, tematami i załącznikami.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Jak wyszukiwać tekst e‑maili w GroupDocs.Watermark Java – kompleksowy przewodnik
type: docs
url: /pl/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Jak wyszukiwać tekst w e-mailach przy użyciu GroupDocs.Watermark Java

Znajdowanie konkretnej frazy w temacie, treści lub załącznikach e‑maila może być uciążliwe — szczególnie gdy obsługujesz dziesiątki lub setki wiadomości. W tym samouczku dowiesz się, **jak wyszukiwać treść e‑maili** szybko i dokładnie przy użyciu **GroupDocs.Watermark for Java**. Przeprowadzimy Cię przez konfigurację, kod oraz wskazówki najlepszych praktyk, abyś mógł z pewnością zintegrować wyszukiwanie tekstu w e‑mailach w swoich aplikacjach.

## Szybkie odpowiedzi
- **Jakiej biblioteki użyć do wyszukiwania tekstu w e‑mailach w Javie?** GroupDocs.Watermark for Java.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa do testów; licencja płatna jest wymagana w środowisku produkcyjnym.  
- **Czy mogę przeszukiwać zarówno temat, jak i treść?** Tak — skonfiguruj `EmailSearchableObjects`, aby uwzględnić Subject, HtmlBody i PlainTextBody.  
- **Czy API jest wrażliwe na wielkość liter?** Możesz wybrać wyszukiwanie nie uwzględniające wielkości liter, ustawiając odpowiedni flag w `TextSearchCriteria`.  
- **Jakiej wersji Javy wymaga biblioteka?** JDK 8 lub wyższa; zalecany jest Maven do zarządzania zależnościami.

## Co to jest „jak wyszukiwać e‑mail” z GroupDocs.Watermark?
GroupDocs.Watermark udostępnia zunifikowane API do lokalizowania, usuwania lub modyfikowania znaków wodnych oraz zwykłego tekstu w wielu typach dokumentów — w tym **wiadomościach e‑mail** (`.msg`, `.eml`). Dzięki modelowi obiektów wyszukiwalnych możesz precyzyjnie określić, które części e‑maila Cię interesują, co przyspiesza i ułatwia przetwarzanie wsadowe.

## Dlaczego warto używać GroupDocs.Watermark Java do wyszukiwania w e‑mailach?
- **Zunifikowane API** – Działa z PDF‑ami, obrazami, plikami Office i e‑mailami przy użyciu tych samych wzorców kodu.  
- **Optymalizacja wydajności** – Operacje wyszukiwania odbywają się w pamięci, bez potrzeby zewnętrznych usług.  
- **Solidna obsługa** – Obsługuje ciała HTML i tekstowe, załączniki oraz nawet e‑maile zabezpieczone hasłem.  
- **Łatwa integracja** – Gotowe do użycia w Maven/Gradle, z przejrzystą dokumentacją i aktywnym wsparciem.

## Wymagania wstępne

- **Java Development Kit (JDK)** 8 lub nowszy.  
- **Maven** (lub Gradle) do zarządzania zależnościami.  
- IDE, takie jak **IntelliJ IDEA** lub **Eclipse**.  
- Podstawowa znajomość składni Javy oraz formatów plików e‑mail (`.msg`, `.eml`).

## Konfiguracja GroupDocs.Watermark dla Javy

### Konfiguracja Maven
Dodaj repozytorium i zależność do swojego `pom.xml`:

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
Alternatywnie możesz pobrać najnowszy plik JAR z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Uzyskanie licencji
- **Darmowa wersja próbna:** Testuj podstawowe funkcje bez klucza licencyjnego.  
- **Licencja tymczasowa:** Poproś o klucz ograniczony czasowo do rozszerzonej oceny.  
- **Licencja płatna:** Zakup na nieograniczone użycie w produkcji.

#### Podstawowa inicjalizacja
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Przewodnik implementacji

### Funkcja 1: Wyszukiwanie tekstu w treści e‑maila

#### Przegląd
Skonfigurujemy API, aby przeszukiwało **temat**, **ciało HTML** oraz **ciało tekstowe** e‑maila pod kątem podanego słowa kluczowego.

#### Krok 1: Definicja ścieżek dokumentów
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Krok 2: Ustawienie opcji ładowania i Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Krok 3: Utworzenie kryteriów wyszukiwania
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Krok 4: Określenie miejsc wyszukiwania
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Krok 5: Wykonanie wyszukiwania i usunięcie znaków wodnych
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Krok 6: Zapisanie zmian
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Wskazówki rozwiązywania problemów
- **Puste wyniki:** Upewnij się, że słowo kluczowe rzeczywiście występuje w wybranych częściach e‑maila.  
- **Wydajność:** Ogranicz obiekty wyszukiwalne tylko do potrzebnych (np. Subject + PlainTextBody), aby przyspieszyć przetwarzanie dużych partii.

### Funkcja 2: Opcje ładowania dokumentu e‑mail

#### Przegląd
`EmailLoadOptions` pozwala kontrolować sposób parsowania e‑maila — przydatne przy wiadomościach zaszyfrowanych lub niestandardowych kodowaniach.

#### Krok 1: Konfiguracja opcji ładowania
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Kluczowe opcje konfiguracji
- **Ochrona hasłem:** Ustaw `loadOptions.setPassword("yourPassword")` dla zaszyfrowanych plików `.msg`.  
- **Ustawienia kodowania:** Dostosuj `loadOptions.setEncoding(Charset.forName("UTF-8"))` przy pracy z nietypowymi zestawami znaków.

## Praktyczne zastosowania

- **Automatyczne przetwarzanie e‑maili:** Masowe skanowanie przychodzących zgłoszeń wsparcia pod kątem słów kluczowych takich jak „refund” czy „error”.  
- **Kontrole zgodności prawnej:** Szybkie znajdowanie poufnych terminów (np. SSN, numery kart kredytowych) w archiwach firmowej poczty.  
- **Automatyzacja obsługi klienta:** Kierowanie e‑maili na podstawie wykrytych fraz do odpowiednich zespołów wsparcia.

## Rozważania dotyczące wydajności
- **Zarządzanie zasobami:** Wywołaj `watermarker.close()` natychmiast po zakończeniu przetwarzania, aby zwolnić zasoby natywne.  
- **Najlepsze praktyki pamięciowe:** Przy obsłudze tysięcy wiadomości przetwarzaj je w partiach i, w miarę możliwości, ponownie używaj instancji `Watermarker`.

## Podsumowanie
Masz już solidne, gotowe do produkcji podejście do **wyszukiwania treści w e‑mailach** przy użyciu GroupDocs.Watermark Java. Elastyczność API pozwala celować w konkretne części wiadomości, usuwać niechciane znaki wodne i włączać logikę do większych przepływów pracy.

### Kolejne kroki
- Eksperymentuj z **wieloma kryteriami wyszukiwania** (np. połączenie „invoice” + „overdue”).  
- Zbadaj **dodawanie znaków wodnych**, aby oznaczyć e‑maile zawierające wrażliwe dane.  
- Zagłęb się w inne typy dokumentów (PDF, DOCX) używając tego samego workflow Watermarker.

## Najczęściej zadawane pytania

**Q1:** Jak obsłużyć zaszyfrowane e‑maile przy użyciu GroupDocs.Watermark?  
**A1:** Użyj `EmailLoadOptions.setPassword("yourPassword")` przed utworzeniem instancji `Watermarker`.

**Q2:** Czy mogę wyszukiwać wiele słów kluczowych jednocześnie?  
**A2:** Tak — utwórz osobne obiekty `SearchCriteria` dla każdego słowa i połącz je operatorami logicznymi (np. `OrSearchCriteria`).

**Q3:** Czy GroupDocs.Watermark Java jest darmowy?  
**A3:** Dostępna jest darmowa wersja próbna do oceny. Do użytku produkcyjnego wymagana jest licencja płatna.

**Q4:** Jak efektywnie obsługiwać duże wolumeny e‑maili?  
**A4:** Ogranicz obiekty wyszukiwalne do niezbędnych, przetwarzaj wiadomości w partiach i zawsze zamykaj `Watermarker`, aby zwolnić zasoby.

**Q5:** Gdzie mogę znaleźć dodatkową pomoc lub wsparcie?  
**A5:** Odwiedź [forum GroupDocs](https://forum.groupdocs.com/c/watermark/10) w celu uzyskania pomocy społeczności lub skontaktuj się bezpośrednio z zespołem wsparcia GroupDocs.

## Zasoby
- **Dokumentacja:** Szczegółowe przewodniki znajdziesz pod adresem [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Referencja API:** Szczegóły techniczne dostępne są pod adresem [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Ostatnia aktualizacja:** 2025-12-31  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

---