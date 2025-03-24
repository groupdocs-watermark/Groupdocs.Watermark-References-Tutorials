---
title: Użycie typu kształtu w dokumentach programu Word
linktitle: Użycie typu kształtu w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak manipulować kształtami w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET. Ten samouczek zawiera wskazówki dotyczące wydajnego przetwarzania dokumentów.
weight: 37
url: /pl/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## Wstęp
W tym samouczku omówimy, jak wykorzystywać typy kształtów w dokumentach programu Word przy użyciu programu GroupDocs.Watermark dla platformy .NET. Kształty w dokumentach programu Word mogą się różnić, a zrozumienie sposobu manipulowania nimi może mieć kluczowe znaczenie w przypadku różnych zadań związanych z przetwarzaniem dokumentów.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Biblioteka GroupDocs.Watermark dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Watermark dla .NET z[link do pobrania](https://releases.groupdocs.com/Watermark/net/).
2. Ścieżka dokumentu: Przygotuj dokument programu Word do przetworzenia.
3. Środowisko programistyczne: Skonfiguruj odpowiednie środowisko programistyczne z obsługą platformy .NET.

## Importuj przestrzenie nazw
Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Te przestrzenie nazw zapewnią dostęp do wymaganych klas i metod pracy z dokumentami programu Word.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Krok 1: Załaduj dokument
Rozpocznij od załadowania dokumentu Word do obiektu Watermarker. Pamiętaj, aby określić ścieżkę dokumentu i wszelkie dodatkowe opcje wymagane podczas procesu ładowania.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tutaj znajduje się kod przetwarzania dokumentu
}
```
## Krok 2: Uzyskaj dostęp do treści dokumentu
 Uzyskaj dostęp do zawartości załadowanego dokumentu programu Word za pomocą`GetContent<WordProcessingContent>()` metoda. Zapewni to dostęp do sekcji, akapitów i kształtów obecnych w dokumencie.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Krok 3: Iteruj po sekcjach i kształtach
Przeglądaj każdą sekcję i kształt w dokumencie, aby je sprawdzić i manipulować nimi zgodnie z wymaganiami.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // Tutaj znajduje się kod manipulacji kształtem
    }
}
```
## Krok 4: Sprawdź typy kształtów
 pętli sprawdź określone typy kształtów za pomocą metody`ShapeType` nieruchomość. Ten przykład ilustruje identyfikację i obsługę narożników ukośnych Zaokrąglone kształty.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // Tutaj znajduje się kod manipulacyjny specyficzny dla kształtu
}
```
## Krok 5: Manipuluj kształtami
Wykonuj czynności, takie jak dodawanie tekstu, modyfikowanie formatowania lub stosowanie zmian wizualnych do zidentyfikowanych kształtów.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## Krok 6: Zapisz dokument
Po dokonaniu wszystkich niezbędnych modyfikacji zapisz dokument z zastosowanymi zmianami w określonym pliku wyjściowym.
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Manipulowanie kształtami w dokumentach programu Word może być niezbędne w przypadku różnych zadań związanych z przetwarzaniem dokumentów. Dzięki GroupDocs.Watermark dla .NET możesz łatwo identyfikować, modyfikować i manipulować kształtami, aby efektywnie spełniać swoje wymagania.
## Często zadawane pytania
### Czy GroupDocs.Watermark dla .NET obsługuje inne formaty dokumentów niż Word?
Tak, GroupDocs.Watermark dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Excel, PowerPoint i inne.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej z[strona z wydaniami](https://releases.groupdocs.com/).
### Czy GroupDocs.Watermark dla .NET zapewnia pomoc techniczną?
 Tak, możesz szukać pomocy i nawiązywać kontakt ze społecznością za pośrednictwem[forum wsparcia](https://forum.groupdocs.com/c/watermark/19).
### Czy mogę dostosować proces znakowania wodnego do konkretnych wymagań dokumentu?
Absolutnie GroupDocs.Watermark dla .NET oferuje szerokie opcje dostosowywania, aby dostosować proces znakowania wodnego do Twoich potrzeb.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Watermark dla .NET?
 Licencję tymczasową można nabyć w witrynie[Strona zakupu licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/) do celów testowania i oceny.