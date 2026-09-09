---
date: '2026-03-27'
description: تعلم كيفية إضافة علامة مائية إلى ملفات Excel باستخدام GroupDocs.Watermark
  للغة Java. يوضح هذا الدليل إعداد البرنامج، والكود، وأفضل الممارسات لتطبيق العلامات
  المائية على جداول البيانات.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: إضافة علامة مائية إلى Excel باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# إضافة علامة مائية إلى Excel باستخدام GroupDocs.Watermark Java

إضافة علامة مائية إلى ملفات Excel الخاصة بك يمكن أن تكون خطوة حاسمة — سواء كنت تحتاج إلى حماية البيانات الحساسة، أو وضع علامة تجارية على تقاريرك، أو ببساطة إضافة لمسة احترافية. في هذا الدرس ستتعلم **كيفية إضافة علامة مائية إلى Excel** باستخدام GroupDocs.Watermark للغة Java، مع شروحات واضحة، وحالات استخدام واقعية، ونصائح لتجنب المشكلات الشائعة.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** GroupDocs.Watermark for Java (latest version).  
- **ما صيغ Excel المدعومة؟** .xlsx و .xls (غير مشفرة).  
- **هل يمكنني إضافة علامات مائية صورة؟** نعم – يدعم SDK كل من العلامات المائية النصية والصورية.  
- **هل أحتاج إلى ترخيص للإنتاج؟** يلزم ترخيص تجاري للنشر غير التجريبي.  
- **كم يستغرق التنفيذ؟** حوالي 10‑15 دقيقة لإضافة علامة مائية نصية أساسية.

## ما هو **إضافة علامة مائية إلى Excel**؟
إضافة علامة مائية إلى مصنف Excel تعني وضع نص أو صورة مرئية (أو شبه شفافة) على كل ورقة عمل أو مستند مضمّن. يساعدك ذلك على تأكيد الملكية، أو الإشارة إلى السرية، أو تعزيز العلامة التجارية عبر الملف بأكمله.

## لماذا تستخدم GroupDocs.Watermark للغة Java؟
يقدم GroupDocs.Watermark واجهة برمجة تطبيقات عالية المستوى تُبسط تعقيد التعامل مع هياكل Office Open XML. يتيح لك:
- تطبيق العلامات المائية على عدة أوراق عمل في استدعاء واحد.  
- معالجة المرفقات المضمّنة (مثل ملفات PDF المضمّنة) تلقائيًا.  
- الحفاظ على التنسيق الأصلي والصيغ.  
- العمل مع كل من العلامات المائية النصية والصورية (مثل **add image watermark java**).

## المتطلبات المسبقة

- **بيئة تطوير Java** – Java 8 أو أعلى (JDK).  
- **GroupDocs.Watermark للغة Java SDK** – قم بتنزيل أحدث إصدار من [هنا](https://releases.groupdocs.com/watermark/java/).  
- **IDE** – IntelliJ IDEA، Eclipse، أو أي محرر متوافق مع Java.  
- **عينة جدول بيانات** – ملف .xlsx تريد حمايته.

يمكنك إضافة SDK إلى مشروعك عبر Maven أو Gradle، أو بوضع ملفات JAR يدويًا على مسار الفئة (classpath).

## استيراد الحزم

توفر لك هذه الاستيرادات الوصول إلى الفئات الأساسية للعلامات المائية، ومعالجة جداول البيانات، وأدوات الخطوط.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## كيفية **وضع علامة مائية على جدول البيانات** – دليل خطوة بخطوة

فيما يلي دليل عملي مرقّم يوضح بالضبط **كيفية وضع علامة مائية على جدول البيانات** باستخدام Java. كل خطوة تتضمن شرحًا قصيرًا يليه كتلة الكود الأصلية (بدون تغيير).

### الخطوة 1: إعداد كائن العلامة المائية الخاص بك  
**لماذا؟** هذا الكائن يحدد المظهر البصري للعلامة التي ستطبقها.

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### الخطوة 2: تحميل جدول البيانات  
**لماذا؟** فتح المصنف يمنح SDK مقبضًا للتعديل.

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### الخطوة 3: الوصول إلى محتوى جدول البيانات وأوراق العمل  
**لماذا؟** يمكن لملفات Excel أن تحتوي على عدة أوراق؛ تحتاج إلى التكرار عبر كل واحدة.

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### الخطوة 4: التكرار عبر المرفقات في كل ورقة عمل  
**لماذا؟** بعض أوراق العمل تضم مستندات أخرى (مثل PDF). معالجتها يضمن علامة مائية متسقة عبر الملف بأكمله.

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### الخطوة 5: وضع علامة مائية على كل مستند مضمّن  
**لماذا؟** تريد نفس ختم "سري" على كل ملف مضمّن.

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### الخطوة 6: حفظ جميع التغييرات  
**لماذا؟** حفظ التعديلات في مصنف جديد.

```java
watermarker.save("your-output-file.xlsx");
```

### الخطوة 7: إغلاق الموارد  
**لماذا؟** تحرير الموارد يمنع تسرب الذاكرة، خاصةً عند معالجة مصنفات كبيرة.

```java
watermarker.close();
```

## تجميع كل شيء معًا: مثال كامل

الصفّ التالي يجمع كل خطوة في برنامج واحد قابل للتنفيذ. **لا تقم بتعديل كتلة الكود** – فهي مطابقة للمثال الأصلي.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## المشكلات الشائعة والحلول

| المشكلة | لماذا يحدث | الحل |
|-------|----------------|-----|
| **تم تخطي المصنف المشفر** | لا يستطيع SDK قراءة الملفات المشفرة بدون كلمة مرور. | فك تشفير الملف أولاً أو توفير كلمة المرور عبر `SpreadsheetLoadOptions.setPassword("pwd")`. |
| **العلامة المائية غير مرئية على بعض الأوراق** | قد تكون الورقة في وضع عرض مخصص أو محمية بحيث تُخفي كائنات الرسم. | قم بإلغاء حماية الورقة قبل إضافة العلامة المائية، ثم أعد تطبيق الحماية إذا لزم الأمر. |
| **تباطؤ الأداء على الملفات الكبيرة** | تحميل المصنف بالكامل إلى الذاكرة قد يكون ثقيلًا. | عالج الأوراق على دفعات أو زد حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`). |
| **العلامة المائية الصورية تظهر مشوهة** | إعدادات التحجيم غير صحيحة. | استخدم `ImageWatermark` مع معلمات العرض/الارتفاع الصريحة للحفاظ على نسبة الأبعاد. |

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامة مائية صورة بدلاً من النص؟**  
ج: نعم. استخدم `ImageWatermark` من SDK ومرّر كائن `java.awt.Image`. هذا يغطي سيناريو **add image watermark java**.

**س: كيف أتحكم في موضع العلامة المائية؟**  
ج: توفر فئة `TextWatermark` (أو `ImageWatermark`) خصائص مثل `setHorizontalAlignment` و `setVerticalAlignment` و `setOpacity` لضبط الموضع والشفافية بدقة.

**س: هل يمكن وضع علامة مائية على عدة ملفات Excel في تشغيل واحد؟**  
ج: بالتأكيد. ضع سير العمل بالكامل داخل حلقة `for` تتكرر عبر دليل يحتوي على الملفات، مع إعادة استخدام نفس كائن `TextWatermark`.

**س: ماذا يحدث إذا كان جدول البيانات يحتوي على مخططات؟**  
ج: تُعامل المخططات ككائنات رسم منفصلة؛ تُطبق العلامة المائية على لوحة ورقة العمل، لذا تظل المخططات غير متأثرة لكنها لا تزال مغطاة بالختم شبه الشفاف.

**س: هل يمكنني إزالة علامة مائية أُضيفت مسبقًا؟**  
ج: يتضمن SDK طرقًا مثل `watermarker.remove(watermark)`، لكن عليك الاحتفاظ بمرجع إلى كائن العلامة المائية الأصلي أو البحث حسب النص/المحتوى لتحديده.

---

**آخر تحديث:** 2026-03-27  
**تم الاختبار مع:** GroupDocs.Watermark 23.12 (Java)  
**المؤلف:** GroupDocs