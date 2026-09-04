---
date: '2025-12-19'
description: تعلم كيفية إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark
  للغة Java. يغطي هذا الدليل خطوة بخطوة الإعداد، إعدادات خط العلامة المائية، وحالات
  الاستخدام العملية.
keywords:
- text watermarks in Java
- add text watermark to diagram
- GroupDocs Watermark for Java setup
title: كيفية إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark للـ
  Java
type: docs
url: /ar/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# كيفية إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark للغة Java

حماية مخططاتك من إعادة الاستخدام غير المصرح بها هي أولوية قصوى للعديد من المطورين والمصممين. في هذا الدليل ستتعلم **كيفية إضافة علامة مائية نصية** إلى ملفات المخططات باستخدام مكتبة **GroupDocs.Watermark للغة Java** القوية. سنستعرض كل خطوة — من إعداد Maven إلى تطبيق إعدادات خط العلامة المائية المخصصة — حتى تتمكن من تأمين أصولك البصرية بسرعة وموثوقية.

## إجابات سريعة
- **ماذا تفعل المكتبة؟** تقوم بإدراج علامات مائية نصية (أو صورة) في أكثر من 100 تنسيق من المستندات والمخططات.  
- **ما هي الكلمة المفتاحية الأساسية التي يجب استهدافها؟** *add text watermark* – تُستخدم طوال هذا الدليل.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي مؤقت يكفي للتطوير؛ يتطلب الترخيص الكامل للإنتاج.  
- **هل يمكنني تخصيص الخط؟** نعم، يمكنك التحكم في عائلة الخط، الحجم، اللون، والدوران عبر إعدادات خط العلامة المائية.  
- **هل هو متوافق مع Java‑8؟** بالتأكيد – المكتبة تدعم JDK 8 والإصدارات الأحدث.  

## ما هو “add text watermark”؟
إضافة علامة مائية نصية تعني وضع نص شبه شفاف فوق كل صفحة أو شكل من المستند بحيث يظل المحتوى قابلًا للتحديد. تُستخدم هذه التقنية على نطاق واسع للعلامة التجارية، حماية حقوق النشر، والتحرير التعاوني.

## لماذا نستخدم GroupDocs.Watermark للغة Java؟
- **دعم واسع للتنسيقات** – يعمل مع Visio، SVG، PDF، Word، والعديد غيرها.  
- **تحكم دقيق** – يمكنك ضبط الخط، اللون، الدوران، الشفافية، والموضع.  
- **واجهة برمجة تطبيقات بسيطة** – بضع أسطر من الشيفرة تكفي لإنجاز المهمة، مما يوفر وقت التطوير.  
- **محسّن للأداء** – يتعامل مع الملفات الكبيرة بكفاءة عندما تقوم بإغلاق الموارد بسرعة.  

## المتطلبات المسبقة
- JDK 8 أو أعلى مثبت على جهازك.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java (الفئات، الكائنات، وMaven).  

### المكتبات والاعتمادات المطلوبة
سنستخدم Maven لجلب مكتبة GroupDocs.Watermark. أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك تمامًا كما هو موضح:

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

إذا كنت تفضّل التحميل اليدوي، قم بزيارة الصفحة الرسمية: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) واتبع التعليمات.

### الحصول على الترخيص
ابدأ بتجربة مجانية عن طريق الحصول على ترخيص مؤقت من بوابة التجربة: [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). حمّل ملف الترخيص قبل أي عملية علامة مائية:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## دليل التنفيذ

### الخطوة 1: تحميل المخطط الخاص بك
أولاً، وجه الـ `Watermarker` إلى ملف المخطط المصدر. كائن `DiagramLoadOptions` يخبر المكتبة بمعاملة الملف كتنسيق مخطط.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### الخطوة 2: تهيئة العلامة المائية النصية (مع **إعدادات خط العلامة المائية** المخصصة)
أنشئ مثالًا من `TextWatermark`، محددًا النص، عائلة الخط، الحجم، وأي تنسيق إضافي تحتاجه.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

> **نصيحة احترافية:** عدّل `setColor` و `setRotationAngle` لتتناسب مع إرشادات العلامة التجارية الخاصة بك. استدعاء `setBackground(false)` يضمن أن العلامة المائية توضع فوق أشكال المخطط بدلاً من خلفها.

