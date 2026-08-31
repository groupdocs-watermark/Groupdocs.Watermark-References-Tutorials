---
date: '2026-07-15'
description: تعلم كيفية إضافة text watermark إلى ملفات Excel باستخدام Java و GroupDocs.Watermark.
  يوضح هذا الدليل كيفية إضافة watermark وتطبيقه على spreadsheet بكفاءة.
keywords:
- add text watermark excel
- how to add watermark
- apply watermark to spreadsheet
lastmod: '2026-07-15'
og_description: تعلم كيفية إضافة text watermark إلى ملفات Excel باستخدام Java و GroupDocs.Watermark.
  يوضح هذا الدليل كيفية إضافة watermark وتطبيقه على spreadsheet بكفاءة.
og_image_alt: 'Guide: Add text watermark to Excel using Java with GroupDocs.Watermark'
og_title: إضافة text watermark إلى Excel باستخدام Java – GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to add text watermark to Excel files using Java and GroupDocs.Watermark.
    This guide shows how to add watermark and apply watermark to spreadsheet efficiently.
  headline: Add Text Watermark to Excel Using Java – GroupDocs.Watermark
  type: TechArticle
- description: Learn how to add text watermark to Excel files using Java and GroupDocs.Watermark.
    This guide shows how to add watermark and apply watermark to spreadsheet efficiently.
  name: Add Text Watermark to Excel Using Java – GroupDocs.Watermark
  steps:
  - name: Load the Excel Document
    text: '**Direct answer:** Initialize the `Watermarker` class with the path to
      your Excel file and appropriate load options – this prepares the document for
      watermark operations. xml <repositories> <repository> <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name> <url>https://releases.groupdo'
  - name: Create and Configure the Text Watermark
    text: '**Direct answer:** Instantiate a `TextWatermark`, set its text, font, size,
      color, and alignment, then attach it to a `SpreadsheetWatermarkOptions` object.
      java import com.groupdocs.watermark.Watermarker; import com.groupdocs.watermark.contents.SpreadsheetLoadOptions;
      // Initialize load options Spre'
  - name: Apply the Watermark to Desired Sheets
    text: '**Direct answer:** Use the `add` method on the `Watermarker` instance,
      passing the options and optionally specifying a sheet index to target a single
      worksheet. java import com.groupdocs.watermark.options.HorizontalAlignment;
      import com.groupdocs.watermark.options.VerticalAlignment; import com.group'
  - name: Save the Watermarked Workbook
    text: '**Direct answer:** Call `save` on the `Watermarker`, providing the output
      path and format; the library writes the watermarked file while preserving original
      data. java // Save the watermarked document watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_watermarked.xlsx");
      // Release resources waterm'
  type: HowTo
- questions:
  - answer: It inserts customizable text watermarks into Excel files without altering
      original content.
    question: What does the library do?
  - answer: GroupDocs.Watermark for Java 24.11 or later.
    question: Which version is required?
  - answer: A free trial works for evaluation; a permanent license removes all limitations.
    question: Do I need a license?
  - answer: Yes – you can apply watermarks to specific worksheets.
    question: Can I target a single sheet?
  - answer: Yes, it processes multi‑hundred‑page workbooks using streaming, keeping
      memory usage low.
    question: Is it fast on large files?
  type: FAQPage
tags:
- add text watermark excel
- GroupDocs.Watermark
- Java spreadsheet watermark
- document security
- Excel watermarking
title: إضافة text watermark إلى Excel باستخدام Java – GroupDocs.Watermark
type: docs
url: /ar/java/spreadsheet-document-watermarking/java-add-customize-text-watermarks-excel/
weight: 1
---

# إضافة علامة مائية نصية إلى Excel باستخدام Java – GroupDocs.Watermark

## إجابات سريعة
- **ما الذي تفعله المكتبة؟** تُدرج علامات مائية نصية قابلة للتخصيص في ملفات Excel دون تعديل المحتوى الأصلي.  
- **ما الإصدار المطلوب؟** GroupDocs.Watermark for Java 24.11 أو أحدث.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للتقييم؛ الترخيص الدائم يزيل جميع القيود.  
- **هل يمكنني استهداف ورقة واحدة؟** نعم – يمكنك تطبيق العلامات المائية على أوراق عمل محددة.  
- **هل هو سريع على الملفات الكبيرة؟** نعم، يعالج دفاتر عمل مئات الصفحات باستخدام البث، مما يحافظ على انخفاض استهلاك الذاكرة.

