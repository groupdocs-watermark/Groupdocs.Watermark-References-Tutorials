---
title: إضافة علامات مائية إلى صفحات محددة في PDF
linktitle: إضافة علامات مائية إلى صفحات محددة في PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية نصية وصورية إلى صفحات معينة في ملفات PDF باستخدام Groupdocs للعلامة المائية لـ .NET. اتبع دليلنا التفصيلي لتأمين مستنداتك.
weight: 15
url: /ar/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
type: docs
---
# إضافة علامات مائية إلى صفحات محددة في PDF

## مقدمة
تعد إضافة علامات مائية إلى مستندات PDF الخاصة بك خطوة حاسمة في حماية المحتوى الخاص بك وتأكيد ملكيتك. سواء كنت تقوم بوضع علامة على مسودة، أو تأمين معلومات حساسة، أو ببساطة إضافة علامة تجارية، فإن العلامات المائية هي أداة فعالة. في هذا البرنامج التعليمي، سنستكشف كيفية استخدام Groupdocs.Watermark لـ .NET لإضافة علامات مائية نصية وصورية إلى صفحات محددة في ملفات PDF الخاصة بك. سنقوم بتقسيم العملية إلى خطوات يمكن التحكم فيها، مما يضمن أنه يمكنك متابعة هذه الميزات وتنفيذها في مشاريعك.
## المتطلبات الأساسية
قبل الغوص في التنفيذ، تأكد من توفر المتطلبات الأساسية التالية:
- تثبيت Visual Studio: ستحتاج إلى IDE مثل Visual Studio لكتابة وتشغيل كود .NET الخاص بك.
- .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
-  Groupdocs.Watermark لـ .NET: قم بتنزيل وتثبيت Groupdocs.Watermark لـ .NET. يمكنك الحصول عليه[هنا](https://releases.groupdocs.com/Watermark/net/).
- المعرفة الأساسية بـ C#: الإلمام بلغة البرمجة C# سيكون مفيدًا.
- مستند PDF: احصل على ملف PDF جاهزًا يمكنك استخدامه لاختبار إضافة العلامات المائية.
## استيراد مساحات الأسماء
للبدء، ستحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروعك. تعتبر هذه الخطوة حاسمة لأنها تتيح لك الوصول إلى فئات وأساليب العلامة المائية.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: إعداد المشروع
### إنشاء مشروع جديد
أولاً، افتح Visual Studio وقم بإنشاء مشروع C# جديد. يمكنك اختيار تطبيق وحدة التحكم للبساطة.
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### قم بتثبيت Groupdocs.العلامة المائية
بعد ذلك، قم بتثبيت مكتبة Groupdocs.Watermark عبر NuGet Package Manager.
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
ابحث عن "Groupdocs.Watermark" وقم بتثبيته.
## الخطوة 2: قم بتحميل مستند PDF الخاص بك
### تحديد مسارات الوثيقة
حدد المسار إلى مستند PDF الخاص بك ودليل الإخراج حيث سيتم حفظ ملف PDF ذو العلامة المائية.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### قم بتحميل مستند PDF
 استخدم ال`PdfLoadOptions` فئة لتحميل وثيقة PDF الخاصة بك.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع الكود الخاص بك لإضافة العلامات المائية هنا
}
```
## الخطوة 3: إضافة علامة مائية نصية إلى الصفحات الفردية
### إنشاء علامة مائية نصية
 إنشاء`TextWatermark` كائن مع إعدادات النص والخط المطلوب.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### تطبيق خيارات العلامة المائية النصية
 يستخدم`PdfArtifactWatermarkOptions` لتحديد كيفية تطبيق العلامة المائية.
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## الخطوة 4: إضافة علامة مائية للصورة إلى الصفحة الأولى
قم بتحميل صورة لاستخدامها كعلامة مائية. تأكد من صحة مسار الصورة.
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## الخطوة 5: احفظ ملف PDF الذي يحمل علامة مائية
وأخيرًا، احفظ ملف PDF الذي يحمل علامة مائية في دليل الإخراج المحدد.
```csharp
watermarker.Save(outputFileName);
```
## خاتمة
تعد إضافة علامات مائية إلى ملفات PDF الخاصة بك باستخدام Groupdocs للعلامة المائية لـ .NET عملية واضحة. باتباع هذه الخطوات، يمكنك إضافة علامات مائية نصية وصورية بكفاءة إلى صفحات محددة في مستندات PDF الخاصة بك. وهذا لا يساعد فقط في تأمين مستنداتك ولكن أيضًا في الحفاظ على المظهر الاحترافي. جربه واستكشف خيارات التخصيص المتنوعة المتاحة لجعل علاماتك المائية فريدة وفعالة.
## الأسئلة الشائعة
### ما هي العلامة المائية Groupdocs.Net لـ .NET؟
Groupdocs.Watermark for .NET هي مكتبة تسمح لك بإضافة العلامات المائية والبحث فيها وإزالتها في تنسيقات المستندات المختلفة بما في ذلك PDF وWord وExcel والمزيد.
### هل يمكنني تخصيص مظهر العلامة المائية؟
نعم، يمكنك تخصيص خط النص وحجمه ولونه وموضعه للعلامات المائية النصية، ويمكنك ضبط الحجم والعتامة والموضع للعلامات المائية للصور.
### هل يمكن إضافة علامات مائية على صفحات محددة فقط؟
قطعاً. يوفر Groupdocs.Watermark for .NET خيارات لإضافة علامات مائية إلى صفحات محددة، أو صفحات فردية أو زوجية، أو نطاق من الصفحات.
### كيف يمكنني الحصول على نسخة تجريبية مجانية من Groupdocs.Watermark؟
 يمكنك تنزيل نسخة تجريبية مجانية من[موقع مستندات المجموعة](https://releases.groupdocs.com/).
### أين يمكنني العثور على وثائق أكثر تفصيلا؟
 لمزيد من المعلومات التفصيلية، يمكنك الرجوع إلى[توثيق](https://tutorials.groupdocs.com/Watermark/net/).