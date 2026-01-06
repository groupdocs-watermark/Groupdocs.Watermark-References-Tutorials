---
date: '2025-12-20'
description: تعلم كيفية استخراج معلومات الشكل باستخدام GroupDocs.Watermark للغة Java.
  استرجع الأبعاد والمواقع والنص من ملفات المخططات بكفاءة.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 'استخراج معلومات الشكل جافا: استخدام GroupDocs.Watermark للرسوم البيانية'
type: docs
url: /ar/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# استخراج معلومات الشكل Java باستخدام GroupDocs.Watermark في المخططات

عند الحاجة إلى **استخراج معلومات الشكل java** من ملفات المخططات المعقدة، يصبح التنفيذ اليدوي غير عملي بسرعة. يوضح هذا الدليل كيفية الاستفادة من GroupDocs.Watermark للـ Java لسحب تفاصيل مثل الأبعاد، المواقع، زوايا الدوران، الصور المدمجة، والنص من كل شكل برمجياً. في النهاية، ستحصل على نمط واضح وقابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java يعمل مع مخططات على نمط Visio.

## المقدمة

إدارة المخططات المعقدة غالباً ما تتطلب الوصول إلى معلومات مفصلة حول مكوناتها، مثل الأشكال والصور. إذا احتجت يوماً إلى استرجاع البيانات برمجياً مثل الأبعاد، المواقع، أو النص المرتبط بأشكال المخطط باستخدام Java، فهذا الدليل لك. الاستفادة من قوة مكتبة GroupDocs.Watermark يمكن أن تبسط هذه العملية في تطبيق Java. في هذا الدليل، سنستعرض كيفية استخدام GroupDocs.Watermark **لاستخراج معلومات الشكل java** من ملف مخطط.

## إجابات سريعة
- **ما المكتبة التي يجب استخدامها؟** GroupDocs.Watermark للـ Java (الإصدار 24.11 أو أعلى).  
- **ما صيغ الملفات المدعومة؟** Visio (.vsdx, .vsd) وأنواع المخططات الأخرى المذكورة في وثائق الـ API.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتطوير؛ الترخيص التجاري مطلوب للإنتاج.  
- **هل يمكنني الحصول على بيانات الصورة من الأشكال؟** نعم – الـ API يوفر عرض الصورة، ارتفاعها، والبيانات الخام للبايت.  
- **هل Maven مطلوب؟** Maven هو الطريقة الموصى بها لإدارة تبعية GroupDocs.Watermark.

## ما هو “استخراج معلومات الشكل java”؟

استخراج معلومات الشكل java يعني قراءة ملف مخطط برمجياً واستخراج خصائص كل شكل—الحجم، الموقع، الدوران، النص، وأي صور مدمجة—باستخدام كود Java. يتيح ذلك التحليل الآلي، إعداد التقارير، أو التكامل مع أنظمة أخرى مثل أدوات CAD أو خطوط أنابيب تصور البيانات.

## لماذا نستخدم GroupDocs.Watermark لهذه المهمة؟

توفر GroupDocs.Watermark تجريدًا عالي المستوى فوق صيغ المخططات، حيث تتولى التحليل منخفض المستوى بدلاً منك. يتيح لك التركيز على منطق الأعمال بدلاً من التعامل مع XML أو المواصفات الثنائية، ويعمل بشكل ثابت عبر أنواع المخططات المدعومة.

## المتطلبات المسبقة

- **GroupDocs.Watermark للـ Java** (الإصدار 24.11 أو أحدث)  
- مجموعة تطوير Java (JDK) 8 أو أعلى  
- Maven لإدارة التبعيات  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse  

## إعداد GroupDocs.Watermark للـ Java

أضف المستودع والتبعية إلى ملف `pom.xml` الخاص بـ Maven:

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

بدلاً من ذلك، يمكنك تحميل أحدث نسخة مباشرةً من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### خطوات الحصول على الترخيص
- **نسخة تجريبية:** حمّل حزمة تجريبية لاختبار المكتبة.  
- **ترخيص مؤقت:** احصل على مفتاح مؤقت لتقييم ممتد.  
- **شراء:** احصل على ترخيص كامل للاستخدام في الإنتاج.

### التهيئة الأساسية

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## دليل التنفيذ

الآن دعنا نتبع الخطوات الدقيقة **لاستخراج معلومات الشكل java** من مستند مخطط.

### تحميل المحتوى واسترجاعه

#### نظرة عامة
نقوم أولاً بتحميل ملف المخطط والحصول على كائن `DiagramContent`، الذي يتيح لنا الوصول إلى الصفحات والأشكال.

#### الخطوات

**تحميل مستند المخطط**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **السبب:** هذا يهيئ كائن `Watermarker`، مما يسمح بالوصول إلى محتوى المستند.

**الوصول إلى محتوى المخطط**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **السبب:** فئة `DiagramContent` توفر طرقًا للتفاعل مع جوانب مختلفة من المخطط، مثل الصفحات والأشكال.

