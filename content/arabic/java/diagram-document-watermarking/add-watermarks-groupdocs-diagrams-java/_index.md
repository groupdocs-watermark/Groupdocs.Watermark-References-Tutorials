---
date: '2025-12-17'
description: تعلم كيفية إضافة علامة مائية إلى صفحة مخطط محددة باستخدام GroupDocs.Watermark
  للغة Java، إضافة علامة مائية إلى المخطط وإضافة علامة مائية صورة في Java. دليل خطوة
  بخطوة لحماية حقوق الملكية الفكرية الخاصة بك.
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

حماية المخططات الخاصة بك أمر حاسم، خاصة عندما يتعلق الأمر بحماية الملكية الفكرية أو ضمان الإسناد الصحيح. في هذا الدرس ستتعلم **كيفية إضافة علامة مائية لصفحة مخطط محددة** باستخدام GroupDocs.Watermark للـ Java، سواء كنت تحتاج إلى **إضافة علامة مائية إلى المخطط** كنص أو **إضافة علامة مائية بصورة** على نمط Java. في نهاية هذا الدليل ستكون قادرًا على:

- إضافة علامات مائية نصية بسلاسة إلى صفحات المخطط المختارة.  
- إدراج علامات مائية صورية في الأقسام المحددة من المخططات.  
- تحسين الأداء عند استخدام GroupDocs.Watermark.

دعنا نتأكد من أن البيئة جاهزة قبل الغوص في الكود.

## إجابات سريعة
- **ما معنى “watermark specific diagram page”؟** يشير إلى تطبيق علامة مائية فقط على الصفحات المختارة من ملف المخطط، مع ترك الصفحات الأخرى دون تعديل.  
- **ما إصدار المكتبة المطلوب؟** GroupDocs.Watermark 24.11 أو أحدث.  
- **هل يمكنني استخدام كل من العلامات المائية النصية والصورية على نفس الصفحة؟** نعم – استدعِ `watermarker.add()` لكل نوع من العلامات المائية.  
- **هل أحتاج إلى ترخيص للتطوير؟** ترخيص تجريبي مؤقت يعمل للاختبار؛ يلزم ترخيص كامل للإنتاج.  
- **هل Maven هو الطريقة الوحيدة لإضافة المكتبة؟** لا – يمكنك أيضًا تنزيل ملف JAR مباشرة (انظر “Direct Download” أدناه).

## ما هو “watermark specific diagram page”؟
عملية **watermark specific diagram page** تستهدف صفحة واحدة (أو مجموعة من الصفحات) داخل مستند مخطط (مثل Visio *.vsdx*) وتضيف طبقة نصية أو صورية. هذا مفيد للمسودات السرية، أو العلامة التجارية، أو إخطارات حقوق النشر دون تعديل الملف بالكامل.

## لماذا نستخدم GroupDocs.Watermark للـ Java؟
GroupDocs.Watermark يوفر API عالي المستوى يُبسط تعقيدات صيغ المخططات، يدعم المعالجة الدفعية، ويقدم تحكمًا دقيقًا في الشفافية، والموضع، واختيار الصفحات. كما يندمج بسلاسة مع Maven وأدوات بناء Java القياسية.

## المتطلبات المسبقة
- مكتبة **GroupDocs.Watermark for Java** الإصدار 24.11 أو أحدث مثبتة.  
- بيئة تطوير تحتوي على Maven (أو القدرة على إضافة ملف JAR يدويًا).  
- معرفة أساسية بـ Java وإمكانية الوصول إلى نظام الملفات.  

## إعداد GroupDocs.Watermark للـ Java

### استخدام Maven
قم بإضافة GroupDocs.Watermark إلى مشروعك عبر Maven بإضافة ما يلي إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، قم بتنزيل أحدث نسخة مباشرة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### الحصول على الترخيص
ابدأ برخصة تجريبية مجانية عن طريق تنزيل رخصة مؤقتة. تتوفر خيارات الشراء على موقعهم الرسمي إذا قررت الاستمرار في استخدام GroupDocs.Watermark.

### التهيئة الأساسية والإعداد
بمجرد توفر المكتبة، أنشئ كائن `Watermarker` يشير إلى المخطط الذي تريد حمايته:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## How to **add watermark to diagram** – العلامة المائية النصية

