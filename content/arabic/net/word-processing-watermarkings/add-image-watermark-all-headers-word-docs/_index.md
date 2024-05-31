---
title: إضافة علامة مائية للصورة إلى كافة الرؤوس في مستندات Word
linktitle: إضافة علامة مائية للصورة إلى كافة الرؤوس في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: يمكنك بسهولة إضافة علامات مائية للصور إلى كافة الرؤوس في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. اتبع دليلنا خطوة بخطوة مع أمثلة التعليمات البرمجية التفصيلية.
type: docs
weight: 10
url: /ar/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---
## مقدمة
يمكن أن تكون العلامات المائية جزءًا أساسيًا من إدارة المستندات، حيث توفر طريقة لتضمين معلومات مثل الملكية أو السرية أو العلامة التجارية في المستندات. في هذا البرنامج التعليمي، سنتعرف على خطوات إضافة علامة مائية مصورة إلى كافة الرؤوس في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. سواء كنت جديدًا في مجال البرمجة أو مطورًا ذا خبرة، سيساعدك هذا الدليل على تحقيق أهدافك المتعلقة بالعلامة المائية بسهولة.
## المتطلبات الأساسية
قبل أن نتعمق في الكود، دعونا نتأكد من أن لدينا كل ما نحتاجه. فيما يلي قائمة مرجعية للبدء:
1.  GroupDocs.Watermark لـ .NET: قم بتنزيل أحدث إصدار من[هنا](https://releases.groupdocs.com/Watermark/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
3. .NET Framework: تأكد من تثبيت .NET Framework.
4. نموذج مستند Word: مستند Word الذي تريد إضافة العلامة المائية إليه.
5. صورة للعلامة المائية: ملف صورة تريد استخدامه كعلامة مائية.
بمجرد الانتهاء من إعداد هذه العناصر، يمكننا البدء في إعداد مشروعنا.
## استيراد مساحات الأسماء
أولاً، لنستورد مساحات الأسماء الضرورية. تحتوي مساحات الأسماء هذه على فئات وطرق ستساعدنا في التعامل مع العلامات المائية في مستنداتنا.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: إعداد مشروعك
للبدء، قم بإنشاء تطبيق وحدة تحكم جديد في Visual Studio. قم بإضافة مراجع إلى GroupDocs.Watermark DLL في مشروعك. يمكن القيام بذلك عن طريق تثبيت حزمة GroupDocs.Watermark NuGet.
```bash
Install-Package GroupDocs.Watermark
```
## الخطوة 2: قم بتحميل المستند الخاص بك
 الخطوة الأولى لإضافة علامة مائية هي تحميل المستند الذي ستتم إضافة العلامة المائية إليه. هنا سوف نستخدم`WordProcessingLoadOptions` لتحميل مستند Word.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع رمز إضافة العلامة المائية هنا
}
```
## الخطوة 3: إنشاء العلامة المائية للصورة
بعد ذلك، سنقوم بإنشاء علامة مائية للصورة. يتضمن ذلك تحديد ملف الصورة الذي تريد استخدامه كعلامة مائية.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // سيتم وضع رمز تطبيق العلامة المائية هنا
}
```
## الخطوة 4: إضافة علامة مائية إلى رؤوس القسم الأول
 نحتاج إلى إضافة العلامة المائية إلى كافة الرؤوس في القسم الأول من مستند Word. لهذا نستخدم`WordProcessingWatermarkSectionOptions` وحدد فهرس القسم.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## الخطوة 5: ربط الرؤوس والتذييلات
للتأكد من ظهور العلامة المائية في رؤوس جميع الأقسام، نقوم بربط جميع الرؤوس والتذييلات الأخرى برؤوس وتذييلات القسم الأول.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## الخطوة 6: احفظ المستند
وأخيرًا، نقوم بحفظ المستند الذي يحمل علامة مائية في المسار المحدد. تضمن هذه الخطوة كتابة تغييراتك في ملف جديد، مع الحفاظ على المستند الأصلي.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## خاتمة
وهناك لديك! لقد نجحت في إضافة علامة مائية مصورة إلى كافة الرؤوس في مستند Word باستخدام GroupDocs.Watermark لـ .NET. تسهل هذه المكتبة القوية إدارة العلامات المائية وتطبيقها على أنواع مختلفة من المستندات، مما يضمن حماية المحتوى الخاص بك وتمييزه بعلامة تجارية احترافية.
## الأسئلة الشائعة
### هل يمكنني استخدام أنواع أخرى من العلامات المائية إلى جانب الصور؟
نعم، تدعم GroupDocs العلامات المائية النصية والصورة وحتى العلامات المائية المركبة.
### هل من الممكن وضع علامة مائية على أجزاء أخرى من المستند إلى جانب العناوين؟
قطعاً! يمكنك وضع علامة مائية على التذييلات والنص وحتى صفحات أو أقسام محددة.
### هل يدعم GroupDocs.Watermark تنسيقات المستندات الأخرى؟
نعم، فهو يدعم مجموعة واسعة من التنسيقات بما في ذلك ملفات PDF وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص موضع العلامة المائية ومظهرها؟
نعم، يمكنك تخصيص الحجم والموضع والعتامة والعديد من الخصائص الأخرى للعلامة المائية.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Watermark؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).