### التكرار عبر الأشكال

#### نظرة عامة
مع وجود `DiagramContent` في يدنا، نقوم بالتكرار عبر كل صفحة ثم كل شكل لاستخراج الخصائص المطلوبة.

#### الخطوات

**التكرار عبر الصفحات**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **السبب:** المخططات تتكون من عدة صفحات؛ نحتاج إلى فحص كل واحدة للحصول على أشكالها.

**استخراج معلومات الشكل**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **السبب:** هذا التكرار يستخرج ويطبع خصائص كل شكل، بما في ذلك الأبعاد، الموقع، الدوران، وأي صور أو نص مدمج. هذه السمات حيوية لفهم كيفية تكوين الأشكال داخل المخطط.

### نصائح استكشاف الأخطاء وإصلاحها
- تأكد من صحة مسار الملف وأنه يشير إلى ملف `.vsdx` (أو مدعوم) قابل للقراءة.  
- تأكد من أن التطبيق يمتلك أذونات قراءة لملف المخطط.  
- إذا واجهت أخطاء “تنسيق غير مدعوم”، تحقق من أن إصدار GroupDocs.Watermark الخاص بك يدعم نوع المخطط المحدد.

## تطبيقات عملية

مع القدرة على **استخراج معلومات الشكل java**، يمكنك تمكين مجموعة متنوعة من السيناريوهات الواقعية:

1. **تحليل المخططات:** توليد تقارير تلقائية تسرد حجم كل شكل، موقعه، ونصه—مفيد لتدقيق الجودة.  
2. **تصور البيانات:** إمداد مقاييس الأشكال إلى لوحات التحكم لتصور كثافة التخطيط أو تحديد العناصر ذات الحجم الزائد.  
3. **تكامل CAD:** ربط بيانات المخطط إلى خطوط أنابيب CAD، مما يتيح إعادة تصميم أو خطوات تحقق آلية.

## اعتبارات الأداء

عند معالجة مخططات كبيرة، احرص على اتباع أفضل الممارسات التالية:

- **إغلاق الموارد بسرعة:** استدعِ `watermarker.close()` (أو استخدم try‑with‑resources) لتحرير الذاكرة.  
- **مراقبة استهلاك الـ Heap:** المخططات الكبيرة قد تستهلك ذاكرة كبيرة؛ عدّل حجم heap للـ JVM (`-Xmx`) حسب الحاجة.  
- **المعالجة على دفعات:** عالج الملفات على دفعات بدلاً من تحميل العشرات في آن واحد.

## الخلاصة

باتباع هذا الدليل، أصبحت الآن تعرف كيفية **استخراج معلومات الشكل java** باستخدام GroupDocs.Watermark للـ Java. يمكنك استرجاع الأبعاد، المواقع، زوايا الدوران، الصور المدمجة، والنص من أي ملف مخطط مدعوم، مما يفتح الباب أمام التحليل الآلي، إعداد التقارير، والتكامل مع أنظمة أكبر. جاهز للخطوة التالية؟ استكشف الإمكانات الكاملة للمكتبة في [الوثائق الرسمية](https://docs.groupdocs.com/watermark/java/) وجرب إضافة العلامات المائية، الإخفاء، أو تعديل الأشكال المخصص.

## الأسئلة المتكررة

**س: ما هو GroupDocs.Watermark؟**  
ج: مكتبة Java شاملة مصممة للعلامات المائية واستخراج المعلومات من صيغ مستندات متعددة، بما في ذلك المخططات.

**س: هل يمكنني استخدام هذه المكتبة لمعالجة جميع أنواع ملفات المخططات؟**  
ج: نعم، لكن تأكد من أن صيغة الملف مدرجة كمدعومة في [API Reference](https://reference.groupdocs.com/watermark/java/).

**س: كيف يمكنني استخراج أبعاد ومواقع الأشكال من مخطط باستخدام Java وGroupDocs.Watermark؟**  
ج: حمّل المخطط، احصل على `DiagramContent`، ثم تكرّر عبر كل `DiagramShape` لقراءة الخصائص مثل العرض، الارتفاع، X، وY.

**س: هل يمكن لـ GroupDocs.Watermark استخراج الصور المدمجة في أشكال المخطط باستخدام Java؟**  
ج: نعم، توفر المكتبة طرقًا للوصول إلى بيانات الصورة داخل الأشكال، بما في ذلك الحجم ومصفوفة البايت الخام، والتي يمكنك استخدامها للتحليل أو التعديل.

**س: ما هي المتطلبات المسبقة لاستخراج معلومات شكل المخطط في Java؟**  
ج: Java JDK 8+، إعداد Maven، مكتبة GroupDocs.Watermark (24.11+)، ومعرفة أساسية ببرمجة Java.

---

**آخر تحديث:** 2025-12-20  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs  

---