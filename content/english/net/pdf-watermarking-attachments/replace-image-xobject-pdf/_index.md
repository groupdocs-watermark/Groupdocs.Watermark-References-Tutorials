---
title: Replace Image for Specific XObject in PDF
linktitle: Replace Image for Specific XObject in PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 39
url: /net/pdf-watermarking-attachments/replace-image-xobject-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// This example shows how to replace the image of a particular XObject.
    /// </summary>
    public static class PdfReplaceImageForParticularXObject
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfReplaceImageForParticularXObject).Name}\n");

            string documentPath = "Your Document Path";
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();

                // Replace image
                foreach (PdfXObject xObject in pdfContent.Pages[0].XObjects)
                {
                    if (xObject.Image != null)
                    {
                        xObject.Image = new PdfWatermarkableImage(File.ReadAllBytes(Constants.TestPng));
                    }
                }

                // Save document
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
