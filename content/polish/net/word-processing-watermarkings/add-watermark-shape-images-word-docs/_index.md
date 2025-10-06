---
title: Dodaj znak wodny do obrazów kształtów w dokumentach programu Word
linktitle: Dodaj znak wodny do obrazów kształtów w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do kształtowania obrazów w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET. Zwiększ bezpieczeństwo dokumentów dzięki temu samouczkowi.
weight: 17
url: /pl/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# Dodaj znak wodny do obrazów kształtów w dokumentach programu Word

## Wstęp
W tym samouczku omówimy, jak dodać znak wodny do kształtowania obrazów w dokumentach programu Word za pomocą programu GroupDocs.Watermark dla platformy .NET. Znak wodny jest kluczowym aspektem ochrony dokumentów, szczególnie w przypadku informacji wrażliwych lub poufnych. Dodając znaki wodne do obrazów kształtów, możesz zapewnić integralność i bezpieczeństwo swoich dokumentów.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark z[strona pobierania](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Przygotuj dokument programu Word, w którym chcesz dodać znak wodny.
3. Środowisko programistyczne: skonfiguruj preferowane środowisko programistyczne .NET.
## Importuj przestrzenie nazw
Przed napisaniem kodu pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
Najpierw zdefiniuj ścieżkę do swojego dokumentu i podaj nazwę pliku wyjściowego:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 2: Zainicjuj znak wodny
 Utwórz instancję a`Watermarker` obiekt, podając ścieżkę dokumentu i opcjonalne opcje ładowania:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dodaj tutaj logikę znaku wodnego
}
```
## Krok 3: Utwórz tekstowy znak wodny
Zdefiniuj tekstowy znak wodny z żądanymi właściwościami, takimi jak tekst, czcionka, wyrównanie, obrót, rozmiar itp.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Zastosuj znak wodny do obrazów kształtów
Przeglądaj sekcje i kształty dokumentu, aby zidentyfikować obrazy kształtów i dodać znak wodny:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Krok 5: Zapisz dokument
Zapisz dokument z dodanym znakiem wodnym do określonego pliku wyjściowego:
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
tym samouczku nauczyliśmy się, jak dodawać znaki wodne do kształtowania obrazów w dokumentach programu Word za pomocą GroupDocs.Watermark dla .NET. Postępując zgodnie ze szczegółowym przewodnikiem i wykorzystując zaawansowane funkcje GroupDocs.Watermark, możesz skutecznie zwiększyć bezpieczeństwo i ochronę swoich dokumentów.
## Często zadawane pytania
### Czy mogę dostosować wygląd tekstu znaku wodnego?
Tak, możesz dostosować różne właściwości, takie jak czcionka, rozmiar, kolor, kąt obrotu i wyrównanie, aby dostosować znak wodny zgodnie z własnymi preferencjami.
### Czy GroupDocs.Watermark obsługuje inne formaty dokumentów oprócz programu Word?
Tak, GroupDocs.Watermark zapewnia obsługę szerokiej gamy formatów dokumentów, w tym PDF, Excel, PowerPoint i innych.
### Czy można dodać wiele znaków wodnych do jednego dokumentu?
Oczywiście możesz dodać wiele znaków wodnych o różnej treści, stylach i pozycjach w tym samym dokumencie.
### Czy mogę usunąć znaki wodne z dokumentów za pomocą GroupDocs.Watermark?
Tak, GroupDocs.Watermark oferuje funkcje umożliwiające skuteczne wykrywanie i usuwanie znaków wodnych z dokumentów.
### Czy GroupDocs.Watermark zapewnia zgodność między platformami?
Tak, GroupDocs.Watermark jest kompatybilny z .NET Framework, .NET Core i .NET Standard, zapewniając bezproblemową integrację na różnych platformach.