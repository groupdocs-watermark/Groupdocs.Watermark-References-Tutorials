---
date: '2026-03-20'
description: تعلم كيفية إضافة علامة مائية إلى جداول Excel باستخدام GroupDocs.Watermark
  للغة Java، مع تغطية تقنيات إضافة علامة مائية نصية إلى Excel وتقنيات إضافة علامة
  مائية إلى Excel باستخدام Java.
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: كيفية إضافة علامة مائية إلى Excel باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# كيفية إضافة علامة مائية إلى جدول بيانات إكسل باستخدام GroupDocs.Watermark للغة Java

إضافة **كيفية إضافة علامة مائية** إلى ملفات إكسل طريقة عملية لحماية البيانات الحساسة وتأكيد الملكية. في هذا الدليل خطوة بخطوة ستتعلم كيفية إضافة علامة مائية إلى جدول بيانات إكسل، تخصيص مظهرها، ووضعها في الرؤوس أو التذييلات — كل ذلك باستخدام GroupDocs.Watermark للغة Java.

## الإجابات السريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark للغة Java (الإصدار 24.11 أو أحدث).  
- **هل يمكنني تخصيص الخط واللون؟** نعم، باستخدام فئات `Font` و `Color`.  
- **أين تظهر العلامة المائية؟** في رأس أو تذييل ورقة العمل المحددة.  
- **هل تحتاج إلى ترخيص للإنتاج؟** يلزم وجود ترخيص GroupDocs صالح للاستخدام غير التجريبي.  
- **هل سيعمل هذا مع ملفات عمل كبيرة؟** نعم، لكن يجب إغلاق كائن `Watermarker` لتحرير الموارد.

## المقدمة

هل تبحث عن تعزيز أمان جداول إكسل الخاصة بك بإضافة علامات مائية نصية؟ سواء كان ذلك لحماية البيانات السرية أو لتأكيد الملكية، فإن دمج علامة مائية في رؤوس أو تذييلات جدول البيانات يمكن أن يكون ذا قيمة كبيرة. في هذا البرنامج التعليمي، سنرشدك إلى تنفيذ هذه الميزة باستخدام GroupDocs.Watermark للغة Java.

**ما ستتعلمه**
- كيفية إضافة علامة مائية نصية إلى جداول إكسل  
- تكوين العلامات المائية بخطوط وألوان مخصصة  
- ضبط محاذاة الرأس/التذييل في مستنداتك  

مع هذه المهارات، ستكون مجهزًا جيدًا لتأمين جداول البيانات بفعالية. الآن، دعنا نستعرض المتطلبات اللازمة للبدء.

## ما هو “كيفية إضافة علامة مائية” في إكسل؟

العلامة المائية هي نص أو صورة شبه شفافة تظهر خلف (أو أمام) المحتوى الرئيسي. في إكسل، تُوضع العلامات المائية عادةً في منطقة الرأس أو التذييل بحيث تظهر في كل صفحة مطبوعة دون التدخل مع بيانات الخلايا.

## لماذا تستخدم GroupDocs.Watermark للغة Java؟

- **متعدد المنصات**: يعمل على أي نظام تشغيل يدعم Java.  
- **تحكم كامل**: تخصيص الخط، الحجم، اللون، والمحاذاة.  
- **مركز على الأداء**: معالجة فعّالة لملفات العمل الكبيرة.  

## المتطلبات المسبقة

- **GroupDocs.Watermark للغة Java** (الإصدار 24.11 أو أحدث)  
- **مجموعة تطوير جافا (JDK)** مثبتة ومُكوَّنة  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse  
- Maven (إذا كنت تفضل إدارة الاعتمادات)  

### المكتبات المطلوبة

- **GroupDocs.Watermark للغة Java** – توفر واجهة برمجة التطبيقات للعلامات المائية.  

### المتطلبات المعرفية

- برمجة جافا الأساسية  
- الإلمام بـ Maven أو التعامل اليدوي مع ملفات JAR  

## إعداد GroupDocs.Watermark للغة Java

يمكنك تثبيت المكتبة عبر Maven أو تنزيل ملف JAR مباشرة.

**تثبيت Maven**

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

**تحميل مباشر**  
بدلاً من ذلك، يمكنك تنزيل أحدث نسخة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **تجربة مجانية** – استكشاف الـ API بدون تكلفة.  
- **ترخيص مؤقت** – فترة تقييم ممتدة.  
- **شراء** – كامل المميزات، استخدام غير محدود.

لتهيئة GroupDocs.Watermark، أدرج بيان الاستيراد التالي:

```java
import com.groupdocs.watermark.Watermarker;
```

## كيفية إضافة علامة مائية إلى جداول إكسل

فيما يلي الكود الكامل القابل للتنفيذ مقسَّم إلى خطوات واضحة. كل خطوة تتضمن شرحًا موجزًا قبل كتلة الكود، حتى لا ترى أي مقتطف بدون سياق.

