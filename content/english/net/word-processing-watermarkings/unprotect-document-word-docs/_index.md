---
title: Unprotect Document in Word Docs
linktitle: Unprotect Document in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 38
url: /net/word-processing-watermarkings/unprotect-document-word-docs/
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
    /// This example shows how to unprotect a Word document regardless of password.
    /// </summary>
    public static class WordProcessingUnProtectDocument
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingUnProtectDocument).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();

                content.Unprotect();

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
