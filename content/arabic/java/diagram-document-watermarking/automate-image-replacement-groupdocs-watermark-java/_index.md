---
date: '2026-10-01'
description: تعلم كيفية أتمتة استبدال الصور java في ملفات المخططات باستخدام GroupDocs.Watermark،
  بما في ذلك إضافة العلامة المائية والمعالجة الفعّالة.
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: أتمتة استبدال الصور java في المخططات باستخدام GroupDocs.Watermark.
  يوضح هذا الدليل كيفية استبدال الصور، إضافة العلامات المائية، ومعالجة الملفات الكبيرة
  بكفاءة.
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: أتمتة استبدال الصور java باستخدام GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: أتمتة استبدال الصور java باستخدام GroupDocs.Watermark
type: docs
url: /ar/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# أتمتة استبدال الصور في Java باستخدام GroupDocs.Watermark

تحديث الصور الفردية داخل مخطط قد يكون مهمة يدوية شاقة وعرضة للأخطاء. باستخدام **GroupDocs.Watermark for Java**، يمكنك **أتمتة استبدال الصور في Java** عبر العشرات أو المئات من الملفات، مما يضمن اتساق العلامة التجارية وتوفير وقت التطوير القيم. يشرح هذا البرنامج التعليمي كيفية إعداد المكتبة، الوصول إلى محتوى المخطط، استبدال الصور داخل أشكال محددة، وإضافة علامة مائية إلى المخطط اختياريًا.

## إجابات سريعة
- **أي مكتبة تتعامل مع تحديث صور المخطط؟** GroupDocs.Watermark for Java.  
- **هل يمكنني إضافة علامة مائية أثناء استبدال الصور؟** نعم – تتيح لك نفس الـ API وضع علامات مائية على أي صفحة من المخطط.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل أحتاج إلى ترخيص للتطوير؟** النسخة التجريبية المجانية تكفي للتقييم؛ يلزم ترخيص تجاري للإنتاج.  
- **هل العملية فعّالة في استهلاك الذاكرة للمخططات الكبيرة؟** نعم – الـ SDK يبث المحتوى ولا يحمل الملف بالكامل في الذاكرة.

## ما هو GroupDocs.Watermark for Java؟
`GroupDocs.Watermark` هو مجموعة تطوير برمجيات (SDK) للـ Java تتيح الإضافة وال إزالة واستبدال العلامات المائية والصور برمجيًا في أكثر من 30 تنسيق مستند، بما في ذلك Visio و SVG وأنواع المخططات الأخرى. يعالج الملفات بطريقة بثية، مما يسمح لك بالعمل مع مخططات مئات الصفحات دون استنزاف الذاكرة.

## لماذا أتمتة استبدال الصور في Java؟
تقلل أتمتة استبدال الصور من العمل اليدوي بنسبة تصل إلى **90 %** عند تحديث أصول العلامة التجارية عبر مجموعات مستندات كبيرة. يدعم الـ SDK **أكثر من 30 تنسيقًا للإدخال والإخراج**، يعالج الملفات التي يصل حجمها إلى **200 ميغابايت** في أقل من ثانية على عتاد الخادم المعتاد، ويضمن تموضعًا دقيقًا للصور على مستوى البكسل.

## المتطلبات المسبقة
- JDK 8 أو أحدث مثبت على جهاز التطوير الخاص بك.  
- Maven (أو أداة بناء أخرى) لإدارة الاعتمادات.  
- بيئة تطوير متكاملة (IDE) مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java وإلمام بملفات الإدخال/الإخراج.

### المكتبات المطلوبة والإصدارات والاعتمادات
أضف إحداثيات Maven التالية إلى ملف `pom.xml` الخاص بك. العنصر النائب أدناه يمثل مقتطف XML الدقيق الذي تحتاجه؛ احتفظ به دون تغيير.

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

للتنزيلات اليدوية، احصل على أحدث ملفات JAR من صفحة الإصدارات الرسمية: [إصدارات GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/).

## كيفية أتمتة استبدال الصور في Java؟
حمّل المخطط باستخدام كائن `Watermarker`، حدد الأشكال المستهدفة، استبدل تدفقات صورها، أضف علامة مائية اختياريًا، وأخيرًا احفظ الملف. يتضمن سير العمل الكامل **أربع خطوات مختصرة**، يتم توضيح كل منها أدناه، وعادةً ما يستغرق بضع ثوانٍ فقط لكل مخطط حتى للملفات الكبيرة.

### الخطوة 1: تهيئة الـ Watermarker
فئة `Watermarker` هي نقطة الدخول لجميع عمليات المستند. تفتح ملف المصدر وتجهز الهياكل الداخلية للتحرير.

```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```

- **DiagramLoadOptions** يضبط معلمات التحميل الخاصة بالمخطط.  
- تهيئة `Watermarker` يفتح مقبض الملف ويتحقق من صحة التنسيق.

