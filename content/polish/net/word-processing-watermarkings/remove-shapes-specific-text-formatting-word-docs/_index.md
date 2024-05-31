---
title: Usuń kształty z określonym formatowaniem tekstu w dokumentach programu Word
linktitle: Usuń kształty z określonym formatowaniem tekstu w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak usuwać kształty o określonym formacie tekstu w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Postępuj zgodnie z naszym przewodnikiem, aby efektywnie manipulować znakami wodnymi.
type: docs
weight: 31
url: /pl/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
---
## Wstęp
GroupDocs.Watermark dla .NET to potężny interfejs API, który umożliwia programistom programowe manipulowanie znakami wodnymi w różnych formatach dokumentów. W tym samouczku skupimy się na usuwaniu kształtów z określonym formatowaniem tekstu w dokumentach Word przy użyciu GroupDocs.Watermark dla .NET. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik krok po kroku pomoże Ci zrozumieć proces wydajnego i skutecznego usuwania kształtów.
## Warunki wstępne
Zanim przejdziemy do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1.  GroupDocs.Watermark dla .NET: Upewnij się, że w środowisku programistycznym zainstalowana jest biblioteka GroupDocs.Watermark dla .NET. Można go pobrać z[strona internetowa](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: skonfiguruj odpowiednie środowisko programistyczne z zainstalowanym programem Visual Studio lub dowolnym innym środowiskiem .NET IDE.
3. Dokument programu Word: Przygotuj dokument programu Word zawierający kształty z określonym formatowaniem tekstu, które chcesz usunąć.

## Importuj przestrzenie nazw
Zanim przystąpimy do wdrożenia zaimportujmy niezbędne przestrzenie nazw:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Implementacja odbywa się tutaj
}
```
## Krok 2: Pobierz treść i przeglądaj sekcje
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    // Implementacja odbywa się tutaj
}
```
## Krok 3: Iteruj po kształtach i usuwaj na podstawie formatowania tekstu
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## Krok 4: Zapisz dokument
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak usuwać kształty z określonym formatowaniem tekstu w dokumentach programu Word przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET. Postępując zgodnie ze szczegółowym przewodnikiem i korzystając z dostarczonych przykładów kodu, programiści mogą łatwo manipulować znakami wodnymi zgodnie ze swoimi wymaganiami.
## Często zadawane pytania
### Czy GroupDocs.Watermark dla .NET jest zgodny z innymi formatami dokumentów oprócz programu Word?
Tak, GroupDocs.Watermark dla .NET obsługuje różne formaty dokumentów, w tym Excel, PowerPoint, PDF i inne.
### Czy mogę dostosować kryteria usuwania kształtów na podstawie formatowania tekstu?
Absolutnie! Możesz zmodyfikować kod, aby kierować określone atrybuty tekstu, takie jak rozmiar czcionki, styl, kolor itp.
### Czy GroupDocs.Watermark dla .NET zapewnia także obsługę dodawania znaków wodnych?
Tak, oprócz usuwania, możesz także dodawać tekstowe lub graficzne znaki wodne do swoich dokumentów za pomocą GroupDocs.Watermark dla .NET.
### Czy dostępna jest wersja próbna do przetestowania przed zakupem?
 Tak, możesz pobrać bezpłatną wersję próbną z GroupDocs[strona internetowa](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną lub pomoc dotyczącą GroupDocs.Watermark dla .NET?
 Aby uzyskać pomoc techniczną, odwiedź forum pomocy technicznej pod adresem[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).