---
title: Usuń adnotację z pliku PDF
linktitle: Usuń adnotację z pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak usuwać adnotacje z plików PDF za pomocą GroupDocs.Watermark dla .NET. Bez wysiłku zwiększ czytelność dokumentów.
weight: 29
url: /pl/net/pdf-watermarking-attachments/remove-annotation-pdf/
type: docs
---
# Usuń adnotację z pliku PDF

## Wstęp
Adnotacje w dokumentach PDF mogą czasami zaśmiecać treść lub zakłócać czytelność dokumentu. Dzięki GroupDocs.Watermark dla .NET możesz bez wysiłku usuwać adnotacje z plików PDF. W tym samouczku przeprowadzimy Cię przez ten proces krok po kroku.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1.  GroupDocs.Watermark dla .NET: Upewnij się, że zainstalowałeś GroupDocs.Watermark dla .NET. Można go pobrać z[strona internetowa](https://releases.groupdocs.com/Watermark/net/).
2. Ścieżka dokumentu: Podaj ścieżkę do dokumentu PDF, z którego chcesz usunąć adnotacje.
3. Katalog wyjściowy: Przygotuj katalog, w którym zostanie zapisany zmodyfikowany dokument.
4. Środowisko .NET: Upewnij się, że masz skonfigurowane środowisko .NET do wykonania dostarczonego kodu.

## Importuj przestrzenie nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcji GroupDocs dla .NET.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
Rozpocznij od załadowania dokumentu PDF przy użyciu podanej ścieżki dokumentu.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Krok 2: Usuń adnotacje
Teraz przejdźmy do usuwania adnotacji z dokumentu PDF. Istnieją dwie możliwości usunięcia adnotacji: według indeksu lub przez odniesienie.
### Usuń adnotację według indeksu
Aby usunąć adnotację według jej indeksu:
```csharp
// Usuń adnotację według indeksu
pdfContent.Pages[0].Annotations.RemoveAt(0);
```
### Usuń adnotację przez odniesienie
Aby usunąć adnotację przez odniesienie:
```csharp
// Usuń adnotację przez odniesienie
pdfContent.Pages[0].Annotations.Remove(pdfContent.Pages[0].Annotations[0]);
```
## Krok 3: Zapisz dokument
Po usunięciu adnotacji zapisz zmodyfikowany dokument w określonym katalogu wyjściowym.
```csharp
    watermarker.Save(outputFileName);
}
```

## Wniosek
Usuwanie adnotacji z dokumentów PDF jest prostym procesem dzięki GroupDocs.Watermark dla .NET. Wykonując kroki opisane w tym samouczku, możesz efektywnie zarządzać adnotacjami i zwiększać czytelność plików PDF.
## Często zadawane pytania
### Czy mogę usunąć wiele adnotacji jednocześnie?
Tak, możesz przeglądać adnotacje i w razie potrzeby je usuwać, korzystając z GroupDocs.Watermark dla .NET.
### Czy GroupDocs.Watermark obsługuje inne formaty dokumentów oprócz PDF?
Tak, GroupDocs Watermark obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej z[Tutaj](https://releases.groupdocs.com/).
### Czy adnotacje można modyfikować zamiast całkowicie usuwać?
Tak, GroupDocs.Watermark udostępnia również metody modyfikowania istniejących adnotacji.
### Gdzie mogę znaleźć dodatkowe wsparcie lub pomoc?
 Możesz odwiedzić forum GroupDocs.Watermark[Tutaj](https://forum.groupdocs.com/c/watermark/19) w przypadku jakichkolwiek pytań lub pomocy.