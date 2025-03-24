---
title: Dodaj znak wodny adnotacji do pliku PDF
linktitle: Dodaj znak wodny adnotacji do pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak bez wysiłku dodawać znaki wodne adnotacji do dokumentów PDF za pomocą GroupDocs.Watermark dla .NET. Z łatwością zwiększ markę i bezpieczeństwo dokumentów.
weight: 10
url: /pl/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---

# Dodaj znak wodny adnotacji do pliku PDF

## Wstęp
dziedzinie zarządzania dokumentami dodawanie znaków wodnych do plików PDF jest kluczowym aspektem, szczególnie ze względu na budowanie marki, bezpieczeństwo i identyfikację dokumentów. GroupDocs.Watermark dla .NET to potężna biblioteka ułatwiająca bezproblemową integrację znaków wodnych z różnymi formatami dokumentów, w tym plikami PDF. W tym samouczku omówimy krok po kroku proces dodawania znaków wodnych adnotacji do dokumentów PDF, wykorzystując funkcje udostępniane przez GroupDocs.Watermark dla .NET.
## Warunki wstępne
Zanim przejdziemy do samouczka, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Biblioteka GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[strona internetowa](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: skonfiguruj odpowiednie środowisko programistyczne, takie jak Visual Studio lub dowolne inne środowisko .NET IDE.
3. Podstawowa znajomość języka C#: Zalecana jest znajomość podstaw języka programowania C#.

## Importowanie niezbędnych przestrzeni nazw
Aby rozpocząć, zaimportuj wymagane przestrzenie nazw do projektu C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
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
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## Krok 3: Dodaj tekstowy znak wodny
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## Krok 4: Dodaj znak wodny obrazu
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## Krok 5: Zapisz dokument ze znakiem wodnym
```csharp
	watermarker.Save(outputFileName);
}
```

## Wniosek
Podsumowując, GroupDocs.Watermark dla .NET oferuje kompleksowe rozwiązanie do programowego dodawania znaków wodnych adnotacji do dokumentów PDF. Postępując zgodnie z opisanymi krokami, użytkownicy mogą bezproblemowo zintegrować tekstowe i graficzne znaki wodne ze swoimi plikami PDF, poprawiając w ten sposób markę i bezpieczeństwo dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest zgodny z innymi formatami dokumentów oprócz PDF?
Tak, GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy mogę dostosować wygląd znaku wodnego?
Absolutnie! GroupDocs.Watermark zapewnia szerokie opcje dostosowywania zarówno tekstowych, jak i graficznych znaków wodnych, umożliwiając użytkownikom dostosowywanie rozmiaru, położenia, krycia i innych parametrów.
### Czy GroupDocs.Watermark nadaje się do przetwarzania wsadowego dokumentów?
pewnością! GroupDocs.Watermark oferuje wydajne możliwości przetwarzania wsadowego, umożliwiając użytkownikom jednoczesne stosowanie znaków wodnych w wielu dokumentach.
### Czy GroupDocs.Watermark obsługuje programowanie .NET Core?
Tak, GroupDocs.Watermark obsługuje platformę .NET Core, umożliwiając programistom integrację funkcji znaku wodnego z aplikacjami wieloplatformowymi.
### Czy dostępna jest pomoc techniczna dla użytkowników GroupDocs.Watermark?
Tak, GroupDocs zapewnia kompleksową pomoc techniczną za pośrednictwem dedykowanych forów i kanałów obsługi klienta.