### الخطوة 1: تحميل جدول البيانات

أولاً، حمّل دفتر العمل باستخدام خيارات التحميل المناسبة.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**شرح**: هذه السطر ينشئ كائن `Watermarker` مرتبط بملف إكسل الخاص بك، جاهز لإجراء عمليات العلامة المائية.

### الخطوة 2: إنشاء العلامة المائية النصية

قم بتكوين المظهر البصري للعلامة المائية.

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**شرح**: نحدد نص العلامة المائية، نختار خط **Segoe UI** غامق، ونطبق ألوان أمامية وخلفية متباينة.

### الخطوة 3: تكوين وضع العلامة المائية

حدد أي ورقة عمل وأي جزء من الصفحة (رأس/تذييل) سيستقبل العلامة المائية.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**شرح**: كائن `SpreadsheetWatermarkHeaderFooterOptions` يخبر الـ API بتطبيق العلامة المائية على رأس/تذييل الورقة الأولى.

### الخطوة 4: إضافة العلامة المائية وحفظ الملف

طبق العلامة المائية واكتب النتيجة إلى ملف جديد.

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**شرح**: طريقة `add` تُدرج العلامة المائية، `save` تكتب دفتر العمل المعدل، و`close` تحرّر الموارد.

## إضافة علامة مائية نصية إلى إكسل – نصائح متقدمة

- **أوراق عمل متعددة**: كرّر عبر فهارس الأوراق واستدعِ `options.setWorksheetIndex(i)` لكل واحدة.  
- **نص ديناميكي**: استخرج نص العلامة المائية من قاعدة بيانات أو ملف إعدادات لتخصيص كل مستند.  
- **التحكم في الشفافية**: استخدم `watermark.setOpacity(0.5)` لجعل العلامة المائية أكثر خفوتًا.  

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| **File Not Found** | تحقق من صحة سلاسل المسار (`YOUR_DOCUMENT_DIRECTORY/...`) واستخدم مسارات مطلقة أثناء الاختبار. |
| **License Not Found** | ضع ملف `GroupDocs.Watermark.lic` في جذر المشروع أو عيّن الترخيص برمجيًا باستخدام `License license = new License(); license.setLicense("path/to/license.lic");`. |
| **Unsupported Format** | تأكد من حفظ دفتر العمل بصيغة `.xlsx` أو `.xls`. قد تحتاج الصيغ القديمة إلى تحويل أولاً. |
| **Performance Lag on Large Files** | عالج ورقة عمل واحدة في كل مرة واستدعِ `watermarker.close()` فور الانتهاء من كل ملف. |

## التطبيقات العملية

1. **حماية البيانات السرية** – ردع النسخ غير المصرح به عن طريق وضع علامة مرئية على كل صفحة مطبوعة.  
2. **تأكيد الملكية** – دمج اسم الشركة أو الشعار كعلامة مائية لإثبات أصل الوثيقة.  
3. **تتبع المستندات** – تضمين معرفات فريدة في العلامة المائية لتتبع مسارات التوزيع.  

## اعتبارات الأداء

- قلل عدد العلامات المائية في كل جلسة.  
- أغلق كائن `Watermarker` فورًا لتحرير مقابض الملفات.  
- بالنسبة لدفاتر العمل الكبيرة جدًا، فكر في زيادة حجم الذاكرة المخصصة للـ JVM (`-Xmx2g`).  

## الأسئلة المتكررة

**س: هل يمكنني تغيير نمط خط علامتي المائية؟**  
ج: نعم، يمكنك تخصيص كائن `Font` بأي عائلة خط مثبتة، حجم، و`FontStyle` (غامق، مائل، إلخ).

**س: هل من الممكن إضافة علامات مائية إلى أوراق متعددة؟**  
ج: بالتأكيد. كرّر عبر فهارس الأوراق وطبق نفس `SpreadsheetWatermarkHeaderFooterOptions` على كل ورقة.

**س: ما صيغ الملفات التي يدعمها GroupDocs.Watermark لملفات إكسل؟**  
ج: صيغ XLS، XLSX، وغيرها من صيغ Office Open XML للجدوال مدعومة بالكامل.

**س: كيف يمكنني التعامل مع المستندات الكبيرة جدًا بكفاءة؟**  
ج: عالج دفتر عمل واحد في كل مرة، أغلق `Watermarker` بعد الحفظ، وتابع استهلاك الذاكرة في JVM.

**س: هل يمكن إزالة العلامات المائية لاحقًا إذا لزم الأمر؟**  
ج: لا يتوفر إزالة مباشرة، لكن يمكنك إعادة إنشاء الملف الأصلي دون تطبيق علامة مائية أو الاحتفاظ بنسخة غير مائية للاستخدام المستقبلي.

## الموارد

- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-03-20  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**Author:** GroupDocs