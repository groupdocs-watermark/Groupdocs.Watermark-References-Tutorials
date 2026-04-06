---
date: '2026-03-22'
description: تعلم كيفية وضع علامة مائية على ملفات Excel عن طريق إضافة علامة مائية
  نصية باستخدام GroupDocs.Watermark للغة Java. احمِ جداولك الإلكترونية وعزز العلامة
  التجارية.
keywords:
- text watermark Excel
- GroupDocs.Watermark Java
- Excel document security
title: كيفية وضع علامة مائية نصية على أوراق Excel باستخدام GroupDocs.Watermark للـ
  Java
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/
weight: 1
---

# كيف تضيف علامة مائية نصية إلى أوراق Excel باستخدام GroupDocs.Watermark للغة Java

عندما تحتاج إلى **كيفية وضع علامة مائية على ملفات Excel**—خاصةً تلك التي تحتوي على بيانات حساسة—إضافة علامة مائية نصية واضحة ومهنية هي واحدة من أكثر الطرق فعالية لحماية المحتوى وتعزيز هوية العلامة التجارية. في هذا الدرس سنستعرض الخطوات الدقيقة **لإضافة علامة مائية نصية إلى ملفات Excel** باستخدام مكتبة GroupDocs.Watermark للغة Java، بدءًا من إعداد المشروع وحتى حفظ المصنف النهائي المؤمّن.

## إجابات سريعة
- **ما المكتبة التي يجب استخدامها؟** GroupDocs.Watermark للغة Java.  
- **هل يمكنني إضافة علامة مائية نصية إلى كل ورقة؟** نعم – قم بالتكرار عبر كل ورقة عمل وطبق نفس العلامة المائية.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ الترخيص الدائم مطلوب للإنتاج.  
- **ما نسخة Java المدعومة؟** JDK 8 أو أحدث.  
- **هل ستؤثر العلامة المائية على بيانات الخلايا؟** لا، فهي تُضيف صورة فوق ورقة العمل فقط.

## ما هو وضع العلامة المائية على Excel؟
وضع العلامة المائية على Excel يعني إدراج علامة مرئية—نص أو صورة—مباشرةً على العناصر البصرية لورقة العمل (مثل الصور) بحيث يمكن لأي شخص يفتح الملف رؤية إشعار الملكية أو السرية. تساعد هذه التقنية في ردع التوزيع غير المصرح به وتضيف مظهرًا احترافيًا لتقاريرك.

## لماذا نضيف علامة مائية نصية إلى Excel باستخدام Java؟
- **الأمان** – يوضح بوضوح أن المعلومات سرية أو مملوكة.  
- **اتساق العلامة التجارية** – يعزز هوية الشركة عبر جميع جداول البيانات المشتركة.  
- **الأتمتة** – تتيح لك Java إدراج العلامات المائية برمجيًا، مما يوفر الوقت على التعديلات اليدوية.  
- **دعم صيغ متعددة** – يعمل مع ملفات `.xlsx` وملفات `.xls` القديمة.

## المتطلبات المسبقة
- **Java Development Kit (JDK)** 8 أو أحدث.  
- **Maven** لإدارة الاعتمادات.  
- إلمام أساسي بصيغة Java ومفاهيم البرمجة الكائنية.

## إعداد GroupDocs.Watermark للغة Java
لبدء العمل، أضف اعتماد GroupDocs.Watermark إلى مشروع Maven الخاص بك.

