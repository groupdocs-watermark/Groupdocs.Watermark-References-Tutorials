---
title: Dodaj znak wodny obrazu kafelkowego
linktitle: Dodaj znak wodny obrazu kafelkowego
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać do dokumentów znaki wodne w postaci sąsiadujących obrazów przy użyciu programu GroupDocs.Watermark dla platformy .NET. Łatwe, wydajne i konfigurowalne.
type: docs
weight: 10
url: /pl/net/image-watermarkings/add-tiled-image-watermark/
---
## Wstęp
GroupDocs.Watermark dla .NET to potężny interfejs API, który umożliwia programistom programowe dodawanie, usuwanie i wyszukiwanie znaków wodnych w różnych formatach dokumentów. W tym samouczku przeprowadzimy Cię przez proces dodawania znaku wodnego z obrazem kafelkowym do dokumentów przy użyciu programu GroupDocs.Watermark dla platformy .NET.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące elementy:
- Podstawowa znajomość języka programowania C#.
- Program Visual Studio zainstalowany w systemie.
- Do Twojego projektu dodano bibliotekę GroupDocs.Watermark for .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/Watermark/net/).

## Importuj przestrzenie nazw
Pamiętaj, aby zaimportować niezbędne przestrzenie nazw na początku pliku C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Ustaw ścieżkę dokumentu i katalog wyjściowy
Zdefiniuj ścieżkę dokumentu wejściowego i katalog, w którym chcesz zapisać dokument wyjściowy:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Zastępować`"Your Document Path"` z bezwzględną lub względną ścieżką do dokumentu wejściowego.
## Krok 2: Zainicjuj obiekt znaku wodnego
Utwórz obiekt Watermarker, korzystając ze ścieżki dokumentu wejściowego:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Dodaj tutaj znak wodny
}
```
## Krok 3: Dodaj znak wodny obrazu kafelkowego
Utwórz instancję obiektu ImageWatermark ze ścieżką do pliku obrazu, którego chcesz użyć jako znaku wodnego:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Skonfiguruj opcje kafelków
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Dodaj znak wodny do dokumentu
    watermarker.Add(watermark);
    // Zapisz zmodyfikowany dokument
    watermarker.Save(outputFileName);
}
```
 Zastępować`"Path to Your Image"` z rzeczywistą ścieżką do pliku obrazu znaku wodnego.

## Wniosek
Wykonując poniższe kroki, możesz łatwo dodać do swoich dokumentów znak wodny z obrazem sąsiadującym za pomocą programu GroupDocs.Watermark dla platformy .NET. Eksperymentuj z różnymi opcjami i konfiguracjami, aby osiągnąć pożądany rezultat.
## Często zadawane pytania
### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?
Tak, możesz dodać wiele znaków wodnych różnych typów do dokumentu za pomocą GroupDocs.Watermark dla .NET.
### Czy GroupDocs.Watermark obsługuje wszystkie formaty dokumentów?
GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i wiele innych.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Czy mogę dostosować wygląd znaku wodnego?
Tak, możesz dostosować różne aspekty znaku wodnego, takie jak położenie, rozmiar, obrót, przezroczystość itp.
### Czy GroupDocs.Watermark oferuje wsparcie techniczne?
 Tak, możesz uzyskać pomoc techniczną na forum GroupDocs.Watermark[Tutaj](https://forum.groupdocs.com/c/watermark/19).