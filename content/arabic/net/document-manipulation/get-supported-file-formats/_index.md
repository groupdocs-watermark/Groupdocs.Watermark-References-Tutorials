---
title: احصل على تنسيقات الملفات المدعومة
linktitle: احصل على تنسيقات الملفات المدعومة
second_title: GroupDocs.Watermark .NET API
description: أضف علامات مائية إلى مستنداتك بسهولة باستخدام GroupDocs.Watermark لـ .NET. اتبع دليلنا الشامل خطوة بخطوة لحماية أصولك الرقمية.
type: docs
weight: 13
url: /ar/net/document-manipulation/get-supported-file-formats/
---
## مقدمة
تعد العلامة المائية لمستنداتك خطوة حاسمة في حماية أصولك الرقمية. سواء كان الأمر يتعلق بحماية الملكية الفكرية، أو ضمان السرية، أو مجرد وضع علامة تجارية، فإن العلامات المائية تلعب دورًا حيويًا. إذا كنت أحد مطوري .NET وتتطلع إلى دمج إمكانيات وضع العلامات المائية في تطبيقاتك، فإن GroupDocs.Watermark for .NET هي أداة قوية ومتعددة الاستخدامات يجب عليك وضعها في الاعتبار. سيرشدك هذا البرنامج التعليمي إلى أساسيات استخدام GroupDocs.Watermark، بدءًا من التثبيت وحتى تطبيق العلامة المائية الأولى، مع تفصيل كل خطوة للتأكد من أنه يمكنك المتابعة بسهولة.
## المتطلبات الأساسية
قبل أن نتعمق في التفاصيل، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:
1.  Visual Studio: تأكد من تثبيت Visual Studio على جهازك. يمكنك تنزيله من[موقع فيجوال ستوديو](https://visualstudio.microsoft.com/).
2. .NET Framework: يدعم GroupDocs.Watermark إصدارات مختلفة من .NET Framework. تأكد من أن مشروعك يستهدف إصدارًا متوافقًا.
3. GroupDocs.Watermark لـ .NET: يمكنك تنزيل أحدث إصدار من[صفحة الإصدار](https://releases.groupdocs.com/Watermark/net/).
4. المعرفة الأساسية بـ C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لتطوير C# و.NET.
## استيراد مساحات الأسماء
أولاً، لنستورد مساحات الأسماء الضرورية في مشروعك. افتح ملف C# الخاص بك وأضف ما يلي باستخدام التوجيهات في الأعلى:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
مع استيراد مساحات الأسماء هذه، أنت جاهز لبدء إضافة علامات مائية إلى مستنداتك.

## الخطوة 1: تهيئة محرك العلامات المائية
 الخطوة الأولى هي تهيئة محرك العلامات المائية. يتضمن ذلك إنشاء مثيل لـ`Watermarker` فئة مع المستند الذي تريد وضع علامة مائية عليه.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 يقوم مقتطف الكود هذا بإعداد`Watermarker` الكائن الذي ستستخدمه لتطبيق العلامات المائية على المستند الخاص بك.
## الخطوة 2: إضافة علامة مائية نصية
الآن، دعونا نضيف علامة مائية نصية بسيطة إلى المستند الخاص بك. تعتبر العلامات المائية النصية رائعة لإضافة تسميات مثل "سري" أو "مسودة".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 هنا، قمنا بإنشاء`TextWatermark`كائن يحتوي على النص "سري"، وقم بتعيين خطه ولونه، ثم قم بمحاذاته في منتصف المستند.
## الخطوة 3: إضافة علامة مائية للصورة
إذا كنت تفضل استخدام صورة كعلامة مائية، فإن GroupDocs.Watermark تجعل من السهل القيام بذلك.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 في هذا المثال، نقوم بإنشاء`ImageWatermark` الكائن، وقم بتعيين أبعاده، ثم قم بمحاذاته في الزاوية العلوية اليمنى من المستند.
## الخطوة 4: احفظ المستند
بعد إضافة العلامات المائية المطلوبة، فإن الخطوة الأخيرة هي حفظ المستند المعدل.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 سيؤدي هذا إلى حفظ المستند الذي يحمل العلامة المائية في المسار المحدد وتحرير أي موارد يستخدمها`Watermarker` مثال.
## الخطوة 5: الحصول على تنسيقات الملفات المدعومة
لمعرفة تنسيقات الملفات التي يدعمها GroupDocs.Watermark، يمكنك استخدام مقتطف التعليمات البرمجية التالي:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
سيؤدي هذا إلى طباعة جميع أنواع الملفات التي يمكن لـ GroupDocs.Watermark التعامل معها، مما يمنحك رؤية شاملة لإمكانياتها.
## خاتمة
يعد وضع العلامات المائية على مستنداتك باستخدام GroupDocs للعلامة المائية لـ .NET أمرًا مباشرًا وفعالاً. باتباع هذا البرنامج التعليمي، تعلمت كيفية تهيئة محرك العلامات المائية، وإضافة علامات مائية نصية وصورية، وحفظ المستندات التي تحمل علامة مائية، وقائمة تنسيقات الملفات المدعومة. باستخدام هذه الأدوات، يمكنك حماية مستنداتك بكل ثقة.
 إذا كان لديك أي أسئلة أو كنت بحاجة إلى مزيد من المساعدة، فلا تتردد في زيارة[منتدى دعم GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## الأسئلة الشائعة
### كيف أقوم بتثبيت GroupDocs.Watermark لـ .NET؟
 يمكنك تنزيله من[صفحة الإصدار](https://releases.groupdocs.com/Watermark/net/) وأضف DLL إلى مشروعك.
### هل يمكنني تجربة GroupDocs.Watermark مجانًا؟
 نعم يمكنك طلب أ[تجربة مجانية](https://releases.groupdocs.com/) لتقييم البرنامج قبل الشراء.
### ما تنسيقات الملفات التي يدعمها GroupDocs.Watermark؟
يمكنك استخدام مقتطف التعليمات البرمجية المقدم لسرد جميع تنسيقات الملفات المدعومة.
### كيف يمكنني شراء ترخيص GroupDocs.Watermark؟
 يمكن شراء التراخيص مباشرة من[صفحة الشراء](https://purchase.groupdocs.com/buy).
### هل هناك أي وثائق متاحة لـ GroupDocs.Watermark؟
 نعم، الوثائق الشاملة متاحة[هنا](https://reference.groupdocs.com/Watermark/net/).