---
title: Rastrovat dokument PDF
linktitle: Rastrovat dokument PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se rastrovat dokumenty PDF pomocí GroupDocs.Watermark for .NET. Vylepšete zabezpečení dokumentů a vizuální přitažlivost bez námahy.
weight: 27
url: /cs/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# Rastrovat dokument PDF

## Úvod
oblasti správy a manipulace s dokumenty je GroupDocs.Watermark for .NET výkonným nástrojem, který nabízí robustní možnosti pro přidávání, odstraňování a vyhledávání vodoznaků v různých formátech dokumentů. Ať už se jedná o ochranu vašich dokumentů pomocí upozornění na autorská práva, přidávání firemních log pro branding nebo pouhé opatřování dokumentů razítky, GroupDocs.Watermark zjednodušuje proces pomocí intuitivního rozhraní API a rozsáhlé sady funkcí.
## Předpoklady
Než se ponoříte do světa vodoznaků s GroupDocs.Watermark for .NET, ujistěte se, že máte splněny následující předpoklady:
### 1. Nainstalujte .NET Framework
Ujistěte se, že máte na vývojovém počítači nainstalováno rozhraní .NET Framework. Můžete si jej stáhnout z webu společnosti Microsoft nebo použít preferovaného správce balíčků.
#### Krok 1: Stáhněte si .NET Framework
Navštivte stránku pro stažení Microsoft .NET Framework.
#### Krok 2: Nainstalujte rozhraní .NET Framework
Při instalaci rozhraní .NET Framework do vašeho systému postupujte podle pokynů k instalaci uvedených na stránce stahování.
### 2. Získejte licenci GroupDocs.Watermark
Abyste mohli využívat všechny možnosti GroupDocs.Watermark, potřebujete platnou licenci. Můžete si buď zakoupit licenci, nebo získat dočasnou pro účely hodnocení.
#### Krok 1: Získejte licenci
Navštivte nákupní stránku GroupDocs.Watermark.
#### Krok 2: Zakupte nebo získejte dočasnou licenci
Vyberte si vhodnou možnost licencování podle svých potřeb – zakupte si licenci pro další používání nebo si získejte dočasnou licenci pro účely vyzkoušení.

## Importovat jmenné prostory
Než začnete s vodoznakem svých dokumentů, ujistěte se, že jste naimportovali potřebné jmenné prostory pro bezproblémový přístup k funkcím GroupDocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Nyní, když máte vše nastaveno, pojďme se vrhnout na rastrování dokumentu PDF pomocí GroupDocs.Watermark for .NET. Rastrování převede každou stránku dokumentu PDF do formátu rastrového obrázku, jako je PNG.
## Krok 1: Inicializujte proměnné
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Ujistěte se, že jste nahradili „Cesta k vašemu dokumentu“ a „Adresář vašeho dokumentu“ skutečnou cestou k dokumentu PDF a požadovaným výstupním adresářem.
## Krok 2: Vložte dokument a přidejte vodoznak
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Inicializujte vodoznak obrázku nebo textu
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Nejprve přidejte vodoznak libovolného typu
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rastrujte všechny stránky
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Obsah všech stránek je nahrazen rastrovými obrázky
    watermarker.Save(outputFileName);
}
```
V tomto kroku načteme dokument PDF a inicializujeme textový vodoznak se zadanými vlastnostmi, jako je text, písmo, zarovnání, úhel otočení, typ velikosti, faktor měřítka a neprůhlednost. Poté do dokumentu přidáme vodoznak. Dále načteme obsah dokumentu PDF a rastrujeme všechny stránky do formátu PNG s rozlišením 100 DPI. Nakonec upravený dokument uložíme s rastrovaným obsahem.

## Závěr
GroupDocs.Watermark for .NET nabízí komplexní řešení pro snadné přidávání vodoznaků do různých formátů dokumentů. Podle kroků uvedených v tomto kurzu můžete efektivně rastrovat dokumenty PDF a zvýšit jejich bezpečnost a vizuální přitažlivost.
## FAQ
### Je GroupDocs.Watermark kompatibilní s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs.Watermark podporuje širokou škálu formátů dokumentů, včetně Microsoft Word, Excel, PowerPoint, Visio, Outlook a mnoha dalších.
### Mohu upravit vzhled vodoznaků přidaných pomocí GroupDocs.Watermark?
Absolutně! GroupDocs.Watermark poskytuje rozsáhlé možnosti pro přizpůsobení vlastností vodoznaku, jako je text, písmo, barva, velikost, neprůhlednost, otočení a poloha.
### Nabízí GroupDocs.Watermark podporu pro dávkové zpracování?
Ano, můžete snadno zpracovat více dokumentů v dávkovém režimu pomocí GroupDocs, což ušetří čas a úsilí při vytváření vodoznaků velkých sad souborů.
### Je k dispozici zkušební verze pro GroupDocs.Watermark?
Ano, z webové stránky si můžete stáhnout bezplatnou zkušební verzi GroupDocs.Watermark, abyste před nákupem vyhodnotili její funkce.
### Jak mohu získat pomoc, pokud narazím na nějaké problémy nebo mám dotazy ohledně GroupDocs.Watermark?
Můžete navštívit fórum GroupDocs.Watermark a vyhledat podporu od komunity nebo se obrátit na tým podpory GroupDocs s žádostí o pomoc.