---
date: '2025-12-19'
description: Dowiedz się, jak usuwać hiperłącza z kształtów diagramu przy użyciu GroupDocs.Watermark
  Java, kluczowy krok w zabezpieczaniu dokumentów Java i masowym usuwaniu hiperłączy.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Jak usunąć hiperłącza z kształtów diagramu przy użyciu GroupDocs.Watermark
  Java
type: docs
url: /pl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak usunąć hiperłącza z kształtów diagramu przy użyciu GroupDocs.Watermark Java

Zarządzanie dokumentami cyfrowymi często obejmuje edycję diagramów, szczególnie gdy **usuwanie hiperłączy** jest potrzebne ze względu na bezpieczeństwo lub przejrzystość. W tym samouczku dowiesz się **jak usuwać hiperłącza** z kształtów diagramu przy użyciu GroupDocs.Watermark dla Java, zapewniając, że Twoje pliki pozostaną czyste, bezpieczne i profesjonalne.

## Szybkie odpowiedzi
- **Jaki jest główny cel?** Aby usunąć niechciane hiperłącza z kształtów diagramu w celu zwiększenia bezpieczeństwa dokumentu.  
- **Która biblioteka jest używana?** GroupDocs.Watermark for Java (wersja 24.11 lub nowsza).  
- **Czy potrzebna jest licencja?** Wersja próbna działa do testów; ważna licencja jest wymagana w środowisku produkcyjnym.  
- **Czy mogę przetwarzać wiele plików jednocześnie?** Tak – tę samą logikę można umieścić w pętli wsadowej.  
- **Czy Java 8 jest wystarczająca?** Java 8+ jest obsługiwana; zalecane są nowsze wersje JDK.  

## Co oznacza „jak usunąć hiperłącza” w kontekście diagramów?
Usuwanie hiperłączy oznacza usunięcie odwołań URL dołączonych do kształtów w pliku diagramu (np. Visio *.vsdx). Ta operacja zapobiega przypadkowej nawigacji do zewnętrznych stron i pomaga spełnić wymogi zgodności lub wewnętrzne polityki bezpieczeństwa.

## Dlaczego używać GroupDocs.Watermark Java do tego zadania?
- **Solidne wsparcie formatów** – działa z szeroką gamą typów diagramów.  
- **Precyzyjne API** – pozwala celować w pojedyncze kształty i ich kolekcje hiperłączy.  
- **Zoptymalizowana wydajność** – odpowiednia zarówno dla pojedynczych plików, jak i przetwarzania wsadowego.  

## Wymagania wstępne
- **GroupDocs.Watermark** wersja biblioteki 24.11 lub nowsza.  
- Maven lub bezpośrednie pobranie JAR (zobacz kroki konfiguracji poniżej).  
- Java Development Kit (JDK 8 lub nowszy) oraz IDE, takie jak IntelliJ IDEA lub Eclipse.  

## Konfiguracja GroupDocs.Watermark dla Java
Aby rozpocząć, dołącz bibliotekę do swojego projektu za pomocą Maven lub pobierając plik JAR.

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
- Rozpocznij od darmowej wersji próbnej, aby ocenić API.  
- Do produkcji uzyskaj tymczasową lub pełnowymiarową licencję z portalu GroupDocs.

#### Podstawowa inicjalizacja i konfiguracja
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak usunąć hiperłącza z kształtów diagramu
Poniżej znajduje się przewodnik krok po kroku, który prowadzi Cię przez ładowanie diagramu, znajdowanie kształtów i usuwanie niechcianych hiperłączy.

### Krok 1: Załaduj plik diagramu
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Dlaczego?* Ładowanie pliku zapewnia programowy dostęp do jego wewnętrznej struktury.

### Krok 2: Uzyskaj dostęp do zawartości kształtu
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Dlaczego?* Potrzebujesz odwołania do konkretnego kształtu, który może zawierać hiperłącza.

### Krok 3: Iteruj i usuń hiperłącza
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Dlaczego?* Iterowanie wstecz zapobiega błędom indeksowania przy usuwaniu elementów z kolekcji.

### Krok 4: Zapisz i zamknij
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Dlaczego?* Zapisanie zmian i zwolnienie zasobów zapobiega wyciekom pamięci oraz zablokowanym plikom.

