---
title: Dodaj znak wodny z adnotacją tylko do druku do pliku PDF
linktitle: Dodaj znak wodny z adnotacją tylko do druku do pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne z adnotacjami przeznaczonymi tylko do druku do plików PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET. Bez wysiłku zwiększ bezpieczeństwo dokumentów i branding.
weight: 13
url: /pl/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Dodaj znak wodny z adnotacją tylko do druku do pliku PDF

## Wstęp
W tym samouczku omówimy proces dodawania znaku wodnego adnotacji przeznaczonej tylko do wydruku do pliku PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET. Znak wodny w dokumentach jest kluczowym aspektem bezpieczeństwa dokumentów i budowania marki, a GroupDocs.Watermark zapewnia programistom .NET płynne rozwiązanie umożliwiające osiągnięcie tego celu.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:
- Podstawowa znajomość języka programowania C#.
- Program Visual Studio zainstalowany na Twoim komputerze.
- Biblioteka GroupDocs.Watermark for .NET zainstalowana w Twoim projekcie.

## Importuj przestrzenie nazw
Na początek zaimportuj niezbędne przestrzenie nazw:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
 Najpierw musisz załadować dokument PDF, do którego chcesz dodać znak wodny. Zastępować`"Your Document Path"` ze ścieżką do pliku PDF i`"Your Document Directory"` z katalogiem, w którym chcesz zapisać plik wyjściowy.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kod znaku wodnego zostanie dodany tutaj
}
```
## Krok 2: Dodaj znak wodny
Następnie utwórz tekstowy obiekt znaku wodnego z żądanym tekstem i czcionką. Ustawić`isPrintOnly` Do`true` aby mieć pewność, że znak wodny będzie widoczny tylko podczas drukowania dokumentu, a nie w trybie przeglądania.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Krok 3: Skonfiguruj opcje znaku wodnego
Zdefiniuj opcje znaku wodnego, takie jak indeks strony, na której powinien zostać dodany znak wodny, i określenie go jako adnotacji przeznaczonej tylko do druku.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Krok 4: Zastosuj znak wodny
Dodaj znak wodny do dokumentu, korzystając z określonych opcji i zapisz plik wyjściowy.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodać znak wodny adnotacji przeznaczonej tylko do wydruku do dokumentu PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET. Dzięki temu programiści mogą z łatwością zwiększać bezpieczeństwo dokumentów i branding.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest zgodny z innymi formatami dokumentów oprócz PDF?
Tak, GroupDocs obsługuje różne formaty dokumentów, takie jak Word, Excel, PowerPoint i obrazy.
### Czy mogę dostosować wygląd znaku wodnego?
Z pewnością GroupDocs.Watermark zapewnia szerokie opcje dostosowywania tekstu znaku wodnego, czcionki, koloru, rozmiaru i położenia.
### Czy GroupDocs.Watermark oferuje możliwości przetwarzania wsadowego?
Oczywiście programiści mogą oznaczać znakami wodnymi wiele dokumentów jednocześnie, korzystając z funkcji przetwarzania wsadowego.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark?
Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Watermark, korzystając z podanego łącza.
### Jak mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Watermark?
Możesz zwrócić się o pomoc techniczną na forum GroupDocs.Watermark dostępnym pod podanym linkiem pomocy technicznej.