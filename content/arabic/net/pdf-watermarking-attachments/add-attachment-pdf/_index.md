---
title: إضافة مرفق إلى PDF
linktitle: إضافة مرفق إلى PDF
second_title: GroupDocs.Watermark .NET API
description: قم بتحسين قدرات إدارة مستندات .NET الخاصة بك باستخدام GroupDocs.Watermark لوضع العلامات المائية ومعالجة المرفقات بشكل سلس.
weight: 12
url: /ar/net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# إضافة مرفق إلى PDF

## مقدمة
في مجال تطوير .NET، تبرز GroupDocs.Watermark كأداة قوية لإدارة العلامات المائية والتعليقات التوضيحية والمزيد ضمن تنسيقات المستندات المختلفة. سواء كنت تعمل باستخدام ملفات PDF أو مستندات Word أو صور، فإن GroupDocs.Watermark for .NET توفر تكاملاً سلسًا يمكّن المطورين من التعامل مع المستندات بسهولة.
## المتطلبات الأساسية
قبل الغوص في تعقيدات استخدام GroupDocs.Watermark لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:
1.  التثبيت: تأكد من تثبيت GroupDocs.Watermark لـ .NET. يمكنك تنزيله من[صفحة الإصدار](https://releases.groupdocs.com/Watermark/net/).
2. إعداد المستند: قم بإعداد مستند تريد وضع علامة مائية أو عمليات أخرى عليه.
3. المعرفة الأساسية بـ C#: تعرف على أساسيات لغة البرمجة C# حيث سنستخدمها للتفاعل مع GroupDocs.Watermark API.

## استيراد مساحات الأسماء
قبل البدء بالتنفيذ، من الضروري استيراد مساحات الأسماء الضرورية للوصول إلى وظيفة GroupDocs.Watermark. فيما يلي مساحات الأسماء المطلوبة:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## الخطوة 1: تحميل المستند
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 في هذه الخطوة، نحدد المسار إلى المستند الذي نريد العمل معه ونقوم بإنشاء ملف`PdfLoadOptions` كائن لتحميل مستندات PDF. ثم نقوم بتهيئة أ`Watermarker` الكائن بمسار المستند وخيارات التحميل.
## الخطوة 2: احصل على محتوى PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 هنا، نحصل على محتوى مستند PDF باستخدام ملف`GetContent<PdfContent>()` طريقة.
## الخطوة 3: إضافة المرفق
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
تتضمن هذه الخطوة إضافة مرفق إلى مستند PDF. تحتاج إلى توفير بايت الملف المرفق، والاسم، والوصف.
## الخطوة 4: حفظ التغييرات
```csharp
watermarker.Save(outputFileName);
```
وأخيرًا، نقوم بحفظ التغييرات التي تم إجراؤها على المستند مع المرفق المضاف.

## خاتمة
يقدم GroupDocs.Watermark for .NET حلاً قويًا لإدارة العلامات المائية والمرفقات للمستندات بسلاسة. باتباع الخطوات الموضحة أعلاه، يمكنك بسهولة دمج وظائف العلامات المائية والمرفقات في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### هل GroupDocs.Watermark متوافق مع جميع أطر عمل .NET؟
نعم، يدعم GroupDocs.Watermark .NET Framework 2.0 والإصدارات الأحدث.
### هل يمكنني إزالة العلامات المائية المضافة باستخدام GroupDocs.Watermark؟
نعم، يوفر GroupDocs.Watermark طرقًا لإزالة العلامات المائية من المستندات.
### هل يدعم GroupDocs.Watermark تشفير المستندات؟
نعم، يتيح لك GroupDocs.Watermark العمل مع المستندات المشفرة.
### هل يمكنني تخصيص مظهر العلامات المائية؟
بالتأكيد، يقدم GroupDocs.Watermark خيارات تخصيص متنوعة للعلامات المائية.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
 نعم، يمكنك الوصول إلى النسخة التجريبية من[صفحة الإصدارات](https://releases.groupdocs.com/).