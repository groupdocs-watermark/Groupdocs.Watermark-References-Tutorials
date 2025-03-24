---
title: استخراج كافة المرفقات من PDF
linktitle: استخراج كافة المرفقات من PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية استخراج جميع المرفقات من ملف PDF باستخدام Groupdocs.Watermark لـ .NET. اتبع دليلنا خطوة بخطوة للحصول على عملية استخراج سلسة.
weight: 22
url: /ar/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---
## مقدمة
هل تتطلع إلى استخراج المرفقات من مستند PDF دون عناء؟ حسنا، أنت في المكان الصحيح! في هذا البرنامج التعليمي الشامل، سنرشدك خلال عملية استخراج جميع المرفقات من ملف PDF باستخدام Groupdocs.Watermark for .NET. تسمح هذه المكتبة القوية للمطورين بإدارة العلامات المائية بتنسيقات المستندات المختلفة، ولكنها تتضمن أيضًا إمكانات قوية لاستخراج الملفات المضمنة. سواء كنت مطورًا متمرسًا أو بدأت للتو، فإن هذا الدليل المفصّل خطوة بخطوة سيجعل العملية سهلة.
## المتطلبات الأساسية
قبل الغوص في التعليمات البرمجية، دعنا نغطي الأساسيات التي ستحتاج إليها للبدء. فيما يلي قائمة مرجعية سريعة للتأكد من أنك مستعد:
1. بيئة .NET: تأكد من إعداد بيئة تطوير .NET. يمكنك استخدام Visual Studio أو أي برنامج .NET IDE آخر من اختيارك.
2.  Groupdocs.Watermark لـ .NET: قم بتنزيل أحدث إصدار من Groupdocs.Watermark لـ .NET وتثبيته من[هنا](https://releases.groupdocs.com/Watermark/net/).
3. مهارات التطوير: الفهم الأساسي لبرمجة C# والإلمام بمكتبات .NET.
4. نموذج مستند PDF: احصل على نموذج مستند PDF مع المرفقات التي يمكنك استخدامها للاختبار.
## استيراد مساحات الأسماء
قبل البدء في البرمجة، ستحتاج إلى استيراد مساحات الأسماء الضرورية. يساعد هذا في تنظيم التعليمات البرمجية الخاصة بك ويمنحك الوصول إلى الفئات والأساليب التي ستستخدمها.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## الخطوة 1: قم بإعداد مشروعك
أول الأشياء أولاً، لنقم بإعداد مشروعك. افتح بيئة تطوير .NET الخاصة بك وقم بإنشاء تطبيق وحدة تحكم جديد.
### إنشاء مشروع جديد
1. افتح فيجوال ستوديو.
2. حدد "إنشاء مشروع جديد".
3. اختر "تطبيق وحدة التحكم (.NET Core)" أو ".NET Framework" حسب تفضيلاتك.
4. قم بتسمية مشروعك وانقر على "إنشاء".
### إضافة Groupdocs.علامة مائية لـ .NET
1. انقر بزر الماوس الأيمن على مشروعك في Solution Explorer.
2. حدد "إدارة حزم NuGet".
3. ابحث عن "Groupdocs.Watermark" وقم بتثبيت أحدث إصدار.
## الخطوة 2: تحديد المسارات الخاصة بك
بعد ذلك، تحتاج إلى تحديد المسارات للمستند ودليل الإخراج. هذا هو المكان الذي سيتم فيه تخزين ملف PDF الخاص بك والمرفقات المستخرجة.

 في الخاص بك`Program.cs` الملف، أضف الكود التالي لتحديد مساراتك:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"` و`"Your Document Directory"` مع المسارات الفعلية على النظام الخاص بك.
## الخطوة 3: قم بتحميل مستند PDF الخاص بك
 الآن، لنقم بتحميل مستند PDF الخاص بك باستخدام Groupdocs.Watermark. تتضمن هذه الخطوة إنشاء خيارات التحميل وتهيئة الملف`Watermarker` فصل.
### إنشاء خيارات التحميل
 أولاً، قم بإنشاء مثيل لـ`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### تهيئة العلامة المائية
 بعد ذلك، استخدم`Watermarker` فئة لتحميل المستند الخاص بك:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع الرمز الخاص بك هنا
}
```
## الخطوة 4: استخراج المرفقات
بعد تحميل المستند، حان الوقت لاستخراج المرفقات. سوف تستخدم`PdfContent` class للوصول إلى المرفقات ثم حفظها في دليل الإخراج المحدد.
### احصل على محتوى PDF
 داخل`using` كتلة، والحصول على محتوى PDF:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### حلقة من خلال المرفقات
قم بالتكرار عبر كل مرفق في ملف PDF:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // احفظ الملف المرفق على القرص
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
يقوم هذا الكود باستخراج كل مرفق وحفظه في دليل الإخراج الخاص بك. كما يقوم أيضًا بطباعة بعض المعلومات الأساسية حول كل مرفق بوحدة التحكم.
## خاتمة
وهناك لديك! لقد نجحت في استخراج المرفقات من ملف PDF باستخدام Groupdocs.Watermark لـ .NET. يرشدك هذا البرنامج التعليمي خلال إعداد مشروعك وتحميل مستندك واستخراج المرفقات خطوة بخطوة. باستخدام هذه المهارات، يمكنك الآن إدارة ومعالجة مرفقات PDF في تطبيقات .NET الخاصة بك بسهولة.
## الأسئلة الشائعة
### ما هي العلامة المائية Groupdocs.Net لـ .NET؟
Groupdocs.Watermark for .NET عبارة عن مكتبة شاملة لإضافة العلامات المائية وإزالتها وإدارتها في تنسيقات المستندات المختلفة، بما في ذلك ملفات PDF. كما يوفر إمكانيات لاستخراج الملفات المضمنة.
### هل يمكنني استخراج أنواع أخرى من الملفات المضمنة في ملف PDF؟
نعم، تسمح لك Groupdocs.Watermark for .NET باستخراج أي نوع من الملفات المضمنة في ملف PDF، وليس فقط المرفقات.
### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من Groupdocs.Watermark لـ .NET من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من خلال زيارة[منتدى دعم Groupdocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### هل أحتاج إلى ترخيص لاستخدام Groupdocs.Watermark لـ .NET؟
 نعم، تحتاج إلى ترخيص لاستخدام المكتبة في الإنتاج. يمكنك شراء ترخيص[هنا](https://purchase.groupdocs.com/buy) أو الحصول على ترخيص مؤقت[هنا](https://purchase.groupdocs.com/temporary-license/).