---
title: Přidat vodoznak do obrazových artefaktů v PDF
linktitle: Přidat vodoznak do obrazových artefaktů v PDF
second_title: GroupDocs.Watermark .NET API
description: Chraňte své soubory PDF pomocí personalizovaných vodoznaků pomocí GroupDocs.Watermark for .NET. Snadno přidávejte textové nebo obrazové vodoznaky k obrazovým artefaktům v dokumentech PDF.
weight: 18
url: /cs/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# Přidat vodoznak do obrazových artefaktů v PDF

## Úvod
tomto tutoriálu vás provedeme procesem přidávání vodoznaku do obrazových artefaktů v dokumentu PDF pomocí GroupDocs.Watermark for .NET. Pomocí těchto kroků můžete účinně chránit své soubory PDF pomocí personalizovaných vodoznaků.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Watermark for .NET: Stáhněte si a nainstalujte knihovnu GroupDocs.Watermark for .NET z[tady](https://releases.groupdocs.com/Watermark/net/).
2. Cesta k dokumentu: Zadejte cestu k dokumentu PDF, kam chcete přidat vodoznak.
3. Výstupní adresář: Vytvořte adresář, do kterého se uloží dokument s vodoznakem.

## Importovat jmenné prostory
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Vložte dokument a inicializujte vodoznak
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Krok 2: Získejte obsah PDF a přidejte vodoznak
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Inicializujte vodoznak obrázku nebo textu
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Přidejte do obrázku vodoznak
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Krok 3: Uložte dokument s vodoznakem
```csharp
	watermarker.Save(outputFileName);
}
```

## Závěr
S GroupDocs.Watermark for .NET se přidávání vodoznaků do obrazových artefaktů v dokumentech PDF stává bezproblémovým procesem. Podle tohoto návodu můžete efektivně chránit své soubory PDF pomocí přizpůsobených vodoznaků, což zajistí jejich bezpečnost a autentičnost.
## FAQ
### Mohu do svého dokumentu PDF přidat obrazový i textový vodoznak?
Ano, GroupDocs.Watermark for .NET podporuje přidávání obrazových i textových vodoznaků současně.
### Existuje nějaké omezení počtu vodoznaků, které mohu přidat do dokumentu?
Ne, do dokumentu můžete přidat více vodoznaků bez jakýchkoli omezení.
### Mohu upravit vzhled a umístění vodoznaku?
Absolutně máte plnou kontrolu nad vzhledem, pozicí a vlastnostmi vodoznaku.
### Podporuje GroupDocs.Watermark for .NET jiné formáty dokumentů kromě PDF?
Ano, podporuje různé formáty dokumentů včetně Wordu, Excelu, PowerPointu a dalších.
### Existuje způsob, jak odstranit vodoznaky z dokumentu?
Ano, GroupDocs.Watermark for .NET poskytuje metody pro odstranění vodoznaků z dokumentů v případě potřeby.