---
date: '2026-03-20'
description: تعلم كيفية إضافة علامة مائية باستخدام مجموعة أدوات GroupDocs.Watermark
  Java SDK لإضافة علامة مائية صورة إلى ملف Excel، وهو مثالي للعلامة التجارية وأمان
  المستندات.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'كيفية إضافة علامة مائية: علامة مائية صورة إلى جدول إكسل باستخدام مجموعة GroupDocs.Watermark
  SDK للـ Java'
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# كيفية إضافة علامة مائية إلى جدول بيانات إكسل باستخدام GroupDocs.Watermark Java SDK

يمكن حماية ملفات إكسل من التوزيع غير المصرح به أو ببساطة تعزيز هوية العلامة التجارية من خلال إضافة علامة مرئية تبقى ظاهرة بغض النظر عن طريقة عرض الملف. في هذا الدليل ستتعلم **كيفية إضافة علامة مائية** — تحديدًا علامة مائية صورة — إلى رأس أو تذييل جدول بيانات إكسل باستخدام **GroupDocs.Watermark Java SDK**. في نهاية الدليل ستكون قادرًا على تضمين شعار، أو شارة سرية، أو أي صورة مخصصة مباشرةً في دفتر العمل دون تعديل بيانات الخلايا.

## إجابات سريعة
- **ماذا يعني “كيفية إضافة علامة مائية”?** إضافة طبقة صورة (أو نص) تظهر على كل صفحة مطبوعة أو على أقسام محددة مثل الرؤوس/التذييلات.  
- **أي مكتبة تدعم ذلك في Java؟** `GroupDocs.Watermark` Java SDK (الإصدار الأخير).  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتطوير؛ يلزم ترخيص تجاري للإنتاج.  
- **هل يمكنني إضافة شعار إلى الرأس؟** نعم – استخدم علامة مائية صورة واضبط خيار الرأس (`add logo to header`).  
- **هل يمكن معالجة عدة أوراق عمل في آن واحد؟** قم بالتكرار عبر مؤشرات الأوراق وتطبيق نفس العلامة المائية على كل ورقة.

## المتطلبات المسبقة

للمتابعة، تأكد من أن لديك:

- **GroupDocs.Watermark for Java SDK** (الإصدار 24.11 أو أحدث).  
- **Java Development Kit (JDK)** 8 أو أعلى.  
- إلمام أساسي بـ Java وبُنى ملفات إكسل.  

## إعداد GroupDocs.Watermark لـ Java SDK

أولاً، أضف تبعيات Maven المطلوبة حتى يكون SDK متاحًا في مسار الفئات الخاص بك.

### تكوين Maven

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

إذا كنت تفضل عدم استخدام Maven، احصل على أحدث ملف JAR من صفحة الإصدار الرسمية: [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

**الحصول على الترخيص**  
- احصل على نسخة تجريبية مجانية أو مفتاح ترخيص مؤقت لتقييم جميع الميزات.  
- اشترِ ترخيصًا كاملاً للنشر التجاري.

### التهيئة والإعداد

أنشئ كائن `Watermarker` الذي سيحمّل ملف إكسل ويعمل كنقطة الدخول لجميع عمليات العلامة المائية.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## كيفية إضافة علامة مائية إلى رأس/تذييل جدول البيانات

فيما يلي العملية خطوة بخطوة التي توضح وظيفة **java add image watermark** وتظهر أيضًا كيف يمكنك **add logo to header**.

### الخطوة 1: تكوين خيارات التحميل

نبدأ بتعريف خيارات التحميل وإعادة إنشاء كائن `Watermarker`. يضمن ذلك أن يقرأ SDK دفتر العمل بشكل صحيح.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### الخطوة 2: إنشاء وتكوين علامة مائية صورة

أنشئ كائن `ImageWatermark` الذي يشير إلى الصورة التي تريد تضمينها (مثل شعار أو شارة “CONFIDENTIAL”). اضبط محاذاته وتوسعه بحيث يتناسب بشكل جيد داخل منطقة الرأس/التذييل.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### الخطوة 3: تكوين خيارات الرأس/التذييل

أخبر SDK أي ورقة عمل وأي جزء (رأس أو تذييل) يجب أن يتلقى العلامة المائية. هنا يمكنك **add logo to header** أو اختيار التذييل بدلاً من ذلك.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### الخطوة 4: إضافة العلامة المائية

الآن قم بإرفاق علامة مائية الصورة المُعدّة إلى موقع الرأس/التذييل المختار.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### الخطوة 5: حفظ وإغلاق

احفظ التغييرات في ملف جديد بحيث يبقى دفتر العمل الأصلي دون تعديل، ثم حرّر الموارد.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### نصائح استكشاف الأخطاء وإصلاحها
- تحقق مرة أخرى من مسار الصورة؛ مسار غير صحيح يسبب استثناء `FileNotFoundException`.  
- تبدأ مؤشرات الأوراق من 0؛ تأكد من أن الفهرس الذي تحدده موجود فعليًا.  
- إذا ظهرت العلامة المائية مشوهة، عدّل `setScaleFactor` أو غيّر `SizingType` إلى `StretchToParentDimensions`.

## لماذا نستخدم GroupDocs.Watermark Java SDK؟

- **دعم متعدد الصيغ** – يعمل مع Excel و Word و PowerPoint و PDFs والصور.  
- **تحرير بدون فقدان** – تبقى بيانات الخلايا الأصلية دون تعديل.  
- **تحسين الأداء** – مناسب لدفاتر العمل الكبيرة والمعالجة الدفعية.  

## حالات الاستخدام العملية

| السيناريو | كيف تساعد العلامة المائية |
|----------|---------------------------|
| **تقارير سرية** | إضافة صورة “CONFIDENTIAL” إلى كل صفحة مطبوعة. |
| **تعزيز العلامة التجارية** | وضع شعار شركتك في رأس الفواتير. |
| **تتبع الإصدارات** | تضمين شارة رقم الإصدار التي يتم تحديثها تلقائيًا. |
| **الامتثال القانوني** | وضع ختم الامتثال على جداول البيانات المنظمة. |

## اعتبارات الأداء

- **استخدام الذاكرة** – راقب مساحة heap في JVM عند معالجة جداول بيانات ضخمة جدًا.  
- **المعالجة الدفعية** – عالج الملفات على دفعات للحفاظ على استهلاك الذاكرة منخفضًا.  
- **إعادة استخدام الكائنات** – إعادة استخدام كائن `Watermarker` واحد لملفات متعددة يقلل من الحمل الزائد.  

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟**  
ج: نعم، بإنشاء مثيلات إضافية من `ImageWatermark` وتكوين كل منها قبل استدعاء `watermarker.add()`.

**س: كيف يمكنني إزالة علامة مائية موجودة من جدول بيانات؟**  
ج: حاليًا، يركز GroupDocs.Watermark على إضافة العلامات المائية. لإزالة واحدة، سيتعين عليك إعادة إنشاء دفتر العمل بدون العلامة المائية أو استخدام أداة تدعم استخراج العلامات المائية.

**س: ما صيغ الصور المدعومة للعلامات المائية؟**  
ج: الصيغ الشائعة مثل PNG و JPEG مدعومة، ولكن تحقق من [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/) للحصول على القائمة الكاملة للصيغ المتوافقة.

**س: هل يمكن وضع علامة مائية على جداول بيانات محمية بكلمة مرور؟**  
ج: نعم، طالما قمت بتوفير كلمة المرور اللازمة عند فتح الملف.

**س: كيف يمكنني تطبيق العلامات المائية على جميع أوراق العمل في مستند؟**  
ج: قم بالتكرار عبر كل فهرس ورقة عمل وكرر خطوات وضع العلامة المائية، مع ضبط `headerFooterOptions.setWorksheetIndex(i)` لكل تكرار.

## الخلاصة

أنت الآن تمتلك طريقة كاملة وجاهزة للإنتاج لإضافة **java add excel watermark** — وتحديدًا علامة مائية صورة — باستخدام **GroupDocs.Watermark Java SDK**. يضيف هذا النهج العلامة التجارية، إشعارات السرية، أو أي إشارة بصرية مباشرةً إلى رأس أو تذييل ملفات إكسل مع الحفاظ على البيانات الأساسية دون تعديل. لا تتردد في استكشاف أنواع أخرى من العلامات المائية (نص، شكل) ودمجها للحصول على حماية مستندات أكثر غنى.

---

**آخر تحديث:** 2026-03-20  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs