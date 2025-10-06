---
title: أضف علامة مائية إلى XObjects في PDF
linktitle: أضف علامة مائية إلى XObjects في PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية إلى XObjects في PDF باستخدام Groupdocs.Watermark لـ .NET. اتبع دليلنا خطوة بخطوة لسهولة التنفيذ.
weight: 20
url: /ar/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# أضف علامة مائية إلى XObjects في PDF

## مقدمة
تعد العلامات المائية لملفات PDF خطوة حاسمة لضمان حماية مستنداتك من الاستخدام غير المصرح به. مع Groupdocs.Watermark for .NET، أصبحت إضافة العلامات المائية إلى XObjects داخل ملفات PDF الخاصة بك أسهل من أي وقت مضى. في هذا البرنامج التعليمي، سنرشدك خلال العملية خطوة بخطوة، مما يضمن أنه يمكنك تطبيق العلامات المائية بثقة على مستندات PDF الخاصة بك. هيا بنا نبدأ!
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، دعونا نتأكد من أن لديك كل ما تحتاج إلى متابعته بسلاسة:
-  Groupdocs.Watermark لـ .NET: قم بتنزيل أحدث إصدار وتثبيته من[هنا](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: تأكد من تثبيت .NET Framework على جهاز التطوير الخاص بك.
- بيئة التطوير: استخدم Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم تطوير .NET.
-  الترخيص المؤقت: الحصول على أ[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) إذا كنت تقوم بتقييم المنتج.
بمجرد استيفاء هذه المتطلبات الأساسية، تصبح جاهزًا لبدء وضع علامة مائية على ملفات PDF الخاصة بك.
## استيراد مساحات الأسماء
أولاً، ستحتاج إلى استيراد مساحات الأسماء الضرورية في مشروعك. افتح مشروع C# الخاص بك وأضف ما يلي باستخدام التوجيهات:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بإعداد مسارات المستندات الخاصة بك
تتضمن الخطوة الأولى إعداد المسارات للمستند الخاص بك. حدد المسار الذي يوجد به ملف PDF الخاص بك والمكان الذي تريد حفظ ملف PDF الذي يحمل علامة مائية.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"` و`"Your Document Directory"` مع المسارات الفعلية على جهازك.
## الخطوة 2: تهيئة خيارات تحميل PDF
بعد ذلك، ستحتاج إلى تهيئة خيارات تحميل PDF. يعد هذا أمرًا بالغ الأهمية لتحميل محتوى PDF بشكل صحيح.
```csharp
var loadOptions = new PdfLoadOptions();
```
## الخطوة 3: قم بتحميل مستند PDF
باستخدام خيارات التحميل، قم بتحميل مستند PDF بالملحق`Watermarker` فصل.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## الخطوة 4: إنشاء العلامة المائية
الآن، تحتاج إلى إنشاء العلامة المائية التي سيتم إضافتها إلى ملف PDF. في هذا البرنامج التعليمي، سنقوم بإنشاء علامة مائية نصية.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## الخطوة 5: إضافة علامة مائية إلى XObjects
قم بالتكرار خلال كل صفحة وكل XObject داخل ملف PDF لتطبيق العلامة المائية.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // إضافة علامة مائية على الصورة
            xObject.Image.Add(watermark);
        }
    }
}
```
## الخطوة 6: احفظ ملف PDF الذي يحمل علامة مائية
وأخيرًا، احفظ ملف PDF الذي يحمل علامة مائية في ملف الإخراج المحدد.
```csharp
    watermarker.Save(outputFileName);
}
```
وهناك لديك! يحتوي ملف PDF الخاص بك الآن على علامات مائية على جميع ملفات XObjects الخاصة به.
## خاتمة
 تعد إضافة علامات مائية إلى مستندات PDF الخاصة بك باستخدام Groupdocs Watermark for .NET عملية مباشرة توفر طبقة إضافية من الأمان. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك التأكد من حماية مستنداتك من الاستخدام غير المصرح به. تذكر أنه يمكنك دائمًا الرجوع إلى[توثيق](https://tutorials.groupdocs.com/Watermark/net/) لمزيد من المعلومات التفصيلية والميزات المتقدمة.
## الأسئلة الشائعة
### هل يمكنني استخدام صورة كعلامة مائية بدلاً من النص؟
نعم، تدعم Groupdocs.Watermark for .NET العلامات المائية النصية والصورية.
### كيف يمكنني اختبار Groupdocs.Watermark دون شرائها؟
 يمكنك استخدام أ[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) لتقييم المنتج.
### هل من الممكن تخصيص مظهر العلامة المائية؟
قطعاً! يمكنك تخصيص الخط والحجم وزاوية التدوير والمزيد.
### هل يدعم Groupdocs.Watermark تنسيقات المستندات الأخرى؟
نعم، فهو يدعم العديد من التنسيقات، بما في ذلك Word وExcel وPowerPoint.
### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من[منتدى المستندات الجماعية](https://forum.groupdocs.com/c/watermark/19).