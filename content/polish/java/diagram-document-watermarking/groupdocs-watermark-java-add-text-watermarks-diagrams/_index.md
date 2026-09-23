---
date: '2025-12-19'
description: Dowiedz się, jak dodać znak wodny z tekstem do diagramów przy użyciu
  GroupDocs.Watermark dla Javy. Skutecznie zabezpiecz swoją treść wizualną i zapewnij
  integralność dokumentów.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: Dodaj znak wodny z tekstem do diagramów przy użyciu GroupDocs.Watermark dla
  Javy – Kompletny przewodnik
type: docs
url: /pl/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Dodaj znak wodny tekstowy do diagramów przy użyciu GroupDocs.Watermark dla Java: Kompletny przewodnik

## Wprowadzenie
Ochrona dokumentów diagramów przed nieautoryzowanym użyciem jest kluczowa, a **dodanie znaku wodnego tekstowego** zapewnia proste, a jednocześnie skuteczne rozwiązanie. W tym samouczku dowiesz się, jak wczytać pliki diagramów, stworzyć konfigurowalny znak wodny tekstowy oraz zastosować go do stron tła lub konkretnych kształtów przy użyciu **GroupDocs.Watermark for Java**. Po zakończeniu przewodnika będziesz w stanie zabezpieczyć swoje zasoby wizualne, zachowując oryginalny wygląd i odczucie.

### Szybkie odpowiedzi
- **Co oznacza „add text watermark”?**  
  Oznacza to osadzenie półprzezroczystej warstwy tekstowej w dokumencie w celu wskazania własności lub poufności.  
- **Która biblioteka obsługuje znakowanie diagramów?**  
  GroupDocs.Watermark for Java zapewnia natywną obsługę formatów diagramów (np. Visio, VSDX).  
- **Czy potrzebna jest licencja?**  
  Do użytku produkcyjnego wymagana jest tymczasowa lub pełna licencja; dostępna jest darmowa wersja próbna do oceny.  
- **Czy mogę umieścić znak wodny na stronach tła?**  
  Tak – użyj opcji `DiagramWatermarkPlacementType.SeparateBackgrounds` dla **znaku wodnego strony tła**.  
- **Czy kod jest kompatybilny z Java 8+?**  
  Zdecydowanie – biblioteka działa z JDK 8 i nowszymi.

## Co to jest znak wodny tekstowy dla diagramów?
Znak wodny tekstowy to fragment czytelnego tekstu (często półprzezroczysty), który jest renderowany nad lub pod elementami diagramu. Może być używany do budowania marki, ochrony praw autorskich lub oznaczania poufnych wersji roboczych.

## Dlaczego warto używać GroupDocs.Watermark dla Java?
- **Szerokie wsparcie formatów** – działa z Visio, VSDX i wieloma innymi typami diagramów.  
- **Precyzyjne rozmieszczenie** – wybierz znakowanie w pierwszym planie, tle lub konkretnym kształcie.  
- **Proste API** – twórz i stosuj znaki wodne za pomocą kilku linii kodu Java.  

## Prerequisites
- **GroupDocs.Watermark for Java** (v24.11 lub nowszy)  
- **Java Development Kit (JDK)** 8 lub wyższy  
- Maven (lub ręczne dołączenie JAR)

## Konfiguracja GroupDocs.Watermark dla Java
### Konfiguracja Maven
Dodaj następującą konfigurację do pliku `pom.xml`:

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
Download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Uzyskanie licencji
- **Free Trial** – oceń wszystkie funkcje bez klucza licencyjnego.  
- **Temporary License** – użyj podczas rozwoju, aby odblokować pełną funkcjonalność.  
- **Purchase** – uzyskaj licencję produkcyjną do projektów komercyjnych.  

### Podstawowa inicjalizacja i konfiguracja
Upewnij się, że następujące importy znajdują się w Twojej klasie Java:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Implementacja krok po kroku

### Krok 1: Wczytaj dokument diagramu
Najpierw wskaż bibliotece plik diagramu i zainicjalizuj opcje ładowania.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Wyjaśnienie*: `DiagramLoadOptions` pozwala kontrolować, jak diagram jest parsowany przed dodaniem znaku wodnego.

