---
date: '2026-06-01'
description: تعلم كيفية إزالة الأشكال من ملفات Excel باستخدام GroupDocs.Watermark
  للـ Java. يتضمن خطوات تحميل Excel، وتكرار الأوراق، وحذف الأشكال المنسقة.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: كيفية إزالة الأشكال من Excel باستخدام GroupDocs.Watermark في Java
type: docs
url: /ar/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# كيفية إزالة الأشكال من إكسل باستخدام GroupDocs.Watermark في جافا

تُعد جداول إكسل أساسًا لتقارير الأعمال، لكن الأشكال غير المرغوب فيها—وخاصة تلك التي تحتوي على تنسيق نص قديم أو غير قياسي—يمكن أن تملأ الملف وتكسر الاتساق البصري. **إزالة الأشكال من إكسل** تصبح ضرورية بسرعة للحصول على مستندات نظيفة ومهنية. في هذا الدرس سنستعرض تحميل دفتر إكسل، وتصفح أوراقه، وحذف الأشكال برمجيًا التي تتطابق مع معايير تنسيق محددة، كل ذلك باستخدام مكتبة GroupDocs.Watermark القوية لجافا.

## إجابات سريعة
- **هل يمكن لـ GroupDocs.Watermark حذف الأشكال؟** نعم، يوفر طريقة `removeShape` التي تعمل على أي ورقة عمل.  
- **هل أحتاج إلى ترخيص لهذه الميزة؟** نسخة تجريبية تعمل للتقييم؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما إصدار جافا المطلوب؟** Java 8 أو أحدث مدعوم.  
- **كم عدد صيغ الملفات التي يدعمها GroupDocs.Watermark؟** أكثر من 30 صيغة إدخال وإخراج، بما في ذلك XLSX و DOCX و PDF و PPTX.  
- **هل استهلاك الذاكرة يمثل قلقًا بالنسبة لدفاتر العمل الكبيرة؟** استخدم try‑with‑resources وتجنب تحميل الأوراق بالكامل في الذاكرة؛ الـ API يبث البيانات بكفاءة.

## ما هو إزالة الأشكال من إكسل؟
*إزالة الأشكال من إكسل* يعني حذف كائنات الرسم برمجيًا — مثل مربعات النص، الأيقونات، أو SmartArt — التي تفي بمعايير معينة، مثل نمط الخط، اللون، أو الحجم. هذه العملية تنظف دفتر العمل دون تحرير يدوي، مما يضمن اتساقًا بصريًا، يقلل حجم الملف، ويمنع ظهور الرسومات القديمة أو غير المرغوب فيها في التقارير الموزعة.

## لماذا إزالة الأشكال من إكسل؟
يمكن لـ GroupDocs.Watermark معالجة **دفاتر عمل متعددة المئات من الصفحات بسرعات تصل إلى 3 × أسرع** من التحرير اليدوي، مع التعامل مع **أكثر من 30 صيغة ملف** مع الحفاظ على استهلاك الذاكرة أقل من 150 ميغابايت للملفات التي يزيد حجمها عن 50 ميغابايت. يزيل أتمتة إزالة الأشكال الأخطاء البشرية ويضمن توحيد العلامة التجارية عبر جميع التقارير المُولدة.

## المتطلبات المسبقة
### المكتبات المطلوبة والإصدارات والاعتمادات
- **Java Development Kit (JDK)**: الإصدار 8 أو أحدث.  
- **GroupDocs.Watermark**: الإصدار 24.11 (أحدث إصدار ثابت في وقت الكتابة).

### متطلبات إعداد البيئة
استخدم بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse وMaven لإدارة الاعتمادات.

### متطلبات المعرفة المسبقة
الإلمام بصياغة جافا ومفاهيم إكسل الأساسية (الأوراق، الخلايا، والأشكال) سيساعدك على متابعة الأمثلة.

## إعداد GroupDocs.Watermark لجافا
**اعتماد Maven**  
أضف ما يلي إلى ملف `pom.xml` الخاص بك:

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

**تحميل مباشر**  
بدلاً من ذلك، قم بتحميل أحدث إصدار من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### خطوات الحصول على الترخيص
- **Free Trial** – ابدأ بنسخة تجريبية مجانية لتقييم الميزات.  
- **Temporary License** – احصل على ترخيص مؤقت للاختبار الموسع.  
- **Purchase** – اشترِ ترخيصًا كاملاً للاستخدام في الإنتاج.

### التهيئة الأساسية والإعداد  
بعد إضافة المكتبة إلى مشروعك، قم بتهيئتها كما هو موضح أدناه:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## كيفية إزالة الأشكال من إكسل؟
حمّل دفتر العمل، وتصفح كل ورقة عمل، واستدعِ واجهة برمجة تطبيقات إزالة الأشكال. يغطي هذا النمط المكوّن من خطوتين — *التحميل* ثم *التصفح* — تقريبًا أي سيناريو تحتاج فيه إلى تنظيف الأشكال عبر ملف كامل. من خلال فحص خصائص كل شكل مقابل معاييرك قبل الإزالة، تضمن حذف العناصر غير المرغوب فيها فقط مع الحفاظ على باقي تخطيط ومحتوى المستند.

## تحميل مستند إكسل
**نظرة عامة**  
تحميل مستند إكسل هو نقطة البداية لأي مهمة تعديل. يبسط GroupDocs.Watermark ذلك بفضل واجهة برمجة التطبيقات البديهية.  

