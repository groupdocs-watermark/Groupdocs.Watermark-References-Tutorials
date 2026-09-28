---
date: '2026-09-26'
description: Dowiedz się, jak konwertować dokument na obraz i generować thumbnails
  w Java przy użyciu GroupDocs.Watermark. Przewodnik krok po kroku obejmuje setup,
  preview streams i performance tips.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Dowiedz się, jak konwertować dokument na obraz i generować thumbnails
  w Java przy użyciu GroupDocs.Watermark. Ten przewodnik przeprowadzi Cię przez installation,
  stream handling i performance optimisation dla fast preview creation.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Konwertuj dokument na obraz przy użyciu GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Konwertuj dokument na obraz przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Konwertowanie dokumentu na obraz przy użyciu GroupDocs.Watermark Java

Tworzenie lekkich podglądów obrazów wielostronicowych dokumentów jest powszechnym wymaganiem dla portali, systemów zarządzania treścią i usług przechowywania w chmurze. Dzięki **konwertowaniu dokumentu na obraz** zapewniasz użytkownikom szybki podgląd wizualny bez konieczności ładowania pełnego pliku. Biblioteka GroupDocs.Watermark Java nie tylko dodaje znaki wodne, ale także zapewnia wysokowydajny silnik podglądu, który może **generować miniatury w Javie** dla każdej strony w jednym przebiegu.

W tym samouczku dowiesz się, jak skonfigurować bibliotekę, tworzyć niestandardowe strumienie stron, bezpiecznie zwalniać zasoby oraz ostatecznie generować podglądy obrazów dla każdej strony dokumentu źródłowego. Instrukcje są przeznaczone dla programistów zaznajomionych z Javą i koncepcjami obiektowymi oraz zawierają wskazówki najlepszych praktyk przy obsłudze dużych partii plików.

## Szybkie odpowiedzi
- **Jaki jest pierwszy krok?** Dodaj zależność Maven GroupDocs.Watermark i zainicjalizuj `Watermarker` ze ścieżką do pliku źródłowego.  
- **Jak tworzone są obrazy podglądu?** Zaimplementuj `ICreatePageStream`, aby otworzyć strumień wyjściowy dla każdej strony, a następnie wywołaj `generatePreview()` z odpowiednimi opcjami.  
- **Czy potrzebna jest licencja?** Wersja próbna działa w podstawowych scenariuszach, ale pełna licencja usuwa znaki wodne i odblokowuje przetwarzanie wsadowe.  
- **Czy mogę przetwarzać pliki PDF większe niż 200 stron?** Tak – biblioteka strumieniuje strony, więc zużycie pamięci pozostaje niskie nawet przy plikach 500‑stronicowych.  
- **Jakie formaty obrazów są obsługiwane?** PNG, JPEG, BMP i TIFF są dostępne od razu.

## Co to jest konwertowanie dokumentu na obraz?
Wyrażenie **konwertowanie dokumentu na obraz** opisuje proces renderowania każdej strony pliku źródłowego (PDF, DOCX, PPTX itp.) do obrazu rastrowego, takiego jak PNG lub JPEG. Ta konwersja jest przydatna w galeriach miniatur, panelach podglądu oraz mobilnych przeglądarkach dokumentów.

## Dlaczego warto używać GroupDocs.Watermark do generowania podglądów?
GroupDocs.Watermark obsługuje **30+ formatów wejściowych** i może generować podglądy dokumentów do **500 stron** bez ładowania całego pliku do pamięci. Wewnątrz przetwarza strony kolejno, co utrzymuje zużycie sterty Java poniżej 50 MB nawet przy dużych plikach PDF. Biblioteka oferuje także wbudowaną optymalizację obrazów, umożliwiając określenie DPI, głębi kolorów i poziomu kompresji, co skutkuje miniaturami zazwyczaj **70 % mniejszymi** niż przy prostym rasteryzowaniu.

## Wymagania wstępne

