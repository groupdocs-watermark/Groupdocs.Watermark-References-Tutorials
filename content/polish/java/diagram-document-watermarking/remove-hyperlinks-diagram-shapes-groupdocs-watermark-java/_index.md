---
date: '2026-04-04'
description: Dowiedz się, jak usuwać linki z kształtów diagramu przy użyciu GroupDocs.Watermark
  Java, zapewniając bezpieczeństwo i przejrzystość dokumentu.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Jak usunąć linki z kształtów diagramu przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak usunąć linki z kształtów diagramu przy użyciu GroupDocs.Watermark Java

Zarządzanie dokumentami cyfrowymi często wymaga edycji diagramów, szczególnie gdy potrzebujesz **jak usunąć linki** ze względów bezpieczeństwa lub przejrzystości. W tym samouczku nauczysz się prostego, krok po kroku sposobu usuwania niechcianych hiperłączy z kształtów diagramu przy użyciu potężnej biblioteki **GroupDocs.Watermark** dla Javy. Po zakończeniu będziesz mieć czyste, pozbawione linków diagramy, które są bezpieczne do udostępniania.

## Szybkie odpowiedzi
- **Co oznacza „jak usunąć linki”?** Odwołuje się do usuwania obiektów hiperlinków osadzonych w kształtach diagramu.  
- **Która biblioteka to obsługuje?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa do testów; ważna licencja jest wymagana w produkcji.  
- **Czy mogę przetwarzać wiele plików jednocześnie?** Tak – otocz kod pętlą lub zadaniem wsadowym.  
- **Czy to podejście jest specyficzne dla języka?** Przykład jest w Javie, ale ta sama koncepcja ma zastosowanie do innych interfejsów .NET/Java.

## Co oznacza „jak usunąć linki” w edycji diagramów?
Usuwanie linków oznacza odnajdywanie obiektów hiperlinków dołączonych do kształtów w diagramie (np. Visio *.vsdx) i ich usuwanie. To eliminuje zewnętrzne adresy URL, które mogłyby ujawnić wrażliwe informacje lub zakłócić przebieg prezentacji.

## Dlaczego używać GroupDocs.Watermark dla Javy?
- **Precyzja** – Bezpośredni dostęp do obiektów kształtów i ich kolekcji hiperlinków.  
- **Wydajność** – Zoptymalizowane pod kątem dużych diagramów bez ładowania całego dokumentu do pamięci.  
- **Obsługa wielu formatów** – Działa z wieloma formatami diagramów (Visio, Draw.io itp.).

