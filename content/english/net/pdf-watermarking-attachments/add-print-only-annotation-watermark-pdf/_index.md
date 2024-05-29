---
title: Add Print Only Annotation Watermark to PDF
linktitle: Add Print Only Annotation Watermark to PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 13
url: /net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// This example shows how to add print only annotation watermark to the document.
    /// </summary>
    public static class PdfAddPrintOnlyAnnotationWatermark
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfAddPrintOnlyAnnotationWatermark).Name}\n");

            string documentPath = Constants.InDocumentPdf;
            string outputDirectory = Constants.GetOutputDirectoryPath();
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
                bool isPrintOnly = true;

                // Annotation will be printed, but not displayed in pdf viewing application
                PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
                options.PageIndex = 0;
                options.PrintOnly = isPrintOnly;
                watermarker.Add(textWatermark, options);

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
