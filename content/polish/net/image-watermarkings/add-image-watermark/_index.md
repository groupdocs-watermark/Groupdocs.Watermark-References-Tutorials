---
title: Dodaj znak wodny obrazu
linktitle: Dodaj znak wodny obrazu
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodawać graficzne znaki wodne do swoich dokumentów za pomocą GroupDocs.Watermark dla platformy .NET, korzystając ze szczegółowego samouczka krok po kroku.
weight: 11
url: /pl/net/image-watermarkings/add-image-watermark/
type: docs
---
# Dodaj znak wodny obrazu

## Wstęp
Witamy w tym obszernym przewodniku na temat dodawania znaków wodnych do obrazów przy użyciu GroupDocs.Watermark dla .NET! Znak wodny to skuteczny sposób ochrony dokumentów i obrazów przed nieupoważnionym użyciem, zapewniający bezpieczeństwo Twojej własności intelektualnej. W tym samouczku przeprowadzimy Cię przez cały proces, od skonfigurowania środowiska po nałożenie znaku wodnego na dokumenty. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik będzie pomocny i łatwy w obsłudze.
## Warunki wstępne
Zanim przejdziemy do samouczka, upewnijmy się, że masz wszystko, czego potrzebujesz:
- Środowisko programistyczne: Visual Studio lub dowolne IDE kompatybilne z .NET
- .NET Framework: .NET Framework 4.0 lub nowszy
-  GroupDocs.Watermark dla .NET: Możesz go pobrać z[Witryna GroupDocs](https://releases.groupdocs.com/Watermark/net/)
-  Plik obrazu: plik obrazu do wykorzystania jako znak wodny (np.`watermark.jpg`)
- Plik dokumentu: dokument, do którego chcesz dodać znak wodny (np.`presentation.pptx`)
## Importuj przestrzenie nazw
Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Jest to niezbędne do uzyskania dostępu do funkcji GroupDocs.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
W tej sekcji podzielimy proces dodawania obrazu znaku wodnego na jasne i łatwe do wykonania etapy. Uważnie postępuj zgodnie z każdym krokiem, aby pomyślnie oznaczyć dokument znakiem wodnym.
## Krok 1: Skonfiguruj swoje środowisko
 Najpierw upewnij się, że środowisko programistyczne jest prawidłowo skonfigurowane. Zainstaluj bibliotekę GroupDocs.Watermark, pobierając ją z witryny[Witryna GroupDocs](https://releases.groupdocs.com/Watermark/net/).
1. Otwórz swój projekt w programie Visual Studio.
2. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań.
3. Wybierz „Zarządzaj pakietami NuGet…”
4.  Szukaj`GroupDocs.Watermark` i zainstaluj go.
## Krok 2: Zdefiniuj ścieżki plików
Następnie musisz zdefiniować ścieżki dokumentu wejściowego i katalogu wyjściowego. Pomaga to programowi zlokalizować pliki, z którymi musi pracować.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Zastępować`"Your Document Path"` I`"Your Document Directory"` z rzeczywistymi ścieżkami do dokumentu i żądanym katalogiem wyjściowym.
## Krok 3: Zainicjuj znak wodny
Teraz zainicjuj`Watermarker` class ze ścieżką do dokumentu. Klasa ta odpowiada za zarządzanie procesem znakowania wodnego.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Przejdź do kolejnych kroków w ramach tego bloku
}
```
## Krok 4: Utwórz znak wodny obrazu
 W ramach`Watermarker` blok, utwórz instancję`ImageWatermark` class, używając ścieżki do obrazu znaku wodnego. Ta klasa reprezentuje obraz, którego chcesz użyć jako znaku wodnego.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Przejdź do następnego kroku w ramach tego bloku
}
```
## Krok 5: Dodaj znak wodny do dokumentu
 Z`ImageWatermark` instancja jest gotowa, dodaj ją do swojego dokumentu za pomocą`Add` metoda`Watermarker` klasa.
```csharp
watermarker.Add(watermark);
```
## Krok 6: Zapisz dokument
Na koniec zapisz dokument ze znakiem wodnym w określonym katalogu wyjściowym. Ten krok gwarantuje, że zmiany zostaną zapisane w nowym pliku.
```csharp
watermarker.Save(outputFileName);
```
## Wniosek
Gratulacje! Pomyślnie dodałeś obrazowy znak wodny do swojego dokumentu za pomocą GroupDocs.Watermark dla .NET. Postępując zgodnie z tym przewodnikiem krok po kroku, możesz łatwo chronić swoje dokumenty za pomocą niestandardowych znaków wodnych. Pamiętaj, że znak wodny to kluczowy krok w ochronie zasobów cyfrowych przed nieupoważnionym użyciem.

## Często zadawane pytania
### Jakie formaty plików są obsługiwane przez GroupDocs.Watermark?
GroupDocs.Watermark obsługuje szeroką gamę formatów plików, w tym PDF, DOCX, PPTX, XLSX i pliki obrazów, takie jak JPEG i PNG.
### Czy mogę używać GroupDocs.Watermark z platformą .NET Core?
Tak, GroupDocs.Watermark jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Watermark?
 Licencję tymczasową można uzyskać od firmy[Witryna GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Czy można dodać wiele znaków wodnych do jednego dokumentu?
 Absolutnie! Możesz dodać wiele znaków wodnych, wywołując metodę`Add` metodę wielokrotnie z różnymi instancjami znaku wodnego.
### Gdzie mogę znaleźć więcej przykładów i dokumentacji?
 Więcej przykładów i szczegółową dokumentację można znaleźć na stronie[Dokumentacja GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).