## Wymagania wstępne
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (lub ręczne dołączenie JAR).  
- Java JDK 8 lub nowszy.  
- IDE, np. IntelliJ IDEA lub Eclipse.

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
Jeśli wolisz nie używać Maven, pobierz najnowszy JAR z oficjalnej strony:  
[Wydania GroupDocs.Watermark dla Javy](https://releases.groupdocs.com/watermark/java/).

#### Kroki uzyskania licencji
- Rozpocznij od pobrania darmowej wersji próbnej.  
- Do produkcji uzyskaj tymczasową lub pełną licencję z portalu GroupDocs.

#### Podstawowa inicjalizacja i konfiguracja
Utwórz instancję `Watermarker`, która wskazuje folder zawierający Twój diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Jak usunąć linki z kształtów diagramu
Poniżej znajduje się zwięzły, czterostopniowy proces, który pokazuje **usuwanie hiperłączy java** w praktyce.

### Krok 1: Załaduj plik diagramu
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Dlaczego?* Załadowanie pliku daje programowy dostęp do jego stron, kształtów i kolekcji hiperlinków.

### Krok 2: Uzyskaj dostęp do zawartości kształtu
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Dlaczego?* Potrzebujesz odniesienia do konkretnego kształtu, który może zawierać hiperlinki.

### Krok 3: Iteruj i usuń hiperlinki
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Dlaczego?* Iterowanie w odwrotnej kolejności zapobiega problemom z przesunięciem indeksów przy usuwaniu elementów z kolekcji.

### Krok 4: Zapisz i zamknij
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Dlaczego?* Zapis zapisuje oczyszczony diagram na dysk, a zamknięcie zwalnia uchwyty plików, aby uniknąć wycieków pamięci.

## Praktyczne zastosowania usuwania linków
1. **Bezpieczeństwo** – Usuwaj zewnętrzne adresy URL, które mogą prowadzić do phishingu lub wycieku danych.  
2. **Zgodność** – Upewnij się, że diagramy spełniają wewnętrzne polityki przed dystrybucją.  
3. **Czystość prezentacji** – Eliminuj niepotrzebne klikalne obszary, które rozpraszają widzów.

## Względy wydajnościowe
- **Efektywność pętli** – Używaj wzorca iteracji w odwrotnej kolejności pokazanego powyżej.  
- **Zarządzanie zasobami** – Preferuj `try‑with‑resources` lub explicite wywołania `close()`.  
- **Duże pliki** – Monitoruj CPU/pamięć; rozważ przetwarzanie stron w partiach.

## Częste problemy i rozwiązania
- **No hyperlinks found** – Nie znaleziono hiperlinków – Sprawdź, czy diagram faktycznie zawiera obiekty hiperlinków; niektóre formaty przechowują je inaczej.  
- **IndexOutOfBoundsException** – Zawsze iteruj w odwrotnej kolejności przy usuwaniu elementów z kolekcji.  
- **License errors** – Błędy licencji – Upewnij się, że plik licencji jest poprawnie umieszczony lub przekazany do konstruktora `Watermarker`.

## Najczęściej zadawane pytania

**Q: Jak obsłużyć wiele kształtów na wielu stronach?**  
A: Iteruj przez `content.getPages()`, a następnie przez kolekcję `getShapes()` każdej strony, stosując tę samą logikę usuwania do każdego kształtu.

**Q: Czy mogę filtrować linki po domenie zamiast pełnego URL?**  
A: Tak – zmień sprawdzanie `contains`, aby szukało ciągu domeny (np. `"example.com"`).

**Q: Czy istnieje sposób, aby zalogować, które linki zostały usunięte?**  
A: Wewnątrz pętli, przechwyć `shape.getHyperlinks().get_Item(i).getAddress()` przed usunięciem i zapisz to do pliku logu.

**Q: Czy to działa z diagramami PDF osadzonymi w innych dokumentach?**  
A: GroupDocs.Watermark obsługuje wiele formatów; upewnij się, że typ pliku jest rozpoznawany jako diagram (Visio, VDX itp.).

**Q: Jakiej licencji potrzebuję do przetwarzania wsadowego?**  
A: Pełna licencja produkcyjna jest wymagana dla wszelkich operacji nie‑próbnych, o dużej objętości.

## Zakończenie
Masz teraz kompletną, gotową do produkcji metodę **jak usunąć linki** z kształtów diagramu przy użyciu GroupDocs.Watermark dla Javy. Włącz ją do swoich potoków przetwarzania dokumentów, aby zwiększyć bezpieczeństwo, zgodność i jakość wizualną.

### Następne kroki
- Zbadaj inne funkcje manipulacji, takie jak dodawanie znaków wodnych lub stemplowanie tekstu.  
- Połącz tę procedurę z usługą monitorującą pliki, aby automatycznie czyścić diagramy w momencie ich przesyłania.

---

**Ostatnia aktualizacja:** 2026-04-04  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Zasoby
- [Dokumentacja](https://docs.groupdocs.com/watermark/java/)
- [Referencja API](https://reference.groupdocs.com/watermark/java)
- [Pobierz](https://releases.groupdocs.com/watermark/java/)
- [Repozytorium GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/watermark/10)
- [Uzyskanie tymczasowej licencji](https://purchase.groupdocs.com/temporary-license/)