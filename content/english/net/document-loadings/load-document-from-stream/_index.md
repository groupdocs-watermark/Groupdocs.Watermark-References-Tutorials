---
title: Load Document from Stream
linktitle: Load Document from Stream
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 11
url: /net/document-loadings/load-document-from-stream/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.LoadingDocuments
{
    /// <summary>
    /// This example democtrates how to create a watermarker for a document stream:
    /// </summary>
    public static class LoadFromStream
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(LoadFromLocalDisk).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            using (Stream document = File.OpenRead(documentPath))
            using (Watermarker watermarker = new Watermarker(document))
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
