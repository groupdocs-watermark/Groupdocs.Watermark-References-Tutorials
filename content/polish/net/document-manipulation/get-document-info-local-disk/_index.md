---
title: Pobierz informacje o dokumencie z dysku lokalnego
linktitle: Pobierz informacje o dokumencie z dysku lokalnego
second_title: GroupDocs.Watermark API .NET
description: tego obszernego przewodnika krok po kroku dowiesz się, jak dodawać, usuwać i wyodrębniać znaki wodne w dokumentach za pomocą programu GroupDocs.
type: docs
weight: 11
url: /pl/net/document-manipulation/get-document-info-local-disk/
---
## Wstęp
Witamy w najlepszym przewodniku na temat korzystania z GroupDocs.Watermark dla .NET! Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten artykuł przeprowadzi Cię przez podstawowe informacje dotyczące znakowania wodnego w dokumentach za pomocą tego potężnego narzędzia. Ostatecznie będziesz profesjonalistą w osadzaniu znaków wodnych w swoich dokumentach, zapewniając ich ochronę i oznakowanie marki zgodnie ze specyfikacjami.
## Warunki wstępne
Zanim zagłębisz się w przewodnik krok po kroku, musisz spełnić kilka warunków wstępnych:
1.  .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET Framework w swoim systemie. GroupDocs.Watermark dla .NET jest kompatybilny z różnymi wersjami .NET Framework, dlatego sprawdź[dokumentacja](https://reference.groupdocs.com/Watermark/net/) aby poznać szczegóły dotyczące kompatybilności.
2.  Biblioteka GroupDocs.Watermark dla .NET: Pobierz i zainstaluj najnowszą wersję z[strona pobierania](https://releases.groupdocs.com/Watermark/net/).
3. Środowisko programistyczne: Powinieneś mieć skonfigurowane środowisko programistyczne. Visual Studio jest popularnym wyborem do programowania .NET.
4. Podstawowa znajomość języka C#: Zrozumienie podstaw programowania w języku C# pomoże Ci postępować zgodnie z przykładami.
## Importuj przestrzenie nazw
Zanim będziesz mógł używać GroupDocs.Watermark dla .NET, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Jest to prosty proces i niezbędny do uzyskania dostępu do funkcji biblioteki.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Podzielmy proces dodawania znaku wodnego do dokumentu na jasne i łatwe do wykonania etapy. Każdy krok ma na celu pomóc Ci w łatwym zrozumieniu i zaimplementowaniu funkcjonalności.
## Krok 1: Załaduj swój dokument
 Pierwszym krokiem jest załadowanie dokumentu, do którego chcesz dodać znak wodny. Odbywa się to za pomocą`Watermarker` class, która umożliwia dostęp do dokumentu i manipulowanie nim.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Dokument jest teraz załadowany i gotowy do dodania znaku wodnego
}
```
 W tym kroku wymień`"Your Document Path"` z rzeczywistą ścieżką do dokumentu. To inicjuje`Watermarker`obiektu, zapewniając dostęp do różnych funkcji znaku wodnego.
## Krok 2: Uzyskaj informacje o dokumencie
Przed dodaniem znaku wodnego warto zebrać informacje o dokumencie. Może to być przydatne do dostosowywania znaku wodnego na podstawie właściwości dokumentu.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Na tym etapie`GetDocumentInfo` Metoda pobiera szczegółowe informacje, takie jak typ pliku, liczba stron i rozmiar dokumentu. Informacje te są drukowane na konsoli, ale w razie potrzeby możesz ich użyć w swojej aplikacji.
## Krok 3: Dodaj tekstowy znak wodny
Teraz, gdy masz już załadowany dokument i zawarte w nim informacje, czas dodać znak wodny. Zaczniemy od prostego tekstowego znaku wodnego.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Tutaj tworzysz`TextWatermark` obiekt z żądanym tekstem, czcionką i stylem. Dostosuj właściwości, takie jak kolor, krycie i kąt obrotu, do swoich potrzeb. Na koniec znak wodny jest dodawany do dokumentu i zapisywany w określonej ścieżce.
## Krok 4: Dodaj znak wodny obrazu
Tekstowe znaki wodne są świetne, ale co, jeśli chcesz dodać logo lub inny obraz? W tym kroku opisano sposób dodawania znaku wodnego obrazu.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Zastępować`"Path to Your Image"` ze ścieżką do obrazu znaku wodnego. Ustaw właściwości, takie jak krycie i kąt obrotu, aby dostosować wygląd znaku wodnego obrazu. Proces dodawania i zapisywania znaku wodnego jest podobny do procesu dodawania tekstowego znaku wodnego.
## Krok 5: Usuń istniejące znaki wodne
 Czasami może być konieczne usunięcie istniejących znaków wodnych z dokumentu. Można to zrobić za pomocą`Remove` metoda podana przez`Watermarker` klasa.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Tutaj`Remove` metoda służy do usuwania tekstowych znaków wodnych z dokumentu. W zależności od potrzeb możesz określić różne typy znaków wodnych do usunięcia, np. obraz lub tekst. Zapisz dokument w nowej ścieżce, aby zobaczyć zmiany.
## Krok 6: Wyodrębnij znaki wodne
Jeśli chcesz wyodrębnić i sprawdzić znaki wodne z dokumentu, GroupDocs.Watermark dla .NET ułatwia to.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Dodatkowe właściwości i logika każdego znaku wodnego
    }
}
```
 Ten krok polega na użyciu`GetWatermarks`metoda pobierania wszystkich znaków wodnych w dokumencie. Następnie możesz przeglądać listę znaków wodnych i sprawdzać ich właściwości lub w razie potrzeby wykonać dodatkowe czynności.
## Wniosek
 Gratulacje! Wiesz już, jak używać GroupDocs.Watermark dla .NET do dodawania, usuwania i wyodrębniania znaków wodnych z dokumentów. Dzięki tym umiejętnościom możesz skutecznie chronić i oznaczać swoje dokumenty. Zapamiętaj[dokumentacja](https://reference.groupdocs.com/Watermark/net/) jest zawsze dostępny, jeśli potrzebujesz bardziej szczegółowych informacji lub zaawansowanych funkcji.
## Często zadawane pytania
### Czy mogę używać GroupDocs.Watermark dla .NET z dowolną wersją .NET?
 Tak, GroupDocs.Watermark dla .NET jest kompatybilny z różnymi wersjami .NET Framework. Sprawdź[dokumentacja](https://reference.groupdocs.com/Watermark/net/) dla szczegółów.
### Gdzie mogę pobrać GroupDocs.Watermark dla .NET?
 Najnowszą wersję można pobrać ze strony[strona pobierania](https://releases.groupdocs.com/Watermark/net/).
### Jak uzyskać licencję tymczasową?
 Licencję tymczasową można uzyskać od firmy[strona licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/).
### Czy dostępny jest bezpłatny okres próbny?
 Tak, możesz rozpocząć bezpłatny okres próbny, odwiedzając stronę[bezpłatna strona próbna](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc, jeśli napotkam problemy?
 Wsparcie jest dostępne na stronie[Forum znaku wodnego GroupDocs](https://forum.groupdocs.com/c/watermark/19).