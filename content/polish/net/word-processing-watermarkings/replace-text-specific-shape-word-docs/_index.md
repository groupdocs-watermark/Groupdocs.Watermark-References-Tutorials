---
title: Zastąp tekst określonym kształtem w dokumentach programu Word
linktitle: Zastąp tekst określonym kształtem w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak zastąpić tekst określonych kształtów w dokumentach programu Word za pomocą programu GroupDocs.Watermark dla platformy .NET. Postępuj zgodnie z naszym samouczkiem krok po kroku.
weight: 35
url: /pl/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
type: docs
---
# Zastąp tekst określonym kształtem w dokumentach programu Word

## Wstęp
W tym samouczku omówimy, jak używać GroupDocs.Watermark dla .NET do zastępowania tekstu dla określonego kształtu w dokumentach programu Word. GroupDocs.Watermark dla .NET to potężna biblioteka udostępniająca szeroką gamę funkcji do pracy ze znakami wodnymi w różnych formatach dokumentów, w tym w dokumentach Word.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1.  GroupDocs.Watermark dla .NET: Upewnij się, że pobrałeś i zainstalowałeś GroupDocs.Watermark dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Przygotuj dokument programu Word, w którym chcesz zastąpić tekst określonym kształtem.
3. Środowisko programistyczne: Skonfiguruj środowisko programistyczne za pomocą niezbędnych narzędzi i zależności.

## Importuj przestrzenie nazw
Najpierw zaimportujmy wymagane przestrzenie nazw do pracy z GroupDocs.Watermark dla .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod trafia tutaj
}
```
 W tym kroku określamy ścieżkę do dokumentu Word i tworzymy instancję`WordProcessingLoadOptions` aby załadować dokument.
## Krok 2: Uzyskaj zawartość dokumentu
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 Tutaj pobieramy zawartość dokumentu Word za pomocą`GetContent<T>()` metoda`Watermarker`class, określając typ jako`WordProcessingContent`.
## Krok 3: Zamień tekst na określony kształt
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
Na tym etapie iterujemy po każdym kształcie w dokumencie. Jeśli kształt zawiera określony tekst (w tym przykładzie „Jakiś tekst”), zastępujemy go żądanym tekstem („Inny tekst”).
## Krok 4: Zapisz dokument
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
Na koniec zapisujemy zmodyfikowany dokument we wskazanym katalogu.

## Wniosek
GroupDocs.Watermark dla .NET oferuje wygodny i skuteczny sposób manipulowania znakami wodnymi w dokumentach programu Word. Wykonując kroki opisane w tym samouczku, możesz łatwo zastąpić tekst określonymi kształtami, zapewniając elastyczność i opcje dostosowywania do potrzeb przetwarzania dokumentów.
## Często zadawane pytania
### Czy mogę zastąpić tekst kształtów w innych formatach dokumentów niż Word?
GroupDocs.Watermark dla .NET obsługuje różne formaty dokumentów, w tym PDF, Excel, PowerPoint i inne. Za pomocą podobnych metod możesz zastąpić tekst kształtów w różnych formatach.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Watermark dla .NET?
Pomoc techniczną można uzyskać odwiedzając forum GroupDocs[Tutaj](https://forum.groupdocs.com/c/watermark/19).
### Czy potrzebuję tymczasowej licencji, aby używać GroupDocs.Watermark dla .NET?
 Jeśli potrzebujesz dodatkowych funkcji lub rozszerzonego użytkowania, możesz uzyskać tymczasową licencję od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę kupić pełną licencję na GroupDocs.Watermark dla .NET?
 Pełną licencję można kupić w witrynie GroupDocs[Tutaj](https://purchase.groupdocs.com/buy).