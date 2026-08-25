---
date: '2026-08-25'
description: Dowiedz się, jak edytować pliki diagramów i usuwać hiperłącza przy użyciu
  GroupDocs.Watermark for Java. Szybko zabezpiecz swoje diagramy dzięki instrukcjom
  krok po kroku.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Dowiedz się, jak edytować pliki diagramów i usuwać hiperłącza przy
  użyciu GroupDocs.Watermark for Java. Postępuj zgodnie z jasnymi krokami, aby chronić
  swoje dokumenty.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Jak edytować diagram i usuwać hiperłącza w Javie
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Jak edytować diagram i usuwać hiperłącza w Javie
type: docs
url: /pl/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Jak edytować diagram i usunąć hiperłącza w Javie  

Zarządzanie dokumentami cyfrowymi często wymaga edycji diagramów, szczególnie gdy trzeba **edytować diagram** pliki, aby usunąć hiperłącza ze względów bezpieczeństwa lub przejrzystości wizualnej. Ten samouczek pokazuje dokładnie, jak edytować pliki diagramów i usuwać niechciane hiperłącza z kształtów diagramu przy użyciu potężnej biblioteki **GroupDocs.Watermark** dla Javy. Po zakończeniu tego przewodnika będziesz mieć czysty diagram bez linków, gotowy do dystrybucji.  

## Szybkie odpowiedzi  
- **Jaki jest główny cel?** Usuń wszystkie hiperłącza z kształtów diagramu, aby poprawić bezpieczeństwo i prezentację.  
- **Która biblioteka jest wymagana?** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa do testów; licencja komercyjna jest wymagana w produkcji.  
- **Czy mogę przetwarzać wiele plików jednocześnie?** Tak – ten sam kod może być umieszczony w pętli, aby obsłużyć partie.  
- **Jaką wersję Javy obsługuje?** Java 8 lub wyższa (zalecana Java 11).  

## Co oznacza „jak edytować diagram”?  
**Jak edytować diagram** odnosi się do procesu programowego otwierania pliku diagramu, modyfikowania jego wewnętrznych elementów (takich jak kształty, tekst lub hiperłącza) i zapisywania wyniku. Korzystając z GroupDocs.Watermark możesz edytować pliki diagramów bez potrzeby używania oryginalnego narzędzia do tworzenia.  

## Dlaczego używać GroupDocs.Watermark dla Javy?  
GroupDocs.Watermark obsługuje **ponad 30 formatów diagramów i obrazów** (w tym VSDX, SVG i WMF) i może przetwarzać pliki do **500 MB** bez ładowania całego dokumentu do pamięci, zapewniając **20 % szybsze** przetwarzanie w porównaniu z wieloma konkurentami.  

## Wymagania wstępne  
- Biblioteka **GroupDocs.Watermark** w wersji 24.11 lub nowszej.  
- Maven zainstalowany (lub pliki JAR, jeśli wolisz ręczną konfigurację).  
- Java Development Kit 8 lub nowszy oraz IDE, takie jak IntelliJ IDEA lub Eclipse.  

### Wymagane biblioteki, wersje i zależności  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (jeśli używasz podejścia Maven)  

### Wymagania dotyczące konfiguracji środowiska  
Upewnij się, że katalog `bin` JDK znajduje się w twojej zmiennej `PATH` oraz że twoje IDE wskazuje prawidłową wersję JDK.  

### Wymagania wiedzy wstępnej  
Powinieneś być zaznajomiony z podstawową składnią Javy, zarządzaniem zależnościami Maven oraz operacjami wejścia/wyjścia plików.  

