---
date: '2026-02-16'
description: تعلم كيفية إضافة علامة مائية إلى صفحة مخطط محددة باستخدام GroupDocs.Watermark
  للغة Java، بما في ذلك كيفية إضافة علامة مائية صورة في Java وحماية ملفاتك.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: وضع علامة مائية على صفحة مخطط محددة باستخدام GroupDocs.Watermark للـ Java
type: docs
url: /ar/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# إضافة علامة مائية لصفحة مخطط محددة باستخدام GroupDocs.Watermark للـ Java

حماية مخططاتك أمر حيوي، خاصة عندما تحتاج إلى **إضافة علامة مائية لصفحة مخطط محددة** لأمان الملكية الفكرية أو إسناد العلامة التجارية. في هذا البرنامج التعليمي ستتعلم خطوة بخطوة كيفية إضافة علامات مائية نصية وصورية إلى الصفحات المختارة من ملف المخطط باستخدام **GroupDocs.Watermark للـ Java**. في النهاية، ستكون جاهزًا لتأمين مخططاتك والتحكم بدقة في مكان ظهور كل علامة مائية.

## إجابات سريعة
- **ما هو الهدف الأساسي؟** إضافة علامات مائية إلى صفحات المخطط المحددة.  
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark للـ Java (Maven أو تحميل مباشر).  
- **هل يمكنني إضافة علامة مائية صورة في Java؟** نعم – استخدم `ImageWatermark` مع خيارات خاصة بالصفحة.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي مؤقت يعمل للاختبار؛ يلزم ترخيص كامل للإنتاج.  
- **كم عدد أسطر الكود؟** أقل من 30 سطرًا لتدفق عمل كامل للعلامة المائية النصية + الصورية.

## ما معنى “إضافة علامة مائية لصفحة مخطط محددة”؟
**إضافة علامة مائية لصفحة مخطط محددة** تعني تطبيق علامة بصرية—نص أو صورة—فقط على الصفحات التي تختارها داخل مخطط متعدد الصفحات (مثل Visio . vsdx). يمنحك ذلك تحكمًا دقيقًا في العلامة التجارية، وإشعارات السرية، أو بيانات حقوق النشر دون التأثير على المستند بأكمله.

## لماذا نستخدم GroupDocs.Watermark للـ Java؟
- **تحكم كامل بالصفحة** – استهدف أي فهرس صفحة تحتاجه.  
- **تنسيق غني** – الخطوط، الألوان، الشفافية، الدوران، وتكبير الصورة كلها قابلة للتخصيص.  
- **أداء محسن** – يعالج المخططات الكبيرة بكفاءة ويتكامل بسلاسة مع بناء Maven.  
- **دعم صيغ متعددة** – يعمل مع Visio، SVG، والعديد من صيغ المخططات الأخرى.

## المتطلبات المسبقة
- مكتبة **GroupDocs.Watermark للـ Java** الإصدار 24.11 أو أحدث.  
- Maven أو تحميل JAR مباشر.  
- إعداد تطوير Java أساسي (يوصى بـ JDK 8+).

## إعداد GroupDocs.Watermark للـ Java
### استخدام Maven groupdocs watermark
أضف GroupDocs.Watermark إلى مشروعك عبر Maven بإضافة ما يلي إلى ملف `pom.xml` الخاص بك:

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

