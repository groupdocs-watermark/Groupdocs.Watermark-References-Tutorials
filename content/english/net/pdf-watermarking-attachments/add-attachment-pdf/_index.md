---
title: Add Attachment to PDF
linktitle: Add Attachment to PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 12
url: /net/pdf-watermarking-attachments/add-attachment-pdf/
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
    /// This example shows how to add attachments to the PDF document.
    /// </summary>
    public static class PdfAddAttachment
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfAddAttachment).Name}\n");

            string documentPath = "Your Document Path";
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();

                // Add the attachment
                pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");

                // Save changes
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
