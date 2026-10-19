---
date: '2025-12-26'
description: تعلم كيفية استخراج المرفقات من ملفات Excel باستخدام GroupDocs.Watermark
  للغة Java. يغطي هذا الدليل استخراج مرفقات Excel في Java، وتكرار أوراق عمل Excel
  في Java، ومعالجة مرفقات Excel على دفعات.
keywords:
- extract attachments from excel
- groupdocs watermark java tutorial
- manage excel document attachments
title: كيفية استخراج المرفقات من Excel باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# كيفية استخراج المرفقات من Excel باستخدام GroupDocs.Watermark Java

في سير العمل القائم على البيانات اليوم، **كيفية استخراج المرفقات** من دفاتر Excel هي حاجة متكررة. سواء كنت تقوم بتجميع موارد المشروع، أرشفة مستندات الامتثال، أو بناء خطوط أنابيب تقارير آلية، فإن القدرة على استخراج الملفات المدمجة توفر الوقت وتزيل الأخطاء اليدوية. في هذا الدليل ستتعرف على كيفية إعداد GroupDocs.Watermark للـ Java، وستستعرض الشيفرة التي **java extract excel attachments**، وتفهم أفضل الممارسات لـ **batch process excel attachments**.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع مرفقات Excel؟** GroupDocs.Watermark for Java.
- **ما الطريقة التي تقوم بتحميل جدول البيانات؟** `new Watermarker(filePath, new SpreadsheetLoadOptions())`.
- **هل يمكنني تكرار أوراق العمل باستخدام Java؟** نعم – استخدم `content.getWorksheets()` وكرر عبر كل `SpreadsheetWorksheet`.
- **هل يلزم وجود ترخيص للإنتاج؟** يلزم وجود ترخيص كامل لـ GroupDocs.Watermark للاستخدام في الإنتاج.
- **هل سيعمل هذا على ملفات كبيرة؟** نعم، عندما تقوم بإغلاق Watermarker بسرعة وتستخدم خيارات التحميل المناسبة.

## ما هو “كيفية استخراج المرفقات” في سياق Excel؟
استخراج المرفقات يعني استرجاع أي كائنات—ملفات، صور، أو روابط—مضمنة داخل أوراق عمل دفتر Excel. تُخزن هذه الكائنات ككائنات `SpreadsheetAttachment` ويمكن الوصول إليها برمجياً، فحصها، وحفظها على القرص.

## لماذا نستخدم GroupDocs.Watermark لاستخراج مرفقات Excel؟
يقدم GroupDocs.Watermark واجهة برمجة تطبيقات عالية المستوى تُجرد التعامل منخفض المستوى مع Office Open XML، مما يتيح لك التركيز على منطق الأعمال بدلاً من تفاصيل تنسيق الملفات. كما يدعم **extract embedded objects excel**، ويوفر استخراج صور المعاينة، ويعمل بشكل ثابت عبر بيئات Java 8+.

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8 أو أعلى** – المكتبة تعمل على أي JDK حديث.
- **IDE** – IntelliJ IDEA، Eclipse، أو أي محرر تفضله.
- **Maven** – لإدارة التبعيات (أو يمكنك تحميل ملف JAR يدوياً).
- معرفة أساسية بـ Java وإلمام بإحداثيات Maven.

## إعداد GroupDocs.Watermark للـ Java

### إعداد Maven
Add the GroupDocs repository and dependency to your `pom.xml`:

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

### التحميل المباشر (بديل)
If you prefer not to use Maven, grab the latest JAR from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### خطوات الحصول على الترخيص
- **تجربة مجانية:** سجّل في بوابة GroupDocs للحصول على تجربة محدودة الوقت.
- **ترخيص مؤقت:** استخدم مفتاحًا مؤقتًا أثناء التطوير.
- **ترخيص كامل:** اشترِ ترخيص إنتاج لاستخدام غير محدود.

### التهيئة الأساسية والإعداد
Create a `Watermarker` instance that points to your Excel file:

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

## كيفية استخراج المرفقات من Excel – دليل خطوة بخطوة

### تحميل وإعداد جدول البيانات
First, load the workbook with `SpreadsheetLoadOptions` so the library knows it’s dealing with an Excel file:

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
Retrieve the high‑level content object that gives you access to worksheets and their attachments:

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### التكرار عبر أوراق العمل (java iterate excel worksheets java)
Loop over each worksheet and then over each attachment inside that sheet:

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### استخراج تفاصيل المرفق
For every `SpreadsheetAttachment` you can read its metadata, preview image, and raw file bytes:

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
Always release the `Watermarker` when you’re done to free memory:

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## التطبيقات العملية
- **تجميع البيانات الآلي:** استخراج كل ملف مرفق من مجموعة من جداول البيانات لتغذية بحيرة البيانات.
- **أرشفة المستندات:** حفظ المرفقات المستخرجة جنبًا إلى جنب مع دفتر العمل الأصلي لتدقيق الامتثال.
- **إنشاء تقارير ديناميكية:** استخدام الصور أو ملفات PDF المستخرجة كمدخلات لمحركات تقارير مخصصة.

## اعتبارات الأداء لمعالجة دفعات مرفقات Excel
- **إدارة الذاكرة:** استدعِ `watermarker.close()` بعد كل ملف؛ فكر في استخدام نمط try‑with‑resources.
- **التكرار على دفعات:** عالج الملفات في مجموعات قابلة للإدارة (مثلاً 20‑30 في كل مرة) لتجنب إغراق ذاكرة JVM.
- **ضبط خيارات التحميل:** عدّل `SpreadsheetLoadOptions` (مثلاً تعطيل الميزات غير الضرورية) لتسريع التحميل للدفاتر الكبيرة جدًا.

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|--------|-----|
| `NullPointerException` on `attachment.getPreviewImageContent()` | لا توجد صورة معاينة للمرفق. | أضف فحصًا للـ null (كما هو موضح في الشيفرة). |
| ارتفاع استهلاك الذاكرة عند معالجة العديد من الملفات الكبيرة | لم يتم إغلاق Watermarker بسرعة. | استخدم كتلة `try { … } finally { watermarker.close(); }`. |
| المرفقات غير مُدرجة | استخدام نسخة أقدم من GroupDocs تفتقر إلى دعم كامل للمرفقات. | قم بالترقية إلى أحدث إصدار 24.11 (أو أحدث). |

## الأسئلة المتكررة

**س: هل يمكنني استخراج المرفقات من ملفات Excel المحمية بكلمة مرور؟**  
ج: نعم. قدّم كلمة المرور عند إنشاء كائن `Watermarker` باستخدام التحميل المناسب.

**س: هل يعمل هذا مع ملفات `.xls` (BIFF) وكذلك `.xlsx`؟**  
ج: يدعم GroupDocs.Watermark كلًا من صيغ `.xls` القديمة و `.xlsx` الحديثة.

**س: كيف أحفظ المرفق المستخرج على القرص؟**  
ج: استرجع مصفوفة البايتات عبر `attachment.getContent()` واكتبها إلى `FileOutputStream`.

**س: هل هناك طريقة لاستخراج أنواع مرفقات محددة فقط (مثل PDFs)؟**  
ج: قم بالفلترة باستخدام `attachment.getDocumentInfo().getFileType()` قبل المعالجة.

**س: ما الترخيص المطلوب للاستخدام التجاري؟**  
ج: يلزم وجود ترخيص كامل لـ GroupDocs.Watermark للنشر في بيئات الإنتاج.

---

**آخر تحديث:** 2025-12-26  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للـ Java  
**المؤلف:** GroupDocs