- **Java Development Kit (JDK) 11 lub nowszy** – biblioteka jest kompilowana dla Java 8+, ale JDK 11 zapewnia długoterminowe wsparcie i lepszą wydajność.
- **Maven 3.6+** – do zarządzania zależnościami.
- **GroupDocs.Watermark for Java wersja 24.11** – najnowsze stabilne wydanie w momencie pisania.
- **Podstawowa znajomość strumieni I/O w Javie** – będziesz tworzyć obiekty `FileOutputStream` dla każdej strony podglądu.
- **Klucz licencyjny** (opcjonalny w produkcji) – wersja próbna ogranicza rozmiar podglądu do 5 MB na dokument.

## Jak skonfigurować GroupDocs.Watermark dla Java

Aby skonfigurować GroupDocs.Watermark, najpierw dodaj repozytorium Maven, a następnie włącz bibliotekę jako zależność w pliku `pom.xml` projektu. Zapewnia to, że Maven pobierze właściwe artefakty i udostępni klasy na classpathie do kompilacji i uruchomienia.

### Dodaj zależność Maven
Biblioteka jest dystrybuowana poprzez Maven Central. Dodaj poniższy fragment do swojego `pom.xml` wewnątrz bloku `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Wskazówka:** Przechowuj numer wersji w właściwości (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`), aby łatwo aktualizować.

### Bezpośrednie pobranie (alternatywa)
Jeśli wolisz ręczną instalację, możesz pobrać plik JAR ze strony oficjalnych wydań: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Jak uzyskać i zastosować licencję

Zastosowanie licencji w GroupDocs.Watermark usuwa ograniczenia wersji próbnej i wyłącza domyślną nakładkę znaku wodnego. Umieść plik licencji w znanej lokalizacji i wskaż na niego API, lub osadź ścieżkę licencji bezpośrednio w kodzie przed jakimikolwiek innymi wywołaniami. Po załadowaniu wszystkie kolejne operacje działają w trybie pełnej funkcjonalności.

Możesz:

- **Poproś o darmową wersję próbną** z portalu GroupDocs – zapewnia 30‑dniowy plik licencyjny.
- **Wygeneruj tymczasową licencję** za pomocą generatora licencji online do środowisk testowych.
- **Kup licencję komercyjną** na nieograniczone użycie produkcyjne i wsparcie priorytetowe.

Umieść plik licencji (`GroupDocs.Watermark.lic`) w katalogu głównym projektu lub określ jego ścieżkę programowo przy pomocy `Watermarker.setLicense("path/to/license.file")`.

## Jak zainicjalizować Watermarker

Zainicjalizuj `Watermarker`, podając ścieżkę do dokumentu źródłowego, opcjonalnie wraz z hasłem do chronionych plików. Konstruktor waliduje format i przygotowuje wewnętrzne parsery, umożliwiając natychmiastowe wywołanie metod podglądu lub znaków wodnych. Po utworzeniu zachowaj referencję, aby móc ponownie używać instancji w wielu operacjach, jeśli to potrzebne.

Klasa `Watermarker` jest podstawowym obiektem GroupDocs.Watermark, który ładuje dokument i udostępnia operacje takie jak wstawianie znaków wodnych oraz generowanie podglądów.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – absolutna lub względna ścieżka do pliku źródłowego.
- Konstruktor waliduje format pliku i przygotowuje wewnętrzne parsery.

> **Definicja:** `Watermarker` jest punktem wejścia dla wszystkich działań przetwarzania dokumentów w GroupDocs.Watermark dla Java.

## Jak tworzyć strumienie stron dla generowania podglądów

Utwórz niestandardowe strumienie stron, implementując interfejs `ICreatePageStream`, który biblioteka wywołuje dla każdej renderowanej strony. Twoja implementacja powinna generować nowy `OutputStream` — zazwyczaj `FileOutputStream` — wskazujący na unikalnie nazwany plik oparty na numerze strony. Takie podejście izoluje wyjście każdej strony i zapobiega nakładaniu się danych.

Aby **generować miniatury w Javie**, musisz dostarczyć strumień dla każdej strony, na której zostanie zapisana renderowana grafika. Zaimplementuj interfejs `ICreatePageStream`; biblioteka wywoła Twoją implementację dla każdej przetwarzanej strony.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** pozwala osadzić numer strony bezpośrednio w nazwie pliku, co upraszcza przetwarzanie wsadowe.
- Metoda zwraca nowy `OutputStream` dla każdej strony, zapewniając, że poprzednie strony nie zakłócą kolejnych zapisów.

