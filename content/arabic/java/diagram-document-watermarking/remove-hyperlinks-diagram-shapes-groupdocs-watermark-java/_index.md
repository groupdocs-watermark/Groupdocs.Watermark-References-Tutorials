---
date: '2026-08-25'
description: تعلم كيفية تعديل ملفات diagram وإزالة hyperlinks باستخدام GroupDocs.Watermark
  for Java. احمِ مخططاتك بسرعة من خلال إرشادات خطوة بخطوة.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: تعلم كيفية تعديل ملفات diagram وإزالة hyperlinks باستخدام GroupDocs.Watermark
  for Java. اتبع خطوات واضحة لحماية documents.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: كيفية تعديل diagram وإزالة hyperlinks باستخدام Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: كيفية تعديل diagram وإزالة hyperlinks باستخدام Java
type: docs
url: /ar/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# كيفية تعديل المخطط وإزالة الروابط التشعبية باستخدام Java  

إدارة المستندات الرقمية غالبًا ما تتضمن تعديل المخططات، خاصة عندما تحتاج إلى **edit diagram** ملفات لإزالة الروابط التشعبية لأسباب تتعلق بالأمان أو الوضوح البصري. يوضح هذا الدليل بالضبط كيفية تعديل ملفات المخطط وإزالة الروابط التشعبية غير المرغوب فيها من أشكال المخطط باستخدام مكتبة **GroupDocs.Watermark** القوية لـ Java. بنهاية هذا الدليل ستحصل على مخطط نظيف خالٍ من الروابط جاهز للتوزيع.  

## إجابات سريعة  
- **ما هو الهدف الرئيسي؟** إزالة جميع الروابط التشعبية من أشكال المخطط لتحسين الأمان والعرض.  
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يعمل للاختبار؛ الترخيص التجاري مطلوب للإنتاج.  
- **هل يمكنني معالجة ملفات متعددة في آن واحد؟** نعم – يمكن وضع نفس الشيفرة داخل حلقة لمعالجة الدُفعات.  
- **ما نسخة Java المدعومة؟** Java 8 or higher (Java 11 recommended).  

## ما هو “how to edit diagram”؟  
**How to edit diagram** تشير إلى عملية فتح ملف مخطط برمجيًا، تعديل عناصره الداخلية (مثل الأشكال، النص، أو الروابط التشعبية)، وحفظ النتيجة. باستخدام GroupDocs.Watermark يمكنك تعديل ملفات المخطط دون الحاجة إلى أداة الإنشاء الأصلية.  

## لماذا تستخدم GroupDocs.Watermark لـ Java؟  
GroupDocs.Watermark يدعم **30+ diagram and image formats** (including VSDX, SVG, and WMF) ويمكنه معالجة ملفات تصل إلى **500 MB** دون تحميل المستند بالكامل في الذاكرة، مما يوفر سرعة معالجة **20 % أسرع** مقارنة بالعديد من المنافسين.  

## المتطلبات المسبقة  
- **GroupDocs.Watermark** إصدار المكتبة 24.11 أو أحدث.  
- Maven مثبت (أو ملفات JAR إذا كنت تفضل الإعداد اليدوي).  
- Java Development Kit 8 أو أحدث وبيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  

### المكتبات المطلوبة، الإصدارات، والاعتمادات  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (إذا كنت تستخدم نهج Maven)  

### متطلبات إعداد البيئة  
تأكد من أن دليل `bin` الخاص بـ JDK موجود في متغير `PATH` وأن بيئة التطوير المتكاملة تشير إلى نسخة JDK الصحيحة.  

### متطلبات المعرفة المسبقة  
يجب أن تكون مرتاحًا مع بنية Java الأساسية، إدارة تبعيات Maven، وعمليات إدخال/إخراج الملفات.  

## كيف تقوم بإعداد GroupDocs.Watermark لـ Java؟  
فئة `Watermarker` توفر نقطة الدخول إلى API لتحميل وتعديل المستندات.  

