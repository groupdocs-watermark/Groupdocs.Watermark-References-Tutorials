---
date: '2026-09-11'
description: تعلم كيفية استخراج خلفية الشريحة في Java وقراءة أبعاد شريحة PowerPoint
  باستخدام GroupDocs.Watermark for Java. احصل على حجم الصورة، حجم الملف، والبيانات
  الوصفية في دقائق.
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: استخراج خلفية الشريحة في Java وقراءة أبعاد شريحة PowerPoint باستخدام
  GroupDocs.Watermark for Java. دليل مفصل مع الإعداد، الكود، وحل المشكلات.
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: استخراج خلفية الشريحة في Java باستخدام GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: كيفية استخراج خلفية الشريحة في Java
type: docs
url: /ar/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# كيفية استخراج خلفية الشريحة في جافا

## مقدمة

استخراج خلفية الشريحة في جافا هو حاجة شائعة عندما تريد تحليل أو إعادة استخدام أو توثيق الأصول البصرية داخل ملف PowerPoint. باستخدام GroupDocs.Watermark for Java يمكنك استرجاع أبعاد الصورة، حجم الملف، وغيرها من البيانات الوصفية برمجياً دون فتح العرض التقديمي في PowerPoint. يشرح هذا البرنامج التعليمي سير العمل الكامل — من إعداد البيئة إلى استخراج وتفسير تفاصيل الخلفية — بحيث يمكنك دمج هذه القدرة في أي خط أنابيب أتمتة مبني على جافا.

### إجابات سريعة
- **ما المكتبة التي تتعامل مع استخراج خلفية الشريحة؟** GroupDocs.Watermark for Java.  
- **ما الطريقة التي تُرجع أبعاد الصورة؟** `getBackground().getImageInfo().getWidth()` و `getHeight()`.  
- **هل يمكنني الحصول على حجم ملف صورة الخلفية؟** نعم، عبر `getBackground().getImageInfo().getSize()`.  
- **هل أحتاج إلى ترخيص لهذه الميزة؟** ترخيص مؤقت أو كامل يفتح جميع الوظائف؛ وضع التجربة يعمل مع بعض القيود.  
- **هل يدعم Maven؟** بالتأكيد — أضف تبعية GroupDocs.Watermark إلى `pom.xml`.

## ما هو استخراج خلفية الشريحة في جافا؟

يشير استخراج خلفية الشريحة في جافا إلى عملية قراءة الخلفية البصرية لكل شريحة في عرض PowerPoint برمجياً باستخدام كود جافا. تنتج هذه العملية بيانات وصفية مثل عرض الصورة، ارتفاعها، وحجم الملف، مما يتيح معالجة لاحقة مثل فحص العلامة التجارية أو إعادة استخدام الأصول.

## لماذا تستخدم GroupDocs.Watermark لهذه المهمة؟

يدعم GroupDocs.Watermark **أكثر من 30 تنسيقًا للإدخال والإخراج**، يعالج العروض التقديمية التي تصل إلى **500 شريحة** دون تحميل الملف بالكامل في الذاكرة، ويوفر API مخصص للوصول إلى خلفيات الشرائح. هذه القدرات المقاسة تجعلها خيارًا موثوقًا لأتمتة على مستوى المؤسسات.

## المتطلبات المسبقة
- **Java 11+** مثبت على جهاز التطوير الخاص بك.  
- **Maven** لإدارة التبعيات.  
- **GroupDocs.Watermark 24.11** (أو أحدث) – المكتبة تحتوي على الفئات `PresentationLoadOptions` و `PresentationContent` المستخدمة في هذا الدليل.  
- رخصة **صحيحة** (مؤقتة أو كاملة) لفتح مجموعة الميزات بالكامل.

## إعداد GroupDocs.Watermark لجافا

### تكوين Maven
أضف تبعية GroupDocs.Watermark إلى ملف `pom.xml` الخاص بك:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

### التحميل المباشر
إذا كنت تفضل التثبيت اليدوي، احصل على أحدث ملف JAR من صفحة الإصدار الرسمية: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
تتيح لك الرخصة المؤقتة تقييم الـ API، بينما تزيل الرخصة الكاملة جميع قيود التجربة. احصل على رخصتك من بوابة الترخيص: [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license/).

#### التهيئة الأساسية والإعداد
الخطوة الأولى هي إنشاء كائن `Watermarker` يشير إلى ملف PowerPoint الخاص بك:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## كيفية استخراج خلفية الشريحة في جافا؟
تبدأ العملية بتحميل ملف PowerPoint باستخدام كائن Watermarker، ثم إنشاء خيارات التحميل المناسبة. بعد فتح المستند، يمكنك الوصول إلى محتوى كل شريحة، استرجاع صورة الخلفية، واستخراج بياناتها الوصفية مثل الأبعاد وحجم الملف. أخيرًا، أغلق Watermarker لتحرير الموارد. الخطوات التالية توضح التسلسل الدقيق الذي يجب اتباعه، وتظهر نواقل الشيفرة أين يجب وضع المقاطع البرمجية الحالية.

### الخطوة 1: إنشاء خيارات التحميل
`PresentationLoadOptions` يحدد تفضيلات التحميل مثل معالجة كلمة المرور واستخدام الذاكرة.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### الخطوة 2: فتح مستند PowerPoint
أنشئ كائن `Watermarker` مع المسار إلى ملف `.pptx` الخاص بك وخيارات التحميل التي تم إنشاؤها مسبقًا.

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### الخطوة 3: الوصول إلى محتوى الشريحة
`PresentationContent` هو نقطة الدخول لاسترجاع كائنات مستوى الشريحة، بما في ذلك صور الخلفية.

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### الخطوة 4: التكرار على الشرائح وقراءة تفاصيل الخلفية
Slide تمثل شريحة فردية داخل العرض التقديمي وتوفر الوصول إلى عناصرها البصرية.  
لكل كائن `Slide`، استدعِ `getBackground()` للحصول على الصورة، ثم اقرأ أبعادها وحجمها.

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### الخطوة 5: إغلاق Watermarker
دائمًا أغلق كائن `Watermarker` لتحرير الموارد الأصلية وتجنب تسرب الذاكرة.

