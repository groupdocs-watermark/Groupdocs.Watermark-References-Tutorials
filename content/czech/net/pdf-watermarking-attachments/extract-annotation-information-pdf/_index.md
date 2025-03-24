---
title: Extrahujte anotační informace z PDF
linktitle: Extrahujte anotační informace z PDF
second_title: GroupDocs.Watermark .NET API
description: V tomto podrobném podrobném průvodci se dozvíte, jak extrahovat informace o anotacích z dokumentů PDF pomocí GroupDocs.Watermark for .NET.
weight: 23
url: /cs/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## Úvod
Stává se vám často, že potřebujete extrahovat podrobné informace o anotacích z vašich dokumentů PDF? Ať už jste vývojář pracující na systémech pro správu dokumentů nebo obchodní profesionál zpracovávající množství PDF, efektivní extrahování a zpracování anotací může být zásadní. S GroupDocs.Watermark for .NET máte k dispozici výkonnou sadu nástrojů, díky které je tento úkol jednoduchý a efektivní.
## Předpoklady
Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:
1. Visual Studio: Ujistěte se, že máte nainstalované Visual Studio. Toto bude naše IDE pro psaní a spouštění kódu.
2.  GroupDocs.Watermark for .NET: Musíte mít knihovnu GroupDocs.Watermark for .NET. Můžeš[stáhněte si to zde](https://releases.groupdocs.com/Watermark/net/).
3. Základní znalost C#: Znalost programování v C# je nutné dodržovat spolu s příklady.
## Importovat jmenné prostory
Nejprve musíte do projektu importovat potřebné jmenné prostory. Tyto jmenné prostory obsahují třídy a metody potřebné pro práci se soubory PDF a extrahování anotací.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## Krok 1: Nastavte svůj projekt
Nejprve nastavíme náš projekt ve Visual Studiu. Vytvořte nový projekt Console App (.NET Core). Jakmile je váš projekt vytvořen, musíte přidat odkaz na knihovnu GroupDocs.Watermark for .NET.
1. Otevřete Správce balíčků NuGet.
2.  Hledat`GroupDocs.Watermark`.
3.  Nainstalujte`GroupDocs.Watermark` balík.
## Krok 2: Definujte cesty dokumentu
Dále budete muset určit cesty pro váš vstupní dokument PDF a výstupní adresář, kam budou extrahované informace uloženy. To zajistí, že vaše aplikace ví, kde má najít soubor PDF a kam uložit výsledky.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Krok 3: Načtěte dokument PDF
 Abychom mohli pracovat s dokumentem PDF, musíme jej načíst pomocí`PdfLoadOptions`. Tato třída poskytuje možnosti konfigurace procesu načítání.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Kód pro extrakci anotací bude umístěn zde
}
```
## Krok 4: Přístup k obsahu PDF
Jakmile je dokument načten, máme přístup k jeho obsahu. Konkrétně chceme získat obsah PDF, abychom mohli iterovat stránky a anotace.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Krok 5: Iterujte stránky a poznámky
S obsahem PDF v ruce můžeme procházet každou stránku a poté každou anotaci na těchto stránkách. To nám umožňuje extrahovat informace, které potřebujeme.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // Zde si vytáhněte podrobnosti anotace
    }
}
```
## Krok 6: Extrahujte podrobnosti anotace
V rámci vnořených smyček získáváme různé podrobnosti o každé anotaci. To zahrnuje typ anotace, všechny související obrázky, text a poziční data.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## Krok 7: Uložte nebo zpracujte extrahovaná data
Nakonec se rozhodněte, co chcete s extrahovanými informacemi anotace udělat. V závislosti na vašich potřebách jej můžete vytisknout na konzoli, uložit do souboru nebo dokonce uložit do databáze.
```csharp
// Příklad uložení extrahovaných dat do souboru
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## Závěr
Extrahování anotačních informací z dokumentů PDF pomocí GroupDocs.Watermark for .NET je přímočarý proces, který vám může ušetřit spoustu času a úsilí. Podle kroků popsaných v této příručce můžete tuto funkci snadno integrovat do svých projektů a automatizovat extrakci cenných anotačních dat.
 Ať už spravujete velké objemy PDF nebo prostě potřebujete extrahovat konkrétní informace, GroupDocs.Watermark for .NET poskytuje spolehlivé a efektivní řešení. Nezapomeňte se podívat na[dokumentace](https://tutorials.groupdocs.com/Watermark/net/) pro pokročilejší funkce a možnosti přizpůsobení.
## FAQ
### Co je GroupDocs.Watermark pro .NET?
GroupDocs.Watermark for .NET je komplexní knihovna, která umožňuje vývojářům přidávat, vyhledávat a odstraňovat vodoznaky z různých formátů dokumentů, včetně PDF, dokumentů Word a obrázků.
### Mohu vyzkoušet GroupDocs.Watermark zdarma?
 Ano, můžete získat a[zkušební verze zdarma](https://releases.groupdocs.com/) k otestování funkcí knihovny před nákupem.
### Jak získám podporu, pokud narazím na problémy?
 Můžete získat podporu od týmu GroupDocs, když je navštívíte[Fórum podpory](https://forum.groupdocs.com/c/watermark/19).
### Je možné získat dočasnou licenci pro testování?
 Ano, můžete požádat o a[dočasná licence](https://purchase.groupdocs.com/temporary-license/)pro testovací účely.
### Kde si mohu koupit plnou verzi GroupDocs.Watermark pro .NET?
 Plnou verzi si můžete zakoupit na[Web GroupDocs](https://purchase.groupdocs.com/buy).