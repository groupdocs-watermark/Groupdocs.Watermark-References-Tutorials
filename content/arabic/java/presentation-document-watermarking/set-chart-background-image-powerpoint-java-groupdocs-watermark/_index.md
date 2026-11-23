---
date: '2026-03-17'
description: تعلم كيفية حفظ صور المخططات في PowerPoint وتعيين خلفية المخطط باستخدام
  Java وGroupDocs.Watermark. اتبع هذا الدليل خطوة بخطوة لتحسين تصور البيانات.
keywords:
- set chart background image PowerPoint
- Java GroupDocs.Watermark
- PowerPoint presentation enhancement
title: حفظ صورة مخطط PowerPoint باستخدام Java و GroupDocs.Watermark
type: docs
url: /ar/java/presentation-document-watermarking/set-chart-background-image-powerpoint-java-groupdocs-watermark/
weight: 1
---

 for Java" translate: "**تم الاختبار مع:** GroupDocs.Watermark 24.11 لـ Java"

"**Author:** GroupDocs" translate: "**المؤلف:** GroupDocs"

Now ensure we keep all markdown formatting.

Let's assemble final output.# حفظ صورة مخطط PowerPoint باستخدام Java & GroupDocs.Watermark

في هذا الدرس ستتعلم **كيفية حفظ مخطط PowerPoint** كصور وتطبيق خلفية مخصصة، مما يمنح عروضك التقديمية مظهرًا مصقولًا ومتسقًا مع العلامة التجارية. سنستعرض العملية بالكامل باستخدام Java وGroupDocs.Watermark، بدءًا من إعداد المكتبة إلى تكوين خيارات الشفافية والتكرار.

## إجابات سريعة
- **ماذا يعني “حفظ مخطط PowerPoint”؟** يعني تصدير المخطط كجزء من ملف PowerPoint بعد تطبيق التخصيصات البصرية.  
- **أي مكتبة تضيف صورة خلفية للمخطط؟** توفر GroupDocs.Watermark for Java واجهة برمجة تطبيقات بسيطة لتعيين صور خلفية للمخططات.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ يتطلب الاستخدام في الإنتاج ترخيصًا كاملًا.  
- **هل يمكنني تكرار صورة الخلفية؟** نعم – استخدم الطريقة `setTileAsTexture(true)` لتكرار الصورة كملمس.  
- **هل Java 8 كافية؟** المكتبة تدعم JDK 8 والإصدارات الأحدث.

## ما هو “حفظ مخطط PowerPoint”؟
يشير حفظ مخطط PowerPoint إلى تضمين مخطط داخل شريحة والحفاظ على أي تغييرات بصرية—مثل صورة خلفية مخصصة—في ملف `.pptx` النهائي. يتيح لك ذلك توزيع عروض تقديمية تحتوي بالفعل على المظهر والشعور المطلوب.

## لماذا تعيين خلفية للمخطط باستخدام GroupDocs.Watermark؟
- **اتساق العلامة التجارية:** تطبيق شعارات الشركة أو القوام الموضوعية مباشرة خلف بيانات المخطط.  
- **تحسين القابلية للقراءة:** ضبط الشفافية بحيث تظل نقاط البيانات واضحة بينما تضيف الخلفية سياقًا بصريًا.  
- **الأتمتة:** دمج العملية في خدمات الخلفية، خطوط معالجة الدُفعات، أو سير عمل CI/CD.  
- **الأداء:** تتعامل GroupDocs.Watermark مع العروض التقديمية الكبيرة بكفاءة، خاصةً عند اتباع نصائح التحسين المذكورة لاحقًا في هذا الدليل.

## المتطلبات المسبقة

### المكتبات المطلوبة
- **GroupDocs.Watermark for Java** (الإصدار الأخير)  
- Java Development Kit (JDK) مثبت على جهازك

### إعداد البيئة
- بيئة تطوير متكاملة (IDE) مثل IntelliJ IDEA أو Eclipse مُعدَّة مع JDK.  
- Maven لإدارة التبعيات.

### المتطلبات المعرفية
- برمجة Java الأساسية وإدخال/إخراج الملفات.  
- الإلمام بهياكل شرائح PowerPoint والمخططات.

## إعداد GroupDocs.Watermark لـ Java

### التثبيت عبر Maven
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

