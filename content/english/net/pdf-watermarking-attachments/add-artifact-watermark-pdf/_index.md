---
title: Add Artifact Watermark to PDF
linktitle: Add Artifact Watermark to PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 11
url: /net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// Thies example shows how to add an artifact watermark to a document.
    /// </summary>
    public static class PdfAddArtifactWatermark
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfAddArtifactWatermark).Name}\n");

            string documentPath = Constants.InDocumentPdf;
            string outputDirectory = Constants.GetOutputDirectoryPath();
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();

                // Add text watermark
                TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
                textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
                watermarker.Add(textWatermark, options);

                // Add image watermark
                using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
                {
                    watermarker.Add(imageWatermark, options);
                }

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
