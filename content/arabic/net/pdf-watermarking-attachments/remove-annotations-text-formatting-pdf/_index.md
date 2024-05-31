---
title: إزالة التعليقات التوضيحية بتنسيق نص محدد في PDF
linktitle: إزالة التعليقات التوضيحية بتنسيق نص محدد في PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إزالة التعليقات التوضيحية بتنسيق نصي محدد في مستندات PDF باستخدام Groupdocs لـ .NET.
type: docs
weight: 30
url: /ar/net/pdf-watermarking-attachments/remove-annotations-text-formatting-pdf/
---
## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إزالة التعليقات التوضيحية بتنسيق نص معين في مستند PDF باستخدام Groupdocs.Watermark for .NET. توفر هذه المكتبة ميزات قوية للعمل مع العلامات المائية والتعليقات التوضيحية وعناصر المستند الأخرى بتنسيقات مختلفة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  Groupdocs.Watermark لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: بيئة تطوير .NET تم إعدادها على جهازك.
3. مستند PDF: احصل على مستند PDF يحتوي على التعليقات التوضيحية التي تريد تعديلها.

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء الضرورية للوصول إلى الفئات والطرق المطلوبة:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل مستند PDF
```csharp
string documentPath = "YourDocumentPath";
string outputDirectory = "YourDocumentDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## الخطوة 2: احصل على محتوى PDF وكرره عبر الصفحات
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfPage page in pdfContent.Pages)
    {
```
## الخطوة 3: التكرار من خلال التعليقات التوضيحية والتحقق من تنسيق النص
```csharp
        for (int i = page.Annotations.Count - 1; i >= 0; i--)
        {
            foreach (FormattedTextFragment fragment in page.Annotations[i].FormattedTextFragments)
            {
```
## الخطوة 4: إزالة التعليقات التوضيحية بتنسيق نص محدد
```csharp
                if (fragment.Font.FamilyName == "Verdana")
                {
                    page.Annotations.RemoveAt(i);
                    break;
                }
            }
        }
    }
```
## الخطوة 5: احفظ مستند PDF المعدل
```csharp
    watermarker.Save(outputFileName);
}
```
لقد نجحت الآن في إزالة التعليقات التوضيحية بتنسيق نصي محدد من مستند PDF الخاص بك باستخدام Groupdocs.Watermark for .NET.

## خاتمة
يوفر Groupdocs.Watermark for .NET حلاً مناسبًا للعمل مع التعليقات التوضيحية والعناصر الأخرى في مستندات PDF. باتباع هذا البرنامج التعليمي، يمكنك بسهولة التعامل مع التعليقات التوضيحية بناءً على تنسيق نص محدد، مما يعزز إمكانية قراءة ملفات PDF الخاصة بك ومظهرها.
## الأسئلة الشائعة
### هل يمكنني استخدام Groupdocs.Watermark لـ .NET مع تنسيقات المستندات الأخرى؟
نعم، يدعم Groupdocs.Watermark تنسيقات المستندات المختلفة، بما في ذلك DOCX وPPTX وXLSX وPDF والمزيد.
### هل هناك نسخة تجريبية مجانية متاحة لـ Groupdocs.Watermark لـ .NET؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من Groupdocs.Watermark لـ .NET من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على وثائق Groupdocs.Watermark لـ .NET؟
 يمكنك العثور على وثائق مفصلة ومراجع API[هنا](https://reference.groupdocs.com/Watermark/net/).
### كيف يمكنني الحصول على الدعم لأية مشكلات أو استفسارات تتعلق بـ Groupdocs.Watermark؟
 يمكنك نشر أسئلتك أو مشكلاتك في منتدى Groupdocs.Watermark[هنا](https://forum.groupdocs.com/c/watermark/19).
### هل يمكنني شراء ترخيص مؤقت لـ Groupdocs.Watermark لـ .NET؟
 نعم، يمكنك شراء ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/).