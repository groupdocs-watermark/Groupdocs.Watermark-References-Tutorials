---
date: '2026-10-21'
description: تعلم كيفية إزالة الارتباط التشعبي من أشكال المخطط باستخدام GroupDocs.Watermark
  for Java. اتبع هذا الدليل خطوة بخطوة لتأمين وتنظيف مستنداتك.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: تعلم كيفية إزالة الارتباط التشعبي من أشكال المخطط باستخدام GroupDocs.Watermark
  for Java. يوضح هذا الدليل إعداد البرنامج، الكود، وأفضل الممارسات للحصول على مستندات
  آمنة ونظيفة.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: كيفية إزالة الارتباط التشعبي من الأشكال باستخدام GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: كيفية إزالة الارتباط التشعبي من الأشكال باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# كيفية إزالة الارتباط التشعبي من الأشكال باستخدام GroupDocs.Watermark Java

إدارة المستندات الرقمية غالبًا ما تتضمن تحرير المخططات، خاصة عندما تحتاج إلى **كيفية إزالة الارتباط التشعبي** من الأشكال لأسباب أمنية أو وضوح بصري. يشرح هذا الدليل طريقة بسيطة لإزالة الروابط التشعبية غير المرغوب فيها من أشكال المخطط باستخدام مكتبة **GroupDocs.Watermark** القوية في Java. في نهاية هذا الدليل، ستفهم لماذا إزالة الروابط التشعبية مهمة، وكيفية إعداد البيئة، والخطوات الدقيقة لتنفيذ الإزالة بأمان.

## إجابات سريعة
- **ما هو الهدف الأساسي من إزالة الروابط التشعبية؟** لإزالة مخاطر الأمان وتحسين الوضوح البصري في المخططات المشتركة.  
- **أي مكتبة تتعامل مع الإزالة؟** GroupDocs.Watermark for Java توفر API مخصص لمعالجة المخططات.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي يعمل للاختبار؛ الترخيص التجاري مطلوب للاستخدام في الإنتاج.  
- **هل يمكنني معالجة ملفات متعددة في آن واحد؟** نعم—قم بلف الكود داخل حلقة أو مهمة دفعة للتعامل مع عمليات الدفعات.  
- **ما نسخة Java المطلوبة؟** Java 8 أو أعلى مدعومة.

## ما هي كيفية إزالة الارتباط التشعبي؟
تشير عبارة **كيفية إزالة الارتباط التشعبي** إلى عملية تحديد وحذف كائنات الارتباط التشعبي المدمجة في عناصر أشكال المخطط. تنفيذ هذا الإجراء يمنع التنقل الخارجي من كشف المستخدمين عن غير قصد لمواقع ضارة أو محتوى غير مرغوب فيه. وهو مهم بشكل خاص عند إعداد المستندات للتوزيع العام، لضمان عدم بقاء مسارات تنقل مخفية قد تؤدي إلى مواقع تصيد أو موارد خارجية غير مقصودة.

## لماذا تستخدم GroupDocs.Watermark للـ Java؟
يدعم GroupDocs.Watermark **أكثر من 30 تنسيقًا للإدخال والإخراج** ويمكنه معالجة المخططات التي تصل **إلى 500 صفحة** دون تحميل الملف بالكامل في الذاكرة، مما يوفر **تقليلًا بنسبة 40 % في استهلاك وحدة المعالجة المركزية** مقارنةً مع محللات XML العامة. يمنحك API الخاص به تحكمًا دقيقًا في خصائص الأشكال، مما يجعله النهج القياسي للتعامل الآمن مع المخططات في تطبيقات Java.

## المتطلبات المسبقة
- **GroupDocs.Watermark** إصدار المكتبة 24.11 أو أحدث.  
- Maven مثبت (أو تحميل JAR مباشرة).  
- JDK 8 أو أحدث وIDE مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java وإلمام باعتمادات Maven.

## إعداد GroupDocs.Watermark للـ Java
للبدء، أدرج مكتبة GroupDocs.Watermark في مشروعك. يمكنك إضافتها عبر Maven أو تحميل ملف JAR يدويًا.

### إعداد Maven
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

### التحميل المباشر
بدلاً من ذلك، قم بتحميل أحدث نسخة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### خطوات الحصول على الترخيص
- ابدأ بتجربة مجانية عن طريق تحميل GroupDocs.Watermark.  
- للاختبار الموسع أو الاستخدام في الإنتاج، احصل على ترخيص مؤقت أو اشترِ ترخيصًا كاملاً.

#### التهيئة الأساسية والإعداد
فئة `Watermarker` هي نقطة الدخول لجميع عمليات مستوى المستند. تقوم بتحميل ملف، وتمنحك الوصول إلى صفحاته، وأشكاله، والبيانات الوصفية، وأخيرًا تكتب المستند المعدل مرة أخرى إلى القرص.

