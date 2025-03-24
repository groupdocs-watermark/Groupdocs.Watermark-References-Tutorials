---
title: إضافة علامة مائية توضيحية إلى ملف PDF
linktitle: إضافة علامة مائية توضيحية إلى ملف PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية توضيحية إلى مستندات PDF بسهولة باستخدام GroupDocs.Watermark لـ .NET. تعزيز العلامة التجارية للمستندات وأمانها بسهولة.
weight: 10
url: /ar/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---

# إضافة علامة مائية توضيحية إلى ملف PDF

## مقدمة
في مجال إدارة المستندات، تعد إضافة العلامات المائية إلى ملفات PDF بمثابة جانب حاسم، خاصة لأغراض العلامات التجارية والأمن وتحديد المستندات. GroupDocs.Watermark for .NET هي مكتبة قوية تسهل التكامل السلس للعلامات المائية في تنسيقات المستندات المختلفة، بما في ذلك ملفات PDF. في هذا البرنامج التعليمي، سوف نتعمق في عملية إضافة علامات مائية توضيحية إلى مستندات PDF خطوة بخطوة، وذلك باستخدام الوظائف التي توفرها GroupDocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن نبدأ البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1.  GroupDocs.Watermark لمكتبة .NET: قم بتنزيل وتثبيت GroupDocs.Watermark لمكتبة .NET من[موقع إلكتروني](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة، مثل Visual Studio أو أي برنامج .NET IDE آخر.
3. الفهم الأساسي لـ C#: يوصى بالإلمام بأساسيات لغة البرمجة C#.

## استيراد مساحات الأسماء الضرورية
للبدء، قم باستيراد مساحات الأسماء المطلوبة إلى مشروع C# الخاص بك:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل مستند PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## الخطوة 2: تحديد خيارات العلامة المائية
```csharp
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## الخطوة 3: إضافة علامة مائية نصية
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## الخطوة 4: إضافة علامة مائية للصورة
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## الخطوة 5: احفظ المستند بالعلامة المائية
```csharp
	watermarker.Save(outputFileName);
}
```

## خاتمة
في الختام، يقدم GroupDocs.Watermark for .NET حلاً شاملاً لإضافة علامات مائية توضيحية إلى مستندات PDF برمجيًا. من خلال اتباع الخطوات الموضحة، يمكن للمستخدمين دمج العلامات المائية النصية والصورية بسلاسة في ملفات PDF الخاصة بهم، وبالتالي تعزيز العلامة التجارية للمستندات وأمانها.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، تدعم GroupDocs.Watermark مجموعة واسعة من تنسيقات المستندات، بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص مظهر العلامة المائية؟
قطعاً! يوفر GroupDocs.Watermark خيارات تخصيص واسعة النطاق لكل من العلامات المائية النصية والصورية، مما يسمح للمستخدمين بضبط الحجم والموضع والعتامة والمعلمات الأخرى.
### هل GroupDocs.Watermark مناسب لمعالجة المستندات دفعة واحدة؟
بالتأكيد! يوفر GroupDocs.Watermark إمكانات معالجة دفعية فعالة، مما يتيح للمستخدمين تطبيق العلامات المائية على مستندات متعددة في وقت واحد.
### هل يدعم GroupDocs.Watermark تطوير .NET Core؟
نعم، يدعم GroupDocs.Watermark .NET Core، مما يسمح للمطورين بدمج وظائف العلامات المائية في التطبيقات عبر الأنظمة الأساسية.
### هل يتوفر الدعم الفني لمستخدمي GroupDocs.Watermark؟
نعم، توفر GroupDocs دعمًا فنيًا شاملاً من خلال المنتديات المخصصة لها وقنوات خدمة العملاء.