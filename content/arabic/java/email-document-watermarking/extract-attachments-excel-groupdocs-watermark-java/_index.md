---
date: '2026-04-04'
description: تعلم كيفية استخراج مرفقات Excel واستخراج الكائنات المضمنة باستخدام GroupDocs.Watermark
  للـ Java. قم بتبسيط إدارة مستنداتك بفعالية.
keywords:
- how to extract excel
- extract embedded objects
- java attachment extraction
title: كيفية استخراج مرفقات Excel باستخدام GroupDocs Watermark Java
type: docs
url: /ar/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# كيفية استخراج مرفقات Excel باستخدام GroupDocs.Watermark Java

استخراج الملفات المدمجة من مصنف Excel يمكن أن يكون عنق زجاجة حقيقي عندما تقوم بأتمتة خطوط البيانات أو بناء حلول الأرشفة. في هذا الدرس ستتعلم **كيفية استخراج مرفقات Excel** بسرعة وبشكل موثوق باستخدام مكتبة GroupDocs.Watermark للغة Java. سنستعرض إعداد البيئة، استعراض الكود، ونصائح عملية حتى تتمكن من دمج هذه القدرة في تطبيقاتك فورًا.

## الإجابات السريعة
- **ما المكتبة التي تتعامل مع مرفقات Excel؟** GroupDocs.Watermark للغة Java  
- **الطريقة الأساسية المستخدمة؟** `Watermarker` مع `SpreadsheetLoadOptions`  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج  
- **إصدار Java المدعوم؟** Java 8 أو أعلى  
- **هل يمكن استخراج صور المعاينة؟** نعم، عبر `getPreviewImageContent()`  

## ما معنى “كيفية استخراج Excel” في سياق أتمتة المستندات؟

عندما نقول *كيفية استخراج Excel* فإننا نشير إلى سحب أي كائنات مدمجة—مثل ملفات PDF أو صور أو جداول بيانات أخرى—مخزنة داخل ملف `.xlsx` برمجياً. يتيح ذلك عمليات لاحقة مثل تحليل البيانات، أرشفة الامتثال، أو توليد تقارير ديناميكية دون تدخل يدوي من المستخدم.

## لماذا نستخدم GroupDocs.Watermark لـ Java؟

توفر GroupDocs.Watermark واجهة برمجة تطبيقات عالية المستوى تُجرد التعامل منخفض المستوى مع OpenXML، لتمنحك:

- **نموذج كائن بسيط** للأوراق، المرفقات، والبيانات الوصفية  
- **استخراج معاينة مدمج** لفحص بصري سريع  
- **ترخيص قوي** يتدرج من النسخة التجريبية إلى المؤسسات  

## المتطلبات المسبقة

- **Java Development Kit (JDK) 8+** – مثبت ومضاف إلى `PATH` الخاص بك  
- **IDE** – IntelliJ IDEA، Eclipse، أو أي محرر تفضله  
- **Maven** – لإدارة الاعتمادات (بدلاً من ذلك يمكنك تحميل ملف JAR)  

### المكتبات والاعتمادات المطلوبة

ستحتاج إلى مكتبة GroupDocs.Watermark للغة Java. يستخدم هذا الدرس الإصدار 24.11، والذي يمكنك سحبه من Maven Central أو المستودع الرسمي لـ GroupDocs.

### رابط التحميل المباشر (محفوظ)

بدلاً من ذلك، حمّل أحدث نسخة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## إعداد GroupDocs.Watermark لـ Java

### إعداد Maven

أضف التكوين التالي إلى ملف `pom.xml` الخاص بك:

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

### خطوات الحصول على الترخيص

- **نسخة تجريبية مجانية:** ابدأ بنسخة تجريبية مجانية لاستكشاف قدرات المكتبة.  
- **ترخيص مؤقت:** احصل على ترخيص مؤقت لاستخدام مطور ممتد.  
- **شراء:** ارتقِ إلى ترخيص كامل للنشر في بيئات الإنتاج.

### التهيئة الأساسية والإعداد

```java
import com.groupdocs.watermark.Watermarker;

public class DocumentSetup {
    public static void main(String[] args) {
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        Watermarker watermarker = new Watermarker(filePath);
        
        // Your code to manipulate the document goes here
        
        watermarker.close();
    }
}
```

## كيفية استخراج مرفقات Excel باستخدام GroupDocs.Watermark

### تحميل وإعداد جدول البيانات

**نظرة عامة:** حمّل مصنفك باستخدام `SpreadsheetLoadOptions` للتحكم في استهلاك الذاكرة وسلوك التحميل.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.Watermarker;

