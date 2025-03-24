---
title: Uzyskaj obsługiwane formaty plików
linktitle: Uzyskaj obsługiwane formaty plików
second_title: GroupDocs.Watermark API .NET
description: Bez wysiłku dodawaj znaki wodne do swoich dokumentów za pomocą GroupDocs.Watermark dla .NET. Postępuj zgodnie z naszym kompleksowym przewodnikiem krok po kroku, aby chronić swoje zasoby cyfrowe.
weight: 13
url: /pl/net/document-manipulation/get-supported-file-formats/
---

# Uzyskaj obsługiwane formaty plików

## Wstęp
Znak wodny dokumentów to kluczowy krok w zabezpieczaniu zasobów cyfrowych. Niezależnie od tego, czy chodzi o ochronę własności intelektualnej, zapewnienie poufności, czy po prostu budowanie marki, znaki wodne odgrywają kluczową rolę. Jeśli jesteś programistą .NET i chcesz zintegrować funkcje znaku wodnego ze swoimi aplikacjami, GroupDocs.Watermark dla .NET to potężne i wszechstronne narzędzie, które powinieneś wziąć pod uwagę. Ten samouczek poprowadzi Cię przez podstawowe informacje dotyczące korzystania z GroupDocs.Watermark, od instalacji po nałożenie pierwszego znaku wodnego, z podziałem na poszczególne kroki, abyś mógł łatwo wykonać wszystkie kroki.
## Warunki wstępne
Zanim przejdziemy do szczegółów, upewnijmy się, że masz wszystko, czego potrzebujesz, aby zacząć:
1.  Visual Studio: Upewnij się, że na komputerze jest zainstalowany program Visual Studio. Można go pobrać z[Witryna internetowa programu Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark obsługuje różne wersje .NET Framework. Upewnij się, że Twój projekt jest przeznaczony dla kompatybilnej wersji.
3. GroupDocs.Watermark dla .NET: Najnowszą wersję można pobrać z witryny[strona wydania](https://releases.groupdocs.com/Watermark/net/).
4. Podstawowa znajomość języka C#: W tym samouczku założono, że masz podstawową wiedzę na temat programowania w językach C# i .NET.
## Importuj przestrzenie nazw
Najpierw zaimportujmy niezbędne przestrzenie nazw do Twojego projektu. Otwórz plik C# i dodaj następujące instrukcje na górze:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Po zaimportowaniu tych przestrzeni nazw możesz rozpocząć dodawanie znaków wodnych do swoich dokumentów.

## Krok 1: Zainicjuj silnik znaku wodnego
 Pierwszym krokiem jest inicjalizacja silnika znaku wodnego. Wiąże się to z utworzeniem instancji`Watermarker` klasę z dokumentem, do którego chcesz dodać znak wodny.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Ten fragment kodu konfiguruje plik`Watermarker` obiekt, którego będziesz używać do stosowania znaków wodnych w dokumencie.
## Krok 2: Dodaj tekstowy znak wodny
Teraz dodajmy prosty tekstowy znak wodny do Twojego dokumentu. Tekstowe znaki wodne doskonale nadają się do dodawania etykiet takich jak „Poufne” lub „Wersja robocza”.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Tutaj stworzyliśmy`TextWatermark`obiekt z tekstem „Poufne”, ustaw jego czcionkę i kolor, a następnie wyrównaj go do środka dokumentu.
## Krok 3: Dodaj znak wodny obrazu
Jeśli wolisz użyć obrazu jako znaku wodnego, GroupDocs.Watermark ułatwia to.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 W tym przykładzie tworzymy plik`ImageWatermark` obiekt, ustaw jego wymiary i wyrównaj do prawego górnego rogu dokumentu.
## Krok 4: Zapisz dokument
Ostatnim krokiem po dodaniu żądanych znaków wodnych jest zapisanie zmodyfikowanego dokumentu.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Spowoduje to zapisanie dokumentu ze znakiem wodnym w określonej ścieżce i zwolnienie wszystkich używanych przez niego zasobów`Watermarker` instancja.
## Krok 5: Uzyskaj obsługiwane formaty plików
Aby sprawdzić, jakie formaty plików są obsługiwane przez GroupDocs.Watermark, możesz użyć następującego fragmentu kodu:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Spowoduje to wydrukowanie wszystkich typów plików obsługiwanych przez GroupDocs.Watermark, co daje kompleksowy obraz jego możliwości.
## Wniosek
Znakowanie wodne dokumentów za pomocą GroupDocs Watermark dla .NET jest proste i wydajne. Wykonując ten samouczek, nauczyłeś się inicjować silnik znaku wodnego, dodawać tekstowe i graficzne znaki wodne, zapisywać dokumenty ze znakami wodnymi oraz wyświetlać listę obsługiwanych formatów plików. Dzięki tym narzędziom możesz bezpiecznie chronić swoje dokumenty.
 Jeśli masz jakieś pytania lub potrzebujesz dalszej pomocy, nie wahaj się odwiedzić witryny[Forum pomocy technicznej GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## Często zadawane pytania
### Jak zainstalować GroupDocs.Watermark dla .NET?
 Można go pobrać z[strona wydania](https://releases.groupdocs.com/Watermark/net/) i dodaj bibliotekę DLL do swojego projektu.
### Czy mogę bezpłatnie wypróbować GroupDocs.Watermark?
 Tak, możesz poprosić o[bezpłatna wersja próbna](https://releases.groupdocs.com/) w celu oceny oprogramowania przed zakupem.
### Jakie formaty plików są obsługiwane przez GroupDocs.Watermark?
Możesz użyć dostarczonego fragmentu kodu, aby wyświetlić listę wszystkich obsługiwanych formatów plików.
### Jak mogę kupić licencję na GroupDocs.Watermark?
 Licencje można kupić bezpośrednio w witrynie[strona zakupu](https://purchase.groupdocs.com/buy).
### Czy dostępna jest dokumentacja dla GroupDocs.Watermark?
 Tak, dostępna jest obszerna dokumentacja[Tutaj](https://tutorials.groupdocs.com/Watermark/net/).