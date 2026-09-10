---
date: '2026-02-05'
description: Dowiedz się, jak wyodrębniać kształty z dokumentów Word przy użyciu GroupDocs.Watermark
  dla Javy, w tym jak wczytać dokument Word w Javie i manipulować danymi kształtów.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Jak wyodrębnić kształty z dokumentów Word przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Jak wyodrębnić kształty z dokumentów Word przy użyciu GroupDocs.Watermark w Javie

W tym samouczku dowiesz się **jak wyodrębnić kształty** z dokumentów Word przy użyciu biblioteki GroupDocs.Watermark dla Javy. Niezależnie od tego, czy potrzebujesz analizować diagramy, wyciągać osadzone obrazy, czy automatyzować generowanie raportów, wyodrębnianie metadanych kształtów daje kontrolę potrzebną do budowania inteligentniejszych potoków przetwarzania dokumentów. Przeprowadzimy Cię przez konfigurację biblioteki, wczytanie dokumentu Word oraz pobranie szczegółowych informacji o kształtach — wszystko w przejrzystym, krok po kroku kodzie Java.

## Szybkie odpowiedzi
- **Co oznacza „wyodrębnić kształty”?** Pobieranie metadanych (typ, rozmiar, pozycja, tekst, obrazy) dla każdego obiektu rysunkowego w pliku Word.  
- **Która biblioteka to obsługuje?** GroupDocs.Watermark dla Javy.  
- **Czy potrzebna jest licencja?** Wersja próbna działa w środowisku deweloperskim; pełna licencja usuwa ograniczenia użytkowania.  
- **Czy mogę także pobrać obrazy z kształtów?** Tak — API udostępnia bajty obrazu dla kształtów‑obrazów.  
- **Jaka wersja Javy jest wymagana?** JDK 8 lub nowsza.

## Co oznacza „wyodrębnić kształty” w kontekście dokumentów Word?
Wyodrębnianie kształtów oznacza programowe uzyskiwanie dostępu do każdego elementu rysunkowego — obrazów, WordArt, auto‑kształtów, wykresów oraz nawet kształtów osadzonych w nagłówkach lub stopkach. Informacje te mogą być wykorzystywane do walidacji, migracji lub analiz opartych na treści.

## Dlaczego używać GroupDocs.Watermark dla Javy?
GroupDocs.Watermark oferuje wysokopoziomowe, pamięciooszczędne API, które ukrywa złożoność podstawowego formatu Office Open XML. Umożliwia ono:
- Szybkie wczytywanie dokumentów (`WordProcessingLoadOptions`).  
- Iterowanie przez sekcje i kształty bez konieczności obsługi niskopoziomowego XML.  
- Pobieranie danych obrazu, tekstu, wyrównania i rotacji w jednym wywołaniu.  
- Bezproblemowa integracja z istniejącymi usługami Java lub mikro‑serwisami.

## Wymagania wstępne
- **Java Development Kit (JDK)** 8 lub wyższy.  
- **IDE** takie jak IntelliJ IDEA lub Eclipse.  
- Podstawowa znajomość Java I/O.  
- Dostęp do licencji lub wersji próbnej **GroupDocs.Watermark dla Javy**.

## Konfiguracja GroupDocs.Watermark dla Javy
Zintegruj bibliotekę za pomocą Maven lub bezpośredniego pobrania.

