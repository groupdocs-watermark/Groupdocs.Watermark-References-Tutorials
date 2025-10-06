---
title: Dodaj znak wodny do XObjects w formacie PDF
linktitle: Dodaj znak wodny do XObjects w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do XObjects w formacie PDF przy użyciu Groupdocs.Watermark dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby ułatwić wdrożenie.
weight: 20
url: /pl/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# Dodaj znak wodny do XObjects w formacie PDF

## Wstęp
Znak wodny w plikach PDF to kluczowy krok zapewniający ochronę dokumentów przed nieupoważnionym użyciem. Dzięki Groupdocs.Watermark dla .NET dodawanie znaków wodnych do XObjects w plikach PDF nigdy nie było łatwiejsze. W tym samouczku przeprowadzimy Cię przez ten proces krok po kroku, upewniając się, że możesz bezpiecznie dodawać znaki wodne do dokumentów PDF. Zacznijmy!
## Warunki wstępne
Zanim zagłębisz się w samouczek, upewnij się, że masz wszystko, czego potrzebujesz, aby płynnie wykonywać następujące czynności:
-  Groupdocs.Watermark dla .NET: Pobierz i zainstaluj najnowszą wersję z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Upewnij się, że na komputerze programistycznym zainstalowano .NET Framework.
- Środowisko programistyczne: użyj programu Visual Studio lub dowolnego innego IDE obsługującego programowanie .NET.
-  Licencja tymczasowa: Uzyskaj[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) jeśli oceniasz produkt.
Po spełnieniu tych wymagań wstępnych możesz rozpocząć znakowanie wodne plików PDF.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Otwórz projekt C# i dodaj następujące dyrektywy using:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Skonfiguruj ścieżki dokumentów
Pierwszy krok polega na skonfigurowaniu ścieżek do dokumentu. Zdefiniuj ścieżkę, w której znajduje się plik PDF i gdzie chcesz zapisać plik PDF ze znakiem wodnym.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Zastępować`"Your Document Path"` I`"Your Document Directory"` z rzeczywistymi ścieżkami na twoim komputerze.
## Krok 2: Zainicjuj opcje ładowania pliku PDF
Następnie musisz zainicjować opcje ładowania pliku PDF. Ma to kluczowe znaczenie dla prawidłowego załadowania zawartości PDF.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Krok 3: Załaduj dokument PDF
Korzystając z opcji ładowania, załaduj dokument PDF z rozszerzeniem`Watermarker` klasa.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Krok 4: Utwórz znak wodny
Teraz musisz utworzyć znak wodny, który zostanie dodany do pliku PDF. Na potrzeby tego samouczka utworzymy tekstowy znak wodny.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Krok 5: Dodaj znak wodny do XObjects
Wykonaj iterację po każdej stronie i każdym obiekcie XObject w pliku PDF, aby zastosować znak wodny.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Dodaj znak wodny do obrazu
            xObject.Image.Add(watermark);
        }
    }
}
```
## Krok 6: Zapisz plik PDF ze znakiem wodnym
Na koniec zapisz plik PDF ze znakiem wodnym w określonym pliku wyjściowym.
```csharp
    watermarker.Save(outputFileName);
}
```
I masz to! Twój plik PDF zawiera teraz znaki wodne na wszystkich swoich XObjects.
## Wniosek
 Dodawanie znaków wodnych do dokumentów PDF przy użyciu programu Groupdocs Watermark dla .NET to prosty proces zapewniający dodatkową warstwę zabezpieczeń. Wykonując czynności opisane w tym samouczku, możesz mieć pewność, że Twoje dokumenty będą chronione przed nieuprawnionym użyciem. Pamiętaj, że zawsze możesz odwołać się do[dokumentacja](https://tutorials.groupdocs.com/Watermark/net/) aby uzyskać bardziej szczegółowe informacje i zaawansowane funkcje.
## Często zadawane pytania
### Czy mogę użyć obrazu jako znaku wodnego zamiast tekstu?
Tak, Groupdocs.Watermark dla .NET obsługuje zarówno tekstowe, jak i graficzne znaki wodne.
### Jak mogę przetestować Groupdocs.Watermark bez jego zakupu?
 Możesz użyć A[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) aby ocenić produkt.
### Czy można dostosować wygląd znaku wodnego?
Absolutnie! Możesz dostosować czcionkę, rozmiar, kąt obrotu i inne.
### Czy Groupdocs.Watermark obsługuje inne formaty dokumentów?
Tak, obsługuje różne formaty, w tym Word, Excel i PowerPoint.
### Gdzie mogę uzyskać pomoc, jeśli napotkam problemy?
 Możesz uzyskać wsparcie od[Forum Groupdocs](https://forum.groupdocs.com/c/watermark/19).