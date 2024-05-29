---
title: Link All Headers/Footers in Section in Word Docs
linktitle: Link All Headers/Footers in Section in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 25
url: /net/word-processing-watermarkings/link-all-headers-footers-section-word-docs/
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
    /// This example shows how to link all the headers/footers in a particular section.
    /// </summary>
    public static class WordProcessingLinkAllHeaderFooterInSection
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingLinkAllHeaderFooterInSection).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                // Link footer for even numbered pages to corresponding footer in previous section
                content.Sections[1].HeadersFooters[1].IsLinkedToPrevious = true;

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
