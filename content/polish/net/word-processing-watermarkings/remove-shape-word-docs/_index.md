---
title: Usuń kształt w dokumentach programu Word
linktitle: Usuń kształt w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak usuwać kształty z dokumentów programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Łatwa, wydajna i wydajna manipulacja dokumentami.
weight: 30
url: /pl/net/word-processing-watermarkings/remove-shape-word-docs/
---

# Usuń kształt w dokumentach programu Word

## Wstęp
W dziedzinie przetwarzania i manipulacji dokumentami GroupDocs.Watermark dla .NET jawi się jako potężny zestaw narzędzi, umożliwiający programistom bezproblemową integrację funkcji znaku wodnego z aplikacjami .NET. W tym artykule omówiono zawiłości wykorzystania programu GroupDocs.Watermark dla platformy .NET do usuwania kształtów z dokumentów programu Word. Postępując zgodnie z przewodnikiem krok po kroku, programiści mogą zrozumieć proces z łatwością i wydajnością.
## Warunki wstępne
Przed rozpoczęciem usuwania kształtów z dokumentów programu Word za pomocą programu GroupDocs.Watermark dla platformy .NET upewnij się, że spełnione są następujące wymagania wstępne:
### 1. Uzyskaj GroupDocs.Watermark dla .NET
 Rozpocznij od nabycia biblioteki GroupDocs.Watermark dla .NET. Bibliotekę można pobrać ze strony[strona wydania](https://releases.groupdocs.com/Watermark/net/).
### 2. Znajomość programowania .NET
Niezbędne jest podstawowe zrozumienie programowania .NET. Upewnij się, że potrafisz programować w języku C# i masz podstawową wiedzę na temat pracy z bibliotekami i zależnościami w ekosystemie .NET.
### 3. Zintegrowane środowisko programistyczne (IDE)
Zainstaluj w swoim systemie środowisko IDE, takie jak Visual Studio, zapewniające sprzyjające środowisko do programowania .NET. 
### 4. Przykładowy dokument Word
Przygotuj przykładowy dokument programu Word zawierający kształty, które chcesz usunąć. Dokument ten posłuży jako poligon doświadczalny dla Twojego wdrożenia.

## Importuj przestrzenie nazw
Aby rozpocząć proces usuwania kształtów w dokumentach programu Word za pomocą GroupDocs.Watermark dla .NET, zaimportuj niezbędne przestrzenie nazw do swojego projektu:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
Rozpocznij od określenia ścieżki do dokumentu programu Word, którym chcesz manipulować, i utwórz nazwę pliku wyjściowego dla przetworzonego dokumentu:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 2: Zainicjuj znak wodny
 Zainicjuj a`Watermarker` obiektu, przekazując ścieżkę dokumentu i opcjonalne opcje ładowania:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 3: Uzyskaj dostęp do treści dokumentu
Pobierz zawartość dokumentu programu Word, aby uzyskać dostęp do jego sekcji i kształtów:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Krok 4: Usuń kształt według indeksu
 Usuń kształt z dokumentu, określając jego indeks w pliku`Shapes` kolekcja:
```csharp
content.Sections[0].Shapes.RemoveAt(0);
```
## Krok 5: Usuń kształt przez odniesienie
 Alternatywnie możesz usunąć kształt, bezpośrednio odwołując się do niego w pliku`Shapes` kolekcja:
```csharp
content.Sections[0].Shapes.Remove(content.Sections[0].Shapes[0]);
```
## Krok 6: Zapisz dokument
Zapisz zmodyfikowany dokument w określonym pliku wyjściowym:
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Podsumowując, GroupDocs.Watermark dla .NET umożliwia programistom łatwe manipulowanie dokumentami programu Word. Postępując zgodnie z tym szczegółowym przewodnikiem, możesz bezproblemowo usuwać kształty z dokumentów programu Word, usprawniając przepływ pracy podczas przetwarzania dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Watermark for .NET obsługuje inne formaty dokumentów niż Word?
Tak, GroupDocs.Watermark dla .NET obsługuje szeroką gamę formatów dokumentów, w tym Excel, PowerPoint, PDF i inne.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Watermark dla .NET z poziomu[strona wydania](https://releases.groupdocs.com/).
### Jak mogę uzyskać tymczasowe licencje na GroupDocs.Watermark dla .NET?
 Tymczasowe licencje na GroupDocs.Watermark dla .NET można uzyskać w witrynie[strona licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć dokumentację i wsparcie dla GroupDocs.Watermark dla .NET?
 Dokumentacja i zasoby pomocy technicznej dla GroupDocs.Watermark dla .NET są dostępne na stronie[forum](https://forum.groupdocs.com/c/watermark/19) I[Strona referencyjna](https://tutorials.groupdocs.com/Watermark/net/).
### Jakie wersje .NET są kompatybilne z GroupDocs.Watermark?
GroupDocs.Watermark dla .NET jest kompatybilny z różnymi wersjami .NET, w tym .NET Framework i .NET Core.