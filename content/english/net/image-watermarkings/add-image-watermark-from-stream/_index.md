---
title: Add Image Watermark from Stream
linktitle: Add Image Watermark from Stream
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 12
url: /net/image-watermarkings/add-image-watermark-from-stream/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddingImageWatermarks
{
    /// <summary>
    /// This example shows how to an image watermark from stream.
    /// </summary>
    public static class AddImageWatermarkUsingStream
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(AddImageWatermarkUsingStream).Name}\n");

            string documentPath = Constants.WatermarkJpg;
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            using (Stream watermarkStream = File.OpenRead(documentPath))
            {
                using (Watermarker watermarker = new Watermarker("Your Document Path"))
                {
                    // Use stream containing an image as constructor parameter
                    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
                    {
                        // Add watermark to the document
                        watermarker.Add(watermark);

                        watermarker.Save(outputFileName);
                    }
                }
            }
        }
    }
}

```
