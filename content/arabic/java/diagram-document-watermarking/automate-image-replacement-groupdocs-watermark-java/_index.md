---
date: '2026-08-19'
description: تعلم كيفية استبدال صور المخطط في Java باستخدام GroupDocs.Watermark، وكذلك
  إضافة علامة مائية إلى المخطط بكفاءة. كود خطوة بخطوة وأفضل الممارسات.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: تعلم كيفية استبدال صور المخطط في Java باستخدام GroupDocs.Watermark،
  وكذلك إضافة علامة مائية إلى المخطط بكفاءة. كود خطوة بخطوة وأفضل الممارسات.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: استبدال صور المخطط في Java باستخدام GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: استبدال صور المخطط في Java باستخدام GroupDocs.Watermark
type: docs
url: /ar/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# استبدال صور المخطط في Java باستخدام GroupDocs.Watermark

تحديث الصور داخل ملفات المخططات يدويًا يستغرق وقتًا طويلاً ومعرض للأخطاء. في هذا الدرس ستتعلم كيفية **استبدال صور المخطط في Java** ببضع أسطر من الشيفرة فقط، وسترى أيضًا كيفية **إضافة علامة مائية إلى المخطط** عند الحاجة. في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java يعمل مع Visio أو Draw.io أو أي صيغ مخططات مدعومة أخرى.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع استبدال صور المخطط؟** GroupDocs.Watermark for Java.
- **كم عدد أسطر الشيفرة المطلوبة للاستبدال الأساسي؟** Only three lines after the Watermarker is created.
- **هل يمكنني إضافة علامة مائية في نفس الوقت؟** Yes – use the same Watermarker instance with a watermark object.
- **ما نسخة Java المطلوبة؟** JDK 8 or higher.
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** A valid GroupDocs.Watermark license is required; a free trial is available.

## ما هو استبدال صور المخطط في Java؟
استبدال صور المخطط في Java يعني العثور برمجيًا على الأشكال التي تحتوي على رسومات نقطية داخل ملف مخطط (مثل .vsdx أو .drawio أو .svg) وتبديل تلك الصور المدمجة بأخرى جديدة باستخدام GroupDocs.Watermark API. هذا ي automatis updates التي كانت تتطلب تحريرًا يدويًا في محرر المخططات.

## لماذا نستخدم GroupDocs.Watermark لاستبدال صور المخطط؟
GroupDocs.Watermark يدعم **أكثر من 50 تنسيق إدخال وإخراج** – بما في ذلك Visio و Draw.io و SVG – ويمكنه معالجة **ملفات تصل إلى 500 MB** دون تحميل المستند بالكامل في الذاكرة، مما يمنحك **تقليل بنسبة 30 % في استهلاك المعالج** مقارنةً بالنهج البسيط لتدفق الملفات.

