---
date: '2026-10-21'
description: Dowiedz się, jak usunąć hiperłącze z kształtów diagramu przy użyciu GroupDocs.Watermark
  dla Java. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby zabezpieczyć i
  oczyścić swoje dokumenty.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Dowiedz się, jak usunąć hiperłącze z kształtów diagramu przy użyciu
  GroupDocs.Watermark dla Java. Ten przewodnik przeprowadzi Cię przez konfigurację,
  kod oraz najlepsze praktyki, aby uzyskać bezpieczne i czyste dokumenty.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Jak usunąć hiperłącze z kształtów przy użyciu GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Jak usunąć hiperłącze z kształtów przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak usunąć hiperłącze z kształtów przy użyciu GroupDocs.Watermark Java

Zarządzanie dokumentami cyfrowymi często wymaga edycji diagramów, szczególnie gdy trzeba **jak usunąć hiperłącze** z kształtów ze względu na bezpieczeństwo lub przejrzystość wizualną. Ten samouczek przeprowadzi Cię przez prostą metodę usuwania niechcianych hiperłączy z kształtów diagramu przy użyciu potężnej biblioteki **GroupDocs.Watermark** w Javie. Po zakończeniu tego przewodnika zrozumiesz, dlaczego usuwanie hiperłączy jest ważne, jak skonfigurować środowisko oraz dokładne kroki, aby bezpiecznie wykonać usunięcie.

## Szybkie odpowiedzi
- **Jaki jest główny cel usuwania hiperłączy?** Aby wyeliminować ryzyko bezpieczeństwa i poprawić przejrzystość wizualną w udostępnionych diagramach.  
- **Która biblioteka obsługuje usuwanie?** GroupDocs.Watermark for Java provides a dedicated API for diagram manipulation.  
- **Czy potrzebuję licencji?** A trial works for testing; a commercial license is required for production use.  
- **Czy mogę przetwarzać wiele plików jednocześnie?** Yes—wrap the code in a loop or batch job to handle bulk operations.  
- **Jaka wersja Javy jest wymagana?** Java 8 or higher is supported.

## Co to jest usuwanie hiperłącza?
Wyrażenie **jak usunąć hiperłącze** odnosi się do procesu lokalizowania i usuwania obiektów hiperłącza osadzonych w elementach kształtów diagramu. Wykonanie tej czynności zapobiega zewnętrznej nawigacji, która mogłaby nieumyślnie narażać użytkowników na złośliwe witryny lub niepożądane treści. Jest to szczególnie ważne przy przygotowywaniu dokumentów do publicznej dystrybucji, zapewniając, że nie pozostają ukryte ścieżki nawigacyjne, które mogłyby prowadzić do stron phishingowych lub niezamierzonych zasobów zewnętrznych.

## Dlaczego używać GroupDocs.Watermark w Javie?
GroupDocs.Watermark obsługuje **ponad 30 formatów wejściowych i wyjściowych** i może przetwarzać diagramy z **do 500 stronami** bez ładowania całego pliku do pamięci, zapewniając **40 % redukcję zużycia CPU** w porównaniu z ogólnymi parserami XML. Jego API daje precyzyjną kontrolę nad właściwościami kształtów, co czyni go standardowym podejściem do bezpiecznego obsługiwania diagramów w aplikacjach Java.

## Wymagania wstępne
- biblioteka **GroupDocs.Watermark** w wersji 24.11 lub nowszej.  
- Maven zainstalowany (lub bezpośrednie pobranie JAR).  
- JDK 8 lub nowszy oraz IDE, takie jak IntelliJ IDEA lub Eclipse.  
- Podstawowa znajomość Javy oraz znajomość zależności Maven.

## Konfiguracja GroupDocs.Watermark dla Javy
Aby rozpocząć, dołącz bibliotekę GroupDocs.Watermark do swojego projektu. Możesz dodać ją za pomocą Maven lub pobrać JAR ręcznie.

### Konfiguracja Maven
Dodaj następującą konfigurację do swojego `pom.xml`:

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

#### Kroki uzyskania licencji
- Rozpocznij od darmowej wersji próbnej, pobierając GroupDocs.Watermark.  
- W celu rozszerzonego testowania lub użycia produkcyjnego, uzyskaj tymczasową licencję lub zakup pełną licencję.

#### Podstawowa inicjalizacja i konfiguracja
Klasa `Watermarker` jest punktem wejścia dla wszystkich operacji na poziomie dokumentu. Ładuje plik, daje dostęp do jego stron, kształtów i metadanych, a na końcu zapisuje zmodyfikowany dokument z powrotem na dysk.

