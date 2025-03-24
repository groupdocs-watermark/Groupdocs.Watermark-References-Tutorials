---
title: أضف علامة مائية مع إعدادات الشكل في مستندات Word
linktitle: أضف علامة مائية مع إعدادات الشكل في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية باستخدام إعدادات الشكل إلى مستندات Word باستخدام GroupDocs لـ .NET. حماية المستندات الخاصة بك بشكل فعال.
weight: 20
url: /ar/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---

# أضف علامة مائية مع إعدادات الشكل في مستندات Word

## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية إضافة علامة مائية مع إعدادات الشكل إلى مستندات Word باستخدام GroupDocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  تم تثبيت GroupDocs.Watermark لـ .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. المعرفة الأساسية ببرمجة C#.
3. فهم معالجة مستندات Word.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية للوصول إلى الفئات والأساليب المطلوبة.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
قم بتحميل مستند Word حيث تريد إضافة العلامة المائية.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // رمز إضافة العلامة المائية موجود هنا
}
```
## الخطوة 2: إضافة علامة مائية
 إنشاء مثيل أ`TextWatermark` الكائن وحدد النص الذي تريد استخدامه كعلامة مائية.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## الخطوة 3: تخصيص إعدادات العلامة المائية
قم بتعيين إعدادات مختلفة للعلامة المائية، مثل المحاذاة وزاوية التدوير واللون والعتامة.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## الخطوة 4: تحديد خيارات قسم العلامة المائية
حدد خيارات قسم العلامة المائية، مثل اسم الشكل والنص البديل.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## الخطوة 5: إضافة علامة مائية إلى المستند
أضف العلامة المائية إلى المستند بالخيارات المحددة.
```csharp
watermarker.Add(watermark, options);
```
## الخطوة 6: احفظ المستند
احفظ المستند بالعلامة المائية المضافة.
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
تعد إضافة علامات مائية مع إعدادات الشكل إلى مستندات Word باستخدام GroupDocs للعلامة المائية لـ .NET عملية واضحة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك حماية مستنداتك بشكل فعال باستخدام العلامات المائية المخصصة.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية متعددة إلى نفس المستند؟
نعم، يمكنك إضافة علامات مائية متعددة بإعدادات مختلفة لنفس المستند.
### هل يدعم GroupDocs.Watermark تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، يدعم GroupDocs.Watermark تنسيقات المستندات المختلفة، بما في ذلك Excel وPowerPoint وPDF والمزيد.
### هل يمكنني تخصيص مظهر العلامة المائية بشكل أكبر؟
بالتأكيد، يمكنك ضبط المعلمات المختلفة مثل حجم الخط والنمط واللون والموضع لتناسب احتياجاتك.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم لـ GroupDocs.Watermark؟
 يمكنك العثور على الدعم وطرح الأسئلة في منتدى GroupDocs[هنا](https://forum.groupdocs.com/c/watermark/19).