public class ExtractAttachments {
    public static void extract() {
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### الوصول إلى محتوى جدول البيانات

**نظرة عامة:** احصل على نموذج المحتوى عالي المستوى الذي يمنحك الوصول إلى الأوراق والكائنات المدمجة.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### التكرار عبر أوراق العمل

**نظرة عامة:** قم بالتكرار عبر كل ورقة عمل ثم عبر كل مرفق لمعالجتها بشكل فردي.

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### استخراج تفاصيل المرفق

**نظرة عامة:** لكل مرفق، استخرج البيانات الوصفية المفيدة مثل النص البديل، الموقع، الحجم، والبايتات الفعلية للملف.

```java
import com.groupdocs.watermark.contents.SpreadsheetAttachment;

// Display alternative text and frame details of each attachment.
System.out.println("Alternative text: " + attachment.getAlternativeText());
System.out.println("Attachment frame x-coordinate: " + attachment.getX());
System.out.println("Attachment frame y-coordinate: " + attachment.getY());
System.out.println("Attachment frame width: " + attachment.getWidth());
System.out.println("Attachment frame height: " + attachment.getHeight());

// Check if a preview image is available and display its size.
int imageSize = (attachment.getPreviewImageContent() != null) ? attachment.getPreviewImageContent().length : 0;
System.out.println("Preview image size: " + imageSize);

if (attachment.isLink()) {
    System.out.println("Full path to the attached file: " + attachment.getSourceFullName());
} else {
    System.out.println("File type: " + attachment.getDocumentInfo().getFileType());
    System.out.println("Name of the source file: " + attachment.getSourceFullName());
    System.out.println("File size: " + attachment.getContent().length);
}
```

### إغلاق الموارد

**نظرة عامة:** احرص دائمًا على إغلاق كائن `Watermarker` لتحرير الموارد الأصلية وتجنب تسرب الذاكرة.

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## التطبيقات العملية (لماذا هذا مهم)

1. **تجميع البيانات تلقائيًا** – اسحب كل ملف PDF أو صورة مرفقة من دفعة تقارير لتشغيل تحليل موحد.  
2. **أرشفة الامتثال** – خزن الملفات المستخرجة جنبًا إلى جنب مع المصنف الأصلي لتلبية متطلبات التدقيق.  
3. **توليد تقارير ديناميكية** – أعد استخدام المخططات أو المستندات المدمجة كأصول منفصلة في محرك تقارير مخصص.  

## اعتبارات الأداء

- **إدارة الذاكرة:** أغلق `Watermarker` فور الانتهاء من معالجة كل ملف.  
- **معالجة دفعات:** عالج المصنفات على دفعات (مثلاً 10‑20 ملفًا لكل خيط) للحفاظ على استقرار استهلاك المعالج.  
- **ضبط خيارات التحميل:** استخدم `SpreadsheetLoadOptions` لتقليل عدد الصفوف/الأعمدة المحملة عندما تحتاج فقط إلى المرفقات.  

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| **`NullPointerException` on `getPreviewImageContent()`** | تحقق من أن المرفق يحتوي فعليًا على معاينة؛ ليس كل أنواع الملفات تُنشئ واحدة. |
| **Large Excel files cause OutOfMemoryError** | زيادة حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`) أو معالجة الملفات بشكل متسلسل مع استدعاء `close()` صريح بعد كل ملف. |
| **LicenseException in production** | تأكد من تطبيق ملف ترخيص كامل صالح عبر `License.setLicense("path/to/license.json")`. |

## الأسئلة المتكررة

**س: هل يمكن استخراج المرفقات من ملفات Excel المحمية بكلمة مرور؟**  
ج: نعم. قم بتحميل المصنف باستخدام `SpreadsheetLoadOptions` التي تتضمن كلمة المرور، ثم تابع كما هو موضح.

**س: هل يدعم API استخراج المخططات المدمجة كصور؟**  
ج: تُعامل المخططات ككائنات منفصلة؛ يمكنك الحصول على صورة المعاينة عبر `getPreviewImageContent()`.

**س: ما صيغ الملفات التي يمكن استخراجها كمرفقات؟**  
ج: أي نوع ملف مدمج في المصنف—PDF، DOCX، PNG، JPG، إلخ—يمكن الوصول إليه عبر API `SpreadsheetAttachment`.

**س: هل هناك طريقة لحفظ الملفات المستخرجة تلقائيًا؟**  
ج: يمكنك كتابة `attachment.getContent()` إلى `FileOutputStream` تختاره. يركز الدرس على طباعة البيانات الوصفية، لكن يمكن حفظ مصفوفة البايت نفسها.

**س: هل أحتاج إلى معالجة صيغ Excel عند استخراج المرفقات؟**  
ج: لا. المرفقات مستقلة عن صيغ الخلايا؛ يتم تخزينها ككائنات OLE داخل المصنف.

## الخاتمة

أنت الآن تملك دليلًا كاملاً وجاهزًا للإنتاج حول **كيفية استخراج مرفقات Excel** باستخدام GroupDocs.Watermark للغة Java. من خلال دمج هذه الخطوات في خطوط الأتمتة الخاصة بك، يمكنك تبسيط جمع البيانات، تحسين الامتثال، وإتاحة إمكانيات تقارير جديدة. استكشف ميزات أخرى للمكتبة—مثل إضافة العلامات المائية أو الحجب—لتعزيز سير عمل معالجة المستندات الخاص بك أكثر.

---

**آخر تحديث:** 2026-04-04  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

---