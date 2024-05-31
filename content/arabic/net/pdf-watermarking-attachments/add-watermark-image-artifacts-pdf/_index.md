---
title: إضافة علامة مائية إلى عناصر الصورة في PDF
linktitle: إضافة علامة مائية إلى عناصر الصورة في PDF
second_title: GroupDocs.Watermark .NET API
description: قم بحماية ملفات PDF الخاصة بك باستخدام علامات مائية مخصصة باستخدام GroupDocs.Watermark لـ .NET. يمكنك بسهولة إضافة علامات مائية نصية أو صورية إلى عناصر الصور في مستندات PDF.
type: docs
weight: 18
url: /ar/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة علامة مائية إلى عناصر الصور في مستند PDF باستخدام GroupDocs.Watermark لـ .NET. باتباع هذه الخطوات، يمكنك حماية ملفات PDF الخاصة بك بكفاءة باستخدام علامات مائية مخصصة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Watermark لـ .NET: قم بتنزيل وتثبيت GroupDocs.Watermark لمكتبة .NET من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. مسار المستند: حدد المسار إلى مستند PDF حيث تريد إضافة العلامة المائية.
3. دليل الإخراج: قم بإنشاء دليل حيث سيتم حفظ المستند الذي يحمل علامة مائية.

## استيراد مساحات الأسماء
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند وتهيئة العلامة المائية
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## الخطوة 2: احصل على محتوى PDF وأضف علامة مائية
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// تهيئة الصورة أو العلامة المائية النصية
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// إضافة علامة مائية على الصورة
				artifact.Image.Add(watermark);
			}
		}
	}
```
## الخطوة 3: احفظ المستند الذي يحمل علامة مائية
```csharp
	watermarker.Save(outputFileName);
}
```

## خاتمة
باستخدام GroupDocs.Watermark for .NET، تصبح إضافة العلامات المائية إلى عناصر الصور في مستندات PDF عملية سلسة. باتباع هذا البرنامج التعليمي، يمكنك حماية ملفات PDF الخاصة بك بكفاءة باستخدام علامات مائية مخصصة، مما يضمن أمانها وأصالتها.
## الأسئلة الشائعة
### هل يمكنني إضافة العلامات المائية المصورة والنصية إلى مستند PDF الخاص بي؟
نعم، تدعم GroupDocs.Watermark for .NET إضافة العلامات المائية للصورة والنص في وقت واحد.
### هل هناك أي قيود على عدد العلامات المائية التي يمكنني إضافتها إلى المستند؟
لا، يمكنك إضافة علامات مائية متعددة إلى المستند دون أي قيود.
### هل يمكنني تخصيص مظهر وموضع العلامة المائية؟
بالتأكيد، لديك السيطرة الكاملة على مظهر العلامة المائية وموضعها وخصائصها.
### هل يدعم GroupDocs.Watermark for .NET تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، فهو يدعم تنسيقات المستندات المختلفة بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل هناك طريقة لإزالة العلامات المائية من المستند؟
نعم، يوفر GroupDocs.Watermark for .NET طرقًا لإزالة العلامات المائية من المستندات إذا لزم الأمر.