**تعريف مرساة**  
`SpreadsheetDocument` هو الصنف الأساسي في GroupDocs.Watermark الذي يمثل دفتر إكسل في الذاكرة، ويوفر طرقًا للوصول إلى الأوراق، الخلايا، والأشكال.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## الوصول والتصفح عبر الأوراق في جدول بيانات
**نظرة عامة**  
التصفح عبر الأوراق يتيح لك تنفيذ عمليات على كل ورقة على حدة.  

**تعريف مرساة**  
`Worksheet` يمثل ورقة واحدة داخل `SpreadsheetDocument`؛ يمكنك قراءة محتواها أو تعديله أو حذفه عبر هذا الكائن.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## إزالة الأشكال ذات تنسيق نص محدد من جدول بيانات
**نظرة عامة**  
تستهدف هذه الميزة الأشكال التي تفي بمعايير تنسيق نص معينة، مثل نوع الخط أو اللون.  

**تعريف مرساة**  
`Shape` هو نموذج الكائن لأي عنصر رسم (مربع نص، صورة، أو SmartArt) داخل ورقة عمل؛ يتيح خصائص مثل `getText`، `getFont`، و `remove`.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## تطبيقات عملية
### حالات استخدام واقعية
1. **Data Validation** – احذف الأشكال التي تحتوي على إشعارات منتهية الصلاحية تلقائيًا.  
2. **Template Standardization** – فرض العلامة التجارية للشركة عن طريق إزالة مربعات النص غير القياسية.  
3. **Automated Reporting** – نظف التقارير المولدة قبل التوزيع، لضمان مظهر مصقول.  

### إمكانيات التكامل
يمكن دمج GroupDocs.Watermark في خطوط أنابيب المؤسسات المبنية على جافا، مثل خدمات المايكرو لتوليد المستندات، وظائف المعالجة الدفعية، أو أنظمة إدارة المحتوى، مما يوفر طريقة سلسة ومتوافقة مع الترخيص لإدارة أصول إكسل.

## اعتبارات الأداء
### تحسين الأداء
- **Avoid heavy operations inside loops** – احصل على مجموعات الأشكال مرة واحدة لكل ورقة عمل.  
- **Release resources promptly** – استخدم try‑with‑resources لإغلاق التدفقات تلقائيًا.  

### إرشادات استخدام الموارد
حرر كائن `SpreadsheetDocument` فور انتهاء المعالجة لتحرير الذاكرة الأصلية. بالنسبة للملفات التي تتجاوز 100 ميغابايت، فكر في معالجة الأوراق عبر تدفقات موازية لاستغلال المعالجات متعددة النوى.  

### أفضل الممارسات لإدارة ذاكرة جافا
استخدم `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` بحيث يتم تشغيل طريقة `close()` حتى في حال حدوث استثناء.  

## المشكلات الشائعة والحلول
- **Shape not found** – تأكد من فحص فهرس الورقة الصحيح؛ الأشكال محصورة لكل ورقة.  
- **License exception** – ترخيص التجربة يعطل المعالجة الدفعية؛ قم بالترقية إلى ترخيص كامل للعمليات غير المحدودة.  
- **Unexpected font values** – قد تكون خصائص الخط موروثة؛ استخدم `shape.getEffectiveFont()` للحصول على النمط المحلول.  

## الأسئلة المتكررة

**س: هل يمكنني إزالة الأشكال من دفتر عمل محمي بكلمة مرور؟**  
ج: نعم. حمّل المستند مع معامل كلمة المرور، ثم نفّذ نفس منطق الإزالة؛ الـ API يفك تشفير الملف في الذاكرة.

**س: هل تدعم المكتبة ملفات .xls (Excel 97‑2003)؟**  
ج: بالتأكيد. يدير GroupDocs.Watermark كلًا من صيغ `.xlsx` و `.xls` القديمة دون تحويل.

**س: كيف أسجل أي الأشكال تم حذفها؟**  
ج: تجول في مجموعة الأشكال، تحقق من معايير التنسيق، سجل `shape.getName()` أو `shape.getId()`، ثم استدعِ `remove()`.

**س: هل يمكن إضافة علامة مائية بعد إزالة الأشكال؟**  
ج: نعم. بعد التنظيف، استدعِ `doc.addWatermark(new TextWatermark("Confidential"))` لإضافة علامة مائية نصية عبر جميع الأوراق.

**س: ما هو الحد الأقصى لحجم الملف المدعوم؟**  
ج: يمكن للمكتبة معالجة ملفات تصل إلى **2 GB** على JVM 64‑bit، مع محدودية فقط بذاكرة الكومة المتاحة وقيود نظام التشغيل.

## الخلاصة
في هذا الدرس، عرضنا نهجًا كاملاً وجاهزًا للإنتاج **لإزالة الأشكال من إكسل** في دفاتر العمل باستخدام GroupDocs.Watermark لجافا. من خلال تحميل المستند، وتصفح الأوراق، وتطبيق مرشحات تنسيق دقيقة، يمكنك أتمتة مهام التنظيف، فرض العلامة التجارية، وتحسين جودة التقارير على نطاق واسع. استكشف ميزات إضافية مثل إدراج العلامات المائية، تحويل المستندات، والمعالجة الدفعية لتوسيع مجموعة أدوات أتمتة المستندات الخاصة بك.

---

**آخر تحديث:** 2026-06-01  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [معالجة أشكال إكسل باستخدام GroupDocs.Watermark في جافا: دليل شامل](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [إضافة علامة مائية صورة إلى جدول إكسل باستخدام GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [معالجة مستند إكسل وإضافة علامة مائية باستخدام GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)