> **Definicja:** `ICreatePageStream` jest interfejsem zwrotnym, który pozwala określić, jak tworzone są strumienie wyjściowe dla każdej strony podglądu.

## Jak zwolnić strumienie stron po generowaniu podglądu

Po zapisaniu obrazu strony biblioteka wywołuje `IReleasePageStream`, aby umożliwić zamknięcie i wyczyszczenie powiązanego strumienia wyjściowego. Zaimplementuj ten callback, aby bezpiecznie zwolnić uchwyty plików, opróżnić bufory i wykonać dodatkowe logowanie. Prawidłowe czyszczenie zapobiega wyciekom deskryptorów i zapewnia, że kolejne strony mogą być przetwarzane bez zakłóceń.

Prawidłowe czyszczenie zasobów zapobiega wyciekom uchwytów plików i chroni JVM przed wyczerpaniem deskryptorów. Zaimplementuj `IReleasePageStream`, aby zamknąć strumienie, gdy biblioteka sygnalizuje zakończenie przetwarzania strony.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definicja:** `IReleasePageStream` jest interfejsem zwrotnym, który pozwala zdefiniować własną logikę usuwania zasobów wyjściowych specyficznych dla strony.

## Jak generować podglądy dokumentów (konwertowanie dokumentu na obraz)

Generuj podglądy, wywołując `generatePreview()` na instancji `Watermarker`, podając obiekt `PreviewOptions`, który definiuje rozdzielczość, format obrazu i zakres stron. Metoda iteruje po każdej stronie, używa Twoich twórców strumieni do zapisu obrazu rastrowego, a następnie zwalnia strumienie. Proces ten tworzy zestaw plików obrazów reprezentujących strony dokumentu.

Mając gotowe `Watermarker`, `FeatureCreatePageStream` i `FeatureReleasePageStream`, możesz uruchomić silnik podglądu. Metoda `generatePreview()` iteruje po każdej stronie, wywołuje Twoje twórcy strumieni, zapisuje obraz i ostatecznie zwalnia strumienie.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** kontroluje DPI; 150 DPI to dobre wyważenie dla miniatur w sieci.
- **`ImageFormat`** może być PNG, JPEG, BMP lub TIFF w zależności od wymagań downstream.
- Metoda przetwarza strony kolejno, więc zużycie pamięci pozostaje niskie nawet przy dokumentach zawierających setki stron.

> **Definicja:** `generatePreview()` jest wywołaniem API, które renderuje każdą stronę załadowanego dokumentu do obrazu przy użyciu dostarczonych strumieni.

## Praktyczne zastosowania konwertowania dokumentu na obraz

Generowanie podglądów obrazów otwiera wiele możliwości:

1. **Przeglądarki dokumentów** – wyświetl siatkę miniatur PNG, aby użytkownicy mogli przeglądać duże PDF‑y bez ich otwierania.
2. **Fragmenty wyników wyszukiwania** – dołącz obraz podglądu do wpisów indeksu wyszukiwania, aby uzyskać bogatszy interfejs.
3. **Załączniki e‑mail** – osadź mały podgląd załączonych PDF‑ów w treści wiadomości e‑mail.
4. **Aplikacje mobilne** – zmniejsz zużycie pasma, wysyłając podglądy PNG o wielkości 200 KB zamiast pełnych PDF‑ów.
5. **Portale zgodności** – renderuj prawnie wymagane wersje kontraktów z znakami wodnymi jako obrazy dla ścieżek audytu.

## Wskazówki dotyczące wydajności przy generowaniu miniatur w Javie

Podczas przetwarzania dużych partii, pamiętaj o następujących wskazówkach optymalizacyjnych:

