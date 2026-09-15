---
date: '2026-03-08'
description: تعلم كيفية إضافة علامة مائية إلى PowerPoint باستخدام Java عبر GroupDocs.Watermark،
  وإضافة علامات مائية نصية وصورية لحماية شرائحك بفعالية.
keywords:
- GroupDocs Watermark Java
- PowerPoint watermarks
- Java presentation watermarking
title: إضافة علامة مائية إلى PowerPoint باستخدام Java وGroupDocs.Watermark
type: docs
url: /ar/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/
weight: 1
---

# إضافة علامة مائية إلى PowerPoint باستخدام Java ومكتبة GroupDocs.Watermark

حماية أصول عروضك التقديمية هي أولوية قصوى، والطريقة الأكثر بساطة للقيام بذلك هي **إضافة علامة مائية إلى PowerPoint باستخدام Java**‑style. سواء كنت تحتاج إلى العلامة التجارية، أو إشعارات حقوق النشر، أو ملصقات السرية، فإن هذا الدليل يشرح لك كيفية استخدام GroupDocs.Watermark for Java لإدراج علامات مائية نصية وصورية في كل شريحة من ملف PowerPoint.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** GroupDocs.Watermark for Java  
- **هل يمكنني إضافة كل من العلامات المائية النصية والصورية؟** نعم، الـ API يدعم كلا النوعين.  
- **هل أحتاج إلى ترخيص؟** يتوفر ترخيص مؤقت للتقييم؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل Maven مطلوب؟** ليس إلزاميًا، لكن Maven يبسط إدارة التبعيات.  

## ما هو إضافة علامة مائية إلى PowerPoint باستخدام Java؟
إضافة علامة مائية تعني تغطية كل شريحة نصًا أو رسومات شبه شفافة برمجيًا. تساعدك هذه التقنية على تعزيز اتساق العلامة التجارية، ومنع التوزيع غير المصرح به، وإبلاغ السرية دون تعديل المحتوى الأصلي.

## لماذا تستخدم GroupDocs.Watermark for Java؟
- **API كامل المميزات:** يدعم العلامات المائية النصية، الصورية، وحتى الأشكال عبر جميع صيغ Office الرئيسية.  
- **بدون تبعيات خارجية:** يعمل مباشرةً باستخدام ملفات JAR فقط.  
- **أداء عالي:** مُحسّن للعروض الكبيرة مع إمكانيات المعالجة الدفعية.  
- **متعدد المنصات:** يعمل على أي نظام تشغيل يدعم JDK.  

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8+** – تأكد من أن `java` و `javac` موجودان في PATH.  
- **Maven** – اختياري لكن يُنصح به لإدارة التبعيات.  
- **IDE** – IntelliJ IDEA أو Eclipse أو أي محرر تفضله.  

