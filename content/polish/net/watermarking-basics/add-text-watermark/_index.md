---
title: Dodaj tekstowy znak wodny
linktitle: Dodaj tekstowy znak wodny
second_title: GroupDocs.Watermark API .NET
description: Z tego przewodnika krok po kroku dowiesz się, jak dodawać tekstowe znaki wodne do dokumentów za pomocą Groupdocs.
weight: 11
url: /pl/net/watermarking-basics/add-text-watermark/
---

# Dodaj tekstowy znak wodny

## Wstęp
GroupDocs.Watermark dla .NET to potężna biblioteka, która umożliwia programistom dodawanie, wyszukiwanie i usuwanie znaków wodnych z różnych formatów dokumentów w aplikacjach .NET. W tym samouczku skupimy się na dodawaniu tekstowego znaku wodnego do dokumentu za pomocą GroupDocs.Watermark.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1. Podstawowa znajomość języka programowania C#.
2. Program Visual Studio zainstalowany w systemie.
3.  Zainstalowana biblioteka GroupDocs.Watermark dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/Watermark/net/).

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do projektu C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Zdefiniuj ścieżkę dokumentu i katalog wyjściowy
Zdefiniuj ścieżkę do dokumentu wejściowego i katalog wyjściowy, w którym zostanie zapisany dokument ze znakiem wodnym.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Zastępować`"Your Document Path"` z bezwzględną lub względną ścieżką do dokumentu wejściowego, na przykład:`@"C:\Docs\document.pdf"`. Określ także katalog, w którym chcesz zapisać dokument ze znakiem wodnym.
## Krok 2: Dodaj tekstowy znak wodny
 Utwórz instancję`Watermarker` class ze ścieżką dokumentu wejściowego. Następnie utwórz plik`TextWatermark` obiekt z żądanymi ustawieniami tekstu i czcionki.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Wniosek
tym samouczku nauczyliśmy się, jak dodać tekstowy znak wodny do dokumentu za pomocą GroupDocs.Watermark dla .NET. Dzięki intuicyjnemu interfejsowi API programiści mogą z łatwością manipulować znakami wodnymi w różnych formatach dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Watermark dla .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word, Excel, PowerPoint i wiele innych.
### Czy mogę dostosować wygląd tekstowego znaku wodnego?
Tak, możesz dostosować różne właściwości, takie jak czcionka, kolor, wyrównanie i przezroczystość tekstowego znaku wodnego.
### Czy GroupDocs.Watermark zapewnia obsługę usuwania znaków wodnych z dokumentów?
Tak, GroupDocs.Watermark oferuje funkcję wyszukiwania i usuwania znaków wodnych z dokumentów.
### Czy przed zakupem mogę wypróbować GroupDocs.Watermark dla .NET?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Watermark?
 Pomoc techniczną można uzyskać odwiedzając witrynę[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).