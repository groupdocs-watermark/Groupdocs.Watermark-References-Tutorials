---
date: '2026-08-31'
description: تعلم كيفية إضافة watermark إلى الرسوم البيانية باستخدام GroupDocs.Watermark
  for Java. يغطي هذا الدليل الإعداد، إنشاء text watermark، خيارات الموضع، وحفظ الملفات
  المحمية.
keywords:
- how to add watermark
- text watermark Java
- diagram watermarking
- GroupDocs.Watermark
lastmod: '2026-08-31'
og_description: تعلم كيفية إضافة watermark إلى الرسوم البيانية باستخدام GroupDocs.Watermark
  for Java. اتبع تعليمات خطوة بخطوة لحماية محتواك البصري باستخدام text watermarks.
og_image_alt: Guide showing how to add watermark to diagram files using GroupDocs.Watermark
  for Java
og_title: كيفية إضافة watermark إلى الرسوم البيانية باستخدام GroupDocs.Watermark for
  Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to add watermark to diagrams using GroupDocs.Watermark for
    Java. This guide covers setup, text watermark creation, placement options, and
    saving the protected files.
  headline: How to add watermark to diagrams with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to diagrams using GroupDocs.Watermark for
    Java. This guide covers setup, text watermark creation, placement options, and
    saving the protected files.
  name: How to add watermark to diagrams with GroupDocs.Watermark for Java
  steps:
  - name: load the diagram document
    text: First, specify the file location and initialise the load options. **Definition
      anchor:** `DiagramLoadOptions` specifies how a diagram file is parsed, including
      page‑size handling and shape extraction.
  - name: create and configure the text watermark
    text: Instantiate a `TextWatermark` object and set its visual properties. **Definition
      anchor:** `TextWatermark` represents a textual overlay that can be styled with
      font, size, color, and opacity before being applied to a document.
  - name: configure watermark placement options
    text: Define where the watermark should appear within the diagram shapes. **Definition
      anchor:** `DiagramShapeWatermarkOptions` lets you target specific diagram elements
      (e.g., background pages, individual shapes) for watermark insertion.
  - name: add the watermark and save the document
    text: Apply the configured watermark to the loaded diagram and write the protected
      file to disk. **Definition anchor:** `Watermarker` is the core class that orchestrates
      loading, watermarking, and saving operations for supported file types.
  type: HowTo