## Masowe usuwanie hiperłączy (zaawansowany przypadek użycia)
Jeśli potrzebujesz wyczyścić wiele diagramów jednocześnie, umieść powyższą logikę w pętli iterującej po liście ścieżek plików. Te same wywołania API mają zastosowanie; wystarczy zmienić katalogi wejściowy i wyjściowy dla każdej iteracji. To podejście spełnia wymagania **batch remove hyperlinks** dla dużych repozytoriów dokumentów.

## Praktyczne zastosowania
Usuwanie hiperłączy z kształtów diagramu może być korzystne w kilku rzeczywistych scenariuszach:

1. **Cele bezpieczeństwa** – Zapobiega zewnętrznym linkom, które mogą narażać Twoją sieć na phishing lub malware.  
2. **Zgodność** – Spełnia korporacyjne polityki zakazujące zewnętrznych URL w udostępnianych dokumentach.  
3. **Przejrzystość** – Tworzy czystsze prezentacje, w których hiperłącza są niepotrzebne lub rozpraszające.  

## Rozważania dotyczące wydajności
### Optymalizacja wydajności
- Używaj wzorca iteracji wstecz, jak pokazano powyżej, aby pętle były wydajne.  
- Zamknij obiekt `Watermarker` natychmiast po zakończeniu, aby zwolnić pamięć.

### Wytyczne dotyczące użycia zasobów
- Monitoruj CPU i RAM podczas przetwarzania dużych diagramów.  
- W przypadku zadań wsadowych rozważ strumieniowe przetwarzanie plików zamiast ładowania ich wszystkich naraz.

### Najlepsze praktyki zarządzania pamięcią w Javie
- Unikaj tworzenia obiektów wewnątrz ciasnych pętli.  
- Używaj try‑with‑resources tam, gdzie to możliwe, aby automatycznie sprzątać zasoby.

## Najczęściej zadawane pytania
1. **Jak obsłużyć wiele kształtów?**  
   Iteruj po wszystkich stronach i ich kształtach, stosując tę samą logikę usuwania hiperłączy do każdego kształtu.  

2. **Czy ten proces może być zautomatyzowany dla dużych partii diagramów?**  
   Tak – wstaw kod w rutynę przetwarzania wsadowego lub zintegrować go z systemem zarządzania dokumentami.  

3. **Co zrobić, jeśli muszę usunąć hiperłącza tylko z określonych stron?**  
   Uzyskaj dostęp do żądanej strony po jej indeksie (`content.getPages().get_Item(pageIndex)`) i celuj tylko w kształty na tej stronie.  

4. **Czy wymagana jest licencja do użycia GroupDocs.Watermark w produkcji?**  
   Ważna licencja komercyjna jest wymagana po okresie próbnym.  

5. **Czy ta metoda działa z innymi formatami diagramów?**  
   GroupDocs.Watermark obsługuje wiele typów diagramów; sprawdź kompatybilność w oficjalnej dokumentacji.  

**Dodatkowe Q&A**

**Q:** *Czy możliwe jest logowanie, które hiperłącza zostały usunięte?*  
**A:** Tak – przed wywołaniem `removeAt(i)`, pobierz `shape.getHyperlinks().get_Item(i).getAddress()` i zapisz to do pliku logu.

**Q:** *Czy usunięcie hiperłączy wpłynie na wygląd wizualny kształtu?*  
**A:** Nie. Geometria kształtu pozostaje niezmieniona; usuwane są tylko metadane linku.

**Q:** *Czy po usunięciu trzeba ponownie zastosować stylizację?*  
**A:** Zazwyczaj nie. Usunięcie hiperłącza nie zmienia wypełnienia, linii ani stylów tekstu.

## Podsumowanie
Masz teraz kompletną, gotową do produkcji metodę **jak usuwać hiperłącza** z kształtów diagramu przy użyciu GroupDocs.Watermark dla Java. Postępując zgodnie z powyższymi krokami, możesz zabezpieczyć swoje diagramy, spełnić wymogi polityk i utrzymać dokumenty w estetycznym stanie.

**Zasoby**  
- [Dokumentacja](https://docs.groupdocs.com/watermark/java/)  
- [Referencja API](https://reference.groupdocs.com/watermark/java)  
- [Pobierz](https://releases.groupdocs.com/watermark/java/)  
- [Repozytorium GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/watermark/10)  
- [Uzyskanie tymczasowej licencji](https://purchase.groupdocs.com/temporary-license/)

---

**Ostatnia aktualizacja:** 2025-12-19  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  