### إنشاء علامة مائية نصية
حدد النص، الخط، اللون، والشفافية التي تريد تطبيقها:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

### تعيين فهرس الصفحة للعلامة المائية
حدد الصفحة الدقيقة التي تريد إضافة العلامة المائية إليها. فهارس الصفحات تبدأ من الصفر:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

### إضافة العلامة المائية النصية
طبق العلامة المائية على الصفحة المختارة:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

## How to **add image watermark java** – العلامة المائية الصورية

### إنشاء علامة مائية صورية
حمّل الصورة التي تريد وضعها فوق المخطط (مثلاً شعار الشركة):

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

### تعيين فهرس الصفحة للعلامة المائية الصورية
اختر الصفحة التي ستظهر فيها الصورة العلامة المائية:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

### إضافة العلامة المائية الصورية
أدرج العلامة المائية الصورية على الصفحة المختارة:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

## حفظ وإغلاق الموارد
بعد إضافة جميع العلامات المائية المطلوبة، احفظ التغييرات وقم بتنظيف الموارد:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## التطبيقات العملية
- **Document Security** – تطبيق تسمية “سري” على مسودات المخططات قبل مشاركتها مع الشركاء.  
- **Branding** – ختم شعارك على صفحات محددة من المخططات التقنية.  
- **Copyright Protection** – تضمين إخطارات حقوق النشر على المخططات ذات القيمة العالية لردع الاستخدام غير المصرح به.

## اعتبارات الأداء
- إدارة الذاكرة بفعالية، خاصةً للملفات الكبيرة.  
- تحسين حجم الصور قبل استخدامها كعلامات مائية لتسريع المعالجة.  
- الاستفادة من جمع القمامة في Java بإغلاق جميع كائنات العلامة المائية بعد الحفظ.

## المشكلات الشائعة والحلول
| Symptom | Likely Cause | Fix |
|---|---|---|
| Watermark not visible | Wrong page index | Verify the zero‑based index matches the intended page. |
| Image appears distorted | High‑resolution source image | Resize the image to a reasonable dimension (e.g., 300 × 300 px). |
| License error on production | Using trial license only | Apply a full license file via `License.setLicense("path/to/license.file")`. |
| Slow processing on big diagrams | Large file size & unclosed resources | Close `Watermarker` and individual watermark objects promptly. |

## الأسئلة المتكررة

**Q1: Can I add multiple watermarks to a single diagram page?**  
A: نعم، ما عليك سوى استدعاء `watermarker.add()` مع كائنات علامات مائية مختلفة لنفس `DiagramPageWatermarkOptions`.

**Q2: What file formats are supported by GroupDocs.Watermark for Java?**  
A: يدعم صيغًا متعددة للمخططات والصور. راجع [API documentation](https://reference.groupdocs.com/watermark/java) للحصول على القائمة الكاملة.

**Q3: How do I handle licensing issues when using a trial version?**  
A: ابدأ برخصة مؤقتة مجانية من GroupDocs. للإنتاج، اشترِ رخصة كاملة لفتح جميع الميزات.

**Q4: What are some common troubleshooting tips if watermarks don’t appear as expected?**  
A: تأكد من صحة فهرس الصفحة، تحقق من مسارات الملفات للصور، وتأكد من أن إعدادات الشفافية ليست مضبوطة على 0.

**Q5: How can I customize watermark appearance further?**  
A: اضبط حجم الخط، الشفافية، الدوران، والموضع باستخدام الأساليب المتوفرة في `TextWatermark` أو `ImageWatermark`.

**Q6: Is it possible to watermark multiple pages in one call?**  
A: نعم – يمكنك إنشاء كائن `DiagramPageWatermarkOptions`، تعيين قائمة بفهارس الصفحات، وتمريره إلى `watermarker.add()`.

**Q7: Does GroupDocs.Watermark support password‑protected diagram files?**  
A: نعم، يمكنك توفير كلمة المرور عبر `DiagramLoadOptions.setPassword("yourPassword")` قبل التحميل.

## الموارد
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference Guide](https://reference.groupdocs.com/watermark/java)  
- [Download Library](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)

استكشف هذه الموارد لتعميق فهمك وقدراتك مع GroupDocs.Watermark للـ Java. نتمنى لك إضافة علامات مائية ناجحة!

---

**آخر تحديث:** 2025-12-17  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs