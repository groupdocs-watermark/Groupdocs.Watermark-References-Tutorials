---
title: Dodaj znak wodny do obrazów w formacie PDF
linktitle: Dodaj znak wodny do obrazów w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do obrazów w dokumentach PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET, korzystając z naszego szczegółowego samouczka krok po kroku. Z łatwością zabezpiecz swoje pliki PDF.
type: docs
weight: 19
url: /pl/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Wstęp
Dodawanie znaków wodnych do obrazów w dokumencie PDF może mieć kluczowe znaczenie dla ochrony własności intelektualnej lub zapewnienia autentyczności dokumentów. Korzystając z GroupDocs.Watermark dla .NET, zadanie to można wykonać sprawnie i łatwo. Ten samouczek przeprowadzi Cię przez każdy etap procesu, od skonfigurowania środowiska, przez dodanie znaków wodnych, aż po zapisanie ostatecznego dokumentu. Zanurzmy się!
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1. Visual Studio: Zainstaluj Visual Studio, zintegrowane środowisko programistyczne (IDE) dla aplikacji .NET.
2.  GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[strona wydania](https://releases.groupdocs.com/Watermark/net/).
3. Dokument PDF: przygotuj dokument PDF z obrazami, aby przetestować funkcję znaku wodnego.
4.  Licencja tymczasowa: Uzyskaj[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) jeśli oceniasz produkt.
## Importuj przestrzenie nazw
Najpierw upewnij się, że w projekcie zaimportowano niezbędne przestrzenie nazw. Będzie to obejmować podstawowe przestrzenie nazw wymagane do pracy z dokumentami PDF i znakami wodnymi.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Skonfiguruj ścieżkę dokumentu i katalog wyjściowy
Aby rozpocząć, zdefiniuj ścieżki dokumentu wejściowego i katalog wyjściowy, w którym zostanie zapisany dokument ze znakiem wodnym. Ten krok jest kluczowy, aby upewnić się, że Twój program wie, gdzie znaleźć dokument źródłowy i gdzie zapisać przetworzony plik.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Załaduj dokument PDF
 Następnie musisz załadować dokument PDF za pomocą`PdfLoadOptions`. Ta klasa umożliwia określenie opcji ładowania pliku PDF, takich jak ochrona hasłem, jeśli to konieczne.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod znaku wodnego zostanie umieszczony tutaj
}
```
## Krok 3: Utwórz znak wodny
Teraz zainicjuj znak wodny. W tym przykładzie tworzymy tekstowy znak wodny o treści „Obraz chroniony”. Dostosuj czcionkę, wyrównanie, obrót i skalowanie zgodnie ze swoimi potrzebami.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Uzyskaj dostęp do treści PDF
Pobierz zawartość dokumentu PDF. W szczególności musimy uzyskać dostęp do obrazów w pliku PDF. Tutaj skupiamy się na pierwszej stronie, ale w razie potrzeby możesz rozszerzyć ją na inne strony.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Pobierz wszystkie obrazy z pierwszej strony
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Krok 5: Zastosuj znak wodny do obrazów
Przejrzyj każdy obraz znajdujący się na pierwszej stronie i zastosuj znak wodny. Dzięki temu wszystkie obrazy na określonej stronie będą miały zastosowany znak wodny.
```csharp
// Dodaj znak wodny do wszystkich znalezionych obrazów
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Krok 6: Zapisz dokument ze znakiem wodnym
Na koniec zapisz plik PDF ze znakiem wodnym w określonym katalogu wyjściowym. Ten krok kończy proces poprzez zapisanie zmian w nowym pliku.
```csharp
watermarker.Save(outputFileName);
```
## Wniosek
I masz to! Dodawanie znaku wodnego do obrazów w pliku PDF przy użyciu programu GroupDocs Watermark for .NET to prosty proces, który może znacznie zwiększyć bezpieczeństwo i autentyczność dokumentów. Wykonując poniższe kroki, możesz mieć pewność, że Twoja własność intelektualna jest chroniona, a Twoje dokumenty są bezpieczne.
## Często zadawane pytania
### Co to jest GroupDocs.Watermark dla .NET?
GroupDocs.Watermark dla .NET to obszerna biblioteka, która umożliwia programistom dodawanie, wyszukiwanie i usuwanie znaków wodnych w różnych formatach dokumentów, w tym w plikach PDF.
### Czy mogę dodać tekstowe i graficzne znaki wodne za pomocą GroupDocs.Watermark?
Tak, GroupDocs.Watermark obsługuje zarówno tekstowe, jak i graficzne znaki wodne, zapewniając elastyczność w przypadku różnych typów znaków wodnych.
### Czy można dodać znak wodny do wielu stron pliku PDF?
Absolutnie! Możesz przeglądać każdą stronę pliku PDF i stosować znaki wodne do obrazów na każdej stronie.
### Czy potrzebuję licencji, aby używać GroupDocs.Watermark dla .NET?
 Tak, wymagana jest licencja. Można uzyskać[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) w celach ewaluacyjnych.
### Gdzie mogę znaleźć więcej dokumentacji dotyczącej GroupDocs.Watermark dla .NET?
 Obszerną dokumentację można znaleźć na stronie[Strona dokumentacji GroupDocs.Watermark](https://reference.groupdocs.com/Watermark/net/).