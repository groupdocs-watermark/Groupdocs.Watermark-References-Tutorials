---
date: '2026-03-27'
description: Dowiedz się, jak dodać znak wodny do plików Excel przy użyciu GroupDocs.Watermark
  dla Javy. Ten przewodnik przeprowadza przez konfigurację, kod i najlepsze praktyki
  znakowania arkuszy kalkulacyjnych.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: Dodaj znak wodny do Excela przy użyciu GroupDocs.Watermark Java
type: docs
url: /pl/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# Dodaj znak wodny do Excela przy użyciu GroupDocs.Watermark Java

Dodawanie znaków wodnych do plików Excel może zmienić zasady gry — niezależnie od tego, czy musisz chronić wrażliwe dane, oznaczyć swoje raporty marką, czy po prostu dodać profesjonalny akcent. W tym samouczku dowiesz się, **jak dodać znak wodny do Excela** przy użyciu GroupDocs.Watermark dla Javy, z jasnymi wyjaśnieniami, rzeczywistymi przykładami i wskazówkami, jak unikać typowych pułapek.

## Szybkie odpowiedzi
- **Jakiej biblioteki potrzebuję?** GroupDocs.Watermark for Java (najnowsza wersja).  
- **Jakie formaty Excel są obsługiwane?** pliki .xlsx i .xls (niezaszyfrowane).  
- **Czy mogę dodać znaki wodne jako obrazy?** Tak — SDK obsługuje zarówno tekstowe, jak i graficzne znaki wodne.  
- **Czy potrzebna jest licencja do produkcji?** Wymagana jest licencja komercyjna dla wdrożeń nie‑testowych.  
- **Jak długo trwa implementacja?** Około 10‑15 minut dla podstawowego tekstowego znaku wodnego.

## Co to jest **dodaj znak wodny do Excela**?
Dodanie znaku wodnego do skoroszytu Excel oznacza naniesienie widocznego (lub półprzezroczystego) tekstu lub obrazu na każdy arkusz lub osadzony dokument. Pomaga to zaznaczyć własność, wskazać poufność lub wzmocnić markę w całym pliku.

## Dlaczego używać GroupDocs.Watermark dla Javy?
GroupDocs.Watermark oferuje wysokopoziomowe API, które ukrywa złożoność pracy ze strukturami Office Open XML. Umożliwia ono:
- Zastosowanie znaków wodnych do wielu arkuszy w jednym wywołaniu.  
- Automatyczne obsługiwanie osadzonych załączników (np. osadzone PDF‑y).  
- Zachowanie oryginalnego formatowania i formuł.  
- Praca zarówno z tekstowymi, jak i graficznymi znakami wodnymi (np. **add image watermark java**).

## Wymagania wstępne