- **Buforowanie strumieni** – otocz `FileOutputStream` w `BufferedOutputStream`, aby zminimalizować operacje I/O na dysku.
- **Równoległe przetwarzanie wsadowe** – użyj `ForkJoinPool` Javy do równoczesnego przetwarzania wielu dokumentów; każde zadanie powinno tworzyć własną instancję `Watermarker`, aby uniknąć problemów z bezpieczeństwem wątków.
- **Ogranicz DPI dla miniatur** – 72–150 DPI wystarcza w większości scenariuszy UI; wyższe DPI zarezerwuj dla podglądów gotowych do druku.
- **Ponowne użycie obiektów licencji** – wczytanie pliku licencji raz na JVM zmniejsza narzut.
- **Monitorowanie pamięci** – biblioteka utrzymuje w pamięci tylko bieżącą stronę. W przypadku wyjątkowo dużych plików rozważ umiarkowane zwiększenie sterty JVM (np. `-Xmx512m`), aby obsłużyć sporadyczne skoki.

## Typowe pułapki i jak ich uniknąć

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|-------|--------------------------|-------------|
| `OutOfMemoryError` podczas generowania podglądu | Użycie `ImageFormat.Jpeg` z 300 DPI w 1000‑stronnicowym PDF | Zmniejsz DPI lub przełącz na PNG o niższej głębi kolorów |
| Puste pliki podglądu | `FeatureCreatePageStream` zwraca ten sam `FileOutputStream` dla każdej strony | Upewnij się, że nowy strumień jest tworzony dla każdego `pageNumber` |
| Obrazy podglądu są obrócone | PDF źródłowy zawiera metadane obrotu, które nie są respektowane | Wywołaj `previewOptions.setRotatePages(true)` (jeśli dostępne) |
| Pojawia się ostrzeżenie o licencji | Plik licencji nie został znaleziony lub ścieżka jest nieprawidłowa | Sprawdź, czy `Watermarker.setLicense("path/to/license.file")` jest wywoływany przed innymi wywołaniami API |

## Najczęściej zadawane pytania

**Q: Czy mogę generować podglądy dla PDF‑ów zabezpieczonych hasłem?**  
A: Tak. Przekaż hasło do konstruktora `Watermarker`: `new Watermarker("file.pdf", "password")`.

**Q: Jakie formaty obrazów są obsługiwane dla wyjścia podglądu?**  
A: Dostępne są PNG, JPEG, BMP i TIFF. PNG jest zalecany dla bezstratnych miniatur.

**Q: Ile stron można przetworzyć w jednym wywołaniu?**  
A: Biblioteka nie narzuca sztywnego limitu; możesz podglądać dokumenty z tysiącami stron, ograniczonych jedynie przestrzenią dyskową i przepustowością I/O.

**Q: Czy potrzebna jest osobna licencja dla każdej instancji serwera?**  
A: Jeden plik licencji może być używany w wielu instancjach, o ile całkowite użycie jest zgodne z warunkami licencji.

**Q: Czy istnieje sposób na wygenerowanie jednej połączonej miniatury (np. tylko pierwszej strony)?**  
A: Tak. Ustaw `previewOptions.setPages(new int[]{1})`, aby ograniczyć generowanie do pierwszej strony.

## Podsumowanie

Masz teraz kompletny, gotowy do produkcji przepływ pracy dla **konwertowanie dokumentu na obraz** i **generowanie miniatur w Javie** przy użyciu GroupDocs.Watermark. Konfigurując własne obsługi strumieni stron, utrzymujesz niskie zużycie pamięci, a dostosowując `PreviewOptions`, kontrolujesz jakość obrazu i rozmiar pliku. Te techniki pozwalają osadzić szybkie, wysokiej jakości podglądy w dowolnej aplikacji opartej na Javie — czy to w portalu internetowym, kliencie desktopowym, czy mikroserwisie natywnym w chmurze.

---

**Last Updated:** 2026-09-26  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Powiązane samouczki

- [Jak pobrać informacje o dokumencie przy użyciu GroupDocs.Watermark dla Java: przewodnik krok po kroku](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Zaawansowane samouczki funkcji znaków wodnych dla GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Jak dodać znak wodny obrazu w Javie przy użyciu GroupDocs.Watermark: przewodnik krok po kroku](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)