## Jak skonfigurować GroupDocs.Watermark dla Javy?  
Klasa `Watermarker` zapewnia punkt wejścia API do ładowania i modyfikacji dokumentów.  
Aby rozpocząć korzystanie z GroupDocs.Watermark, dodaj jego współrzędne Maven do pliku `pom.xml` projektu. To pobiera bibliotekę i jej zależności, umożliwiając utworzenie instancji klasy Watermarker i pracę z plikami diagramów bezpośrednio z kodu Javy. Następnie możesz skonfigurować licencję i ustawić opcje wyjścia przed przetworzeniem jakiegokolwiek dokumentu.  

Dodaj zależność GroupDocs.Watermark do swojego `pom.xml`.  

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

Jeśli nie chcesz używać Maven, pobierz najnowszy JAR z oficjalnej strony wydań.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Kroki uzyskania licencji  
- Rozpocznij od darmowej wersji próbnej, aby ocenić API.  
- Dla produkcji uzyskaj tymczasową lub stałą licencję w portalu dostawcy.  

#### Podstawowa inicjalizacja i konfiguracja  
Klasa `Watermarker` jest punktem wejścia dla wszystkich operacji przetwarzania dokumentów.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Jak edytować diagram i usunąć hiperłącza przy użyciu GroupDocs.Watermark?  
Klasa `Watermarker` zapewnia punkt wejścia API do ładowania i modyfikacji dokumentów.  
Najpierw załaduj plik diagramu do instancji Watermarker. Następnie pobierz kolekcję kształtów, zidentyfikuj te zawierające obiekty hiperłączy i iteruj po nich w kolejności odwróconej, aby bezpiecznie usunąć każde łącze bez wpływu na indeksowanie kolekcji. To zapewnia usunięcie wszystkich osadzonych URL-i przy zachowaniu integralności wizualnej diagramu.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Dlaczego ten krok ma znaczenie**: Ładowanie pliku daje programowy dostęp do każdego kształtu i jego powiązanych właściwości.  

## Jak uzyskać dostęp do zawartości kształtu w diagramie?  
Obiekt `DiagramShape` reprezentuje pojedynczy kształt w diagramie, udostępniając jego właściwości i powiązane metadane.  
Po załadowaniu diagramu wywołaj `getShapes()` na Watermarker, aby uzyskać listę obiektów `DiagramShape`. Każdy kształt może być sprawdzony pod kątem kolekcji hiperłączy, co umożliwia precyzyjne wybranie linków do usunięcia lub modyfikacji. Możesz także odczytać tekst kształtu, kolory i geometrię, jeśli potrzebne są dalsze korekty.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Dlaczego ten krok ma znaczenie**: Skierowanie się do konkretnego kształtu zapewnia usunięcie tylko niechcianych linków bez wpływu na inne elementy wizualne.  

## Jak iterować i bezpiecznie usuwać hiperłącza?  
Metoda `removeHyperlink(int index)` usuwa hiperłącze w określonej pozycji w kolekcji hiperłączy kształtu.  
Iteruj po liście hiperłączy od ostatniego indeksu w dół do zera. Ta odwrócona pętla zapobiega przesunięciu indeksów, które występuje przy usuwaniu elementów, zapewniając przetworzenie każdego hiperłącza bez pomijania. Po usunięciu możesz odświeżyć stan kształtu lub przejść do kolejnego kształtu w diagramie.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Dlaczego ten krok ma znaczenie**: Odwrócona pętla gwarantuje, że wszystkie hiperłącza zostaną usunięte bez pomijania jakichkolwiek wpisów.  

## Jak zapisać edytowany diagram i zwolnić zasoby?  
Metoda `save(String path)` zapisuje zmodyfikowany dokument w określonej lokalizacji pliku, finalizując wszystkie zmiany.  
Po usunięciu wszystkich hiperłączy wywołaj metodę `save` na instancji Watermarker, podając nową nazwę pliku, aby nie nadpisać oryginału. Następnie wywołaj `close()`, aby zwolnić uchwyty plików i pamięć, co jest niezbędne w długotrwałych procesach wsadowych. To zapewnia prawidłowe zamknięcie pliku i gotowość do dalszego użycia.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Dlaczego ten krok ma znaczenie**: Prawidłowe zamykanie zasobów zapobiega wyciekom pamięci i problemom z blokowaniem plików na serwerze.  

