---
title: أضف علامة مائية مقفلة إلى جميع الصفحات في مستندات Word
linktitle: أضف علامة مائية مقفلة إلى جميع الصفحات في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: قم بتأمين مستنداتك عن طريق إضافة علامات مائية مقفلة باستخدام Groupdocs.Watermark لـ .NET. اتبع دليلنا خطوة بخطوة لسهولة التنفيذ.
weight: 11
url: /ar/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# أضف علامة مائية مقفلة إلى جميع الصفحات في مستندات Word

## مقدمة
تعد إضافة علامات مائية إلى مستنداتك خطوة حيوية في تأمين المحتوى الخاص بك ووضع علامة تجارية عليه. سواء كنت تمنع الاستخدام غير المصرح به أو ببساطة تضيف لمسة احترافية، يمكن للعلامات المائية أن تخدم أغراضًا متعددة. في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة علامة مائية مقفلة إلى كافة صفحات مستند Word باستخدام Groupdocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن نتعمق في الدليل التفصيلي، دعنا نتأكد من أن لديك كل ما تحتاجه:
1. Groupdocs.Watermark لـ .NET: قم بتنزيل أحدث إصدار من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
3. بيئة التطوير: بيئة تطوير مثل Visual Studio.
4.  الترخيص: يمكنك اختيار أ[تجربة مجانية](https://releases.groupdocs.com/) أو شراء أ[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/).
## استيراد مساحات الأسماء
أول الأشياء أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية في مشروعك. تعتبر هذه العناصر ضرورية للوصول إلى الفئات والأساليب التي توفرها Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بإعداد مشروعك

افتح بيئة التطوير الخاصة بك وقم بإنشاء مشروع .NET جديد. يمكن أن يكون هذا تطبيقًا لوحدة التحكم أو أي نوع آخر يناسب احتياجاتك.

تحتاج إلى إضافة حزمة Groupdocs.Watermark إلى مشروعك. يمكن القيام بذلك عبر NuGet Package Manager. قم بتشغيل الأمر التالي في وحدة تحكم NuGet Package Manager:
```sh
Install-Package GroupDocs.Watermark
```
## الخطوة 2: قم بتحميل مستند Word
### تحديد مسار الوثيقة
حدد المسار إلى مستند Word الخاص بك. سيكون هذا هو المستند الذي تريد إضافة العلامة المائية إليه.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### ضبط خيارات التحميل
 إنشاء مثيل ل`WordProcessingLoadOptions` لتحميل مستند Word الخاص بك بخيارات محددة.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## الخطوة 3: إنشاء العلامة المائية
### تهيئة العلامة المائية
 باستخدام`Watermarker`فئة، قم بتحميل المستند بخيارات التحميل المحددة.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // ستكون الخطوات الإضافية داخل هذه الكتلة باستخدام
}
```
### تحديد خصائص العلامة المائية
 إنشاء`TextWatermark` على سبيل المثال مع النص والخط واللون المطلوب.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## الخطوة 4: تطبيق العلامة المائية على جميع الصفحات
### ضبط خيارات العلامة المائية
 يُعرِّف`WordProcessingWatermarkPagesOptions` وتعيين`IsLocked` الخاصية صحيحة لقفل العلامة المائية. وهذا يضمن عدم إمكانية إزالة العلامة المائية بسهولة.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### اختياري: إضافة حماية بكلمة المرور
إذا كنت تريد إضافة طبقة إضافية من الأمان، فيمكنك تعيين كلمة مرور للعلامة المائية.
```csharp
// للحماية بكلمة مرور
// options.Password = "7654321";
```
### أضف العلامة المائية
 استخدم ال`Add` طريقة`Watermarker` class لإضافة العلامة المائية إلى المستند بالخيارات المحددة.
```csharp
watermarker.Add(watermark, options);
```
## الخطوة 5: احفظ المستند
وأخيرًا، احفظ المستند المعدل في ملف الإخراج المحدد.
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
باتباع هذه الخطوات، يمكنك بسهولة إضافة علامة مائية مقفلة إلى كافة صفحات مستندات Word الخاصة بك باستخدام Groupdocs.Watermark for .NET. وهذا لا يساعد فقط في حماية مستنداتك من الاستخدام غير المصرح به ولكنه يضيف أيضًا لمسة احترافية إلى المحتوى الخاص بك. يقدم Groupdocs.Watermark حلاً شاملاً لاحتياجات العلامات المائية، مما يضمن بقاء مستنداتك آمنة ومميزة.
## الأسئلة الشائعة
### هل يمكنني استخدام صورة كعلامة مائية بدلاً من النص؟
 نعم، تدعم Groupdocs العلامات المائية النصية والصورية. يمكنك استبدال`TextWatermark` مع`ImageWatermark` وتحديد صورتك.
### هل من الممكن تخصيص موضع العلامة المائية؟
 قطعاً! يمكنك ضبط موضع العلامة المائية باستخدام خصائص مثل`HorizontalAlignment` و`VerticalAlignment`.
### هل يمكنني تطبيق علامات مائية مختلفة على صفحات مختلفة من المستند؟
 نعم، يمكنك تخصيص العلامات المائية لصفحات معينة باستخدام`PageIndex` الممتلكات في`WordProcessingWatermarkPagesOptions`.
### هل يدعم Groupdocs.Watermark تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، تدعم العلامة المائية Groupdocs العديد من التنسيقات بما في ذلك PDF وExcel وPowerPoint والمزيد.
### ما هي متطلبات النظام لاستخدام Groupdocs.Watermark؟
أنت بحاجة إلى نظام مثبت عليه .NET Framework وبيئة تطوير مثل Visual Studio.