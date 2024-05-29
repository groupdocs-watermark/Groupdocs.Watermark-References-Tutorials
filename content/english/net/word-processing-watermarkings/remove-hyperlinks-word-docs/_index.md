---
title: Remove Hyperlinks in Word Docs
linktitle: Remove Hyperlinks in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 29
url: /net/word-processing-watermarkings/remove-hyperlinks-word-docs/
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
    /// This example shows how to remove/replace hyperlink associated with a particular shape inside a Word document.
    /// </summary>
    public static class WordProcessingRemoveHyperlinks
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingRemoveHyperlinks).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                // Replace hyperlink
                content.Sections[0].Shapes[0].Hyperlink = "https://www.groupdocs.com/";

                // Remove hyperlink
                content.Sections[0].Shapes[1].Hyperlink = null;

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
