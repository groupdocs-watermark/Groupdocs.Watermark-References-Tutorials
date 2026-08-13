---
date: '2026-03-20'
description: Dowiedz się, jak dodać znak wodny do arkuszy Excel przy użyciu GroupDocs.Watermark
  dla Javy, obejmując techniki dodawania tekstowego znaku wodnego w Excelu oraz dodawania
  znaku wodnego w Excelu w Javie.
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: Jak dodać znak wodny do Excela przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# Jak dodać znak wodny do arkusza Excel przy użyciu GroupDocs.Watermark for Java

Dodanie możliwości **how to add watermark** do plików Excel jest praktycznym sposobem ochrony wrażliwych danych i potwierdzenia własności. W tym przewodniku krok po kroku nauczysz się, jak dodać znak wodny do arkusza Excel, dostosować jego wygląd i umieścić go w nagłówkach lub stopkach — wszystko przy użyciu GroupDocs.Watermark for Java.

## Szybkie odpowiedzi
- **Jakiej biblioteki wymagana jest?** GroupDocs.Watermark for Java (24.11 lub nowszej).  
- **Czy mogę dostosować czcionkę i kolor?** Tak, przy użyciu klas `Font` i `Color`.  
- **Gdzie pojawia się znak wodny?** W nagłówku lub stopce wybranego arkusza.  
- **Czy wymagana jest licencja do produkcji?** Wymagana jest ważna licencja GroupDocs do użytku nie‑testowego.  
- **Czy to działa z dużymi skoroszytami?** Tak, ale zamknij obiekt `Watermarker`, aby zwolnić zasoby.

## Wprowadzenie

Czy chcesz zwiększyć bezpieczeństwo swoich arkuszy Excel, dodając tekstowe znaki wodne? Niezależnie od tego, czy chodzi o ochronę poufnych danych, czy potwierdzenie własności, osadzenie znaku wodnego w nagłówkach lub stopkach arkusza może być nieocenione. W tym samouczku poprowadzimy Cię przez implementację tej funkcji przy użyciu GroupDocs.Watermark for Java.

**Czego się nauczysz**
- Jak dodać tekstowy znak wodny do arkuszy Excel  
- Konfigurowanie znaków wodnych z własnymi czcionkami i kolorami  
- Ustawianie wyrównania nagłówka/stopki w dokumentach  

Dzięki tym umiejętnościom będziesz dobrze przygotowany do skutecznego zabezpieczania swoich arkuszy. Teraz przejdźmy do wymagań wstępnych niezbędnych do rozpoczęcia.

## Co to jest „how to add watermark” w Excelu?

Znak wodny to słaby, półprzezroczysty tekst lub obraz, który pojawia się za (lub przed) główną treścią. W Excelu znaki wodne są zazwyczaj umieszczane w obszarze nagłówka lub stopki, aby pojawiały się na każdej drukowanej stronie bez zakłócania danych w komórkach.

## Dlaczego używać GroupDocs.Watermark for Java?

- **Cross‑platform**: Działa na każdym systemie operacyjnym obsługującym Javę.  
- **Full control**: Dostosuj czcionkę, rozmiar, kolor i wyrównanie.  
- **Performance‑focused**: Efektywne przetwarzanie dużych skoroszytów.

## Wymagania wstępne

- **GroupDocs.Watermark for Java** (24.11 lub nowszy)  
- **Java Development Kit (JDK)** zainstalowany i skonfigurowany  
- IDE, takie jak IntelliJ IDEA lub Eclipse  
- Maven (jeśli preferujesz zarządzanie zależnościami)

### Wymagane biblioteki

- **GroupDocs.Watermark for Java** – dostarcza API do znakowania.

### Wymagania wiedzy

- Podstawowa programowanie w Javie  
- Znajomość Maven lub ręcznego obsługi JAR‑ów

## Konfiguracja GroupDocs.Watermark for Java

Możesz zainstalować bibliotekę za pomocą Maven lub pobrać plik JAR bezpośrednio.

**Instalacja Maven**

Add the following configuration to your `pom.xml`:

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

