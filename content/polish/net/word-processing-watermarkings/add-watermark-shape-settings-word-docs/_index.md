---
title: Dodaj znak wodny z ustawieniami kształtu w dokumentach programu Word
linktitle: Dodaj znak wodny z ustawieniami kształtu w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne z ustawieniami kształtu do dokumentów programu Word za pomocą programu GroupDocs dla platformy .NET. Skutecznie chroń swoje dokumenty.
weight: 20
url: /pl/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Wstęp
W tym samouczku omówimy proces dodawania znaku wodnego z ustawieniami kształtu do dokumentów programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  Zainstalowano GroupDocs.Watermark dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Podstawowa znajomość programowania w języku C#.
3. Znajomość przetwarzania dokumentów w programie Word.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do wymaganych klas i metod.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
Załaduj dokument programu Word, w którym chcesz dodać znak wodny.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tutaj znajduje się kod dodawania znaku wodnego
}
```
## Krok 2: Dodaj znak wodny
 Utwórz instancję a`TextWatermark` obiekt i określ tekst, którego chcesz użyć jako znaku wodnego.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Krok 3: Dostosuj ustawienia znaku wodnego
Ustaw różne ustawienia znaku wodnego, takie jak wyrównanie, kąt obrotu, kolor i krycie.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Krok 4: Zdefiniuj opcje sekcji znaku wodnego
Zdefiniuj opcje sekcji znaku wodnego, takie jak nazwa kształtu i tekst alternatywny.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Krok 5: Dodaj znak wodny do dokumentu
Dodaj znak wodny do dokumentu z określonymi opcjami.
```csharp
watermarker.Add(watermark, options);
```
## Krok 6: Zapisz dokument
Zapisz dokument z dodanym znakiem wodnym.
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Dodawanie znaków wodnych z ustawieniami kształtu do dokumentów programu Word za pomocą programu GroupDocs dla platformy .NET jest prostym procesem. Wykonując kroki opisane w tym samouczku, możesz skutecznie chronić swoje dokumenty za pomocą niestandardowych znaków wodnych.
## Często zadawane pytania
### Czy mogę dodać wiele znaków wodnych do tego samego dokumentu?
Tak, możesz dodać wiele znaków wodnych z różnymi ustawieniami do tego samego dokumentu.
### Czy GroupDocs.Watermark obsługuje inne formaty dokumentów oprócz programu Word?
Tak, GroupDocs.Watermark obsługuje różne formaty dokumentów, w tym Excel, PowerPoint, PDF i inne.
### Czy mogę bardziej dostosować wygląd znaku wodnego?
Oczywiście możesz dostosować różne parametry, takie jak rozmiar czcionki, styl, kolor i położenie, do swoich potrzeb.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz uzyskać bezpłatną wersję próbną od[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć pomoc dotyczącą GroupDocs.Watermark?
 Pomoc i pytania można znaleźć na forum GroupDocs[Tutaj](https://forum.groupdocs.com/c/watermark/19).