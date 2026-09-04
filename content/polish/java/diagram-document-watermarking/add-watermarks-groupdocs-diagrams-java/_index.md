---
date: '2026-02-16'
description: Dowiedz się, jak dodać znak wodny do konkretnej strony diagramu przy
  użyciu GroupDocs.Watermark dla Javy, w tym jak dodać znak wodny obrazu w Javie i
  chronić swoje pliki.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: Znak wodny konkretnej strony diagramu przy użyciu GroupDocs.Watermark dla Javy
type: docs
url: /pl/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# Nakładanie znaku wodnego na określoną stronę diagramu przy użyciu GroupDocs.Watermark dla Javy

Ochrona diagramów jest kluczowa, szczególnie gdy musisz **nakładać znak wodny na wybraną stronę diagramu** w celu zapewnienia bezpieczeństwa własności intelektualnej lub przypisania marki. W tym samouczku dowiesz się krok po kroku, jak dodać zarówno tekstowe, jak i graficzne znaki wodne do wybranych stron pliku diagramu przy użyciu **GroupDocs.Watermark dla Javy**. Po zakończeniu będziesz gotowy zabezpieczyć swoje diagramy i precyzyjnie kontrolować, gdzie pojawia się każdy znak wodny.

## Szybkie odpowiedzi
- **Jaki jest główny cel?** Dodawanie znaków wodnych do wybranych stron diagramu.  
- **Jakiej biblioteki wymaga?** GroupDocs.Watermark for Java (Maven lub bezpośrednie pobranie).  
- **Czy mogę dodać znak wodny w postaci obrazu w Javie?** Tak – użyj `ImageWatermark` z opcjami specyficznymi dla strony.  
- **Czy potrzebna jest licencja?** Tymczasowa licencja próbna działa do testów; pełna licencja jest wymagana w środowisku produkcyjnym.  
- **Ile linii kodu?** Mniej niż 30 linii dla pełnego przepływu pracy z tekstowym + obrazowym znakiem wodnym.

## Co oznacza „nakładanie znaku wodnego na określoną stronę diagramu”?
**Nakładanie znaku wodnego na określoną stronę diagramu** oznacza zastosowanie wizualnego znacznika – tekstu lub obrazu – wyłącznie do wybranych stron w wielostronicowym diagramie (np. Visio . vsdx). Daje to precyzyjną kontrolę nad brandingiem, informacjami poufnymi lub oświadczeniami o prawach autorskich, nie wpływając na cały dokument.

## Dlaczego warto używać GroupDocs.Watermark dla Javy?
- **Pełna kontrola nad stronami** – możesz wybrać dowolny indeks strony.  
- **Bogate formatowanie** – czcionki, kolory, przezroczystość, obrót i skalowanie obrazu są w pełni konfigurowalne.  
- **Wydajność** – przetwarza duże diagramy efektywnie i integruje się płynnie z budowami Maven.  
- **Obsługa wielu formatów** – działa z Visio, SVG i wieloma innymi formatami diagramów.

## Wymagania wstępne
- Biblioteka **GroupDocs.Watermark for Java** w wersji 24.11 lub nowszej.  
- Maven lub bezpośrednie pobranie pliku JAR.  
- Podstawowe środowisko programistyczne Javy (zalecany JDK 8+).  

## Konfiguracja GroupDocs.Watermark dla Javy
### Użycie Maven groupdocs watermark
Dodaj GroupDocs.Watermark do swojego projektu za pomocą Maven, umieszczając poniższy fragment w pliku `pom.xml`:

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
Alternatywnie pobierz najnowszą wersję bezpośrednio z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Uzyskanie licencji
Rozpocznij od darmowej wersji próbnej, pobierając tymczasową licencję. Opcje zakupu są dostępne na ich oficjalnej stronie, jeśli zdecydujesz się kontynuować korzystanie z GroupDocs.Watermark.

### Podstawowa inicjalizacja i konfiguracja
Po instalacji zainicjalizuj klasę `Watermarker` do operacji nakładania znaków wodnych:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## Przewodnik implementacji
### Dodawanie tekstowego znaku wodnego do określonej strony
Aby dodać tekstowy znak wodny, utwórz go i skonfiguruj przed określeniem docelowej strony.

