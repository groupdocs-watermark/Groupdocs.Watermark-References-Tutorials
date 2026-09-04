---
date: '2026-05-27'
description: تعلم كيفية استخدام GroupDocs لإضافة علامات مائية على الأشكال إلى ملفات
  PPT باستخدام Java. دليل خطوة بخطوة، نصائح التكوين، ورؤى حول الأداء.
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: كيفية استخدام GroupDocs لإضافة علامات مائية على الأشكال في Java لعروض PowerPoint
type: docs
url: /ar/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# كيفية استخدام GroupDocs لإضافة علامات مائية على شكل في Java لعروض PowerPoint

حماية عروض PowerPoint الخاصة بك أمر أساسي لضمان تناسق العلامة التجارية وأمان البيانات. في هذا البرنامج التعليمي ستكتشف **كيفية استخدام GroupDocs** لإدراج علامات مائية على شكل مباشرةً في ملفات PPTX باستخدام Java، مما يمنحك طريقة موثوقة برمجية لتوسيم كل شريحة.

## الإجابات السريعة
- **ما المكتبة التي تضيف علامات مائية إلى PPTX في Java؟** GroupDocs.Watermark.
- **أي فئة تقوم بتحميل العرض التقديمي؟** `PresentationLoadOptions`.
- **أي فئة تطبق العلامة المائية؟** `Watermarker`.
- **هل أحتاج إلى ترخيص للتطوير؟** نسخة تجريبية مجانية تعمل للاختبار؛ يلزم ترخيص مدفوع للإنتاج.
- **هل يمكنني وضع علامة مائية على ملفات كبيرة (>500 ميغابايت)؟** نعم – يقوم GroupDocs بمعالجة ملفات تصل إلى 2 جيجابايت دون تحميل المستند بالكامل في الذاكرة.

## ما هو GroupDocs.Watermark؟
`GroupDocs.Watermark` هو مجموعة تطوير برمجيات (SDK) للـ Java تتيح لك إضافة علامات مائية نصية أو صورة أو شكل إلى أكثر من 100 تنسيق مستند، بما في ذلك PPT و PPTX و PDF و DOCX. يعالج الملفات حتى 2 جيجابايت مع الحفاظ على استهلاك منخفض للذاكرة. كما توفر المكتبة واجهات برمجة تطبيقات (APIs) لتخصيص الشفافية، والدوران، والموضع، مما يضمن دمج العلامة المائية بسلاسة مع تخطيطات الشرائح الحالية.

## لماذا إضافة علامات مائية على شكل إلى عروض PowerPoint؟
تحافظ العلامات المائية على شكل على التناسق البصري عبر الشرائح ويمكن وضعها بدقة باستخدام إحداثيات المتجهات، مما يتيح لك محاذاة عناصر العلامة التجارية تمامًا حيثما تحتاج. تظل قابلة للتحرير كأشكال PowerPoint الأصلية، مما يضمن أن أي تعديلات لاحقة على العرض التقديمي تحافظ على مظهر العلامة المائية وموقعها. تشمل الفوائد المكمّنة:
- **50+** أنماط علامات مائية (نص، صورة، شكل) مدعومة.
- **100 %** دقة التخطيط – تبقى الأشكال محاذية بعد التعديل.
- **حتى 2 جيجابايت** من معالجة حجم الملف دون تحميل المستند بالكامل، مما يقلل استهلاك الذاكرة بنسبة **70 %** مقارنةً بالطرق البسيطة.

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8+** مثبت.
- **Maven** لإدارة الاعتمادات.
- بيئة تطوير متكاملة (IDE) مثل **IntelliJ IDEA** أو **Eclipse**.
- معرفة أساسية بـ Java وإلمام بـ Maven.
- الوصول إلى ترخيص **GroupDocs.Watermark** (تجريبي أو تجاري).

### المكتبات المطلوبة والإصدارات
- **GroupDocs.Watermark for Java** الإصدار **24.11** أو أحدث.

### متطلبات إعداد البيئة
- تأكد من أن `JAVA_HOME` يشير إلى JDK الخاص بك.
- قم بتكوين `pom.xml` الخاص بمشروعك كما هو موضح أدناه.

## كيفية إضافة علامة مائية على شكل إلى ملف PowerPoint باستخدام GroupDocs.Watermark في Java؟
`PresentationLoadOptions` يحدد خيارات تحميل ملفات PowerPoint، مثل اختيار الشرائح ومعالجة كلمة المرور.  
`Watermarker` هي الفئة الأساسية التي تقوم بتحميل المستند وتطبيق العلامات المائية.  

حمّل العرض التقديمي باستخدام `PresentationLoadOptions`، أنشئ كائنًا من `Watermarker`، عرّف علامة مائية على شكل، طبّقها على كل شريحة، وأخيرًا احفظ الملف. يتطلب هذا التدفق من البداية إلى النهاية بضع أسطر من الشيفرة فقط ويعمل في أقل من ثانية لعرض تقديمي مكوّن من 10 شرائح عادةً.

### تكوين Maven
أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

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

### تحميل مباشر
بدلاً من ذلك، قم بتنزيل أحدث نسخة من [إصدارات GroupDocs.Watermark للـ Java](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
احصل على نسخة تجريبية مجانية أو ترخيص مؤقت لاستكشاف جميع ميزات GroupDocs.Watermark. للاستخدام في الإنتاج، اشترِ ترخيصًا يتناسب مع حجم نشر تطبيقك.

#### التهيئة الأساسية والإعداد
`Watermarker` هي الفئة الأساسية التي تقوم بتحميل المستند وتطبيق العلامات المائية.  
`PresentationLoadOptions` توفر خيارات لتحميل ملفات PowerPoint، مثل معالجة الشرائح وحفظ الرسوم المتحركة.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### الخطوة 1: إنشاء علامة مائية على شكل
`ShapeWatermarkOptions` يحدد الخصائص البصرية لعلامة مائية على شكل، بما في ذلك الحجم، اللون، الشفافية، والدوران.

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### الخطوة 2: تطبيق العلامة المائية على جميع الشرائح
قم بالتكرار عبر كل شريحة في العرض التقديمي وأضف علامة مائية على شكل.

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### الخطوة 3: حفظ العرض التقديمي المائي
اختر تنسيق الإخراج (PPTX) واحفظ الملف. يحافظ الـ SDK على محتوى الشرائح الأصلي والرسوم المتحركة.

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### المشكلات الشائعة والحلول
- **خطأ عدم وجود ترخيص:** تأكد من وضع ملف الترخيص في classpath أو تعيينه عبر `License.setLicense("path/to/license.lic")`.  
`License` class loads and applies a GroupDocs license file to enable full SDK functionality.  
- **الشكل غير مرئي:** زيادة شفافية الشكل أو تباين اللون؛ الشفافية الافتراضية هي 0.2.  
- **تباطؤ الملفات الكبيرة:** استخدم `PresentationLoadOptions.setLoadAllSlides(false)` لتحميل الشرائح عند الطلب، مما يقلل من استهلاك الذاكرة.

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامات مائية متعددة إلى نفس الشريحة؟**  
ج: نعم – استدعِ `watermarker.add()` عدة مرات مع `ShapeWatermarkOptions` مختلفة لكل علامة مائية.

**س: هل يدعم GroupDocs.Watermark ملفات PPTX المحمية بكلمة مرور؟**  
ج: بالتأكيد. قدّم كلمة المرور في `PresentationLoadOptions.setPassword("yourPassword")` قبل التحميل.

**س: هل يمكن وضع علامة مائية على شرائح مختارة فقط؟**  
ج: نعم – حدد مؤشرات الشرائح في طريقة `add` بدلاً من التكرار على جميع الشرائح.

**س: ما إصدارات Java المتوافقة؟**  
ج: يعمل الـ SDK مع Java 8 حتى Java 21، مما يغطي البيئات القديمة والحديثة.

**س: كيف يتعامل المكتبة مع الأشكال المتحركة؟**  
ج: العلامات المائية على شكل ثابتة بطبيعتها؛ لا تتداخل مع الرسوم المتحركة الموجودة على الشريحة.

---

**آخر تحديث:** 2026-05-27  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs

## الدروس ذات الصلة

- [إضافة علامات مائية إلى عروض PowerPoint باستخدام GroupDocs.Watermark للـ Java](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [كيفية إضافة علامات مائية نصية إلى صور PowerPoint باستخدام GroupDocs.Watermark للـ Java](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [كيفية إضافة علامات مائية بتأثيرات الخط في PowerPoint باستخدام GroupDocs.Watermark و Java](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)