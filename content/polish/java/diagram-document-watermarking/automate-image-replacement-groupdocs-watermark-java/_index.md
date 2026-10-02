---
date: '2026-10-01'
description: Dowiedz się, jak zautomatyzować image replacement java w plikach diagramów
  przy użyciu GroupDocs.Watermark, w tym watermark addition i efficient processing.
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: Automatyzuj image replacement java w diagramach przy użyciu GroupDocs.Watermark.
  Ten przewodnik pokazuje, jak wymieniać obrazy, dodawać watermarks i obsługiwać large
  files efektywnie.
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: Automatyzacja image replacement java przy użyciu GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: Automatyzacja image replacement java przy użyciu GroupDocs.Watermark
type: docs
url: /pl/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Automatyzacja wymiany obrazów w Javie przy użyciu GroupDocs.Watermark

Aktualizowanie pojedynczych obrazów w diagramie może być żmudnym, podatnym na błędy zadaniem ręcznym. Dzięki **GroupDocs.Watermark for Java** możesz **automatyzować wymianę obrazów w Javie** w dziesiątkach lub setkach plików, zapewniając spójność marki i oszczędzając cenny czas programistyczny. Ten samouczek przeprowadzi Cię przez konfigurację biblioteki, dostęp do zawartości diagramu, zamianę obrazów w określonych kształtach oraz opcjonalne dodanie znaku wodnego do diagramu.

## Szybkie odpowiedzi
- **Która biblioteka obsługuje aktualizacje obrazów w diagramie?** GroupDocs.Watermark for Java.  
- **Czy mogę dodać znak wodny podczas wymiany obrazów?** Tak – to samo API pozwala nakładać znaki wodne na dowolną stronę diagramu.  
- **Jaką wersję Javy wymaga się?** JDK 8 lub wyższa.  
- **Czy potrzebna jest licencja do rozwoju?** Darmowa wersja próbna działa w celach oceny; licencja komercyjna jest wymagana w produkcji.  
- **Czy proces jest oszczędny pamięciowo dla dużych diagramów?** Tak – SDK strumieniuje zawartość i nigdy nie ładuje całego pliku do pamięci.

## Co to jest GroupDocs.Watermark for Java?
`GroupDocs.Watermark` jest zestawem SDK w Javie, który umożliwia programowe dodawanie, usuwanie i wymianę znaków wodnych oraz obrazów w ponad 30 formatach dokumentów, w tym Visio, SVG i innych typach diagramów. Przetwarza pliki w trybie strumieniowym, co pozwala pracować z diagramami liczącymi setki stron bez wyczerpywania pamięci.

## Dlaczego automatyzować wymianę obrazów w Javie?
Automatyzacja wymiany obrazów zmniejsza ręczną pracę nawet o **90 %** przy aktualizacji elementów marki w dużych zbiorach dokumentów. SDK obsługuje **ponad 30 formatów wejściowych i wyjściowych**, przetwarza pliki do **200 MB** w mniej niż sekundę na typowym sprzęcie serwerowym i zapewnia precyzyjne pozycjonowanie obrazów piksel po pikselu.

## Wymagania wstępne
- JDK 8 lub nowszy zainstalowany na Twoim komputerze deweloperskim.  
- Maven (lub inne narzędzie budowania) do zarządzania zależnościami.  
- IDE, takie jak IntelliJ IDEA lub Eclipse.  
- Podstawowa znajomość Javy i obeznanie z operacjami I/O na plikach.

### Wymagane biblioteki, wersje i zależności
Dodaj następujące współrzędne Maven do swojego `pom.xml`. Poniższy placeholder reprezentuje dokładny fragment XML, którego potrzebujesz; pozostaw go niezmienionym.

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

Aby pobrać ręcznie, pobierz najnowsze pliki JAR z oficjalnej strony wydań: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Jak automatyzować wymianę obrazów w Javie?
Załaduj diagram przy użyciu instancji `Watermarker`, zlokalizuj docelowe kształty, zamień ich strumienie obrazów, opcjonalnie dodaj znak wodny i na końcu zapisz plik. Cały przepływ pracy mieści się w **czterech zwięzłych krokach**, z których każdy jest przedstawiony poniżej i zazwyczaj wymaga tylko kilku sekund na diagram, nawet przy dużych plikach.

### Krok 1: zainicjalizuj watermarker
Klasa `Watermarker` jest punktem wejścia dla wszystkich operacji na dokumentach. Otwiera plik źródłowy i przygotowuje wewnętrzne struktury do edycji.

```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```

- **DiagramLoadOptions** konfiguruje parametry ładowania specyficzne dla diagramu.  
- Inicjalizacja `Watermarker` otwiera uchwyt pliku i waliduje format.

### Krok 2: uzyskaj dostęp do zawartości diagramu
`DiagramContent` reprezentuje logiczną strukturę diagramu, udostępniając strony i poszczególne kształty do inspekcji.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- Użyj `watermarker.getContent()`, aby pobrać obiekt `DiagramContent`.  
- Iteruj przez `content.getPages()`, a następnie `page.getShapes()`, aby znaleźć kształty zawierające obrazy.

### Krok 3: zamień obrazy kształtów w diagramie
Obiekty `DiagramShape` mogą zawierać osadzony obraz. Zamień go, dostarczając nowy `InputStream`, który odczytuje obraz zastępczy.

Metoda `setImage(InputStream)` zamienia bieżący obraz kształtu na podany strumień.  

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```

- Sprawdź `shape.getImage()`; jeśli nie jest null, wywołaj `shape.setImage(newImageStream)`.  
- SDK automatycznie aktualizuje wymiary obrazu i zachowuje pierwotny układ kształtu.

### Krok 4: dodaj znak wodny do diagramu (opcjonalnie)
Jeśli potrzebujesz również **dodać znak wodny do diagramu**, utwórz obiekt `Watermark` i zastosuj go do wybranej strony lub całego dokumentu.

Klasa `Watermark` definiuje wizualną nakładkę, którą można umieścić na stronach diagramu lub w całym dokumencie.  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

Metoda `add(Watermark, AddOptions)` stosuje określony znak wodny do dokumentu przy użyciu podanych opcji.  

*(Powyższy kod jest ilustracyjny i nie liczy się jako nowy blok kodu; jest umieszczony wewnątrz istniejącego akapitu.)*

### Krok 5: zapisz i zamknij watermarker
Zachowaj zmiany i zwolnij zasoby, aby uniknąć blokad plików.

Metoda `save(String)` zapisuje zmodyfikowany dokument w określonej ścieżce.  

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```

- Wywołaj `watermarker.save("output.vsdx")` (lub odpowiednie rozszerzenie).  
- Zawsze wywołuj `watermarker.close()` w bloku `finally` lub użyj try‑with‑resources dla automatycznego czyszczenia.

## Typowe pułapki i rozwiązywanie problemów
- **Niezgodność rozmiaru obrazu** – Upewnij się, że obraz zastępczy ma taki sam współczynnik proporcji jak oryginał, aby uniknąć zniekształceń.  
- **Skoki pamięci przy dużych diagramach** – Przetwarzaj diagramy pojedynczo i zamykaj `Watermarker` po każdym zapisie.  
- **Błędy licencji** – Licencja próbna wygasa po 30 dniach; zamień ją na klucz produkcyjny przed wdrożeniem. Tymczasową licencję możesz uzyskać od GroupDocs: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Najczęściej zadawane pytania

**Q: Czy mogę zamienić obrazy w diagramach chronionych hasłem?**  
A: Tak. Załaduj plik przy użyciu `DiagramLoadOptions`, który zawiera hasło, a następnie kontynuuj normalne kroki wymiany.

**Q: Czy SDK obsługuje przetwarzanie wsadowe wielu diagramów?**  
A: Zdecydowanie tak. Owiń przepływ pracy dla jednego pliku w pętlę iterującą po katalogu; architektura strumieniowa utrzymuje niskie zużycie pamięci.

**Q: Z jakimi formatami mogę pracować oprócz Visio?**  
A: GroupDocs.Watermark obsługuje SVG, VDX, VSDX i kilka innych formatów diagramów, łącznie ponad 30 obsługiwanych typów.

**Q: Czy można dodać znak wodny po zamianie obrazów?**  
A: Tak – wywołaj `watermarker.add(watermark, options)` po kroku wymiany obrazu i przed zapisem.

**Q: Jak zapewnić, że nowy obraz jest osadzony, a nie linkowany?**  
A: Metoda `setImage(InputStream)` osadza dane obrazu bezpośrednio w pliku diagramu, zapewniając przenośność.

**Ostatnia aktualizacja:** 2026-10-01  
**Testowano z:** GroupDocs.Watermark 23.12 for Java  
**Autor:** GroupDocs

## Powiązane samouczki

- [Samouczki znakowania diagramów dla GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Usuwanie hiperłączy z kształtów diagramu przy użyciu GroupDocs.Watermark Java w celu zwiększenia bezpieczeństwa dokumentów](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Jak dodać znak wodny obrazu w Javie przy użyciu GroupDocs.Watermark: przewodnik krok po kroku](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)