---
title: Zastąp tekst kształtu tekstem sformatowanym w dokumentach programu Word
linktitle: Zastąp tekst kształtu tekstem sformatowanym w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak zastąpić tekst kształtu tekstem sformatowanym w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Twoje możliwości edycji dokumentów bez wysiłku.
type: docs
weight: 34
url: /pl/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Wstęp
tym samouczku przeprowadzimy Cię przez proces zastępowania tekstu kształtu tekstem sformatowanym w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Ta biblioteka zapewnia zaawansowane funkcje pracy ze znakami wodnymi, w tym zastępowanie tekstu w kształtach.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  GroupDocs.Watermark dla .NET: Upewnij się, że zainstalowałeś i skonfigurowałeś GroupDocs.Watermark dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/Watermark/net/).
2. Ścieżka dokumentu: Powinieneś mieć ścieżkę do dokumentu programu Word, w którym chcesz zastąpić tekst.

## Importuj przestrzenie nazw
Przed napisaniem kodu zaimportuj niezbędne przestrzenie nazw:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
 Załaduj dokument Word za pomocą`Watermarker` klasa:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Twój kod jest kontynuowany tutaj...
}
```
## Krok 2: Pobierz treść i zamień tekst
Po załadowaniu dokumentu pobierz zawartość i zamień tekst w kształtach:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Krok 3: Zapisz dokument
Po zastąpieniu tekstu zapisz zmodyfikowany dokument:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Wniosek
Zastępowanie tekstu kształtowego tekstem sformatowanym w dokumentach programu Word jest łatwe dzięki rozwiązaniu GroupDocs dla platformy .NET. Wykonując kroki opisane w tym samouczku, możesz efektywnie zarządzać tekstem w dokumentach i manipulować nim.

## Często zadawane pytania
### Czy mogę zastąpić tekst w dokumentach innych typów za pomocą GroupDocs.Watermark dla .NET?
Tak, GroupDocs Watermark obsługuje różne formaty dokumentów, takie jak PDF, Excel, PowerPoint i inne.
### Czy GroupDocs.Watermark jest zgodny z platformą .NET Core?
Tak, GroupDocs.Watermark obsługuje zarówno .NET Framework, jak i .NET Core.
### Czy GroupDocs.Watermark obsługuje dodawanie obrazów jako znaków wodnych?
Oczywiście GroupDocs.Watermark umożliwia dodawanie do dokumentów zarówno tekstowych, jak i graficznych znaków wodnych.
### Czy mogę dostosować wygląd znaków wodnych dodanych za pomocą GroupDocs.Watermark?
Tak, masz pełną kontrolę nad wyglądem, pozycją i innymi właściwościami znaków wodnych.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark dla platformy .NET?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).