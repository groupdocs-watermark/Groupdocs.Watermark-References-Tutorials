---
title: Dodaj znaki wodne do pliku PDF
linktitle: Dodaj znaki wodne do pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać tekstowe i graficzne znaki wodne do plików PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET, korzystając z naszego obszernego przewodnika krok po kroku.
type: docs
weight: 14
url: /pl/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## Wstęp
Czy chcesz dodać znaki wodne do plików PDF, aby chronić dokumenty lub oznaczyć je swoim logo? Nie szukaj dalej! W tym samouczku szczegółowo omówimy proces używania programu GroupDocs.Watermark dla platformy .NET w celu dodawania tekstowych i graficznych znaków wodnych do plików PDF. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik przeprowadzi Cię przez każdy krok, zapewniając, że możesz łatwo i precyzyjnie dodawać znaki wodne.
## Warunki wstępne
Zanim zaczniemy, upewnijmy się, że masz wszystko, czego potrzebujesz, wraz z tym samouczkiem:
-  GroupDocs.Watermark dla .NET: Upewnij się, że masz zainstalowaną najnowszą wersję. Możesz[Pobierz to tutaj](https://releases.groupdocs.com/Watermark/net/).
- Środowisko programistyczne .NET: Visual Studio lub dowolne inne IDE obsługujące .NET.
- Podstawowa znajomość języka C#: Zrozumienie podstaw programowania w języku C# pomoże Ci z łatwością wykonać poniższe kroki.
- Dokument PDF: Przygotuj przykładowy dokument PDF do dodania znaku wodnego.
- Obraz znaku wodnego: Jeśli dodajesz obrazowy znak wodny, przygotuj plik obrazu.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#. Umożliwi to dostęp do funkcjonalności GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Podzielmy teraz proces na łatwe do wykonania etapy.
## Krok 1: Załaduj swój dokument PDF
Pierwszym krokiem jest załadowanie dokumentu PDF do znaku wodnego. Oto jak możesz to zrobić:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dalsze kroki zostaną dodane tutaj
}
```
## Krok 2: Dodaj tekstowy znak wodny do pierwszej strony
Następnie dodamy tekstowy znak wodny do pierwszej strony pliku PDF. Postępuj zgodnie z tymi instrukcjami:
```csharp
// Dodaj tekstowy znak wodny na pierwszej stronie
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Dodanie tekstowego znaku wodnego może pomóc chronić dokument przed nieupoważnionym użyciem lub po prostu oznaczyć go marką. Wyobraź sobie, że stemplujesz swój dokument niewidzialną pieczęcią autentyczności.
## Krok 3: Dodaj znak wodny obrazu do drugiej strony
Dodajmy teraz obrazowy znak wodny do drugiej strony. Jest to szczególnie przydatne w przypadku logo lub graficznych znaków wodnych.
```csharp
// Dodaj znak wodny obrazu do drugiej strony
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Obrazowe znaki wodne mogą nadać Twoim dokumentom profesjonalny wygląd i zapewnić, że Twoja marka będzie zawsze widoczna. To jak dodanie swojego podpisu do każdej strony.
## Krok 4: Zapisz plik PDF ze znakiem wodnym
Ostatnim krokiem po dodaniu znaków wodnych jest zapisanie pliku PDF ze znakiem wodnym w wybranej lokalizacji.
```csharp
watermarker.Save(outputFileName);
```
Zapisanie dokumentu kończy wszystkie wprowadzone zmiany. To moment, w którym Twoje wysiłki zamieniają się w namacalny rezultat, gotowy do użycia lub dystrybucji.
## Wniosek
Gratulacje! Pomyślnie dodałeś tekstowe i graficzne znaki wodne do pliku PDF przy użyciu programu GroupDocs.Watermark dla .NET. Proces ten jest nie tylko prosty, ale także można go w dużym stopniu dostosować do konkretnych potrzeb. Niezależnie od tego, czy chronisz swoje dokumenty, czy też je oznakujesz, znaki wodne są potężnym narzędziem do Twojej dyspozycji.
## Często zadawane pytania
### Czy mogę dodać wiele znaków wodnych do tej samej strony?
 Tak, możesz dodać wiele znaków wodnych do tej samej strony, wywołując metodę`Add` metodę wielokrotnie z różnymi obiektami znaku wodnego.
### Jak mogę dostosować wygląd tekstowego znaku wodnego?
 Możesz dostosować tekstowy znak wodny, dostosowując właściwości, takie jak czcionka, rozmiar, kolor i krycie, za pomocą przycisku`TextWatermark` obiekt.
### Czy można dodać znak wodny tylko do określonych stron pliku PDF?
 Tak, możesz określić, które strony mają być znakami wodnymi, ustawiając opcję`PageIndex` nieruchomość w`PdfArtifactWatermarkOptions`.
### Czy mogę usunąć znaki wodne z pliku PDF?
Tak, GroupDocs.Watermark zapewnia funkcję wyszukiwania i usuwania znaków wodnych z dokumentów PDF.
### Jak uzyskać tymczasową licencję na GroupDocs.Watermark?
Licencję tymczasową możesz uzyskać odwiedzając stronę[strona licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/).