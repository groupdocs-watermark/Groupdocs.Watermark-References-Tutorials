---
title: Přidat vodoznak do obrázků v PDF
linktitle: Přidat vodoznak do obrázků v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do obrázků v dokumentech PDF pomocí GroupDocs.Watermark for .NET s naším podrobným, podrobným návodem. Zabezpečte své PDF snadno.
weight: 19
url: /cs/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Úvod
Přidání vodoznaků do obrázků v dokumentu PDF může být zásadní pro ochranu vašeho duševního vlastnictví nebo zajištění pravosti vašich dokumentů. Pomocí GroupDocs.Watermark for .NET lze tento úkol provést efektivně a snadno. Tento tutoriál vás provede každým krokem procesu, od nastavení prostředí přes přidání vodoznaků až po uložení konečného dokumentu. Pojďme se ponořit!
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1. Visual Studio: Nainstalujte Visual Studio, integrované vývojové prostředí (IDE) pro aplikace .NET.
2.  GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark for .NET z[stránka vydání](https://releases.groupdocs.com/Watermark/net/).
3. Dokument PDF: Připravte si dokument PDF s obrázky k otestování funkce vodoznaku.
4.  Dočasná licence: Získejte a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) pokud produkt hodnotíte.
## Importovat jmenné prostory
Nejprve se ujistěte, že máte do projektu importovány potřebné jmenné prostory. To bude zahrnovat základní jmenné prostory potřebné pro práci s dokumenty PDF a vodoznaky.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Nastavte cestu k dokumentu a výstupní adresář
Chcete-li začít, definujte cesty pro vstupní dokument a výstupní adresář, kam bude dokument s vodoznakem uložen. Tento krok je zásadní pro zajištění toho, aby váš program věděl, kde najít zdrojový dokument a kam uložit zpracovaný soubor.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Načtěte dokument PDF
 Dále budete muset načíst dokument PDF pomocí`PdfLoadOptions`. Tato třída vám umožňuje určit volby pro načítání PDF, jako je ochrana heslem, pokud je to nutné.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Sem přijde váš kód pro vodoznak
}
```
## Krok 3: Vytvořte vodoznak
Nyní inicializujte vodoznak. V tomto příkladu vytváříme textový vodoznak, který zní "Chráněný obrázek". Přizpůsobte si písmo, zarovnání, otočení a měřítko podle svých potřeb.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Krok 4: Přístup k obsahu PDF
Načtěte obsah dokumentu PDF. Konkrétně potřebujeme přístup k obrázkům v PDF. Zde se zaměřujeme na první stránku, ale můžete ji podle potřeby rozšířit na další stránky.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Získejte všechny obrázky z první stránky
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Krok 5: Použijte vodoznak na obrázky
Projděte každý obrázek na první stránce a použijte vodoznak. Tím zajistíte, že všechny obrázky na zadané stránce budou mít vodoznak.
```csharp
// Přidejte vodoznak do všech nalezených obrázků
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Krok 6: Uložte dokument s vodoznakem
Nakonec uložte vodoznak PDF do určeného výstupního adresáře. Tento krok dokončí proces zápisem změn do nového souboru.
```csharp
watermarker.Save(outputFileName);
```
## Závěr
A tady to máte! Přidání vodoznaku do obrázků v rámci PDF pomocí GroupDocs Watermark for .NET je jednoduchý proces, který může výrazně zvýšit bezpečnost a autentičnost vašich dokumentů. Pomocí těchto kroků můžete zajistit ochranu vašeho duševního vlastnictví a zabezpečení vašich dokumentů.
## FAQ
### Co je GroupDocs.Watermark pro .NET?
GroupDocs.Watermark for .NET je komplexní knihovna, která umožňuje vývojářům přidávat, vyhledávat a odstraňovat vodoznaky v různých formátech dokumentů, včetně PDF.
### Mohu přidat textové i obrázkové vodoznaky pomocí GroupDocs.Watermark?
Ano, GroupDocs.Watermark podporuje textové i obrazové vodoznaky a poskytuje flexibilitu pro různé typy potřeb vodoznaků.
### Je možné vodoznakem více stránek v PDF?
Absolutně! Můžete procházet každou stránku v PDF a aplikovat vodoznaky na obrázky na každé stránce.
### Potřebuji licenci k používání GroupDocs.Watermark pro .NET?
 Ano, je vyžadována licence. Můžete získat a[dočasná licence](https://purchase.groupdocs.com/temporary-license/) pro účely hodnocení.
### Kde najdu další dokumentaci ke GroupDocs.Watermark for .NET?
 Komplexní dokumentaci naleznete na[Stránka dokumentace GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).