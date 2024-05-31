---
title: إضافة علامة مائية نصية
linktitle: إضافة علامة مائية نصية
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية نصية إلى مستنداتك باستخدام Groupdocs للعلامة المائية لـ .NET من خلال هذا الدليل المفصل خطوة بخطوة.
type: docs
weight: 11
url: /ar/net/watermarking-basics/add-text-watermark/
---
## مقدمة
تعد GroupDocs.Watermark for .NET مكتبة قوية تسمح للمطورين بإضافة العلامات المائية والبحث فيها وإزالتها من تنسيقات المستندات المختلفة في تطبيقات .NET. في هذا البرنامج التعليمي، سنركز على إضافة علامة مائية نصية إلى مستند باستخدام GroupDocs.Watermark.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1. المعرفة الأساسية بلغة البرمجة C#.
2. تم تثبيت Visual Studio على نظامك.
3.  تم تثبيت GroupDocs.Watermark لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/Watermark/net/).

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## الخطوة 1: تحديد مسار المستند ودليل الإخراج
حدد المسار إلى مستند الإدخال الخاص بك ودليل الإخراج حيث سيتم حفظ المستند الذي يحمل علامة مائية.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"` بالمسار المطلق أو النسبي لمستند الإدخال الخاص بك، على سبيل المثال:`@"C:\Docs\document.pdf"`. حدد أيضًا الدليل الذي تريد حفظ المستند الذي يحمل علامة مائية فيه.
## الخطوة 2: إضافة علامة مائية نصية
 إنشاء مثيل`Watermarker` فئة مع مسار وثيقة الإدخال. ثم قم بإنشاء`TextWatermark` كائن مع إعدادات النص والخط المطلوبة.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة علامة مائية نصية إلى مستند باستخدام GroupDocs.Watermark لـ .NET. بفضل واجهة برمجة التطبيقات البديهية، يمكن للمطورين التعامل بسهولة مع العلامات المائية بتنسيقات المستندات المختلفة.
## الأسئلة الشائعة
### هل GroupDocs.Watermark لـ .NET متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Watermark مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وMicrosoft Word وExcel وPowerPoint وغيرها الكثير.
### هل يمكنني تخصيص مظهر العلامة المائية النصية؟
نعم، يمكنك تخصيص خصائص مختلفة مثل الخط واللون والمحاذاة والتعتيم للعلامة المائية النصية.
### هل توفر GroupDocs.Watermark الدعم لإزالة العلامات المائية من المستندات؟
نعم، يوفر GroupDocs.Watermark وظيفة للبحث عن العلامات المائية وإزالتها من المستندات.
### هل يمكنني تجربة GroupDocs.Watermark لـ .NET قبل الشراء؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم الفني لـ GroupDocs.Watermark؟
 يمكنك الحصول على الدعم الفني من خلال زيارة[GroupDocs.منتدى العلامة المائية](https://forum.groupdocs.com/c/watermark/19).