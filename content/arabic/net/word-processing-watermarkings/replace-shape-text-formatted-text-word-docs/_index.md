---
title: استبدال نص الشكل بنص منسق في مستندات Word
linktitle: استبدال نص الشكل بنص منسق في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية استبدال نص الشكل بنص منسق في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. قدرات تحرير المستندات الخاصة بك دون عناء.
weight: 34
url: /ar/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---

# استبدال نص الشكل بنص منسق في مستندات Word

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية استبدال نص الشكل بنص منسق في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. توفر هذه المكتبة ميزات قوية للتعامل مع العلامات المائية، بما في ذلك استبدال النص داخل الأشكال.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Watermark لـ .NET: تأكد من تثبيت GroupDocs.Watermark وإعداده لـ .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. مسار المستند: يجب أن يكون لديك المسار إلى مستند Word الذي تريد استبدال النص فيه.

## استيراد مساحات الأسماء
قبل كتابة التعليمات البرمجية، قم باستيراد مساحات الأسماء الضرورية:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
 قم بتحميل مستند Word باستخدام`Watermarker` فصل:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // يستمر الرمز الخاص بك هنا ...
}
```
## الخطوة 2: الحصول على المحتوى واستبدال النص
بمجرد تحميل المستند، احصل على المحتوى واستبدل النص داخل الأشكال:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## الخطوة 3: احفظ المستند
بعد استبدال النص، احفظ المستند المعدل:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## خاتمة
أصبح استبدال نص الشكل بنص منسق في مستندات Word أمرًا سهلاً باستخدام GroupDocs لـ .NET. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك إدارة النص ومعالجته بكفاءة داخل مستنداتك.

## الأسئلة الشائعة
### هل يمكنني استبدال النص في أنواع أخرى من المستندات باستخدام GroupDocs.Watermark لـ .NET؟
نعم، تدعم GroupDocs تنسيقات المستندات المختلفة مثل PDF وExcel وPowerPoint والمزيد.
### هل GroupDocs.Watermark متوافق مع .NET Core؟
نعم، يدعم GroupDocs.Watermark كلاً من .NET Framework و.NET Core.
### هل توفر GroupDocs.Watermark الدعم لإضافة الصور كعلامات مائية؟
بالتأكيد، GroupDocs.Watermark يسمح لك بإضافة علامات مائية نصية وصورية إلى مستنداتك.
### هل يمكنني تخصيص مظهر العلامات المائية المضافة باستخدام GroupDocs.Watermark؟
نعم، لديك السيطرة الكاملة على مظهر العلامات المائية وموضعها وخصائصها الأخرى.
### هل هناك إصدار تجريبي متاح لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).