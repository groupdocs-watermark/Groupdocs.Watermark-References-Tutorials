---
title: إنشاء معاينة المستند
linktitle: إنشاء معاينة المستند
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إنشاء معاينات للمستندات باستخدام GroupDocs.Watermark لـ .NET باستخدام هذا الدليل. قم بتعزيز أمان المستندات وإدارتها دون عناء.
weight: 10
url: /ar/net/document-manipulation/generate-document-preview/
---
## مقدمة
في عالم إدارة المستندات الرقمية، تلعب العلامة المائية دورًا حاسمًا في ضمان أمان المستندات وصحتها. تعد GroupDocs.Watermark for .NET أداة قوية تسمح للمطورين بإضافة علامات مائية إلى المستندات دون عناء. في هذا البرنامج التعليمي، سنرشدك خلال عملية إنشاء معاينات المستندات باستخدام GroupDocs.Watermark لـ .NET. سواء كنت مطورًا متمرسًا أو بدأت للتو، سيوفر لك هذا الدليل عملية شاملة خطوة بخطوة لتحقيق هدفك.
## المتطلبات الأساسية
قبل الغوص في التنفيذ، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:
- فهم أساسي لـ C# و.NET Framework.
- تم تثبيت Visual Studio على جهازك.
- GroupDocs.علامة مائية لمكتبة .NET. أنت تستطيع[قم بتنزيله هنا](https://releases.groupdocs.com/Watermark/net/).
-  ترخيص صالح لـ GroupDocs.Watermark. يمكنك إما شرائه[هنا](https://purchase.groupdocs.com/buy) أو الحصول على[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) لأغراض التقييم.
## استيراد مساحات الأسماء
لبدء استخدام GroupDocs.Watermark في مشروعك، ستحتاج إلى استيراد مساحات الأسماء الضرورية. يمكن القيام بذلك عن طريق إضافة ما يلي باستخدام التوجيهات إلى التعليمات البرمجية الخاصة بك:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
ستوفر مساحات الأسماء هذه إمكانية الوصول إلى الفئات والأساليب المطلوبة لوضع العلامات المائية وإنشاء معاينات للمستندات.

دعنا نقسم عملية إنشاء معاينة المستند إلى خطوات بسيطة وسهلة المتابعة.
## الخطوة 1: قم بإعداد مشروعك
أول الأشياء أولاً، قم بإعداد مشروع .NET الخاص بك في Visual Studio. إذا لم يكن لديك مشروع بالفعل، قم بإنشاء مشروع جديد باتباع الخطوات التالية:
1. افتح فيجوال ستوديو.
2. انقر على "إنشاء مشروع جديد".
3. حدد "تطبيق وحدة التحكم (.NET Core)" وانقر فوق "التالي".
4. قم بتسمية مشروعك واختر موقعًا لحفظه، ثم انقر فوق "إنشاء".
## الخطوة 2: تثبيت GroupDocs.Watermark لـ .NET
لاستخدام GroupDocs.Watermark في مشروعك، تحتاج إلى تثبيت المكتبة. يمكن القيام بذلك باستخدام مدير الحزم NuGet:
1. انقر بزر الماوس الأيمن على مشروعك في Solution Explorer.
2. حدد "إدارة حزم NuGet".
3. ابحث عن "GroupDocs.Watermark" في علامة التبويب "تصفح".
4. انقر فوق "تثبيت" لإضافة المكتبة إلى مشروعك.
وبدلاً من ذلك، يمكنك تثبيته عبر وحدة تحكم إدارة الحزم:
```powershell
Install-Package GroupDocs.Watermark
```
## الخطوة 3: تحديد مسار المستند ودليل الإخراج
قبل إنشاء المعاينة، تحتاج إلى تحديد مسار المستند الذي تريد معاينته والدليل الذي سيتم حفظ صور المعاينة فيه:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
استبدل "مسار المستند الخاص بك" بالمسار إلى المستند الخاص بك و"دليل المستندات الخاص بك" بالدليل الذي تريد حفظ صور المعاينة فيه.
## الخطوة 4: تهيئة كائن العلامة المائية
إنشاء مثيل لـ`Watermarker` فئة عن طريق تمرير مسار الوثيقة إلى منشئها. سيتم استخدام هذا الكائن لتنفيذ جميع عمليات وضع العلامات المائية:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // الرمز الخاص بك هنا
}
```
## الخطوة 5: إنشاء أساليب التفويض لمعالجة الدفق
لإنشاء المعاينة، تحتاج إلى تحديد طرق التفويض لإنشاء التدفقات وإصدارها. ستتعامل هذه التوابع مع إنشاء وإصدار التدفقات لكل صفحة من المستند:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 ال`createPageStreamDelegate` تقوم الطريقة بإنشاء دفق لكل صفحة من المستند، بينما تقوم الطريقة`releasePageStreamDelegate` تغلق الطريقة الدفق بعد إنشاء المعاينة.
## الخطوة 6: تكوين خيارات المعاينة
 بعد ذلك، قم بتكوين خيارات المعاينة عن طريق إنشاء مثيل لـ`PreviewOptions` فصل. حدد طرق التفويض واضبط تنسيق المعاينة على PNG. يمكنك أيضًا تحديد الصفحات التي سيتم تضمينها في المعاينة:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
في هذا المثال، نقوم بإنشاء معاينات للصفحتين الأوليين من المستند.
## الخطوة 7: إنشاء معاينة المستند
 وأخيرا اتصل ب`GeneratePreview` الطريقة على`Watermarker`الكائن، ويمر في تكوينه`PreviewOptions`. سيؤدي هذا إلى إنشاء صور المعاينة وحفظها في الدليل المحدد:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## خاتمة
يعد إنشاء معاينات المستندات باستخدام GroupDocs.Watermark لـ .NET عملية مباشرة يمكن إنجازها ببضعة أسطر من التعليمات البرمجية فقط. باتباع الخطوات الموضحة في هذا الدليل، يمكنك بسهولة إعداد مشروعك وتكوين الخيارات الضرورية وإنشاء معاينات لمستنداتك. لا تعمل هذه المكتبة القوية على تبسيط عملية وضع العلامات المائية فحسب، بل توفر أيضًا ميزات قوية لإدارة العلامات المائية ومعالجتها.
 إذا كان لديك أي أسئلة أو كنت بحاجة إلى مزيد من المساعدة، فلا تتردد في زيارة[منتدى دعم GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) أو الرجوع إلى[توثيق](https://tutorials.groupdocs.com/Watermark/net/).
## الأسئلة الشائعة
### ما تنسيقات الملفات التي يدعمها GroupDocs.Watermark لـ .NET؟
 يدعم GroupDocs.Watermark for .NET نطاقًا واسعًا من تنسيقات الملفات، بما في ذلك PDF وDOCX وPPTX وXLSX وغيرها الكثير. للحصول على قائمة كاملة بالتنسيقات المدعومة، راجع[توثيق](https://tutorials.groupdocs.com/Watermark/net/).
### هل يمكنني تخصيص مظهر العلامات المائية؟
نعم، تتيح لك GroupDocs.Watermark إمكانية تخصيص مظهر العلامات المائية بشكل كامل، بما في ذلك العلامات المائية النصية والصورة والأشكال. يمكنك ضبط خصائص مثل الخط واللون والحجم والشفافية.
### هل هناك نسخة تجريبية متاحة؟
 نعم يمكنك الحصول على[تجربة مجانية](https://releases.groupdocs.com/) GroupDocs.Watermark لـ .NET لتقييم ميزاته قبل إجراء عملية شراء.
### كيف يمكنني شراء ترخيص لـ GroupDocs.Watermark؟
 يمكنك شراء ترخيص لـ GroupDocs.Watermark[هنا](https://purchase.groupdocs.com/buy). هناك العديد من خيارات الترخيص المتاحة لتناسب الاحتياجات المختلفة.
### هل يمكنني استخدام GroupDocs.Watermark في مشروع تجاري؟
 نعم، بترخيص صالح، يمكنك استخدام GroupDocs.Watermark في المشاريع التجارية. تأكد من مراجعة شروط وأحكام الترخيص على[صفحة الشراء](https://purchase.groupdocs.com/buy).