---
title: تنقيط وثيقة PDF
linktitle: تنقيط وثيقة PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية تحويل مستندات PDF إلى نقطية باستخدام GroupDocs.Watermark لـ .NET. قم بتعزيز أمان المستندات وجاذبيتها المرئية دون عناء.
weight: 27
url: /ar/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# تنقيط وثيقة PDF

## مقدمة
في مجال إدارة المستندات ومعالجتها، تقف GroupDocs.Watermark for .NET شامخة كأداة قوية، حيث توفر إمكانات قوية لإضافة العلامات المائية وإزالتها والبحث فيها في تنسيقات المستندات المختلفة. سواء أكان الأمر يتعلق بحماية مستنداتك من خلال إشعارات حقوق الطبع والنشر، أو إضافة شعارات الشركة للعلامة التجارية، أو ببساطة إضافة تعليقات توضيحية إلى المستندات باستخدام الطوابع، تعمل GroupDocs.Watermark على تبسيط العملية من خلال واجهة برمجة التطبيقات البديهية ومجموعة الميزات الشاملة.
## المتطلبات الأساسية
قبل الغوص في عالم العلامات المائية باستخدام GroupDocs.Watermark for .NET، تأكد من توفر المتطلبات الأساسية التالية:
### 1. قم بتثبيت .NET Framework
تأكد من تثبيت .NET Framework على جهاز التطوير الخاص بك. يمكنك تنزيله من موقع Microsoft على الويب أو استخدام مدير الحزم المفضل لديك.
#### الخطوة 1: تنزيل .NET Framework
قم بزيارة صفحة تنزيل Microsoft .NET Framework.
#### الخطوة 2: تثبيت .NET Framework
اتبع تعليمات التثبيت المتوفرة في صفحة التنزيل لتثبيت .NET Framework على نظامك.
### 2. الحصول على ترخيص GroupDocs.Watermark
للاستفادة من الإمكانيات الكاملة لـ GroupDocs.Watermark، تحتاج إلى ترخيص صالح. يمكنك إما شراء ترخيص أو الحصول على ترخيص مؤقت لأغراض التقييم.
#### الخطوة 1: الحصول على الترخيص
قم بزيارة صفحة شراء GroupDocs.Watermark.
#### الخطوة 2: شراء أو الحصول على ترخيص مؤقت
اختر خيار الترخيص المناسب بناءً على احتياجاتك — قم بشراء ترخيص للاستخدام المستمر أو احصل على ترخيص مؤقت لأغراض التقييم.

## استيراد مساحات الأسماء
قبل البدء في وضع علامة مائية على مستنداتك، تأكد من استيراد مساحات الأسماء اللازمة للوصول إلى وظائف GroupDocs بسلاسة.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

الآن بعد أن قمت بإعداد كل شيء، دعنا نتعمق في تحويل مستند PDF إلى تنسيق نقطي باستخدام GroupDocs.Watermark لـ .NET. يقوم التنقيط بتحويل كل صفحة من مستند PDF إلى تنسيق صورة نقطية، مثل PNG.
## الخطوة 1: تهيئة المتغيرات
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
تأكد من استبدال "Your Document Path" و"Your Document Directory" بالمسار الفعلي لمستند PDF الخاص بك ودليل الإخراج المطلوب، على التوالي.
## الخطوة 2: تحميل المستند وإضافة علامة مائية
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // تهيئة الصورة أو العلامة المائية النصية
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // أضف علامة مائية من أي نوع أولاً
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // تنقيط كافة الصفحات
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // يتم استبدال محتوى جميع الصفحات بالصور النقطية
    watermarker.Save(outputFileName);
}
```
في هذه الخطوة، نقوم بتحميل مستند PDF وتهيئة علامة مائية نصية بخصائص محددة مثل النص والخط والمحاذاة وزاوية التدوير ونوع الحجم وعامل القياس والعتامة. ثم نقوم بإضافة العلامة المائية إلى المستند. بعد ذلك، نقوم باسترداد محتوى مستند PDF ونقوم بتنقيط جميع الصفحات إلى تنسيق PNG بدقة 100 نقطة في البوصة. وأخيرًا، نقوم بحفظ المستند المعدل بمحتوى نقطي.

## خاتمة
يقدم GroupDocs.Watermark for .NET حلاً شاملاً لإضافة علامات مائية إلى تنسيقات المستندات المختلفة بسهولة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تنقيط مستندات PDF بشكل فعال وتحسين أمانها وجاذبيتها المرئية.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، يدعم GroupDocs.Watermark مجموعة واسعة من تنسيقات المستندات، بما في ذلك Microsoft Word وExcel وPowerPoint وVisio وOutlook وغيرها الكثير.
### هل يمكنني تخصيص مظهر العلامات المائية المضافة باستخدام GroupDocs.Watermark؟
قطعاً! يوفر GroupDocs.Watermark خيارات واسعة لتخصيص خصائص العلامة المائية مثل النص والخط واللون والحجم والعتامة والتدوير والموضع.
### هل تقدم GroupDocs.Watermark الدعم لمعالجة الدُفعات؟
نعم، يمكنك بسهولة معالجة مستندات متعددة في الوضع الدفعي باستخدام GroupDocs، مما يوفر الوقت والجهد في وضع علامة مائية على مجموعات كبيرة من الملفات.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Watermark من الموقع الإلكتروني لتقييم ميزاته قبل إجراء عملية الشراء.
### كيف يمكنني الحصول على المساعدة إذا واجهت أية مشكلات أو كانت لدي أسئلة حول GroupDocs.Watermark؟
يمكنك زيارة منتدى GroupDocs.Watermark لطلب الدعم من المجتمع أو التواصل مع فريق دعم GroupDocs للحصول على المساعدة.