- questions:
  - answer: A size between 14 pt and 24 pt balances readability and unobtrusiveness
      for most diagram dimensions.
    question: What is the best font size for a diagram watermark?
  - answer: Yes – use `textWatermark.setColor(Color.BLUE)` (or any `java.awt.Color`)
      to customise the hue.
    question: Can I change the watermark colour?
  - answer: Iterate over your file collection and reuse a single `Watermarker` per
      thread, calling `watermarker.add()` for each document before saving.
    question: How do I process a large batch of diagrams?
  - answer: GroupDocs.Watermark supports over 50 formats, including Visio (.vsdx),
      SVG, PNG, and JPEG. See the full list in the official [documentation](https://docs.groupdocs.com/watermark/java/).
    question: Are there any format limitations?
  - answer: 'Post questions on the community forum: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10).'
    question: Where can I get help if I encounter issues?
  type: FAQPage
tags:
- watermark
- GroupDocs.Watermark
- Java diagram
- text watermark
- document protection
title: كيفية إضافة watermark إلى الرسوم البيانية باستخدام GroupDocs.Watermark for
  Java
type: docs
url: /ar/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# كيفية إضافة علامة مائية إلى المخططات باستخدام GroupDocs.Watermark للغة Java

حماية مستندات المخططات من الاستخدام غير المصرح به أمر أساسي لأي منظمة تشارك الأصول البصرية. في هذا الدرس الشامل ستكتشف **كيفية إضافة علامة مائية** إلى المخططات باستخدام GroupDocs.Watermark للغة Java، بدءًا من إعداد المشروع وحتى حفظ المستند النهائي. الدليل مكتوب للمطورين الملمين بلغة Java ويهدف إلى تقديم حل واضح وجاهز للإنتاج.

## إجابات سريعة
- **أي مكتبة تتعامل مع علامات مائية للمخططات؟** GroupDocs.Watermark للغة Java.  
- **ما هو الحد الأدنى لإصدار Java؟** JDK 8 أو أعلى.  
- **هل يمكنني معالجة العديد من المخططات دفعة واحدة؟** نعم – توفر API طرقًا للمعالجة الدفعية.  
- **هل أحتاج إلى ترخيص للتطوير؟** الترخيص المؤقت يزيل جميع القيود.  
- **أين يتم حفظ الملفات ذات العلامة المائية؟** إلى أي مسار تحدده عبر `watermarker.save()`.

## ما هو إضافة علامة مائية إلى المخططات؟
إضافة علامة مائية تعني دمج نص شبه شفاف (أو صور) داخل ملف المخطط بحيث يحمل المحتوى البصري معلومات الملكية. تصبح العلامة المائية جزءًا من الملف ولا يمكن إزالتها دون تعديل المستند نفسه. عادةً ما يتم عرضها بعتامة منخفضة بحيث يظل المخطط الأساسي قابلًا للقراءة بينما تظل العلامة المائية مرئية.

## لماذا تستخدم GroupDocs.Watermark للغة Java؟
يدعم GroupDocs.Watermark **أكثر من 50 تنسيقًا للإدخال والإخراج** — بما في ذلك Visio (.vsdx)، SVG، وأنواع الصور الشائعة — ويمكنه معالجة المخططات التي تصل إلى **500 صفحة** دون تحميل الملف بالكامل في الذاكرة، مما يوفر عمليات سريعة ومنخفضة الذاكرة للمشاريع الكبيرة. كما توفر المكتبة APIs للمعالجة الدفعية، وتدوير مخصص، وتعديلات اللون، مما يجعلها مناسبة لأنابيب المستندات على مستوى المؤسسات.

## المتطلبات المسبقة
- **GroupDocs.Watermark للغة Java** ≥ 24.11 (حمّل من صفحة الإصدارات الرسمية).  
- **Java Development Kit (JDK)** 8 أو أحدث.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- Maven لإدارة التبعيات (اختياري لكن يُنصح به).  

## إعداد GroupDocs.Watermark للغة Java
### إعداد Maven
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
احصل على أحدث ملف JAR من صفحة الإصدارات الرسمية: [GroupDocs.Watermark للغة Java الإصدارات](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **Free trial** – تقييم جميع الميزات دون تكلفة.  
- **Temporary license** – يزيل حدود الاستخدام أثناء التطوير.  
- **Commercial license** – مطلوب للنشر في بيئات الإنتاج.  

## كيفية إضافة علامة مائية إلى المخططات باستخدام GroupDocs.Watermark للغة Java؟
تتكون العملية من أربع خطوات رئيسية: تحميل مخطط المصدر إلى كائن `Watermarker`، إنشاء `TextWatermark` بالمظهر المطلوب، تكوين مكان ظهور العلامة المائية باستخدام `DiagramShapeWatermarkOptions`، وأخيرًا حفظ الملف المعدل إلى الموقع المستهدف. يتم توضيح كل خطوة باستخدام مقتطفات شفرة مختصرة أدناه.

### الخطوة 1: تحميل مستند المخطط
أولاً، حدد موقع الملف وابدأ خيارات التحميل.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

**تعريف مرساة:** `DiagramLoadOptions` يحدد كيفية تحليل ملف المخطط، بما في ذلك معالجة حجم الصفحة واستخراج الأشكال.

### الخطوة 2: إنشاء وتكوين العلامة المائية النصية
أنشئ كائن `TextWatermark` واضبط خصائصه البصرية.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

**تعريف مرساة:** `TextWatermark` يمثل تغطية نصية يمكن تنسيقها بالخط، الحجم، اللون، والعتامة قبل تطبيقها على المستند.

### الخطوة 3: تكوين خيارات وضع العلامة المائية
حدد مكان ظهور العلامة المائية داخل أشكال المخطط.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

**تعريف مرساة:** `DiagramShapeWatermarkOptions` يتيح لك استهداف عناصر مخطط محددة (مثل صفحات الخلفية، الأشكال الفردية) لإدراج العلامة المائية.

### الخطوة 4: إضافة العلامة المائية وحفظ المستند
طبق العلامة المائية المكوّنة على المخطط المحمّل واكتب الملف المحمي إلى القرص.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

**تعريف مرساة:** `Watermarker` هو الفئة الأساسية التي تنسق عمليات التحميل، إضافة العلامة المائية، والحفظ للأنواع المدعومة من الملفات.

## التطبيقات العملية
إدراج العلامات المائية ذو قيمة في العديد من السيناريوهات الواقعية:
- **حماية الملكية الفكرية:** منع المنافسين من إعادة استخدام المخططات المملوكة.  
- **تعزيز العلامة التجارية:** عرض اسم شركتك على جميع المخططات المصدرة.  
- **الامتثال القانوني:** وضع علامة على المخططات السرية بعبارة “سري – لا للتوزيع”.  
- **النزاهة الأكاديمية:** وضع علامة على طلبات الطلاب بمعرفات فريدة.

يمكنك دمج سير العمل هذا في أنظمة إدارة المستندات، خطوط أنابيب CI، أو خدمات المعالجة الدفعية لأتمتة الحماية عبر آلاف الملفات.

## اعتبارات الأداء
- **تحسين الذاكرة:** أعد استخدام كائنات `Watermarker` حيثما أمكن وأغلقها باستخدام `watermarker.close()` لتحرير الموارد الأصلية.  
- **معالجة الملفات الكبيرة:** تعالج المكتبة الصفحات عند الطلب، لذا حتى المخططات التي تحتوي على 300 صفحة تبقى تحت 200 ميغابايت من استهلاك الذاكرة في JVM عادية بسعة 8 جيجابايت.  
- **سلامة الخيوط:** يجب على كل خيط العمل مع كائن `Watermarker` الخاص به؛ الـ API غير متزامن على مستوى عالمي.

## الأسئلة المتكررة
**س: ما هو أفضل حجم خط للعلامة المائية في المخطط؟**  
ج: حجم يتراوح بين 14 pt و 24 pt يوازن بين قابلية القراءة وعدم الإزعاج لمعظم أبعاد المخطط.

**س: هل يمكنني تغيير لون العلامة المائية؟**  
ج: نعم – استخدم `textWatermark.setColor(Color.BLUE)` (أو أي `java.awt.Color`) لتخصيص اللون.

**س: كيف يمكنني معالجة دفعة كبيرة من المخططات؟**  
ج: قم بالتكرار عبر مجموعة الملفات الخاصة بك وأعد استخدام كائن `Watermarker` واحد لكل خيط، مع استدعاء `watermarker.add()` لكل مستند قبل الحفظ.

**س: هل هناك أي قيود على الصيغ؟**  
ج: يدعم GroupDocs.Watermark أكثر من 50 صيغة، بما في ذلك Visio (.vsdx)، SVG، PNG، و JPEG. راجع القائمة الكاملة في [الوثائق الرسمية](https://docs.groupdocs.com/watermark/java/).

**س: أين يمكنني الحصول على المساعدة إذا واجهت مشاكل؟**  
ج: انشر أسئلتك في منتدى المجتمع: [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10).

## الموارد
- **الوثائق:** [وثائق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API:** [مرجع API لجافا](https://reference.groupdocs.com/watermark/java)  
- **التنزيل:** [احصل على GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GitHub:** [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى الدعم المجاني:** [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10)  
- **ترخيص مؤقت:** [احصل على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)  

نفّذ الخطوات أعلاه لحماية أصول المخططات الخاصة بك بعلامة مائية نصية احترافية. جرّب خطوطًا وألوانًا وخيارات وضع مختلفة لتتناسب مع إرشادات علامتك التجارية، وفكّر في أتمتة العملية لمكتبات المستندات الكبيرة.

---

**آخر تحديث:** 2026-08-31  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## الدروس ذات الصلة

- [دليل إضافة علامات مائية إلى المخططات باستخدام GroupDocs.Watermark للغة Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [كيفية إضافة علامة مائية نصية إلى ملفات PDF باستخدام GroupDocs.Watermark للغة Java: دليل خطوة بخطوة](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-groupdocs-java/)
- [كيفية إضافة علامات مائية نصية إلى صور مستندات Word باستخدام GroupDocs.Watermark للغة Java](/watermark/java/image-watermarks/add-watermarks-word-images-groupdocs-java/)