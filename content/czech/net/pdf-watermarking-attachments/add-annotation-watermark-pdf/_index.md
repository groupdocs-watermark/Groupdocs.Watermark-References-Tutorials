---
title: Přidat anotační vodoznak do PDF
linktitle: Přidat anotační vodoznak do PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se, jak snadno přidávat anotační vodoznaky do dokumentů PDF pomocí GroupDocs.Watermark for .NET. Snadno vylepšete značku a zabezpečení dokumentů.
type: docs
weight: 10
url: /cs/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---
## Úvod
oblasti správy dokumentů slouží přidávání vodoznaků do souborů PDF jako zásadní aspekt, zejména pro účely brandingu, zabezpečení a identifikace dokumentů. GroupDocs.Watermark for .NET je výkonná knihovna, která usnadňuje bezproblémovou integraci vodoznaků do různých formátů dokumentů, včetně PDF. V tomto tutoriálu se krok za krokem ponoříme do procesu přidávání anotačních vodoznaků do dokumentů PDF s využitím funkcí, které poskytuje GroupDocs.Watermark pro .NET.
## Předpoklady
Než budeme pokračovat s výukovým programem, ujistěte se, že máte splněny následující předpoklady:
1.  Knihovna GroupDocs.Watermark for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Watermark for .NET z[webová stránka](https://releases.groupdocs.com/Watermark/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí, jako je Visual Studio nebo jakékoli jiné .NET IDE.
3. Základní porozumění C#: Doporučuje se znalost základů programovacího jazyka C#.

## Import nezbytných jmenných prostorů
Chcete-li začít, importujte požadované jmenné prostory do svého projektu C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Načtěte dokument PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Definujte možnosti vodoznaku
```csharp
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## Krok 3: Přidejte textový vodoznak
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## Krok 4: Přidejte vodoznak obrázku
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## Krok 5: Uložte dokument s vodoznakem
```csharp
	watermarker.Save(outputFileName);
}
```

## Závěr
Na závěr, GroupDocs.Watermark for .NET nabízí komplexní řešení pro programové přidávání anotačních vodoznaků do dokumentů PDF. Dodržením nastíněných kroků mohou uživatelé bez problémů integrovat textové a obrazové vodoznaky do svých souborů PDF, a tím zlepšit značku a zabezpečení dokumentů.
## FAQ
### Je GroupDocs.Watermark kompatibilní s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs.Watermark podporuje širokou škálu formátů dokumentů, včetně Wordu, Excelu, PowerPointu a dalších.
### Mohu upravit vzhled vodoznaku?
Absolutně! GroupDocs.Watermark poskytuje rozsáhlé možnosti přizpůsobení textových i obrazových vodoznaků a umožňuje uživatelům upravit velikost, polohu, neprůhlednost a další parametry.
### Je GroupDocs.Watermark vhodný pro dávkové zpracování dokumentů?
Rozhodně! GroupDocs.Watermark nabízí efektivní možnosti dávkového zpracování, které uživatelům umožňuje aplikovat vodoznaky na více dokumentů současně.
### Podporuje GroupDocs.Watermark vývoj .NET Core?
Ano, GroupDocs.Watermark podporuje .NET Core a umožňuje vývojářům integrovat funkce vodoznaku do aplikací pro různé platformy.
### Je pro uživatele GroupDocs.Watermark k dispozici technická podpora?
Ano, GroupDocs poskytuje komplexní technickou podporu prostřednictvím svých vyhrazených fór a kanálů zákaznických služeb.