### الخطوة 3: اختيار الموضع – الخلفية أم المقدمة
تتيح لك GroupDocs اختيار ما إذا كانت العلامة المائية تظهر خلف أشكال المخطط (الخلفية) أو فوقها (المقدمة). في معظم سيناريوهات العلامة التجارية، يكون وضع الخلفية هو الأنسب.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### الخطوة 4: حفظ المخطط المائي
أخيرًا، احفظ الملف المعدل إلى القرص وأطلق الموارد.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| **خطأ: الملف غير موجود** | مسار `inputFilePath` غير صحيح أو عدم وجود أذونات قراءة | تحقق من المسار وتأكد من أن عملية Java يمكنها قراءة الملف. |
| **العلامة المائية غير مرئية** | تم تعيين الموضع إلى `Foreground` مع لون شفاف | استخدم وضع `Background` أو اختر لونًا متباينًا. |
| **استثناء نفاد الذاكرة** على المخططات الكبيرة | عدم إغلاق الـ `Watermarker` أو معالجة العديد من الملفات في حلقة | استدعِ `watermarker.close()` بعد كل ملف وفكّر في المعالجة على دفعات. |
| **الترخيص غير معترف به** | مسار ملف الترخيص غير صحيح أو انتهاء صلاحية التجربة | تحقق مرة أخرى من المسار واستخدم ملف ترخيص ساري. |

## تطبيقات عملية
1. **أمان المستندات** – منع المنافسين من سرقة المخططات الخاصة.  
2. **العلامة التجارية** – دمج اسم الشركة أو الشعار عبر جميع صفحات المخطط.  
3. **تتبع التعاون** – إضافة الأحرف الأولى للمستخدم كعلامة مائية لتحديد من قام بتحرير المخطط.  

## اعتبارات الأداء
- أغلق الـ `Watermarker` فورًا بعد الحفظ لتحرير الموارد الأصلية.  
- اجعل نص العلامة المائية مختصرًا؛ الخطوط الكبيرة جدًا تزيد من وقت المعالجة.  
- اختبر على عينة تمثيلية قبل معالجة آلاف الملفات على دفعات.  

## الخلاصة
أنت الآن تمتلك طريقة كاملة وجاهزة للإنتاج **لإضافة علامة مائية نصية** إلى ملفات المخططات باستخدام **GroupDocs.Watermark للغة Java**. هذه الطريقة تحمي ملكيتك الفكرية وتمنحك التحكم الكامل في إعدادات خط العلامة المائية وموضعها.

### الخطوات التالية
- استكشف العلامات المائية الصورية لإضفاء لمسة بصرية للعلامة التجارية.  
- دمج علامات مائية متعددة (نص + صورة) للحصول على حماية متعددة الطبقات.  
- أتمتة المعالجة على دفعات باستخدام حلقة `for` بسيطة ونفس استدعاءات الـ API.  

## أسئلة شائعة
**س: هل يعمل GroupDocs.Watermark مع أحدث إصدارات Java؟**  
ج: نعم، هو متوافق بالكامل مع Java 8 حتى Java 21.  

**س: هل يمكنني تخصيص شفافية العلامة المائية النصية؟**  
ج: بالتأكيد. استخدم `textWatermark.setOpacity(0.5)` لتعيين شفافية بنسبة 50 ٪.  

**س: هل هناك طريقة لإضافة علامات مائية فقط إلى أشكال مخطط مختارة؟**  
ج: يمكنك تصفية الأشكال عبر `DiagramShapeWatermarkOptions` بتوفير معرفات الأشكال أو أسمائها.  

**س: كيف أتعامل مع ملفات المخططات المحمية بكلمة مرور؟**  
ج: حمّل الملف باستخدام `DiagramLoadOptions` التي تتضمن كلمة المرور، ثم طبّق العلامة المائية كالمعتاد.  

**س: هل هناك أي قيود ترخيص للاستخدام التجاري؟**  
ج: يتطلب الترخيص التجاري للنشر في بيئات الإنتاج؛ الترخيص التجريبي مخصص للتقييم فقط.  

## الموارد
- [الوثائق](https://docs.groupdocs.com/watermark/java/)
- [مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل أحدث نسخة](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)

**آخر تحديث:** 2025-12-19  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs