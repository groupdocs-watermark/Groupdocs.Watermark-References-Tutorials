---
date: '2026-02-13'
description: Poznaj sposób wyodrębniania kształtów oraz obrazu z kształtu przy użyciu
  GroupDocs.Watermark for Java, efektywnie uzyskując szczegółowe informacje o diagramie.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Jak wyodrębnić kształty z diagramów przy użyciu GroupDocs.Watermark w Javie
type: docs
url: /pl/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Jak wyodrębnić kształty z diagramów przy użyciu GroupDocs.Watermark w Javie

Kiedy potrzebujesz **jak wyodrębnić kształty** z diagramu w stylu Visio programowo, biblioteka GroupDocs.Watermark zapewnia czysty, Java‑pierwszy sposób na pobranie każdego szczegółu — wymiarów, pozycji, osadzonych obrazów i nawet tekstu wewnątrz każdego kształtu. W tym samouczku zobaczysz dokładnie **jak wyodrębnić kształty**, dlaczego ma to znaczenie oraz kod krok po kroku, który możesz skopiować do swojego projektu.

## Szybkie odpowiedzi
- **Jaka biblioteka obsługuje wyodrębnianie kształtów?** GroupDocs.Watermark for Java  
- **Która wersja Javy jest wymagana?** JDK 8 lub wyższa  
- **Czy mogę uzyskać dane obrazu z kształtu?** Tak – użyj `shape.getImage()`  
- **Czy tekst wewnątrz kształtu jest dostępny?** Absolutnie, poprzez `shape.getText()`  
- **Czy potrzebna jest licencja do produkcji?** Wymagana jest ważna licencja GroupDocs.Watermark  

## Wprowadzenie

Zarządzanie złożonymi diagramami często wymaga dostępu do szczegółowych informacji o ich komponentach, takich jak kształty i obrazy. Jeśli kiedykolwiek potrzebowałeś programowo pobrać dane takie jak wymiary, pozycje lub tekst powiązany z kształtami diagramu przy użyciu Javy, ten samouczek jest dla Ciebie. Wykorzystanie mocy biblioteki GroupDocs.Watermark może usprawnić ten proces w aplikacji Java. W tym przewodniku przejdziemy przez **jak wyodrębnić kształty** z pliku diagramu oraz pokażemy, jak **wyodrębnić obraz z kształtu** i **wyodrębnić tekst z kształtu**.

## Co to jest „jak wyodrębnić kształty”?

Wyodrębnianie kształtów oznacza odczytywanie wewnętrznych obiektów diagramu (strony, kształty, obrazy, tekst), aby można je było analizować, przekształcać lub ponownie wykorzystywać w innych aplikacjach — idealne do automatyzacji, raportowania lub integracji z narzędziami CAD.

## Dlaczego używać GroupDocs.Watermark do wyodrębniania kształtów?

- **Pełne wsparcie formatów** – działa z VSDX, VDX i wieloma innymi typami diagramów.  
- **Bogaty model obiektowy** – zapewnia bezpośredni dostęp do geometrii kształtu, obrazów i tekstu.  
- **Brak zewnętrznych zależności** – czysta Java, łatwa do osadzenia w projektach Maven.  

## Wymagania wstępne

- **GroupDocs.Watermark for Java** (wersja 24.11 lub nowsza)  
- Java Development Kit (JDK) 8 lub wyższy  
- Maven do zarządzania zależnościami  
- IDE, takie jak IntelliJ IDEA lub Eclipse  

## Konfiguracja GroupDocs.Watermark dla Javy

Dodaj bibliotekę do swojego pliku Maven `pom.xml`:

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

Możesz również pobrać najnowsze pliki binarne z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Kroki uzyskania licencji
- **Darmowa wersja próbna:** Pobierz pakiet próbny, aby ocenić API.  
- **Licencja tymczasowa:** Poproś o tymczasowy klucz do rozszerzonego testowania.  
- **Zakup:** Uzyskaj pełną licencję do użytku produkcyjnego.  

### Podstawowa inicjalizacja i konfiguracja

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Jak wyodrębnić kształty – przewodnik implementacji

