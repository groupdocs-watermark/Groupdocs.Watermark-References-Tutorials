---
title: إضافة علامة مائية إلى الصور التوضيحية في PDF
linktitle: إضافة علامة مائية إلى الصور التوضيحية في PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية حماية مستندات PDF الخاصة بك عن طريق إضافة علامات مائية إلى صور التعليقات التوضيحية باستخدام Groupdocs.Watermark for .NET.
weight: 17
url: /ar/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
type: docs
---
# إضافة علامة مائية إلى الصور التوضيحية في PDF

## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية إضافة علامات مائية إلى صور التعليقات التوضيحية في مستندات PDF باستخدام Groupdocs.Watermark for .NET. تعد العلامة المائية أمرًا ضروريًا لحماية مستنداتك من الاستخدام أو التوزيع غير المصرح به. باتباع هذا الدليل خطوة بخطوة، ستتعلم كيفية تطبيق العلامات المائية النصية على صور التعليقات التوضيحية في ملفات PDF بشكل فعال.
## المتطلبات الأساسية
قبل المتابعة، تأكد من أن لديك ما يلي:
1. الفهم الأساسي للغة البرمجة C#.
2. تم تثبيت Groupdocs.Watermark لمكتبة .NET.
3. الوصول إلى بيئة التطوير مثل Visual Studio.
4. مستند PDF يحتوي على صور توضيحية للعلامة المائية.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى كود C# الخاص بك:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## الخطوة 2: احصل على محتوى PDF وقم بتهيئة العلامة المائية
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // تهيئة الصورة أو العلامة المائية النصية
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## الخطوة 3: التكرار عبر صفحات PDF وصور التعليقات التوضيحية
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // إضافة علامة مائية على الصورة
                annotation.Image.Add(watermark);
            }
        }
    }
```
## الخطوة 4: احفظ المستند بالعلامة المائية
```csharp
    watermarker.Save(outputFileName);
}
```
بعد تنفيذ هذه الخطوات، ستتم إضافة العلامة المائية المحددة إلى صور التعليقات التوضيحية في مستند PDF الخاص بك.

## خاتمة
تعد إضافة علامات مائية إلى صور التعليقات التوضيحية في ملفات PDF أمرًا ضروريًا لحماية سلامة مستنداتك وضمان عدم إساءة استخدامها. مع Groupdocs.Watermark for .NET، تصبح هذه العملية بسيطة وفعالة، مما يسمح لك بحماية ملفات PDF الخاصة بك بشكل فعال.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية متعددة لنفس مستند PDF؟
نعم، يمكنك إضافة علامات مائية متعددة إلى مستند PDF نفسه باستخدام Groupdocs.Watermark لـ .NET.
### هل يدعم Groupdocs.Watermark تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، تدعم العلامة المائية Groupdocs تنسيقات المستندات المختلفة، بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل من الممكن تخصيص مظهر العلامة المائية؟
بالتأكيد، يمكنك تخصيص النص والخط واللون والحجم وموضع العلامة المائية وفقًا لتفضيلاتك.
### هل يمكنني إزالة العلامات المائية من مستندات PDF باستخدام Groupdocs.Watermark؟
نعم، يوفر Groupdocs.Watermark وظيفة لإزالة العلامات المائية من مستندات PDF دون عناء.
### هل هناك أي نسخة تجريبية مجانية متاحة لـ Groupdocs.Watermark لـ .NET؟
نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من Groupdocs.Watermark لـ .NET من موقع الويب.