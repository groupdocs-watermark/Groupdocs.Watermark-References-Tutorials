---
title: إضافة علامة مائية للصورة المتجانبة
linktitle: إضافة علامة مائية للصورة المتجانبة
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية للصور المتجانبة إلى مستنداتك باستخدام GroupDocs.Watermark لـ .NET. سهلة وفعالة وقابلة للتخصيص.
weight: 10
url: /ar/net/image-watermarkings/add-tiled-image-watermark/
---

# إضافة علامة مائية للصورة المتجانبة

## مقدمة
GroupDocs.Watermark for .NET عبارة عن واجهة برمجة تطبيقات قوية تسمح للمطورين بإضافة العلامات المائية وإزالتها والبحث فيها في تنسيقات المستندات المختلفة برمجيًا. في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة علامة مائية مقسمة إلى صور إلى مستنداتك باستخدام GroupDocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
- المعرفة الأساسية بلغة البرمجة C#.
- تم تثبيت Visual Studio على نظامك.
- تمت إضافة GroupDocs.Watermark لمكتبة .NET إلى مشروعك. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/Watermark/net/).

## استيراد مساحات الأسماء
تأكد من استيراد مساحات الأسماء الضرورية في بداية ملف C# الخاص بك:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## الخطوة 1: قم بتعيين مسار المستند ودليل الإخراج
حدد مسار مستند الإدخال الخاص بك والدليل الذي تريد حفظ مستند الإخراج فيه:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"` بالمسار المطلق أو النسبي لمستند الإدخال الخاص بك.
## الخطوة 2: تهيئة كائن العلامة المائية
قم بإنشاء كائن علامة مائية باستخدام مسار مستند الإدخال:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // أضف علامة مائية هنا
}
```
## الخطوة 3: إضافة علامة مائية للصورة المتجانبة
قم بإنشاء كائن ImageWatermark بالمسار إلى ملف الصورة الذي تريد استخدامه كعلامة مائية:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // تكوين خيارات البلاط
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // أضف علامة مائية إلى المستند
    watermarker.Add(watermark);
    // احفظ المستند المعدل
    watermarker.Save(outputFileName);
}
```
 يستبدل`"Path to Your Image"` مع المسار الفعلي لملف صورة العلامة المائية الخاصة بك.

## خاتمة
باتباع هذه الخطوات، يمكنك بسهولة إضافة علامة مائية مقسمة إلى مستنداتك باستخدام GroupDocs.Watermark for .NET. قم بتجربة خيارات وتكوينات مختلفة لتحقيق النتيجة المرجوة.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟
نعم، يمكنك إضافة علامات مائية متعددة من أنواع مختلفة إلى مستند باستخدام GroupDocs.Watermark لـ .NET.
### هل يدعم GroupDocs.Watermark جميع تنسيقات المستندات؟
يدعم GroupDocs.Watermark مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF وWord وExcel وPowerPoint وغيرها الكثير.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### هل يمكنني تخصيص مظهر العلامة المائية؟
نعم، يمكنك تخصيص جوانب مختلفة من العلامة المائية، مثل الموضع والحجم والتدوير والشفافية وما إلى ذلك.
### هل تقدم GroupDocs.Watermark الدعم الفني؟
 نعم، يمكنك الحصول على الدعم الفني من منتدى GroupDocs.Watermark[هنا](https://forum.groupdocs.com/c/watermark/19).