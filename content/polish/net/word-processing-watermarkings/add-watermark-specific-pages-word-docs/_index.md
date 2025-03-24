---
title: Dodaj znak wodny do określonych stron w dokumentach programu Word
linktitle: Dodaj znak wodny do określonych stron w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak bez wysiłku dodawać znaki wodne do określonych stron w dokumentach programu Word przy użyciu narzędzia Groupdocs dla platformy .NET. Zwiększ bezpieczeństwo dokumentów i branding.
weight: 18
url: /pl/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## Wstęp
W tym samouczku omówimy proces dodawania znaków wodnych do określonych stron w dokumentach programu Word przy użyciu programu Groupdocs.Watermark dla platformy .NET. Znak wodny jest kluczowym aspektem zarządzania dokumentami, zapewniającym bezpieczeństwo i branding dokumentów. Dzięki Groupdocs.Watermark dla .NET możesz łatwo i precyzyjnie dodawać tekstowe lub graficzne znaki wodne do dokumentów programu Word.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj Groupdocs.Watermark dla .NET z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Przygotuj dokument programu Word, do którego chcesz dodać znak wodny.
3. Środowisko programistyczne: Skonfiguruj środowisko programistyczne za pomocą programu Visual Studio lub dowolnego innego narzędzia programistycznego .NET.

## Importuj przestrzenie nazw
Zanim zagłębimy się w kod, zaimportujmy niezbędne przestrzenie nazw:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Załaduj dokument
Najpierw musimy załadować dokument Word do obiektu znaku wodnego.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dodaj kod znaku wodnego, który przejdzie tutaj
}
```
## Krok 2: Dodaj znak wodny
Dodajmy teraz tekstowy znak wodny do określonych stron dokumentu.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Określ strony, na których ma zostać dodany znak wodny
};
watermarker.Add(textWatermark);
```
## Krok 3: Zapisz dokument
Na koniec zapisz dokument ze znakiem wodnym w żądanej lokalizacji.
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
W tym samouczku nauczyliśmy się, jak dodawać znaki wodne do określonych stron w dokumentach programu Word przy użyciu narzędzia Groupdocs.Watermark dla platformy .NET. Za pomocą zaledwie kilku linijek kodu możesz bez wysiłku zwiększyć bezpieczeństwo i branding swoich dokumentów.
## Często zadawane pytania
### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?
Tak, możesz dodać wiele znaków wodnych, powtarzając proces dodawania znaku wodnego dla każdego znaku wodnego.
### Czy Groupdocs.Watermark obsługuje inne formaty dokumentów oprócz programu Word?
Tak, Groupdocs Watermark obsługuje szeroką gamę formatów dokumentów, w tym PDF, Excel, PowerPoint i inne.
### Czy dostępna jest wersja próbna?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Czy mogę dostosować wygląd znaku wodnego?
Oczywiście możesz dostosować różne aspekty znaku wodnego, takie jak czcionka, rozmiar, kolor i krycie.
### Czy dostępna jest pomoc techniczna?
 Tak, pomoc techniczną i zasoby można znaleźć na forum Groupdocs[Tutaj](https://forum.groupdocs.com/c/watermark/19).