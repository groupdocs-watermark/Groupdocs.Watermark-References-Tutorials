---
date: '2026-10-27'
description: تعلم كيفية حذف نص watermark من ملفات المخططات باستخدام GroupDocs.Watermark
  for Java واكتشاف image watermark بكفاءة. دليل خطوة بخطوة للمطورين.
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: حذف نص watermark من ملفات المخططات باستخدام GroupDocs.Watermark for
  Java. تعلم اكتشاف image watermark، search، وإزالة watermarks باستخدام code snippets.
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: حذف نص watermark من ملفات المخططات باستخدام Java بسرعة
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: كيفية حذف نص watermark في المخططات باستخدام Java
type: docs
url: /ar/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# كيفية حذف العلامة المائية النصية في المخططات باستخدام Java

إدارة العلامات المائية في المستندات أمر أساسي لحماية الملكية الفكرية والحفاظ على سلامة المستند. في هذا الدرس ستتعلم كيفية **حذف العلامة المائية النصية** من ملفات المخططات مثل `.vsdx` باستخدام GroupDocs.Watermark للـ Java، وكذلك كيفية **اكتشاف العلامة المائية الصورية** عند الحاجة. سواءً كنت تبني خط أنابيب مستندات على مستوى المؤسسة أو تقوم بأتمتة مهمة دفعة بسيطة، فإن هذه التقنيات تمنحك تحكمًا دقيقًا في علامات المائية للمخططات.

**ما ستتعلمه**
- إعداد مكتبة GroupDocs.Watermark
- تحميل مستند مخطط بخيارات محددة
- البحث عن العلامات المائية النصية وحذفها
- اكتشاف العلامات المائية الصورية وإزالتها
- نصائح أفضل الممارسات للمعالجة على نطاق واسع

هل أنت مستعد للبدء؟ لنجهز بيئتك أولًا.

## إجابات سريعة
- **هل يمكنني حذف كل من العلامات المائية النصية والصورية مرة واحدة؟** نعم – اجمع بين `TextSearchCriteria` و `ImageDctHashSearchCriteria` باستخدام شرط `or()`.  
- **هل تقوم المكتبة بتحميل المخطط بالكامل في الذاكرة؟** لا – تقوم ببث الصفحات، مما يسمح بملفات تصل إلى 500 ميغابايت دون استهلاك كامل للذاكرة.  
- **ما هي صيغ المخططات المدعومة؟** أكثر من 20 صيغة، بما في ذلك `.vsdx` و `.vdx` و `.drawio`.  
- **هل يلزم وجود ترخيص للإنتاج؟** يلزم وجود ترخيص صالح لـ GroupDocs.Watermark للاستخدام غير التجريبي.  
- **هل يمكن تشغيله في خط أنابيب CI/CD؟** بالتأكيد – الـ API بدون واجهة رسومية ويعمل على Windows و Linux و macOS.

## ما هو حذف العلامة المائية النصية؟
حذف العلامة المائية النصية يعني إزالة كائنات التراكب النصية التي أضيفت إلى المستند للدلالة على الملكية أو السرية أو حالة المسودة. في GroupDocs.Watermark يتم تنفيذ هذه العملية عبر تحديد كائنات العلامة المائية باستخدام معايير البحث ثم استدعاء `clear()` على المجموعة الناتجة.

## لماذا نكتشف العلامة المائية الصورية؟
اكتشاف العلامة المائية الصورية يتيح لك التعرف على الشعارات أو الأختام الرسومية المدمجة في المخطط. هذا أمر حاسم لفحوصات الامتثال، وحماية العلامة التجارية، وإدارة المحتوى الآلية. يستخدم GroupDocs.Watermark التجزئة الإدراكية (DCT) لمقارنة الصور بسرعة وكفاءة.

## المتطلبات المسبقة
قبل أن نبدأ، تأكد من وجود ما يلي:
1. **مجموعة تطوير جافا (JDK)** 8 أو أعلى.  
2. **بيئة تطوير متكاملة (IDE)** – IntelliJ IDEA أو Eclipse أو أي محرر تفضله.  
3. **GroupDocs.Watermark للـ Java** – يجب أن تكون ملفات JAR الخاصة بالمكتبة موجودة في مسار الفئة (classpath).  

### المكتبات والاعتمادات المطلوبة
يمكنك إضافة المكتبة عبر Maven أو تنزيل ملفات JAR يدويًا.

#### إعداد Maven
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

#### التحميل المباشر
بدلاً من ذلك، قم بتنزيل أحدث نسخة من [إصدارات GroupDocs.Watermark لـ Java](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **تجربة مجانية** – اختبر جميع الميزات دون مفتاح ترخيص.  
- **ترخيص مؤقت** – اطلب مفتاحًا محدودًا زمنيًا للتقييم.  
- **شراء** – احصل على ترخيص دائم أو اشتراك للاستخدام الإنتاجي.

## إعداد GroupDocs.Watermark للـ Java
1. **تثبيت المكتبة** – تأكد من وجود مستودع Maven وإدخالات الاعتماد، أو ضع ملفات JAR في `libs/` وأضفها إلى مسار بناء المشروع.  
2. **تهيئة الـ API** – أنشئ كائن `Watermarker`؛ هذا الكائن هو نقطة الدخول لتحميل المخططات وتنفيذ عمليات العلامات المائية.

## كيفية حذف العلامة المائية النصية في المخططات باستخدام Java
لحذف علامة مائية نصية، قم بتحميل المخطط باستخدام `Watermarker`، أنشئ `TextSearchCriteria` يتطابق مع نص العلامة المائية، استرجع `PossibleWatermarkCollection` المتطابقة، ثم استدعِ `clear()` عليها. سيؤدي ذلك إلى إزالة النصوص المحددة فقط مع إبقاء باقي المخطط سليمًا.

فئة `Watermarker` تمثل مستندًا واحدًا في الذاكرة وتوفر طرقًا للتحميل والبحث وتعديل العلامات المائية.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```
- **المعلمات:**  
  - `inputFilePath`: مسار ملف `.vsdx` الخاص بك.  
  - `loadOptions`: يحدد كيفية تحميل المستند (مثل نطاق الصفحات، كلمة المرور).

## كيفية اكتشاف العلامة المائية الصورية في ملف مخطط؟
يتضمن اكتشاف العلامة المائية الصورية إنشاء `ImageDctHashSearchCriteria` بصورة مرجعية، ثم استخدام `Watermarker` للبحث في المخطط. يولد الـ API تجزئة إدراكية لكل صورة مدمجة ويقارنها بالمرجعية، مع إرجاع التطابقات مع درجات التشابه لتتمكن من تحديد وإزالة الشعارات أو الأختام غير المرغوب فيها.

`ImageDctHashSearchCriteria` ينشئ تجزئة للصورة المرجعية ويقارنها بالصور المدمجة في المخطط، مع إرجاع التطابقات مع درجة التشابه.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```
- **الطرق الأساسية:**  
  - `TextSearchCriteria` – ينشئ معايير للعلامات المائية النصية.  
  - `PossibleWatermarkCollection` – يحمل نتائج أي عملية بحث.

## كيفية إزالة العلامات المائية بمجرد العثور عليها؟
بعد تحديد العلامات المائية، يمكنك إزالتها باستدعاء طريقة `clear()` على `PossibleWatermarkCollection` التي تم إرجاعها من البحث. هذه العملية تحذف كائنات العلامة المائية مع الحفاظ على جميع عناصر المخطط الأخرى، مما يضمن بقاء المحتوى الأصلي غير متغير تمامًا.

`clear()` يزيل كل علامة مائية في المجموعة مع الحفاظ على باقي محتوى المخطط.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```
- **الطريقة الأساسية:** `clear()` – تحذف جميع العلامات المائية في المجموعة المقدمة دون تعديل عناصر المخطط الأخرى.

## التطبيقات العملية
1. **تكامل برمجيات المؤسسة** – دمج إدارة العلامات المائية في تطبيقات الأعمال التي تركز على المستندات لحماية المخططات المملوكة.  
2. **أنظمة إدارة المحتوى (CMS)** – أتمتة اكتشاف الشعارات غير المصرح بها قبل نشر المخططات التي يولدها المستخدمون.  
3. **معالجة المستندات القانونية** – إضافة أو حذف العلامات المائية في مراحل مختلفة من سير عمل ملف القضية، لضمان الامتثال لسياسات السرية.

## الأخطاء الشائعة واستكشاف الأخطاء وإصلاحها
- **الملفات الكبيرة** – زد إعداد `maxMemory` في `LoadOptions` إذا واجهت `OutOfMemoryError`.  
- **المخططات المحمية بكلمة مرور** – قدم كلمة المرور في `LoadOptions` لفتح الملف.  
- **عدم وجود تطابقات تجزئة الصورة** – تأكد من أن الصورة المرجعية ذات دقة كافية؛ قد تنتج الصور منخفضة الدقة تجزئات ضعيفة.

## الأسئلة المتكررة

**س: هل يمكنني البحث عن النصوص والصور في آنٍ واحد؟**  
ج: نعم – اجمع بين `TextSearchCriteria` و `ImageDctHashSearchCriteria` باستخدام عامل `or()` لتحديد كلا النوعين في خطوة واحدة.

**س: هل يمكن حذف العلامات المائية دون الإضرار بالمخطط؟**  
ج: بالتأكيد. يقوم الـ API بعزل كائنات العلامة المائية وإزالتها، مع ترك بنية المخطط الأصلية دون تغيير.

**س: هل يدعم GroupDocs.Watermark صيغ مخططات متعددة؟**  
ج: نعم – يدعم أكثر من 20 صيغة، بما في ذلك `.vsdx` و `.vdx` و `.drawio` و `.svg`، مما يتيح إدارة واسعة النطاق للمخططات.

**س: كيف يمكنني معالجة حجم كبير من المستندات بكفاءة؟**  
ج: استخدم حلقات المعالجة الدفعية، وأعد استخدام كائن `Watermarker` واحد حيثما أمكن، واضبط `LoadOptions` لبث الصفحات بدلاً من تحميل الملفات بالكامل.

**س: هل يمكن دمج اكتشاف العلامات المائية في خط أنابيب CI/CD؟**  
ج: نعم – المكتبة بدون واجهة رسومية ويمكن استدعاؤها من Maven أو Gradle أو أي سكريبت بناء للتحقق الآلي من أصول المخططات.

---

**آخر تحديث:** 2026-10-27  
**تم الاختبار مع:** GroupDocs.Watermark 23.6 للـ Java  
**المؤلف:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## دروس ذات صلة

- [كيفية إضافة علامات مائية نصية إلى المخططات باستخدام GroupDocs.Watermark في Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [دليل إضافة علامات مائية إلى المخططات باستخدام GroupDocs.Watermark للـ Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [كيفية استرجاع معلومات المستند باستخدام GroupDocs.Watermark للـ Java: دليل خطوة بخطوة](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)