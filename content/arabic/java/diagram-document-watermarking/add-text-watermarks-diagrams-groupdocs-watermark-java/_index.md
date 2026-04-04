---
date: '2026-04-04'
description: تعلم كيفية إنشاء علامة مائية نصية على مخططات Visio باستخدام GroupDocs.Watermark
  للغة Java. يتضمن الإعداد، الكود، وحالات الاستخدام الواقعية.
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: إنشاء علامة مائية نصية على المخططات باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# إنشاء علامة مائية نصية على المخططات باستخدام GroupDocs.Watermark Java

حماية مخططاتك من إعادة الاستخدام غير المصرح بها أمر ضروري في بيئات التعاون الحالية. في هذا الدليل ستقوم **بإنشاء علامة مائية نصية** على المخططات بنمط Visio باستخدام **GroupDocs.Watermark for Java**. سنستعرض كل شيء من إعداد Maven إلى حفظ الملف المائي، حتى تتمكن من إضافة العلامة التجارية أو العلامات الأمنية بثقة إلى كل صفحة من المخطط.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** GroupDocs.Watermark for Java (Maven artifact `groupdocs-watermark`).
- **ما أنواع الملفات المدعومة؟** Visio (`.vsdx`, `.vsd`)، بالإضافة إلى العديد من صيغ المخططات الأخرى.
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي مؤقت يعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج.
- **هل يمكنني تخصيص الخط واللون والدوران؟** نعم – تسمح لك فئة `TextWatermark` بتعيين جميع هذه الخصائص.
- **كم يستغرق العملية من وقت؟** إضافة علامة مائية نصية إلى مخطط نموذجي تستغرق أقل من ثانية على الأجهزة الحديثة.

## ما هي عملية “إنشاء علامة مائية نصية”؟
إنشاء علامة مائية نصية يعني وضع نص شبه شفاف فوق صفحة المستند برمجيًا. يمكن وضع العلامة المائية في المقدمة أو الخلفية، وتدويرها، وتلوينها، وتنسيقها لتتناسب مع متطلبات العلامة التجارية أو الأمان.

## لماذا تستخدم GroupDocs.Watermark for Java؟
- **دعم صيغ واسع** – يعمل مع Visio وPDF وWord وExcel وغيرها.
- **تحكم دقيق** – اختر الموضع، والشفافية، والدوران، وعرض الخلفية/المقدمة.
- **تكامل سهل** – إعداد قائم على Maven واستدعاءات API بسيطة تحافظ على نظافة الكود.
- **تحسين الأداء** – يتم تحرير الموارد تلقائيًا عند إغلاق `Watermarker`.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) 8 أو أعلى.
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.
- Maven لإدارة التبعيات.

## إعداد GroupDocs.Watermark for Java
أضف المستودع والتبعيات إلى ملف `pom.xml` الخاص بك:

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

إذا كنت تفضل التحميل اليدوي، احصل على الملفات الثنائية من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) وأضفها إلى مسار الفئة (classpath) في مشروعك.

### الحصول على الترخيص
ابدأ برخصة تجريبية مجانية من [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). حمّل ملف الترخيص قبل أي عملية علامة مائية:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## تنفيذ خطوة بخطوة

### الخطوة 1: تحميل ملف المخطط
استخدم `DiagramLoadOptions` لفتح ملف Visio (أو أي صيغة مخطط مدعومة).

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### الخطوة 2: إنشاء العلامة المائية النصية
قم بتكوين نص العلامة المائية، الخط، اللون، علامة الخلفية، وزاوية الدوران.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### الخطوة 3: تحديد موضع العلامة المائية للمخطط
اختر ما إذا كانت العلامة المائية تظهر في الخلفية أو المقدمة لكل صفحة من المخطط.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### الخطوة 4: حفظ المخطط المائي
اكتب النتيجة إلى ملف جديد وحرّر الموارد.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|---------|------|
| **الملف غير موجود** | تحقق من المسارات المطلقة/النسبية وتأكد من أن الملف قابل للقراءة من قبل عملية Java. |
| **الترخيص غير مُطبق** | تأكد من صحة مسار ملف الترخيص وأن الملف غير معطوب. |
| **العلامة المائية غير مرئية** | تحقق من `setBackground(false)` وزاوية الدوران؛ جرّب لونًا أو شفافية مختلفة. |
| **إصدار مخطط غير مدعوم** | استخدم أحدث نسخة من GroupDocs.Watermark (24.11) التي تضيف دعمًا لإصدارات Visio الأحدث. |

