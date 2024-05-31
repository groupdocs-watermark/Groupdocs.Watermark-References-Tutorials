---
title: Dodaj znak wodny do określonej strony w dokumentach programu Word
linktitle: Dodaj znak wodny do określonej strony w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do określonych stron w dokumentach programu Word przy użyciu programu GroupDocs dla platformy .NET. Chroń swoje treści bez wysiłku.
type: docs
weight: 14
url: /pl/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## Wstęp
Znakowanie dokumentów wodnych jest kluczowym aspektem bezpieczeństwa dokumentów i budowania marki. W tym samouczku omówimy, jak dodać znak wodny do określonej strony w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
- Podstawowa znajomość programowania w języku C#.
- Zainstalowano środowisko IDE programu Visual Studio.
- GroupDocs.Watermark dla .NET zainstalowany w Twoim projekcie.

## Importowanie przestrzeni nazw
Zanim zagłębisz się w kod, pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod trafi tutaj
}
```
## Krok 2: Dodaj znak wodny
```csharp
// Zdefiniuj tekst i styl znaku wodnego
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Dodaj znak wodny do ostatniej strony
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Krok 3: Zapisz dokument
```csharp
// Zapisz dokument ze znakiem wodnym
watermarker.Save(outputFileName);
```

## Wniosek
tym samouczku dowiedzieliśmy się, jak dodać znak wodny do określonej strony w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Wykonując poniższe kroki, możesz skutecznie chronić swoje dokumenty i w razie potrzeby dodawać elementy marki.
## Często zadawane pytania
### Czy mogę dostosować tekst i styl znaku wodnego?
Tak, możesz dostosować tekst, czcionkę, rozmiar, kolor i położenie znaku wodnego zgodnie ze swoimi wymaganiami.
### Czy GroupDocs.Watermark dla .NET jest kompatybilny z innymi formatami dokumentów?
Tak, GroupDocs.Watermark obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint, PDF i inne.
### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?
Oczywiście możesz dodać wiele znaków wodnych o różnej treści i stylach do tego samego dokumentu.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz poznać funkcje GroupDocs.Watermark w ramach bezpłatnej wersji próbnej. Aby rozpocząć, wystarczy odwiedzić podany link[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Watermark?
 Możesz znaleźć przydatne zasoby i uzyskać pomoc techniczną[Tutaj](https://forum.groupdocs.com/c/watermark/19)na forum GroupDocs.Watermark. Kliknij podany link, aby dołączyć do społeczności.