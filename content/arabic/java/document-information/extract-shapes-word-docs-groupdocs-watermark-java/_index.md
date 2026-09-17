---
date: '2026-02-05'
description: تعلم كيفية استخراج الأشكال من مستندات Word باستخدام GroupDocs.Watermark
  للغة Java، بما في ذلك كيفية تحميل مستند Word في Java ومعالجة بيانات الشكل.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: كيفية استخراج الأشكال من مستندات Word باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# كيفية استخراج الأشكال من مستندات Word باستخدام GroupDocs.Watermark في Java

في هذا الدرس ستكتشف **كيفية استخراج الأشكال** من مستندات Word باستخدام مكتبة GroupDocs.Watermark للـ Java. سواءً كنت بحاجة إلى تحليل المخططات، استخراج الصور المدمجة، أو أتمتة إنشاء التقارير، فإن استخراج بيانات الأشكال يمنحك التحكم لبناء خطوط معالجة مستندات أكثر ذكاءً. سنستعرض إعداد المكتبة، تحميل مستند Word، واستخراج معلومات مفصلة عن الأشكال—كل ذلك في كود Java واضح خطوة بخطوة.

## إجابات سريعة
- **ماذا يعني “استخراج الأشكال”؟** استرجاع البيانات الوصفية (النوع، الحجم، الموقع، النص، الصور) لكل عنصر رسم في ملف Word.  
- **ما المكتبة التي تتعامل مع ذلك؟** GroupDocs.Watermark للـ Java.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية تعمل للتطوير؛ الترخيص الكامل يزيل حدود الاستخدام.  
- **هل يمكنني أيضًا الحصول على الصور من الأشكال؟** نعم – الـ API يتيح بايتات الصورة للأشكال من نوع picture.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أحدث.

## ما هو “كيفية استخراج الأشكال” في سياق مستندات Word؟
استخراج الأشكال يعني الوصول برمجياً إلى كل عنصر رسم—الصور، WordArt، الأشكال التلقائية، المخططات، وحتى الأشكال المدمجة في رؤوس أو تذييلات الصفحات. يمكن استخدام هذه المعلومات للتحقق، الترحيل، أو التحليلات المدفوعة بالمحتوى.

## لماذا نستخدم GroupDocs.Watermark للـ Java؟
GroupDocs.Watermark توفر API عالي المستوى وفعال في الذاكرة يُجرد التعقيد من تنسيق Office Open XML الأساسي. يتيح لك:
- تحميل المستندات بسرعة (`WordProcessingLoadOptions`).  
- التنقل عبر الأقسام والأشكال دون التعامل مع XML منخفض المستوى.  
- استرجاع بيانات الصورة، النص، المحاذاة، والدوران في استدعاء واحد.  
- التكامل بسلاسة مع خدمات Java الحالية أو الميكرو‑خدمات.

## المتطلبات المسبقة
- **Java Development Kit (JDK)** 8 أو أعلى.  
- **IDE** مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java I/O.  
- الوصول إلى ترخيص **GroupDocs.Watermark للـ Java** أو نسخة تجريبية.

## إعداد GroupDocs.Watermark للـ Java
دمج المكتبة عبر Maven أو تحميل مباشر.

