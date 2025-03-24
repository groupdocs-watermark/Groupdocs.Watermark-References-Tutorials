---
title: استخراج معلومات التعليق التوضيحي من PDF
linktitle: استخراج معلومات التعليق التوضيحي من PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية استخراج معلومات التعليقات التوضيحية من مستندات PDF باستخدام GroupDocs.Watermark لـ .NET في هذا الدليل المفصل خطوة بخطوة.
weight: 23
url: /ar/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# استخراج معلومات التعليق التوضيحي من PDF

## مقدمة
هل تجد نفسك غالبًا بحاجة إلى استخراج معلومات توضيحية مفصلة من مستندات PDF الخاصة بك؟ سواء كنت مطورًا يعمل على أنظمة إدارة المستندات أو محترفًا في مجال الأعمال يتعامل مع العديد من ملفات PDF، فقد يكون استخراج التعليقات التوضيحية ومعالجتها بكفاءة أمرًا بالغ الأهمية. باستخدام GroupDocs.Watermark for .NET، لديك مجموعة أدوات قوية تحت تصرفك لجعل هذه المهمة واضحة وفعالة.
## المتطلبات الأساسية
قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:
1. Visual Studio: تأكد من تثبيت Visual Studio. سيكون هذا هو بيئة التطوير المتكاملة الخاصة بنا لكتابة التعليمات البرمجية وتشغيلها.
2.  GroupDocs.Watermark لـ .NET: يجب أن يكون لديك GroupDocs.Watermark لمكتبة .NET. أنت تستطيع[قم بتنزيله هنا](https://releases.groupdocs.com/Watermark/net/).
3. المعرفة الأساسية بـ C#: الإلمام ببرمجة C# ضروري للمتابعة مع الأمثلة.
## استيراد مساحات الأسماء
للبدء، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروعك. تحتوي مساحات الأسماء هذه على الفئات والأساليب المطلوبة للعمل مع ملفات PDF واستخراج التعليقات التوضيحية.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## الخطوة 1: قم بإعداد مشروعك
أولاً، لنقم بإعداد مشروعنا في Visual Studio. قم بإنشاء مشروع جديد لتطبيق Console (.NET Core). بمجرد إنشاء مشروعك، تحتاج إلى إضافة مرجع إلى GroupDocs.Watermark لمكتبة .NET.
1. افتح مدير الحزم NuGet.
2.  بحث عن`GroupDocs.Watermark`.
3.  تحميل هذا`GroupDocs.Watermark` طَرد.
## الخطوة 2: تحديد مسارات الوثيقة
بعد ذلك، ستحتاج إلى تحديد المسارات لمستند PDF المدخل الخاص بك ودليل الإخراج حيث سيتم حفظ المعلومات المستخرجة. وهذا يضمن أن تطبيقك يعرف مكان العثور على ملف PDF ومكان تخزين النتائج.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## الخطوة 3: قم بتحميل مستند PDF
 للعمل مع مستند PDF، نحتاج إلى تحميله باستخدام`PdfLoadOptions`. توفر هذه الفئة خيارات لتكوين عملية التحميل.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع رمز استخراج التعليقات التوضيحية هنا
}
```
## الخطوة 4: الوصول إلى محتوى PDF
بمجرد تحميل المستند، يمكننا الوصول إلى محتواه. على وجه التحديد، نريد الحصول على محتوى PDF حتى نتمكن من تكرار الصفحات والشروح.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## الخطوة 5: التكرار عبر الصفحات والشروح
مع وجود محتوى PDF في متناول اليد، يمكننا التكرار خلال كل صفحة ثم من خلال كل تعليق توضيحي على تلك الصفحات. وهذا يسمح لنا باستخراج المعلومات التي نحتاجها.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // استخراج تفاصيل الشرح هنا
    }
}
```
## الخطوة 6: استخراج تفاصيل التعليق التوضيحي
داخل الحلقات المتداخلة، نستخرج تفاصيل مختلفة حول كل تعليق توضيحي. يتضمن ذلك نوع التعليق التوضيحي وأي صور ونصوص وبيانات موضعية مرتبطة به.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## الخطوة 7: حفظ البيانات المستخرجة أو معالجتها
أخيرًا، قرر ما تريد فعله بمعلومات التعليقات التوضيحية المستخرجة. يمكنك طباعته على وحدة التحكم، أو حفظه في ملف، أو حتى تخزينه في قاعدة بيانات، حسب احتياجاتك.
```csharp
// مثال على حفظ البيانات المستخرجة في ملف
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## خاتمة
يعد استخراج معلومات التعليقات التوضيحية من مستندات PDF باستخدام GroupDocs.Watermark لـ .NET عملية مباشرة يمكن أن توفر لك الكثير من الوقت والجهد. باتباع الخطوات الموضحة في هذا الدليل، يمكنك بسهولة دمج هذه الوظيفة في مشاريعك وأتمتة استخراج بيانات التعليقات التوضيحية القيمة.
 سواء كنت تدير كميات كبيرة من ملفات PDF أو تحتاج ببساطة إلى استخراج معلومات محددة، فإن GroupDocs.Watermark for .NET يوفر حلاً موثوقًا وفعالاً. لا تنسى التحقق من[توثيق](https://tutorials.groupdocs.com/Watermark/net/) لمزيد من الميزات المتقدمة وخيارات التخصيص.
## الأسئلة الشائعة
### ما هي العلامة المائية GroupDocs.Net لـ .NET؟
GroupDocs.Watermark for .NET هي مكتبة شاملة تسمح للمطورين بإضافة العلامات المائية والبحث فيها وإزالتها من تنسيقات المستندات المختلفة، بما في ذلك ملفات PDF ومستندات Word والصور.
### هل يمكنني تجربة GroupDocs.Watermark مجانًا؟
 نعم يمكنك الحصول على[تجربة مجانية](https://releases.groupdocs.com/) لاختبار ميزات المكتبة قبل إجراء عملية الشراء.
### كيف يمكنني الحصول على الدعم إذا واجهت مشكلات؟
 يمكنك الحصول على الدعم من فريق GroupDocs من خلال زيارتهم[منتدى الدعم](https://forum.groupdocs.com/c/watermark/19).
### هل من الممكن الحصول على ترخيص مؤقت للاختبار؟
 نعم يمكنك طلب أ[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)لأغراض تجريبية.
### أين يمكنني شراء الإصدار الكامل من GroupDocs.Watermark لـ .NET؟
 يمكنك شراء النسخة الكاملة من[موقع مستندات المجموعة](https://purchase.groupdocs.com/buy).