## ما هو “add text watermark excel”؟
**Add text watermark excel** يشير إلى عملية تضمين طبقة نصية مرئية في دفتر عمل Excel للدلالة على السرية أو الملكية أو العلامة التجارية. تُخزن هذه الطبقة كجزء من الملف وتظل مرئية عند فتح الجدول في أي عارض متوافق.

## لماذا تستخدم GroupDocs.Watermark for Java؟
يدعم GroupDocs.Watermark **أكثر من 30 تنسيقًا للإدخال والإخراج** ويمكنه معالجة ملفات Excel حتى **200 ميغابايت** دون تحميل دفتر العمل بالكامل إلى الذاكرة، مما يوفر أداءً بأقل من ثانية على عتاد الخادم المعتاد. API الخاص به آمن تمامًا من حيث الخيوط، مما يجعله مثاليًا لأنابيب المؤسسات ذات الإنتاجية العالية.

## المتطلبات المسبقة
1. **المكتبات والاعتمادات**  
   - GroupDocs.Watermark for Java (الإصدار 24.11 أو أحدث)
2. **إعداد البيئة**  
   - مجموعة تطوير جافا (JDK) 8 أو أحدث مثبتة
3. **متطلبات المعرفة**  
   - مهارات برمجة Java الأساسية  
   - الإلمام بـ Maven لإدارة الاعتمادات  

## كيفية إضافة علامة مائية نصية إلى Excel – دليل خطوة بخطوة
لدمج علامة مائية نصية في دفتر عمل Excel، تقوم أولاً بتحميل الملف باستخدام Watermarker، ثم تحديد مظهر العلامة المائية، وأخيرًا تطبيقها على الأوراق المطلوبة قبل الحفظ. العملية بسيطة ويمكن تنفيذها ببضع أسطر من كود Java، كما هو موضح في المقاطع أدناه.

### الخطوة 1: تحميل مستند Excel
**الإجابة المباشرة:** تهيئة فئة `Watermarker` بمسار ملف Excel الخاص بك وخيارات التحميل المناسبة – هذا يجهز المستند لعمليات العلامة المائية.  

``` 
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
```  

### الخطوة 2: إنشاء وتكوين العلامة المائية النصية
**الإجابة المباشرة:** إنشاء كائن `TextWatermark`، تعيين نصه، الخط، الحجم، اللون، والمحاذاة، ثم ربطه بكائن `SpreadsheetWatermarkOptions`.  

