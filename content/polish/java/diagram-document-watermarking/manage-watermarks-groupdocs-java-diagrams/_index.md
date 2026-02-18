---
date: '2026-02-18'
description: Dowiedz się, jak dodać znak wodny i jak usunąć znak wodny w plikach diagramów,
  takich jak .vsdx, przy użyciu GroupDocs.Watermark dla Javy. Chroń integralność dokumentu
  za pomocą GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Jak dodać znak wodny do diagramów przy użyciu GroupDocs.Watermark dla Javy
type: docs
url: /pl/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Jak dodać znak wodny do diagramów przy użyciu GroupDocs.Watermark dla Javy

Zarządzanie znakami wodnymi w plikach diagramów jest kluczowym elementem ochrony własności intelektualnej i utrzymania dokumentów w czystości do publicznego udostępniania. W tym przewodniku dowiesz się **jak dodać znak wodny** do diagramu Visio, a także **jak usunąć znak wodny**, gdy nie jest już potrzebny, przy użyciu biblioteki **groupdocs watermark java**. Niezależnie od tego, czy tworzysz przedsiębiorstwowy potok dokumentów, czy szybki skrypt narzędziowy, te kroki zapewnią pełną kontrolę nad znakowaniem diagramów.

## Szybkie odpowiedzi
- **Jakiej biblioteki używać do znaków wodnych w diagramach w Javie?** GroupDocs.Watermark for Java.  
- **Czy mogę dodać i usunąć znaki wodne w tym samym uruchomieniu?** Tak – wczytaj diagram raz i wykonaj zarówno operację dodawania, jak i usuwania.  
- **Jakie formaty plików są obsługiwane?** Formaty Visio, takie jak `.vsdx`, `.vdx`, oraz inne typy diagramów.  
- **Czy potrzebna jest licencja?** Licencja próbna działa w fazie rozwoju; pełna licencja jest wymagana w produkcji.  
- **Jakiej wersji Javy potrzebuję?** JDK 8 lub wyższej.

## Co oznacza „jak dodać znak wodny” w kontekście diagramów?
Dodanie znaku wodnego oznacza osadzenie widocznego lub niewidzialnego znacznika – tekstu, logo lub obrazu – w pliku diagramu. Ten znacznik podróżuje razem z plikiem, ułatwiając udowodnienie własności lub oznaczenie wersji roboczych.

## Dlaczego warto używać GroupDocs.Watermark dla Javy?
* **Bogate API** – wyszukiwanie, dodawanie i usuwanie zarówno tekstowych, jak i graficznych znaków wodnych w kilku linijkach kodu.  
* **Obsługa wielu formatów** – działa z Visio (`.vsdx`, `.vdx`) oraz wieloma innymi typami diagramów.  
* **Skoncentrowane na wydajności** – ładuje tylko te części diagramu, które są potrzebne do operacji znakowania, co utrzymuje niskie zużycie pamięci.

## Wymagania wstępne
1. **Java Development Kit (JDK) 8+** – Upewnij się, że `java -version` zwraca 1.8 lub nowszą wersję.  
2. **IDE** – IntelliJ IDEA, Eclipse lub dowolny edytor, którego używasz.  
3. **GroupDocs.Watermark for Java** – Dodaj ją do projektu za pomocą Maven lub pobierając bezpośrednio plik JAR.  

### Wymagane biblioteki i zależności
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

*Jeśli nie chcesz używać Maven, możesz pobrać najnowszy JAR z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Uzyskanie licencji
- **Bezpłatna wersja próbna:** Testuj wszystkie funkcje bez klucza licencyjnego.  
- **Licencja tymczasowa:** Poproś o klucz ograniczony czasowo do oceny.  
- **Pełna licencja:** Kup subskrypcję, aby uzyskać nieograniczone użycie w produkcji.

## Konfiguracja GroupDocs.Watermark dla Javy
1. **Dodaj bibliotekę** do projektu (Maven lub ręczny JAR).  
2. **Utwórz instancję `Watermarker`** – ten obiekt jest punktem wejścia do wczytywania diagramów, wyszukiwania, dodawania i usuwania znaków wodnych.

