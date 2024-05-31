---
title: Dodaj znak wodny obrazu
linktitle: Dodaj znak wodny obrazu
second_title: GroupDocs.Watermark API .NET
description: Bez wysiłku dodawaj graficzne znaki wodne do swoich dokumentów za pomocą GroupDocs.Watermark dla .NET. Z łatwością chroń swoją własność intelektualną.
type: docs
weight: 10
url: /pl/net/watermarking-basics/add-image-watermark/
---
## Wstęp
W tym samouczku omówimy proces dodawania graficznego znaku wodnego do dokumentów za pomocą GroupDocs.Watermark dla .NET. Dokumenty zawierające znak wodny są niezbędne do ochrony własności intelektualnej i marki. Dzięki GroupDocs.Watermark dla .NET możesz bezproblemowo integrować znaki wodne z różnymi formatami dokumentów, takimi jak Word, Excel, PowerPoint, PDF i wiele innych.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Biblioteka GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[strona internetowa](https://releases.groupdocs.com/Watermark/net/).
2. Dokument: Przygotuj dokument, do którego chcesz dodać znak wodny.
3. Obraz znaku wodnego: Przygotuj plik obrazu, którego chcesz użyć jako znaku wodnego.

## Importuj przestrzenie nazw
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Krok 1: Zainicjuj ścieżkę dokumentu i katalog wyjściowy
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Zastępować`"Your Document Path"` bezwzględną lub względną ścieżką do dokumentu i`"Your Document Directory"` z katalogiem, w którym chcesz zapisać dokument ze znakiem wodnym.
## Krok 2: Otwórz strumień dokumentów i zainicjuj znak wodny
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Proces znakowania wodnego odbędzie się tutaj
    }
}
```
 Otwórz strumień dokumentów za pomocą`FileStream` i zainicjuj`Watermarker` obiekt.
## Krok 3: Dodaj znak wodny obrazu
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Stworzyć`ImageWatermark` obiekt ze ścieżką do pliku obrazu, którego chcesz użyć jako znaku wodnego. Ustaw poziome i pionowe wyrównanie znaku wodnego.
## Krok 4: Zapisz dokument ze znakiem wodnym
```csharp
watermarker.Save(outputFileName);
```
Zapisz dokument ze znakiem wodnym w określonym katalogu wyjściowym pod żądaną nazwą pliku.

## Wniosek
Podsumowując, GroupDocs.Watermark dla .NET zapewnia kompleksowe rozwiązanie umożliwiające łatwe dodawanie znaków wodnych do różnych formatów dokumentów. Wykonując kroki opisane w tym samouczku, możesz skutecznie dodawać graficzne znaki wodne do swoich dokumentów i chronić swoją własność intelektualną.
## Często zadawane pytania
### Czy mogę dodawać tekstowe znaki wodne za pomocą GroupDocs.Watermark dla .NET?
Tak, GroupDocs.Watermark dla .NET obsługuje dodawanie do dokumentów zarówno graficznych, jak i tekstowych znaków wodnych.
### Czy GroupDocs.Watermark dla .NET jest kompatybilny z różnymi formatami dokumentów?
Oczywiście GroupDocs.Watermark dla .NET obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PowerPoint, PDF i inne.
### Czy GroupDocs.Watermark dla .NET udostępnia opcje dostosowywania znaków wodnych?
Tak, możesz dostosować różne aspekty znaku wodnego, takie jak położenie, rozmiar, krycie i obrót.
### Czy mogę usunąć znaki wodne z dokumentów za pomocą GroupDocs.Watermark dla .NET?
Tak, GroupDocs.Watermark dla .NET oferuje funkcję wykrywania i usuwania znaków wodnych z dokumentów.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz skorzystać z bezpłatnej wersji próbnej dostępnej na stronie internetowej, aby zapoznać się z funkcjami przed zakupem[Tutaj](https://releases.groupdocs.com/).