---
title: Usuń adnotacje z określonym formatowaniem tekstu w formacie PDF
linktitle: Usuń adnotacje z określonym formatowaniem tekstu w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak usuwać adnotacje o określonym formacie tekstu w dokumentach PDF za pomocą Groupdocs dla .NET.
type: docs
weight: 30
url: /pl/net/pdf-watermarking-attachments/remove-annotations-text-formatting-pdf/
---
## Wstęp
W tym samouczku przeprowadzimy Cię przez proces usuwania adnotacji o określonym formacie tekstu w dokumencie PDF przy użyciu programu Groupdocs.Watermark dla .NET. Ta biblioteka zapewnia zaawansowane funkcje do pracy ze znakami wodnymi, adnotacjami i innymi elementami dokumentów w różnych formatach.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  Biblioteka Groupdocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: Środowisko programistyczne .NET skonfigurowane na Twoim komputerze.
3. Dokument PDF: Przygotuj dokument PDF z adnotacjami, które chcesz zmodyfikować.

## Importowanie przestrzeni nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do wymaganych klas i metod:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument PDF
```csharp
string documentPath = "YourDocumentPath";
string outputDirectory = "YourDocumentDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Pobierz zawartość PDF i przeglądaj strony
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfPage page in pdfContent.Pages)
    {
```
## Krok 3: Iteruj po adnotacjach i sprawdź formatowanie tekstu
```csharp
        for (int i = page.Annotations.Count - 1; i >= 0; i--)
        {
            foreach (FormattedTextFragment fragment in page.Annotations[i].FormattedTextFragments)
            {
```
## Krok 4: Usuń adnotacje z określonym formatowaniem tekstu
```csharp
                if (fragment.Font.FamilyName == "Verdana")
                {
                    page.Annotations.RemoveAt(i);
                    break;
                }
            }
        }
    }
```
## Krok 5: Zapisz zmodyfikowany dokument PDF
```csharp
    watermarker.Save(outputFileName);
}
```
Teraz pomyślnie usunąłeś adnotacje o określonym formacie tekstu z dokumentu PDF za pomocą Groupdocs.Watermark dla .NET.

## Wniosek
Groupdocs.Watermark dla .NET oferuje wygodne rozwiązanie do pracy z adnotacjami i innymi elementami w dokumentach PDF. Postępując zgodnie z tym samouczkiem, możesz łatwo manipulować adnotacjami w oparciu o określone formatowanie tekstu, poprawiając czytelność i wygląd plików PDF.
## Często zadawane pytania
### Czy mogę używać Groupdocs.Watermark dla .NET z innymi formatami dokumentów?
Tak, Groupdocs.Watermark obsługuje różne formaty dokumentów, w tym DOCX, PPTX, XLSX, PDF i inne.
### Czy dostępna jest bezpłatna wersja próbna programu Groupdocs.Watermark dla platformy .NET?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej Groupdocs.Watermark dla .NET z[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację Groupdocs.Watermark dla .NET?
 Można znaleźć szczegółową dokumentację i odniesienia do API[Tutaj](https://reference.groupdocs.com/Watermark/net/).
### Jak mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z Groupdocs.Watermark?
 Możesz publikować swoje pytania lub problemy na forum Groupdocs.Watermark[Tutaj](https://forum.groupdocs.com/c/watermark/19).
### Czy mogę kupić tymczasową licencję na Groupdocs.Watermark dla .NET?
 Tak, możesz kupić tymczasową licencję od[Tutaj](https://purchase.groupdocs.com/temporary-license/).