---
title: Protect Document in Word Docs
linktitle: Protect Document in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 28
url: /net/word-processing-watermarkings/protect-document-word-docs/
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
    /// This example shows how to protect a Word document with the password.
    /// </summary>
    public static class WordProcessingProtectDocument
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingProtectDocument).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                content.Protect(WordProcessingProtectionType.ReadOnly, "7654321");

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
