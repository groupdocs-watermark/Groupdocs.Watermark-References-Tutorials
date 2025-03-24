---
title: Dodaj znaki wodne do określonych stron w formacie PDF
linktitle: Dodaj znaki wodne do określonych stron w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać tekstowe i graficzne znaki wodne do określonych stron w plikach PDF przy użyciu narzędzia Groupdocs dla platformy .NET. Postępuj zgodnie z naszym szczegółowym przewodnikiem, aby zabezpieczyć swoje dokumenty.
weight: 15
url: /pl/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
---

# Dodaj znaki wodne do określonych stron w formacie PDF

## Wstęp
Dodawanie znaków wodnych do dokumentów PDF to kluczowy krok w ochronie treści i potwierdzaniu własności. Niezależnie od tego, czy zaznaczasz wersję roboczą, zabezpieczasz poufne informacje, czy po prostu dodajesz branding, znaki wodne są skutecznym narzędziem. W tym samouczku omówimy, jak używać programu Groupdocs.Watermark dla platformy .NET do dodawania tekstowych i graficznych znaków wodnych do określonych stron plików PDF. Podzielimy proces na łatwe do wykonania etapy, dzięki czemu będziesz mógł śledzić i wdrażać te funkcje w swoich projektach.
## Warunki wstępne
Przed przystąpieniem do wdrożenia upewnij się, że spełnione są następujące wymagania wstępne:
- Zainstalowany program Visual Studio: do pisania i uruchamiania kodu .NET potrzebne będzie środowisko IDE, takie jak Visual Studio.
- .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET na swoim komputerze.
-  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj Groupdocs.Watermark dla .NET. Możesz to dostać[Tutaj](https://releases.groupdocs.com/Watermark/net/).
- Podstawowa znajomość języka C#: Znajomość języka programowania C# będzie korzystna.
- Dokument PDF: przygotuj plik PDF, którego możesz użyć do przetestowania dodawania znaków wodnych.
## Importuj przestrzenie nazw
Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Ten krok jest kluczowy, ponieważ umożliwia dostęp do klas i metod Groupdocs.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Konfiguracja projektu
### Utwórz nowy projekt
Najpierw otwórz program Visual Studio i utwórz nowy projekt C#. Dla uproszczenia możesz wybrać aplikację konsolową.
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### Zainstaluj Groupdocs.Watermark
Następnie zainstaluj bibliotekę Groupdocs.Watermark za pomocą Menedżera pakietów NuGet.
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
Wyszukaj „Groupdocs.Watermark” i zainstaluj go.
## Krok 2: Załaduj swój dokument PDF
### Zdefiniuj ścieżki dokumentów
Określ ścieżkę do dokumentu PDF i katalog wyjściowy, w którym zostanie zapisany plik PDF ze znakiem wodnym.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Załaduj dokument PDF
 Użyj`PdfLoadOptions` class, aby załadować dokument PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod umożliwiający dodanie znaków wodnych zostanie umieszczony tutaj
}
```
## Krok 3: Dodaj tekstowy znak wodny do stron nieparzystych
### Utwórz tekstowy znak wodny
 Stwórz`TextWatermark` obiekt z żądanymi ustawieniami tekstu i czcionki.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### Zastosuj opcje tekstowego znaku wodnego
 Używać`PdfArtifactWatermarkOptions` aby określić sposób zastosowania znaku wodnego.
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## Krok 4: Dodaj znak wodny obrazu do pierwszej strony
Załaduj obraz, który chcesz wykorzystać jako znak wodny. Upewnij się, że ścieżka obrazu jest poprawna.
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## Krok 5: Zapisz plik PDF ze znakiem wodnym
Na koniec zapisz plik PDF ze znakiem wodnym w określonym katalogu wyjściowym.
```csharp
watermarker.Save(outputFileName);
```
## Wniosek
Dodawanie znaków wodnych do plików PDF przy użyciu programu Groupdocs dla platformy .NET jest prostym procesem. Wykonując poniższe kroki, możesz skutecznie dodawać tekstowe i graficzne znaki wodne do określonych stron dokumentów PDF. Pomaga to nie tylko w zabezpieczeniu dokumentów, ale także w utrzymaniu profesjonalnego wyglądu. Wypróbuj i poznaj różne dostępne opcje dostosowywania, aby Twoje znaki wodne były wyjątkowe i skuteczne.
## Często zadawane pytania
### Co to jest Groupdocs.Watermark dla .NET?
Groupdocs.Watermark dla .NET to biblioteka umożliwiająca dodawanie, wyszukiwanie i usuwanie znaków wodnych w różnych formatach dokumentów, w tym PDF, Word, Excel i innych.
### Czy mogę dostosować wygląd znaku wodnego?
Tak, możesz dostosować czcionkę, rozmiar, kolor i położenie tekstowych znaków wodnych, a także rozmiar, krycie i położenie graficznych znaków wodnych.
### Czy można dodać znaki wodne tylko do określonych stron?
Absolutnie. Groupdocs.Watermark dla .NET udostępnia opcje dodawania znaków wodnych do określonych stron, stron nieparzystych lub parzystych lub zakresu stron.
### Jak uzyskać bezpłatną wersję próbną Groupdocs.Watermark?
 Możesz pobrać bezpłatną wersję próbną ze strony[Witryna Groupdocs](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć bardziej szczegółową dokumentację?
 Aby uzyskać bardziej szczegółowe informacje, możesz zapoznać się z[dokumentacja](https://tutorials.groupdocs.com/Watermark/net/).