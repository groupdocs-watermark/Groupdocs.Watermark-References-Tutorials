---
title: Load Password Protected Document
linktitle: Load Password Protected Document
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 13
url: /net/document-loadings/load-password-protected-document/
---

## Complete Source Code
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;

namespace GroupDocs.Watermark.Examples.CSharp.AdvancedUsage.LoadingDocuments
{
    /// <summary>
    /// This example demontrates how to load an encrypted document using the password.
    /// </summary>
    public static class LoadPasswordProtectedDocument
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Advanced Usage] # {typeof(LoadPasswordProtectedDocument).Name}\n");

            string documentPath = Constants.InProtectedDocumentDocx;
            string outputFileName = Path.Combine(Constants.GetOutputDirectoryPath(), Path.GetFileName(documentPath));

            LoadOptions loadOptions = new LoadOptions();
            loadOptions.Password = "P@$$w0rd";
            using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
            {
                // use watermarker methods to manage watermarks in the document
                TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));

                watermarker.Add(watermark);

                watermarker.Save(outputFileName);
            }
        }
    }
}

```
