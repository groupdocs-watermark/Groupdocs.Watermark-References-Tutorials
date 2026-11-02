---
date: '2026-06-06'
description: تعلم كيفية إضافة مرفق إلى Excel باستخدام GroupDocs.Watermark للغة Java.
  إعداد خطوة بخطوة، استعراض الكود، وأفضل الممارسات.
keywords:
- add attachment to excel
- how to add attachment excel
- embed file in excel worksheet
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to add attachment to excel with GroupDocs.Watermark for Java.
    Step‑by‑step setup, code walkthrough, and best practices.
  headline: How to Add Attachments to Excel Using GroupDocs.Watermark Java
  type: TechArticle
- questions:
  - answer: Yes. Call `addAttachment` repeatedly with different file names and byte
      arrays; each call creates a separate entry in the worksheet’s attachment collection.
    question: Can I attach multiple files to the same worksheet?
  - answer: Absolutely. Excel shows attached files under the “Insert → Object → Create
      from File → Display as icon” pane, and users can double‑click the icon to open
      the embedded document.
    question: Will the attachment be visible in Excel’s UI?
  - answer: GroupDocs.Watermark can open password‑protected workbooks when you supply
      the password via `SpreadsheetLoadOptions.setPassword("yourPassword")`.
    question: Does this work with password‑protected Excel files?
  - answer: The library supports attachments up to 2 GB, limited only by the underlying
      ZIP package format and available disk space.
    question: Is there a size limit for attachments?
  - answer: Retrieve the worksheet’s attachment collection and call `removeAttachment("AttachmentName.ext")`
      before saving the workbook again.
    question: How do I remove an attachment later?
  type: FAQPage
title: كيفية إضافة مرفقات إلى Excel باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/spreadsheet-document-watermarking/groupdocs-watermark-java-add-attachments-excel/
weight: 1
---

# كيفية إضافة مرفقات إلى Excel باستخدام GroupDocs.Watermark Java

## المقدمة
في بيئة الأعمال سريعة الحركة اليوم، **add attachment to excel** هي طريقة قوية للحفاظ على الوثائق ذات الصلة معًا دون إغراق نظام الملفات الخاص بك. سواء كنت بحاجة إلى تجميع عقد PDF مع نموذج مالي أو إرفاق صورة بمتتبع المشروع، فإن تضمين الملفات مباشرة داخل ورقة عمل Excel يبسط التعاون ويحسن سلامة البيانات. يوضح لك هذا البرنامج التعليمي، خطوة بخطوة، كيفية استخدام GroupDocs.Watermark for Java لإضافة مرفقات إلى أوراق Excel بسرعة وموثوقية.

## الإجابات السريعة
- **ما المكتبة التي تضيف مرفقات إلى Excel؟** GroupDocs.Watermark for Java.  
- **كم عدد أسطر الكود المطلوبة؟** سطران فقط بعد تحميل دفتر العمل.  
- **هل يمكنني إرفاق أي نوع ملف؟** نعم – ملفات PDF، صور، مستندات Word، وأكثر (أكثر من 50 تنسيقًا).  
- **هل أحتاج إلى ترخيص للاختبار؟** ترخيص مؤقت مجاني يكفي للتقييم.  
- **هل استهلاك الذاكرة مصدر قلق؟** الـ API يبث البيانات، لذا حتى دفاتر العمل التي تحتوي على 500 صفحة تبقى تحت 200 ميغابايت من الذاكرة.

## ما هو add attachment to excel؟
**Add attachment to excel** يشير إلى تضمين ملف خارجي داخل ورقة عمل Excel بحيث يمكن للمستخدمين فتح الملف مباشرة من الجدول. هذه الميزة تحافظ على الوثائق الداعمة مع البيانات التي تصفها، مما يلغي الحاجة إلى نقل ملفات منفصلة.

## لماذا تستخدم GroupDocs.Watermark for Java لتضمين الملفات؟
GroupDocs.Watermark يدعم **30+ تنسيقًا للإدخال والإخراج**، يعالج جداول بيانات مئات الصفحات دون تحميل الملف بالكامل في الذاكرة، ويوفر API بسيط يتطلب عددًا قليلًا من استدعاءات الطرق. استخدام هذه المكتبة يقلل من التعامل اليدوي مع ملفات ZIP بنسبة تصل إلى 80 % ويقضي على خطر الروابط المكسورة عند نقل الملفات.

## المتطلبات المسبقة
للتبع هذا الدرس، ستحتاج إلى:

