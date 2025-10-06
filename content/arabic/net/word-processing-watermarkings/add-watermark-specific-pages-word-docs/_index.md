---
title: أضف علامة مائية إلى صفحات محددة في مستندات Word
linktitle: أضف علامة مائية إلى صفحات محددة في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية إلى صفحات معينة في مستندات Word دون عناء باستخدام Groupdocs للعلامة المائية لـ .NET. تعزيز أمان المستندات والعلامات التجارية.
weight: 18
url: /ar/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
type: docs
---
# أضف علامة مائية إلى صفحات محددة في مستندات Word

## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية إضافة علامات مائية إلى صفحات محددة في مستندات Word باستخدام Groupdocs.Watermark لـ .NET. تعد العلامة المائية جانبًا مهمًا في إدارة المستندات، حيث توفر الأمان والعلامة التجارية لمستنداتك. باستخدام Groupdocs.Watermark for .NET، يمكنك بسهولة إضافة علامات مائية نصية أو صورية إلى مستندات Word الخاصة بك بدقة وكفاءة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  Groupdocs.Watermark لـ .NET: قم بتنزيل وتثبيت Groupdocs.Watermark لـ .NET من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. المستند: اجعل مستند Word الذي تريد وضع علامة مائية عليه جاهزًا.
3. بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك باستخدام Visual Studio أو أي أداة تطوير .NET أخرى.

## استيراد مساحات الأسماء
قبل الغوص في الكود، فلنستورد مساحات الأسماء الضرورية:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## الخطوة 1: قم بتحميل المستند
أولاً، نحتاج إلى تحميل مستند Word في كائن العلامة المائية.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // إضافة رمز العلامة المائية سوف يذهب هنا
}
```
## الخطوة 2: إضافة علامة مائية
الآن، دعونا نضيف علامة مائية نصية إلى صفحات محددة من المستند.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // حدد الصفحات لإضافة العلامة المائية
};
watermarker.Add(textWatermark);
```
## الخطوة 3: احفظ المستند
وأخيرًا، احفظ المستند الذي يحمل علامة مائية في الموقع المطلوب.
```csharp
watermarker.Save(outputFileName);
```

## خاتمة
تعلمنا في هذا البرنامج التعليمي كيفية إضافة علامات مائية إلى صفحات معينة في مستندات Word باستخدام Groupdocs.Watermark لـ .NET. باستخدام بضعة أسطر فقط من التعليمات البرمجية، يمكنك تحسين الأمان والعلامة التجارية لمستنداتك دون عناء.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟
نعم، يمكنك إضافة علامات مائية متعددة عن طريق تكرار عملية إضافة العلامة المائية لكل علامة مائية.
### هل يدعم Groupdocs.Watermark تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، تدعم Groupdocs مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل هناك نسخة تجريبية متاحة؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### هل يمكنني تخصيص مظهر العلامة المائية؟
بالتأكيد، يمكنك تخصيص جوانب مختلفة من العلامة المائية مثل الخط والحجم واللون والعتامة.
### هل الدعم الفني متوفر؟
 نعم، يمكنك العثور على الدعم الفني والموارد في منتدى Groupdocs[هنا](https://forum.groupdocs.com/c/watermark/19).