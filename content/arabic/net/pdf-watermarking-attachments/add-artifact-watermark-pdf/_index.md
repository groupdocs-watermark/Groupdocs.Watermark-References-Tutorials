---
title: إضافة علامة مائية قطعة أثرية إلى PDF
linktitle: إضافة علامة مائية قطعة أثرية إلى PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية أثرية إلى ملفات PDF بسهولة باستخدام Groupdocs.Watermark for .NET. حماية المستندات الخاصة بك بكل سهولة.
type: docs
weight: 11
url: /ar/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## مقدمة
تعد إضافة علامات مائية إلى ملفات PDF جانبًا مهمًا في إدارة المستندات، خاصة عندما يتعلق الأمر بحماية الملكية الفكرية أو مستندات العلامة التجارية. يوفر Groupdocs.Watermark for .NET حلاً قويًا لإضافة علامات مائية إلى ملفات PDF دون عناء. في هذا البرنامج التعليمي، سنتعرف على عملية إضافة علامة مائية فنية إلى ملفات PDF خطوة بخطوة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  Groupdocs.Watermark لـ .NET: قم بتنزيل وتثبيت Groupdocs.Watermark لـ .NET من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير .NET.
3. مستند PDF: قم بإعداد مستند PDF الذي تريد إضافة العلامة المائية إليه.
4. دليل الإخراج: قم بإنشاء دليل لحفظ ملف PDF الذي يحمل علامة مائية.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using GroupDocs.Watermark.Common;
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
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## الخطوة 3: إضافة علامة مائية نصية
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## الخطوة 4: إضافة علامة مائية للصورة
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## الخطوة 5: احفظ ملف PDF الذي يحمل علامة مائية
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة علامات مائية صناعية إلى ملفات PDF باستخدام Groupdocs.Watermark لـ .NET. باتباع هذه الخطوات، يمكنك دمج وظيفة العلامات المائية بسلاسة في تطبيقات .NET الخاصة بك، مما يضمن أمان وسلامة مستنداتك.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر العلامة المائية النصية؟
نعم، يمكنك تخصيص جوانب مختلفة مثل الخط والحجم واللون ومحاذاة العلامة المائية النصية وفقًا لتفضيلاتك.
### هل يدعم Groupdocs.Watermark إضافة علامات مائية إلى تنسيقات المستندات الأخرى؟
نعم، تدعم Groupdocs.Watermark إضافة علامات مائية إلى مجموعة واسعة من تنسيقات المستندات بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل هناك إصدار تجريبي متاح لـ Groupdocs.Watermark لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لأية مشكلات أو استفسارات تتعلق بـ Groupdocs.Watermark؟
 يمكنك الحصول على الدعم من منتدى مجتمع Groupdocs[هنا](https://forum.groupdocs.com/c/watermark/19).
### هل يمكنني استخدام Groupdocs.Watermark لأغراض تجارية؟
نعم، يمكنك شراء ترخيص للاستخدام التجاري من[هنا](https://purchase.groupdocs.com/buy).