- **مجموعة تطوير جافا (JDK) 8+** – الحد الأدنى من الإصدار المدعوم من قبل GroupDocs.Watermark.  
- **GroupDocs.Watermark for Java 24.11** – أحدث إصدار ثابت في وقت كتابة هذا الدليل.  
- **IDE** – IntelliJ IDEA أو Eclipse أو أي بيئة متوافقة مع Maven.

### المكتبات والاعتمادات المطلوبة
دمج GroupDocs.Watermark في مشروعك باستخدام Maven أو عن طريق تنزيل ملفات JAR مباشرة. إليك كيفية إعدادها مع Maven:

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

**التنزيل المباشر**  
بدلاً من ذلك، قم بتنزيل أحدث نسخة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
ابدأ بتجربة مجانية عن طريق تنزيل ترخيص مؤقت من [here](https://purchase.groupdocs.com/temporary-license/) لاستكشاف جميع الميزات دون قيود. للاستخدام الإنتاجي، اشترِ ترخيصًا دائمًا.

## إعداد GroupDocs.Watermark for Java
فئة `Watermarker` هي نقطة الدخول لجميع عمليات المستندات في GroupDocs.Watermark. بعد إضافة اعتماد Maven، تقوم بإنشاء كائن `Watermarker` مع مسار ملف Excel وخيارات التحميل الاختيارية.

```java
import com.groupdocs.watermark.Watermarker;

public class SetupGroupDocs {
    public static void main(String[] args) throws Exception {
        // Initialize watermarker with an input file
        Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
        
        // Your code to manipulate the document goes here
        
        // Close the watermarker when done
        watermarker.close();
    }
}
```
هذه التهيئة تُعد المكتبة لقراءة وتعديل وحفظ محتوى جدول البيانات.

## دليل التنفيذ
في هذا القسم نُفصِّل كل خطوة مطلوبة لـ **add attachment to excel** أوراق العمل.

### تحميل جدول بيانات Excel
**كيف يتم تحميل دفتر عمل Excel؟**  
أنشئ مثالًا من `Watermarker`، مع تمرير مسار ملف Excel وكائن `SpreadsheetLoadOptions` الذي يُخبر الـ API بمعالجة الملف كجدول بيانات. تفتح هذه الخطوة دفتر العمل في وضع القراءة/الكتابة مع الحفاظ على استهلاك منخفض للذاكرة.

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class LoadSpreadsheet {
    public static void run() throws Exception {
        // Create new SpreadsheetLoadOptions instance
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Initialize Watermarker with the Excel file path and load options
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```

### قراءة ملف إلى بايتات
**ما هي أفضل طريقة لتحضير ملف للمرفق؟**  
اقرأ الملف الخارجي (PDF، صورة، DOCX، إلخ) إلى مصفوفة بايتات باستخدام طريقة Java `Files.readAllBytes`. يمكن تمرير مصفوفة البايتات الناتجة مباشرة إلى API المرفقات، مما يضمن الحفاظ على تنسيق الملف الأصلي.

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class ReadFileToBytes {
    public static byte[] readFileToByteArray(String filePath) throws Exception {
        File file = new File(filePath);
        byte[] fileContentBytes = new byte[(int) file.length()];

        try (InputStream inputStream = new FileInputStream(file)) {
            inputStream.read(fileContentBytes);
        }
        
        return fileContentBytes;
    }
}
```

### إضافة مرفق إلى ورقة عمل جدول البيانات
**كيف تقوم بتضمين ملف داخل ورقة عمل محددة؟**  
استدعِ `watermarker.getWorksheets().get(0).addAttachment("AttachmentName.ext", fileBytes)`. المعامل الأول هو اسم العرض الذي يظهر في لوحة “المرفقات” في Excel، والمعامل الثاني هو مصفوفة البايتات من الخطوة السابقة. يصبح المرفق جزءًا من حزمة الورقة الداخلية.

`addAttachment` يدمج الملف المحدد في الورقة كمرفق.

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

public class AddAttachmentToWorksheet {
    public static void run(Watermarker watermarker, byte[] attachmentBytes, String fileName, byte[] previewImageBytes) throws Exception {
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        SpreadsheetWorksheet worksheet = content.getWorksheets().get_Item(0);

        worksheet.getAttachments().addAttachment(
            attachmentBytes,
            fileName,
            previewImageBytes,
            50, 100, 200, 400
        );
    }
}
```

### حفظ التغييرات إلى جدول البيانات
**كيف يتم حفظ دفتر العمل المعدل؟**  
استدعِ `watermarker.save("output.xlsx", SaveFormat.Xlsx)`. الـ API يكتب الحزمة المحدثة، بما فيها المرفق الجديد، إلى المسار المحدد. تُحفظ جميع التغييرات في عملية واحدة، مما يبقي العملية سريعة وذرية.

`save` يكتب دفتر العمل المعدل، بما في ذلك المرفقات، إلى الملف المحدد.

```java
public class SaveSpreadsheet {
    public static void run(Watermarker watermarker, String outputPath) throws Exception {
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```

## التطبيقات العملية
تضمين الملفات داخل دفاتر Excel يحل العديد من المشكلات الواقعية:

- **الوثائق القانونية:** احفظ العقود الموقعة جنبًا إلى جنب مع الجداول المالية، مما يضمن قدرة المدققين على استرجاع الاتفاقية الأصلية فورًا.  
- **التقارير والعروض:** أرفق ملفات PDF أو عروض شرائح داعمة إلى تقرير قائم على البيانات، لتوفير رؤية شاملة لجميع المواد لأصحاب المصلحة.  
- **المحتوى التعليمي:** يمكن للمعلمين تجميع أوراق العمل مع ملفات PDF مرجعية، مما يبسط توزيع المواد على الطلاب.

## اعتبارات الأداء
تحسين الأداء عند **add attachment to excel** سهل:

- **إدارة الذاكرة:** دائمًا استدعِ `watermarker.close()` (أو استخدم كتلة try‑with‑resources) لتحرير مقابض الملفات بسرعة.  
- **المعالجة الدُفعية:** عند التعامل مع عشرات دفاتر العمل، عالجها على دفعات من 10 إلى 20 لتجنب استهلاك الذاكرة الزائد.  
- **المرفقات الكبيرة:** للملفات التي يزيد حجمها عن 50 ميغابايت، فكر في بث مصفوفة البايتات على أجزاء للحفاظ على بصمة الذاكرة للـ JVM منخفضة.

## الأسئلة المتكررة

**س: هل يمكنني إرفاق ملفات متعددة إلى نفس ورقة العمل؟**  
ج: نعم. استدعِ `addAttachment` عدة مرات بأسماء ملفات ومصفوفات بايت مختلفة؛ كل استدعاء يُنشئ إدخالًا منفصلًا في مجموعة مرفقات الورقة.

**س: هل سيكون المرفق مرئيًا في واجهة Excel؟**  
ج: بالتأكيد. Excel يعرض الملفات المرفقة تحت لوحة “Insert → Object → Create from File → Display as icon”، ويمكن للمستخدمين النقر مزدوجًا على الأيقونة لفتح المستند المدمج.

**س: هل يعمل هذا مع ملفات Excel المحمية بكلمة مرور؟**  
ج: يمكن لـ GroupDocs.Watermark فتح دفاتر العمل المحمية عندما تزود كلمة المرور عبر `SpreadsheetLoadOptions.setPassword("yourPassword")`.

**س: هل هناك حد لحجم المرفقات؟**  
ج: تدعم المكتبة مرفقات تصل إلى 2 جيجابايت، وهو الحد المتاح فقط من تنسيق ZIP الأساسي والمساحة المتوفرة على القرص.

**س: كيف يمكن إزالة مرفق لاحقًا؟**  
ج: استرجع مجموعة مرفقات الورقة واستدعِ `removeAttachment("AttachmentName.ext")` قبل حفظ دفتر العمل مرة أخرى.

## الخلاصة
لقد أتقنت الآن كيفية **add attachment to excel** باستخدام GroupDocs.Watermark for Java. من خلال تحميل دفتر العمل، تحويل الملفات الخارجية إلى مصفوفات بايت، تضمينها باستدعاء API واحد، وحفظ النتيجة، يمكنك إبقاء جميع الوثائق ذات الصلة معًا في حزمة نظيفة وقابلة للبحث. جرّب أنواع ملفات مختلفة، أتمتة المعالجة الدُفعية، واستكشف ميزات العلامات المائية الأخرى لإثراء جداول البيانات أكثر.

---

**Last Updated:** 2026-06-06  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## الدروس ذات الصلة

- [كيفية إضافة علامات مائية إلى مرفقات Excel باستخدام GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/add-watermarks-excel-attachments-groupdocs-java/)
- [إضافة علامة مائية صورة إلى جدول بيانات Excel باستخدام GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [معالجة مستندات Excel وإضافة علامات مائية باستخدام GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)