## Praktyczne zastosowania  
Usuwanie hiperłączy z kształtów diagramu może być korzystne w kilku rzeczywistych scenariuszach:  

1. **Bezpieczeństwo** – Zapobiega zewnętrznym linkom, które mogą prowadzić do złośliwych stron.  
2. **Zgodność** – Spełnia polityki korporacyjne zakazujące osadzonych URL-i w udostępnianych zasobach.  
3. **Przejrzystość** – Tworzy czystsze prezentacje, w których linki byłyby rozpraszające.  

Możesz wbudować tę logikę w większe potoki automatyzacji, takie jak nocne zadania wsadowe, które oczyszczają wszystkie diagramy przed ich publikacją w intranecie.  

## Rozważania dotyczące wydajności  

### Optymalizacja wydajności  
- Używaj jednej instancji `Watermarker` na plik, aby zmniejszyć narzut.  
- Preferuj iterację od końca (jak pokazano), aby uniknąć kosztownego ponownego indeksowania listy.  

### Wytyczne dotyczące użycia zasobów  
- Dla diagramów większych niż 200 MB monitoruj zużycie sterty i rozważ zwiększenie flagi JVM `-Xmx`.  
- Narzędzia profilujące, takie jak VisualVM, mogą pomóc zidentyfikować wąskie gardła w dużych uruchomieniach wsadowych.  

### Najlepsze praktyki zarządzania pamięcią w Javie  
- Deklaruj obiekty w jak najmniejszym możliwym zakresie.  
- Używaj try‑with‑resources przy pracy ze strumieniami, aby zapewnić automatyczne zamykanie.  

## Najczęściej zadawane pytania  

**Q: Jak obsłużyć diagramy zawierające tysiące kształtów?**  
A: Przetwarzaj diagram strona po stronie i zwalniaj zasoby każdej strony przed przejściem do kolejnej, aby utrzymać niskie zużycie pamięci.  

**Q: Czy mogę ograniczyć usuwanie hiperłączy tylko do określonych stron?**  
A: Tak – pobierz indeks strony, którą chcesz, a następnie zastosuj pętlę usuwania tylko do kształtów na tej stronie.  

**Q: Czy licencja komercyjna jest obowiązkowa przy przetwarzaniu wsadowym?**  
A: Ważna licencja jest wymagana dla każdej produkcyjnej implementacji; darmowa wersja próbna jest ograniczona do 30 dni i 5 dokumentów.  

**Q: Czy GroupDocs.Watermark obsługuje diagramy SVG?**  
A: Zdecydowanie – SVG jest jednym z ponad 30 obsługiwanych formatów, a hiperłącza można usuwać przy użyciu tych samych wywołań API.  

**Q: Co zrobić, jeśli kształt ma wiele hiperłączy?**  
A: Pętla iterująca od końca usuwa każdy wpis hiperłącza osobno, zapewniając usunięcie wszystkich linków.  

## Zasoby  

- [Dokumentacja](https://docs.groupdocs.com/watermark/java/)  
- [Referencja API](https://reference.groupdocs.com/watermark/java)  
- [Pobierz](https://releases.groupdocs.com/watermark/java/)  
- [Repozytorium GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/watermark/10)  
- [Uzyskanie tymczasowej licencji](https://purchase.groupdocs.com/temporary-license/)  

---  

**Ostatnia aktualizacja:** 2026-08-25  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Powiązane samouczki

- [Samouczki znakowania diagramów dla GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Edycja nagłówków i stopek diagramu w Javie przy użyciu GroupDocs.Watermark: Kompletny przewodnik](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Efektywne usuwanie kształtów z diagramów przy użyciu GroupDocs.Watermark dla Javy](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)