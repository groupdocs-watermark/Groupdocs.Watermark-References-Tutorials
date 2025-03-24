---
title: Dodaj znak wodny do artefaktów obrazu w formacie PDF
linktitle: Dodaj znak wodny do artefaktów obrazu w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Chroń swoje pliki PDF za pomocą spersonalizowanych znaków wodnych za pomocą GroupDocs.Watermark dla .NET. Z łatwością dodawaj tekstowe lub graficzne znaki wodne do artefaktów graficznych w dokumentach PDF.
weight: 18
url: /pl/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Wstęp
tym samouczku przeprowadzimy Cię przez proces dodawania znaku wodnego do artefaktów obrazu w dokumencie PDF przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Wykonując poniższe kroki, możesz skutecznie chronić swoje pliki PDF za pomocą spersonalizowanych znaków wodnych.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET ze strony[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Ścieżka dokumentu: Podaj ścieżkę do dokumentu PDF, do którego chcesz dodać znak wodny.
3. Katalog wyjściowy: Utwórz katalog, w którym zostanie zapisany dokument ze znakiem wodnym.

## Importuj przestrzenie nazw
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument i zainicjuj znak wodny
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Pobierz zawartość PDF i dodaj znak wodny
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Zainicjuj obrazowy lub tekstowy znak wodny
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Dodaj znak wodny do obrazu
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Krok 3: Zapisz dokument ze znakiem wodnym
```csharp
	watermarker.Save(outputFileName);
}
```

## Wniosek
Dzięki GroupDocs.Watermark dla .NET dodawanie znaków wodnych do artefaktów obrazów w dokumentach PDF staje się bezproblemowym procesem. Postępując zgodnie z tym samouczkiem, możesz skutecznie chronić swoje pliki PDF za pomocą niestandardowych znaków wodnych, zapewniając ich bezpieczeństwo i autentyczność.
## Często zadawane pytania
### Czy mogę dodać do mojego dokumentu PDF zarówno graficzne, jak i tekstowe znaki wodne?
Tak, GroupDocs.Watermark dla .NET obsługuje jednoczesne dodawanie graficznych i tekstowych znaków wodnych.
### Czy istnieje ograniczenie liczby znaków wodnych, które mogę dodać do dokumentu?
Nie, możesz dodać wiele znaków wodnych do dokumentu bez żadnych ograniczeń.
### Czy mogę dostosować wygląd i położenie znaku wodnego?
Absolutnie masz pełną kontrolę nad wyglądem, pozycją i właściwościami znaku wodnego.
### Czy GroupDocs.Watermark dla .NET obsługuje inne formaty dokumentów oprócz PDF?
Tak, obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy istnieje sposób na usunięcie znaków wodnych z dokumentu?
Tak, GroupDocs.Watermark dla .NET udostępnia metody usuwania znaków wodnych z dokumentów, jeśli zajdzie taka potrzeba.