### Korzystanie z Maven
Add the repository and dependency to your `pom.xml`:

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
Alternatywnie, pobierz najnowszy plik JAR z [wydania GroupDocs.Watermark dla Javy](https://releases.groupdocs.com/watermark/java/).

### Uzyskanie licencji
Wersja próbna jest wystarczająca do testów. W środowisku produkcyjnym, poproś o stałą licencję, aby odblokować wszystkie funkcje.

## Przewodnik implementacji
Podzielimy implementację na dwa wyraźne kroki: **wczytanie dokumentu Word** oraz **wyodrębnienie informacji o kształtach**.

### Krok 1: Wczytaj dokument Word (load word document java)
Najpierw skonfiguruj opcje ładowania i utwórz instancję `Watermarker`. Przygotowuje to dokument do dalszej inspekcji.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Wskazówka:** Trzymaj instancję `Watermarker` w jak najwęższym zakresie; jej szybkie zamknięcie zwalnia zasoby natywne i zapobiega wyciekom pamięci.

### Krok 2: Wyodrębnij informacje o kształtach (extract images from shapes)
Teraz pobierzemy szczegóły każdego kształtu, w tym wszelkie osadzone obrazy. Kod iteruje przez każdą sekcję i każdy kształt, wypisując przydatne metadane.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**Co robi ten kod:**  
- Pobiera **typ** każdego kształtu (np. obraz, WordArt).  
- Wypisuje wartości **rozmiaru**, **pozycji** i **rotacji**.  
- Pokazuje **tekst alternatywny** i **nazwę**, które są przydatne przy sprawdzaniu dostępności.  
- Jeśli kształt zawiera obraz, wypisuje **wymiary w pikselach** oraz **rozmiar w bajtach** obrazu — idealne do wyodrębniania obrazów z kształtów.  

### Typowe problemy i jak je rozwiązać
| Problem | Przyczyna | Rozwiązanie |
|-------|-------|----------|
| `FileNotFoundException` | Nieprawidłowa ścieżka pliku lub brak uprawnień | Sprawdź ścieżkę bezwzględną/względną i upewnij się, że plik jest czytelny. |
| Null `shape.getImage()` | Kształt nie jest obrazem (np. auto‑kształt) | Zabezpiecz kod przy użyciu `if (shape.getImage() != null)`, jak pokazano. |
| Wysokie zużycie pamięci przy dużych dokumentach | Ładowanie całego dokumentu jednocześnie | Przetwarzaj sekcje pojedynczo lub zwiększ przydział pamięci JVM (`-Xmx`). |
| Brak kształtów w nagłówku/stopce | Brak sprawdzenia `shape.getHeaderFooter()` | Przykład już loguje, gdy kształt należy do nagłówka/stopki. |

## Praktyczne zastosowania
1. **Automatyczne generowanie raportów** – Pobieraj wykresy i diagramy do osadzenia w kolejnych plikach PDF.  
2. **Audyt zgodności** – Sprawdzaj, czy wszystkie kształty zawierają odpowiedni tekst alternatywny pod kątem dostępności.  
3. **Migracja treści** – Eksportuj osadzone obrazy ze starszych plików Word do systemu zarządzania zasobami cyfrowymi.  

## Uwagi dotyczące wydajności
- **Zwalnianie zasobów**: Zawsze wywołuj `watermarker.close()` w bloku `finally` lub używaj try‑with‑resources, jeśli otaczasz API.  
- **Przetwarzanie w partiach**: Dla dokumentów powyżej 50 MB rozważ przetwarzanie każdej sekcji osobno, aby utrzymać niski zużycie pamięci.  
- **Bezpieczeństwo wątków**: Instancje `Watermarker` nie są bezpieczne wątkowo; twórz nową instancję dla każdego wątku.  

## Podsumowanie
Teraz wiesz **jak wyodrębnić kształty** z dokumentów Word przy użyciu GroupDocs.Watermark dla Javy, od wczytania pliku po odczytanie metadanych każdego kształtu oraz danych osadzonych obrazów. Ta możliwość otwiera drzwi do zaawansowanej analizy dokumentów, zautomatyzowanych potoków treści i walidacji dostępności.

### Kolejne kroki
- Eksperymentuj z modyfikacją właściwości kształtów (np. zmiana rozmiaru lub położenia).  
- Połącz to podejście z **GroupDocs.Parser**, aby wyodrębnić otaczający tekst.  
- Zintegruj logikę wyodrębniania w usługę REST do przetwarzania na żądanie.

## Sekcja FAQ
**P:** Co to jest GroupDocs.Watermark dla Javy?  
**O:** To kompleksowa biblioteka zaprojektowana do zarządzania znakami wodnymi i zawartością dokumentów w różnych formatach, umożliwiająca takie zadania jak wyodrębnianie kształtów, pobieranie obrazów i manipulację tekstem.

**P:** Czy mogę wyodrębnić obrazy z kształtów bez licencji?  
**O:** Wersja próbna umożliwia wyodrębnianie, ale pełna licencja usuwa ograniczenia użytkowania i pozwala na wdrożenia komercyjne.

**P:** Czy to działa z plikami `.doc` (binarnymi)?  
**O:** Tak, API obsługuje zarówno format `.docx`, jak i starszy format `.doc`.

**P:** Jak obsłużyć dokumenty chronione hasłem?  
**O:** Podaj hasło za pomocą `WordProcessingLoadOptions.setPassword("yourPassword")` przed utworzeniem `Watermarker`.

**P:** Czy istnieje sposób na wyeksportowanie wyodrębnionych danych kształtów do JSON?  
**O:** Możesz zamapować wypisane wartości na POJO i użyć dowolnej biblioteki JSON (np. Jackson) do serializacji kolekcji.

---

**Ostatnia aktualizacja:** 2026-02-05  
**Testowano z:** GroupDocs.Watermark 24.11 dla Javy  
**Autor:** GroupDocs