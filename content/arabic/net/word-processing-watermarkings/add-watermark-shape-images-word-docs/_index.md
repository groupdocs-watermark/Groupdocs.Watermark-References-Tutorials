---
title: أضف علامة مائية لتشكيل الصور في مستندات Word
linktitle: أضف علامة مائية لتشكيل الصور في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية لتشكيل الصور في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. قم بتعزيز أمان المستندات باستخدام هذا البرنامج التعليمي.
weight: 17
url: /ar/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# أضف علامة مائية لتشكيل الصور في مستندات Word

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية إضافة علامة مائية لتشكيل الصور داخل مستندات Word باستخدام GroupDocs.Watermark لـ .NET. تعد العلامة المائية جانبًا مهمًا لحماية المستندات، خاصة عند التعامل مع معلومات حساسة أو سرية. من خلال إضافة علامات مائية لتشكيل الصور، يمكنك ضمان سلامة وأمان مستنداتك.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Watermark لـ .NET: قم بتنزيل وتثبيت مكتبة GroupDocs.Watermark من[صفحة التحميل](https://releases.groupdocs.com/Watermark/net/).
2. المستند: قم بإعداد مستند Word حيث تريد إضافة العلامة المائية.
3. بيئة التطوير: قم بإعداد بيئة تطوير .NET المفضلة لديك.
## استيراد مساحات الأسماء
قبل كتابة الكود، تأكد من استيراد مساحات الأسماء الضرورية:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
أولاً، حدد المسار إلى المستند الخاص بك وحدد اسم ملف الإخراج:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## الخطوة 2: تهيئة العلامة المائية
 إنشاء مثيل أ`Watermarker` الكائن من خلال توفير مسار المستند وخيارات التحميل الاختيارية:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // أضف منطق العلامة المائية هنا
}
```
## الخطوة 3: إنشاء علامة مائية نصية
حدد العلامة المائية النصية بالخصائص المطلوبة مثل النص والخط والمحاذاة والتدوير والتحجيم وما إلى ذلك:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## الخطوة 4: تطبيق العلامة المائية على شكل الصور
قم بالتكرار خلال أقسام المستند وأشكاله لتحديد صور الأشكال وإضافة العلامة المائية:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## الخطوة 5: احفظ المستند
احفظ المستند مع العلامة المائية المضافة إلى ملف الإخراج المحدد:
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة علامات مائية لتشكيل الصور في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. باتباع الدليل الموضح خطوة بخطوة والاستفادة من الميزات القوية لـ GroupDocs.Watermark، يمكنك تعزيز أمان وحماية مستنداتك بشكل فعال.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر نص العلامة المائية؟
نعم، يمكنك ضبط خصائص مختلفة مثل الخط والحجم واللون وزاوية التدوير والمحاذاة لتخصيص العلامة المائية وفقًا لتفضيلاتك.
### هل يدعم GroupDocs.Watermark تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، يوفر GroupDocs.Watermark الدعم لمجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل من الممكن إضافة علامات مائية متعددة إلى وثيقة واحدة؟
بالتأكيد، يمكنك إضافة علامات مائية متعددة بمحتوى وأنماط ومواضع مختلفة داخل نفس المستند.
### هل يمكنني إزالة العلامات المائية من المستندات باستخدام GroupDocs.Watermark؟
نعم، يوفر GroupDocs.Watermark ميزات لاكتشاف العلامات المائية وإزالتها من المستندات بكفاءة.
### هل توفر GroupDocs.Watermark توافقًا عبر الأنظمة الأساسية؟
نعم، GroupDocs.Watermark متوافق مع .NET Framework و.NET Core و.NET Standard، مما يضمن التكامل السلس عبر الأنظمة الأساسية المختلفة.