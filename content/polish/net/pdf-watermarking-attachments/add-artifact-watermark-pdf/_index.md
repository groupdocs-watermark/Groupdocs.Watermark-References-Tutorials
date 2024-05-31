---
title: Dodaj znak wodny artefaktu do pliku PDF
linktitle: Dodaj znak wodny artefaktu do pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak bez wysiłku dodawać znaki wodne artefaktów do plików PDF za pomocą Groupdocs.Watermark dla .NET. Chroń swoje dokumenty z łatwością.
type: docs
weight: 11
url: /pl/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Wstęp
Dodawanie znaków wodnych do plików PDF jest kluczowym aspektem zarządzania dokumentami, zwłaszcza jeśli chodzi o ochronę własności intelektualnej lub dokumentów związanych z marką. Groupdocs.Watermark dla .NET zapewnia niezawodne rozwiązanie do łatwego dodawania znaków wodnych do plików PDF. W tym samouczku omówimy krok po kroku proces dodawania znaku wodnego artefaktu do plików PDF.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj Groupdocs.Watermark dla .NET z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: skonfiguruj środowisko programistyczne .NET.
3. Dokument PDF: Przygotuj dokument PDF, do którego chcesz dodać znak wodny.
4. Katalog wyjściowy: Utwórz katalog, w którym zostanie zapisany plik PDF ze znakiem wodnym.

## Importowanie przestrzeni nazw
Na początek zaimportuj niezbędne przestrzenie nazw do swojego projektu C#:
```csharp
using GroupDocs.Watermark.Common;
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
## Krok 2: Zdefiniuj opcje znaku wodnego
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Krok 3: Dodaj tekstowy znak wodny
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Krok 4: Dodaj znak wodny obrazu
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Krok 5: Zapisz plik PDF ze znakiem wodnym
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
tym samouczku nauczyliśmy się, jak dodawać znaki wodne artefaktów do plików PDF przy użyciu narzędzia Groupdocs.Watermark dla platformy .NET. Wykonując poniższe kroki, możesz bezproblemowo zintegrować funkcję znaku wodnego z aplikacjami .NET, zapewniając bezpieczeństwo i integralność dokumentów.
## Często zadawane pytania
### Czy mogę dostosować wygląd tekstowego znaku wodnego?
Tak, możesz dostosować różne aspekty, takie jak czcionka, rozmiar, kolor i wyrównanie tekstowego znaku wodnego, zgodnie z własnymi preferencjami.
### Czy Groupdocs.Watermark obsługuje dodawanie znaków wodnych do innych formatów dokumentów?
Tak, Groupdocs.Watermark obsługuje dodawanie znaków wodnych do szerokiej gamy formatów dokumentów, w tym Word, Excel, PowerPoint i innych.
### Czy dostępna jest wersja próbna programu Groupdocs.Watermark dla platformy .NET?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z Groupdocs.Watermark?
 Pomoc można uzyskać na forum społeczności Groupdocs[Tutaj](https://forum.groupdocs.com/c/watermark/19).
### Czy mogę używać Groupdocs.Watermark do celów komercyjnych?
Tak, możesz kupić licencję do użytku komercyjnego od[Tutaj](https://purchase.groupdocs.com/buy).