#### Utwórz tekstowy znak wodny
Zdefiniuj swój tekstowy znak wodny z możliwością dostosowania treści, stylu czcionki, rozmiaru itp.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### Ustaw indeks strony dla znaku wodnego
Określ, na której stronie diagramu ma się pojawić znak wodny, używając `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### Dodaj tekstowy znak wodny
Dodaj skonfigurowany znak wodny do diagramu:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### Dodawanie graficznego znaku wodnego do określonej strony
Postępuj analogicznie, używając obiektu `ImageWatermark`.

#### Utwórz graficzny znak wodny
Utwórz instancję `ImageWatermark` z żądaną ścieżką do obrazu znaku wodnego:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### Ustaw indeks strony dla znaku wodnego
Określ, na której stronie ma się wyświetlić obrazowy znak wodny:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### Dodaj graficzny znak wodny
Dodaj obraz do wybranej strony diagramu:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### Zapisz i zamknij zasoby
Pamiętaj, aby zapisać zmiany i zamknąć zasoby, aby uniknąć wycieków pamięci:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Praktyczne zastosowania
- **Bezpieczeństwo dokumentu** – Nakładaj poufne znaki wodne tylko na strony zawierające wrażliwe schematy.  
- **Branding** – Umieść logo firmy na stronie tytułowej, pozostawiając wewnętrzne strony czyste.  
- **Ochrona praw autorskich** – Dodaj informację o prawach autorskich na ostatniej stronie pakietu diagramów technicznych.

## Wskazówki dotyczące wydajności
- **Zarządzanie pamięcią** – Zamykaj każdy obiekt znaku wodnego po zapisaniu, aby zwolnić zasoby natywne.  
- **Optymalizacja obrazów** – Używaj odpowiednio rozmiarowanych plików PNG/JPEG, aby przyspieszyć przetwarzanie.  
- **Przetwarzanie wsadowe** – Przy obsłudze wielu diagramów, w miarę możliwości ponownie używaj jednej instancji `Watermarker`.

## Typowe problemy i rozwiązania
| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Znak wodny niewidoczny | Nieprawidłowy `pageIndex` (liczony od zera) | Sprawdź, czy indeks odpowiada zamierzonej stronie. |
| Obraz jest zniekształcony | Obraz źródłowy o wysokiej rozdzielczości | Zmień rozmiar obrazu przed utworzeniem `ImageWatermark`. |
| Błąd licencji w produkcji | Używanie licencji próbnej po jej wygaśnięciu | Zastosuj pełny plik licencyjny za pomocą `License.setLicense("path/to/license.json")`. |

## Najczęściej zadawane pytania

**Q1: Czy mogę dodać wiele znaków wodnych do jednej strony diagramu?**  
A1: Tak, po prostu wywołaj `watermarker.add()` z różnymi obiektami znaków wodnych dla tego samego indeksu strony.

**Q2: Jakie formaty plików są obsługiwane przez GroupDocs.Watermark dla Javy?**  
A2: Obsługuje różne formaty diagramów i obrazów. Sprawdź pełną listę w [dokumentacji API](https://reference.groupdocs.com/watermark/java).

**Q3: Jak radzić sobie z problemami licencyjnymi przy wersji próbnej?**  
A3: Rozpocznij od darmowej tymczasowej licencji od GroupDocs. Kup pełną licencję, aby odblokować wszystkie funkcje w środowisku produkcyjnym.

**Q4: Jakie są typowe wskazówki, gdy znaki wodne nie pojawiają się tak, jak oczekiwano?**  
A4: Upewnij się, że indeks strony jest poprawny i podwójnie sprawdź ścieżki do plików obrazów. Również zweryfikuj, czy przezroczystość znaku wodnego nie jest ustawiona na 0.

**Q5: Jak mogę dalej dostosować wygląd znaku wodnego?**  
A5: Dostosuj rozmiar czcionki, przezroczystość, obrót i pozycję za pomocą metod dostępnych w `TextWatermark` lub `ImageWatermark`.

## Zasoby
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference Guide](https://reference.groupdocs.com/watermark/java)  
- [Download Library](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)

Zapoznaj się z tymi zasobami, aby pogłębić swoją wiedzę i możliwości pracy z GroupDocs.Watermark dla Javy. Powodzenia w nakładaniu znaków wodnych!

---

**Ostatnia aktualizacja:** 2026-02-16  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs