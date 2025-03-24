---
title: Dodaj zablokowany znak wodny do określonych stron w dokumentach programu Word
linktitle: Dodaj zablokowany znak wodny do określonych stron w dokumentach programu Word
second_title: GroupDocs.Watermark API .NET
description: Dowiedz się, jak dodać zablokowany znak wodny do określonych stron w dokumentach programu Word za pomocą programu GroupDocs.Watermark dla platformy .NET, korzystając z naszego prostego przewodnika krok po kroku.
weight: 12
url: /pl/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---
## Wstęp
Czy chcesz dodać znak wodny do określonych stron dokumentów programu Word, ale chcesz, aby był on zablokowany, aby nie można było go łatwo usunąć lub edytować? Jesteś we właściwym miejscu! W tym samouczku przeprowadzimy Cię przez proces dodawania zablokowanego znaku wodnego do określonych stron w dokumentach programu Word za pomocą GroupDocs.Watermark dla .NET. Ta potężna biblioteka ułatwia stosowanie, zarządzanie i dostosowywanie znaków wodnych na różnych typach dokumentów. Niezależnie od tego, czy jesteś programistą, czy po prostu osobą, która musi zabezpieczyć swoje dokumenty, ten przewodnik w prosty sposób przeprowadzi Cię przez każdy krok.
## Warunki wstępne
Zanim przejdziemy do samouczka, upewnijmy się, że masz wszystko, czego potrzebujesz:
1.  GroupDocs.Watermark dla .NET: Możesz[pobierać](https://releases.groupdocs.com/Watermark/net/) Najnowsza wersja.
2. Środowisko programistyczne: IDE takie jak Visual Studio.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie pomocna.
4. Dokument do znaku wodnego: dokument programu Word (.docx lub .doc), do którego chcesz dodać znak wodny.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#. Te przestrzenie nazw zapewniają dostęp do klas i metod wymaganych do pracy z GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Teraz, gdy mamy już spełnione wymagania wstępne i zaimportowane niezbędne przestrzenie nazw, przeanalizujmy proces krok po kroku.
## Krok 1: Załaduj dokument Word
 Na początek musisz załadować dokument Word, do którego chcesz dodać znak wodny. Można to zrobić za pomocą`Watermarker` klasa wraz z`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Przejdź do kolejnych kroków
}
```
## Krok 2: Utwórz tekstowy znak wodny
Następnie utwórz tekstowy znak wodny. Możesz dostosować tekst, czcionkę, kolor i inne właściwości zgodnie ze swoimi wymaganiami.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Krok 3: Skonfiguruj opcje znaku wodnego
 Aby zastosować znak wodny do określonych stron i zablokować go, skonfiguruj`WordProcessingWatermarkPagesOptions`Tutaj określasz numery stron, na których powinien pojawić się znak wodny i ustawiasz opcje blokowania.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Określ strony
options.IsLocked = true; // Zablokuj znak wodny
options.LockType = WordProcessingLockType.AllowOnlyComments; // Ustaw typ blokady
// Aby zabezpieczyć hasłem
// opcje.Hasło = "7654321";
```
## Krok 4: Dodaj znak wodny do dokumentu
Po skonfigurowaniu znaku wodnego i opcji możesz teraz dodać znak wodny do dokumentu.
```csharp
watermarker.Add(watermark, options);
```
## Krok 5: Zapisz dokument
Na koniec zapisz dokument z zastosowanym znakiem wodnym. Wybierz odpowiednią ścieżkę wyjściową i zapisz plik.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Wniosek
Gratulacje! Pomyślnie dodałeś zablokowany znak wodny do określonych stron dokumentu programu Word przy użyciu GroupDocs.Watermark dla .NET. W tym samouczku omówiono wszystkie niezbędne kroki, od załadowania dokumentu do zapisania pliku ze znakiem wodnym. Wykonując poniższe kroki, możesz mieć pewność, że Twoje dokumenty będą bezpiecznie oznaczone znakiem wodnym, chroniąc zawartość przed nieuprawnioną edycją i wykorzystaniem.
 Aby uzyskać więcej informacji, możesz zapoznać się z[Dokumentacja GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Jeśli masz jakieś pytania lub potrzebujesz dalszej pomocy, odwiedź stronę[forum wsparcia](https://forum.groupdocs.com/c/watermark/19).
## Często zadawane pytania
### Co to jest GroupDocs.Watermark dla .NET?
GroupDocs.Watermark dla .NET to potężna biblioteka, która umożliwia programistom dodawanie znaków wodnych do różnych typów dokumentów, w tym Word, PDF, Excel i innych.
### Czy mogę zastosować znaki wodne na wielu stronach dokumentu?
 Tak, możesz określić wiele numerów stron w pliku`PageNumbers` array do stosowania znaków wodnych na wielu stronach.
### Jak chronić znak wodny hasłem?
 Możesz chronić znak wodny hasłem, ustawiając opcję`Password` nieruchomość w`WordProcessingWatermarkPagesOptions`.
### Czy można dostosować wygląd znaku wodnego?
Absolutnie! Możesz dostosować tekst, czcionkę, kolor, rozmiar i inne właściwości znaku wodnego do swoich potrzeb.
### Gdzie mogę uzyskać tymczasową licencję na GroupDocs.Watermark?
 Licencję tymczasową można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).