```java
watermarker.close();
```

## كيفية قراءة أبعاد شريحة PowerPoint باستخدام GroupDocs.Watermark؟
تُظهر الـ API العرض والارتفاع عبر كائن `ImageInfo` المرتبط بخلفية الشريحة. استرجعهما باستخدام `getWidth()` و `getHeight()`، والتي تُعيد قيم بكسل يمكنك استخدامها لحسابات التخطيط أو للتحقق من التوافق مع إرشادات العلامة التجارية.

## المشكلات الشائعة واستكشاف الأخطاء
- **الملف غير موجود** – تحقق من أن مسار الملف مطلق أو نسبي بشكل صحيح إلى جذر مشروعك.  
- **تنسيق غير مدعوم** – يدعم GroupDocs.Watermark تنسيقات PPTX و PPT و ODP؛ قد تحتاج ملفات PPT الثنائية القديمة إلى تحويل أولاً.  
- **الترخيص غير مفعّل** – تأكد من استدعاء `License.setLicense("path/to/license.file")` قبل أي استخدام آخر للـ API.

## التطبيقات العملية
1. **الامتثال التلقائي للعلامة التجارية** – فحص خلفيات الشرائح للتأكد من مطابقتها لألوان الشركة أو أبعاد الشعار.  
2. **جرد الأصول** – بناء فهرس لصور الخلفية عبر مكتبة المستندات لإعادة استخدامها في أصول التسويق.  
3. **ترحيل المحتوى** – استخراج الخلفيات، تخزينها في مدير أصول رقمي، وإعادة تطبيقها على عروض تقديمية جديدة برمجياً.  
4. **مراقبة الأداء** – تسجيل إحصاءات حجم الصورة لاكتشاف الأصول الكبيرة غير العادية التي قد تبطئ عرض الشرائح.

## اعتبارات الأداء
- **تنظيف الموارد** – إغلاق `Watermarker` بسرعة يحرر الذاكرة الأصلية، وهو أمر حاسم عند معالجة مجموعات شرائح كبيرة.  
- **بصمة الذاكرة** – المكتبة تبث بيانات الشرائح؛ يمكنك تقليل الاستخدام أكثر بمعالجة الشرائح واحدةً تلو الأخرى بدلاً من تحميل العرض الكامل.  
- **نصيحة المعالجة الدفعية** – عند التعامل مع العشرات من الملفات، أعد استخدام كائن `License` واحد وأنشئ `Watermarker` جديد لكل ملف للحفاظ على استقرار ذاكرة JVM.

## الخلاصة
أصبح لديك الآن دليل كامل وجاهز للإنتاج لاستخراج خلفية الشريحة في جافا باستخدام GroupDocs.Watermark. باتباع الخطوات أعلاه يمكنك استرجاع أبعاد الصورة، حجم الملف، وغيرها من البيانات الوصفية، ثم تطبيق هذه المعلومات على فحوصات العلامة التجارية، إدارة الأصول، أو أي سير عمل مخصص تتخيله.

**الخطوات التالية**
- جرب `PresentationLoadOptions` المختلفة (مثل الملفات المحمية بكلمة مرور).  
- استكشف API العلامة المائية لإضافة أو استبدال الخلفيات تلقائيًا.  
- دمج منطق الاستخراج هذا مع خدمة REST لتوفير نقاط نهاية لبيانات ميتا الشريحة.

## الأسئلة المتكررة

**س: ما هو الحد الأدنى لإصدار Java المطلوب؟**  
ج: Java 11 أو أحدث مطلوب؛ الإصدارات الأقدم تفتقر إلى ميزات اللغة اللازمة للمكتبة.

**س: هل يمكنني استخراج الخلفيات من العروض المحمية بكلمة مرور؟**  
ج: نعم — قم بتعيين كلمة المرور في `PresentationLoadOptions` قبل فتح الملف.

**س: هل يحد وضع التجربة عدد الشرائح التي يمكنني معالجتها؟**  
ج: وضع التجربة يضيف علامة مائية على ملفات الإخراج لكنه لا يحد من عدد الشرائح لاستخراج البيانات الوصفية.

**س: هل يمكن حفظ صورة الخلفية المستخرجة إلى القرص؟**  
ج: بالتأكيد — استخدم `ImageInfo.save("output.png")` بعد استرجاع كائن `ImageInfo`.

**س: إلى أي تنسيقات يمكنني تصدير الصورة المستخرجة؟**  
ج: الـ API يدعم PNG و JPEG و BMP و GIF لتصدير صورة الخلفية.

## الموارد

- **الوثائق:** [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/)  
- **الوثائق:** [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API:** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **التنزيل:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GitHub:** [GroupDocs GitHub Page](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى الدعم:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/10)

---

**آخر تحديث:** 2026-09-11  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية استرجاع أبعاد شريحة PowerPoint باستخدام GroupDocs.Watermark Java API](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)
- [إزالة خلفية شريحة PowerPoint في جافا باستخدام مكتبة GroupDocs.Watermark](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)
- [كيفية استرجاع معلومات المستند باستخدام GroupDocs.Watermark لجافا: دليل خطوة بخطوة](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)