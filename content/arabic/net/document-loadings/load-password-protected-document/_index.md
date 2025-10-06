---
title: تحميل مستند محمي بكلمة مرور
linktitle: تحميل مستند محمي بكلمة مرور
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية إلى المستندات المحمية بكلمة مرور باستخدام Groupdocs لـ .NET من خلال دليلنا خطوة بخطوة. قم بتأمين ملفاتك وعلامتها التجارية بسهولة.
weight: 13
url: /ar/net/document-loadings/load-password-protected-document/
type: docs
---
# تحميل مستند محمي بكلمة مرور

## مقدمة
هل تتطلع إلى حماية مستنداتك عن طريق إضافة علامات مائية، حتى لو كانت محمية بكلمة مرور؟ تعد Groupdocs.Watermark for .NET أداة قوية تتيح لك القيام بذلك. في هذا البرنامج التعليمي، سنرشدك خلال عملية تحميل مستند محمي بكلمة مرور وإضافة علامة مائية إليه باستخدام Groupdocs.Watermark for .NET. دعونا الغوص في!
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. Visual Studio: أي إصدار من Visual Studio مثبت على جهازك.
2. .NET Framework: تأكد من أن لديك .NET Framework 4.6.1 أو إصدار أحدث.
3. Groupdocs.Watermark لـ .NET: قم بتنزيل وتثبيت Groupdocs.Watermark لمكتبة .NET من[رابط التحميل](https://releases.groupdocs.com/Watermark/net/).
## استيراد مساحات الأسماء
أولاً، نحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروعنا. وهذا يضمن أنه يمكننا الوصول إلى كافة الأساليب والخصائص التي توفرها Groupdocs.Watermark لـ .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
الآن، دعونا نقسم العملية إلى خطوات بسيطة وسهلة المتابعة.
## الخطوة 1: قم بإعداد مشروعك
للبدء، قم بإنشاء تطبيق C# Console جديد في Visual Studio. بمجرد إعداد مشروعك، قم بتثبيت Groupdocs.Watermark لمكتبة .NET عبر NuGet Package Manager.
1. افتح Visual Studio وقم بإنشاء تطبيق وحدة تحكم جديد (.NET Framework).
2.  اذهب إلى`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  بحث عن`GroupDocs.Watermark` وتثبيت الحزمة.
## الخطوة 2: تحديد مسارات الوثيقة
بعد ذلك، ستحتاج إلى تحديد المسار إلى مستندك المحمي بكلمة مرور ومسار ملف الإخراج حيث سيتم حفظ المستند الذي تم وضع علامة مائية عليه.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 يستبدل`"Your Document Path"` و`"Your Document Directory"` مع المسارات الفعلية على جهازك.
## الخطوة 3: ضبط خيارات التحميل بكلمة المرور
لفتح مستند محمي بكلمة مرور، يجب عليك توفير كلمة المرور في خيارات التحميل.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 يستبدل`"P@$w0rd"` بكلمة المرور الفعلية للمستند الخاص بك.
## الخطوة 4: قم بتحميل المستند
 الآن، لنقم بتحميل المستند باستخدام ملف`Watermarker` فصل.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // سيتم وضع الرمز الخاص بك لإضافة العلامة المائية هنا
}
```
## الخطوة 5: إنشاء علامة مائية
سنقوم بإنشاء علامة مائية نصية يمكننا إضافتها إلى المستند. يمكنك تخصيص النص والخط والحجم والخصائص الأخرى حسب الحاجة.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 لا تتردد في التغيير`"Test watermark"`, `"Arial"` ، و`12` إلى النص والخط والحجم المفضل لديك.
## الخطوة 6: إضافة العلامة المائية
 أضف العلامة المائية إلى المستند باستخدام`Add` طريقة`Watermarker` فصل.
```csharp
watermarker.Add(watermark);
```
## الخطوة 7: احفظ المستند الذي يحمل علامة مائية
وأخيرًا، احفظ المستند الذي يحمل علامة مائية في مسار ملف الإخراج المحدد.
```csharp
watermarker.Save(outputFileName);
```
## خاتمة
تعد إضافة علامات مائية إلى مستنداتك المحمية بكلمة مرور عملية مباشرة باستخدام Groupdocs للعلامة المائية لـ .NET. باتباع هذه الخطوات البسيطة، يمكنك التأكد من حماية مستنداتك وتصنيفها وفقًا لمتطلباتك. سواء كان الأمر يتعلق بالأمان أو العلامة التجارية أو الامتثال، فإن وضع العلامات المائية على مستنداتك لم يكن بهذه السهولة من قبل.
## الأسئلة الشائعة
### هل يمكنني إضافة علامات مائية مصورة باستخدام Groupdocs.Watermark لـ .NET؟
 نعم، يمكنك إضافة علامات مائية نصية وصورية. ببساطة استخدم`ImageWatermark` الصف بدلا من`TextWatermark`.
### هل من الممكن إزالة العلامات المائية من المستند؟
نعم، يوفر Groupdocs.Watermark for .NET طرقًا للبحث عن العلامات المائية وإزالتها.
### هل يدعم Groupdocs.Watermark for .NET تنسيقات المستندات الأخرى إلى جانب ملفات PDF؟
نعم، فهو يدعم مجموعة واسعة من التنسيقات بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص مظهر العلامة المائية؟
قطعاً! يمكنك تخصيص الخط والحجم واللون والعتامة والمزيد.
### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك زيارة[منتدى دعم مستندات المجموعة](https://forum.groupdocs.com/c/watermark/19) للمساعدة والتوجيه.