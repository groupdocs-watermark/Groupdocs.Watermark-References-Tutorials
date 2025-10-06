---
title: Dodaj znak wodny do obrazów adnotacji w formacie PDF
linktitle: Dodaj znak wodny do obrazów adnotacji w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak chronić dokumenty PDF, dodając znaki wodne do obrazów adnotacji za pomocą Groupdocs.Watermark dla .NET.
weight: 17
url: /pl/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
type: docs
---
# Dodaj znak wodny do obrazów adnotacji w formacie PDF

## Wstęp
W tym samouczku omówimy, jak dodawać znaki wodne do obrazów adnotacji w dokumentach PDF przy użyciu narzędzia Groupdocs.Watermark dla platformy .NET. Znak wodny ma kluczowe znaczenie dla ochrony dokumentów przed nieuprawnionym użyciem lub dystrybucją. Postępując zgodnie z tym przewodnikiem krok po kroku, dowiesz się, jak skutecznie stosować tekstowe znaki wodne do obrazów adnotacji w plikach PDF.
## Warunki wstępne
Przed kontynuowaniem upewnij się, że masz następujące elementy:
1. Podstawowa znajomość języka programowania C#.
2. Zainstalowano bibliotekę Groupdocs.Watermark dla .NET.
3. Dostęp do środowiska programistycznego, takiego jak Visual Studio.
4. Dokument PDF z obrazami adnotacji do znaku wodnego.

## Importowanie przestrzeni nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego kodu C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Pobierz zawartość PDF i zainicjuj znak wodny
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Zainicjuj obrazowy lub tekstowy znak wodny
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Krok 3: Iteruj po stronach PDF i obrazach adnotacji
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Dodaj znak wodny do obrazu
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Krok 4: Zapisz dokument ze znakiem wodnym
```csharp
    watermarker.Save(outputFileName);
}
```
Po wykonaniu tych kroków do obrazów adnotacji w dokumencie PDF zostanie dodany określony znak wodny.

## Wniosek
Dodawanie znaków wodnych do obrazów adnotacji w plikach PDF ma kluczowe znaczenie dla ochrony integralności dokumentów i zapobiegania ich niewłaściwemu wykorzystaniu. Dzięki Groupdocs.Watermark dla .NET proces ten staje się prosty i wydajny, umożliwiając skuteczną ochronę plików PDF.
## Często zadawane pytania
### Czy mogę dodać wiele znaków wodnych do tego samego dokumentu PDF?
Tak, możesz dodać wiele znaków wodnych do tego samego dokumentu PDF za pomocą Groupdocs.Watermark dla .NET.
### Czy Groupdocs.Watermark obsługuje inne formaty dokumentów oprócz PDF?
Tak, Groupdocs Watermark obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy można dostosować wygląd znaku wodnego?
Oczywiście możesz dostosować tekst, czcionkę, kolor, rozmiar i położenie znaku wodnego zgodnie ze swoimi preferencjami.
### Czy mogę usunąć znaki wodne z dokumentów PDF za pomocą Groupdocs.Watermark?
Tak, Groupdocs.Watermark zapewnia funkcję łatwego usuwania znaków wodnych z dokumentów PDF.
### Czy dostępna jest bezpłatna wersja próbna programu Groupdocs.Watermark dla platformy .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej Groupdocs.Watermark dla .NET na stronie internetowej.