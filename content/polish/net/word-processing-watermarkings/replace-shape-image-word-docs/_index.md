---
title: Zamień obraz kształtu w dokumentach programu Word
linktitle: Zamień obraz kształtu w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak programowo zastępować obrazy kształtów w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET. Uprość zadania związane z manipulacją dokumentami bez wysiłku.
weight: 33
url: /pl/net/word-processing-watermarkings/replace-shape-image-word-docs/
---
## Wstęp
obszarze tworzenia oprogramowania, zwłaszcza w środowisku .NET, sprawna i bezpieczna obsługa dokumentów jest kluczowa. Wśród niezliczonej liczby zadań, z którymi często spotykają się programiści, jednym z częstych wyzwań jest programowe zastępowanie obrazów kształtów w dokumentach programu Word. Bez odpowiednich narzędzi i bibliotek może to być żmudne zadanie.
Na szczęście GroupDocs oferuje potężne rozwiązanie w postaci GroupDocs.Watermark dla .NET, wszechstronnej biblioteki przeznaczonej do obsługi znaków wodnych i manipulowania znakami wodnymi w różnych formatach dokumentów, w tym w dokumentach Word. W tym samouczku omówimy krok po kroku proces zastępowania obrazów kształtów w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET.
## Warunki wstępne
Zanim przejdziemy do tego samouczka, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Biblioteka GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[link do pobrania](https://releases.groupdocs.com/Watermark/net/).
2. Dokument do manipulacji: Przygotuj dokument programu Word zawierający obrazy kształtów, które chcesz programowo zastąpić.
3. Środowisko programistyczne: Skonfiguruj działające środowisko programistyczne, najlepiej Visual Studio, z możliwościami .NET.
4. Podstawowa znajomość programowania w języku C#: Zapoznaj się z podstawami programowania w języku C#, ponieważ będziemy używać języka C# do interakcji z biblioteką GroupDocs.
## Importuj przestrzenie nazw
Zanim zagłębimy się w kodowanie, zaimportujmy niezbędne przestrzenie nazw do naszego projektu C#:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System;
using System.IO;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dokument został załadowany pomyślnie
}
```
 W tym kroku definiujemy ścieżkę do dokumentu Word, którym chcemy manipulować. Następnie tworzymy instancję`WordProcessingLoadOptions` aby określić opcje ładowania dokumentu programu Word. Następnie inicjujemy a`Watermarker` obiekt ze ścieżką dokumentu i opcjami ładowania.
## Krok 2: Uzyskaj dostęp do treści dokumentu
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Tutaj pobieramy zawartość dokumentu Word za pomocą`GetContent` metoda`Watermarker` obiekt. Treść jest przechowywana w pliku a`WordProcessingContent` obiekt, który umożliwia nam dostęp do różnych elementów dokumentu i manipulowanie nimi.
## Krok 3: Zamień obrazy kształtów
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Image != null)
    {
        shape.Image = new WordProcessingWatermarkableImage(File.ReadAllBytes(Constants.TestPng));
    }
}
```
Na tym etapie iterujemy po każdym kształcie w pierwszej części dokumentu. Dla każdego kształtu zawierającego obraz (`shape.Image != null`), zastępujemy istniejący obraz nowym. W tym przykładzie używamy stałej`TestPng` jako obraz zastępczy. Pamiętaj, aby zastąpić go ścieżką do żądanego obrazu.
## Krok 4: Zapisz dokument
```csharp
watermarker.Save(outputFileName);
```
Na koniec zapisujemy zmodyfikowany dokument z zastąpionymi obrazami pod określoną nazwą pliku wyjściowego.

## Wniosek
GroupDocs.Watermark dla .NET upraszcza proces programowego zastępowania obrazów kształtów w dokumentach programu Word. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować tę funkcjonalność z aplikacjami .NET, oszczędzając czas i wysiłek związany z zadaniami manipulacji dokumentami.
## Często zadawane pytania
### Czy GroupDocs.Watermark dla .NET jest kompatybilny z różnymi wersjami dokumentów Word?
Tak, GroupDocs.Watermark dla .NET obsługuje różne wersje dokumentów programu Word, w tym formaty .doc i .docx.
### Czy mogę zastąpić inne typy elementów oprócz obrazów kształtów za pomocą GroupDocs.Watermark?
Absolutnie. GroupDocs.Watermark oferuje rozbudowaną funkcjonalność zastępowania znaków wodnych, obrazów, tekstu i innych elementów w dokumentach o różnych formatach.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz poznać możliwości GroupDocs.Watermark dla .NET, pobierając bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Czy GroupDocs.Watermark dla .NET zapewnia obsługę znaków wodnych w dokumentach PDF?
Tak, GroupDocs.Watermark dla .NET obsługuje znaki wodne i manipulowanie nimi w dokumentach PDF, a także w innych formatach, takich jak Word, Excel, PowerPoint i nie tylko.
### Jak mogę uzyskać pomoc lub wsparcie dotyczące GroupDocs.Watermark dla .NET?
 Możesz odwiedzić forum GroupDocs.Watermark[Tutaj](https://forum.groupdocs.com/c/watermark/19) aby szukać pomocy lub kontaktować się ze społecznością w przypadku jakichkolwiek pytań lub problemów, które możesz napotkać.