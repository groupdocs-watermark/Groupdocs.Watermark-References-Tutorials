---
title: إضافة علامات مائية إلى PDF
linktitle: إضافة علامات مائية إلى PDF
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية نصية وصورية إلى ملفات PDF الخاصة بك باستخدام GroupDocs.Watermark لـ .NET من خلال دليلنا الشامل خطوة بخطوة.
type: docs
weight: 14
url: /ar/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## مقدمة
هل تتطلع إلى إضافة علامات مائية إلى ملفات PDF الخاصة بك لحماية مستنداتك أو تمييزها بشعارك؟ لا مزيد من البحث! في هذا البرنامج التعليمي، سنتعمق في عملية استخدام GroupDocs.Watermark لـ .NET لإضافة علامات مائية نصية وصورية إلى ملفات PDF الخاصة بك. سواء كنت مطورًا متمرسًا أو بدأت للتو، سيرشدك هذا الدليل خلال كل خطوة، مما يضمن أنه يمكنك تطبيق العلامات المائية بسهولة ودقة.
## المتطلبات الأساسية
قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاج إلى متابعته مع هذا البرنامج التعليمي:
-  GroupDocs.Watermark لـ .NET: تأكد من تثبيت أحدث إصدار. أنت تستطيع[قم بتنزيله هنا](https://releases.groupdocs.com/Watermark/net/).
- بيئة تطوير .NET: Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم .NET.
- المعرفة الأساسية بـ C#: إن فهم أساسيات برمجة C# سيساعدك على اتباع الخطوات بسهولة.
- مستند PDF: احصل على نموذج مستند PDF جاهز للعلامة المائية.
- صورة للعلامة المائية: إذا كنت تضيف علامة مائية مصورة، فاحرص على تجهيز ملف الصورة الخاص بك.
## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك. سيسمح لك هذا بالوصول إلى وظيفة GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
الآن، دعونا نقسم العملية إلى خطوات يمكن التحكم فيها.
## الخطوة 1: قم بتحميل مستند PDF الخاص بك
الخطوة الأولى هي تحميل مستند PDF الخاص بك في العلامة المائية. وإليك كيف يمكنك القيام بذلك:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم إضافة المزيد من الخطوات هنا
}
```
## الخطوة 2: إضافة علامة مائية نصية إلى الصفحة الأولى
بعد ذلك، سنقوم بإضافة علامة مائية نصية إلى الصفحة الأولى من ملف PDF الخاص بك. اتبع هذه التعليمات:
```csharp
// أضف علامة مائية نصية إلى الصفحة الأولى
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

يمكن أن تساعد إضافة علامة مائية نصية في حماية مستندك من الاستخدام غير المصرح به أو ببساطة وضع علامة تجارية عليه. تخيل أنك تقوم بختم مستندك بختم أصالة غير مرئي.
## الخطوة 3: إضافة علامة مائية للصورة إلى الصفحة الثانية
الآن، دعونا نضيف صورة مائية للصفحة الثانية. وهذا مفيد بشكل خاص للشعارات أو أي علامات مائية رسومية.
```csharp
// أضف علامة مائية للصورة إلى الصفحة الثانية
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

يمكن للعلامات المائية المصورة أن تجعل مستنداتك تبدو احترافية وتضمن ظهور علامتك التجارية دائمًا. إنه مثل إضافة توقيعك إلى كل صفحة.
## الخطوة 4: احفظ ملف PDF الذي يحمل علامة مائية
بعد إضافة العلامات المائية، فإن الخطوة الأخيرة هي حفظ ملف PDF الذي يحمل العلامة المائية في الموقع الذي تريده.
```csharp
watermarker.Save(outputFileName);
```
يؤدي حفظ المستند إلى إنهاء كافة التغييرات التي أجريتها. هذه هي اللحظة التي تتعزز فيها جهودك وتتحول إلى نتيجة ملموسة، جاهزة للاستخدام أو التوزيع.
## خاتمة
تهانينا! لقد نجحت في إضافة علامات مائية نصية وصورية إلى ملف PDF الخاص بك باستخدام GroupDocs.Watermark لـ .NET. هذه العملية ليست واضحة ومباشرة فحسب، بل إنها أيضًا قابلة للتخصيص بدرجة كبيرة لتناسب احتياجاتك الخاصة. سواء كنت تحمي مستنداتك أو تضع علامة تجارية عليها، فإن العلامات المائية هي أداة قوية تحت تصرفك.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية متعددة إلى نفس الصفحة؟
 نعم، يمكنك إضافة علامات مائية متعددة إلى نفس الصفحة عن طريق الاتصال بـ`Add` الطريقة عدة مرات باستخدام كائنات علامة مائية مختلفة.
### كيف يمكنني تخصيص مظهر العلامة المائية النصية؟
 يمكنك تخصيص العلامة المائية النصية عن طريق ضبط خصائص مثل الخط والحجم واللون والعتامة باستخدام`TextWatermark` هدف.
### هل من الممكن وضع علامة مائية على صفحات محددة فقط من ملف PDF؟
 نعم، يمكنك تحديد الصفحات التي سيتم وضع علامة مائية عليها عن طريق تعيين`PageIndex` الممتلكات في`PdfArtifactWatermarkOptions`.
### هل يمكنني إزالة العلامات المائية من ملف PDF؟
نعم، يوفر GroupDocs.Watermark وظيفة للبحث عن العلامات المائية وإزالتها من مستندات PDF.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Watermark؟
يمكنك الحصول على ترخيص مؤقت بزيارة[صفحة الترخيص المؤقتة](https://purchase.groupdocs.com/temporary-license/).