**Bezpośrednie pobranie**  
Alternatywnie możesz pobrać najnowszą wersję z [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Uzyskanie licencji
- **Free Trial** – wypróbuj API bez kosztów.  
- **Temporary License** – przedłużony okres oceny.  
- **Purchase** – pełna funkcjonalność, nieograniczone użycie.

Aby zainicjować GroupDocs.Watermark, dołącz instrukcję importu:

```java
import com.groupdocs.watermark.Watermarker;
```

## Jak dodać znak wodny do arkuszy Excel

Poniżej znajduje się kompletny, gotowy do uruchomienia kod podzielony na przejrzyste kroki. Każdy krok zawiera krótkie wyjaśnienie przed blokiem kodu, więc nigdy nie zobaczysz fragmentu bez kontekstu.

### Krok 1: Załaduj arkusz

Najpierw załaduj skoroszyt przy użyciu odpowiednich opcji ładowania.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**Wyjaśnienie**: Tworzy to instancję `Watermarker` powiązaną z Twoim plikiem Excel, gotową do operacji znakowania.

### Krok 2: Utwórz tekstowy znak wodny

Skonfiguruj wygląd wizualny znaku wodnego.

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**Wyjaśnienie**: Ustawiamy tekst znaku wodnego, wybieramy pogrubioną czcionkę **Segoe UI** i stosujemy kontrastujące kolory pierwszego planu i tła.

### Krok 3: Skonfiguruj położenie znaku wodnego

Zdecyduj, który arkusz i która część strony (nagłówek/stopka) otrzyma znak wodny.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**Wyjaśnienie**: Obiekt `SpreadsheetWatermarkHeaderFooterOptions` informuje API, aby zastosować znak wodny w nagłówku/stopce pierwszego arkusza.

### Krok 4: Dodaj znak wodny i zapisz

Zastosuj znak wodny i zapisz wynik do nowego pliku.

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**Wyjaśnienie**: Metoda `add` wstawia znak wodny, `save` zapisuje zmodyfikowany skoroszyt, a `close` zwalnia zasoby.

## Dodaj tekstowy znak wodny w Excel – Zaawansowane wskazówki

- **Multiple Worksheets**: Przejdź pętlą po indeksach arkuszy i wywołaj `options.setWorksheetIndex(i)` dla każdego.  
- **Dynamic Text**: Pobierz tekst znaku wodnego z bazy danych lub pliku konfiguracyjnego, aby spersonalizować każdy dokument.  
- **Opacity Control**: Użyj `watermark.setOpacity(0.5)`, aby znak wodny był bardziej subtelny.  

## Częste problemy i rozwiązania

| Problem | Rozwiązanie |
|-------|----------|
| **Plik nie znaleziony** | Sprawdź, czy ciągi ścieżek (`YOUR_DOCUMENT_DIRECTORY/...`) są poprawne i używaj ścieżek bezwzględnych podczas testów. |
| **Licencja nie znaleziona** | Umieść plik `GroupDocs.Watermark.lic` w katalogu głównym projektu lub ustaw licencję programowo za pomocą `License license = new License(); license.setLicense("path/to/license.lic");`. |
| **Nieobsługiwany format** | Upewnij się, że skoroszyt jest zapisany jako `.xlsx` lub `.xls`. Starsze formaty mogą wymagać najpierw konwersji. |
| **Spowolnienie przy dużych plikach** | Przetwarzaj jeden arkusz na raz i wywołuj `watermarker.close()` zaraz po zakończeniu pracy z każdym plikiem. |

## Praktyczne zastosowania

1. **Confidential Data Protection** – Zniechęć nieautoryzowane kopiowanie, wyraźnie oznaczając każdą drukowaną stronę.  
2. **Ownership Assertion** – Osadź nazwę firmy lub logo jako znak wodny, aby udowodnić pochodzenie dokumentu.  
3. **Document Tracking** – Dodaj unikalne identyfikatory do znaku wodnego, aby śledzić ścieżki dystrybucji.  

## Uwagi dotyczące wydajności

- Zminimalizuj liczbę znaków wodnych na sesję.  
- Niezwłocznie zamykaj obiekt `Watermarker`, aby zwolnić uchwyty plików.  
- W przypadku bardzo dużych skoroszytów rozważ zwiększenie rozmiaru sterty JVM (`-Xmx2g`).  

## Najczęściej zadawane pytania

**Q: Czy mogę zmienić styl czcionki mojego znaku wodnego?**  
A: Tak, dostosuj obiekt `Font` do dowolnej zainstalowanej rodziny czcionek, rozmiaru i `FontStyle` (Bold, Italic, itp.).

**Q: Czy można dodać znaki wodne do wielu arkuszy?**  
A: Oczywiście. Przejdź pętlą po indeksach arkuszy i zastosuj te same `SpreadsheetWatermarkHeaderFooterOptions` dla każdego arkusza.

**Q: Jakie formaty plików obsługuje GroupDocs.Watermark dla plików Excel?**  
A: XLS, XLSX oraz inne formaty arkuszy Office Open XML są w pełni obsługiwane.

**Q: Jak efektywnie obsługiwać bardzo duże dokumenty?**  
A: Przetwarzaj jeden skoroszyt na raz, zamykaj `Watermarker` po zapisaniu i monitoruj zużycie pamięci JVM.

**Q: Czy znaki wodne można później usunąć, jeśli zajdzie taka potrzeba?**  
A: Bezpośrednie usunięcie nie jest dostępne, ale możesz odtworzyć oryginalny plik bez nakładania znaku wodnego lub zachować nieoznaczoną kopię do późniejszego użycia.

## Zasoby

- [Dokumentacja GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- [Referencja API](https://reference.groupdocs.com/watermark/java)  
- [Pobierz GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [Repozytorium GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/watermark/10)  
- [Informacje o licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/)

---

**Ostatnia aktualizacja:** 2026-03-20  
**Testowano z:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs