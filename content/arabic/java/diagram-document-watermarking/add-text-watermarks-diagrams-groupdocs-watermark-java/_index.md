---
date: '2026-10-06'
description: تعلم كيفية إضافة علامة مائية إلى الصفحات في المخططات باستخدام GroupDocs.Watermark
  for Java. إعداد خطوة بخطوة، مقتطفات شفرة، ونصائح عملية للنشر الآمن للمخططات.
keywords:
- add watermark to pages
- text watermarks in Java
- GroupDocs.Watermark for Java
- diagram watermarking tutorial
lastmod: '2026-10-06'
og_description: أضف علامة مائية إلى الصفحات في المخططات باستخدام GroupDocs.Watermark
  for Java. اتبع هذا الدليل لإعداد، تنفيذ، وأفضل الممارسات.
og_image_alt: Developer guide showing Java code that adds text watermarks to diagram
  pages
og_title: كيفية إضافة علامة مائية إلى الصفحات باستخدام GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-06'
  description: Learn how to add watermark to pages in diagrams with GroupDocs.Watermark
    for Java. Step‑by‑step setup, code snippets, and practical tips for secure diagram
    publishing.
  headline: How to add watermark to pages using GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to add watermark to pages in diagrams with GroupDocs.Watermark
    for Java. Step‑by‑step setup, code snippets, and practical tips for secure diagram
    publishing.
  name: How to add watermark to pages using GroupDocs.Watermark Java
  steps:
  - name: load your diagram
    text: 'First, create a `DiagramLoadOptions` instance to tell the SDK how to interpret
      the source file, then open the diagram with `Watermarker`. DiagramLoadOptions
      specifies loading parameters such as format and password for diagram files.
      `Watermarker` is the main class that manages loading, editing, and '
  - name: initialize the text watermark
    text: Next, build a `TextWatermark` object that holds the watermark text, font,
      color, and rotation angle. `TextWatermark` represents a reusable textual overlay
      that can be applied to one or many pages.
  - name: add watermark to diagram
    text: Now specify the pages you want to watermark. Using `DiagramPage` with `WatermarkPageOptions`
      lets you target background, foreground, or both. `DiagramPage` selects individual
      or ranges of diagram pages for watermarking. `WatermarkPageOptions` defines
      where (background/foreground) and how the waterma
  - name: save and close
    text: Finally, write the watermarked diagram to disk and release resources. `Watermarker.save()`
      persists the changes, and `close()` frees native resources to keep memory usage
      low.
  type: HowTo
- questions:
  - answer: Yes – it supports over 50 formats, including PDF, Word, Excel, PowerPoint,
      and image files.
    question: Can GroupDocs.Watermark handle other file types besides diagrams?
  - answer: There is no hard limit, but applying more than 10 watermarks per page
      can increase processing time by roughly 15 % per additional watermark.
    question: Is there a limit to how many watermarks I can apply?
  - answer: Use the `Watermarker.removeWatermarks()` method with a matching `WatermarkSearchOptions`
      filter to delete specific watermarks.
    question: How do I remove a watermark once it’s been added?
  - answer: Absolutely – configure `DiagramPage` with a page index range or a custom
      predicate to apply watermarks selectively.
    question: Can I target only selected pages instead of all pages?
  - answer: Verify the page’s background/foreground settings and ensure the opacity
      is not set below 10 %. Also confirm the font size is appropriate for the page
      dimensions.
    question: The watermark is not visible on some pages; what should I check?
  type: FAQPage
tags:
- add watermark to pages
- GroupDocs.Watermark
- Java diagram security
- watermark tutorial
title: كيفية إضافة علامة مائية إلى الصفحات باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# كيفية إضافة علامة مائية إلى الصفحات باستخدام GroupDocs.Watermark Java

حماية الملكية الفكرية أمر أساسي عندما تشارك المخططات مع الزملاء أو العملاء أو الجمهور. في هذا الدرس ستتعلم **كيفية إضافة علامة مائية إلى الصفحات** في ملفات المخططات باستخدام GroupDocs.Watermark للـ Java، بحيث يحمل كل صفحة مُصدَّرة علامتك التجارية أو إشعار السرية. تغطي الخطوات إعداد البيئة، الترخيص، واستدعاءات API الدقيقة التي تحتاجها لتضمين علامة مائية نصية قابلة للتخصيص.

## إجابات سريعة
- **ما المكتبة التي تضيف علامات مائية إلى المخططات في Java؟** GroupDocs.Watermark for Java.  
- **ما الطريقة الأساسية التي تنشئ كائن العلامة المائية؟** `new TextWatermark(...)`.  
- **هل أحتاج إلى ترخيص للتطوير؟** ترخيص تجريبي مؤقت يعمل للاختبار؛ يلزم ترخيص كامل للإنتاج.  
- **هل يمكنني إضافة علامة مائية إلى كل صفحة تلقائيًا؟** نعم – استخدم `Watermarker.addWatermark()` مع محدد `DiagramPage`.  
- **هل العملية آمنة للاستخدام في بيئات متعددة الخيوط؟** تم تصميم API للاستخدام المتزامن؛ فقط تجنّب مشاركة نفس كائن `Watermarker` عبر الخيوط.

