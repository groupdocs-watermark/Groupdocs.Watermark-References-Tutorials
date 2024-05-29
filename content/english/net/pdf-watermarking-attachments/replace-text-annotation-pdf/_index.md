---
title: Replace Text for Specific Annotation in PDF
linktitle: Replace Text for Specific Annotation in PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 40
url: /net/pdf-watermarking-attachments/replace-text-annotation-pdf/
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
    /// This example shows how to edit and replace the text of the particular annotations.
    /// </summary>
    public static class PdfReplaceTextForParticularAnnotation
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfReplaceTextForParticularAnnotation).Name}\n");

            string documentPath = "Your Document Path";
            string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                foreach (PdfAnnotation annotation in pdfContent.Pages[0].Annotations)
                {
                    // Replace text 
                    if (annotation.Text.Contains("Test"))
                    {
                        annotation.Text = "Passed";
                    }
                }

                // Save document
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
