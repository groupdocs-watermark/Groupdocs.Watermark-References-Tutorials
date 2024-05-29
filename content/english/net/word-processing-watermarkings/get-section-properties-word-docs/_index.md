---
title: Get Section Properties in Word Docs
linktitle: Get Section Properties in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 23
url: /net/word-processing-watermarkings/get-section-properties-word-docs/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToWordProcessing
{
    /// <summary>
    /// This example shows how to get some page properties for a section.
    /// </summary>
    public static class WordProcessingGetSectionProperties
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingGetSectionProperties).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                Console.WriteLine(content.Sections[0].PageSetup.Width);
                Console.WriteLine(content.Sections[0].PageSetup.Height);
                Console.WriteLine(content.Sections[0].PageSetup.TopMargin);
                Console.WriteLine(content.Sections[0].PageSetup.RightMargin);
                Console.WriteLine(content.Sections[0].PageSetup.BottomMargin);
                Console.WriteLine(content.Sections[0].PageSetup.LeftMargin);
            }
        }
    }
}

```
