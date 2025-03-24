---
title: Rasteryzuj dokument PDF
linktitle: Rasteryzuj dokument PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak rasteryzować dokumenty PDF za pomocą GroupDocs.Watermark dla .NET. Bez wysiłku zwiększ bezpieczeństwo dokumentów i atrakcyjność wizualną.
weight: 27
url: /pl/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## Wstęp
dziedzinie zarządzania dokumentami i manipulacji nimi GroupDocs.Watermark dla .NET jest potężnym narzędziem oferującym solidne możliwości dodawania, usuwania i wyszukiwania znaków wodnych w różnych formatach dokumentów. Niezależnie od tego, czy chodzi o zabezpieczenie dokumentów za pomocą informacji o prawach autorskich, dodanie logo firmy w celu podkreślenia marki, czy po prostu opatrzenie dokumentów pieczęciami, GroupDocs.Watermark upraszcza ten proces dzięki intuicyjnemu interfejsowi API i obszernemu zestawowi funkcji.
## Warunki wstępne
Zanim zagłębisz się w świat znaków wodnych za pomocą GroupDocs.Watermark dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:
### 1. Zainstaluj .NET Framework
Upewnij się, że na komputerze programistycznym zainstalowano platformę .NET Framework. Możesz pobrać go ze strony internetowej Microsoft lub skorzystać z preferowanego menedżera pakietów.
#### Krok 1: Pobierz .NET Framework
Odwiedź stronę pobierania Microsoft .NET Framework.
#### Krok 2: Zainstaluj .NET Framework
Postępuj zgodnie z instrukcjami instalacji podanymi na stronie pobierania, aby zainstalować .NET Framework w swoim systemie.
### 2. Uzyskaj licencję GroupDocs.Watermark
Aby w pełni wykorzystać możliwości GroupDocs.Watermark, potrzebujesz ważnej licencji. Możesz kupić licencję lub uzyskać tymczasową licencję do celów testowych.
#### Krok 1: Uzyskaj licencję
Odwiedź stronę zakupu GroupDocs.Watermark.
#### Krok 2: Kup lub uzyskaj licencję tymczasową
Wybierz odpowiednią opcję licencjonowania w zależności od potrzeb — kup licencję do dalszego użytkowania lub uzyskaj licencję tymczasową do celów testowych.

## Importuj przestrzenie nazw
Zanim zaczniesz dodawać znaki wodne do swoich dokumentów, pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw, aby bezproblemowo uzyskać dostęp do funkcjonalności GroupDocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Teraz, gdy już wszystko skonfigurowałeś, przejdźmy do rasteryzacji dokumentu PDF przy użyciu GroupDocs.Watermark dla .NET. Rasteryzacja konwertuje każdą stronę dokumentu PDF do formatu obrazu rastrowego, takiego jak PNG.
## Krok 1: Zainicjuj zmienne
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Upewnij się, że zastąpiłeś „Ścieżka Twojego dokumentu” i „Katalog Twojego dokumentu” odpowiednio rzeczywistą ścieżką do dokumentu PDF i żądanym katalogiem wyjściowym.
## Krok 2: Załaduj dokument i dodaj znak wodny
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Zainicjuj obrazowy lub tekstowy znak wodny
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Najpierw dodaj dowolny znak wodny
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasteryzuj wszystkie strony
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Treść wszystkich stron zostaje zastąpiona obrazami rastrowymi
    watermarker.Save(outputFileName);
}
```
Na tym etapie ładujemy dokument PDF i inicjujemy tekstowy znak wodny z określonymi właściwościami, takimi jak tekst, czcionka, wyrównanie, kąt obrotu, typ rozmiaru, współczynnik skali i krycie. Następnie dodajemy znak wodny do dokumentu. Następnie pobieramy zawartość dokumentu PDF i rasteryzujemy wszystkie strony do formatu PNG z rozdzielczością 100 DPI. Na koniec zapisujemy zmodyfikowany dokument z zrastrowaną zawartością.

## Wniosek
GroupDocs.Watermark dla .NET oferuje kompleksowe rozwiązanie umożliwiające łatwe dodawanie znaków wodnych do różnych formatów dokumentów. Wykonując kroki opisane w tym samouczku, możesz skutecznie rasteryzować dokumenty PDF i zwiększać ich bezpieczeństwo i atrakcyjność wizualną.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest zgodny z innymi formatami dokumentów oprócz PDF?
Tak, GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym Microsoft Word, Excel, PowerPoint, Visio, Outlook i wiele innych.
### Czy mogę dostosować wygląd znaków wodnych dodanych przy użyciu GroupDocs.Watermark?
Absolutnie! GroupDocs.Watermark udostępnia rozbudowane opcje dostosowywania właściwości znaku wodnego, takich jak tekst, czcionka, kolor, rozmiar, krycie, obrót i położenie.
### Czy GroupDocs.Watermark oferuje obsługę przetwarzania wsadowego?
Tak, możesz łatwo przetwarzać wiele dokumentów w trybie wsadowym za pomocą GroupDocs, oszczędzając czas i wysiłek związany z dodawaniem znaków wodnych do dużych zestawów plików.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark?
Tak, możesz pobrać bezpłatną wersję próbną GroupDocs.Watermark ze strony internetowej, aby przetestować jej funkcje przed dokonaniem zakupu.
### Jak mogę uzyskać pomoc, jeśli napotkam jakiekolwiek problemy lub mam pytania dotyczące GroupDocs.Watermark?
Możesz odwiedzić forum GroupDocs.Watermark, aby uzyskać pomoc od społeczności lub skontaktować się z zespołem pomocy technicznej GroupDocs w celu uzyskania pomocy.