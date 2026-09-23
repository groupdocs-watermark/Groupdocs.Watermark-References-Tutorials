---
date: '2026-02-26'
description: تعلم كيفية استخراج الصور من ملفات PDF باستخدام GroupDocs.Watermark للغة
  Java. يشرح هذا الدليل عملية استخراج الصور، وحفظ صور PDF بصيغة PNG، واستخراج صور
  PDF دفعةً واحدة.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: كيفية استخراج الصور من ملفات PDF باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/pdf-document-watermarking/master-image-search-pdfs-groupdocs-watermark-java/
weight: 1
---

# كيف تستخرج الصور من ملفات PDF باستخدام GroupDocs.Watermark Java

العمل مع ملفات PDF غالبًا ما يعني أنك تحتاج إلى **استخراج الصور** — سواء لإعادة استخدام الرسومات، أو إجراء OCR، أو تطبيق علامات مائية مخصصة. في هذا الدرس ستتعلم **كيفية استخراج الصور** من ملفات PDF بسرعة وموثوقية باستخدام مكتبة GroupDocs.Watermark Java. سنغطي كل شيء بدءًا من إعداد البيئة إلى حفظ كل صورة تم العثور عليها كملف PNG، وسنوضح لك أيضًا كيفية توسيع الحل لاستخراج صور PDF على دفعات.

## إجابات سريعة
- **ماذا يعني “كيفية استخراج الصور”?** يشير إلى تحديد وحفظ الرسومات المدمجة في ملف PDF برمجيًا.  
- **ما هي المكتبة الأفضل لجافا؟** توفر GroupDocs.Watermark واجهة برمجة تطبيقات بسيطة للبحث عن الصور واستخراجها.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يكفي للتطوير؛ يتطلب الترخيص التجاري للإنتاج.  
- **هل يمكنني حفظ الصور بصيغة PNG؟** نعم — استخدم طريقة `save` على كائنات `PdfImage`.  
- **هل المعالجة الدفعة ممكنة؟** بالطبع؛ فقط قم بتكرار المسارات المتعددة للملفات PDF باستخدام نفس الشيفرة.

## ما هو استخراج الصور من ملفات PDF؟
استخراج الصور هو عملية تحديد كل رسمة نقطية أو متجهة مدمجة في مستند PDF وتصديرها إلى ملف صورة منفصل. هذا مفيد لإعادة استخدام المحتوى، أو فحص الجودة، أو إمداد الصور إلى سير عمل لاحق مثل خطوط أنابيب التعلم الآلي.

## لماذا تستخدم GroupDocs.Watermark لجافا؟
- **دقة عالية** – يقوم المحرك بتحليل بنية PDF لتحديد الصور المرفقة والمضمنة.  
- **واجهة برمجة تطبيقات بسيطة** – بضع أسطر من الشيفرة تمكنك من استرجاع مجموعة من كائنات `PdfImage`.  
- **محسّن للأداء** – يعمل جيدًا حتى مع ملفات PDF الكبيرة ومتعددة الصفحات.  
- **قابل للتوسيع** – يمكنك التصفية حسب الحجم أو الصيغة، أو استبدال الصور بعد الاستخراج.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) الإصدار 8 أو أحدث.  
- إضافة GroupDocs.Watermark لـ Java SDK إلى مشروعك (Maven/Gradle أو JAR يدوي).  
- ملف PDF تجريبي يحتوي على رسومات مدمجة.  
- إلمام أساسي بصياغة جافا وتكوين بيئة التطوير المتكاملة (IDE).

## استيراد الحزم المطلوبة
ابدأ باستيراد الفئات الأساسية التي توفرها الواجهة البرمجية:

```java
import com.groupdocs.watermark.domain.PdfSearchableObjects;
import com.groupdocs.watermark.domain.watermarkable.PdfImage;
import com.groupdocs.watermark.domain.watermarkable.WatermarkableImageCollection;
import com.groupdocs.watermark.options.PdfLoadOptions;
import com.groupdocs.watermark.Watermarker;
```

## دليل خطوة بخطوة

### الخطوة 1: تحميل مستند PDF الخاص بك
تحتاج إلى تحميل ملف PDF إلى كائن `Watermarker` قبل أن تتمكن من البحث فيه.

```java
// Specify the path to your PDF
String inputPdfPath = "C:\\Docs\\sample.pdf";

// Initialize load options
PdfLoadOptions loadOptions = new PdfLoadOptions();

// Create Watermarker instance
Watermarker watermarker = new Watermarker(inputPdfPath, loadOptions);
```

> **نصيحة:** تأكد من صحة مسار الملف وأن التطبيق يمتلك أذونات القراءة.

### الخطوة 2: تكوين البحث عن الصور المدمجة أو المرفقة
أخبر المحرك بالبحث فقط عن الصور (متجاهلًا الكائنات الأخرى مثل النص أو التعليقات التوضيحية).

```java
// Set to search only for attached images
watermarker.getSearchableObjects().setPdfSearchableObjects(PdfSearchableObjects.AttachedImages);
```

