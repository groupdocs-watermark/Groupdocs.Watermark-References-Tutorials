---
title: Rasteryzuj stronę PDF
linktitle: Rasteryzuj stronę PDF
second_title: GroupDocs.Watermark API .NET
description: Zwiększ bezpieczeństwo dokumentów dzięki GroupDocs dla platformy .NET. Bezproblemowo dodawaj znaki wodne do plików PDF i innych formatów.
weight: 28
url: /pl/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# Rasteryzuj stronę PDF

## Wstęp
GroupDocs.Watermark dla .NET to potężny interfejs API, który umożliwia programistom bezproblemowe dodawanie znaków wodnych do różnych formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i innych. Dzięki intuicyjnemu interfejsowi i rozbudowanym funkcjom GroupDocs.Watermark upraszcza proces dodawania tekstowych lub graficznych znaków wodnych do dokumentów, umożliwiając użytkownikom ochronę ich własności intelektualnej i bezproblemowe zwiększanie bezpieczeństwa dokumentów.
## Warunki wstępne
Zanim zaczniesz korzystać z GroupDocs.Watermark dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:
1. Instalacja: Pobierz i zainstaluj GroupDocs.Watermark dla .NET z[strona pobierania](https://releases.groupdocs.com/Watermark/net/).
2.  Licencja: Kup licencję na GroupDocs.Watermark dla .NET. Licencję tymczasową do celów testowych można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/) lub kup pełną licencję od[strona zakupu](https://purchase.groupdocs.com/buy).
3. .NET Framework: Upewnij się, że na komputerze programistycznym zainstalowano .NET Framework.
4. Dokument: Przygotuj dokument, do którego chcesz dodać znaki wodne.

## Importuj przestrzenie nazw
Aby rozpocząć korzystanie z GroupDocs.Watermark dla .NET, zaimportuj niezbędne przestrzenie nazw do swojego projektu:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod trafia tutaj
}
```
## Krok 2: Zainicjuj znak wodny
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Krok 3: Dodaj znak wodny
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Krok 4: Rasteryzacja strony
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Krok 5: Zapisz dokument
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Podsumowując, GroupDocs.Watermark dla .NET oferuje płynne rozwiązanie do dodawania znaków wodnych do plików PDF i innych formatów dokumentów. Postępując zgodnie ze szczegółowym przewodnikiem opisanym powyżej, programiści mogą skutecznie rasteryzować strony PDF i z łatwością zwiększać bezpieczeństwo dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest zgodny z innymi formatami dokumentów oprócz PDF?
Tak, GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PowerPoint, Visio i inne.
### Czy mogę dostosować wygląd znaku wodnego dodanego do dokumentu?
Absolutnie! GroupDocs.Watermark zapewnia szerokie opcje dostosowywania tekstowych i graficznych znaków wodnych, umożliwiając użytkownikom dostosowanie czcionki, rozmiaru, koloru, krycia i położenia zgodnie z ich preferencjami.
### Czy GroupDocs.Watermark nadaje się zarówno do użytku osobistego, jak i komercyjnego?
Tak, GroupDocs.Watermark oferuje elastyczne opcje licencjonowania, aby zaspokoić potrzeby zarówno osób indywidualnych, jak i przedsiębiorstw, dzięki czemu nadaje się do projektów osobistych, a także zastosowań komercyjnych na dużą skalę.
### Czy GroupDocs.Watermark oferuje wsparcie techniczne dla programistów?
Tak, programiści mogą uzyskać dostęp do wszechstronnej pomocy technicznej za pośrednictwem forum GroupDocs.Watermark, gdzie mogą szukać pomocy, dzielić się doświadczeniami i kontaktować się z innymi programistami.
### Czy mogę wypróbować GroupDocs.Watermark przed dokonaniem zakupu?
 pewnością! Możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Watermark na stronie[strona z wydaniami](https://releases.groupdocs.com/), dzięki czemu możesz zapoznać się z jego funkcjami i funkcjonalnościami przed podjęciem decyzji o zakupie.