``` 
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetLoadOptions;

// Initialize load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create a watermarker instance for the Excel file
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```
```  

### الخطوة 3: تطبيق العلامة المائية على الأوراق المطلوبة
**الإجابة المباشرة:** استخدم طريقة `add` على كائن `Watermarker`، مع تمرير الخيارات وإمكانية تحديد فهرس ورقة لاستهداف ورقة عمل واحدة.  

``` 
```java
import com.groupdocs.watermark.options.HorizontalAlignment;
import com.groupdocs.watermark.options.VerticalAlignment;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a text watermark
TextWatermark watermark = new TextWatermark("Confidential", new Font("Segoe UI", 19));

// Set size, alignment and color of the watermark
watermark.setSizingType(TextWatermark.SIZING_TYPE.FIT_TO_PAGE);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
```
```  

### الخطوة 4: حفظ دفتر العمل المموج
**الإجابة المباشرة:** استدعِ `save` على كائن `Watermarker`، مع توفير مسار الإخراج والصيغة؛ تقوم المكتبة بكتابة الملف المموج مع الحفاظ على البيانات الأصلية.  

``` 
```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_watermarked.xlsx");

// Release resources
watermarker.close();
```
```  

## تطبيق تأثيرات نصية على العلامات المائية في جداول البيانات
تحسين الرؤية باستخدام أنماط الخط، الشفافية، والدوران.

### تخصيص تنسيق الخط
**مرساة التعريف:** `SpreadsheetTextEffects` هي فئة مساعدة تُعرّف سمك الخط، نمط الشرط، واللون للعلامات المائية النصية في جداول البيانات.  

``` 
```java
import com.groupdocs.watermark.options.SpreadsheetLineFormat;
import com.groupdocs.watermark.options.SpreadsheetDashStyle;
import com.groupdocs.watermark.options.SpreadsheetLineStyle;

// Set up text effects for the watermark
SpreadsheetTextEffects effects = new SpreadsheetTextEffects();
effects.getLineFormat().setEnabled(true);
effects.getLineFormat().setColor(Color.getRed());
effects.getLineFormat().setDashStyle(SpreadsheetDashStyle.DashDotDot);
effects.getLineFormat().setLineStyle(SpreadsheetLineStyle.Triple);
effects.getLineFormat().setWeight(1);
```
```  

### تطبيق التأثيرات على خيارات العلامة المائية
دمج `SpreadsheetTextEffects` في `SpreadsheetWatermarkOptions` للتحكم في كيفية عرض العلامة المائية على كل صفحة.

``` 
```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkShapeOptions;

// Attach effects to the watermark shape options
SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setEffects(effects);
```
```  

## التطبيقات العملية
جداول البيانات المموجة نصيًا مفيدة في العديد من السيناريوهات:
1. **تقارير سرية** – وضع علامة “سري” على القوائم المالية لمنع التسريب.  
2. **العلامة التجارية** – وضع شعار أو شعار شركتك فوق جداول البيانات الموجهة للعملاء.  
3. **الوثائق القانونية** – وضع تسمية واضحة للعقود والاتفاقيات لتأكيد الأصالة.  

## اعتبارات الأداء
عند التعامل مع دفاتر عمل Excel الكبيرة، اتبع هذه الممارسات الأفضل:
- **البث بدلاً من التحميل:** يعالج GroupDocs.Watermark البيانات بطريقة بث، متجنبًا تخصيص الذاكرة للوثيقة بالكامل.  
- **إغلاق الموارد بسرعة:** استخدم try‑with‑resources أو استدعاءات `close()` الصريحة لتحرير مقابض الملفات.  
- **ضبط JVM:** زيادة حجم الكومة (`-Xmx2g`) للملفات التي تتجاوز 100 ميغابايت، لكن راقب توقفات جمع القمامة.  

## الخلاصة
أنت الآن تعرف كيفية **إضافة علامة مائية نصية إلى ملفات Excel** باستخدام GroupDocs.Watermark for Java، من الإدراج الأساسي إلى التنسيق المتقدم. جرّب خطوطًا وألوانًا وزوايا دوران مختلفة لتتناسب مع هوية شركتك، ودمج سير العمل في أنابيب معالجة المستندات الأكبر لحماية تلقائية.

## الأسئلة المتكررة

**س:** ما هو الحد الأقصى لحجم الملف المدعوم من قبل GroupDocs.Watermark؟  
**ج:** يمكن للمكتبة معالجة دفاتر عمل Excel حتى **200 ميغابايت** دون تدهور الأداء، بفضل بنية البث الخاصة بها.

**س:** هل يمكنني تخصيص أنماط الخطوط وأحجامها؟  
**ج:** نعم – تسمح فئة `Font` بتعيين العائلة، الحجم، النمط (غامق، مائل)، واللون لأي علامة مائية نصية.

**س:** هل من الممكن إضافة علامات مائية إلى أوراق معينة فقط؟  
**ج:** بالتأكيد. استخدم نسخة طريقة `add` التي تقبل فهرس أو اسم الورقة لاستهداف أوراق العمل الفردية.

**س:** كيف يجب أن أتعامل مع الأخطاء أثناء تطبيق العلامة المائية؟  
**ج:** غلف الكود بكتلة try‑catch والتقط الاستثناءات `IOException` و `WatermarkException` لإدارة مشكلات الوصول إلى الملفات وأخطاء API بشكل سلس.

**س:** هل يمكن إزالة العلامات المائية لاحقًا إذا لزم الأمر؟  
**ج:** نعم – يوفر GroupDocs.Watermark API `remove` الذي يمكنه حذف العلامات المائية المضافة مسبقًا مع الحفاظ على المحتوى الأصلي.

**آخر تحديث:** 2026-07-15  
**تم الاختبار مع:** GroupDocs.Watermark for Java 24.11  
**المؤلف:** GroupDocs  

## الموارد
- [إصدارات GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [التوثيق](https://docs.groupdocs.com/watermark/java/releases)

## دروس ذات صلة
- [إضافة علامة مائية صورة إلى جدول Excel باستخدام GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [كيفية إضافة مرفقات إلى Excel باستخدام GroupDocs.Watermark Java لتطبيق العلامات المائية على جداول البيانات](/watermark/java/spreadsheet-document-watermarking/groupdocs-watermark-java-add-attachments-excel/)
- [دروس وضع علامات مائية على جداول Excel لـ GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/)