## Przewodnik implementacji

### Ładowanie dokumentu diagramu
Ładowanie to pierwszy krok, zanim będziesz mógł **dodać znak wodny** lub **usunąć znak wodny**. Poniższy kod pokazuje, jak otworzyć plik `.vsdx` z własnymi opcjami ładowania.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Wyszukiwanie znaków wodnych tekstowych
Zanim dodasz nowy znak wodny, możesz zweryfikować, czy znak tekstowy już istnieje. Ten fragment wyszukuje frazę „Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Wyszukiwanie znaków wodnych graficznych
Jeśli musisz zlokalizować logo lub dowolny obraz użyty jako znak wodny, użyj `ImageDctHashSearchCriteria`. Jest to przydatne, gdy chcesz **usunąć znak wodny**, który odpowiada znanemu logo.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Usuwanie znaków wodnych
Gdy już zidentyfikujesz znaki wodne – tekstowe, graficzne lub oba – możesz je usunąć z diagramu. Poniższy przykład demonstruje połączoną operację usuwania.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Praktyczne zastosowania
1. **Integracja oprogramowania korporacyjnego** – Wbuduj zarządzanie znakami wodnymi w system ERP lub platformę generowania dokumentów, aby wymusić branding.  
2. **Systemy zarządzania treścią (CMS)** – Automatycznie skanuj przesyłane diagramy pod kątem nieautoryzowanych logo i usuwaj je.  
3. **Obsługa dokumentów prawnych** – Dodaj tekstowy znak wodny „Confidential” w fazach projektowych, a później **usuń znak wodny** przed ostatecznym złożeniem.

## Typowe problemy i rozwiązania
| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Nie znaleziono znaków wodnych | Tekst/obraz wyszukiwania nie pasuje dokładnie | Użyj `or()` aby połączyć kryteria lub dostosuj ustawienia wrażliwości na wielkość liter. |
| `OutOfMemoryError` przy dużych plikach | Diagram wczytany w całości do pamięci | Użyj `DiagramLoadOptions.setLoadPages()` aby wczytać tylko potrzebne strony. |
| Zapisany plik jest uszkodzony | `watermarker.save()` wywołany przed usunięciem wszystkich znaków wodnych | Upewnij się, że `possibleWatermarks.clear()` zakończyło się pomyślnie i wywołaj `watermarker.close()` po zapisaniu. |

## Najczęściej zadawane pytania

**P: Czy mogę wyszukiwać jednocześnie tekst i obrazy?**  
O: Tak. Połącz `TextSearchCriteria` i `ImageDctHashSearchCriteria` metodą `or()`, jak pokazano w przykładzie usuwania.

**P: Czy można usunąć znaki wodne bez uszkadzania diagramu?**  
O: Absolutnie. Biblioteka izoluje obiekty znaków wodnych, więc wywołanie `clear()` usuwa tylko warstwy znaków wodnych, zachowując oryginalną treść diagramu.

**P: Czy GroupDocs.Watermark obsługuje wiele formatów diagramów?**  
O: Tak. Formaty takie jak `.vsdx`, `.vdx` oraz inne pliki kompatybilne z Visio są w pełni wspierane.

**P: Jak efektywnie obsługiwać duże wolumeny dokumentów?**  
O: Implementuj pętle przetwarzania wsadowego, ponownie używaj jednej instancji `Watermarker` tam, gdzie to możliwe, i ogranicz ładowanie stron przy pomocy `DiagramLoadOptions`.

**P: Czy istnieje sposób na automatyczną detekcję znaków wodnych w pipeline CI/CD?**  
O: Możesz osadzić dostarczone fragmenty Javy w skryptach budowania (np. Maven lub Gradle), aby zweryfikować brak nieautoryzowanych znaków wodnych przed wydaniem artefaktów.

---

**Ostatnia aktualizacja:** 2026-02-18  
**Testowane z:** GroupDocs.Watermark 24.11 dla Javy  
**Autor:** GroupDocs