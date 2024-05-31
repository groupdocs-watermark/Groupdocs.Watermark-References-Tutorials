---
title: Přidat vodoznak do všech příloh v PDF
linktitle: Přidat vodoznak do všech příloh v PDF
second_title: GroupDocs.Watermark .NET API
description: Naučte se přidávat vodoznaky do příloh PDF pomocí GroupDocs.Watermark for .NET. Zabezpečte své dokumenty snadno pomocí vlastních vodoznaků.
type: docs
weight: 16
url: /cs/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Úvod
Přidání vodoznaků do příloh PDF může být zásadním krokem ve správě dokumentů, zejména při zajišťování zabezpečení nebo brandingu. GroupDocs.Watermark for .NET nabízí komplexní řešení pro bezproblémové vkládání vodoznaků do souborů PDF. V tomto tutoriálu vás provedeme procesem přidání vodoznaku do všech příloh v dokumentu PDF pomocí GroupDocs.Watermark for .NET.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Watermark for .NET: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte GroupDocs.Watermark for .NET z webu[webová stránka](https://releases.groupdocs.com/Watermark/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí pomocí sady Visual Studio nebo jiného IDE kompatibilního s .NET.
3. Dokument PDF: Připravte dokument PDF, do kterého chcete přidat vodoznak, spolu s přílohami, které chcete vodoznakem přidat.

## Import jmenných prostorů
Než se ponoříte do kódu, ujistěte se, že jste importovali potřebné jmenné prostory pro přístup k funkcím GroupDocs.Watermark for .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Krok 1: Definujte cestu k dokumentu a výstupní adresář
Nejprve definujte cestu k vašemu vstupnímu PDF dokumentu a adresář, kam bude vodoznak uložen:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 2: Inicializujte možnosti načtení a vodoznak
Dále inicializujte možnosti načtení pro dokument PDF a vytvořte textový vodoznak:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Krok 3: Vložte dokument a přílohy
Načtěte dokument PDF a projděte si jeho přílohy:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Krok 4: Zkontrolujte podporu příloh
Zkontrolujte, zda je přiložený soubor podporován GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Krok 5: Přidejte vodoznak do příloh
Vložte přiložený dokument a přidejte vodoznak:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Krok 6: Uložte změny
Nakonec uložte změny do dokumentu PDF s vodoznakem:
```csharp
    watermarker.Save(outputFileName);
}
```

## Závěr
V tomto tutoriálu jsme prozkoumali, jak přidat vodoznaky do všech příloh v dokumentu PDF pomocí GroupDocs.Watermark for .NET. Dodržováním tohoto podrobného průvodce můžete vodoznaky bez problémů integrovat do svých souborů PDF a zajistit tak zabezpečení dokumentů a branding.
## FAQ
### Mohu upravit vzhled vodoznaku?
Ano, můžete přizpůsobit různé aspekty, jako je text, písmo, velikost, barva a umístění vodoznaku podle vašich požadavků.
### Podporuje GroupDocs.Watermark jiné formáty dokumentů kromě PDF?
Ano, GroupDocs.Watermark podporuje širokou škálu formátů dokumentů včetně Microsoft Word, Excel, PowerPoint, Visio, Outlook a Obrázky.
### Je k dispozici zkušební verze pro GroupDocs.Watermark?
Ano, funkce GroupDocs.Watermark můžete prozkoumat stažením bezplatné zkušební verze z webu.
### Mohu přidat více vodoznaků do jednoho dokumentu?
Rozhodně, GroupDocs.Watermark umožňuje přidat více vodoznaků, včetně textu, obrázku a anotace současně, aby se zvýšila bezpečnost dokumentů a branding.
### Je pro uživatele GroupDocs.Watermark k dispozici technická podpora?
Ano, GroupDocs poskytuje komplexní technickou podporu prostřednictvím fór a vyhrazených kanálů podpory, které uživatelům pomáhají s jakýmikoli dotazy nebo problémy, se kterými se mohou setkat.