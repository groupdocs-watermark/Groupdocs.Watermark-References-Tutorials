---
title: Dodaj znak wodny obrazu ze strumienia
linktitle: Dodaj znak wodny obrazu ze strumienia
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać graficzne znaki wodne do dokumentów przy użyciu programu GroupDocs.Watermark dla platformy .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby uzyskać bezproblemową integrację znaku wodnego.
weight: 12
url: /pl/net/image-watermarkings/add-image-watermark-from-stream/
---
## Wstęp
W dziedzinie zarządzania dokumentami i bezpieczeństwa dodawanie znaków wodnych do plików ma ogromne znaczenie. Niezależnie od tego, czy chodzi o budowanie marki, ochronę praw autorskich, czy utrzymanie integralności dokumentów, znaki wodne odgrywają kluczową rolę. Na szczęście GroupDocs.Watermark dla .NET zapewnia niezawodne rozwiązanie do dodawania, usuwania i wyszukiwania znaków wodnych w różnych formatach dokumentów.
## Warunki wstępne
Zanim zagłębisz się w implementację znaków wodnych przy użyciu GroupDocs.Watermark dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Zainstaluj GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[link do pobrania](https://releases.groupdocs.com/Watermark/net/).
2. Dostęp do dokumentu: Uzyskaj dostęp do dokumentu, w którym chcesz dodać lub usunąć znaki wodne.
3. Podstawowa znajomość języka C#: Znajomość języka programowania C# jest konieczna do zrozumienia i wdrożenia dostarczonych fragmentów kodu.

## Importuj przestrzenie nazw
Przed przystąpieniem do dodawania znaków wodnych obrazu ze strumienia zaimportuj niezbędne przestrzenie nazw:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Krok 1: Zdefiniuj ścieżkę dokumentu i katalog wyjściowy
Najpierw zdefiniuj ścieżkę dokumentu, w którym chcesz dodać znak wodny i określ katalog wyjściowy przetwarzanego dokumentu.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Otwórz strumień znaku wodnego
 Otwórz plik obrazu znaku wodnego jako strumień za pomocą`File.OpenRead` metoda.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // Tutaj przejdzie logika przetwarzania znaku wodnego
}
```
## Krok 3: Dodaj znak wodny do dokumentu
 Zainicjuj a`Watermarker` obiekt ze ścieżką dokumentu, a następnie utwórz plik`ImageWatermark` obiekt strumieniem znaku wodnego uzyskanym w kroku 2. Dodaj znak wodny do dokumentu za pomocą`Add` metoda`Watermarker` obiekt.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Dodaj znak wodny do dokumentu
        watermarker.Add(watermark);
        // Zapisz dokument ze znakiem wodnym
        watermarker.Save(outputFileName);
    }
}
```

## Wniosek
GroupDocs.Watermark dla .NET zapewnia płynne rozwiązanie do dodawania znaków wodnych do dokumentów, zapewniając tożsamość marki, ochronę praw autorskich i integralność dokumentów. Postępując zgodnie z opisanymi krokami i korzystając z dostarczonych fragmentów kodu, użytkownicy mogą bez wysiłku umieszczać znaki wodne w swoich dokumentach.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym dokumenty Word, arkusze kalkulacyjne Excel, prezentacje PowerPoint, pliki PDF i inne.
### Czy mogę dostosować wygląd i położenie znaków wodnych?
Absolutnie GroupDocs.Watermark oferuje szerokie opcje dostosowywania wyglądu, położenia, przezroczystości, rotacji i innych znaków wodnych, aby dopasować je do konkretnych wymagań.
### Czy GroupDocs.Watermark udostępnia interfejsy API umożliwiające usuwanie istniejących znaków wodnych?
Tak, GroupDocs.Watermark umożliwia użytkownikom nie tylko dodawanie znaków wodnych, ale także łatwe usuwanie istniejących znaków wodnych z dokumentów.
### Czy dostępna jest pomoc techniczna dla użytkowników GroupDocs.Watermark?
 Tak, użytkownicy mogą korzystać ze wsparcia technicznego i pomocy za pośrednictwem dedykowanego serwisu[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### Czy mogę przetestować GroupDocs.Watermark przed zakupem?
Z pewnością użytkownicy mogą zdecydować się na bezpłatną wersję próbną GroupDocs.Watermark, aby zapoznać się z jego funkcjami i funkcjonalnościami przed podjęciem decyzji o zakupie.