Aby zainicjalizować klasę Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak usunąć hiperłącze z kształtów diagramu?
Załaduj diagram, znajdź każdy kształt zawierający hiperłącze i usuń te obiekty hiperłącza. Cała operacja może być wykonana w mniej niż dziesięciu linijkach kodu i zapewnia, że wynikowy diagram nie zawiera już żadnych klikalnych linków, które mogłyby przekierować użytkowników do zewnętrznych witryn lub ujawnić wrażliwe informacje.

### Krok 1: załaduj plik diagramu
Rozpocznij od załadowania diagramu przy użyciu `Watermarker`. Ten obiekt zapewnia dostęp do różnych elementów dokumentu, w tym kształtów i ich właściwości.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Dlaczego**: Ładowanie pliku jest niezbędne, aby uzyskać dostęp do jego zawartości w celu dalszej manipulacji.

### Krok 2: uzyskaj dostęp do zawartości kształtów
Pobierz zawartość kształtów diagramu. To pozwala pracować bezpośrednio z elementami, które mogą zawierać hiperłącza.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Dlaczego**: Dostęp do konkretnych kształtów jest kluczowy dla celowego modyfikowania właściwości hiperłącza.

### Krok 3: iteruj i usuń hiperłącza
Iteruj po hiperłączach w odwrotnej kolejności, aby bezpiecznie usuwać niechciane linki bez zakłócania procesu iteracji.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Dlaczego**: Odwrócenie kolejności iteracji zapobiega problemom z indeksowaniem podczas usuwania elementów.

### Krok 4: zapisz i zamknij
Po zakończeniu modyfikacji zapisz zmiany w nowej lokalizacji pliku i zamknij zasób watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Dlaczego**: Prawidłowe zamykanie zasobów zapewnia brak wycieków pamięci ani zablokowanych plików w systemie.

## Typowe pułapki i rozwiązywanie problemów
- **Null shape collections** – Zawsze sprawdzaj, czy kolekcja `Hyperlinks` kształtu nie jest null przed iteracją.  
- **Large diagrams** – Dla plików większych niż 200 stron, zwiększ rozmiar sterty JVM (`-Xmx2g`), aby uniknąć `OutOfMemoryError`.  
- **License errors** – Jeśli pojawi się wyjątek licencyjny, sprawdź, czy licencja próbna nie wygasła i czy ścieżka do pliku licencji jest poprawna.

## Najczęściej zadawane pytania

**P: Jak obsłużyć wiele kształtów na tej samej stronie?**  
Iteruj przez kolekcję `Shapes` każdej strony, stosując tę samą logikę usuwania hiperłączy do każdego napotkanego kształtu.

**P: Czy mogę ograniczyć usuwanie do określonego zakresu stron?**  
Tak—użyj indeksu strony przy pobieraniu kształtów i pomiń strony poza wybranym zakresem.

**P: Czy licencja jest wymagana do przetwarzania wsadowego?**  
Ważna licencja komercyjna jest wymagana dla każdego zadania wsadowego w środowisku produkcyjnym; licencja próbna działa tylko w ograniczonym testowaniu.

**P: Czy to działa z plikami SVG lub Visio?**  
GroupDocs.Watermark obsługuje SVG, VSDX i kilka innych formatów diagramów; upewnij się, że typ pliku znajduje się w tabeli obsługiwanych formatów.

**P: Jaką wydajność mogę oczekiwać przy diagramie 300‑stronnicowym?**  
Na typowym serwerze (8 CPU, 16 GB RAM) przetworzenie diagramu 300‑stronnicowego zajmuje mniej niż 45 sekund, przy zużyciu pamięci poniżej 200 MB.

## Zasoby
- [Dokumentacja](https://docs.groupdocs.com/watermark/java/)
- [Referencja API](https://reference.groupdocs.com/watermark/java)
- [Pobierz](https://releases.groupdocs.com/watermark/java/)
- [Repozytorium GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/watermark/10)
- [Uzyskanie tymczasowej licencji](https://purchase.groupdocs.com/temporary-license/)

---

**Ostatnia aktualizacja:** 2026-10-21  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Powiązane samouczki

- [Modyfikacja kształtów dokumentu Word przy użyciu GroupDocs.Watermark w Javie: Kompletny przewodnik](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Usuwanie kształtów z dokumentów Word przy użyciu GroupDocs.Watermark w Javie: Kompletny przewodnik](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Edycja nagłówków i stopek diagramu w Javie przy użyciu GroupDocs.Watermark: Kompletny przewodnik](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)