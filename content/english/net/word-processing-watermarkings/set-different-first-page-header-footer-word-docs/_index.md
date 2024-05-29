---
title: Set Different First Page Header/Footer in Word Docs
linktitle: Set Different First Page Header/Footer in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 36
url: /net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToWordProcessing
{
    /// <summary>
    /// This example shows how to set different headers/footers for even/odd numbered pages and for the first page of the document
    /// </summary>
    public static class WordProcessingSetDifferentFirstPageHeaderFooter
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingSetDifferentFirstPageHeaderFooter).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
                content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