### التحميل المباشر
بدلاً من ذلك، قم بتحميل أحدث إصدار مباشرةً من [إصدارات GroupDocs.Watermark لـ Java](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية:** استكشاف جميع الميزات دون تكلفة.  
- **ترخيص مؤقت:** استخدمه لفترات تقييم ممتدة.  
- **شراء:** الحصول على ترخيص كامل للاستخدام الإنتاجي غير المقيد.

## دليل التنفيذ

### تحميل ملف العرض التقديمي
أولاً، قم بتحميل ملف PowerPoint الذي يحتوي على المخطط الذي تريد تعديله:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\presentation.pptx", loadOptions);
```
- **السبب:** هذا ينشئ كائن `Watermarker` يمنحك إمكانية الوصول البرمجي إلى محتوى العرض التقديمي.

### استرجاع وتعديل خصائص المخطط
بعد ذلك، حدد المخطط وحمّل الصورة التي تريد استخدامها كخلفية له:

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);

// Load image to be set as background for chart.
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY\\test_image.png");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```
- **السبب:** تحويل الصورة إلى مصفوفة بايت يتيح لـ GroupDocs.Watermark تضمينها مباشرةً في تنسيق تعبئة المخطط.

### تعيين صورة الخلفية
الآن اربط الصورة بالمخطط الأول في الشريحة الأولى:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setBackgroundImage(new PresentationWatermarkableImage(imageBytes));
```
- **السبب:** هذه العملية تستبدل خلفية المخطط الافتراضية بالصورة المخصصة الخاصة بك، محققة تأثير **تعيين خلفية المخطط**.

### تكوين الشفافية والتكرار
ضبط المظهر بدقة باستخدام الشفافية وتكرار النسيج:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTransparency(0.5);
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTileAsTexture(true);
```
- **السبب:** الشفافية (`0.5`) تحافظ على وضوح البيانات، بينما `setTileAsTexture(true)` **تكرار خلفية المخطط** لإنشاء نمط سلس.

### حفظ وإغلاق الموارد
أخيرًا، اكتب العرض التقديمي المعدل إلى القرص وحرّر الموارد:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY\\updated_presentation.pptx");
watermarker.close();
```
- **السبب:** حفظ التغييرات ينشئ ملفًا جديدًا يمكنك توزيعه، وإغلاق `Watermarker` يحرّر موارد النظام.

## تطبيقات عملية
1. **تقارير الشركات:** إدراج شعارات العلامة التجارية أو ألوان الشركة كخلفيات للمخططات.  
2. **شرائح تعليمية:** استخدام صور موضوعية (مثل الخرائط أو الجزيئات) لجعل البيانات أكثر جاذبية.  
3. **عروض تسويقية:** إضافة قوام أو رسومات بنمط العلامة المائية لتمييز شرائحك عن المنافسين.

## اعتبارات الأداء
- **إعادة تحجيم الصور** قبل تضمينها للحفاظ على حجم الملف ضمن حدود معقولة.  
- **استخدام try‑with‑resources** للتيارات لضمان التنظيف التلقائي.  
- **تجنب تحميل عروض تقديمية كبيرة** بالكامل إلى الذاكرة مرة واحدة؛ عالج الشرائح بشكل تدريجي عندما يكون ذلك ممكنًا.

## المشكلات الشائعة وإصلاح الأخطاء

| المشكلة | الحل |
|-------|----------|
| `OutOfMemoryError` عند معالجة صور كبيرة | أعد تحجيم الصورة أو استخدم التحميل القائم على `InputStream` بدلاً من قراءة الملف بالكامل إلى مصفوفة بايت. |
| صورة الخلفية غير مرئية | تحقق من أن `ImageFillFormat` للمخطط لم يتم استبداله لاحقًا في الشيفرة. |
| الشفافية تبدو داكنة جدًا | قم بتعديل القيمة الممررة إلى `setTransparency()` (النطاق 0.0–1.0). |

## الأسئلة المتكررة

**س:** ما الفرق بين `setBackgroundImage` و `add watermark chart`؟  
**ج:** `setBackgroundImage` يستبدل تعبئة المخطط بصورة، بينما إضافة مخطط علامة مائية يضع نصًا أو رسومات شبه شفافة فوق بيانات المخطط.

**س:** هل يمكنني تطبيق نفس الخلفية على عدة مخططات في آن واحد؟  
**ج:** نعم—قم بالتكرار عبر `content.getSlides().get_Item(i).getCharts()` وطبق نفس `PresentationWatermarkableImage` على `ImageFillFormat` لكل مخطط.

**س:** هل يدعم GroupDocs.Watermark ملفات GIF المتحركة كخلفيات للمخططات؟  
**ج:** المكتبة تتعامل مع ملفات GIF كصور ثابتة؛ يتم استخدام الإطار الأول فقط.

**س:** كيف أضمن أن الخلفية تتناسب بشكل صحيح مع أحجام الشرائح المختلفة؟  
**ج:** استخدم `setTileAsTexture(true)` لتكرار الصورة أو احسب الأبعاد المناسبة بناءً على عرض وارتفاع الشريحة قبل تعيين الخلفية.

**س:** هل هناك طريقة للتحقق برمجيًا مما إذا كان المخطط يحتوي بالفعل على صورة خلفية؟  
**ج:** يمكنك فحص `getImageFillFormat().getBackgroundImage()`؛ إذا أعاد `null`، فلا توجد صورة محددة.

## الموارد
- **توثيق GroupDocs.Watermark:** [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API لـ GroupDocs.Watermark:** [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **تنزيلات GroupDocs:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GroupDocs.Watermark على GitHub:** [GroupDocs.Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى دعم GroupDocs Watermark:** [GroupDocs Watermark Forum](https://forum.groupdocs.com/c/watermark/10)  
- **التقدم بطلب للحصول على ترخيص مؤقت:** [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**آخر تحديث:** 2026-03-17  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 لـ Java  
**المؤلف:** GroupDocs