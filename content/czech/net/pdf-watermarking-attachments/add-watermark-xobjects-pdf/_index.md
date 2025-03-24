---
title: Přidejte vodoznak do XObjects v PDF
linktitle: Přidejte vodoznak do XObjects v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do XObjects v PDF pomocí Groupdocs.Watermark for .NET. Pro snadnou implementaci postupujte podle našeho podrobného průvodce.
weight: 20
url: /cs/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Úvod
Vodoznak PDF je zásadním krokem k zajištění ochrany vašich dokumentů před neoprávněným použitím. S Groupdocs.Watermark for .NET nebylo přidávání vodoznaků do XObjects v rámci vašich PDF nikdy jednodušší. V tomto tutoriálu vás provedeme procesem krok za krokem a zajistíme, že můžete s jistotou použít vodoznaky na své dokumenty PDF. Začněme!
## Předpoklady
Než se ponoříte do výukového programu, ujistěte se, že máte vše, co potřebujete, abyste bez problémů sledovali:
-  Groupdocs.Watermark for .NET: Stáhněte si a nainstalujte nejnovější verzi z[tady](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: Ujistěte se, že máte na vývojovém počítači nainstalované rozhraní .NET Framework.
- Vývojové prostředí: Použijte Visual Studio nebo jakékoli jiné IDE, které podporuje vývoj .NET.
-  Dočasná licence: Získejte a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) pokud produkt hodnotíte.
Jakmile splníte tyto předpoklady, jste připraveni začít vytvářet vodoznaky PDF.
## Importovat jmenné prostory
Nejprve budete muset do projektu importovat potřebné jmenné prostory. Otevřete svůj projekt C# a pomocí direktiv přidejte následující:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Nastavte cesty k dokumentu
První krok zahrnuje nastavení cest pro váš dokument. Definujte cestu, kde se vaše PDF nachází a kam chcete uložit PDF s vodoznakem.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Nahradit`"Your Document Path"` a`"Your Document Directory"` se skutečnými cestami na vašem počítači.
## Krok 2: Inicializujte možnosti načítání PDF
Dále budete muset inicializovat možnosti načítání PDF. To je zásadní pro správné načtení obsahu PDF.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Krok 3: Načtěte dokument PDF
Pomocí voleb načtení načtěte dokument PDF pomocí`Watermarker` třída.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Krok 4: Vytvořte vodoznak
Nyní musíte vytvořit vodoznak, který bude přidán do PDF. Pro tento tutoriál vytvoříme textový vodoznak.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Krok 5: Přidejte vodoznak do XObjects
Chcete-li vodoznak použít, projděte každou stránku a každý objekt XObject v PDF.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Přidejte do obrázku vodoznak
            xObject.Image.Add(watermark);
        }
    }
}
```
## Krok 6: Uložte PDF s vodoznakem
Nakonec uložte vodoznak PDF do určeného výstupního souboru.
```csharp
    watermarker.Save(outputFileName);
}
```
A tady to máte! Váš PDF nyní obsahuje vodoznaky na všech svých objektech XObjects.
## Závěr
 Přidávání vodoznaků do dokumentů PDF pomocí Groupdocs Watermark for .NET je jednoduchý proces, který poskytuje další vrstvu zabezpečení. Dodržováním kroků uvedených v tomto kurzu můžete zajistit, aby byly vaše dokumenty chráněny před neoprávněným použitím. Pamatujte si, že vždy můžete odkazovat na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) pro podrobnější informace a pokročilé funkce.
## FAQ
### Mohu použít obrázek jako vodoznak místo textu?
Ano, Groupdocs.Watermark for .NET podporuje textové i obrázkové vodoznaky.
### Jak mohu otestovat Groupdocs.Watermark bez jeho zakoupení?
 Můžete použít a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) hodnotit produkt.
### Je možné upravit vzhled vodoznaku?
Absolutně! Můžete si přizpůsobit písmo, velikost, úhel otočení a další.
### Podporuje Groupdocs.Watermark jiné formáty dokumentů?
Ano, podporuje různé formáty, včetně Wordu, Excelu a PowerPointu.
### Kde mohu získat podporu, pokud narazím na problémy?
 Můžete získat podporu od[Groupdocs fórum](https://forum.groupdocs.com/c/watermark/19).