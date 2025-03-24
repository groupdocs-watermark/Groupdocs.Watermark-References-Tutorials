---
title: أضف علامة مائية توضيحية للطباعة فقط إلى PDF
linktitle: أضف علامة مائية توضيحية للطباعة فقط إلى PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية توضيحية للطباعة فقط إلى ملفات PDF باستخدام GroupDocs.Watermark لـ .NET. تعزيز أمان المستندات والعلامات التجارية دون عناء.
weight: 13
url: /ar/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# أضف علامة مائية توضيحية للطباعة فقط إلى PDF

## مقدمة
في هذا البرنامج التعليمي، سوف نتعمق في عملية إضافة علامة مائية توضيحية للطباعة فقط إلى ملف PDF باستخدام GroupDocs.Watermark لـ .NET. تعتبر وضع العلامات المائية على المستندات جانبًا مهمًا لأمن المستندات والعلامات التجارية، وتوفر GroupDocs.Watermark حلاً سلسًا لمطوري .NET لتحقيق ذلك.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
- الفهم الأساسي للغة البرمجة C#.
- تم تثبيت Visual Studio على جهازك.
- GroupDocs.Watermark لمكتبة .NET المثبتة في مشروعك.

## استيراد مساحات الأسماء
للبدء، تأكد من استيراد مساحات الأسماء الضرورية:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
 أولاً، تحتاج إلى تحميل مستند PDF الذي تريد وضع علامة مائية عليه. يستبدل`"Your Document Path"` مع المسار إلى ملف PDF الخاص بك و`"Your Document Directory"` مع الدليل الذي تريد حفظ ملف الإخراج فيه.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم إضافة رمز العلامة المائية هنا
}
```
## الخطوة 2: إضافة علامة مائية
بعد ذلك، قم بإنشاء كائن علامة مائية نصية بالنص والخط المطلوبين. تعيين`isPrintOnly` ل`true` للتأكد من أن العلامة المائية مرئية فقط عند طباعة المستند، وليس في وضع العرض.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## الخطوة 3: تكوين خيارات العلامة المائية
حدد خيارات العلامة المائية، مثل فهرس الصفحة حيث يجب إضافة العلامة المائية وتحديدها كتعليق توضيحي للطباعة فقط.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## الخطوة 4: تطبيق العلامة المائية
أضف العلامة المائية إلى المستند باستخدام الخيارات المحددة واحفظ ملف الإخراج.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة علامة مائية توضيحية للطباعة فقط إلى مستند PDF باستخدام GroupDocs.Watermark لـ .NET. يتيح ذلك للمطورين تحسين أمان المستندات والعلامات التجارية بسهولة.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، تدعم العلامة المائية GroupDocs تنسيقات المستندات المختلفة مثل Word وExcel وPowerPoint والصور.
### هل يمكنني تخصيص مظهر العلامة المائية؟
من المؤكد أن GroupDocs.Watermark يوفر خيارات واسعة لتخصيص نص العلامة المائية والخط واللون والحجم والموضع.
### هل توفر GroupDocs.Watermark إمكانات معالجة الدفعات؟
بالتأكيد، يمكن للمطورين وضع علامة مائية على مستندات متعددة في وقت واحد باستخدام ميزات المعالجة المجمعة.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark؟
نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من GroupDocs.Watermark من الرابط المقدم.
### كيف يمكنني الحصول على الدعم الفني لـ GroupDocs.Watermark؟
يمكنك طلب المساعدة الفنية من منتدى GroupDocs.Watermark المتوفر على رابط الدعم المقدم.