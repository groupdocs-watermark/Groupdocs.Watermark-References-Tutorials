---
title: Load Document from Local Disk
linktitle: Load Document from Local Disk
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 10
url: /net/document-loadings/load-document-from-local-disk/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.LoadingDocuments
{
    public static class LoadFromLocalDisk
    {
        /// <summary>
        /// This example demontrates how to create a watermarker for a local filesystem document.
        /// </summary>
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(LoadFromLocalDisk).Name}\n");

            string documentPath = Constants.InDocumentDocx;
            string outputFileName = Path.Combine(Constants.GetOutputDirectoryPath(), Path.GetFileName(documentPath));

            var loadOptions = new WordProcessingLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                // use watermarker methods to manage watermarks
                TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));

                watermarker.Add(watermark);
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
