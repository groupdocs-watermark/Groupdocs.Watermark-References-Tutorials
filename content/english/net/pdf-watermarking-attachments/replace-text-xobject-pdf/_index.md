---
title: Replace Text for Specific XObject in PDF
linktitle: Replace Text for Specific XObject in PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 44
url: /net/pdf-watermarking-attachments/replace-text-xobject-pdf/
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
    /// This example shows how to edit and replace the text of the particular XObject.
    /// </summary>
    public static class PdfReplaceTextForParticularXObject
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfReplaceTextForParticularXObject).Name}\n");

            string documentPath = Constants.InDocumentPdf;
            string outputFileName = Path.Combine(Constants.GetOutputDirectoryPath(), Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                foreach (PdfXObject xObject in pdfContent.Pages[0].XObjects)
                {
                    // Replace text
                    if (xObject.Text.Contains("Test"))
                    {
                        xObject.Text = "Passed";
                    }
                }

                // Save document
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
