---
date: '2026-03-30'
description: تعلم كيفية إضافة علامة مائية إلى جدول البيانات باستخدام GroupDocs.Watermark
  للغة Java، مع تغطية تقنيات النص وإضافة علامة مائية صورة في دليل خطوة بخطوة.
keywords:
- GroupDocs Watermark Java
- add watermarks to spreadsheets
- Java watermarking guide
title: إضافة علامة مائية إلى جدول البيانات باستخدام GroupDocs.Watermark لجافا
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-watermarks-to-spreadsheets-using-groupdocs-watermark-for-java/
weight: 1
---

# إضافة علامة مائية إلى جدول بيانات باستخدام GroupDocs.Watermark للغة Java: دليل شامل

في بيئة اليوم المعتمدة على البيانات، **إضافة علامة مائية إلى جدول بيانات** هي واحدة من أكثر الطرق فاعلية لحماية المعلومات الحساسة من الاستخدام غير المصرح به أو العبث. سواءً كنت تتعامل مع تقارير أعمال سرية، أو بيانات مالية، أو بيانات شخصية، فإن العلامة المائية الموضوعة بشكل جيد تشير إلى الملكية وتثني عن سوء الاستخدام. يشرح هذا الدرس كل خطوة مطلوبة لإضافة علامات مائية نصية وصورية إلى ملفات Excel باستخدام GroupDocs.Watermark للغة Java.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** GroupDocs.Watermark for Java (v24.11 أو أحدث).  
- **هل يمكنني إضافة كل من العلامات المائية النصية والصورية؟** نعم – الـ API يدعم كلا النوعين.  
- **هل يلزم وجود ترخيص للإنتاج؟** يلزم وجود ترخيص GroupDocs صالح؛ يتوفر نسخة تجريبية مجانية.  
- **ما نسخة Java المدعومة؟** أي بيئة تشغيل JDK 8+ تعمل مع المكتبة.  
- **كيف يمكنني إزالة العلامة المائية لاحقًا؟** استخدم طرق الإزالة في الـ API – راجع قسم “إزالة العلامة المائية من جدول البيانات”.

## ما هو إضافة علامة مائية إلى جدول بيانات؟
العلامة المائية هي طبقة نصف شفافة (نصية أو صورية) تظهر خلف محتوى جدول البيانات. تظل مرئية عندما يُفتح الملف في Excel أو عارضات أخرى، وتعمل كإشارة بصرية على أن المستند سري أو مملوك.

## لماذا استخدام GroupDocs.Watermark للغة Java؟
يقدم GroupDocs.Watermark API بسيطًا وعالي الأداء يعمل عبر جميع صيغ جداول البيانات الرئيسية (XLS, XLSX, ODS). يتعامل مع الملفات الكبيرة، يدعم المعالجة الدفعية، ويوفر تحكمًا دقيقًا في الموضع والشفافية والدوران — دون الحاجة إلى Microsoft Office على الخادم.

## المتطلبات المسبقة
1. **مكتبة GroupDocs.Watermark** – الإصدار 24.11 أو أحدث.  
2. **مجموعة تطوير جافا (JDK)** – JDK 8 أو أحدث مثبت.  
3. **Maven** (أو أداة بناء أخرى) لإدارة التبعيات.  
4. **معرفة أساسية بجافا** – يجب أن تكون مرتاحًا لإنشاء الفئات ومعالجة الاستثناءات.

## إعداد GroupDocs.Watermark للغة Java
يمكنك إضافة المكتبة إلى مشروعك عبر Maven أو بتحميل ملف JAR مباشرة.

### استخدام Maven
أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، قم بتحميل أحدث JAR من صفحة الإصدار الرسمية: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### الحصول على الترخيص
- **نسخة تجريبية مجانية** – اختبار جميع الميزات دون تكلفة.  
- **ترخيص مؤقت** – طلب ترخيص قصير الأجل لتقييم ممتد.  
- **ترخيص كامل** – شراء للاستخدام الإنتاجي غير المحدود.

## التهيئة الأساسية والإعداد
استورد الفئات المطلوبة في ملف مصدر Java الخاص بك وتأكد من أن المكتبة موجودة في classpath قبل المتابعة.

## دليل التنفيذ
فيما يلي دليل خطوة بخطوة يغطي تحميل جدول بيانات، إضافة كل من العلامات المائية النصية والصورية، وأخيرًا حفظ الملف المحمي.

### تحميل مستند جدول بيانات
**نظرة عامة:** فتح ملف Excel الذي تريد حمايته.

#### الخطوة 1: تحديد مسار الملف
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
```

#### الخطوة 2: إنشاء خيارات التحميل لجداول البيانات
```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
```

#### الخطوة 3: تهيئة كائن Watermarker
```java
Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### إضافة علامة مائية نصية
**نظرة عامة:** إدراج علامة مائية نصية قابلة للقراءة مثل “سري”.