## إعداد GroupDocs.Watermark for Java
### تثبيت Maven
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
إذا كنت تفضّل إعدادًا يدويًا، احصل على أحدث ملف JAR من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
احصل على مفتاح تقييم مؤقت أو اشترِ ترخيصًا كاملاً عبر [موقع GroupDocs](https://purchase.groupdocs.com/temporary-license/). يجب وضع ملف الترخيص في مجلد الموارد (resources) الخاص بمشروعك.

### التهيئة الأساسية والإعداد
أنشئ مثالًا من `Watermarker` يشير إلى ملف PowerPoint الخاص بك:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## دليل التنفيذ
فيما يلي دليل خطوة بخطوة يضيف كل من العلامات المائية النصية والصورية إلى كل شريحة.

### إضافة علامات مائية نصية
**نظرة عامة:** يضع نصًا مخصصًا فوق صورة خلفية كل شريحة.

#### الخطوة 1: إنشاء وتكوين العلامة المائية النصية
```java
// Create a TextWatermark object
textWatermark = new TextWatermark("Protected Image", new Font("Arial", 8));
```

#### الخطوة 2: ضبط المحاذاة، الدوران، والحجم
```java
// Center align the watermark horizontally and vertically
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);

// Rotate the watermark by 45 degrees for better visibility
textWatermark.setRotateAngle(45);

// Scale based on parent dimensions, with no additional scaling factor
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

#### الخطوة 3: تطبيق العلامة المائية على الشرائح التي تحتوي على صور خلفية
```java
PresentationContent content = watermarker.getContent(PresentationContent.class);
for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Add watermark to the slide's background image
        slide.getImageFillFormat().getBackgroundImage().add(textWatermark);
    }
}
```

### إضافة علامات مائية صورية
**نظرة عامة:** يضع شعارًا أو أي صورة PNG/JPEG على كل شريحة.

#### الخطوة 1: تحميل العلامة المائية الصورية
```java
// Load the watermark image
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
```

#### الخطوة 2: ضبط الموضع والشفافية
```java
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Bottom);
imageWatermark.setOpacity(0.5f);
```

#### الخطوة 3: إدراج العلامة المائية الصورية في كل شريحة
```java
for (PresentationSlide slide : content.getSlides()) {
    slide.add(imageWatermark);
}
```

### حفظ العرض المعدل وإطلاق الموارد
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/presentation_output.pptx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## تطبيقات عملية
1. **العلامة التجارية:** تضمين شعار شركتك تلقائيًا في جميع العروض المقدمة للعملاء.  
2. **حماية حقوق النشر:** عرض إشعار حقوق النشر لمنع النسخ غير المصرح به.  
3. **ملصقات السرية:** وضع علامة على العروض الداخلية بـ “سري – لا تُوزَّع”.  
4. **تكامل إدارة المستندات:** ربط خطوة إضافة العلامة المائية بخط أنابيب CI/CD أو نظام إدارة المستندات (DMS) للحماية الفورية.  

## اعتبارات الأداء
- **المعالجة الدفعية:** بالنسبة لعروض الشرائح الكبيرة، عالجها على دفعات أصغر لتقليل استهلاك الذاكرة.  
- **تنظيف الموارد:** احرص دائمًا على إغلاق كائنات `Watermarker` و `TextWatermark` و `ImageWatermark` لتحرير الموارد الأصلية.  
- **التنفيذ المتوازي:** إذا كنت بحاجة إلى إضافة علامة مائية للعديد من الملفات، فكر في استخدام مجموعة من الخيوط (thread pool)، لكن احرص على حصر كل مثال `Watermarker` في خيط واحد.  

## المشكلات الشائعة والحلول
- **صورة خلفية فارغة:** قد تستخدم بعض الشرائح ألوانًا صلبة بدلًا من الصور. في هذه الحالة، أضف العلامة المائية مباشرة إلى الشريحة (`slide.add(textWatermark)`).  
- **أخطاء الترخيص:** تأكد من وضع ملف الترخيص المؤقت في المكان الصحيح وتعيين المسار عبر `License license = new License(); license.setLicense("path/to/license.file");`.  
- **بطء الملفات الكبيرة:** زد حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`) أو عالج الشرائح على دفعات.  

## الأسئلة المتكررة

**س: ما صيغ الملفات التي يدعمها GroupDocs.Watermark؟**  
ج: يدعم PowerPoint و Word و Excel و PDF و Visio والعديد من صيغ الصور.

**س: هل يمكنني إضافة علامات مائية صورية أيضًا؟**  
ج: نعم، المكتبة تدعم كل من العلامات المائية النصية والصورية، كما هو موضح أعلاه.

**س: كيف يمكنني التعامل مع العروض الكبيرة بكفاءة؟**  
ج: عالج الشرائح على دفعات، أغلق الموارد فورًا، وفكّر في زيادة حجم الذاكرة المخصصة للـ JVM.

**س: هل GroupDocs.Watermark Java مجانية للاستخدام؟**  
ج: يمكنك الحصول على ترخيص مؤقت للتقييم؛ يتطلب الاستخدام في الإنتاج ترخيصًا مدفوعًا.

**س: هل يمكن إزالة العلامات المائية بعد إضافتها؟**  
ج: العلامات المائية مدمجة في الملف. إزالتها تتطلب إعادة فتح العرض وتعديل الشرائح لحذف كائنات العلامة المائية.

## الموارد
- [التوثيق](https://docs.groupdocs.com/watermark/java/)
- [مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

استكشف سيناريوهات إضافية لإضافة العلامات المائية — مثل المعالجة الدفعية لعدة ملفات أو التكامل مع التخزين السحابي — لتعزيز أمان سير عمل المستندات الخاص بك.

---

**آخر تحديث:** 2026-03-08  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs