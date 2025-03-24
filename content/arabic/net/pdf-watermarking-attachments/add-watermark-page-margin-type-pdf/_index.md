---
title: إضافة علامة مائية مع نوع هامش الصفحة في PDF
linktitle: إضافة علامة مائية مع نوع هامش الصفحة في PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية مع نوع هامش الصفحة في ملف PDF باستخدام Groupdocs لـ .NET. تأمين المستندات الخاصة بك دون عناء.
weight: 21
url: /ar/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---
## مقدمة
في العصر الرقمي الذي نعيشه اليوم، أصبح تأمين المستندات أكثر أهمية من أي وقت مضى. إحدى الطرق لضمان سلامة وصحة مستنداتك هي إضافة علامات مائية. تعد Groupdocs.Watermark for .NET أداة استثنائية مصممة لتسهيل هذه العملية. في هذا البرنامج التعليمي، سنرشدك خلال خطوات إضافة علامة مائية مع نوع هامش الصفحة في ملف PDF باستخدام Groupdocs.Watermark for .NET.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:
-  Groupdocs.Watermark لـ .NET: قم بتنزيل وتثبيت[احدث اصدار](https://releases.groupdocs.com/Watermark/net/) من Groupdocs.علامة مائية لـ .NET.
- بيئة التطوير: بيئة تطوير .NET مثل Visual Studio.
- المعرفة الأساسية بـ C#: الإلمام بلغة البرمجة C#.
- مستند PDF: مستند PDF الذي تريد إضافة علامة مائية إليه.
## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك. ستوفر مساحات الأسماء هذه إمكانية الوصول إلى وظائف Groupdocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
الآن، دعونا نقسم العملية إلى خطوات يمكن التحكم فيها. اتبع كل خطوة بعناية لإضافة علامة مائية إلى مستند PDF الخاص بك.
## الخطوة 1: قم بإعداد مسار المستند ودليل الإخراج
أولاً، ستحتاج إلى تحديد المسار إلى المستند الخاص بك ودليل الإخراج حيث سيتم حفظ ملف PDF ذو العلامة المائية.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## الخطوة 2: قم بتحميل مستند PDF الخاص بك
 بعد ذلك، ستقوم بتحميل مستند PDF الخاص بك باستخدام الملف`PdfLoadOptions` فصل. تتيح لك هذه الفئة تحديد أي خيارات مطلوبة لتحميل ملف PDF الخاص بك.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## الخطوة 3: إنشاء العلامة المائية النصية
الآن، حان الوقت لإنشاء العلامة المائية. في هذا المثال، سنقوم بإنشاء علامة مائية نصية بخصائص محددة مثل الخط والحجم والمحاذاة.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## الخطوة 4: تعيين نوع هامش الصفحة
 لوضع العلامة المائية الخاصة بك بشكل مناسب، ستحتاج إلى تعيين نوع هامش الصفحة. هنا، قمنا بتعيين نوع هامش الصفحة على`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## الخطوة 5: إضافة وحفظ العلامة المائية
أخيرًا، أضف العلامة المائية إلى مستندك واحفظ ملف PDF المعدل في دليل الإخراج المحدد.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## خاتمة
وهناك لديك! باتباع هذه الخطوات، يمكنك بسهولة إضافة علامة مائية بنوع هامش صفحة محدد إلى مستندات PDF الخاصة بك باستخدام Groupdocs.Watermark for .NET. لا يساعد هذا في حماية مستنداتك فحسب، بل يضمن أيضًا صحتها. سواء كنت تتعامل مع تقارير سرية أو مستندات قانونية أو أعمال إبداعية، فإن العلامة المائية هي طريقة بسيطة ولكنها فعالة لحماية المحتوى الخاص بك.
## الأسئلة الشائعة
### ما هي العلامة المائية Groupdocs.Net لـ .NET؟
تعد Groupdocs.Watermark for .NET مكتبة قوية لإضافة علامات مائية إلى تنسيقات المستندات المختلفة برمجيًا. وهو يدعم الصور والنصوص والمزيد، مما يسمح بالتخصيص الشامل.
### هل يمكنني استخدام هذه الطريقة لوضع علامة مائية على أنواع المستندات الأخرى؟
نعم، تدعم Groupdocs.Watermark for .NET نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك Word وExcel وPowerPoint والصور. العملية متشابهة ولكنها قد تتضمن خيارات وفئات مختلفة.
### كيف يمكنني الحصول على نسخة تجريبية مجانية من Groupdocs.Watermark لـ .NET؟
 أنت تستطيع[قم بتنزيل نسخة تجريبية مجانية](https://releases.groupdocs.com/) من موقع Groupdocs الإلكتروني لاستكشاف ميزات المكتبة ووظائفها.
### هل من الممكن تخصيص مظهر العلامة المائية؟
قطعاً! يمكنك تخصيص الخط والحجم واللون والتعتيم والمحاذاة والخصائص الأخرى للعلامة المائية لتناسب احتياجاتك.
### أين يمكنني الحصول على دعم لـ Groupdocs.Watermark لـ .NET؟
 للحصول على الدعم، يمكنك زيارة[منتدى دعم العلامة المائية Groupdocs](https://forum.groupdocs.com/c/watermark/19) حيث يمكنك طرح الأسئلة والحصول على المساعدة من المجتمع وفريق Groupdocs.