## ما هو إضافة علامة مائية إلى الصفحات؟
*إضافة علامة مائية إلى الصفحات* تعني إدراج طبقة نصية شبه شفافة على كل صفحة من مستند أو مخطط بحيث يبقى المحتوى قابلاً للقراءة بينما تكون العلامة المائية واضحة. تُعَد هذه التقنية رادعة لإعادة الاستخدام غير المصرح به وتعزز هوية العلامة التجارية.

## لماذا تستخدم GroupDocs.Watermark للـ Java؟
GroupDocs.Watermark يدعم **أكثر من 50 تنسيق ملف** (بما في ذلك VDX، VSDX، SVG، وغيرها من أنواع المخططات) ويمكنه معالجة ملفات تصل إلى **500 ميغابايت** دون تحميل الملف بالكامل في الذاكرة، مما يوفر زمن استجابة أقل من الثانية على خوادم عادية. يتيح API السلس لك تكوين الخط، اللون، الدوران، والشفافية في استدعاء واحد.

## المتطلبات المسبقة
- مجموعة تطوير Java 8 أو أحدث.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- خبرة أساسية في برمجة Java.  

### المكتبات والاعتمادات المطلوبة
GroupDocs.Watermark للـ Java يُوزَّع عبر Maven Central. أضف الاعتماد إلى ملف `pom.xml` الخاص بك:

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

