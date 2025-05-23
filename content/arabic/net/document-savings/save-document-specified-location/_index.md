---
title: احفظ المستند في الموقع المحدد
linktitle: احفظ المستند في الموقع المحدد
second_title: GroupDocs.Watermark .NET API
description: تعرف على كيفية إضافة علامات مائية بسهولة إلى مستنداتك باستخدام GroupDocs.Watermark لـ .NET باستخدام هذا الدليل التفصيلي خطوة بخطوة. تعزيز أمان المستندات.
weight: 11
url: /ar/net/document-savings/save-document-specified-location/
---

# احفظ المستند في الموقع المحدد

## مقدمة
في العصر الرقمي، أصبح تأمين المستندات أكثر أهمية من أي وقت مضى. تعد العلامة المائية طريقة فعالة لحماية مستنداتك من الاستخدام غير المصرح به. يقدم GroupDocs.Watermark for .NET حلاً قويًا لإضافة علامات مائية إلى مستنداتك. سواء كنت مطورًا يتطلع إلى دمج العلامة المائية في تطبيقك أو شخصًا مهتمًا بحماية مستنداتك، فإن هذا البرنامج التعليمي سيرشدك خلال العملية خطوة بخطوة.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:
- بيئة تطوير .NET: تأكد من تثبيت Visual Studio أو أي بيئة تطوير .NET أخرى.
-  GroupDocs.Watermark لمكتبة .NET: قم بتنزيل المكتبة والإشارة إليها في مشروعك.[قم بتنزيل GroupDocs.Watermark لـ .NET](https://releases.groupdocs.com/Watermark/net/)
- المعرفة الأساسية ببرمجة C#: سيكون فهم مفاهيم برمجة C# الأساسية مفيدًا.
- مستند إلى علامة مائية: قم بإعداد نموذج مستند تريد تطبيق العلامة المائية عليه.
## استيراد مساحات الأسماء
قبل أن نبدأ بالمثال، تحتاج إلى استيراد مساحات الأسماء الضرورية. أضف عبارات الاستخدام التالية في أعلى ملف التعليمات البرمجية الخاص بك:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
دعنا نقسم عملية إضافة علامة مائية إلى مستند باستخدام GroupDocs.Watermark لـ .NET إلى خطوات يمكن التحكم فيها. اتبع هذه الخطوات لتطبيق العلامة المائية بنجاح وحفظ المستند في موقع محدد.
## الخطوة 1: قم بإعداد مشروعك
ابدأ بإنشاء مشروع .NET جديد في Visual Studio. يمكنك اختيار تطبيق وحدة التحكم للبساطة.
1. افتح فيجوال ستوديو.
2.  يختار`File` >`New` >`Project`.
3.  يختار`Console App (.NET Core)` أو`Console App (.NET Framework)`.
4.  قم بتسمية مشروعك ثم انقر`Create`.

## الخطوة 2: قم بإعداد المستند ونص العلامة المائية
### تحديد مسار الوثيقة
حدد مسار المستند الذي تريد وضع علامة مائية عليه. في هذا المثال، دعونا نستخدم مسار العنصر النائب.
```csharp
string documentPath = "Your Document Path";
```
### تحديد مسار الإخراج
قم بإعداد مسار الإخراج حيث تريد حفظ المستند الذي يحمل علامة مائية.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## الخطوة 3: قم بتحميل المستند
 استخدم ال`Watermarker` فئة لتحميل المستند الخاص بك. توفر هذه الفئة طرقًا لإضافة العلامات المائية وإزالتها وتحريرها.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // أضف منطق العلامة المائية هنا
}
```
## الخطوة 4: إنشاء وإضافة علامة مائية

### إنشاء علامة مائية نصية
 إنشاء مثيل أ`TextWatermark` الكائن مع خصائص النص والخط المطلوب.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### أضف علامة مائية إلى المستند
 أضف العلامة المائية التي تم إنشاؤها إلى المستند الخاص بك باستخدام`Add` طريقة`Watermarker` فصل.
```csharp
watermarker.Add(watermark);
```
## الخطوة 5: احفظ المستند
وأخيرًا، احفظ المستند الذي يحتوي على العلامة المائية في الموقع المحدد.
```csharp
watermarker.Save(outputFileName);
```
## خاتمة
تعد العلامة المائية لمستنداتك باستخدام GroupDocs Watermark for .NET عملية مباشرة يمكن أن تعزز أمان المستند بشكل كبير. باتباع هذا الدليل التفصيلي، يمكنك بسهولة إضافة علامات مائية إلى مستنداتك وحفظها في الموقع الذي تريده. سواء كنت تحمي الملكية الفكرية، أو تضمن صحة المستند، أو ببساطة تضيف لمسة احترافية، فإن GroupDocs.Watermark for .NET يوفر الأدوات التي تحتاجها.
## الأسئلة الشائعة
### هل يمكنني استخدام الصور كعلامات مائية مع GroupDocs.Watermark لـ .NET؟
نعم، يمكنك استخدام العلامات المائية النصية والصورية مع GroupDocs للعلامة المائية لـ .NET. تدعم المكتبة أنواعًا مختلفة من العلامات المائية لتناسب احتياجاتك.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Watermark لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[موقع إلكتروني](https://releases.groupdocs.com/).
### كيف يمكنني شراء ترخيص GroupDocs.Watermark لـ .NET؟
 يمكنك شراء ترخيص من[صفحة الشراء](https://purchase.groupdocs.com/buy).
### هل تدعم GroupDocs.Watermark لـ .NET العلامة المائية المجمعة؟
نعم، يمكنك وضع علامة مائية على مستندات متعددة في عملية مجمعة من خلال التكرار خلال قائمة المستندات وتطبيق العلامات المائية.
### أين يمكنني الحصول على دعم لـ GroupDocs.Watermark لـ .NET؟
 الدعم متاح على[منتدى مستندات المجموعة](https://forum.groupdocs.com/c/watermark/19).