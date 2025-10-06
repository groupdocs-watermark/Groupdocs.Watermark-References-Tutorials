---
title: أضف علامة مائية إلى صفحة معينة في مستندات Word
linktitle: أضف علامة مائية إلى صفحة معينة في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية إلى صفحات محددة في مستندات Word باستخدام GroupDocs لـ .NET. حماية المحتوى الخاص بك دون عناء.
weight: 14
url: /ar/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
type: docs
---
# أضف علامة مائية إلى صفحة معينة في مستندات Word

## مقدمة
يعد وضع العلامات المائية على المستندات جانبًا مهمًا لأمن المستندات والعلامات التجارية. في هذا البرنامج التعليمي، سنستكشف كيفية إضافة علامة مائية إلى صفحة معينة في مستندات Word باستخدام GroupDocs.Watermark لـ .NET.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
- المعرفة الأساسية ببرمجة C#.
- تم تثبيت Visual Studio IDE.
- تم تثبيت GroupDocs.Watermark لـ .NET في مشروعك.

## استيراد مساحات الأسماء
قبل الغوص في التعليمات البرمجية، تأكد من استيراد مساحات الأسماء الضرورية:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: قم بتحميل المستند
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع الرمز الخاص بك هنا
}
```
## الخطوة 2: إضافة العلامة المائية
```csharp
// تحديد نص العلامة المائية ونمطها
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// أضف علامة مائية إلى الصفحة الأخيرة
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## الخطوة 3: احفظ المستند
```csharp
// احفظ المستند بالعلامة المائية
watermarker.Save(outputFileName);
```

## خاتمة
تعلمنا في هذا البرنامج التعليمي كيفية إضافة علامة مائية إلى صفحة معينة في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. باتباع هذه الخطوات، يمكنك حماية مستنداتك بشكل فعال وإضافة عناصر العلامة التجارية حسب الحاجة.
## الأسئلة الشائعة
### هل يمكنني تخصيص نص العلامة المائية ونمطها؟
نعم، يمكنك تخصيص النص والخط والحجم واللون وموضع العلامة المائية وفقًا لمتطلباتك.
### هل GroupDocs.Watermark لـ .NET متوافق مع تنسيقات المستندات الأخرى؟
نعم، يدعم GroupDocs.Watermark تنسيقات المستندات المختلفة، بما في ذلك Word وExcel وPowerPoint وPDF والمزيد.
### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟
بالتأكيد، يمكنك إضافة علامات مائية متعددة بمحتوى وأنماط مختلفة لنفس المستند.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك استكشاف ميزات GroupDocs.Watermark من خلال النسخة التجريبية المجانية. ما عليك سوى زيارة الرابط المقدم للبدء[هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Watermark؟
 يمكنك العثور على موارد مفيدة والحصول على الدعم الفني من[هنا](https://forum.groupdocs.com/c/watermark/19)منتدى GroupDocs.Watermark. قم بزيارة الرابط المقدم للانضمام إلى المجتمع.