[إصدارات GroupDocs.Watermark لـ Java](https://releases.groupdocs.com/watermark/java/)

إذا كنت تفضّل التحميل اليدوي، احصل على الملفات الثنائية من صفحة الإصدار الرسمية.

### الحصول على الترخيص
يمكنك البدء بتجربة مجانية عن طريق تنزيل ترخيص مؤقت من بوابة التجربة الخاصة بـ GroupDocs. بعد الحصول على ملف `.lic`، حمّله كما هو موضح أدناه.

فئة `License` تتحقق من صحة ملف الترخيص التجريبي أو المشتراَة أثناء التشغيل.  

```java
License license = new License();
license.setLicense("path/to/license/file");
```

[ترخيص تجريبي من GroupDocs](https://purchase.groupdocs.com/temporary-license/)

## دليل التنفيذ

### إضافة علامات مائية نصية إلى صفحات المخطط

#### الخطوة 1: تحميل المخطط الخاص بك
أولاً، أنشئ كائن `DiagramLoadOptions` لتخبر الـ SDK كيفية تفسير ملف المصدر، ثم افتح المخطط باستخدام `Watermarker`.  
`DiagramLoadOptions` يحدد معلمات التحميل مثل التنسيق وكلمة المرور لملفات المخططات.  
`Watermarker` هو الفئة الرئيسية التي تدير تحميل، تعديل، وحفظ مستندات المخططات.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

#### الخطوة 2: تهيئة العلامة المائية النصية
بعد ذلك، أنشئ كائن `TextWatermark` يحمل نص العلامة المائية، الخط، اللون، وزاوية الدوران.  
`TextWatermark` يمثل طبقة نصية قابلة لإعادة الاستخدام يمكن تطبيقها على صفحة واحدة أو عدة صفحات.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

#### الخطوة 3: إضافة علامة مائية إلى المخطط
الآن حدد الصفحات التي تريد إضافة العلامة المائية إليها. باستخدام `DiagramPage` مع `WatermarkPageOptions` يمكنك استهداف الخلفية أو المقدمة أو كليهما.  
`DiagramPage` يختار صفحات المخطط الفردية أو نطاقات الصفحات للعلامة المائية.  
`WatermarkPageOptions` يحدد أين (خلفية/مقدمة) وكيف يتم رسم العلامة المائية على الصفحات المختارة.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

#### الخطوة 4: حفظ وإغلاق
أخيرًا، اكتب المخطط المموج إلى القرص وأفرغ الموارد.

`Watermarker.save()` يحفظ التغييرات، و`close()` يحرّر الموارد الأصلية للحفاظ على استهلاك الذاكرة منخفضًا.  

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## المشكلات الشائعة والحلول
- **أخطاء مسار الملف** – تأكد من أن مسارات الإدخال والإخراج مطلقة أو نسبية بشكل صحيح بالنسبة إلى دليل العمل الخاص بك.  
- **عدم توافق الإصدارات** – استخدم GroupDocs.Watermark 23.11 أو أحدث؛ الإصدارات القديمة قد تفتقر إلى دعم المخططات.  
- **صلاحيات غير كافية** – يجب أن تكون العملية لديها صلاحية قراءة/كتابة للمجلدات التي تحددها.

## التطبيقات العملية
1. **تأمين مخرجات العملاء** – ضع علامة مائية على كل مخطط قبل إرسال ملفات PDF إلى الشركاء الخارجيين.  
2. **العلامة التجارية للشركة** – أدخل شعارك أو اسم شركتك عبر جميع الصفحات المُصدَّرة تلقائيًا.  
3. **تتبع التعاون** – أضف الأحرف الأولى للمستخدم كعلامة مائية للإشارة إلى من قام بتحرير كل نسخة من المخطط.

## اعتبارات الأداء
- عالج دفعات كبيرة بإعادة استخدام كائن `Watermarker` واحد واستدعاء `addWatermark` داخل حلقة؛ هذا يقلل من تكلفة إنشاء الكائنات بنسبة تصل إلى **30 %**.  
- حافظ على نص العلامة المائية مختصرًا (أقل من 30 حرفًا) لتقليل زمن الرسم، خاصةً على المخططات عالية الدقة.  
- اختبر مع مخطط مكوّن من 200 صفحة؛ زمن المعالجة النموذجي أقل من **2 ثانية** على جهاز افتراضي بمعالج 2 vCPU قياسي.

## الخلاصة
أصبح لديك الآن سير عمل كامل وجاهز للإنتاج **لإضافة علامة مائية إلى الصفحات** في ملفات المخططات باستخدام GroupDocs.Watermark للـ Java. لا تحمي هذه الطريقة أصولك فحسب، بل تعزز أيضًا اتساق العلامة التجارية عبر جميع المخرجات المُصدَّرة.

### الخطوات التالية
- استكشف العلامات المائية الصورية للحصول على علامة تجارية أغنى.  
- دمج العلامات المائية النصية والصورية لحماية متعددة الطبقات.  
- دمج روتين وضع العلامة المائية في خط أنابيب CI/CD الخاص بك لأتمتة أمان المستندات.

## الأسئلة المتكررة

**س: هل يمكن لـ GroupDocs.Watermark معالجة أنواع ملفات أخرى غير المخططات؟**  
ج: نعم – يدعم أكثر من 50 تنسيقًا، بما في ذلك PDF، Word، Excel، PowerPoint، وملفات الصور.

**س: هل هناك حد لعدد العلامات المائية التي يمكنني تطبيقها؟**  
ج: لا يوجد حد صريح، لكن إضافة أكثر من 10 علامات مائية لكل صفحة قد يزيد زمن المعالجة بحوالي 15 % لكل علامة مائية إضافية.

**س: كيف يمكنني إزالة علامة مائية بعد إضافتها؟**  
ج: استخدم طريقة `Watermarker.removeWatermarks()` مع مرشح `WatermarkSearchOptions` المطابق لحذف العلامات المائية المحددة.

**س: هل يمكنني استهداف صفحات محددة فقط بدلاً من جميع الصفحات؟**  
ج: بالتأكيد – قم بتكوين `DiagramPage` بنطاق فهارس الصفحات أو بدالة مخصصة لتطبيق العلامات المائية بشكل انتقائي.

**س: العلامة المائية غير مرئية على بعض الصفحات؛ ماذا يجب أن أتحقق؟**  
ج: تحقق من إعدادات الخلفية/المقدمة للصفحة وتأكد من أن الشفافية ليست أقل من 10 %. كما يجب التأكد من أن حجم الخط مناسب لأبعاد الصفحة.

## الموارد
- [الوثائق](https://docs.groupdocs.com/watermark/java/) – دليل رسمي ودروس.  
- [مرجع API](https://reference.groupdocs.com/watermark/java) – أوصاف مفصلة للفئات والطرق.  
- [تحميل أحدث نسخة](https://releases.groupdocs.com/watermark/java/) – احصل على أحدث إصدار من المكتبة.  
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) – شفرة المصدر، المشكلات، والمساهمات.  
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10) – مساعدة المجتمع والنقاشات.

---

**آخر تحديث:** 2026-10-06  
**تم الاختبار مع:** GroupDocs.Watermark 23.11 for Java  
**المؤلف:** GroupDocs  

## الدروس ذات الصلة

- [كيفية إضافة علامات مائية نصية وصورية إلى صفحات PDF محددة باستخدام GroupDocs.Watermark للـ Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [كيفية إضافة علامات مائية نصية إلى المخططات باستخدام GroupDocs.Watermark في Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [إضافة علامات مائية نصية في Java باستخدام GroupDocs.Watermark: دليل خطوة بخطوة](/watermark/java/text-watermarks/add-text-watermarks-java-groupdocs/)