## المتطلبات المسبقة
- JDK 8 أو أحدث مثبت.
- بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، أو VS Code) لتطوير Java.
- Maven (أو القدرة على إضافة ملفات JAR يدويًا).
- ترخيص صالح لـ GroupDocs.Watermark (تجريبي أو دائم). يمكنك الحصول على ترخيص من [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### المكتبات المطلوبة والإصدارات والاعتماديات
أضف مستودع GroupDocs.Watermark والاعتماديات إلى ملف `pom.xml` الخاص بك:

```xml
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
```

إذا كنت تفضل إدارة ملفات JAR يدويًا، قم بتنزيل أحدث إصدار من الموقع الرسمي: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## كيفية استبدال صور المخطط في Java خطوة بخطوة

### كيف تقوم بتهيئة Watermarker لملف مخطط؟
Watermarker هو الصف الرئيسي الذي يمثل مستندًا ويوفر طرقًا للتلاعب بالمحتوى. للبدء، أنشئ كائن `Watermarker` يحمل ملف المخطط في الذاكرة. صف `Watermarker` هو نقطة الدخول الأساسية لـ GroupDocs.Watermark، مما يتيح لك قراءة المستندات وتعديلها وحفظها. استخدم `DiagramLoadOptions` لتحديد إعدادات خاصة بالتنسيق مثل DPI أو نطاق الصفحات. `DiagramLoadOptions` يكوّن طريقة تحميل المخطط، على سبيل المثال تحديد DPI أو وضع التحميل.

```java
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
```

### كيف يمكنك الوصول إلى محتوى المخطط لتحديد الأشكال؟
بعد تحميل الملف، استرجع كائن `DiagramContent` من `Watermarker`. `DiagramContent` يمثل الهيكل الداخلي للمخطط من صفحات وأشكال. هذا النموذج يعرّض مجموعات من الصفحات والأشكال التي يمكنك التنقل خلالها، مما يسهل تحديد العناصر المحددة مثل الصور أو النص.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### كيف تستبدل صور الأشكال في المخطط؟
تجول عبر كل `DiagramShape` في الصفحة المطلوبة، تحقق مما إذا كان الشكل يحتوي على صورة، واستبدل بايتات الصورة ببايتات ملف جديد. `DiagramShape` هو النموذج لشكل فردي في المخطط، بينما `DiagramWatermarkableImage` يخزن بيانات الصورة التي يمكن تطبيقها على الشكل.

```java
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
```

### كيف تحفظ التغييرات وتغلق Watermarker؟
عند اكتمال جميع التعديلات، استدعِ `save` على `Watermarker` لكتابة المخطط المحدث إلى ملف، ثم استدعِ `close` لتحرير الموارد الأصلية. هذا يضمن تحرير مقبض الملف ويمنع تسرب الذاكرة، خاصةً عند معالجة عدد كبير من المخططات في مهمة دفعة.

```java
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
```

## إضافة علامة مائية إلى نفس المخطط (اختياري)

إذا كنت تحتاج أيضًا إلى تمييز المخطط، يمكنك إضافة علامة مائية قبل أو بعد استبدال الصورة:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## المشكلات الشائعة واستكشاف الأخطاء

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لم يحدث تغيير في الصورة بعد تشغيل الشيفرة | `DiagramShape.hasImage()` أرجع false | تحقق من نوع الشكل؛ بعض الأشكال المتجهية تخزن الصور بطريقة مختلفة. |
| خطأ OutOfMemoryError في الملفات الكبيرة | تحميل المخطط بالكامل مرة واحدة | استخدم `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` لمعالجة الصفحات بشكل متسلسل. |
| العلامة المائية غير مرئية | العلامة المائية وضعت خلف المحتوى الموجود | استدعِ `watermarker.setWatermarkPosition(Position.Foreground)` قبل الحفظ. |

## الأسئلة المتكررة

**س: هل يمكنني استبدال الصور في المخططات المحمية بكلمة مرور؟**  
ج: نعم. مرّر كلمة المرور إلى `DiagramLoadOptions` عند إنشاء `Watermarker`.

**س: هل تعمل المكتبة مع ملفات .drawio (XML)؟**  
ج: بالتأكيد – GroupDocs.Watermark يدعم تنسيق Draw.io XML ويعامل كل عقدة كشكل.

**س: كم عدد المخططات التي يمكنني معالجتها بالتوازي؟**  
ج: المكتبة آمنة للقراءة المتعددة الخيوط للعمليات القراءة فقط؛ بالنسبة لعمليات الكتابة، حدّ التوازي بعدد نوى المعالج لتجنب التنافس على مقابض الملفات.

**س: هل هناك حد لحجم الصورة؟**  
ج: تدعم الصور حتى 100 MB؛ يجب تصغير الملفات الأكبر مسبقًا لتقليل استهلاك الذاكرة.

**س: ما خيارات الترخيص المتاحة؟**  
ج: يمكنك البدء بتجربة مجانية لمدة 30 يومًا؛ الاستخدام في الإنتاج يتطلب ترخيصًا مدفوعًا يمكن الحصول عليه من متجر GroupDocs.

---

**آخر تحديث:** 2026-08-19  
**تم الاختبار مع:** GroupDocs.Watermark 23.9 for Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [دروس وضع العلامة المائية للمخططات لـ GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [إزالة الروابط التشعبية من أشكال المخطط باستخدام GroupDocs.Watermark Java لتعزيز أمان المستند](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [كيفية إضافة علامة مائية صورة في Java باستخدام GroupDocs.Watermark: دليل خطوة بخطوة](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)