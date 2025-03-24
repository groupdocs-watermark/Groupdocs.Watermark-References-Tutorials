---
title: Vízjel hozzáadása a képi műtermékekhez PDF-ben
linktitle: Vízjel hozzáadása a képi műtermékekhez PDF-ben
second_title: GroupDocs.Watermark .NET API
description: Védje meg PDF-fájljait személyre szabott vízjelekkel a GroupDocs.Watermark for .NET segítségével. Könnyen hozzáadhat szöveges vagy képi vízjeleket a PDF-dokumentumok képtermékeihez.
weight: 18
url: /hu/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük Önt a PDF-dokumentum képtermékeihez vízjel hozzáadásának folyamatán a GroupDocs.Watermark for .NET segítségével. Ha követi ezeket a lépéseket, hatékonyan védheti PDF-fájljait személyre szabott vízjelekkel.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  GroupDocs.Watermark for .NET: Töltse le és telepítse a GroupDocs.Watermark for .NET könyvtárat innen:[itt](https://releases.groupdocs.com/Watermark/net/).
2. Dokumentum elérési útja: Rendelje meg annak a PDF-dokumentumnak az elérési útját, amelyhez a vízjelet hozzá kívánja adni.
3. Kimeneti könyvtár: Hozzon létre egy könyvtárat, ahová a vízjellel ellátott dokumentum mentésre kerül.

## Névterek importálása
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1. lépés: Töltse be a dokumentumot, és inicializálja a vízjelet
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 2. lépés: Szerezzen be PDF tartalmat és adjon hozzá vízjelet
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Kép vagy szöveg vízjel inicializálása
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
				// Vízjel hozzáadása a képhez
				artifact.Image.Add(watermark);
			}
		}
	}
```
## 3. lépés: Mentse el a vízjellel ellátott dokumentumot
```csharp
	watermarker.Save(outputFileName);
}
```

## Következtetés
A GroupDocs.Watermark for .NET segítségével zökkenőmentessé válik a vízjelek hozzáadása a PDF-dokumentumok képtermékeihez. Az oktatóanyag követésével hatékonyan védheti PDF-fájljait testreszabott vízjelekkel, így biztosítva azok biztonságát és hitelességét.
## GYIK
### Hozzáadhatok képet és szöveges vízjelet is a PDF dokumentumomhoz?
Igen, a GroupDocs.Watermark for .NET támogatja a képi és szöveges vízjelek egyidejű hozzáadását.
### Van-e korlátozás a dokumentumhoz hozzáadható vízjelek számára?
Nem, több vízjelet is hozzáadhat egy dokumentumhoz korlátozás nélkül.
### Testreszabhatom a vízjel megjelenését és helyzetét?
A vízjel megjelenését, helyzetét és tulajdonságait teljes mértékben Ön szabályozhatja.
### A GroupDocs.Watermark for .NET támogatja a PDF-en kívül más dokumentumformátumokat is?
Igen, különféle dokumentumformátumokat támogat, beleértve a Word, Excel, PowerPoint és még sok mást.
### Van mód a vízjelek eltávolítására a dokumentumból?
Igen, a GroupDocs.Watermark for .NET módszereket biztosít a vízjelek eltávolítására a dokumentumokból, ha szükséges.