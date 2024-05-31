---
title: Dodaj znak wodny do wszystkich załączników w formacie PDF
linktitle: Dodaj znak wodny do wszystkich załączników w formacie PDF
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać znaki wodne do załączników PDF za pomocą GroupDocs.Watermark dla .NET. Z łatwością zabezpiecz swoje dokumenty za pomocą niestandardowych znaków wodnych.
type: docs
weight: 16
url: /pl/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Wstęp
Dodawanie znaków wodnych do załączników PDF może być kluczowym krokiem w zarządzaniu dokumentami, zwłaszcza jeśli chodzi o zapewnienie bezpieczeństwa lub marki. GroupDocs.Watermark dla .NET oferuje kompleksowe rozwiązanie umożliwiające bezproblemowe osadzanie znaków wodnych w plikach PDF. W tym samouczku przeprowadzimy Cię przez proces dodawania znaku wodnego do wszystkich załączników w dokumencie PDF przy użyciu programu GroupDocs.Watermark dla .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  GroupDocs.Watermark dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz i zainstaluj GroupDocs.Watermark dla .NET z[strona internetowa](https://releases.groupdocs.com/Watermark/net/).
2. Środowisko programistyczne: Skonfiguruj odpowiednie środowisko programistyczne za pomocą programu Visual Studio lub dowolnego innego środowiska IDE zgodnego z platformą .NET.
3. Dokument PDF: Przygotuj dokument PDF, do którego chcesz dodać znaki wodne, wraz z załącznikami, do których chcesz dodać znak wodny.

## Importowanie przestrzeni nazw
Zanim zagłębisz się w kod, pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Watermark dla .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Zdefiniuj ścieżkę dokumentu i katalog wyjściowy
Najpierw zdefiniuj ścieżkę do wejściowego dokumentu PDF i katalog, w którym zostanie zapisany dokument ze znakiem wodnym:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Zainicjuj opcje ładowania i znak wodny
Następnie zainicjuj opcje ładowania dokumentu PDF i utwórz tekstowy znak wodny:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Krok 3: Załaduj dokument i załączniki
Załaduj dokument PDF i przeglądaj jego załączniki:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Krok 4: Sprawdź obsługę załączników
Sprawdź, czy załączony plik jest obsługiwany przez GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Krok 5: Dodaj znak wodny do załączników
Załaduj załączony dokument i dodaj znak wodny:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Krok 6: Zapisz zmiany
Na koniec zapisz zmiany w dokumencie PDF ze znakiem wodnym:
```csharp
    watermarker.Save(outputFileName);
}
```

## Wniosek
W tym samouczku omówiliśmy, jak dodać znaki wodne do wszystkich załączników w dokumencie PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET. Postępując zgodnie ze szczegółowym przewodnikiem, możesz bezproblemowo zintegrować znaki wodne z plikami PDF, zapewniając bezpieczeństwo dokumentów i budowanie marki.
## Często zadawane pytania
### Czy mogę dostosować wygląd znaku wodnego?
Tak, możesz dostosować różne aspekty, takie jak tekst, czcionka, rozmiar, kolor i położenie znaku wodnego, zgodnie z własnymi wymaganiami.
### Czy GroupDocs.Watermark obsługuje inne formaty dokumentów oprócz PDF?
Tak, GroupDocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym Microsoft Word, Excel, PowerPoint, Visio, Outlook i obrazy.
### Czy dostępna jest wersja próbna programu GroupDocs.Watermark?
Tak, możesz poznać funkcje GroupDocs.Watermark, pobierając bezpłatną wersję próbną ze strony internetowej.
### Czy mogę dodać wiele znaków wodnych do jednego dokumentu?
Absolutnie GroupDocs.Watermark umożliwia jednoczesne dodawanie wielu znaków wodnych, w tym tekstu, obrazu i adnotacji, w celu zwiększenia bezpieczeństwa dokumentów i budowania marki.
### Czy dostępna jest pomoc techniczna dla użytkowników GroupDocs.Watermark?
Tak, GroupDocs zapewnia wszechstronną pomoc techniczną za pośrednictwem forów i dedykowanych kanałów pomocy, aby pomóc użytkownikom w razie jakichkolwiek pytań lub problemów, jakie mogą napotkać.