---
title: Wygeneruj podgląd dokumentu
linktitle: Wygeneruj podgląd dokumentu
second_title: GroupDocs.Watermark API .NET
description: Z tego przewodnika dowiesz się, jak generować podglądy dokumentów przy użyciu GroupDocs.Watermark dla platformy .NET. Bez wysiłku zwiększ bezpieczeństwo swoich dokumentów i zarządzanie nimi.
type: docs
weight: 10
url: /pl/net/document-manipulation/generate-document-preview/
---
## Wstęp
W świecie cyfrowego zarządzania dokumentami znak wodny odgrywa kluczową rolę w zapewnieniu bezpieczeństwa i autentyczności dokumentów. GroupDocs.Watermark dla .NET to potężne narzędzie, które umożliwia programistom bezproblemowe dodawanie znaków wodnych do dokumentów. W tym samouczku przeprowadzimy Cię przez proces generowania podglądów dokumentów przy użyciu GroupDocs.Watermark dla .NET. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik zapewni Ci kompleksowy proces krok po kroku prowadzący do osiągnięcia celu.
## Warunki wstępne
Zanim przejdziesz do wdrożenia, upewnijmy się, że masz wszystko, czego potrzebujesz, aby rozpocząć:
- Podstawowa znajomość frameworku C# i .NET.
- Program Visual Studio zainstalowany na Twoim komputerze.
- Biblioteka GroupDocs.Watermark dla .NET. Możesz[Pobierz to tutaj](https://releases.groupdocs.com/Watermark/net/).
-  Ważna licencja na GroupDocs.Watermark. Możesz albo kupić[Tutaj](https://purchase.groupdocs.com/buy) lub uzyskaj[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/) w celach ewaluacyjnych.
## Importuj przestrzenie nazw
Aby rozpocząć korzystanie z GroupDocs.Watermark w swoim projekcie, musisz zaimportować niezbędne przestrzenie nazw. Można to zrobić, dodając do kodu następujące dyrektywy using:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Te przestrzenie nazw zapewnią dostęp do klas i metod wymaganych do znakowania wodnego i generowania podglądów dokumentów.

Podzielmy proces generowania podglądu dokumentu na proste, łatwe do wykonania kroki.
## Krok 1: Skonfiguruj swój projekt
Na początek skonfiguruj projekt .NET w programie Visual Studio. Jeśli nie masz jeszcze projektu, utwórz nowy, wykonując następujące kroki:
1. Otwórz Visual Studio.
2. Kliknij „Utwórz nowy projekt”.
3. Wybierz „Aplikacja konsolowa (.NET Core)” i kliknij „Dalej”.
4. Nazwij swój projekt i wybierz lokalizację, w której chcesz go zapisać, a następnie kliknij „Utwórz”.
## Krok 2: Zainstaluj GroupDocs.Watermark dla .NET
Aby użyć GroupDocs.Watermark w swoim projekcie, musisz zainstalować bibliotekę. Można to zrobić za pomocą Menedżera pakietów NuGet:
1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań.
2. Wybierz opcję „Zarządzaj pakietami NuGet”.
3. Wyszukaj „GroupDocs.Watermark” na karcie Przeglądaj.
4. Kliknij „Zainstaluj”, aby dodać bibliotekę do swojego projektu.
Alternatywnie możesz zainstalować go za pomocą konsoli Menedżera pakietów:
```powershell
Install-Package GroupDocs.Watermark
```
## Krok 3: Zdefiniuj ścieżkę dokumentu i katalog wyjściowy
Przed wygenerowaniem podglądu należy określić ścieżkę dokumentu, który chcemy wyświetlić oraz katalog, w którym będą zapisywane obrazy podglądu:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Zastąp „Ścieżka Twojego dokumentu” ścieżką do dokumentu, a „Katalog Twojego dokumentu” katalogiem, w którym chcesz zapisać obrazy podglądu.
## Krok 4: Zainicjuj obiekt znaku wodnego
Utwórz instancję`Watermarker` klasę, przekazując ścieżkę dokumentu do jego konstruktora. Obiekt ten będzie używany do wykonywania wszelkich operacji związanych ze znakiem wodnym:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Twój kod tutaj
}
```
## Krok 5: Utwórz metody delegowania do obsługi strumienia
Aby wygenerować podgląd, musisz zdefiniować metody delegowania do tworzenia i udostępniania strumieni. Metody te obsłużą tworzenie i udostępnianie strumieni dla każdej strony dokumentu:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 The`createPageStreamDelegate` Metoda tworzy strumień dla każdej strony dokumentu, natomiast metoda`releasePageStreamDelegate` Metoda zamyka strumień po wygenerowaniu podglądu.
## Krok 6: Skonfiguruj opcje podglądu
 Następnie skonfiguruj opcje podglądu, tworząc instancję pliku`PreviewOptions` klasa. Określ metody delegowania i ustaw format podglądu na PNG. Możesz także określić, które strony mają być uwzględnione w podglądzie:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
W tym przykładzie generujemy podglądy dla pierwszych dwóch stron dokumentu.
## Krok 7: Wygeneruj podgląd dokumentu
 Na koniec zadzwoń do`GeneratePreview` metoda na`Watermarker`obiekt, przekazując skonfigurowany`PreviewOptions`. Spowoduje to wygenerowanie obrazów podglądu i zapisanie ich w określonym katalogu:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Wniosek
Generowanie podglądów dokumentów przy użyciu GroupDocs.Watermark dla .NET to prosty proces, który można wykonać za pomocą zaledwie kilku linijek kodu. Postępując zgodnie z krokami opisanymi w tym przewodniku, możesz łatwo skonfigurować swój projekt, skonfigurować niezbędne opcje i wygenerować podglądy swoich dokumentów. Ta potężna biblioteka nie tylko upraszcza proces znakowania wodnego, ale także zapewnia zaawansowane funkcje zarządzania znakami wodnymi i manipulowania nimi.
 Jeśli masz jakieś pytania lub potrzebujesz dalszej pomocy, nie wahaj się odwiedzić witryny[Forum pomocy technicznej GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) lub zapoznaj się z[dokumentacja](https://reference.groupdocs.com/Watermark/net/).
## Często zadawane pytania
### Jakie formaty plików są obsługiwane przez GroupDocs.Watermark dla .NET?
 GroupDocs.Watermark dla .NET obsługuje szeroką gamę formatów plików, w tym PDF, DOCX, PPTX, XLSX i wiele innych. Pełna lista obsługiwanych formatów znajduje się na stronie[dokumentacja](https://reference.groupdocs.com/Watermark/net/).
### Czy mogę dostosować wygląd znaków wodnych?
Tak, GroupDocs.Watermark umożliwia pełne dostosowanie wyglądu znaków wodnych, w tym znaków wodnych zawierających tekst, obraz i kształt. Można dostosować właściwości, takie jak czcionka, kolor, rozmiar i przezroczystość.
### Czy dostępna jest wersja próbna?
 Tak, możesz uzyskać[bezpłatna wersja próbna](https://releases.groupdocs.com/) GroupDocs.Watermark dla .NET w celu oceny jego funkcji przed dokonaniem zakupu.
### Jak mogę kupić licencję na GroupDocs.Watermark?
 Możesz kupić licencję na GroupDocs.Watermark[Tutaj](https://purchase.groupdocs.com/buy). Dostępne są różne opcje licencjonowania dostosowane do różnych potrzeb.
### Czy mogę używać GroupDocs.Watermark w projekcie komercyjnym?
 Tak, mając ważną licencję, możesz używać GroupDocs.Watermark w projektach komercyjnych. Koniecznie zapoznaj się z warunkami licencji dostępnymi na stronie[strona zakupu](https://purchase.groupdocs.com/buy).