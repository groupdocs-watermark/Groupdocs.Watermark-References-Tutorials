---
title: إضافة علامة مائية إلى الصور في PDF
linktitle: إضافة علامة مائية إلى الصور في PDF
second_title: GroupDocs.Watermark .NET API
description: تعلم كيفية إضافة علامات مائية إلى الصور في مستندات PDF باستخدام GroupDocs.Watermark لـ .NET من خلال برنامجنا التعليمي المفصل خطوة بخطوة. تأمين ملفات PDF الخاصة بك بسهولة.
weight: 19
url: /ar/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## مقدمة
يمكن أن تكون إضافة علامات مائية إلى الصور داخل مستند PDF أمرًا ضروريًا لحماية ملكيتك الفكرية أو ضمان صحة مستنداتك. باستخدام GroupDocs.Watermark لـ .NET، يمكن تنفيذ هذه المهمة بكفاءة وسهولة. سيرشدك هذا البرنامج التعليمي خلال كل خطوة من خطوات العملية، بدءًا من إعداد البيئة الخاصة بك وحتى إضافة العلامات المائية وحتى حفظ المستند النهائي. دعونا الغوص في!
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. Visual Studio: قم بتثبيت Visual Studio، بيئة التطوير المتكاملة (IDE) لتطبيقات .NET.
2.  GroupDocs.Watermark لـ .NET: قم بتنزيل وتثبيت GroupDocs.Watermark لمكتبة .NET من[صفحة الإصدار](https://releases.groupdocs.com/Watermark/net/).
3. مستند PDF: احصل على مستند PDF يحتوي على صور جاهزة لاختبار وظيفة العلامة المائية.
4.  الترخيص المؤقت: الحصول على أ[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) إذا كنت تقوم بتقييم المنتج.
## استيراد مساحات الأسماء
أولاً، تأكد من استيراد مساحات الأسماء الضرورية إلى مشروعك. سيتضمن ذلك مساحات الأسماء الأساسية المطلوبة للعمل مع مستندات PDF والعلامات المائية.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## الخطوة 1: إعداد مسار المستند ودليل الإخراج
للبدء، حدد المسارات لمستند الإدخال ودليل الإخراج حيث سيتم حفظ المستند الذي تم وضع علامة مائية عليه. تعتبر هذه الخطوة ضرورية للتأكد من أن برنامجك يعرف مكان العثور على المستند المصدر ومكان تخزين الملف المعالج.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## الخطوة 2: قم بتحميل مستند PDF
 بعد ذلك، ستحتاج إلى تحميل مستند PDF باستخدام`PdfLoadOptions`. تسمح لك هذه الفئة بتحديد خيارات تحميل ملف PDF، مثل الحماية بكلمة مرور إذا لزم الأمر.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع رمز العلامة المائية الخاص بك هنا
}
```
## الخطوة 3: إنشاء العلامة المائية
الآن، قم بتهيئة العلامة المائية. في هذا المثال، نقوم بإنشاء علامة مائية نصية نصها "صورة محمية". قم بتخصيص الخط والمحاذاة والتدوير والقياس وفقًا لاحتياجاتك.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## الخطوة 4: الوصول إلى محتوى PDF
استرجع محتوى وثيقة PDF. وعلى وجه التحديد، نحتاج إلى الوصول إلى الصور الموجودة في ملف PDF. نحن نركز هنا على الصفحة الأولى، ولكن يمكنك توسيع ذلك ليشمل صفحات أخرى حسب الحاجة.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// احصل على جميع الصور من الصفحة الأولى
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## الخطوة 5: تطبيق العلامة المائية على الصور
قم بمراجعة كل صورة موجودة في الصفحة الأولى وقم بتطبيق العلامة المائية. وهذا يضمن أن جميع الصور الموجودة على الصفحة المحددة سيتم تطبيق العلامة المائية عليها.
```csharp
// أضف علامة مائية إلى جميع الصور الموجودة
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## الخطوة 6: احفظ المستند الذي يحمل علامة مائية
وأخيرًا، احفظ ملف PDF الذي يحمل علامة مائية في دليل الإخراج المحدد. تُنهي هذه الخطوة العملية عن طريق كتابة التغييرات على ملف جديد.
```csharp
watermarker.Save(outputFileName);
```
## خاتمة
وهناك لديك! تعد إضافة علامة مائية إلى الصور داخل ملف PDF باستخدام GroupDocs Watermark for .NET عملية مباشرة يمكن أن تعزز أمان مستنداتك وصحتها بشكل كبير. باتباع هذه الخطوات، يمكنك التأكد من حماية ملكيتك الفكرية وتأمين مستنداتك.
## الأسئلة الشائعة
### ما هي العلامة المائية GroupDocs.Net لـ .NET؟
GroupDocs.Watermark for .NET هي مكتبة شاملة تسمح للمطورين بإضافة العلامات المائية والبحث فيها وإزالتها في تنسيقات المستندات المختلفة، بما في ذلك ملفات PDF.
### هل يمكنني إضافة علامات مائية نصية وصورية باستخدام GroupDocs.Watermark؟
نعم، يدعم GroupDocs.Watermark كلا من العلامات المائية النصية والصورية، مما يوفر المرونة لأنواع مختلفة من احتياجات العلامات المائية.
### هل من الممكن وضع علامة مائية على صفحات متعددة في ملف PDF؟
قطعاً! يمكنك تكرار كل صفحة في ملف PDF وتطبيق العلامات المائية على الصور في كل صفحة.
### هل أحتاج إلى ترخيص لاستخدام GroupDocs.Watermark لـ .NET؟
 نعم، الترخيص مطلوب. يمكنك الحصول على[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) لأغراض التقييم.
### أين يمكنني العثور على مزيد من الوثائق حول GroupDocs.Watermark لـ .NET؟
 يمكنك العثور على وثائق شاملة عن[صفحة وثائق GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).