---
title: Link Header/Footer in Section in Word Docs
linktitle: Link Header/Footer in Section in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 26
url: /net/word-processing-watermarkings/link-header-footer-section-word-docs/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToWordProcessing
{
    /// <summary>
    /// This example shows how to link the header/footer.
    /// </summary>
    public static class WordProcessingLinkHeaderFooterInSection
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingLinkHeaderFooterInSection).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                // Link footer for even numbered pages to corresponding footer in previous section
                content.Sections[1].HeadersFooters[OfficeHeaderFooterType.FooterEven].IsLinkedToPrevious = true;

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
