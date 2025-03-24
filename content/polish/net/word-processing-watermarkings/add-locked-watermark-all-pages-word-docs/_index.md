---
title: Dodaj zablokowany znak wodny do wszystkich stron w dokumentach programu Word
linktitle: Dodaj zablokowany znak wodny do wszystkich stron w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Zabezpiecz swoje dokumenty, dodając zablokowane znaki wodne za pomocą Groupdocs.Watermark dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby ułatwić wdrożenie.
weight: 11
url: /pl/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# Dodaj zablokowany znak wodny do wszystkich stron w dokumentach programu Word

## Wstęp
Dodawanie znaków wodnych do dokumentów to istotny krok w zabezpieczaniu i budowaniu marki treści. Niezależnie od tego, czy zapobiegasz nieautoryzowanemu użyciu, czy po prostu dodajesz profesjonalny akcent, znaki wodne mogą służyć wielu celom. W tym samouczku przeprowadzimy Cię przez proces dodawania zablokowanego znaku wodnego do wszystkich stron dokumentu programu Word za pomocą Groupdocs.Watermark dla .NET.
## Warunki wstępne
Zanim przejdziemy do przewodnika krok po kroku, upewnijmy się, że masz wszystko, czego potrzebujesz:
1. Groupdocs.Watermark dla .NET: Pobierz najnowszą wersję z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: Upewnij się, że na komputerze jest zainstalowana platforma .NET Framework.
3. Środowisko programistyczne: środowisko programistyczne, takie jak Visual Studio.
4.  Licencja: Możesz wybrać[bezpłatna wersja próbna](https://releases.groupdocs.com/) lub kup A[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/).
## Importuj przestrzenie nazw
Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Są one niezbędne do uzyskania dostępu do klas i metod udostępnianych przez Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Skonfiguruj swój projekt

Otwórz swoje środowisko programistyczne i utwórz nowy projekt .NET. Może to być aplikacja konsolowa lub dowolny inny typ, który odpowiada Twoim potrzebom.

Musisz dodać pakiet Groupdocs.Watermark do swojego projektu. Można to zrobić za pomocą Menedżera pakietów NuGet. Uruchom następujące polecenie w konsoli Menedżera pakietów NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Krok 2: Załaduj dokument Word
### Zdefiniuj ścieżkę dokumentu
Określ ścieżkę do dokumentu programu Word. Będzie to dokument, do którego chcesz dodać znak wodny.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Ustaw opcje ładowania
 Utwórz instancję`WordProcessingLoadOptions` , aby załadować dokument programu Word z określonymi opcjami.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Krok 3: Utwórz znak wodny
### Zainicjuj znak wodny
 Używając`Watermarker`class, załaduj dokument z określonymi opcjami ładowania.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Dalsze kroki będą zawarte w tym bloku using
}
```
### Zdefiniuj właściwości znaku wodnego
 Stwórz`TextWatermark` instancję z żądanym tekstem, czcionką i kolorem.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Krok 4: Zastosuj znak wodny do wszystkich stron
### Ustaw opcje znaku wodnego
 Definiować`WordProcessingWatermarkPagesOptions` i ustaw`IsLocked` właściwość na true, aby zablokować znak wodny. Dzięki temu znak wodny nie będzie łatwo usunięty.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Opcjonalnie: Dodaj ochronę hasłem
Jeśli chcesz dodać dodatkową warstwę zabezpieczeń, możesz ustawić hasło dla znaku wodnego.
```csharp
// Aby zabezpieczyć hasłem
// opcje.Hasło = "7654321";
```
### Dodaj znak wodny
 Użyj`Add` metoda`Watermarker` class, aby dodać znak wodny do dokumentu z określonymi opcjami.
```csharp
watermarker.Add(watermark, options);
```
## Krok 5: Zapisz dokument
Na koniec zapisz zmodyfikowany dokument w określonym pliku wyjściowym.
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Wykonując poniższe kroki, możesz łatwo dodać zablokowany znak wodny do wszystkich stron dokumentów programu Word przy użyciu Groupdocs.Watermark dla .NET. Pomaga to nie tylko chronić dokumenty przed nieuprawnionym użyciem, ale także nadaje profesjonalny charakter treściom. Groupdocs.Watermark oferuje kompleksowe rozwiązanie do znakowania wodnego, zapewniające bezpieczeństwo i markę dokumentów.
## Często zadawane pytania
### Czy mogę użyć obrazu jako znaku wodnego zamiast tekstu?
 Tak, Groupdocs Watermark obsługuje zarówno tekstowe, jak i graficzne znaki wodne. Możesz wymienić`TextWatermark` z`ImageWatermark` i określ swój obraz.
### Czy można dostosować położenie znaku wodnego?
 Absolutnie! Możesz ustawić położenie znaku wodnego za pomocą właściwości takich jak`HorizontalAlignment` I`VerticalAlignment`.
### Czy mogę zastosować różne znaki wodne na różnych stronach dokumentu?
 Tak, możesz dostosować znaki wodne dla określonych stron za pomocą`PageIndex` nieruchomość w`WordProcessingWatermarkPagesOptions`.
### Czy Groupdocs.Watermark obsługuje inne formaty dokumentów oprócz programu Word?
Tak, Groupdocs Watermark obsługuje różne formaty, w tym PDF, Excel, PowerPoint i inne.
### Jakie są wymagania systemowe dotyczące korzystania z Groupdocs.Watermark?
Potrzebujesz systemu z zainstalowanym .NET Framework i środowiskiem programistycznym, takim jak Visual Studio.