### باستخدام Maven
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
بدلاً من ذلك، حمّل أحدث ملف JAR من [إصدارات GroupDocs.Watermark للغة Java](https://releases.groupdocs.com/watermark/java/).

**الحصول على الترخيص**
- **نسخة تجريبية مجانية** – استكشف جميع الميزات دون تكلفة.  
- **ترخيص مؤقت** – للاستخدام قصير الأمد في الاختبار.  
- **شراء** – لفتح جميع إمكانات الإنتاج.

### التهيئة الأساسية
```java
import com.groupdocs.watermark.Watermarker;
// Initialize watermarker instance for your document
Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
```

## دليل التنفيذ

### الميزة 1: إنشاء علامة مائية نصية وتكوين خصائصها
إنشاء وتخصيص العلامة المائية يتضمن تحديد النص، الخط، المحاذاة، زاوية الدوران، والقياس.  

#### نظرة عامة خطوة بخطوة
**تعريف العلامة المائية الخاصة بك**
```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a new TextWatermark object
text watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// Configure the watermark properties
text watermark.setHorizontalAlignment(HorizontalAlignment.Center);
text watermark.setVerticalAlignment(VerticalAlignment.Center);
text watermark.setRotateAngle(45); // Set rotation angle
text watermark.setSizingType(SizingType.ScaleToParentDimensions);
text watermark.setScaleFactor(1); // Maintain original size scale factor
```
- **النص والخط** – اختر رسالة واضحة وخطًا مقروءًا.  
- **المحاذاة** – التوسيط يعمل جيدًا لمعظم الصور.  
- **الدوران والقياس** – ميل بزاوية 45° يجعل العلامة المائية بارزة دون إخفاء الصورة.

### الميزة 2: تحميل مستند جدول بيانات لتطبيق العلامة المائية
حمّل المصنف مع الخيارات المناسبة حتى يتمكن GroupDocs من الوصول إلى صوره الداخلية.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
// Load your Excel spreadsheet
documentLoadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", documentLoadOptions);
```

### الميزة 3: إضافة علامة مائية نصية إلى الصور في ورقة العمل
قم بالتكرار عبر الصور في الورقة الأولى وطبق العلامة المائية المُكوَّنة.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.WatermarkableImageCollection;

// Access content from your loaded document
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
WatermarkableImageCollection images = content.getWorksheets().get_Item(0).findImages();

for (com.groupdocs.watermark.contents.WatermarkableImage image : images) {
    // Add the configured watermark to each image in the worksheet
    image.add(watermark);
}
```

### الميزة 4: حفظ وإغلاق مستند جدول البيانات المُمَوسَّى
احفظ التغييرات في ملف جديد ونظّف الموارد المستخدمة.

```java
// Save the changes to a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx");
// Close the watermarker instance to free resources
watermarker.close();
```

## تطبيقات عملية
- **أمان المستندات** – حماية النماذج المالية أو بيانات الموارد البشرية السرية.  
- **العلامة التجارية** – إدراج شعارات الشركة أو إخطارات قانونية عبر جميع التقارير المشتركة.  
- **حماية حقوق النشر** – ردع السرقة عن طريق وضع علامة على كل صورة مُصدَّرة.

## اعتبارات الأداء
- حافظ على تحديث GroupDocs.Watermark للاستفادة من أحدث تحسينات الأداء.  
- حرر كائن `Watermarker` فورًا (`close()`) لتفريغ الذاكرة.  
- بالنسبة للمصنفات الكبيرة جدًا، عالج أوراق العمل على دفعات لتجنب استهلاك الذاكرة العالي.

## المشكلات الشائعة والحلول
| المشكلة | الحل |
|-------|----------|
| العلامة المائية غير مرئية | تأكد من أن ورقة العمل تحتوي فعليًا على صور؛ الـ API يضيف العلامة المائية فقط على الصور، وليس على الخلايا. |
| العلامة المائية غير محاذاة | عدّل `HorizontalAlignment` / `VerticalAlignment` أو غيّر `RotateAngle`. |
| أخطاء نفاد الذاكرة في الملفات الكبيرة | زد حجم heap الخاص بـ JVM (`-Xmx`) أو عالج كل ورقة عمل على حدة. |
| أخطاء الترخيص | تأكد من أن ملف الترخيص التجريبي أو الدائم مُشار إليه بشكل صحيح في مشروعك. |

## الأسئلة المتكررة

**س: هل يمكنني استخدام هذا على جميع إصدارات Excel؟**  
ج: نعم، يدعم GroupDocs صيغ `.xlsx` و `.xls`.

**س: ماذا أفعل إذا لم تظهر العلامة المائية بشكل صحيح؟**  
ج: تحقق من إعدادات المحاذاة وتأكد من أن أبعاد الصورة مناسبة لمعامل القياس المختار.

**س: كيف يمكنني تخصيص نمط الخط أكثر؟**  
ج: استخدم فئة `Font` لتحديد الوزن (bold)، المائل (italic)، اللون، أو أي سمات طباعية أخرى.

**س: هل يمكن إضافة علامات مائية إلى جميع الأوراق في المصنف؟**  
ج: بالتأكيد—قم بالتكرار عبر `content.getWorksheets()` وطبق نفس منطق `image.add(watermark)` على كل ورقة.

**س: كيف أتعامل مع ملفات Excel الكبيرة بكفاءة؟**  
ج: عالج أوراق العمل بشكل تدريجي، أغلق كل كائن `Watermarker` بعد الحفظ، وفكّر في زيادة حجم heap للـ JVM.

## موارد
- [توثيق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- [مرجع API](https://reference.groupdocs.com/watermark/java)  
- [تحميل GroupDocs.Watermark للغة Java](https://releases.groupdocs.com/watermark/java/)  
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)  
- [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) 

من خلال دمج هذه الخطوات في مشاريع Java الخاصة بك، يمكنك **إضافة علامة مائية إلى ملفات Excel** بسرعة، مع ضمان الأمان واتساق العلامة التجارية.

---

**آخر تحديث:** 2026-03-22  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

---