#### الخطوة 1: تحديد نص العلامة المائية والنمط
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
```

#### الخطوة 2: تطبيق العلامة المائية النصية على كل ورقة
```java
watermarker.add(watermark);
```

### إضافة علامة مائية صورية
**نظرة عامة:** استخدم صورة (شعار، ختم، إلخ) لحماية بصرية أقوى.

#### الخطوة 1: تحديد كائن العلامة المائية الصورية
```java
ImageWatermark imageWatermark = new ImageWatermark("path/to/image.png");
```

#### الخطوة 2: تطبيق العلامة المائية الصورية على المستند
```java
watermarker.add(imageWatermark);
```

### حفظ وإغلاق المستند المموج بالعلامة المائية
**نظرة عامة:** حفظ التغييرات وإطلاق الموارد.

#### الخطوة 1: تحديد مسار ملف الإخراج
```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx";
```

#### الخطوة 2: حفظ جدول البيانات المموج بالعلامة المائية
```java
watermarker.save(outputPath);
```

#### الخطوة 3: إغلاق Watermarker لتحرير الذاكرة
```java
watermarker.close();
```

## كيفية إزالة العلامة المائية من جدول البيانات
إذا احتجت إلى إزالة علامة مائية لاحقًا (على سبيل المثال، بعد انتهاء فترة سرية المستند)، يوفر GroupDocs.Watermark طريقة `remove()`. ستقوم بتحميل المستند بنفس الطريقة، وتستدعي `watermarker.remove(watermark)` لكل علامة مائية تريد حذفها، ثم حفظ الملف مرة أخرى. يمكن العثور على تفاصيل استخدام الـ API في الوثائق الرسمية.

## المشكلات الشائعة والحلول
| المشكلة | السبب المحتمل | الحل |
|---------|--------------|-----|
| **`FileNotFoundException`** | مسار الملف غير صحيح | تحقق من المسار المطلق/النسبي وتأكد من وجود الملف. |
| **OutOfMemoryError on large files** | عدم إغلاق كائنات Watermarker | دائمًا استدعِ `watermarker.close()` داخل كتلة `finally` أو استخدم try‑with‑resources. |
| **Watermark not visible** | تم ضبط الشفافية منخفضة جدًا أو تم وضعها خلف الخلايا | قم بضبط الشفافية أو استخدم `watermark.setRotationAngle(45)` لجعلها بارزة. |
| **License errors** | ملف الترخيص مفقود أو منتهي الصلاحية | ضع ملف `license.lic` صالح في classpath أو اضبط الترخيص برمجيًا. |

## التطبيقات العملية
يمكن دمج GroupDocs.Watermark في العديد من السيناريوهات الواقعية:

1. **إدارة الوثائق المؤسسية** – تأمين التقارير المالية الداخلية قبل التوزيع.  
2. **المكاتب القانونية** – وضع علامة مائية “محجوز” على ملفات القضايا لردع التسريبات.  
3. **المؤسسات التعليمية** – وضع علامة على أعمال الطلاب بشعار المدرسة لمنع الانتحال.  

## اعتبارات الأداء
عند معالجة العديد من جداول البيانات أو ملفات كبيرة جدًا، احرص على مراعاة هذه النصائح:

- **إدارة الموارد:** دائمًا أغلق كائنات `Watermarker` لتحرير الموارد الأصلية.  
- **المعالجة الدفعية:** استخدم `ExecutorService` في Java لتوازي إضافة العلامات المائية عبر ملفات متعددة.  
- **مراقبة الذاكرة:** بالنسبة للملفات > 100 ميغابايت، فكر في استخدام واجهات برمجة التطبيقات المتدفقة أو زيادة حجم heap في JVM.

## الأسئلة المتكررة
**س: هل يمكنني إضافة علامة مائية صورية باستخدام GroupDocs.Watermark للغة Java؟**  
ج: بالتأكيد. استخدم الفئة `ImageWatermark` كما هو موضح في قسم “إضافة علامة مائية صورية”.

**س: كيف يمكنني إزالة علامة مائية من جدول بيانات؟**  
ج: قم بتحميل المستند، استدعِ `watermarker.remove(existingWatermark)`، ثم احفظ الملف. راجع وثائق الـ API للحصول على التفاصيل الدقيقة للطرق المتعددة.

**س: هل تدعم المكتبة صيغًا غير XLSX؟**  
ج: نعم – تعمل مع XLS، ODS، وغيرها من صيغ جداول البيانات المدعومة من معيار OpenXML.

**س: ماذا أفعل إذا واجهت أخطاءً أثناء إضافة العلامة المائية؟**  
ج: تحقق مرة أخرى من مسارات الملفات، تأكد من تحميل الترخيص بشكل صحيح، وراجع تتبع الأخطاء (stack trace) للعثور على التبعيات المفقودة.

**س: هل يمكنني تخصيص موضع ودوران العلامة المائية؟**  
ج: يوفر الـ API طرقًا مثل `setHorizontalAlignment()`, `setVerticalAlignment()`, و `setRotationAngle()` لضبط الموضع بدقة.

## الموارد
- **الوثائق:** [GroupDocs Watermark Java Documentation](https://docs.groupdocs.com/watermark/java/)  
- **مرجع الـ API:** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **التحميل:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **مستودع GitHub:** [GroupDocs.Watermark for Java on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **منتدى الدعم المجاني:** [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **ترخيص مؤقت:** [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

**آخر تحديث:** 2026-03-30  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs