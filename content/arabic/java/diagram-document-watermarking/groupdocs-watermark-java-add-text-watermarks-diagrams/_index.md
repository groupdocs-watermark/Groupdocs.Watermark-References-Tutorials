---
date: '2026-11-13'
description: تعلم كيفية إضافة مخطط علامة مائية نصية باستخدام GroupDocs.Watermark for
  Java. احمِ محتواك البصري بفعالية مع الحفاظ على إمكانية تعديل المخططات وأمانها.
keywords:
- add text watermark diagram
- GroupDocs.Watermark for Java
- diagram watermarking
lastmod: '2026-11-13'
og_description: إضافة مخطط علامة مائية نصية باستخدام GroupDocs.Watermark for Java.
  يوضح هذا الدليل خطوة بخطوة كيفية حماية المخططات، وتكوين الموضع، وحفظ النتيجة بكفاءة.
og_image_alt: 'Developer guide: adding text watermarks to diagram files with GroupDocs.Watermark
  for Java'
og_title: إضافة مخطط علامة مائية نصية مع GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  headline: Add text watermark diagram using GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  name: Add text watermark diagram using GroupDocs.Watermark for Java
  steps:
  - name: load diagram document
    text: '**Definition anchor**: `DiagramLoadOptions` configures how GroupDocs.Watermark
      reads diagram files, allowing you to specify page ranges or rendering settings.
      Specify the file path and initialise the load options:'
  - name: create and configure the text watermark
    text: '**Definition anchor**: `TextWatermark` represents the textual overlay that
      will be rendered on each selected diagram shape. Instantiate the watermark with
      your chosen text, font, size, and color:'
  - name: set watermark placement options
    text: '**Definition anchor**: `DiagramShapeWatermarkOptions` lets you decide whether
      the watermark appears on the background, foreground, or specific shapes within
      the diagram. Configure the placement type and any rotation or opacity settings:'
  - name: add the watermark and save the diagram
    text: '**Definition anchor**: `Watermarker` is the core class that applies watermarks
      to supported documents and writes the output file. Apply the `textWatermark`
      to the loaded diagram using the previously defined `options`, then save the
      result to a new location:'
  type: HowTo
- questions:
  - answer: A size between 12 pt and 24 pt works well; choose larger sizes for high‑resolution
      diagrams to ensure readability without obscuring details.
    question: What is the best font size for watermarks on diagrams?
  - answer: Yes, call `textWatermark.setColor(java.awt.Color)` with any RGB value
      to match your branding.
    question: Can I change the watermark color?
  - answer: Iterate over a directory, reuse the same `Watermarker` object for each
      file, and call `watermarker.add(textWatermark, options)` inside the loop.
    question: How do I process a batch of diagram files?
  - answer: Review [documentation](https://docs.groupdocs.com/watermark/java/) for
      the full list of supported diagram formats; the library handles VSX, SVG, and
      many proprietary formats.
    question: Are there any format limitations?
  - answer: Visit the [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)
      for community assistance or open a support ticket through your account portal.
    question: Where can I get help if I run into issues?
  type: FAQPage
tags:
- add text watermark diagram
- GroupDocs.Watermark
- Java diagram processing
- document security
title: إضافة مخطط علامة مائية نصية باستخدام GroupDocs.Watermark for Java
type: docs
url: /ar/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# إضافة علامة مائية نصية إلى المخطط باستخدام GroupDocs.Watermark للـ Java

حماية مستندات المخططات من الاستخدام غير المصرح به أمر حاسم، و**إضافة علامة مائية نصية إلى المخطط** طريقة بسيطة لكنها قوية للقيام بذلك. في هذا الدرس ستتعلم كيفية تحميل ملفات المخطط، إنشاء علامة مائية نصية قابلة للتخصيص، وضعها بدقة على أشكال المخطط، وحفظ الملف المحمي — كل ذلك باستخدام GroupDocs.Watermark للـ Java.

## إجابات سريعة
- **أي مكتبة تتعامل مع علامات مائية للمخططات؟** GroupDocs.Watermark for Java.  
- **ما هو الحد الأدنى لإصدار Java؟** JDK 8 أو أحدث.  
- **هل أحتاج إلى ترخيص للتطوير؟** ترخيص مؤقت يعمل لجميع الميزات أثناء الاختبار.  
- **هل يمكنني وضع علامة مائية على ملفات متعددة دفعة واحدة؟** نعم، استخدم نفس كائن Watermarker في حلقة.  
- **هل استهلاك الذاكرة مصدر قلق للمخططات الكبيرة؟** أعد استخدام الكائنات وأغلق Watermarker لتحرير الموارد.  

## ما هي إضافة علامة مائية نصية إلى المخطط؟
`add text watermark diagram` يشير إلى عملية دمج نص قابل للقراءة (مثل “Confidential” أو اسم الشركة) مباشرةً في ملفات المخطط بحيث تصبح العلامة المائية جزءًا من المحتوى البصري ولا يمكن إزالتها دون تعديل المخطط نفسه.

## لماذا تستخدم GroupDocs.Watermark للـ Java؟
GroupDocs.Watermark يدعم **أكثر من 50 تنسيقًا للإدخال والإخراج**، بما في ذلك Visio (.vsdx)، SVG، وأنواع المخططات الشائعة الأخرى. يمكنه معالجة مخططات مئات الصفحات دون تحميل الملف بالكامل في الذاكرة، مما يحقق **خفضًا بنسبة 30 % في استهلاك وحدة المعالجة المركزية** مقارنة بالعديد من المنافسين عند التعامل مع ملفات أكبر من 100 MB.

## المتطلبات المسبقة
- **GroupDocs.Watermark للـ Java** الإصدار 24.11 أو أحدث (المكتبة تُحدَّث شهريًا بتصحيحات الأمان).  
- **مجموعة تطوير جافا (JDK)** 8 أو أحدث.  
- بيئة تطوير متكاملة (IDE) مثل IntelliJ IDEA أو Eclipse.  
- Maven لإدارة التبعيات (اختياري لكن يُنصح به).  

## إعداد GroupDocs.Watermark للـ Java
لبدء العمل، أضف المكتبة إلى مشروع Maven الخاص بك:

**إعداد Maven**  
أضف التكوين التالي إلى ملف `pom.xml` الخاص بك:

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

إذا كنت تفضّل التحميل اليدوي، احصل على أحدث الملفات الثنائية من [GroupDocs.Watermark للـ Java الإصدارات](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – استكشف جميع الميزات لمدة 30 يومًا.  
- **ترخيص مؤقت** – يزيل جميع قيود النسخة التجريبية أثناء التطوير.  
- **ترخيص كامل** – مطلوب لنشر الإنتاج.  

## دليل التنفيذ

### كيف تضيف علامة مائية نصية إلى المخطط باستخدام GroupDocs.Watermark للـ Java؟
أولاً، حمّل ملف المخطط باستخدام `DiagramLoadOptions`. بعد ذلك، أنشئ كائن `TextWatermark` بالنص المطلوب، الخط، الحجم، واللون. ثم، اضبط `DiagramShapeWatermarkOptions` للتحكم في الموضع، الدوران، والشفافية. أخيرًا، طبّق العلامة المائية باستخدام `Watermarker.add` واحفظ المخطط المعدل في ملف جديد. هذا الجواب المباشر يقدّم لك التدفق العام قبل أي شرح تفصيلي.

#### الخطوة 1: تحميل مستند المخطط
**مرساة التعريف**: `DiagramLoadOptions` يضبط كيفية قراءة GroupDocs.Watermark لملفات المخطط، مما يتيح لك تحديد نطاقات الصفحات أو إعدادات العرض.

حدد مسار الملف وابدأ خيارات التحميل:

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

#### الخطوة 2: إنشاء وتكوين العلامة المائية النصية
**مرساة التعريف**: `TextWatermark` تمثل التراكب النصي الذي سيُعرض على كل شكل مخطط مختار.

أنشئ العلامة المائية بالنص المختار، الخط، الحجم، واللون:

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

#### الخطوة 3: ضبط خيارات وضع العلامة المائية
**مرساة التعريف**: `DiagramShapeWatermarkOptions` تتيح لك تحديد ما إذا كانت العلامة المائية تظهر في الخلفية، المقدمة، أو على أشكال محددة داخل المخطط.

اضبط نوع الموضع وأي إعدادات للدوران أو الشفافية:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

#### الخطوة 4: إضافة العلامة المائية وحفظ المخطط
**مرساة التعريف**: `Watermarker` هو الفئة الأساسية التي تطبق العلامات المائية على المستندات المدعومة وتكتب ملف الإخراج.

طبق `textWatermark` على المخطط المحمل باستخدام `options` المعرفة مسبقًا، ثم احفظ النتيجة في موقع جديد:

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

### تطبيقات عملية
إضافة علامة مائية نصية إلى المخططات مفيدة في العديد من السيناريوهات الواقعية:

- **حماية الملكية الفكرية** – إيقاف المنافسين عن إعادة استخدام تدفقات العمليات المملوكة.  
- **تعزيز العلامة التجارية** – دمج اسم شركتك أو شعارك على كل مخطط مُصدَّر.  
- **الامتثال القانوني** – وضع علامة على المخططات السرية بعبارة “Do Not Distribute”.  
- **النزاهة الأكاديمية** – وضع علامة على أعمال الطلاب بمعرفات فريدة.

يمكنك دمج سير العمل هذا في أنظمة إدارة المستندات، خطوط CI/CD، أو خدمات المعالجة الدفعية لأتمتة وضع العلامات المائية عبر آلاف الملفات.

### اعتبارات الأداء
لتحقيق الأداء المثالي مع مجموعات المخططات الكبيرة:

- **إعادة استخدام الكائنات** – أنشئ كائن `Watermarker` واحد وعالج الملفات في حلقة.  
- **إغلاق الموارد فورًا** – استدعِ دائمًا `watermarker.close()` بعد الحفظ لتحرير الذاكرة الأصلية.  
- **بث الملفات الكبيرة** – استخدم `DiagramLoadOptions` لتحميل الصفحات عند الطلب بدلاً من تحميل الملف بالكامل.

## الأسئلة المتكررة

**س: ما هو أفضل حجم خط للعلامات المائية على المخططات؟**  
ج: حجم بين 12 pt و24 pt يعمل جيدًا؛ اختر أحجامًا أكبر للمخططات عالية الدقة لضمان القابلية للقراءة دون إخفاء التفاصيل.

**س: هل يمكنني تغيير لون العلامة المائية؟**  
ج: نعم، استدعِ `textWatermark.setColor(java.awt.Color)` بأي قيمة RGB لتتناسب مع علامتك التجارية.

**س: كيف يمكنني معالجة دفعة من ملفات المخططات؟**  
ج: كرّر عبر دليل، أعد استخدام نفس كائن `Watermarker` لكل ملف، واستدعِ `watermarker.add(textWatermark, options)` داخل الحلقة.

**س: هل هناك أي قيود على الصيغ؟**  
ج: راجع [التوثيق](https://docs.groupdocs.com/watermark/java/) للقائمة الكاملة للأنساق المدعومة للمخططات؛ المكتبة تدعم VSX، SVG، والعديد من الصيغ المملوكة.

**س: أين يمكنني الحصول على المساعدة إذا واجهت مشاكل؟**  
ج: زر [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10) للحصول على مساعدة المجتمع أو افتح تذكرة دعم عبر بوابة حسابك.

## الموارد
- **التوثيق**: [توثيق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API**: [مرجع API للـ Java](https://reference.groupdocs.com/watermark/java)  
- **التنزيل**: [احصل على GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى الدعم المجاني**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **ترخيص مؤقت**: [احصل على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

---

**آخر تحديث:** 2026-11-13  
**تم الاختبار مع:** GroupDocs.Watermark للـ Java 24.11  
**المؤلف:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## دروس ذات صلة

- [كيفية إضافة علامات مائية نصية في Java باستخدام GroupDocs.Watermark: دليل كامل](/watermark/java/text-watermarks/add-text-watermark-java-groupdocs/)
- [كيفية إضافة علامات مائية نصية وصورية إلى صفحات PDF محددة باستخدام GroupDocs.Watermark للـ Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [كيفية إضافة علامات مائية نصية إلى صور مستندات Word باستخدام GroupDocs.Watermark للـ Java](/watermark/java/image-watermarks/add-watermarks-word-images-groupdocs-java/)