### Ładowanie i pobieranie zawartości

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Iteracja po kształtach

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Jak wyodrębnić obraz z kształtu

Wywołanie `shape.getImage()` zwraca obiekt zawierający surową bitmapę, jej wymiary oraz tablicę bajtów. Użyj właściwości pokazanych powyżej, aby zapisać obraz na dysku lub przekazać go do innego potoku przetwarzania.

### Jak wyodrębnić tekst z kształtu

Metoda `shape.getText()` zwraca czysty tekst wewnątrz kształtu. Jeśli kształt nie zawiera tekstu, metoda zwraca `null`. Przykładowa pętla już wypisuje tekst, a Ty możesz go dalej przetwarzać — na przykład budując indeks wszystkich etykiet kształtów.

## Porady dotyczące rozwiązywania problemów
- Zweryfikuj ścieżkę do pliku i uprawnienia odczytu.  
- Upewnij się, że używasz obsługiwanego formatu diagramu (VSDX, VDX itp.).  
- Jeśli kształt pojawia się bez oczekiwanych danych, sprawdź notatki wydania biblioteki pod kątem specyficznych dla formatu nieprawidłowości.

## Praktyczne zastosowania

1. **Analiza diagramów:** Automatycznie audytuj diagramy pod kątem zgodności, sprawdzając rozmiary kształtów lub brakujące etykiety.  
2. **Wizualizacja danych:** Przekaż wyodrębnione wymiary do pulpitu raportowego, aby zwizualizować gęstość układu.  
3. **Integracja z CAD:** Połącz dane kształtów z API CAD, aby synchronizować specyfikacje projektowe między narzędziami.  

## Rozważania dotyczące wydajności

- **Zamykaj zasoby:** Wywołaj `watermarker.close()`, gdy skończysz, aby zwolnić zasoby natywne.  
- **Zarządzanie pamięcią:** Duże diagramy mogą zużywać znaczną część sterty; monitoruj pamięć i zwiększ `-Xmx`, jeśli to konieczne.  
- **Przetwarzanie wsadowe:** Przetwarzaj pliki w partiach i ponownie używaj jednej instancji `Watermarker`, gdy to możliwe.

## Zakończenie

Postępując zgodnie z tym przewodnikiem, teraz wiesz **jak wyodrębnić kształty**, jak **wyodrębnić obraz z kształtu** oraz jak **wyodrębnić tekst z kształtu** przy użyciu GroupDocs.Watermark dla Javy. Techniki te otwierają drzwi do automatycznej analizy diagramów, raportowania i integracji z innymi systemami inżynieryjnymi. Następnym krokiem jest poznanie pełnego API, przeglądając jego [dokumentację](https://docs.groupdocs.com/watermark/java/) i wypróbowanie łączenia wyodrębniania kształtów z własną logiką biznesową.

## Sekcja FAQ

1. **Czym jest GroupDocs.Watermark?**  
   - Kompleksowa biblioteka Java przeznaczona do znakowania wodnego i wyodrębniania informacji z różnych formatów dokumentów, w tym diagramów.  

2. **Czy mogę używać tej biblioteki do przetwarzania wszystkich typów plików diagramów?**  
   - Tak, ale upewnij się, że format pliku jest obsługiwany, sprawdzając [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Jak wyodrębnić wymiary i pozycje kształtów z diagramu przy użyciu Javy i GroupDocs.Watermark?**  
   - Załaduj diagram, uzyskaj dostęp do `DiagramContent`, a następnie iteruj kształty, aby pobrać właściwości takie jak szerokość, wysokość, X i Y.  

4. **Czy GroupDocs.Watermark może wyodrębnić obrazy osadzone w kształtach diagramu przy użyciu Javy?**  
   - Tak, udostępnia metody dostępu do danych obrazu w kształtach, w tym rozmiar i dane pikseli, przydatne do analizy lub modyfikacji.  

5. **Jakie są wymagania wstępne do wyodrębniania informacji o kształtach diagramu w Javie?**  
   - Java JDK 8+, konfiguracja Maven, biblioteka GroupDocs.Watermark (24.11+), oraz podstawowa znajomość Javy są niezbędne do implementacji.  

---

**Ostatnia aktualizacja:** 2026-02-13  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs