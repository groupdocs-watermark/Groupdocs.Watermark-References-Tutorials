---
title: Generovat náhled dokumentu
linktitle: Generovat náhled dokumentu
second_title: GroupDocs.Watermark .NET API
description: V této příručce se dozvíte, jak generovat náhledy dokumentů pomocí GroupDocs.Watermark for .NET. Vylepšete zabezpečení a správu dokumentů bez námahy.
weight: 10
url: /cs/net/document-manipulation/generate-document-preview/
---
## Úvod
Ve světě správy digitálních dokumentů hraje vodoznak zásadní roli při zajišťování bezpečnosti a pravosti dokumentů. GroupDocs.Watermark for .NET je výkonný nástroj, který umožňuje vývojářům přidávat vodoznaky do dokumentů bez námahy. V tomto tutoriálu vás provedeme procesem generování náhledů dokumentů pomocí GroupDocs.Watermark for .NET. Ať už jste zkušený vývojář nebo teprve začínáte, tato příručka vám poskytne komplexní postup krok za krokem k dosažení vašeho cíle.
## Předpoklady
Než se pustíte do implementace, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:
- Základní znalost C# a .NET frameworku.
- Visual Studio nainstalované na vašem počítači.
- GroupDocs.Watermark pro knihovnu .NET. Můžeš[stáhněte si to zde](https://releases.groupdocs.com/Watermark/net/).
-  Platná licence pro GroupDocs.Watermark. Buď si ho můžete koupit[tady](https://purchase.groupdocs.com/buy) nebo získat a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) pro účely hodnocení.
## Importovat jmenné prostory
Chcete-li ve svém projektu začít používat GroupDocs.Watermark, budete muset importovat potřebné jmenné prostory. To lze provést přidáním následujících pomocí direktiv do vašeho kódu:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Tyto jmenné prostory budou poskytovat přístup ke třídám a metodám potřebným pro vodoznaky a generování náhledů dokumentů.

Pojďme si proces generování náhledu dokumentu rozdělit do jednoduchých a snadno pochopitelných kroků.
## Krok 1: Nastavte svůj projekt
Nejprve nastavte svůj projekt .NET v sadě Visual Studio. Pokud ještě nemáte projekt, vytvořte nový podle následujících kroků:
1. Otevřete Visual Studio.
2. Klikněte na „Vytvořit nový projekt“.
3. Vyberte „Console App (.NET Core)“ a klikněte na „Další“.
4. Pojmenujte svůj projekt a vyberte umístění pro jeho uložení, poté klikněte na „Vytvořit“.
## Krok 2: Nainstalujte GroupDocs.Watermark for .NET
Chcete-li ve svém projektu použít GroupDocs.Watermark, musíte nainstalovat knihovnu. To lze provést pomocí NuGet Package Manager:
1. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
2. Vyberte „Spravovat balíčky NuGet“.
3. Na kartě Procházet vyhledejte „GroupDocs.Watermark“.
4. Kliknutím na „Instalovat“ přidáte knihovnu do svého projektu.
Případně jej můžete nainstalovat prostřednictvím konzoly Správce balíčků:
```powershell
Install-Package GroupDocs.Watermark
```
## Krok 3: Definujte cestu k dokumentu a výstupní adresář
Před vygenerováním náhledu musíte zadat cestu k dokumentu, který chcete zobrazit, a adresář, do kterého budou obrázky náhledu uloženy:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Nahraďte "Cesta k vašemu dokumentu" cestou k dokumentu a "Adresář vašeho dokumentu" adresářem, do kterého chcete uložit náhledové obrázky.
## Krok 4: Inicializujte objekt vodoznaku
Vytvořte instanci souboru`Watermarker` třídy předáním cesty dokumentu jeho konstruktoru. Tento objekt bude použit k provádění všech operací vodoznaku:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Váš kód zde
}
```
## Krok 5: Vytvořte metody delegování pro zpracování datových proudů
Chcete-li vygenerovat náhled, musíte definovat metody delegování pro vytváření a uvolňování streamů. Tyto metody se postarají o vytvoření a uvolnění proudů pro každou stránku dokumentu:
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
 The`createPageStreamDelegate` metoda vytvoří proud pro každou stránku dokumentu, zatímco`releasePageStreamDelegate` metoda zavře stream po vygenerování náhledu.
## Krok 6: Nakonfigurujte možnosti náhledu
 Dále nakonfigurujte možnosti náhledu vytvořením instance souboru`PreviewOptions` třída. Zadejte metody delegování a nastavte formát náhledu na PNG. Můžete také určit, které stránky zahrnout do náhledu:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
V tomto příkladu generujeme náhledy pro první dvě stránky dokumentu.
## Krok 7: Vygenerujte náhled dokumentu
 Nakonec zavolejte na`GeneratePreview` metoda na`Watermarker`objekt, předávání nakonfigurovaného`PreviewOptions`. Tím se vygenerují náhledové obrázky a uloží je do určeného adresáře:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Závěr
Generování náhledů dokumentů pomocí GroupDocs.Watermark for .NET je jednoduchý proces, který lze provést pomocí několika řádků kódu. Podle kroků uvedených v této příručce můžete snadno nastavit svůj projekt, nakonfigurovat potřebné možnosti a generovat náhledy dokumentů. Tato výkonná knihovna nejen zjednodušuje proces vodoznaku, ale také poskytuje robustní funkce pro správu a manipulaci s vodoznaky.
 Pokud máte nějaké dotazy nebo potřebujete další pomoc, neváhejte a navštivte[Fórum podpory GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) nebo odkazovat na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/).
## FAQ
### Jaké formáty souborů podporuje GroupDocs.Watermark for .NET?
 GroupDocs.Watermark for .NET podporuje širokou škálu formátů souborů, včetně PDF, DOCX, PPTX, XLSX a mnoha dalších. Úplný seznam podporovaných formátů naleznete na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/).
### Mohu upravit vzhled vodoznaků?
Ano, GroupDocs.Watermark umožňuje plně přizpůsobit vzhled vodoznaků, včetně textových, obrazových a tvarových vodoznaků. Můžete upravit vlastnosti, jako je písmo, barva, velikost a průhlednost.
### Je k dispozici zkušební verze?
 Ano, můžete získat a[zkušební verze zdarma](https://releases.groupdocs.com/) GroupDocs.Watermark for .NET k vyhodnocení jeho funkcí před nákupem.
### Jak si mohu zakoupit licenci pro GroupDocs.Watermark?
 Můžete si zakoupit licenci pro GroupDocs.Watermark[tady](https://purchase.groupdocs.com/buy). K dispozici jsou různé možnosti licencování, které vyhovují různým potřebám.
### Mohu použít GroupDocs.Watermark v komerčním projektu?
 Ano, s platnou licencí můžete GroupDocs.Watermark používat v komerčních projektech. Nezapomeňte si přečíst licenční podmínky na webu[nákupní stránku](https://purchase.groupdocs.com/buy).