---
title: Wyodrębnij informacje o adnotacjach z pliku PDF
linktitle: Wyodrębnij informacje o adnotacjach z pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Z tego szczegółowego przewodnika krok po kroku dowiesz się, jak wyodrębnić informacje z adnotacji z dokumentów PDF przy użyciu narzędzia GroupDocs.Watermark dla platformy .NET.
weight: 23
url: /pl/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## Wstęp
Czy często musisz wyodrębnić szczegółowe informacje z adnotacji z dokumentów PDF? Niezależnie od tego, czy jesteś programistą pracującym nad systemami zarządzania dokumentami, czy profesjonalistą obsługującym wiele plików PDF, wydajne wyodrębnianie i przetwarzanie adnotacji może mieć kluczowe znaczenie. Dzięki GroupDocs.Watermark dla .NET masz do dyspozycji potężny zestaw narzędzi, dzięki którym to zadanie będzie proste i wydajne.
## Warunki wstępne
Zanim zagłębimy się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz, aby zacząć:
1. Visual Studio: Upewnij się, że masz zainstalowany program Visual Studio. To będzie nasze IDE do pisania i uruchamiania kodu.
2.  GroupDocs.Watermark dla .NET: Musisz mieć bibliotekę GroupDocs.Watermark dla .NET. Możesz[Pobierz to tutaj](https://releases.groupdocs.com/Watermark/net/).
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest konieczna, aby postępować zgodnie z przykładami.
## Importuj przestrzenie nazw
Na początek musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Te przestrzenie nazw zawierają klasy i metody wymagane do pracy z plikami PDF i wyodrębniania adnotacji.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Krok 1: Skonfiguruj swój projekt
Najpierw skonfigurujmy nasz projekt w Visual Studio. Utwórz nowy projekt aplikacji konsolowej (.NET Core). Po utworzeniu projektu musisz dodać odwołanie do biblioteki GroupDocs.Watermark for .NET.
1. Otwórz Menedżera pakietów NuGet.
2.  Szukaj`GroupDocs.Watermark`.
3.  Zainstaluj`GroupDocs.Watermark` pakiet.
## Krok 2: Zdefiniuj ścieżki dokumentów
Następnie musisz określić ścieżki wejściowego dokumentu PDF i katalog wyjściowy, w którym zostaną zapisane wyodrębnione informacje. Dzięki temu Twoja aplikacja będzie wiedzieć, gdzie znaleźć plik PDF i gdzie zapisać wyniki.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 3: Załaduj dokument PDF
 Aby pracować z dokumentem PDF, musimy go załadować za pomocą`PdfLoadOptions`. Ta klasa udostępnia opcje konfigurowania procesu ładowania.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tutaj będzie umieszczony kod wyodrębniający adnotacje
}
```
## Krok 4: Uzyskaj dostęp do treści PDF
Po załadowaniu dokumentu możemy uzyskać dostęp do jego zawartości. W szczególności chcemy uzyskać zawartość PDF, abyśmy mogli przeglądać strony i adnotacje.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Krok 5: Iteruj po stronach i adnotacjach
Mając pod ręką zawartość PDF, możemy przeglądać każdą stronę, a następnie każdą adnotację na tych stronach. Dzięki temu możemy wyodrębnić potrzebne nam informacje.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Wyodrębnij tutaj szczegóły adnotacji
    }
}
```
## Krok 6: Wyodrębnij szczegóły adnotacji
W zagnieżdżonych pętlach wyodrębniamy różne szczegóły dotyczące każdej adnotacji. Obejmuje to typ adnotacji, wszelkie powiązane obrazy, tekst i dane dotyczące pozycji.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Krok 7: Zapisz lub przetwórz wyodrębnione dane
Na koniec zdecyduj, co chcesz zrobić z wyodrębnionymi informacjami adnotacyjnymi. Możesz wydrukować go na konsolę, zapisać do pliku, a nawet przechowywać w bazie danych, w zależności od potrzeb.
```csharp
// Przykład zapisu wyodrębnionych danych do pliku
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Wniosek
Wyodrębnianie informacji o adnotacjach z dokumentów PDF przy użyciu programu GroupDocs.Watermark dla platformy .NET to prosty proces, który pozwala zaoszczędzić dużo czasu i wysiłku. Wykonując kroki opisane w tym przewodniku, możesz łatwo zintegrować tę funkcję ze swoimi projektami i zautomatyzować wyodrębnianie cennych danych adnotacji.
 Niezależnie od tego, czy zarządzasz dużymi ilościami plików PDF, czy po prostu chcesz wyodrębnić określone informacje, GroupDocs.Watermark dla .NET zapewnia niezawodne i wydajne rozwiązanie. Nie zapomnij sprawdzić[dokumentacja](https://tutorials.groupdocs.com/Watermark/net/) aby uzyskać bardziej zaawansowane funkcje i opcje dostosowywania.
## Często zadawane pytania
### Co to jest GroupDocs.Watermark dla .NET?
GroupDocs.Watermark dla .NET to obszerna biblioteka, która umożliwia programistom dodawanie, wyszukiwanie i usuwanie znaków wodnych z różnych formatów dokumentów, w tym plików PDF, dokumentów programu Word i obrazów.
### Czy mogę bezpłatnie wypróbować GroupDocs.Watermark?
 Tak, możesz dostać[bezpłatna wersja próbna](https://releases.groupdocs.com/) aby przetestować funkcje biblioteki przed dokonaniem zakupu.
### Jak uzyskać pomoc, jeśli napotkam problemy?
 Możesz uzyskać pomoc od zespołu GroupDocs, odwiedzając go[forum wsparcia](https://forum.groupdocs.com/c/watermark/19).
### Czy jest możliwość uzyskania tymczasowej licencji na testowanie?
 Tak, możesz poprosić o[licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/)do celów testowych.
### Gdzie mogę kupić pełną wersję GroupDocs.Watermark dla .NET?
 Pełną wersję można kupić na stronie[Witryna GroupDocs](https://purchase.groupdocs.com/buy).