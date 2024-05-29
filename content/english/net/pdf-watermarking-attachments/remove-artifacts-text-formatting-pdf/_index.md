---
title: Remove Artifacts with Specific Text Formatting in PDF
linktitle: Remove Artifacts with Specific Text Formatting in PDF
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 32
url: /net/pdf-watermarking-attachments/remove-artifacts-text-formatting-pdf/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.AddingWatermarks.AddWatermarksToPdf
{
    /// <summary>
    /// This example shows how to find and remove all artifacts containing text with a particular formatting from a PDF document.
    /// </summary>
    public static class PdfRemoveArtifactsWithParticularTextFormatting
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(PdfRemoveArtifactsWithParticularTextFormatting).Name}\n");

            string documentPath = "Your Document Path";
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));

            var loadOptions = new PdfLoadOptions();
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                PdfContent pdfContent = watermarker.GetContent<PdfContent>();
                foreach (PdfPage page in pdfContent.Pages)
                {
                    for (int i = page.Artifacts.Count - 1; i >= 0; i--)
                    {
                        foreach (FormattedTextFragment fragment in page.Artifacts[i].FormattedTextFragments)
                        {
                            if (fragment.Font.Size > 42)
                            {
                                page.Artifacts.RemoveAt(i);
                                break;
                            }
                        }
                    }
                }

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
