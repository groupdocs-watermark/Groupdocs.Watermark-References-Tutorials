---
title: إضافة علامة مائية إلى كافة المرفقات في ملف PDF
linktitle: إضافة علامة مائية إلى كافة المرفقات في ملف PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية إلى مرفقات PDF باستخدام GroupDocs.Watermark لـ .NET. تأمين المستندات الخاصة بك مع العلامات المائية المخصصة بسهولة.
type: docs
weight: 16
url: /ar/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## مقدمة
يمكن أن تكون إضافة علامات مائية إلى مرفقات PDF خطوة حاسمة في إدارة المستندات، خاصة عند ضمان الأمان أو العلامة التجارية. يقدم GroupDocs.Watermark for .NET حلاً شاملاً لتضمين العلامات المائية بسلاسة في ملفات PDF. في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة علامة مائية إلى كافة المرفقات داخل مستند PDF باستخدام GroupDocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Watermark لـ .NET: إذا لم تكن قد قمت بذلك بالفعل، فقم بتنزيل GroupDocs.Watermark لـ .NET وتثبيته من[موقع إلكتروني](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة باستخدام Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
3. مستند PDF: قم بإعداد مستند PDF الذي تريد إضافة علامات مائية إليه، بالإضافة إلى المرفقات التي ترغب في وضع علامة مائية عليها.

## استيراد مساحات الأسماء
قبل الغوص في التعليمات البرمجية، تأكد من استيراد مساحات الأسماء الضرورية للوصول إلى GroupDocs.Watermark لوظائف .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: تحديد مسار المستند ودليل الإخراج
أولاً، حدد المسار إلى مستند PDF الذي قمت بإدخاله والدليل الذي سيتم حفظ المستند الذي يحمل العلامة المائية فيه:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## الخطوة 2: تهيئة خيارات التحميل والعلامة المائية
بعد ذلك، قم بتهيئة خيارات التحميل لمستند PDF وقم بإنشاء علامة مائية نصية:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## الخطوة 3: تحميل المستند والمرفقات
قم بتحميل مستند PDF وكرر من خلال مرفقاته:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## الخطوة 4: التحقق من دعم المرفقات
تحقق مما إذا كان الملف المرفق مدعومًا بواسطة GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## الخطوة 5: إضافة علامة مائية إلى المرفقات
قم بتحميل المستند المرفق وأضف العلامة المائية:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## الخطوة 6: حفظ التغييرات
أخيرًا، احفظ التغييرات التي تم إجراؤها على مستند PDF الذي يحمل علامة مائية:
```csharp
    watermarker.Save(outputFileName);
}
```

## خاتمة
في هذا البرنامج التعليمي، اكتشفنا كيفية إضافة علامات مائية إلى كافة المرفقات داخل مستند PDF باستخدام GroupDocs.Watermark لـ .NET. باتباع الدليل الموضح خطوة بخطوة، يمكنك دمج العلامات المائية بسلاسة في ملفات PDF الخاصة بك، مما يضمن أمان المستندات والعلامة التجارية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر العلامة المائية؟
نعم، يمكنك تخصيص جوانب مختلفة مثل النص والخط والحجم واللون وموضع العلامة المائية وفقًا لمتطلباتك.
### هل يدعم GroupDocs.Watermark تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، يدعم GroupDocs.Watermark مجموعة واسعة من تنسيقات المستندات بما في ذلك Microsoft Word وExcel وPowerPoint وVisio وOutlook والصور.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark؟
نعم، يمكنك استكشاف ميزات GroupDocs.Watermark عن طريق تنزيل الإصدار التجريبي المجاني من موقع الويب.
### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟
بالتأكيد، تتيح لك GroupDocs.Watermark إضافة علامات مائية متعددة بما في ذلك النص والصورة والتعليق التوضيحي في وقت واحد لتعزيز أمان المستندات والعلامة التجارية.
### هل يتوفر الدعم الفني لمستخدمي GroupDocs.Watermark؟
نعم، يوفر GroupDocs دعمًا فنيًا شاملاً من خلال المنتديات وقنوات الدعم المخصصة لمساعدة المستخدمين في أي استفسارات أو مشكلات قد يواجهونها.