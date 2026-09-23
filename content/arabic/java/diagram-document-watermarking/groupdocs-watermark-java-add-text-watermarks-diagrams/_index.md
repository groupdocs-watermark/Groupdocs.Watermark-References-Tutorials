---
date: '2025-12-19'
description: تعلم كيفية إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark
  للغة Java. احمِ محتواك البصري بفعالية وتأكد من سلامة المستند.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark للغة Java
  – دليل شامل
type: docs
url: /ar/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# إضافة علامة مائية نصية إلى المخططات باستخدام GroupDocs.Watermark للـ Java: دليل شامل

## المقدمة
حماية مستندات المخططات من الاستخدام غير المصرح به أمر حاسم، و**إضافة علامة مائية نصية** توفر حلاً بسيطًا وفعالًا. في هذا الدرس ستكتشف كيفية تحميل ملفات المخططات، إنشاء علامة مائية نصية قابلة للتخصيص، وتطبيقها على صفحات الخلفية أو الأشكال المحددة باستخدام **GroupDocs.Watermark للـ Java**. في نهاية الدليل ستكون قادرًا على حماية أصولك البصرية مع الحفاظ على المظهر والشعور الأصلي.

### إجابات سريعة
- **ماذا يعني “إضافة علامة مائية نصية”?**  
  يعني ذلك دمج طبقة نصية شبه شفافة داخل المستند للإشارة إلى الملكية أو السرية.  
- **أي مكتبة تدعم وضع العلامات المائية على المخططات؟**  
  توفر GroupDocs.Watermark للـ Java دعمًا أصليًا لتنسيقات المخططات (مثل Visio، VSDX).  
- **هل أحتاج إلى ترخيص؟**  
  يلزم الحصول على ترخيص مؤقت أو كامل للاستخدام في الإنتاج؛ يتوفر نسخة تجريبية مجانية للتقييم.  
- **هل يمكنني وضع العلامة المائية على صفحات الخلفية؟**  
  نعم – استخدم الخيار `DiagramWatermarkPlacementType.SeparateBackgrounds` للحصول على **علامة مائية لصفحة الخلفية**.  
- **هل الكود متوافق مع Java 8+؟**  
  بالتأكيد – المكتبة تعمل مع JDK 8 والإصدارات الأحدث.

## ما هي العلامة المائية النصية للمخططات؟
العلامة المائية النصية هي قطعة من النص القابل للقراءة (غالبًا ما تكون شبه شفافة) تُعرض فوق أو خلف عناصر المخطط. يمكن استخدامها للعلامة التجارية، حماية حقوق النشر، أو لتحديد المسودات السرية.

## لماذا تستخدم GroupDocs.Watermark للـ Java؟
- **دعم واسع للتنسيقات** – يعمل مع Visio، VSDX، والعديد من أنواع المخططات الأخرى.  
- **تحديد دقيق للموقع** – اختر وضع العلامة المائية في المقدمة، الخلفية، أو على شكل محدد.  
- **واجهة برمجة تطبيقات بسيطة** – إنشاء وتطبيق العلامات المائية ببضع أسطر فقط من كود Java.  

## المتطلبات المسبقة
- **GroupDocs.Watermark للـ Java** (الإصدار v24.11 أو أحدث)  
- **مجموعة تطوير Java (JDK)** الإصدار 8 أو أعلى  
- Maven (أو تضمين JAR يدويًا)  

