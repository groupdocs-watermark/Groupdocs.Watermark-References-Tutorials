---
title: أضف علامة مائية مقفلة إلى صفحات محددة في مستندات Word
linktitle: أضف علامة مائية مقفلة إلى صفحات محددة في مستندات Word
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامة مائية مقفلة إلى صفحات محددة في مستندات Word باستخدام GroupDocs.Watermark لـ .NET من خلال دليلنا السهل خطوة بخطوة.
weight: 12
url: /ar/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# أضف علامة مائية مقفلة إلى صفحات محددة في مستندات Word

## مقدمة
هل تتطلع إلى إضافة علامة مائية إلى صفحات محددة في مستندات Word الخاصة بك، ولكنك تريد قفلها بحيث لا يمكن إزالتها أو تحريرها بسهولة؟ أنت في المكان الصحيح! في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة علامة مائية مقفلة إلى صفحات محددة في مستندات Word باستخدام GroupDocs.Watermark لـ .NET. تسهل هذه المكتبة القوية تطبيق العلامات المائية وإدارتها وتخصيصها على مجموعة متنوعة من أنواع المستندات. سواء كنت مطورًا أو مجرد شخص يحتاج إلى تأمين مستنداته، فسيرشدك هذا الدليل خلال كل خطوة بطريقة مباشرة.
## المتطلبات الأساسية
قبل أن نتعمق في البرنامج التعليمي، دعونا نتأكد من أن لديك كل ما تحتاجه:
1.  GroupDocs.علامة مائية لـ .NET: يمكنك ذلك[تحميل](https://releases.groupdocs.com/Watermark/net/) الاصدار الاخير.
2. بيئة التطوير: بيئة تطوير متكاملة (IDE) مثل Visual Studio.
3. المعرفة الأساسية بـ C#: الإلمام ببرمجة C# سيكون مفيدًا.
4. مستند إلى علامة مائية: مستند Word (.docx أو .doc) الذي تريد إضافة علامة مائية إليه.
## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك. توفر مساحات الأسماء هذه إمكانية الوصول إلى الفئات والأساليب المطلوبة للعمل مع GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
الآن بعد أن انتهينا من تغطية المتطلبات الأساسية واستيراد مساحات الأسماء الضرورية، دعنا نقسم العملية خطوة بخطوة.
## الخطوة 1: قم بتحميل مستند Word
 للبدء، تحتاج إلى تحميل مستند Word الذي تريد إضافة علامة مائية إليه. ويمكن القيام بذلك باستخدام`Watermarker` الطبقة جنبا إلى جنب`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // تابع إلى الخطوات التالية
}
```
## الخطوة 2: إنشاء العلامة المائية النصية
بعد ذلك، قم بإنشاء علامة مائية نصية. يمكنك تخصيص النص والخط واللون والخصائص الأخرى وفقًا لمتطلباتك.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## الخطوة 3: تكوين خيارات العلامة المائية
 لتطبيق العلامة المائية على صفحات معينة وقفلها، قم بتكوين`WordProcessingWatermarkPagesOptions`هنا، يمكنك تحديد أرقام الصفحات التي يجب أن تظهر فيها العلامة المائية وضبط خيارات القفل.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // تحديد الصفحات
options.IsLocked = true; // قفل العلامة المائية
options.LockType = WordProcessingLockType.AllowOnlyComments; // ضبط نوع القفل
// للحماية بكلمة مرور
// options.Password = "7654321";
```
## الخطوة 4: أضف العلامة المائية إلى المستند
بعد تكوين العلامة المائية والخيارات، يمكنك الآن إضافة العلامة المائية إلى المستند.
```csharp
watermarker.Add(watermark, options);
```
## الخطوة 5: احفظ المستند
أخيرًا، احفظ المستند مع العلامة المائية المطبقة. اختر مسار الإخراج المناسب واحفظ الملف.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## خاتمة
تهانينا! لقد نجحت في إضافة علامة مائية مقفلة إلى صفحات محددة في مستند Word باستخدام GroupDocs.Watermark لـ .NET. غطى هذا البرنامج التعليمي جميع الخطوات الأساسية بدءًا من تحميل المستند وحتى حفظ الملف الذي يحمل علامة مائية. باتباع هذه الخطوات، يمكنك التأكد من وضع علامة مائية على مستنداتك بشكل آمن، وحماية المحتوى الخاص بك من التحرير والاستخدام غير المصرح به.
 لمزيد من المعلومات، يمكنك الرجوع إلى[وثائق GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . إذا كان لديك أي أسئلة أو كنت بحاجة إلى مزيد من المساعدة، فلا تتردد في زيارة[منتدى الدعم](https://forum.groupdocs.com/c/watermark/19).
## الأسئلة الشائعة
### ما هي العلامة المائية GroupDocs.Net لـ .NET؟
GroupDocs.Watermark for .NET هي مكتبة قوية تسمح للمطورين بإضافة علامات مائية إلى أنواع مختلفة من المستندات، بما في ذلك Word وPDF وExcel والمزيد.
### هل يمكنني تطبيق العلامات المائية على صفحات متعددة في المستند؟
 نعم، يمكنك تحديد أرقام صفحات متعددة في ملف`PageNumbers` مجموعة لتطبيق العلامات المائية على صفحات متعددة.
### كيف يمكنني حماية العلامة المائية بكلمة مرور؟
 يمكنك حماية العلامة المائية بكلمة مرور عن طريق ضبط`Password` الممتلكات في`WordProcessingWatermarkPagesOptions`.
### هل من الممكن تخصيص مظهر العلامة المائية؟
قطعاً! يمكنك تخصيص النص والخط واللون والحجم والخصائص الأخرى للعلامة المائية لتناسب احتياجاتك.
### أين يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Watermark؟
 يمكنك الحصول على ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/).