## حالات الاستخدام العملية
1. **أمان المستندات** – منع المنافسين من إعادة استخدام المخططات الانسيابية المملوكة.
2. **اتساق العلامة التجارية** – تضمين اسم الشركة أو الشعار تلقائيًا عبر جميع المخططات المصدرة.
3. **تتبع التعاون** – إضافة الأحرف الأولى للمستخدم كعلامة مائية لتحديد من قام بتحرير كل مخطط.

## نصائح الأداء
- أغلق `Watermarker` بمجرد الانتهاء لتحرير الموارد الأصلية.
- لمعالجة الدفعات، أعد استخدام نسخة واحدة من `Watermarker` عندما يكون ذلك ممكنًا.
- اجعل نص العلامة المائية مختصرًا؛ الخطوط الكبيرة تزيد من زمن التقديم.

## الخلاصة
أنت الآن تعرف كيف **تنشئ علامة مائية نصية** على مخططات Visio باستخدام GroupDocs.Watermark for Java. يمنحك هذا النهج تحكمًا كاملاً في المظهر والموضع والتنسيق، مما يساعدك على حماية علامتك التجارية وأصولك البصرية بفعالية.

### الخطوات التالية
- جرّب علامات مائية صورة (`ImageWatermark`) للعلامة التجارية للشعار.
- استكشف وضع العلامة المائية على صفحات محددة عن طريق التكرار على `watermarker.getPages()` وتطبيق الخيارات بشكل شرطي.
- دمج هذه المنطق في خط أنابيب CI/CD الخاص بك لتأمين المخططات تلقائيًا قبل النشر.

## قسم الأسئلة المتكررة
1. **هل يمكنني استخدام GroupDocs.Watermark لصيغ ملفات أخرى؟**  
   نعم، يدعم ملفات PDF، مستندات Word، جداول Excel، عروض PowerPoint، والعديد غيرها.
2. **هل هناك حد لعدد العلامات المائية التي يمكنني إضافتها؟**  
   لا يوجد حد ثابت، لكن إضافة العديد من العلامات المائية المعقدة قد يؤثر على الأداء.
3. **كيف يمكنني إزالة علامة مائية من مخطط؟**  
   يوفر GroupDocs.Watermark واجهات كشف وإزالة يمكنك استدعاؤها بطريقة مشابهة لتدفق الإضافة.
4. **هل يمكن إضافة علامات مائية نصية إلى جميع الصفحات أو إلى صفحات مختارة فقط؟**  
   يمكنك تكوين `DiagramShapeWatermarkOptions` لكل صفحة أو تطبيق فلاتر قبل استدعاء `add`.
5. **ماذا أفعل إذا لم تظهر العلامة المائية كما هو متوقع؟**  
   تحقق مرة أخرى من إعدادات الموضع، وتباين اللون، وتأكد من أن المخطط لا يتم تسطيحه بعد الحفظ.

## الأسئلة المتكررة

**س: هل تعمل المكتبة مع ملفات Visio 2003 (`.vsd` )؟**  
ج: نعم – `DiagramLoadOptions` يدعم كلًا من صيغ `.vsdx` و`.vsd` القديمة.

**س: هل يمكنني تغيير شفافية العلامة المائية النصية؟**  
ج: بالتأكيد. استخدم `textWatermark.setOpacity(0.5);` لتعيين شفافية بنسبة 50 %.

**س: هل يمكن إضافة علامات مائية مختلفة إلى صفحات مخطط مختلفة؟**  
ج: نعم. قم بالتكرار عبر `watermarker.getPages()` وطبق مثيلات `TextWatermark` متميزة مع خيارات مخصصة لكل صفحة.

**س: هل هناك أي قيود ترخيص للاستخدام التجاري؟**  
ج: يتطلب ترخيص تجاري كامل للنشر في بيئات الإنتاج؛ الترخيص التجريبي مخصص للتقييم فقط.

**س: كيف يمكنني معالجة دفعة من المخططات المتعددة في تشغيل واحد؟**  
ج: ضع الخطوات السابقة داخل حلقة تقوم بتحميل كل ملف، وتطبيق العلامة المائية، وحفظه، وإغلاق `Watermarker` قبل الانتقال إلى الملف التالي.

**آخر تحديث:** 2026-04-04  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs  

## الموارد
- [الوثائق](https://docs.groupdocs.com/watermark/java/)
- [مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل أحدث نسخة](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)