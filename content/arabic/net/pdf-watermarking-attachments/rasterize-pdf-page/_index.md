---
title: تنقيط صفحة PDF
linktitle: تنقيط صفحة PDF
second_title: GroupDocs.Watermark .NET API
description: قم بتحسين أمان المستند باستخدام GroupDocs للعلامة المائية لـ .NET. أضف علامات مائية إلى PDF والتنسيقات الأخرى بسلاسة.
weight: 28
url: /ar/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## مقدمة
GroupDocs.Watermark for .NET عبارة عن واجهة برمجة تطبيقات قوية تسمح للمطورين بإضافة علامات مائية بسلاسة إلى تنسيقات المستندات المختلفة، بما في ذلك PDF وWord وExcel وPowerPoint والمزيد. بفضل واجهته البديهية وميزاته الشاملة، يعمل GroupDocs.Watermark على تبسيط عملية إضافة علامات مائية نصية أو صورية إلى المستندات، مما يمكّن المستخدمين من حماية ملكيتهم الفكرية وتعزيز أمان المستندات دون عناء.
## المتطلبات الأساسية
قبل الغوص في استخدام GroupDocs.Watermark لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:
1. التثبيت: قم بتنزيل وتثبيت GroupDocs.Watermark لـ .NET من[صفحة التحميل](https://releases.groupdocs.com/Watermark/net/).
2.  الترخيص: الحصول على ترخيص لـ GroupDocs.Watermark لـ .NET. يمكنك الحصول على ترخيص مؤقت لأغراض التقييم من[هنا](https://purchase.groupdocs.com/temporary-license/) أو قم بشراء ترخيص كامل من[صفحة الشراء](https://purchase.groupdocs.com/buy).
3. .NET Framework: تأكد من تثبيت .NET Framework على جهاز التطوير الخاص بك.
4. المستند: قم بإعداد المستند الذي تريد إضافة علامات مائية إليه.

## استيراد مساحات الأسماء
لبدء استخدام GroupDocs.Watermark لـ .NET، قم باستيراد مساحات الأسماء الضرورية إلى مشروعك:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // الكود الخاص بك يذهب هنا
}
```
## الخطوة 2: تهيئة العلامة المائية
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## الخطوة 3: إضافة علامة مائية
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## الخطوة 4: تنقيط الصفحة
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## الخطوة 5: احفظ المستند
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
في الختام، يقدم GroupDocs.Watermark for .NET حلاً سلسًا لإضافة علامات مائية إلى PDF وتنسيقات المستندات الأخرى. من خلال اتباع الدليل الموضح أعلاه خطوة بخطوة، يمكن للمطورين تنقيط صفحات PDF بكفاءة وتعزيز أمان المستندات بسهولة.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، تدعم GroupDocs.Watermark نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك Word وExcel وPowerPoint وVisio والمزيد.
### هل يمكنني تخصيص مظهر العلامة المائية المضافة إلى المستند؟
قطعاً! يوفر GroupDocs.Watermark خيارات تخصيص واسعة النطاق للعلامات المائية النصية والصورية، مما يسمح للمستخدمين بضبط الخط والحجم واللون والعتامة والموضع وفقًا لتفضيلاتهم.
### هل GroupDocs.Watermark مناسب للاستخدام الشخصي والتجاري؟
نعم، توفر GroupDocs.Watermark خيارات ترخيص مرنة لتلبية احتياجات الأفراد والمؤسسات، مما يجعلها مناسبة للمشاريع الشخصية بالإضافة إلى التطبيقات التجارية واسعة النطاق.
### هل يقدم GroupDocs.Watermark الدعم الفني للمطورين؟
نعم، يمكن للمطورين الوصول إلى الدعم الفني الشامل من خلال منتدى GroupDocs.Watermark، حيث يمكنهم طلب المساعدة ومشاركة الخبرات والتفاعل مع زملائهم المطورين.
### هل يمكنني تجربة GroupDocs.Watermark قبل إجراء عملية الشراء؟
بالتأكيد! يمكنك الاستفادة من الإصدار التجريبي المجاني من GroupDocs.Watermark من[صفحة الإصدارات](https://releases.groupdocs.com/)مما يسمح لك باستكشاف ميزاته ووظائفه قبل الالتزام بالشراء.