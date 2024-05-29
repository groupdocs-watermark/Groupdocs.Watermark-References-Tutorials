---
title: Add Locked Watermark to All Pages in Word Docs
linktitle: Add Locked Watermark to All Pages in Word Docs
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 11
url: /net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToWordProcessing
{
    /// <summary>
    /// This example shows how to lock watermark in all pages.
    /// </summary>
    public static class WordProcessingAddLockedWatermarkToAllPages
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(WordProcessingAddLockedWatermarkToAllPages).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
                watermark.ForegroundColor = Color.Red;

                WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
                options.IsLocked = true;
                options.LockType = WordProcessingLockType.AllowOnlyFormFields;

                // To protect with password
                //options.Password = "7654321";

                watermarker.Add(watermark, options);

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
