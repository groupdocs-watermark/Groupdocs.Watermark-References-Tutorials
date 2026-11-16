---
date: '2026-01-23'
description: تعلم كيفية إضافة علامة مائية إلى ملفات PDF باستخدام علامات مائية نصية
  وصورية عبر GroupDocs.Watermark للغة Java – دليل شامل لأمان مستندات PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: كيفية وضع علامة مائية على PDF باستخدام GroupDocs.Watermark للـ Java
type: docs
url: /ar/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# كيفية وضع علامة مائية على PDF باستخدام GroupDocs.Watermark للغة Java

في العالم الرقمي اليوم، **كيفية وضع علامة مائية على PDF** هي سؤال شائع لأي شخص يحتاج إلى حماية الملكية الفكرية أو أصول العلامة التجارية. إضافة العلامات المائية—سواء نصية أو صورية—تساعدك على تعزيز **أمان مستندات PDF** وتجعل التوزيع غير المصرح به أصعب بكثير. في هذا الدرس، ستتعلم خطوة‑بخطوة كيفية استخدام **GroupDocs.Watermark للغة Java** لإضافة كل من العلامات المائية النصية والصورية إلى مستندات PDF.

## إجابات سريعة
- **ما المكتبة التي تضيف علامات مائية إلى PDF في Java؟** GroupDocs.Watermark للغة Java.  
- **هل يمكنني إضافة كل من العلامات المائية النصية والصورية؟** نعم، الـ API يدعم كلا النوعين.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للتقييم؛ الترخيص المدفوع يزيل القيود.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل يدعم Maven؟** بالتأكيد – فقط أضف المستودع والاعتماد.

## ما هو وضع العلامة المائية على PDF ولماذا نستخدمه؟
وضع العلامة المائية على PDF يدمج علامة مرئية أو غير مرئية تحدد الملكية أو السرية أو العلامة التجارية. إنها طريقة خفيفة الوزن لكنها قوية لردع النسخ، وإثبات التأليف، والامتثال لسياسات الشركة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

1. **Java Development Kit (JDK) 8+** مثبت على جهازك.  
2. **GroupDocs.Watermark للغة Java** (أحدث نسخة).  
3. **Maven** (أو القدرة على إضافة ملف JAR يدويًا).

### إعداد البيئة

#### تكوين Maven
أضف مستودع GroupDocs واعتماد العلامة المائية إلى ملف `pom.xml` الخاص بك:

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
إذا كنت تفضل عدم استخدام Maven، يمكنك تحميل ملف JAR مباشرة من [GroupDocs.Watermark للغة Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
للبدء بنسخة تجريبية مجانية أو للحصول على ترخيص مؤقت، زر [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). للاستخدام الإنتاجي، اشترِ اشتراكًا لفتح جميع الميزات.

## إعداد GroupDocs.Watermark للغة Java

استورد الفئة الأساسية التي تدير جميع عمليات العلامة المائية:

```java
import com.groupdocs.watermark.Watermarker;
```

هذا الاستيراد يمنحك الوصول إلى فئة `Watermarker`، وهي نقطة الدخول لإضافة العلامات المائية إلى أي نوع مستند مدعوم.

## تنفيذ خطوة‑بخطوة

فيما يلي نقسم العملية إلى أقسام منطقية: إنشاء علامات مائية نصية، إنشاء علامات مائية صورية، وأخيرًا تطبيقها على الصور داخل PDF.

### 1. تهيئة علامة مائية نصية

**لماذا علامة مائية نصية؟** إنها خفيفة الوزن، قابلة للبحث، ومثالية لإضافة إشعارات حقوق النشر أو عبارات السرية.

#### 1.1 إنشاء كائن TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 ضبط المحاذاة
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 تدوير العلامة المائية
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 تكوين الحجم
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. تهيئة علامة مائية صورية

**متى نستخدم علامة مائية صورية؟** مثالية للعلامة التجارية باستخدام الشعارات أو لإضافة أنماط بصرية معقدة.

#### 2.1 تحميل ملف الصورة
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 ضبط المحاذاة
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 تدوير العلامة المائية الصورية
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 تكوين الحجم
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. إضافة العلامات المائية إلى الصور داخل PDF

الآن سنجمع كل شيء معًا: فتح PDF، تحديد كل صورة، وتطبيق إما العلامة المائية النصية أو الصورية بناءً على الحجم.

#### 3.1 فتح مستند PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 استرجاع جميع الصور
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 تطبيق العلامات المائية بشكل شرطي
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 تحرير موارد الصورة
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 حفظ PDF المعدل
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 التنظيف
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## تطبيقات عملية لوضع العلامة المائية على PDF

| حالة الاستخدام | كيف تساعد العلامة المائية |
|----------------|---------------------------|
| **أمان المستندات** | تضع علامة على الملفات السرية، مما يردع التسريبات. |
| **حماية العلامة التجارية** | تدمج الشعارات في ملفات PDF التسويقية، مما يعزز هوية العلامة. |
| **إثبات حقوق النشر** | تضيف اسم المؤلف أو رمز © لتأكيد الملكية. |
| **التحكم في الإصدارات** | تظهر أرقام الإصدارات أو التواريخ مباشرة على الصفحة. |

## الأخطاء الشائعة والنصائح

- **فواصل المسارات:** استخدم الشرطتين المائلتين (`\\`) على Windows أو الشرط المائل (`/`) على Linux/macOS لتجنب `FileNotFoundException`.  
- **ملفات PDF الكبيرة:** عالج الصور على دفعات أو زد حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`) لتفادي أخطاء OutOfMemory.  
- **حدود الترخيص:** قد تحد النسخة التجريبية عدد الصفحات المعالجة؛ قم بالترقية للاستخدام غير المحدود.  
- **الالتباس في التدوير:** تذكر أن `setRotateAngle` يتوقع درجات؛ القيم السالبة تدور عكس اتجاه عقارب الساعة.

## الأسئلة المتكررة

**س: هل يمكنني وضع علامة مائية على ملفات PDF محمية بكلمة مرور؟**  
ج: نعم. افتح المستند باستخدام كلمة المرور عبر مُنشئ `Watermarker` الذي يقبل سلسلة كلمة المرور.

**س: هل تدعم المكتبة صيغًا أخرى مثل DOCX أو PPTX؟**  
ج: بالتأكيد. يعمل GroupDocs.Watermark مع ملفات Word وPowerPoint وExcel وكذلك ملفات الصور.

**س: كيف أغيّر شفافية العلامة المائية؟**  
ج: استخدم `setOpacity(float opacity)` على كائن العلامة المائية (قيمة بين 0.0 و 1.0).

**س: هل يمكن وضع علامة مائية فقط على الصفحة الأولى؟**  
ج: استرجع مجموعة الصفحات عبر `watermarker.getPages()` وطبق العلامة المائية على فهرس الصفحة المطلوب.

**س: ماذا لو أردت وضع علامة مائية على PDF مخزن في سحابة؟**  
ج: حمّل PDF إلى `InputStream` ومرره إلى مُنشئ `Watermarker`؛ بعد المعالجة، اكتب الـ output stream مرة أخرى إلى السحابة.

## الخلاصة

أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج **كيفية وضع علامة مائية على PDF** باستخدام GroupDocs.Watermark للغة Java. من خلال الجمع بين العلامات المائية النصية والصورية، يمكنك تحقيق أمان قوي **لمستندات PDF** يلبي متطلبات العلامة التجارية والامتثال. استكشف ميزات المكتبة الأخرى—مثل إزالة العلامات المائية أو المعالجة الدفعية—لتوسيع سير عمل المستندات الخاص بك أكثر.

---

**آخر تحديث:** 2026-01-23  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

---