## إعداد GroupDocs.Watermark للـ Java
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
حمّل أحدث نسخة من [إصدارات GroupDocs.Watermark للـ Java](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – تقييم جميع الميزات دون مفتاح ترخيص.  
- **ترخيص مؤقت** – استخدمه أثناء التطوير لفتح جميع الوظائف.  
- **شراء** – الحصول على ترخيص إنتاج للمشاريع التجارية.  

### التهيئة الأساسية والإعداد
تأكد من وجود الاستيرادات التالية في فئة Java الخاصة بك:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## تنفيذ خطوة بخطوة

### الخطوة 1: تحميل مستند المخطط
أولاً، وجه المكتبة إلى ملف المخطط الخاص بك وقم بتهيئة خيارات التحميل.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*شرح*: يتيح لك `DiagramLoadOptions` التحكم في كيفية تحليل المخطط قبل إضافة العلامة المائية.

### الخطوة 2: إنشاء علامة مائية نصية
الآن أنشئ نص العلامة المائية وحدد نمطها البصري.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*شرح*: هذا ينشئ `TextWatermark` بالعبارة **“Test watermark 1”** باستخدام خط Calibri بحجم 19.

### الخطوة 3: تكوين الموقع – علامة مائية لصفحة الخلفية
اختر المكان الذي يجب أن تظهر فيه العلامة المائية. للحصول على **علامة مائية لصفحة الخلفية**، استخدم الخيار التالي:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*شرح*: يتحكم `DiagramShapeWatermarkOptions` في الموقع الدقيق. ضبط نوع الموقع إلى `SeparateBackgrounds` يضيف العلامة المائية إلى كل صفحة خلفية في المخطط.

### الخطوة 4: تطبيق العلامة المائية وحفظ الملف
أخيرًا، أضف العلامة المائية إلى المستند، احفظ النتيجة، وأفرغ الموارد.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*شرح*: طريقة `add` تطبق `textWatermark` المكوَّنة باستخدام خيارات الموقع، ثم يُحفظ المخطط المعدل إلى `outputPath`.

## تطبيقات عملية
- **حماية الملكية الفكرية** – منع المنافسين من إعادة استخدام المخططات المملوكة.  
- **تعزيز العلامة التجارية** – تضمين اسم الشركة أو الشعار كعلامة مائية نصية على جميع المخططات المصدرة.  
- **وثائق قانونية** – وضع علامة على المسودات السرية للمخططات الهندسية.  
- **تقديمات أكاديمية** – إرفاق أرقام هوية الطلاب أو رموز الدورات إلى المخططات لتتبع الانتحال.

## اعتبارات الأداء
- **إدارة الذاكرة** – أغلق كائن `Watermarker` (`watermarker.close()`) لتحرير الموارد الأصلية، خاصةً عند معالجة ملفات كبيرة.  
- **المعالجة الدفعية** – كرر عبر مجموعة من مسارات المخططات وأعد استخدام كائن `Watermarker` واحد حيثما أمكن لتقليل الحمل.  

## المشكلات الشائعة والحلول
| المشكلة | الحل |
|-------|----------|
| **OutOfMemoryError على مخططات كبيرة** | زيادة حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`) ومعالجة الملفات واحدةً تلو الأخرى. |
| **العلامة المائية غير مرئية** | تأكد من أن لون العلامة المائية لديه تباين كافٍ؛ اضبط الشفافية عبر `textWatermark.setOpacity(0.5)`. |
| **تنسيق مخطط غير مدعوم** | تحقق من أن التنسيق مدرج في وثائق تنسيقات GroupDocs.Watermark المدعومة. |

## الأسئلة المتكررة

**س: ما هو أفضل حجم خط للعلامات المائية؟**  
ج: يعتمد الحجم المثالي على أبعاد المخطط؛ 12‑20 pt يعمل جيدًا في معظم الحالات.

**س: هل يمكنني تخصيص ألوان العلامة المائية؟**  
ج: نعم، استخدم `textWatermark.setColor(Color.GRAY)` (أو أي `java.awt.Color`).

**س: كيف يمكنني التعامل مع دفعات كبيرة من المستندات؟**  
ج: استفد من API الدفعات في المكتبة أو اكتب حلقة تعيد استخدام كائنات `Watermarker` لتقليل الحمل.

**س: هل هناك أي قيود على GroupDocs.Watermark؟**  
ج: تدعم المكتبة معظم تنسيقات المخططات الشائعة، لكن بعض الامتدادات المملوكة قد لا تُعرض بالكامل. راجع [الوثائق](https://docs.groupdocs.com/watermark/java/) للتفاصيل.

**س: كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟**  
ج: زر [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10) للحصول على مساعدة المجتمع أو تواصل مباشرةً مع دعم GroupDocs.

## موارد إضافية
- **الوثائق**: [توثيق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API**: [مرجع API للـ Java](https://reference.groupdocs.com/watermark/java)  
- **تحميل**: [احصل على GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى الدعم المجاني**: [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10)  
- **ترخيص مؤقت**: [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)  

---

**آخر تحديث:** 2025-12-19  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs  

---