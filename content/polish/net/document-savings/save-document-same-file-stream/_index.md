---
title: Zapisz dokument w tym samym pliku lub strumieniu
linktitle: Zapisz dokument w tym samym pliku lub strumieniu
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do dokumentów za pomocą Groupdocs.Watermark dla .NET. Ten przewodnik zawiera instrukcje zapewniające ochronę i integralność dokumentów.
weight: 10
url: /pl/net/document-savings/save-document-same-file-stream/
---

# Zapisz dokument w tym samym pliku lub strumieniu

## Wstęp
W dzisiejszej epoce cyfrowej dodawanie znaków wodnych do dokumentów stało się niezbędne dla ochrony własności intelektualnej i zapewnienia integralności marki. Groupdocs.Watermark dla .NET oferuje solidne rozwiązanie dla programistów, którzy chcą bezproblemowo osadzać znaki wodne w dokumentach. Ten kompleksowy przewodnik przeprowadzi Cię przez etapy zapisywania dokumentu ze znakiem wodnym w tym samym pliku lub strumieniu przy użyciu Groupdocs.Watermark dla .NET.
## Warunki wstępne
Zanim zagłębisz się w samouczek, upewnij się, że posiadasz następujące elementy:
1. Środowisko programistyczne: Visual Studio zainstalowane na Twoim komputerze.
2. .NET Framework: Upewnij się, że masz .NET Framework 4.0 lub nowszy.
3.  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj najnowszą wersję z[strona](https://releases.groupdocs.com/Watermark/net/).
4.  Licencja: Uzyskaj tymczasową lub stałą licencję od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
## Importuj przestrzenie nazw
Aby rozpocząć korzystanie z Groupdocs.Watermark w projekcie .NET, musisz zaimportować niezbędne przestrzenie nazw:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Skonfiguruj swój projekt
Zanim dodamy znaki wodne do naszych dokumentów, musimy skonfigurować nasz projekt .NET. Oto jak:
1. Utwórz nowy projekt: Otwórz program Visual Studio i utwórz nową aplikację konsolową.
2. Dodaj odwołanie do Groupdocs.Watermark: Kliknij projekt prawym przyciskiem myszy w Eksploratorze rozwiązań, wybierz opcję „Zarządzaj pakietami NuGet” i zainstaluj pakiet Groupdocs.Watermark.
## Krok 2: Skopiuj dokument do nowej lokalizacji
Aby uniknąć bezpośredniej zmiany oryginalnego dokumentu, dobrą praktyką jest najpierw skopiowanie go do nowej lokalizacji. Oto jak to zrobić:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Krok 3: Zainicjuj znak wodny
Teraz, gdy mamy już skopiowany dokument, możemy zainicjować klasę Watermarker, aby dodać nasz znak wodny:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Znak wodny znajduje się tutaj
}
```
## Krok 4: Utwórz i dodaj tekstowy znak wodny
Następnie tworzymy tekstowy znak wodny i dodajemy go do naszego dokumentu:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Krok 5: Zapisz dokument
Na koniec zapisz dokument z zastosowanym znakiem wodnym:
```csharp
watermarker.Save();
```
## Wniosek
Dodawanie znaków wodnych do dokumentów przy użyciu programu Groupdocs dla platformy .NET jest proste i wydajne. Wykonując czynności opisane powyżej, możesz bez wysiłku chronić swoje dokumenty i zachować ich integralność. Więcej szczegółów można znaleźć w[dokumentacja](https://tutorials.groupdocs.com/Watermark/net/).
## Często zadawane pytania
### Czy mogę użyć obrazu jako znaku wodnego zamiast tekstu?
Tak, Groupdocs.Watermark umożliwia używanie obrazów, kształtów i tekstu jako znaków wodnych.
### Jak usunąć znak wodny z dokumentu?
 Znak wodny można usunąć, uzyskując dostęp do kolekcji znaków wodnych w dokumencie i korzystając z opcji`Remove` metoda.
### Czy można dostosować wygląd znaku wodnego?
Absolutnie. Możesz dostosować czcionkę, rozmiar, kolor i położenie znaku wodnego.
### Czy mogę zastosować wiele znaków wodnych do jednego dokumentu?
 Tak, możesz dodać wiele znaków wodnych, dzwoniąc pod numer`Add` metodę wielokrotnie z różnymi obiektami znaku wodnego.
### Czy Groupdocs.Watermark jest kompatybilny ze wszystkimi formatami dokumentów?
Groupdocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, PPTX i wiele innych.