---
title: Add Image Watermark to All Headers in Word Docs
linktitle: Add Image Watermark to All Headers in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 10
url: /net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToWordProcessing
{
    /// <summary>
    /// This example shows how to add watermark with linking headers and footers.
    /// </summary>
    public static class WordProcessingAddImageWatermarkToAllHeaders
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingAddImageWatermarkToAllHeaders).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                using (ImageWatermark watermark = new ImageWatermark(Constants.LargePng))
                {
                    // Add watermark to all headers of the first section
                    WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
                    options.SectionIndex = 0;
                    watermarker.Add(watermark, options);
                }

                // Link all other headers&footers to corresponding headers&footers of the first section
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
                for (int i = 1; i < content.Sections.Count; i++)
                {
                    content.Sections[i].HeadersFooters.LinkToPrevious(true);
                }

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