- **Środowisko programistyczne Java** – Java 8 lub wyższa (JDK).  
- **GroupDocs.Watermark for Java SDK** – pobierz najnowsze wydanie z [tutaj](https://releases.groupdocs.com/watermark/java/).  
- **IDE** – IntelliJ IDEA, Eclipse lub dowolny edytor kompatybilny z Javą.  
- **Przykładowy arkusz** – plik .xlsx, który chcesz zabezpieczyć.

SDK możesz dodać do swojego projektu za pomocą Maven, Gradle lub ręcznie umieszczając pliki JAR na classpath.

## Importowanie pakietów

Te importy dają dostęp do podstawowych klas znakowania, obsługi arkuszy oraz narzędzi czcionek.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## Jak **oznaczyć arkusz znakem wodnym** – Przewodnik krok po kroku

Poniżej znajduje się praktyczny, numerowany przewodnik, który dokładnie pokazuje, **jak oznaczyć arkusz znakem wodnym** przy użyciu Javy. Każdy krok zawiera krótkie wyjaśnienie, po którym następuje oryginalny blok kodu (bez zmian).

### Krok 1: Skonfiguruj obiekt znaku wodnego  
**Dlaczego?** Ten obiekt definiuje wygląd wizualny znaku, który zostanie zastosowany.

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Krok 2: Załaduj arkusz  
**Dlaczego?** Otwarcie skoroszytu daje SDK uchwyt do edycji.

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### Krok 3: Uzyskaj dostęp do zawartości arkusza i jego arkuszy  
**Dlaczego?** Pliki Excel mogą zawierać wiele arkuszy; musisz iterować po każdym z nich.

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### Krok 4: Przejdź przez załączniki w każdym arkuszu  
**Dlaczego?** Niektóre arkusze osadzają inne dokumenty (np. PDF‑y). Ich obsługa zapewnia spójny znak wodny w całym pliku.

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### Krok 5: Dodaj znak wodny do każdego załączonego dokumentu  
**Dlaczego?** Chcesz, aby każdy osadzony plik miał ten sam znak „Poufny”.

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### Krok 6: Zapisz wszystkie zmiany  
**Dlaczego?** Zapisz zmiany w nowym skoroszycie.

```java
watermarker.save("your-output-file.xlsx");
```

### Krok 7: Zamknij zasoby  
**Dlaczego?** Zwolnienie zasobów zapobiega wyciekom pamięci, szczególnie przy przetwarzaniu dużych skoroszytów.

```java
watermarker.close();
```

## Połączenie wszystkiego: pełny przykład

Poniższa klasa łączy wszystkie kroki w jeden, uruchamialny program. **Nie modyfikuj bloku kodu** – jest identyczny z oryginalnym przykładem.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## Częste problemy i rozwiązania

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Zaszyfrowany skoroszyt jest pomijany** | SDK nie może odczytać zaszyfrowanych plików bez hasła. | Najpierw odszyfruj plik lub podaj hasło za pomocą `SpreadsheetLoadOptions.setPassword("pwd")`. |
| **Znak wodny nie jest widoczny na niektórych arkuszach** | Arkusz może mieć niestandardowy widok lub ochronę, które ukrywają obiekty rysunkowe. | Wyłącz ochronę arkusza przed dodaniem znaku wodnego, a następnie w razie potrzeby ponownie ją włącz. |
| **Spowolnienie wydajności przy dużych plikach** | Ładowanie całego skoroszytu do pamięci może być kosztowne. | Przetwarzaj arkusze w partiach lub zwiększ rozmiar sterty JVM (`-Xmx2g`). |
| **Obrazowy znak wodny jest zniekształcony** | Nieprawidłowe ustawienia skalowania. | Użyj `ImageWatermark` z wyraźnie określonymi parametrami szerokości/wysokości, aby zachować proporcje. |

## Najczęściej zadawane pytania

**P: Czy mogę dodać obrazowy znak wodny zamiast tekstowego?**  
O: Tak. Użyj `ImageWatermark` z SDK i przekaż instancję `java.awt.Image`. To obejmuje scenariusz **add image watermark java**.

**P: Jak kontrolować pozycję znaku wodnego?**  
O: Klasa `TextWatermark` (lub `ImageWatermark`) udostępnia właściwości takie jak `setHorizontalAlignment`, `setVerticalAlignment` oraz `setOpacity`, aby precyzyjnie dostosować położenie i przezroczystość.

**P: Czy można dodać znak wodny do wielu plików Excel w jednym uruchomieniu?**  
O: Oczywiście. Owiń cały przepływ pracy w pętlę `for`, która iteruje po katalogu plików, ponownie używając tej samej instancji `TextWatermark`.

**P: Co się stanie, jeśli arkusz zawiera wykresy?**  
O: Wykresy są traktowane jako oddzielne obiekty rysunkowe; znak wodny jest nakładany na płótno arkusza, więc wykresy pozostają niezmienione, ale są nadal pokryte półprzezroczystym stemplem.

**P: Czy mogę usunąć znak wodny dodany wcześniej?**  
O: SDK zawiera metody `watermarker.remove(watermark)`, ale musisz zachować referencję do oryginalnego obiektu znaku wodnego lub wyszukać go po tekście/treści, aby go zidentyfikować.

---

**Ostatnia aktualizacja:** 2026-03-27  
**Testowano z:** GroupDocs.Watermark 23.12 (Java)  
**Autor:** GroupDocs