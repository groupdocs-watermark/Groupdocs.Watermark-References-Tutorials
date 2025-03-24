---
title: Dodaj znak wodny z typem marginesu strony w formacie PDF
linktitle: Dodaj znak wodny z typem marginesu strony w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne z typem marginesu strony w formacie PDF przy użyciu Groupdocs dla .NET. Zabezpiecz swoje dokumenty bez wysiłku.
weight: 21
url: /pl/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---
## Wstęp
dzisiejszej erze cyfrowej zabezpieczanie dokumentów jest ważniejsze niż kiedykolwiek. Jednym ze sposobów zapewnienia integralności i autentyczności dokumentów jest dodanie znaków wodnych. Groupdocs.Watermark dla .NET to wyjątkowe narzędzie zaprojektowane tak, aby ułatwić ten proces. W tym samouczku przeprowadzimy Cię przez kolejne etapy dodawania znaku wodnego z marginesem strony w pliku PDF przy użyciu programu Groupdocs.Watermark dla platformy .NET.
## Warunki wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
-  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj[Ostatnia wersja](https://releases.groupdocs.com/Watermark/net/) z Groupdocs.Watermark dla .NET.
- Środowisko programistyczne: środowisko programistyczne .NET, takie jak Visual Studio.
- Podstawowa znajomość języka C#: Znajomość języka programowania C#.
- Dokument PDF: Dokument PDF, do którego chcesz dodać znak wodny.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#. Te przestrzenie nazw zapewnią dostęp do funkcjonalności Groupdocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Podzielmy teraz proces na łatwe do wykonania etapy. Wykonaj dokładnie każdy krok, aby dodać znak wodny do dokumentu PDF.
## Krok 1: Skonfiguruj ścieżkę dokumentu i katalog wyjściowy
Najpierw musisz określić ścieżkę do dokumentu i katalog wyjściowy, w którym zostanie zapisany plik PDF ze znakiem wodnym.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Załaduj swój dokument PDF
 Następnie załadujesz dokument PDF za pomocą`PdfLoadOptions` klasa. Ta klasa pozwala określić wszelkie opcje potrzebne do załadowania pliku PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 3: Utwórz tekstowy znak wodny
Teraz czas na utworzenie znaku wodnego. W tym przykładzie utworzymy tekstowy znak wodny z określonymi właściwościami, takimi jak czcionka, rozmiar i wyrównanie.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Ustaw typ marginesu strony
 Aby odpowiednio ustawić znak wodny, musisz ustawić typ marginesu strony. Tutaj ustawiamy typ marginesu strony na`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Krok 5: Dodaj i zapisz znak wodny
Na koniec dodaj znak wodny do swojego dokumentu i zapisz zmodyfikowany plik PDF w określonym katalogu wyjściowym.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Wniosek
masz to! Wykonując poniższe kroki, możesz łatwo dodać znak wodny z określonym typem marginesu strony do dokumentów PDF za pomocą Groupdocs.Watermark dla .NET. Pomaga to nie tylko chronić dokumenty, ale także zapewnia ich autentyczność. Niezależnie od tego, czy masz do czynienia z poufnymi raportami, dokumentami prawnymi, czy dziełami twórczymi, znak wodny to prosty, ale skuteczny sposób zabezpieczenia treści.
## Często zadawane pytania
### Co to jest Groupdocs.Watermark dla .NET?
Groupdocs.Watermark dla .NET to potężna biblioteka do programowego dodawania znaków wodnych do różnych formatów dokumentów. Obsługuje obrazy, tekst i inne elementy, umożliwiając szerokie dostosowywanie.
### Czy mogę użyć tej metody do znakowania wodnego innych typów dokumentów?
Tak, Groupdocs.Watermark dla .NET obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PowerPoint i obrazy. Proces jest podobny, ale może obejmować różne opcje i klasy.
### Jak mogę uzyskać bezpłatną wersję próbną Groupdocs.Watermark dla .NET?
 Możesz[Pobierz bezpłatną wersję próbną](https://releases.groupdocs.com/) z witryny Groupdocs, aby zapoznać się z funkcjami i funkcjonalnością biblioteki.
### Czy można dostosować wygląd znaku wodnego?
Absolutnie! Możesz dostosować czcionkę, rozmiar, kolor, przezroczystość, wyrównanie i inne właściwości znaku wodnego do swoich potrzeb.
### Gdzie mogę uzyskać pomoc dotyczącą Groupdocs.Watermark dla .NET?
 Aby uzyskać pomoc, możesz odwiedzić stronę[Forum pomocy technicznej Groupdocs Watermark](https://forum.groupdocs.com/c/watermark/19) gdzie możesz zadawać pytania i uzyskać pomoc od społeczności i zespołu Groupdocs.