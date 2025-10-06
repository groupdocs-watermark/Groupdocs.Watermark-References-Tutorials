---
title: Extract All Attachments from PDF
linktitle: Extract All Attachments from PDF
second_title: GroupDocs.Watermark .NET API
description: Learn how to extract all attachments from a PDF using Groupdocs.Watermark for .NET. Follow our step-by-step guide for a seamless extraction process.
weight: 22
url: /net/pdf-watermarking-attachments/extract-all-attachments-pdf/
type: docs
---
# Extract All Attachments from PDF

## Introduction
Are you looking to extract attachments from a PDF document effortlessly? Well, you're in the right place! In this comprehensive tutorial, we'll guide you through the process of extracting all attachments from a PDF using Groupdocs.Watermark for .NET. This powerful library allows developers to manage watermarks in various document formats, but it also includes robust capabilities for extracting embedded files. Whether you're a seasoned developer or just starting, this step-by-step guide will make the process a breeze.
## Prerequisites
Before diving into the code, let's cover the basics you'll need to get started. Here's a quick checklist to ensure you're ready:
1. .NET Environment: Make sure you have a .NET development environment set up. You can use Visual Studio or any other .NET IDE of your choice.
2. Groupdocs.Watermark for .NET: Download and install the latest version of Groupdocs.Watermark for .NET from [here](https://releases.groupdocs.com/Watermark/net/).
3. Development Skills: Basic understanding of C# programming and familiarity with .NET libraries.
4. Sample PDF Document: Have a sample PDF document with attachments that you can use for testing.
## Import Namespaces
Before you start coding, you'll need to import the necessary namespaces. This helps organize your code and gives you access to the classes and methods you'll be using.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Step 1: Set Up Your Project
First things first, let's set up your project. Open your .NET development environment and create a new console application.
### Create a New Project
1. Open Visual Studio.
2. Select "Create a new project."
3. Choose "Console App (.NET Core)" or ".NET Framework" depending on your ptutorials.
4. Name your project and click "Create."
### Add Groupdocs.Watermark for .NET
1. Right-click on your project in the Solution Explorer.
2. Select "Manage NuGet Packages."
3. Search for "Groupdocs.Watermark" and install the latest version.
## Step 2: Define Your Paths
Next, you need to define the paths for your document and output directory. This is where your PDF and the extracted attachments will be stored.

In your `Program.cs` file, add the following code to define your paths:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Replace `"Your Document Path"` and `"Your Document Directory"` with the actual paths on your system.
## Step 3: Load Your PDF Document
Now, let's load your PDF document using Groupdocs.Watermark. This step involves creating load options and initializing the `Watermarker` class.
### Create Load Options
First, create an instance of `PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### Initialize Watermarker
Next, use the `Watermarker` class to load your document:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Your code will go here
}
```
## Step 4: Extract Attachments
With your document loaded, it's time to extract the attachments. You'll use the `PdfContent` class to access the attachments and then save them to your specified output directory.
### Get PDF Content
Inside the `using` block, get the PDF content:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Loop Through Attachments
Loop through each attachment in the PDF:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // Save the attached file on disk
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
This code extracts each attachment and saves it to your output directory. It also prints some basic information about each attachment to the console.
## Conclusion
And there you have it! You've successfully extracted attachments from a PDF using Groupdocs.Watermark for .NET. This tutorial walked you through setting up your project, loading your document, and extracting the attachments step-by-step. With these skills, you can now manage and manipulate PDF attachments in your .NET applications with ease.
## FAQ's
### What is Groupdocs.Watermark for .NET?
Groupdocs.Watermark for .NET is a comprehensive library for adding, removing, and managing watermarks in various document formats, including PDFs. It also offers capabilities for extracting embedded files.
### Can I extract other types of files embedded in a PDF?
Yes, Groupdocs.Watermark for .NET allows you to extract any type of file embedded in a PDF, not just attachments.
### Is there a free trial available?
Yes, you can download a free trial of Groupdocs.Watermark for .NET from [here](https://releases.groupdocs.com/).
### How can I get support if I encounter issues?
You can get support by visiting the [Groupdocs.Watermark support forum](https://forum.groupdocs.com/c/watermark/19).
### Do I need a license to use Groupdocs.Watermark for .NET?
Yes, you need a license to use the library in production. You can purchase a license [here](https://purchase.groupdocs.com/buy) or obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