### Krok 2: Utwórz znak wodny tekstowy
Teraz utwórz tekst znaku wodnego i zdefiniuj jego styl wizualny.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Wyjaśnienie*: To tworzy `TextWatermark` z frazą **“Test watermark 1”** używając czcionki Calibri o rozmiarze 19.

### Krok 3: Skonfiguruj rozmieszczenie – znak wodny strony tła
Wybierz, gdzie ma się pojawić znak wodny. Dla **znaku wodnego strony tła**, użyj następującej opcji:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Wyjaśnienie*: `DiagramShapeWatermarkOptions` kontroluje dokładną lokalizację. Ustawienie typu rozmieszczenia na `SeparateBackgrounds` dodaje znak wodny do każdej strony tła diagramu.

### Krok 4: Zastosuj znak wodny i zapisz
Na koniec dodaj znak wodny do dokumentu, zapisz wynik i zwolnij zasoby.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Wyjaśnienie*: Metoda `add` stosuje skonfigurowany `textWatermark` przy użyciu opcji rozmieszczenia, a zmodyfikowany diagram jest zapisywany do `outputPath`.

## Praktyczne zastosowania
- **Ochrona własności intelektualnej** – Zapobiegaj wykorzystywaniu własnych diagramów przez konkurencję.  
- **Wzmacnianie marki** – Osadź nazwę firmy lub logo jako znak wodny tekstowy na wszystkich wyeksportowanych diagramach.  
- **Dokumentacja prawna** – Oznacz poufne wersje robocze schematów inżynieryjnych.  
- **Zgłoszenia akademickie** – Dodaj identyfikatory studentów lub kody kursów do diagramów w celu śledzenia plagiatu.

## Rozważania dotyczące wydajności
- **Zarządzanie pamięcią** – Zamknij instancję `Watermarker` (`watermarker.close()`), aby zwolnić zasoby natywne, szczególnie przy przetwarzaniu dużych plików.  
- **Przetwarzanie wsadowe** – Przejdź pętlą przez kolekcję ścieżek diagramów i w miarę możliwości ponownie użyj jednej instancji `Watermarker`, aby zmniejszyć narzut.  

## Typowe problemy i rozwiązania

| Problem | Rozwiązanie |
|-------|----------|
| **OutOfMemoryError przy dużych diagramach** | Zwiększ rozmiar sterty JVM (`-Xmx2g`) i przetwarzaj pliki pojedynczo. |
| **Znak wodny niewidoczny** | Upewnij się, że kolor znaku wodnego ma wystarczający kontrast; ustaw przezroczystość za pomocą `textWatermark.setOpacity(0.5)`. |
| **Nieobsługiwany format diagramu** | Sprawdź, czy format jest wymieniony w dokumentacji obsługiwanych formatów GroupDocs.Watermark. |

## Najczęściej zadawane pytania

**Q:** Jaki jest najlepszy rozmiar czcionki dla znaków wodnych?  
**A:** Optymalny rozmiar zależy od wymiarów diagramu; 12‑20 pt sprawdza się w większości przypadków.

**Q:** Czy mogę dostosować kolory znaku wodnego?  
**A:** Tak, użyj `textWatermark.setColor(Color.GRAY)` (lub dowolnego `java.awt.Color`).

**Q:** Jak obsłużyć duże partie dokumentów?  
**A:** Skorzystaj z API wsadowego biblioteki lub napisz pętlę, która ponownie używa obiektów `Watermarker`, aby zminimalizować narzut.

**Q:** Czy istnieją ograniczenia w GroupDocs.Watermark?  
**A:** Biblioteka obsługuje większość popularnych formatów diagramów, ale niektóre własnościowe rozszerzenia mogą nie być w pełni renderowane. Sprawdź [dokumentację](https://docs.groupdocs.com/watermark/java/) po szczegóły.

**Q:** Jak mogę uzyskać wsparcie w razie problemów?  
**A:** Odwiedź [Forum GroupDocs](https://forum.groupdocs.com/c/watermark/10) w celu uzyskania pomocy społeczności lub skontaktuj się bezpośrednio z wsparciem GroupDocs.

## Dodatkowe zasoby
- **Dokumentacja**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Referencja API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Pobierz**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Repozytorium GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Darmowe forum wsparcia**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Licencja tymczasowa**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**Ostatnia aktualizacja:** 2025-12-19  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

---