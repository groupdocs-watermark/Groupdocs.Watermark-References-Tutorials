---
title: Dodaj załącznik do pliku PDF
linktitle: Dodaj załącznik do pliku PDF
second_title: GroupDocs.Watermark API .NET
description: Zwiększ możliwości zarządzania dokumentami .NET dzięki GroupDocs.Watermark, który umożliwia bezproblemową obsługę znaków wodnych i załączników.
weight: 12
url: /pl/net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# Dodaj załącznik do pliku PDF

## Wstęp
W dziedzinie programowania .NET GroupDocs.Watermark wyróżnia się jako potężne narzędzie do zarządzania znakami wodnymi, adnotacjami i nie tylko w różnych formatach dokumentów. Niezależnie od tego, czy pracujesz z plikami PDF, dokumentami programu Word czy obrazami, GroupDocs.Watermark dla platformy .NET zapewnia bezproblemową integrację, która umożliwia programistom łatwe manipulowanie dokumentami.
## Warunki wstępne
Zanim zagłębisz się w zawiłości korzystania z GroupDocs.Watermark dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:
1.  Instalacja: Upewnij się, że zainstalowałeś GroupDocs.Watermark dla .NET. Można go pobrać z[strona wydania](https://releases.groupdocs.com/Watermark/net/).
2. Przygotowanie dokumentu: Przygotuj dokument, na którym chcesz wykonać znak wodny lub inne operacje.
3. Podstawowa znajomość języka C#: Zapoznaj się z podstawami języka programowania C#, ponieważ będziemy go używać do interakcji z interfejsem API GroupDocs.Watermark.

## Importuj przestrzenie nazw
Przed rozpoczęciem wdrożenia istotne jest zaimportowanie niezbędnych przestrzeni nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Watermark. Poniżej znajdują się wymagane przestrzenie nazw:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Krok 1: Załaduj dokument
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 W tym kroku określamy ścieżkę do dokumentu, z którym chcemy pracować i tworzymy plik`PdfLoadOptions` obiekt do ładowania dokumentów PDF. Następnie inicjujemy a`Watermarker` obiekt ze ścieżką dokumentu i opcjami ładowania.
## Krok 2: Pobierz zawartość PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Tutaj uzyskujemy zawartość dokumentu PDF za pomocą`GetContent<PdfContent>()` metoda.
## Krok 3: Dodaj załącznik
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Ten krok polega na dodaniu załącznika do dokumentu PDF. Musisz podać bajty, nazwę i opis pliku załącznika.
## Krok 4: Zapisz zmiany
```csharp
watermarker.Save(outputFileName);
```
Na koniec zapisujemy zmiany dokonane w dokumencie wraz z dodanym załącznikiem.

## Wniosek
GroupDocs.Watermark dla .NET oferuje solidne rozwiązanie do płynnego zarządzania znakami wodnymi i załącznikami dokumentów. Wykonując kroki opisane powyżej, możesz łatwo zintegrować funkcje znaków wodnych i załączników z aplikacjami .NET.
## Często zadawane pytania
### Czy GroupDocs.Watermark jest kompatybilny ze wszystkimi frameworkami .NET?
Tak, GroupDocs.Watermark obsługuje .NET Framework 2.0 i nowsze wersje.
### Czy mogę usunąć znaki wodne dodane za pomocą GroupDocs.Watermark?
Tak, GroupDocs.Watermark udostępnia metody usuwania znaków wodnych z dokumentów.
### Czy GroupDocs.Watermark obsługuje szyfrowanie dokumentów?
Tak, GroupDocs.Watermark umożliwia pracę z zaszyfrowanymi dokumentami.
### Czy mogę dostosować wygląd znaków wodnych?
Oczywiście GroupDocs.Watermark oferuje różne opcje dostosowywania znaków wodnych.
### Czy dostępna jest wersja próbna do celów testowych?
 Tak, możesz uzyskać dostęp do wersji próbnej z poziomu[strona z wydaniami](https://releases.groupdocs.com/).