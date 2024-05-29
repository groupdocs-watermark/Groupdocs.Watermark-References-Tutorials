---
title: Get Document Info from Stream
linktitle: Get Document Info from Stream
second_title: GroupDocs.Watermark .NET API
description: 
type: docs
weight: 12
url: /net/document-manipulation/get-document-info-stream/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;

namespace GroupDocs.Watermark.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to get document information from the file stream.
    /// </summary>
    public static class GetDocumentInfoForTheFileFromStream
    {
        public static void Run()
        {
            Console.WriteLine($"[Example Basic Usage] # {typeof(GetDocumentInfoForTheFileFromStream).Name}\n");

            // "Your Document Path" is an absolute or relative path to your document. Ex: @"C:\Docs\source.docx"
            using (FileStream stream = File.OpenRead("Your Document Path"))
            {
                using (Watermarker watermarker = new Watermarker(stream))
                {
                    IDocumentInfo info = watermarker.GetDocumentInfo();
                    Console.WriteLine("File type: {0}", info.FileType);
                    Console.WriteLine("Number of pages: {0}", info.PageCount);
                    Console.WriteLine("Document size: {0} bytes", info.Size);
                }
            }
        }
    }
}

```
