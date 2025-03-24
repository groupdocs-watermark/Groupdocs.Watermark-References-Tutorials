---
title: أضف علامة مائية مع تأثيرات النص في مستندات Word
linktitle: أضف علامة مائية مع تأثيرات النص في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية مخصصة مع تأثيرات نصية إلى مستندات Word باستخدام GroupDocs.Watermark لـ .NET. أمان المستندات وجاذبية بصرية دون عناء.
weight: 21
url: /ar/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---

# أضف علامة مائية مع تأثيرات النص في مستندات Word

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية إضافة علامة مائية ذات تأثيرات نصية إلى مستندات Word باستخدام GroupDocs.Watermark لـ .NET. باتباع هذه الإرشادات خطوة بخطوة، ستتمكن من تحسين مستنداتك باستخدام علامات مائية مخصصة تتضمن تأثيرات نصية متنوعة.
## المتطلبات الأساسية
قبل البدء، تأكد من أن لديك ما يلي:
1.  GroupDocs.Watermark لـ .NET: قم بتنزيل المكتبة وتثبيتها من[موقع إلكتروني](https://releases.groupdocs.com/Watermark/net/).
2. مسار المستند: تعرف على مسار مستند Word الذي تريد إضافة العلامة المائية إليه.
3. دليل الإخراج: لديك دليل تريد حفظ المستند المعدل فيه.

## استيراد مساحات الأسماء
تأكد من استيراد مساحات الأسماء اللازمة للوصول إلى الفئات والأساليب المطلوبة:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
قم بتحميل مستند Word الذي تريد إضافة العلامة المائية إليه.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // رمز إضافة العلامة المائية موجود هنا
}
```
## الخطوة 2: إضافة علامة مائية مع تأثيرات النص
أنشئ علامة مائية نصية بالنص والخط المطلوبين، ثم حدد تأثيرات النص مثل تنسيق الخط.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## الخطوة 3: تخصيص خيارات العلامة المائية
حدد خيارات قسم العلامة المائية، مثل تأثيرات النص، وقم بتعيينها للعلامة المائية.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## الخطوة 4: احفظ المستند
احفظ المستند المعدل بالعلامة المائية المضافة.
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
يمكن أن تؤدي إضافة علامات مائية ذات تأثيرات نصية إلى مستندات Word إلى تعزيز جاذبيتها البصرية وحمايتها بشكل كبير. باستخدام GroupDocs.Watermark for .NET، تصبح هذه العملية مبسطة وقابلة للتخصيص، مما يسمح لك بإنشاء مستندات ذات مظهر احترافي بكفاءة.
## الأسئلة الشائعة
### هل يمكنني تخصيص خط وحجم نص العلامة المائية؟
نعم، يمكنك تحديد الخط والحجم أثناء إنشاء كائن TextWatermark.
### هل من الممكن إضافة علامات مائية متعددة إلى وثيقة واحدة؟
بالتأكيد، يدعم GroupDocs.Watermark for .NET إضافة علامات مائية متعددة بإعدادات مختلفة إلى مستند واحد.
### هل يدعم GroupDocs.Watermark تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، فهو يدعم مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل يمكنني إزالة العلامة المائية بمجرد إضافتها إلى المستند؟
نعم، توفر المكتبة طرقًا لإزالة العلامات المائية من المستندات بسهولة.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).