### استخدام Maven
أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، قم بتحميل أحدث JAR من [GroupDocs.Watermark لإصدارات Java](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
النسخة التجريبية المجانية كافية للاختبار. للإنتاج، اطلب ترخيصًا دائمًا لفتح جميع الميزات.

## دليل التنفيذ
سنقسم التنفيذ إلى خطوتين واضحيتين: **تحميل مستند Word** و **استخراج معلومات الشكل**.

### الخطوة 1: تحميل مستند Word (load word document java)
أولاً، قم بتهيئة خيارات التحميل وإنشاء كائن `Watermarker`. هذا يُعد المستند للمزيد من الفحص.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **نصيحة احترافية:** احتفظ بنطاق كائن `Watermarker` بأصغر ما يمكن؛ إغلاقه فورًا يحرر الموارد الأصلية ويجنب تسرب الذاكرة.

### الخطوة 2: استخراج معلومات الشكل (extract images from shapes)
الآن سنستخرج تفاصيل كل شكل، بما في ذلك أي صور مدمجة. يتنقل الكود عبر كل قسم وكل شكل، ويطبع البيانات الوصفية المفيدة.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**ما يفعله هذا الكود:**  
- يسترجع **نوع** كل شكل (مثلاً picture، WordArt).  
- يطبع قيم **الحجم**، **الموقع**، و**الدوران**.  
- يعرض **النص البديل** و**الاسم**، وهما مفيدان لفحوصات إمكانية الوصول.  
- إذا كان الشكل يحتوي على صورة، يطبع **أبعاد البكسل** و**حجم البايت** للصورة—مثالي لاستخراج الصور من الأشكال.

### الأخطاء الشائعة وكيفية إصلاحها
| المشكلة | السبب | الحل |
|-------|-------|----------|
| `FileNotFoundException` | مسار الملف غير صحيح أو أذونات مفقودة | تحقق من المسار المطلق/النسبي وتأكد من أن الملف قابل للقراءة. |
| Null `shape.getImage()` | الشكل ليس صورة (مثلاً auto‑shape) | استخدم شرط `if (shape.getImage() != null)` كما هو موضح. |
| استخدام عالي للذاكرة في المستندات الكبيرة | تحميل المستند بالكامل مرة واحدة | معالجة الأقسام واحدةً تلو الأخرى أو زيادة حجم heap للـ JVM (`-Xmx`). |
| عدم وجود أشكال في الرأس/التذييل | عدم التحقق من `shape.getHeaderFooter()` | العينة تسجل بالفعل عندما يكون الشكل جزءًا من رأس أو تذييل. |

## التطبيقات العملية
1. **إنشاء تقارير تلقائي** – استخراج المخططات والرسوم لتضمينها في ملفات PDF لاحقة.  
2. **تدقيق الامتثال** – التحقق من أن جميع الأشكال تحتوي على نص بديل مناسب لإمكانية الوصول.  
3. **ترحيل المحتوى** – تصدير الصور المدمجة من ملفات Word القديمة إلى نظام إدارة الأصول الرقمية.  

## اعتبارات الأداء
- **تحرير الموارد**: دائمًا استدعِ `watermarker.close()` داخل كتلة `finally` أو استخدم try‑with‑resources إذا قمت بلف الـ API.  
- **معالجة على دفعات**: للمستندات التي تتجاوز 50 MB، فكر في معالجة كل قسم على حدة لتقليل استهلاك الذاكرة.  
- **سلامة الخيوط**: كائنات `Watermarker` غير آمنة للاستخدام المتعدد الخيوط؛ أنشئ كائنًا جديدًا لكل خيط.

## الخلاصة
أنت الآن تعرف **كيفية استخراج الأشكال** من مستندات Word باستخدام GroupDocs.Watermark للـ Java، بدءًا من تحميل الملف إلى قراءة بيانات كل شكل والبيانات المدمجة للصور. هذه القدرة تفتح أبوابًا للتحليلات المتقدمة للمستندات، خطوط المحتوى الآلية، والتحقق من إمكانية الوصول.

### الخطوات التالية
- جرّب تعديل خصائص الشكل (مثل تغيير الحجم أو إعادة التحديد).  
- دمج هذا النهج مع **GroupDocs.Parser** لاستخراج النص المحيط.  
- دمج منطق الاستخراج في خدمة REST للمعالجة عند الطلب.

## قسم الأسئلة المتكررة
**س: ما هو GroupDocs.Watermark للـ Java؟**  
ج: إنها مكتبة شاملة صُممت لإدارة العلامات المائية ومحتوى المستندات عبر الصيغ، مما يتيح مهامًا مثل استخراج الأشكال، استرجاع الصور، وتعديل النص.

**س: هل يمكنني استخراج الصور من الأشكال بدون ترخيص؟**  
ج: النسخة التجريبية تسمح بالاستخراج، لكن الترخيص الكامل يزيل حدود الاستخدام ويفتح إمكانية النشر التجاري.

**س: هل يعمل هذا مع ملفات `.doc` (ثنائية)؟**  
ج: نعم، الـ API يدعم كلًا من صيغ `.docx` و `.doc` القديمة.

**س: كيف أتعامل مع المستندات المحمية بكلمة مرور؟**  
ج: قدّم كلمة المرور عبر `WordProcessingLoadOptions.setPassword("yourPassword")` قبل إنشاء كائن `Watermarker`.

**س: هل هناك طريقة لتصدير بيانات الأشكال المستخرجة إلى JSON؟**  
ج: يمكنك تحويل القيم المطبوعة إلى POJO واستخدام أي مكتبة JSON (مثل Jackson) لتسلسل المجموعة.

---

**آخر تحديث:** 2026-02-05  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs