---
title: Přidejte vodoznaky na konkrétní stránky v PDF
linktitle: Přidejte vodoznaky na konkrétní stránky v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat textové a obrazové vodoznaky na konkrétní stránky v PDF pomocí Groupdocs. Zabezpečte své dokumenty podle našeho podrobného průvodce.
weight: 15
url: /cs/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
---
## Úvod
Přidání vodoznaků do dokumentů PDF je zásadním krokem při ochraně vašeho obsahu a prosazování vašeho vlastnictví. Ať už označujete koncept, zajišťujete citlivé informace nebo jednoduše přidáváte značku, vodoznaky jsou účinným nástrojem. V tomto tutoriálu prozkoumáme, jak používat Groupdocs.Watermark pro .NET k přidávání textových i obrazových vodoznaků na konkrétní stránky v souborech PDF. Rozdělíme proces do zvládnutelných kroků a zajistíme, že budete moci tyto funkce sledovat a implementovat do svých projektů.
## Předpoklady
Než se pustíte do implementace, ujistěte se, že máte splněny následující předpoklady:
- Nainstalované Visual Studio: K psaní a spouštění kódu .NET budete potřebovat IDE, jako je Visual Studio.
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
-  Groupdocs.Watermark pro .NET: Stáhněte a nainstalujte Groupdocs.Watermark pro .NET. Můžeš to dostat[tady](https://releases.groupdocs.com/Watermark/net/).
- Základní znalost C#: Výhodou bude znalost programovacího jazyka C#.
- Dokument PDF: Připravte si soubor PDF, který můžete použít k testování přidávání vodoznaků.
## Importovat jmenné prostory
Chcete-li začít, budete muset do projektu importovat potřebné jmenné prostory. Tento krok je zásadní, protože umožňuje přístup k třídám a metodám Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Nastavení projektu
### Vytvořit nový projekt
Nejprve otevřete Visual Studio a vytvořte nový projekt C#. Pro jednoduchost si můžete vybrat konzolovou aplikaci.
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### Nainstalujte Groupdocs.Watermark
Dále nainstalujte knihovnu Groupdocs.Watermark prostřednictvím NuGet Package Manager.
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
Vyhledejte „Groupdocs.Watermark“ a nainstalujte jej.
## Krok 2: Načtěte dokument PDF
### Definujte cesty dokumentu
Zadejte cestu k vašemu dokumentu PDF a výstupní adresář, kam se uloží PDF s vodoznakem.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Načtěte dokument PDF
 Použijte`PdfLoadOptions` třídy k načtení dokumentu PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Sem bude umístěn váš kód pro přidání vodoznaků
}
```
## Krok 3: Přidejte textový vodoznak na liché stránky
### Vytvořte textový vodoznak
 Vytvořit`TextWatermark` objekt s požadovaným nastavením textu a písma.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### Použít možnosti textového vodoznaku
 Použití`PdfArtifactWatermarkOptions` specifikovat, jak má být vodoznak aplikován.
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## Krok 4: Přidejte vodoznak obrázku na první stránku
Načtěte obrázek, který chcete použít jako vodoznak. Ujistěte se, že cesta obrazu je správná.
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## Krok 5: Uložte PDF s vodoznakem
Nakonec uložte PDF s vodoznakem do určeného výstupního adresáře.
```csharp
watermarker.Save(outputFileName);
```
## Závěr
Přidávání vodoznaků do souborů PDF pomocí Groupdocs je jednoduchý proces. Pomocí těchto kroků můžete efektivně přidávat textové a obrazové vodoznaky na konkrétní stránky v dokumentech PDF. To pomáhá nejen při zabezpečení vašich dokumentů, ale také při zachování profesionálního vzhledu. Vyzkoušejte to a prozkoumejte různé dostupné možnosti přizpůsobení, aby byly vaše vodoznaky jedinečné a efektivní.
## FAQ
### Co je Groupdocs.Watermark pro .NET?
Groupdocs.Watermark for .NET je knihovna, která umožňuje přidávat, vyhledávat a odstraňovat vodoznaky v různých formátech dokumentů včetně PDF, Wordu, Excelu a dalších.
### Mohu přizpůsobit vzhled vodoznaku?
Ano, můžete upravit písmo textu, velikost, barvu a polohu pro textové vodoznaky a můžete upravit velikost, neprůhlednost a polohu vodoznaků obrázku.
### Je možné přidávat vodoznaky pouze na konkrétní stránky?
Absolutně. Groupdocs.Watermark for .NET poskytuje možnosti pro přidání vodoznaků na konkrétní stránky, liché nebo sudé stránky nebo řadu stránek.
### Jak získám bezplatnou zkušební verzi Groupdocs.Watermark?
 Můžete si stáhnout bezplatnou zkušební verzi z[Web Groupdocs](https://releases.groupdocs.com/).
### Kde najdu podrobnější dokumentaci?
 Pro podrobnější informace se můžete podívat na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/).