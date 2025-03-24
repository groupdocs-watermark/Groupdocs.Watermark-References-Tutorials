---
title: تعيين رأس/تذييل مختلف للصفحة الأولى في مستندات Word
linktitle: تعيين رأس/تذييل مختلف للصفحة الأولى في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية تعيين رؤوس وتذييلات مختلفة على الصفحة الأولى من مستندات Word باستخدام GroupDocs.Watermark لـ .NET.
weight: 36
url: /ar/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---

# تعيين رأس/تذييل مختلف للصفحة الأولى في مستندات Word

## مقدمة
في مجال إدارة المستندات ومعالجتها، تظهر GroupDocs.Watermark for .NET كأداة قوية توفر تكاملًا سلسًا ووظائف قوية لوضع العلامات المائية على المستندات. أحد المتطلبات الشائعة في معالجة المستندات هو تعيين رؤوس وتذييلات مختلفة على الصفحة الأولى من مستندات Word. سيوضح هذا البرنامج التعليمي عملية تحقيق هذه المهمة باستخدام GroupDocs.Watermark لـ .NET، مع تقسيم كل خطوة إلى أجزاء يسهل فهمها.
## المتطلبات الأساسية
قبل الغوص في التنفيذ، تأكد من استيفاء المتطلبات الأساسية التالية:
1.  تثبيت GroupDocs.Watermark لـ .NET: قم بتنزيل وتثبيت GroupDocs.Watermark لـ .NET من[رابط التحميل](https://releases.groupdocs.com/Watermark/net/).
2. إعداد المستند: جهز مستند Word الذي يتطلب إعداد رؤوس وتذييلات مختلفة على صفحته الأولى.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية المطلوبة لاستخدام GroupDocs.Watermark لوظائف .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
في هذه الخطوة، نحدد المسار إلى المستند الذي يحتاج إلى المعالجة ونحدد اسم ملف الإخراج والدليل. بالإضافة إلى ذلك، نقوم بتهيئة أ`Watermarker` الكائن بمسار المستند وخيارات التحميل.
## الخطوة 2: الوصول إلى محتوى المستند
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 هنا، نقوم باسترداد محتوى مستند Word باستخدام ملف`GetContent<T>()` طريقة`Watermarker` كائن، وتحديد نوع المحتوى كما`WordProcessingContent`.
## الخطوة 3: تكوين إعداد الصفحة
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
في هذه الخطوة، نقوم بتكوين خيارات إعداد الصفحة لتمكين الرؤوس والتذييلات المختلفة للصفحة الأولى (`DifferentFirstPageHeaderFooter`) وكذلك للصفحات الفردية والزوجية (`OddAndEvenPagesHeaderFooter`).
## الخطوة 4: حفظ التغييرات
```csharp
watermarker.Save(outputFileName);
```
 وأخيرًا، نقوم بحفظ التعديلات التي تم إجراؤها على المستند عن طريق استدعاء`Save()` طريقة`Watermarker` الكائن، وتمرير اسم ملف الإخراج.

## خاتمة
يوفر GroupDocs.Watermark for .NET حلاً مباشرًا لتعيين رؤوس وتذييلات مختلفة على الصفحة الأولى من مستندات Word. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكن للمستخدمين التعامل بسهولة مع محتوى المستند وفقًا لمتطلباتهم.
## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Watermark لـ .NET التعامل مع تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، يدعم GroupDocs.Watermark for .NET نطاقًا واسعًا من تنسيقات المستندات بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
نعم، يمكن للمستخدمين الاستفادة من النسخة التجريبية المجانية من GroupDocs.Watermark لـ .NET من[صفحة الإصدارات](https://releases.groupdocs.com/).
### هل تقدم GroupDocs.Watermark for .NET الدعم الفني؟
 نعم، يتوفر الدعم الفني لـ GroupDocs للعلامة المائية لـ .NET من خلال[منتدى الدعم](https://forum.groupdocs.com/c/watermark/19).
### هل يمكنني شراء ترخيص مؤقت للاستخدام قصير المدى؟
 نعم، يمكن الحصول على تراخيص مؤقتة لـ GroupDocs للعلامة المائية لـ .NET من[صفحة شراء الترخيص المؤقت](https://purchase.groupdocs.com/temporary-license/).
### أين يمكنني العثور على وثائق شاملة لـ GroupDocs.Watermark لـ .NET؟
 تتوفر الوثائق التفصيلية لـ GroupDocs.Watermark لـ .NET على الموقع[الصفحه المرجعيه](https://tutorials.groupdocs.com/Watermark/net/).