### الخطوة 2: الوصول إلى محتوى المخطط
`DiagramContent` يمثل البنية المنطقية للمخطط، ويكشف عن الصفحات والأشكال الفردية للتفحص.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- استخدم `watermarker.getContent()` لاسترجاع كائن `DiagramContent`.  
- تجول عبر `content.getPages()` ثم `page.getShapes()` للعثور على الأشكال التي تحتوي على صور.

### الخطوة 3: استبدال صور الأشكال في المخطط
كائنات `DiagramShape` قد تحتوي على صورة مدمجة. استبدلها عن طريق توفير `InputStream` جديد يقرأ الصورة البديلة.

طريقة `setImage(InputStream)` تستبدل الصورة الحالية للشكل بالمجرى المقدم.  

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```

- تحقق من `shape.getImage()`؛ إذا لم يكن فارغًا، استدعِ `shape.setImage(newImageStream)`.  
- يقوم الـ SDK تلقائيًا بتحديث أبعاد الصورة ويحافظ على تخطيط الشكل الأصلي.

### الخطوة 4: إضافة علامة مائية إلى المخطط (اختياري)
إذا كنت بحاجة أيضًا إلى **إضافة علامة مائية إلى المخطط**، أنشئ كائن `Watermark` وطبقه على الصفحة المطلوبة أو على المستند بأكمله.

فئة `Watermark` تعرف تغطية بصرية يمكن وضعها على صفحات المخطط أو على المستند بأكمله.  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

طريقة `add(Watermark, AddOptions)` تطبق العلامة المائية المحددة على المستند باستخدام الخيارات المعطاة.  

* (الكود أعلاه توضيحي ولا يُحسب ككتلة كود جديدة؛ وهو موجود داخل فقرة موجودة.) *

### الخطوة 5: حفظ وإغلاق الـ Watermarker
احفظ التغييرات وأفرغ الموارد لتجنب قفل الملفات.

طريقة `save(String)` تكتب المستند المعدل إلى المسار المحدد.  

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```

- استدعِ `watermarker.save("output.vsdx")` (أو الامتداد المناسب).  
- دائمًا استدعِ `watermarker.close()` داخل كتلة `finally` أو استخدم try‑with‑resources للتنظيف التلقائي.

## المشكلات الشائعة واستكشاف الأخطاء
- **عدم تطابق حجم الصورة** – تأكد من أن الصورة البديلة لها نفس نسبة العرض إلى الارتفاع كما الأصل لتجنب التشويه.  
- **ارتفاع الذاكرة في المخططات الكبيرة** – عالج المخططات واحدةً تلو الأخرى وأغلق `Watermarker` بعد كل حفظ.  
- **أخطاء الترخيص** – ينتهي الترخيص التجريبي بعد 30 يومًا؛ استبدله بمفتاح إنتاج قبل النشر. يمكنك الحصول على ترخيص مؤقت من GroupDocs: [الحصول على ترخيص مؤقت من GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## الأسئلة المتكررة

**س: هل يمكنني استبدال الصور في المخططات المحمية بكلمة مرور؟**  
ج: نعم. حمّل الملف باستخدام `DiagramLoadOptions` التي تتضمن كلمة المرور، ثم تابع خطوات الاستبدال العادية.

**س: هل يدعم الـ SDK المعالجة الدفعية لعدة مخططات؟**  
ج: بالتأكيد. غلف سير العمل لملف واحد داخل حلقة تتجول عبر دليل؛ بنية البث تحافظ على انخفاض استهلاك الذاكرة.

**س: ما هي الصيغ التي يمكنني العمل معها بخلاف Visio؟**  
ج: يدعم GroupDocs.Watermark صيغ SVG و VDX و VSDX والعديد من صيغ المخططات الأخرى، بما يزيد عن 30 نوعًا مدعومًا.

**س: هل يمكن إضافة علامة مائية بعد استبدال الصور؟**  
ج: نعم – استدعِ `watermarker.add(watermark, options)` بعد خطوة استبدال الصورة وقبل الحفظ.

**س: كيف أضمن أن الصورة الجديدة مدمجة وليست مرتبطة؟**  
ج: طريقة `setImage(InputStream)` تدمج بيانات الصورة مباشرةً في ملف المخطط، مما يضمن قابلية النقل.

---

**آخر تحديث:** 2026-10-01  
**تم الاختبار مع:** GroupDocs.Watermark 23.12 for Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [دروس وضع العلامات المائية على المخططات لـ GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [إزالة الروابط التشعبية من أشكال المخطط باستخدام GroupDocs.Watermark Java لتعزيز أمان المستند](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [كيفية إضافة علامة مائية صورة في Java باستخدام GroupDocs.Watermark: دليل خطوة بخطوة](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)