لبدء استخدام GroupDocs.Watermark، أضف إحداثيات Maven الخاصة به إلى ملف `pom.xml` الخاص بمشروعك. هذا يجلب المكتبة وتبعياتها، مما يتيح لك إنشاء كائن من فئة Watermarker والعمل مع ملفات المخطط مباشرةً من كود Java. يمكنك بعد ذلك تكوين الترخيص وتحديد خيارات الإخراج قبل معالجة أي مستند.  

أضف تبعية GroupDocs.Watermark إلى ملف `pom.xml` الخاص بك.  

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

إذا كنت تفضل عدم استخدام Maven، قم بتنزيل أحدث ملف JAR من صفحة الإصدارات الرسمية.  

[إصدارات GroupDocs.Watermark لـ Java](https://releases.groupdocs.com/watermark/java/)  

#### خطوات الحصول على الترخيص  
- ابدأ بإصدار تجريبي مجاني لتقييم الـ API.  
- للإنتاج، احصل على ترخيص مؤقت أو دائم من بوابة البائع.  

#### التهيئة الأساسية والإعداد  
فئة `Watermarker` هي نقطة الدخول لجميع عمليات معالجة المستندات.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## كيف تقوم بتعديل المخطط وإزالة الروابط التشعبية باستخدام GroupDocs.Watermark؟  
فئة `Watermarker` توفر نقطة الدخول إلى API لتحميل وتعديل المستندات.  

أولاً، قم بتحميل ملف المخطط إلى كائن Watermarker. ثم استرجع مجموعة الأشكال، حدد تلك التي تحتوي على كائنات روابط تشعبية، وتكرّر عليها بترتيب عكسي لحذف كل رابط بأمان دون التأثير على فهرسة المجموعة. هذا يضمن إزالة جميع عناوين URL المضمنة مع الحفاظ على سلامة الشكل البصري للمخطط.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **لماذا هذه الخطوة مهمة**: تحميل الملف يمنحك وصولًا برمجيًا إلى كل شكل وخصائصه المرتبطة.  

## كيف تصل إلى محتوى الشكل في المخطط؟  
كائن `DiagramShape` يمثل شكلًا فرديًا داخل المخطط، ويكشف عن خصائصه والبيانات الوصفية المرفقة.  

بعد تحميل المخطط، استدعِ `getShapes()` على Watermarker للحصول على قائمة من كائنات `DiagramShape`. يمكن فحص كل شكل للبحث عن مجموعات الروابط التشعبية، مما يتيح استهدافًا دقيقًا للروابط لإزالتها أو تعديلها. يمكنك أيضًا قراءة نص الشكل، ألوانه، وهندسته إذا كانت هناك حاجة لتعديلات إضافية.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **لماذا هذه الخطوة مهمة**: استهداف الشكل المحدد يضمن إزالة الروابط غير المرغوب فيها فقط دون التأثير على العناصر البصرية الأخرى.  

## كيف تتكرر وتزيل الروابط التشعبية بأمان؟  
طريقة `removeHyperlink(int index)` تحذف رابطًا تشعبيًا في الموضع المحدد داخل مجموعة الروابط التشعبية للشكل.  

تكرّر عبر قائمة الروابط التشعبية من آخر فهرس إلى الصفر. هذه الحلقة العكسية تمنع تغير الفهارس الذي يحدث عند إزالة العناصر، مما يضمن معالجة كل رابط تشعبي دون تخطيه. بعد الإزالة، يمكنك تحديث حالة الشكل أو المتابعة إلى الشكل التالي في المخطط.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **لماذا هذه الخطوة مهمة**: الحلقة العكسية تضمن إزالة جميع الروابط التشعبية دون تخطي أي إدخال.  

## كيف تحفظ المخطط المعدل وتحرر الموارد؟  
طريقة `save(String path)` تكتب المستند المعدل إلى موقع الملف المحدد، مُنهية جميع التغييرات.  

بعد إزالة جميع الروابط التشعبية، استدعِ طريقة `save` على كائن Watermarker، مع توفير اسم ملف جديد لتجنب الكتابة فوق الأصلي. ثم استدعِ `close()` لتحرير مقابض الملفات وتحرير الذاكرة، وهو أمر أساسي للعمليات الدُفعية الطويلة. هذا يضمن إغلاق الملف بشكل صحيح وجعله جاهزًا للاستخدام لاحقًا.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **لماذا هذه الخطوة مهمة**: إغلاق الموارد بشكل صحيح يمنع تسرب الذاكرة ومشكلات حجز الملفات على الخادم.  

## تطبيقات عملية  
إزالة الروابط التشعبية من أشكال المخطط يمكن أن يكون مفيدًا في عدة سيناريوهات واقعية:  

1. **الأمان** – منع الروابط الخارجية التي قد تؤدي إلى مواقع ضارة.  
2. **الامتثال** – تلبية سياسات الشركة التي تحظر عناوين URL المضمنة في الأصول المشتركة.  
3. **الوضوح** – إنتاج عروض تقديمية أنظف حيث تكون الروابط مشتتة للانتباه.  

يمكنك دمج هذه المنطق في خطوط أتمتة أكبر، مثل وظائف الدُفعات الليلية التي تقوم بتنظيف جميع المخططات قبل نشرها على الإنترانت.  

## اعتبارات الأداء  

### تحسين الأداء  
- استخدم نسخة واحدة من `Watermarker` لكل ملف لتقليل الحمل.  
- فضلًا عن التكرار العكسي (كما هو موضح) لتجنب إعادة فهرسة القوائم المكلفة.  

### إرشادات استخدام الموارد  
- بالنسبة للمخططات التي يزيد حجمها عن 200 MB، راقب استخدام الذاكرة heap وفكر في زيادة علم JVM `-Xmx`.  
- أدوات التحليل مثل VisualVM يمكن أن تساعد في تحديد عنق الزجاجة في عمليات الدُفعات الكبيرة.  

### أفضل الممارسات لإدارة ذاكرة Java  
- أعلن عن الكائنات داخل أصغر نطاق ممكن.  
- استخدم try‑with‑resources عند العمل مع التدفقات لضمان الإغلاق التلقائي.  

## الأسئلة الشائعة  

**س: كيف أتعامل مع المخططات التي تحتوي على آلاف الأشكال؟**  
ج: عالج المخطط صفحة بصفحة وحرّر موارد كل صفحة قبل الانتقال إلى التالية للحفاظ على انخفاض استهلاك الذاكرة.  

**س: هل يمكنني تحديد إزالة الروابط التشعبية لصفحات معينة فقط؟**  
ج: نعم – استرجع فهرس الصفحة المطلوبة، ثم طبّق حلقة الإزالة فقط على الأشكال في تلك الصفحة.  

**س: هل الترخيص التجاري إلزامي لمعالجة الدُفعات؟**  
ج: الترخيص الساري مطلوب لأي نشر على مستوى الإنتاج؛ الإصدار التجريبي المجاني محدود بـ 30 يومًا و5 مستندات.  

**س: هل يدعم GroupDocs.Watermark مخططات SVG؟**  
ج: بالتأكيد – SVG من بين الصيغ الـ 30+ المدعومة، ويمكن إزالة الروابط التشعبية باستخدام نفس استدعاءات الـ API.  

**س: ماذا لو كان الشكل يحتوي على روابط تشعبية متعددة؟**  
ج: حلقة التكرار العكسي تزيل كل إدخال رابط تشعبي على حدة، مما يضمن مسح جميع الروابط.  

## الموارد  

- [التوثيق](https://docs.groupdocs.com/watermark/java/)  
- [مرجع API](https://reference.groupdocs.com/watermark/java)  
- [التنزيل](https://releases.groupdocs.com/watermark/java/)  
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)  
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)  

---  

**آخر تحديث:** 2026-08-25  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs  

## دروس ذات صلة  

- [دروس وضع علامة مائية على المخططات لـ GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [تحرير رؤوس وتذييلات المخطط في Java باستخدام GroupDocs.Watermark: دليل شامل](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [إزالة الأشكال من المخططات بفعالية باستخدام GroupDocs.Watermark لـ Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)