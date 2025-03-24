---
title: Ustaw inny nagłówek/stopkę pierwszej strony w dokumentach programu Word
linktitle: Ustaw inny nagłówek/stopkę pierwszej strony w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak ustawić różne nagłówki i stopki na pierwszej stronie dokumentów programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET.
weight: 36
url: /pl/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---
## Wstęp
dziedzinie zarządzania dokumentami i manipulacji nimi GroupDocs.Watermark dla .NET jawi się jako potężne narzędzie, oferujące bezproblemową integrację i solidne funkcje dodawania znaków wodnych do dokumentów. Jednym z typowych wymagań w przetwarzaniu dokumentów jest ustawienie różnych nagłówków i stopek na pierwszej stronie dokumentów Word. W tym samouczku wyjaśniono proces realizacji tego zadania przy użyciu programu GroupDocs.Watermark dla platformy .NET, dzieląc każdy krok na łatwo zrozumiałe segmenty.
## Warunki wstępne
Przed przystąpieniem do wdrożenia upewnij się, że spełnione są następujące wymagania wstępne:
1.  Instalacja GroupDocs.Watermark dla .NET: Pobierz i zainstaluj GroupDocs.Watermark dla .NET z[link do pobrania](https://releases.groupdocs.com/Watermark/net/).
2. Przygotowanie dokumentu: Przygotuj dokument Word, który wymaga ustawienia różnych nagłówków i stopek na pierwszej stronie.

## Importuj przestrzenie nazw
Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw wymagane do korzystania z funkcjonalności GroupDocs.Watermark dla .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 tym kroku definiujemy ścieżkę do dokumentu, który ma zostać przetworzony oraz określamy nazwę pliku wyjściowego i katalog. Dodatkowo inicjujemy a`Watermarker` obiekt ze ścieżką dokumentu i opcjami ładowania.
## Krok 2: Uzyskaj dostęp do treści dokumentu
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Tutaj pobieramy zawartość dokumentu Word za pomocą`GetContent<T>()` metoda`Watermarker` obiekt, określając typ zawartości jako`WordProcessingContent`.
## Krok 3: Skonfiguruj ustawienia strony
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
Na tym etapie konfigurujemy opcje ustawień strony, aby włączyć różne nagłówki i stopki dla pierwszej strony (`DifferentFirstPageHeaderFooter`) oraz dla stron nieparzystych i parzystych (`OddAndEvenPagesHeaderFooter`).
## Krok 4: Zapisz zmiany
```csharp
watermarker.Save(outputFileName);
```
 Na koniec zapisujemy zmiany wprowadzone w dokumencie wywołując metodę`Save()` metoda`Watermarker` obiekt, przekazując nazwę pliku wyjściowego.

## Wniosek
GroupDocs.Watermark dla .NET zapewnia proste rozwiązanie do ustawiania różnych nagłówków i stopek na pierwszej stronie dokumentów programu Word. Wykonując kroki opisane w tym samouczku, użytkownicy mogą bez wysiłku manipulować zawartością dokumentu zgodnie ze swoimi wymaganiami.
## Często zadawane pytania
### Czy GroupDocs.Watermark dla .NET obsługuje inne formaty dokumentów niż Word?
Tak, GroupDocs.Watermark dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Excel, PowerPoint i inne.
### Czy dostępna jest wersja próbna do celów testowych?
Tak, użytkownicy mogą skorzystać z bezpłatnej wersji próbnej GroupDocs.Watermark dla .NET w witrynie[strona z wydaniami](https://releases.groupdocs.com/).
### Czy GroupDocs.Watermark dla .NET oferuje pomoc techniczną?
 Tak, pomoc techniczna dla GroupDocs Watermark dla .NET jest dostępna za pośrednictwem[forum wsparcia](https://forum.groupdocs.com/c/watermark/19).
### Czy mogę kupić tymczasową licencję na krótkotrwałe użytkowanie?
 Tak, tymczasowe licencje na GroupDocs Watermark dla .NET można nabyć w witrynie[Strona zakupu licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć obszerną dokumentację GroupDocs.Watermark dla .NET?
 Szczegółowa dokumentacja GroupDocs.Watermark dla .NET jest dostępna na stronie[Strona referencyjna](https://tutorials.groupdocs.com/Watermark/net/).