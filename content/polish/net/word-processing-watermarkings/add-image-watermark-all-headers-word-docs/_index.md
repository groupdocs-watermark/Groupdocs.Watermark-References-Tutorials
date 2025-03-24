---
title: Dodaj obrazowy znak wodny do wszystkich nagłówków w dokumentach programu Word
linktitle: Dodaj obrazowy znak wodny do wszystkich nagłówków w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Z łatwością dodawaj graficzne znaki wodne do wszystkich nagłówków w dokumentach programu Word za pomocą GroupDocs.Watermark dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku ze szczegółowymi przykładami kodu.
weight: 10
url: /pl/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

# Dodaj obrazowy znak wodny do wszystkich nagłówków w dokumentach programu Word

## Wstęp
Znaki wodne mogą stanowić istotną część zarządzania dokumentami, umożliwiając osadzanie w dokumentach informacji takich jak własność, poufność czy marka. W tym samouczku omówimy kroki dodawania obrazu znaku wodnego do wszystkich nagłówków w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET. Niezależnie od tego, czy dopiero zaczynasz programować, czy jesteś doświadczonym programistą, ten przewodnik pomoże Ci z łatwością osiągnąć cele związane ze znakami wodnymi.
## Warunki wstępne
Zanim zagłębimy się w kod, upewnijmy się, że mamy wszystko, czego potrzebujemy. Oto lista kontrolna na początek:
1.  GroupDocs.Watermark dla .NET: Pobierz najnowszą wersję z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: Visual Studio lub dowolne inne IDE kompatybilne z .NET.
3. .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET Framework.
4. Przykładowy dokument programu Word: dokument programu Word, w którym chcesz dodać znak wodny.
5. Obraz znaku wodnego: plik obrazu, którego chcesz użyć jako znaku wodnego.
Gdy już je przygotujemy, możemy przystąpić do konfiguracji naszego projektu.
## Importuj przestrzenie nazw
Najpierw zaimportujmy niezbędne przestrzenie nazw. Te przestrzenie nazw zawierają klasy i metody, które pomogą nam pracować ze znakami wodnymi w naszych dokumentach.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Konfiguracja projektu
Aby rozpocząć, utwórz nową aplikację konsolową w programie Visual Studio. Dodaj odniesienia do biblioteki DLL GroupDocs.Watermark w swoim projekcie. Można to zrobić, instalując pakiet GroupDocs.Watermark NuGet.
```bash
Install-Package GroupDocs.Watermark
```
## Krok 2: Załaduj swój dokument
 Pierwszym krokiem w dodaniu znaku wodnego jest załadowanie dokumentu, w którym znak wodny zostanie dodany. Tutaj użyjemy`WordProcessingLoadOptions` aby załadować dokument Word.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kod do dodania znaku wodnego zostanie umieszczony tutaj
}
```
## Krok 3: Utwórz znak wodny obrazu
Następnie utworzymy obrazowy znak wodny. Wiąże się to z określeniem pliku obrazu, którego chcesz użyć jako znaku wodnego.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Kod do zastosowania znaku wodnego zostanie umieszczony tutaj
}
```
## Krok 4: Dodaj znak wodny do nagłówków pierwszej sekcji
 Musimy dodać znak wodny do wszystkich nagłówków w pierwszej części dokumentu Word. W tym celu używamy`WordProcessingWatermarkSectionOptions` i określ indeks sekcji.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Krok 5: Nagłówki i stopki linków
Aby mieć pewność, że znak wodny pojawi się w nagłówkach wszystkich sekcji, wszystkie pozostałe nagłówki i stopki łączymy z nagłówkami i stopkami pierwszej sekcji.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Krok 6: Zapisz dokument
Na koniec zapisujemy dokument ze znakiem wodnym w określonej ścieżce. Ten krok gwarantuje, że zmiany zostaną zapisane w nowym pliku, zachowując oryginalny dokument.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Wniosek
I masz to! Pomyślnie dodałeś obrazowy znak wodny do wszystkich nagłówków w dokumencie programu Word przy użyciu GroupDocs.Watermark dla .NET. Ta potężna biblioteka ułatwia zarządzanie znakami wodnymi i stosowanie ich do różnych typów dokumentów, zapewniając ochronę treści i profesjonalną markę.
## Często zadawane pytania
### Czy oprócz obrazów mogę używać innych typów znaków wodnych?
Tak, GroupDocs obsługuje tekst, obraz, a nawet złożone znaki wodne.
### Czy można dodać znak wodny do innych części dokumentu oprócz nagłówków?
Absolutnie! Możesz oznaczać stopki, treść, a nawet określone strony lub sekcje znakiem wodnym.
### Czy GroupDocs.Watermark obsługuje inne formaty dokumentów?
Tak, obsługuje szeroką gamę formatów, w tym pliki PDF, Excel, PowerPoint i inne.
### Czy mogę dostosować położenie i wygląd znaku wodnego?
Tak, możesz dostosować rozmiar, położenie, krycie i wiele innych właściwości znaku wodnego.
### Czy dostępna jest bezpłatna wersja próbna GroupDocs.Watermark?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).