### تحميل مباشر
بدلاً من ذلك، قم بتحميل أحدث نسخة مباشرة من [GroupDocs.Watermark للـ Java releases](https://releases.groupdocs.com/watermark/java/).

#### الحصول على الترخيص
ابدأ برخصة تجريبية مجانية عن طريق تحميل ترخيص مؤقت. تتوفر خيارات الشراء على موقعهم الرسمي إذا رغبت في الاستمرار باستخدام GroupDocs.Watermark.

### التهيئة الأساسية والإعداد
بعد التثبيت، قم بتهيئة فئة `Watermarker` لعمليات إضافة العلامات المائية:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## دليل التنفيذ
### إضافة علامة مائية نصية إلى صفحة محددة
لإضافة علامة مائية نصية، أنشئها وقم بتكوينها قبل تحديد الصفحة المستهدفة.

#### إنشاء علامة مائية نصية
عرّف علامتك المائية النصية بالمحتوى القابل للتخصيص، نمط الخط، الحجم، إلخ:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### تعيين فهرس الصفحة للعلامة المائية
حدد أي صفحة من المخطط ستظهر فيها العلامة المائية باستخدام `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### إضافة العلامة المائية النصية
أضف العلامة المائية التي قمت بتكوينها إلى المخطط:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### إضافة علامة مائية صورية إلى صفحة محددة
اتبع خطوات مشابهة للعلامات المائية الصورية باستخدام كائن `ImageWatermark`.

#### إنشاء علامة مائية صورية
أنشئ نسخة من `ImageWatermark` مع مسار صورة العلامة المائية المطلوبة:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### تعيين فهرس الصفحة للعلامة المائية
حدد أي صفحة يجب أن تعرض العلامة المائية الصورية:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### إضافة العلامة المائية الصورية
أضف الصورة إلى صفحة المخطط المحددة:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### حفظ وإغلاق الموارد
تذكر حفظ التغييرات وإغلاق الموارد لتجنب تسرب الذاكرة:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## تطبيقات عملية
- **أمان المستند** – تطبيق علامات مائية سرية فقط على الصفحات التي تحتوي على مخططات حساسة.  
- **العلامة التجارية** – وضع شعار شركتك على صفحة الغلاف مع ترك الصفحات الداخلية خالية.  
- **حماية حقوق النشر** – إضافة إشعار حقوق نشر إلى الصفحة الأخيرة من حزمة المخططات التقنية.

## اعتبارات الأداء
- **إدارة الذاكرة** – أغلق كل كائن علامة مائية بعد الحفظ لتحرير الموارد الأصلية.  
- **تحسين الصورة** – استخدم ملفات PNG/JPEG بالحجم المناسب للحفاظ على سرعة المعالجة.  
- **المعالجة الدفعية** – عند التعامل مع العديد من المخططات، أعد استخدام كائن `Watermarker` واحد قدر الإمكان.

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| العلامة المائية غير مرئية | فهرس `pageIndex` غير صحيح (يبدأ من الصفر) | تحقق من أن الفهرس يطابق الصفحة المقصودة. |
| الصورة مشوهة | صورة المصدر ذات دقة عالية جدًا | قم بتغيير حجم الصورة قبل إنشاء `ImageWatermark`. |
| خطأ ترخيص في الإنتاج | استخدام ترخيص تجريبي بعد انتهاء صلاحيته | ضع ملف ترخيص كامل عبر `License.setLicense("path/to/license.json")`. |

## الأسئلة المتكررة

**س1: هل يمكنني إضافة عدة علامات مائية إلى صفحة مخطط واحدة؟**  
ج1: نعم، ما عليك سوى استدعاء `watermarker.add()` مع كائنات علامة مائية مختلفة لنفس فهرس الصفحة.

**س2: ما صيغ الملفات التي يدعمها GroupDocs.Watermark للـ Java؟**  
ج2: يدعم صيغًا متعددة للمخططات والصور. راجع [توثيق API](https://reference.groupdocs.com/watermark/java) للقائمة الكاملة.

**س3: كيف أتعامل مع مشاكل الترخيص عند استخدام النسخة التجريبية؟**  
ج3: ابدأ برخصة تجريبية مجانية من GroupDocs. اشترِ ترخيصًا كاملًا لفتح جميع الميزات للإنتاج.

**س4: ما هي بعض النصائح الشائعة إذا لم تظهر العلامات المائية كما هو متوقع؟**  
ج4: تأكد من صحة فهرس الصفحة وتحقق من مسارات ملفات الصور. كما يجب التأكد من أن شفافية العلامة المائية ليست مضبوطة على 0.

**س5: كيف يمكنني تخصيص مظهر العلامة المائية بشكل أعمق؟**  
ج5: عدّل حجم الخط، الشفافية، الدوران، والموضع باستخدام الطرق المتاحة في `TextWatermark` أو `ImageWatermark`.

## موارد
- [توثيق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)
- [دليل مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل المكتبة](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)
- [معلومات الترخيص المؤقت](https://purchase.groupdocs.com/temporary-license/)

استكشف هذه الموارد لتعميق فهمك وقدراتك مع GroupDocs.Watermark للـ Java. نتمنى لك تجربة إضافة علامات مائية موفقة!

---

**آخر تحديث:** 2026-02-16  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs