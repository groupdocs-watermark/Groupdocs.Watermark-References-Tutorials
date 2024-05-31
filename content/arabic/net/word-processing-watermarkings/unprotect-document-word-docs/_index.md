---
title: إلغاء حماية المستند في مستندات Word
linktitle: إلغاء حماية المستند في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إلغاء حماية مستندات Word بسهولة باستخدام GroupDocs.Watermark لـ .NET. اتبع دليلنا خطوة بخطوة.
type: docs
weight: 38
url: /ar/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## مقدمة
GroupDocs.Watermark for .NET عبارة عن واجهة برمجة تطبيقات قوية تسمح للمطورين بالعمل مع العلامات المائية في تنسيقات المستندات المختلفة، بما في ذلك مستندات Word. في هذا البرنامج التعليمي، سنرشدك خلال عملية إلغاء حماية مستند Word باستخدام GroupDocs.Watermark لـ .NET. سواء كنت مطورًا متمرسًا أو بدأت للتو في تطوير .NET، سيساعدك هذا الدليل التفصيلي خطوة بخطوة على إنجاز المهمة بكفاءة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Watermark لـ .NET: تحتاج إلى تثبيت GroupDocs.Watermark لـ .NET API في بيئة التطوير الخاصة بك. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير مناسبة تم إعدادها لتطوير .NET، بما في ذلك Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة.
3. مستند Word: احصل على مستند Word الذي تريد إلغاء حمايته جاهزًا في نظام الملفات لديك.

## استيراد مساحات الأسماء
قبل الغوص في التعليمات البرمجية، تحتاج إلى استيراد مساحات الأسماء الضرورية لمشروع .NET الخاص بك. يتيح لك هذا الوصول إلى الوظائف التي توفرها GroupDocs.Watermark لـ .NET بسلاسة.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## الخطوة 1: تحديد مسار المستند
حدد المسار إلى مستند Word الذي تريد إلغاء حمايته.
```csharp
string documentPath = "Your Document Path";
```
 يستبدل`"Your Document Path"` بالمسار الفعلي إلى مستند Word الخاص بك.
## الخطوة 2: تعيين اسم ملف الإخراج
حدد الدليل الذي تريد حفظ المستند غير المحمي فيه وقم بتوفير اسم لملف الإخراج.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Directory"` باستخدام مسار الدليل حيث تريد حفظ ملف الإخراج.
## الخطوة 3: قم بتحميل المستند بالخيارات
 إنشاء مثيل ل`WordProcessingLoadOptions` لتحميل مستند Word بخيارات محددة.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## الخطوة 4: إلغاء حماية المستند
 إنشاء مثيل`Watermarker` فئة مع مسار الوثيقة وخيارات التحميل. ثم احصل على محتوى المستند كـ WordProcessingContent وقم بإلغاء حمايته.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## خاتمة
باتباع هذه الخطوات، يمكنك بسهولة إلغاء حماية مستند Word باستخدام GroupDocs.Watermark لـ .NET. توفر واجهة برمجة التطبيقات هذه طريقة مباشرة للتعامل مع العلامات المائية وحماية مستنداتك بكفاءة.
## الأسئلة الشائعة
### هل GroupDocs.Watermark لـ .NET متوافق مع كافة إصدارات .NET؟
نعم، إن GroupDocs.Watermark for .NET متوافق مع .NET Framework 2.0 والإصدارات الأحدث، بما في ذلك .NET Core و.NET Standard.
### هل يمكنني تطبيق العلامات المائية على المستندات بتنسيقات أخرى غير Word؟
قطعاً! يدعم GroupDocs.Watermark for .NET نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم الفني لـ GroupDocs.Watermark لـ .NET؟
 يمكنك زيارة[GroupDocs.منتدى العلامة المائية](https://forum.groupdocs.com/c/watermark/19) للحصول على المساعدة الفنية والدعم المجتمعي.
### هل يمكنني شراء ترخيص مؤقت لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك شراء ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/).