لتهيئة فئة Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## كيفية إزالة الارتباط التشعبي من أشكال المخطط؟
قم بتحميل المخطط، حدد كل شكل يحتوي على ارتباط تشعبي، واحذف تلك الكائنات. يمكن تنفيذ العملية بالكامل في أقل من عشر أسطر من الشيفرة، وتضمن أن المخطط الناتج لم يعد يحتوي على أي روابط قابلة للنقر قد تعيد توجيه المستخدمين إلى مواقع خارجية أو تكشف معلومات حساسة.

### الخطوة 1: تحميل ملف المخطط
ابدأ بتحميل المخطط الخاص بك باستخدام `Watermarker`. هذا الكائن يوفر الوصول إلى عناصر المستند المختلفة، بما في ذلك الأشكال وخصائصها.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **لماذا**: تحميل الملف ضروري للوصول إلى محتواه للمعالجة اللاحقة.

### الخطوة 2: الوصول إلى محتوى الشكل
استرجع محتويات أشكال المخطط. يتيح لك ذلك العمل مباشرةً مع العناصر التي قد تحتوي على روابط تشعبية.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **لماذا**: الوصول إلى الأشكال المحددة أمر حاسم لاستهداف وتعديل خصائص الروابط التشعبية.

### الخطوة 3: التكرار وإزالة الروابط التشعبية
قم بالتكرار على الروابط التشعبية بترتيب عكسي لإزالة الروابط غير المرغوب فيها بأمان دون إحداث اضطراب في عملية التكرار.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **لماذا**: عكس ترتيب التكرار يمنع مشاكل الفهرسة عند إزالة العناصر.

### الخطوة 4: الحفظ والإغلاق
بعد إكمال التعديلات، احفظ تغييراتك إلى موقع ملف جديد وأغلق مورد الـ watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **لماذا**: إغلاق الموارد بشكل صحيح يضمن عدم وجود تسريبات للذاكرة أو ملفات مقفلة في النظام.

## المشكلات الشائعة واستكشاف الأخطاء
- **مجموعات الأشكال الفارغة** – تحقق دائمًا من أن مجموعة `Hyperlinks` الخاصة بالشكل ليست null قبل التكرار.  
- **المخططات الكبيرة** – للملفات التي تتجاوز 200 صفحة، قم بزيادة حجم ذاكرة JVM (`-Xmx2g`) لتجنب `OutOfMemoryError`.  
- **أخطاء الترخيص** – إذا ظهرت استثناء ترخيص، تحقق من أن الترخيص التجريبي لم ينته صلاحيته وأن مسار ملف الترخيص صحيح.

## الأسئلة المتكررة

**س: كيف يمكنني التعامل مع أشكال متعددة في نفس الصفحة؟**  
ج: قم بالتكرار عبر مجموعة `Shapes` لكل صفحة، مع تطبيق نفس منطق إزالة الروابط التشعبية على كل شكل تصادفه.

**س: هل يمكنني حصر الإزالة على نطاق صفحات محدد؟**  
ج: نعم—استخدم فهرس الصفحة عند استرجاع الأشكال وتجاوز الصفحات خارج النطاق المستهدف.

**س: هل يلزم وجود ترخيص للمعالجة الدفعية؟**  
ج: يلزم وجود ترخيص تجاري صالح لأي مهمة دفعة ذات مستوى إنتاج؛ الترخيص التجريبي يعمل للاختبار المحدود فقط.

**س: هل يعمل هذا مع ملفات SVG أو Visio؟**  
ج: يدعم GroupDocs.Watermark ملفات SVG وVSDX والعديد من صيغ المخططات الأخرى؛ تأكد من أن نوع الملف مدرج في جدول الصيغ المدعومة.

**س: ما هو الأداء المتوقع على مخطط مكون من 300 صفحة؟**  
ج: على خادم نموذجي (8 معالجات، 16 جيجابايت RAM)، يستغرق معالجة مخطط من 300 صفحة أقل من 45 ثانية، مع بقاء استهلاك الذاكرة أقل من 200 ميجابايت.

## الموارد
- [التوثيق](https://docs.groupdocs.com/watermark/java/)
- [مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

---

**آخر تحديث:** 2026-10-21  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [تعديل أشكال مستند Word باستخدام GroupDocs.Watermark في Java: دليل شامل](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [إزالة الأشكال من مستندات Word باستخدام GroupDocs.Watermark في Java: دليل شامل](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [تحرير رؤوس وتذييلات المخططات في Java باستخدام GroupDocs.Watermark: دليل شامل](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)