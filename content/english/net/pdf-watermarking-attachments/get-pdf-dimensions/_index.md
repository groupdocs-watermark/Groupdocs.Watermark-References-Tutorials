---
title: Get PDF Dimensions
linktitle: Get PDF Dimensions
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 26
url: /net/pdf-watermarking-attachments/get-pdf-dimensions/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// This example shows how to get the dimensions of the page in a PDF document.
    /// </summary>
    public static class PdfGetDimensions
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfGetDimensions).Name}\n");

            string documentPath = Constants.InDocumentPdf;
            string outputDirectory = Constants.GetOutputDirectoryPath();
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();

                Console.WriteLine(pdfContent.Pages[0].Width);
                Console.WriteLine(pdfContent.Pages[0].Height);
            }
        }
    }
}

```
