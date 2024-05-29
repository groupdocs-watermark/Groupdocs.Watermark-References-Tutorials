---
title: Remove Annotation from PDF
linktitle: Remove Annotation from PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 29
url: /net/pdf-watermarking-attachments/remove-annotation-pdf/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// This example shows how to remove a particular annotation from a PDF document.
    /// </summary>
    public static class PdfRemoveAnnotation
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfRemoveAnnotation).Name}\n");

            string documentPath = "Your Document Path";
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();

                // Remove Annotation by index
                pdfContent.Pages[0].Annotations.RemoveAt(0);

                // Remove Annotation by reference
                pdfContent.Pages[0].Annotations.Remove(pdfContent.Pages[0].Annotations[0]);

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
