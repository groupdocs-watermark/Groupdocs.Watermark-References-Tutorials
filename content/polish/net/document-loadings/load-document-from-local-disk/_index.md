---
title: Załaduj dokument z dysku lokalnego
linktitle: Załaduj dokument z dysku lokalnego
second_title: GroupDocs.Watermark API .NET
description: Chroń swoje dokumenty i zarządzaj nimi za pomocą Groupdocs dla .NET. Postępuj zgodnie z naszym szczegółowym przewodnikiem, aby bezproblemowo dodawać znaki wodne.
weight: 10
url: /pl/net/document-loadings/load-document-from-local-disk/
---

# Załaduj dokument z dysku lokalnego

## Wstęp
Dokumenty ze znakami wodnymi są niezbędne w dzisiejszej epoce cyfrowej, aby zapewnić ochronę treści, potwierdzenie własności i poufność. Groupdocs.Watermark dla .NET to potężna biblioteka, która umożliwia programistom dodawanie, wyszukiwanie i zarządzanie znakami wodnymi w różnych formatach dokumentów. W tym samouczku omówimy proces używania Groupdocs.Watermark dla platformy .NET do dodawania znaków wodnych do dokumentów, korzystając ze szczegółowych instrukcji krok po kroku.
## Warunki wstępne
Zanim przejdziesz do wdrożenia, upewnij się, że masz następujące elementy:
1. Zainstalowany program Visual Studio: Będziesz potrzebować programu Visual Studio lub innego kompatybilnego środowiska .NET IDE.
2.  Groupdocs.Watermark dla .NET: Pobierz bibliotekę z[link do pobrania](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET Framework 4.6.1 lub nowszą.
4. Przykładowy dokument: Przygotuj przykładowy dokument, aby przetestować proces znakowania wodnego.
## Importuj przestrzenie nazw
Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Są one niezbędne do uzyskania dostępu do klas i metod wymaganych do znakowania wodnego.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Załaduj dokument z dysku lokalnego
Najpierw musisz załadować dokument z dysku lokalnego. To ten dokument będzie tym, do którego dodasz znak wodny.
Zdefiniuj ścieżkę dokumentu, do którego chcesz dodać znak wodny.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Krok 2: Zainicjuj opcje ładowania
 Następnie zainicjuj opcje ładowania. Na przykład, jeśli pracujesz z dokumentem programu Word, użyjesz`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Krok 3: Utwórz i skonfiguruj znak wodny
 Teraz utworzysz instancję`Watermarker` klasa. Ta instancja będzie używana do zarządzania znakami wodnymi i stosowania ich w dokumencie.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ten blok będzie zawierał dalsze kroki, aby dodać i zapisać znak wodny
}
```
## Krok 4: Utwórz znak wodny
Utwórz tekstowy znak wodny. Ten znak wodny może zawierać dowolny wybrany tekst. Tutaj użyjemy „Testowego znaku wodnego”.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Krok 5: Dodaj znak wodny do dokumentu
Dodaj utworzony znak wodny do dokumentu za pomocą`Add` metoda`Watermarker` klasa.
```csharp
watermarker.Add(watermark);
```
## Krok 6: Zapisz dokument ze znakiem wodnym
Na koniec zapisz dokument ze znakiem wodnym w określonej ścieżce.
```csharp
watermarker.Save(outputFileName);
```

## Wniosek
Dodawanie znaków wodnych do dokumentów przy użyciu programu Groupdocs dla platformy .NET jest proste i wydajne. Ten przewodnik przeprowadził Cię przez cały proces, od konfiguracji środowiska po zapisanie dokumentu ze znakiem wodnym. Dzięki temu potężnemu narzędziu możesz mieć pewność, że Twoje dokumenty będą chronione, a Twoja własność intelektualna będzie bezpieczna. 
 Aby uzyskać więcej informacji, sprawdź[dokumentacja](https://tutorials.groupdocs.com/Watermark/net/) , a jeśli napotkasz jakiekolwiek problemy,[forum wsparcia](https://forum.groupdocs.com/c/watermark/19) to doskonałe miejsce na pomoc. 
## Często zadawane pytania
### Czy mogę używać niestandardowych czcionek w znakach wodnych?
Tak, Groupdocs obsługuje niestandardowe czcionki. Możesz określić dowolną czcionkę zainstalowaną w systemie.
### Jakie typy dokumentów są obsługiwane?
Groupdocs.Watermark obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PDF, PowerPoint i inne.
### Jak usunąć znak wodny z dokumentu?
 Możesz skorzystać z`Remove` metoda podana przez`Watermarker` klasa do usuwania znaków wodnych.
### Czy można dodać znaki wodne do obrazów?
 Tak, możesz dodawać obrazy wodne za pomocą`ImageWatermark` klasa.
### Czy mogę bezpłatnie wypróbować Groupdocs.Watermark?
 Oczywiście, możesz pobrać plik[bezpłatna wersja próbna](https://releases.groupdocs.com/) aby ocenić bibliotekę przed zakupem.