> **لماذا؟** تركيز البحث يقلل من زمن المعالجة ويعيد مجموعة أنظف.

### الخطوة 3: البحث عن الصور في ملف PDF
استرجع المجموعة الكاملة من الصور التي تطابق المعايير.

```java
// Retrieve all images matching the search criteria
WatermarkableImageCollection images = watermarker.getImages();

// Output the number of images found
System.out.println("Number of images found: " + images.getCount());
```

> **نصيحة احترافية:** يمكنك فحص `images.getCount()` لتقرر ما إذا كان هناك حاجة لمعالجة إضافية.

### الخطوة 4: معالجة الصور المكتشفة – حفظ صور PDF كملفات PNG
الآن بعد أن لديك كائنات `PdfImage`، يمكنك حفظ كل واحدة كملف PNG منفصل — وهو طلب شائع عندما تحتاج إلى **save pdf images png**.

```java
int index = 1;
for (PdfImage image : images) {
    // Save each image as PNG
    image.save("C:\\Output\\Image_" + index + ".png");
    index++;
}
```

> **مشكلة شائعة:** نسيان إنشاء دليل الإخراج سيتسبب في حدوث `IOException`. أنشئ المجلد مسبقًا أو أضف فحصًا في الشيفرة.

### الخطوة 5: إغلاق الموارد
دائمًا حرّر كائن `Watermarker` لتحرير الموارد الأصلية.

```java
watermarker.close();
```

## كيفية تنفيذ استخراج صور PDF دفعةً
إذا كنت بحاجة إلى استخراج الصور من العديد من ملفات PDF، غلف الخطوات السابقة داخل حلقة تتكرر على قائمة من مسارات الملفات. منطق `Watermarker` نفسه يُطبق على كل مستند، مما يتيح لك بناء خط أنابيب **batch pdf image extraction** ببضع أسطر إضافية من جافا.

## المشكلات الشائعة والحلول
| المشكلة | الحل |
|-------|----------|
| **لم يتم العثور على صور** | تحقق من أن ملف PDF يحتوي فعليًا على صور مدمجة. استخدم ميزة “Export images” في عارض PDF للتأكيد. |
| **أخطاء الأذونات** | تأكد من أن عملية جافا لديها صلاحية القراءة/الكتابة على مجلدي الإدخال والإخراج. |
| **ملفات PDF الكبيرة تسبب OutOfMemoryError** | زد حجم الذاكرة المخصصة للـ JVM (`-Xmx` flag) أو عالج PDF صفحةً بصفحة باستخدام `PdfLoadOptions.setPageNumber`. |
| **الصور محفوظة بصيغة خاطئة** | طريقة `save` تحترم امتداد الملف الذي تحدده؛ استخدم `.png` للحصول على إخراج غير مضغوط. |

## الأسئلة المتكررة

**س: هل يمكنني تصفية الصور حسب الحجم أو الصيغة أثناء استخدام `extract images pdf java`؟**  
ج: نعم. بعد استرجاع `WatermarkableImageCollection`، افحص خصائص كل `PdfImage` (العرض، الارتفاع، الصيغة) وطبق منطقًا شرطيًا قبل الحفظ.

**س: هل من الممكن استبدال صورة بعد استخراجها؟**  
ج: بالتأكيد. استخدم `watermarker.replace(image, newImage)` حيث `newImage` هو `PdfImage` تنشئه من ملف أو تدفق.

**س: هل المكتبة تدعم ملفات PDF المحمية بكلمة مرور؟**  
ج: نعم. قدم كلمة المرور في `PdfLoadOptions.setPassword("yourPassword")` قبل إنشاء `Watermarker`.

**س: كيف يقارن هذا النهج باستخدام ميزة “Export images” في عارض PDF؟**  
ج: الاستخراج البرمجي عبر GroupDocs.Watermark قابل للأتمتة بالكامل، يعمل على الخوادم، ويمكن دمجه في سير عمل أكبر مثل المعالجة الدفعة أو خطوط أنابيب الذكاء الاصطناعي اللاحقة.

**س: ما الإصدار المطلوب من GroupDocs.Watermark؟**  
ج: أي إصدار حديث (إصدارات 2024‑2025) يدعم الواجهة المعروضة. راجع ملاحظات الإصدار الرسمية للتغييرات الطفيفة.

## الخلاصة
أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج **كيفية استخراج الصور** من ملفات PDF باستخدام GroupDocs.Watermark لجافا. من خلال تحميل المستند، تكوين البحث، استرجاع مجموعة الصور، وحفظ كل صورة كملف PNG، يمكنك أتمتة المهام المتكررة، دعم المعالجة الدفعة، وتكامل استخراج الصور في تطبيقات جافا الأكبر.

---

**آخر تحديث:** 2026-02-26  
**تم الاختبار مع:** GroupDocs.Watermark for Java 23.9 (أحدث نسخة وقت الكتابة)  
**المؤلف:** GroupDocs