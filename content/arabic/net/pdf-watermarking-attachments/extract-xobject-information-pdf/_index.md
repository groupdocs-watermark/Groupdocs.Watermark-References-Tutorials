---
title: استخراج معلومات XObject من PDF
linktitle: استخراج معلومات XObject من PDF
second_title: GroupDocs.Watermark .NET API
description: أطلق العنان لقوة وضع العلامات المائية على المستندات باستخدام GroupDocs.Watermark لـ .NET. إدارة العلامات المائية بسلاسة في ملفات PDF ومستندات Word والصور.
weight: 25
url: /ar/net/pdf-watermarking-attachments/extract-xobject-information-pdf/
type: docs
---
# استخراج معلومات XObject من PDF

## مقدمة
GroupDocs.Watermark for .NET عبارة عن واجهة برمجة تطبيقات قوية للعلامات المائية للمستندات مصممة لمعالجة العلامات المائية بتنسيقات المستندات المختلفة مثل PDF وWord وExcel وPowerPoint والصور. فهو يوفر للمطورين أسلوبًا مباشرًا لإضافة العلامات المائية وإزالتها والبحث فيها واستبدالها في المستندات برمجيًا. سواء كنت بحاجة إلى إضافة شعار الشركة، أو إشعار حقوق الطبع والنشر، أو ختم سري إلى مستنداتك، فإن GroupDocs.Watermark يبسط العملية من خلال واجهة برمجة التطبيقات البديهية الخاصة به.
## المتطلبات الأساسية
قبل الغوص في GroupDocs.Watermark لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:
1. التثبيت: قم بتنزيل وتثبيت GroupDocs.Watermark لـ .NET من[صفحة التحميل](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: قم بتثبيت Visual Studio أو أي برنامج .NET IDE آخر على نظامك.
3. .NET Framework: تأكد من تثبيت .NET Framework المطلوب على جهاز التطوير الخاص بك.

## استيراد مساحات الأسماء
لبدء استخدام GroupDocs.Watermark لـ .NET في مشروعك، تحتاج إلى استيراد مساحات الأسماء الضرورية.
في مشروع .NET الخاص بك، قم بإضافة مرجع إلى GroupDocs.Watermark.dll.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## الخطوة 1: قم بتحميل المستند
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## الخطوة 2: الوصول إلى محتوى PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## الخطوة 3: التكرار عبر الصفحات
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## الخطوة 4: الوصول إلى XObjects
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## الخطوة 5: استخراج المعلومات
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## خاتمة
تمكن GroupDocs.Watermark for .NET المطورين من إدارة العلامات المائية للمستندات بسلاسة في تطبيقات .NET الخاصة بهم. بفضل واجهة برمجة التطبيقات (API) البديهية والميزات القوية، فهو الحل الأمثل لأي احتياجات خاصة بالعلامات المائية. باتباع الخطوات الموضحة في هذا الدليل، يمكنك الاستفادة من الإمكانات الكاملة للعلامة المائية GroupDocs وتحسين سير عمل إدارة المستندات.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع جميع أطر عمل .NET؟
نعم، يدعم GroupDocs.Watermark نطاقًا واسعًا من أطر عمل .NET، بما في ذلك .NET Core و.NET Framework.
### هل يمكنني تطبيق علامات مائية متعددة على مستند واحد باستخدام GroupDocs.Watermark؟
قطعاً! يتيح لك GroupDocs.Watermark إضافة علامات مائية متعددة من أنواع مختلفة إلى مستند واحد.
### هل توفر GroupDocs.Watermark الدعم لتشفير المستندات؟
نعم، يوفر GroupDocs.Watermark إمكانات تشفير لتأمين مستنداتك ضد الوصول غير المصرح به.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark؟
 نعم، يمكنك الوصول إلى الإصدار التجريبي المجاني من GroupDocs.Watermark من[صفحة التحميل](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم وموارد إضافية لـ GroupDocs.Watermark؟
يمكنك استكشاف وثائق GroupDocs.Watermark أو الانضمام إلى منتدى المجتمع أو التواصل مع فريق الدعم للحصول على المساعدة.