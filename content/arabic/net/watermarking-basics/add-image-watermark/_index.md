---
title: إضافة علامة مائية للصورة
linktitle: إضافة علامة مائية للصورة
second_title: GroupDocs.Watermark .NET API
description: قم بإضافة علامات مائية للصور إلى مستنداتك بسهولة باستخدام GroupDocs.Watermark لـ .NET. حماية الملكية الفكرية الخاصة بك بكل سهولة.
weight: 10
url: /ar/net/watermarking-basics/add-image-watermark/
type: docs
---
# إضافة علامة مائية للصورة

## مقدمة
في هذا البرنامج التعليمي، سنتعمق في عملية إضافة علامة مائية مصورة إلى مستنداتك باستخدام GroupDocs.Watermark لـ .NET. تعد وثائق العلامات المائية ضرورية لحماية الملكية الفكرية والعلامات التجارية. باستخدام GroupDocs.Watermark for .NET، يمكنك دمج العلامات المائية بسلاسة في تنسيقات المستندات المختلفة مثل Word وExcel وPowerPoint وPDF وغيرها الكثير.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Watermark لمكتبة .NET: قم بتنزيل وتثبيت GroupDocs.Watermark لمكتبة .NET من[موقع إلكتروني](https://releases.groupdocs.com/Watermark/net/).
2. المستند: اجعل المستند جاهزًا الذي تريد إضافة العلامة المائية إليه.
3. صورة للعلامة المائية: قم بإعداد ملف الصورة الذي تريد استخدامه كعلامة مائية.

## استيراد مساحات الأسماء
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## الخطوة 1: تهيئة مسار المستند ودليل الإخراج
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"`بالمسار المطلق أو النسبي للمستند الخاص بك و`"Your Document Directory"` مع الدليل الذي تريد حفظ المستند الذي يحمل علامة مائية.
## الخطوة 2: افتح دفق المستندات وقم بتهيئة العلامة المائية
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // ستتم عملية وضع العلامات المائية هنا
    }
}
```
 افتح دفق المستند باستخدام`FileStream` وتهيئة`Watermarker` هدف.
## الخطوة 3: إضافة علامة مائية للصورة
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 يخترع`ImageWatermark` الكائن بالمسار إلى ملف الصورة الذي تريد استخدامه كعلامة مائية. اضبط المحاذاة الأفقية والرأسية للعلامة المائية.
## الخطوة 4: حفظ المستند الذي يحمل علامة مائية
```csharp
watermarker.Save(outputFileName);
```
احفظ المستند الذي يحمل علامة مائية في دليل الإخراج المحدد باسم الملف المطلوب.

## خاتمة
في الختام، يوفر GroupDocs.Watermark for .NET حلاً شاملاً لإضافة علامات مائية إلى تنسيقات المستندات المختلفة دون عناء. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك إضافة علامات مائية مصورة إلى مستنداتك بكفاءة وحماية ملكيتك الفكرية.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية نصية باستخدام GroupDocs.Watermark لـ .NET؟
نعم، تدعم GroupDocs.Watermark for .NET إضافة كل من العلامات المائية المصورة والنصية إلى المستندات.
### هل GroupDocs.Watermark لـ .NET متوافق مع تنسيقات المستندات المختلفة؟
بالتأكيد، تدعم GroupDocs.Watermark for .NET نطاقًا واسعًا من تنسيقات المستندات بما في ذلك Word وExcel وPowerPoint وPDF والمزيد.
### هل يوفر GroupDocs.Watermark for .NET خيارات تخصيص للعلامات المائية؟
نعم، يمكنك تخصيص جوانب مختلفة من العلامة المائية مثل الموضع والحجم والعتامة والتدوير.
### هل يمكنني إزالة العلامات المائية من المستندات باستخدام GroupDocs.Watermark لـ .NET؟
نعم، يوفر GroupDocs.Watermark for .NET وظيفة لاكتشاف العلامات المائية وإزالتها من المستندات.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من الموقع لاستكشاف الميزات قبل الشراء[هنا](https://releases.groupdocs.com/).