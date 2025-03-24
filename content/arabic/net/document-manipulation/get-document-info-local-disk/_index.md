---
title: احصل على معلومات المستند من القرص المحلي
linktitle: احصل على معلومات المستند من القرص المحلي
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة العلامات المائية وإزالتها واستخراجها في المستندات باستخدام GroupDocs للعلامة المائية لـ .NET باستخدام هذا الدليل الشامل خطوة بخطوة.
weight: 11
url: /ar/net/document-manipulation/get-document-info-local-disk/
---
## مقدمة
مرحبًا بك في الدليل النهائي حول استخدام GroupDocs.Watermark لـ .NET! سواء كنت مطورًا متمرسًا أو بدأت للتو، سترشدك هذه المقالة إلى أساسيات وضع العلامات المائية على مستنداتك باستخدام هذه الأداة القوية. وفي النهاية، ستكون محترفًا في تضمين العلامات المائية في مستنداتك، مما يضمن حمايتها وعلامتها التجارية وفقًا لمواصفاتك.
## المتطلبات الأساسية
قبل الغوص في الدليل التفصيلي، هناك بعض المتطلبات الأساسية التي يجب عليك استيفائها:
1.  .NET Framework: تأكد من تثبيت .NET Framework على نظامك. تتوافق العلامة المائية GroupDocs.Watermark لـ .NET مع إصدارات مختلفة من .NET Framework، لذا تحقق من[توثيق](https://tutorials.groupdocs.com/Watermark/net/) للحصول على تفاصيل التوافق.
2.  GroupDocs.Watermark لمكتبة .NET: قم بتنزيل أحدث إصدار من .NET وتثبيته[صفحة التحميل](https://releases.groupdocs.com/Watermark/net/).
3. بيئة التطوير: يجب أن يكون لديك بيئة تطوير. يعد Visual Studio خيارًا شائعًا لتطوير .NET.
4. المعرفة الأساسية لـ C#: سيساعدك فهم أساسيات برمجة C# على متابعة الأمثلة.
## استيراد مساحات الأسماء
قبل أن تتمكن من استخدام GroupDocs.Watermark لـ .NET، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروعك. هذه عملية مباشرة وضرورية للوصول إلى ميزات المكتبة.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
دعونا نقسم عملية وضع علامة مائية على المستند إلى خطوات واضحة يمكن التحكم فيها. تم تصميم كل خطوة لمساعدتك على فهم الوظيفة وتنفيذها بسهولة.
## الخطوة 1: قم بتحميل المستند الخاص بك
 الخطوة الأولى هي تحميل المستند الذي تريد وضع علامة مائية عليه. ويتم ذلك باستخدام`Watermarker` class، والذي يسمح لك بالوصول إلى المستند الخاص بك ومعالجته.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // تم الآن تحميل المستند وجاهز لوضع العلامة المائية عليه
}
```
 في هذه الخطوة، استبدل`"Your Document Path"` مع المسار الفعلي إلى المستند الخاص بك. يؤدي هذا إلى تهيئة`Watermarker`الكائن، مما يتيح لك الوصول إلى وظائف العلامات المائية المختلفة.
## الخطوة 2: الحصول على معلومات المستند
قبل إضافة علامة مائية، قد ترغب في جمع بعض المعلومات حول المستند. يمكن أن يكون هذا مفيدًا لتخصيص العلامة المائية الخاصة بك بناءً على خصائص المستند.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 في هذه الخطوة،`GetDocumentInfo` تسترد الطريقة التفاصيل مثل نوع الملف وعدد الصفحات وحجم المستند. تتم طباعة هذه المعلومات على وحدة التحكم، ولكن يمكنك استخدامها في التطبيق الخاص بك حسب الحاجة.
## الخطوة 3: إضافة علامة مائية نصية
الآن بعد أن قمت بتحميل المستند الخاص بك وأصبحت المعلومات الخاصة به في متناول اليد، فقد حان الوقت لإضافة علامة مائية. سنبدأ بعلامة مائية نصية بسيطة.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 هنا تقوم بإنشاء`TextWatermark` كائن بالنص والخط والتصميم المطلوب. اضبط خصائص مثل اللون والعتامة وزاوية التدوير لتناسب احتياجاتك. وأخيرًا، تتم إضافة العلامة المائية إلى المستند وحفظها في المسار المحدد.
## الخطوة 4: إضافة علامة مائية للصورة
العلامات المائية النصية رائعة، ولكن ماذا لو كنت تريد إضافة شعار أو صورة أخرى؟ تغطي هذه الخطوة كيفية إضافة علامة مائية للصورة.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 يستبدل`"Path to Your Image"` مع المسار إلى صورة العلامة المائية الخاصة بك. قم بتعيين خصائص مثل العتامة وزاوية التدوير لتخصيص مظهر العلامة المائية لصورتك. تشبه عملية إضافة العلامة المائية وحفظها عملية العلامة المائية النصية.
## الخطوة 5: إزالة العلامات المائية الموجودة
 في بعض الأحيان، قد تحتاج إلى إزالة العلامات المائية الموجودة من المستند. ويمكن القيام بذلك باستخدام`Remove` الطريقة المقدمة من`Watermarker` فصل.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 هنا،`Remove` يتم استخدام الطريقة لإزالة العلامات المائية النصية من المستند. يمكنك تحديد أنواع مختلفة من العلامات المائية المراد إزالتها، مثل الصورة أو النص، حسب احتياجاتك. احفظ المستند في مسار جديد لرؤية التغييرات.
## الخطوة 6: استخراج العلامات المائية
إذا كنت بحاجة إلى استخراج العلامات المائية وفحصها من مستند ما، فإن GroupDocs.Watermark for .NET يجعل ذلك ممكنًا بسهولة.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // خصائص ومنطق إضافي لكل علامة مائية
    }
}
```
 تتضمن هذه الخطوة استخدام`GetWatermarks`طريقة لاسترداد كافة العلامات المائية في مستند. يمكنك بعد ذلك مراجعة قائمة العلامات المائية وفحص خصائصها أو تنفيذ إجراءات إضافية حسب الحاجة.
## خاتمة
 تهانينا! لقد تعلمت الآن كيفية استخدام GroupDocs.Watermark لـ .NET لإضافة العلامات المائية وإزالتها واستخراجها من مستنداتك. باستخدام هذه المهارات، يمكنك حماية مستنداتك وعلامتها التجارية بشكل فعال. تذكر[توثيق](https://tutorials.groupdocs.com/Watermark/net/) موجود دائمًا إذا كنت بحاجة إلى معلومات أكثر تفصيلاً أو وظائف متقدمة.
## الأسئلة الشائعة
### هل يمكنني استخدام GroupDocs.Watermark لـ .NET مع أي إصدار .NET؟
 نعم، GroupDocs.Watermark for .NET متوافق مع إصدارات .NET Framework المختلفة. افحص ال[توثيق](https://tutorials.groupdocs.com/Watermark/net/) للحصول على تفاصيل.
### أين يمكنني تنزيل GroupDocs.Watermark لـ .NET؟
 يمكنك تنزيل أحدث إصدار من[صفحة التحميل](https://releases.groupdocs.com/Watermark/net/).
### كيف أحصل على ترخيص مؤقت؟
 يمكنك الحصول على ترخيص مؤقت من[صفحة الترخيص المؤقتة](https://purchase.groupdocs.com/temporary-license/).
### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم، يمكنك بدء نسخة تجريبية مجانية من خلال زيارة الموقع[صفحة تجريبية مجانية](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 الدعم متاح على[منتدى العلامات المائية لـ GroupDocs](https://forum.groupdocs.com/c/watermark/19).