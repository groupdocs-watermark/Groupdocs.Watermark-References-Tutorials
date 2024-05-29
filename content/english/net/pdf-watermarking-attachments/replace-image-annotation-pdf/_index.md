---
title: Replace Image for Specific Annotation in PDF
linktitle: Replace Image for Specific Annotation in PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 37
url: /net/pdf-watermarking-attachments/replace-image-annotation-pdf/
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
    /// This example shows how to replace the image of a particular annotation.
    /// </summary>
    public static class PdfReplaceImageForParticularAnnotation
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfReplaceImageForParticularAnnotation).Name}\n");

            string documentPath = Constants.InDocumentPdf;
            string outputDirectory = Constants.GetOutputDirectoryPath();
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();

                // Replace image
                foreach (PdfAnnotation annotation in pdfContent.Pages[0].Annotations)
                {
                    if (annotation.Image != null)
                    {
                        annotation.Image = new PdfWatermarkableImage(File.ReadAllBytes(Constants.TestPng));
                    }
                }

                // Save document
                watermarker.Save(outputFileName);
            }
        }
    }
}

```
