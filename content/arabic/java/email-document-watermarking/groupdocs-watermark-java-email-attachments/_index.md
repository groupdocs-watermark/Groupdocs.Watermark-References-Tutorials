---
date: '2026-04-07'
description: تعلم كيفية إنشاء علامة مائية نصية لمرفقات البريد الإلكتروني باستخدام
  GroupDocs.Watermark للغة Java، وتأمين مرفقات البريد الإلكتروني وحماية البيانات السرية.
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: إنشاء علامة مائية نصية لمرفقات البريد الإلكتروني باستخدام GroupDocs Java
type: docs
url: /ar/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# كيفية إضافة العلامات المائية إلى مرفقات البريد الإلكتروني باستخدام GroupDocs.Watermark للغة Java

في هذا البرنامج التعليمي ستقوم **بإنشاء كائنات علامة مائية نصية** وتطبيقها على كل مرفق مدعوم داخل رسالة بريد إلكتروني. إضافة علامة مائية هي طريقة فعّالة **لتأمين مرفقات البريد الإلكتروني**، وإظهار السرية، وتعزيز هوية العلامة التجارية—كل ذلك ببضع أسطر من كود Java.

## مقدمة

حماية المعلومات الحساسة عندما تنتقل عبر البريد الإلكتروني أصبحت أكثر أهمية من أي وقت مضى. سواء كنت بحاجة إلى وضع علامة على التقارير الداخلية، أو تمييز العقود القانونية، أو ببساطة وضع علامة تجارية على أصول التسويق، توفر العلامة المائية النصية طبقة خفيفة من الحماية غير القابلة للتلاعب. يوضح هذا الدليل العملية الكاملة لاستخدام **GroupDocs.Watermark للغة Java** لإضافة علامة مائية مخصصة إلى كل مرفق في ملف Outlook `.msg`.

### ما ستتعلمه
- كيفية **إنشاء كائنات علامة مائية نصية** بخطوط وألوان مخصصة.  
- دمج العلامات المائية خطوة بخطوة في سير عمل معالجة البريد الإلكتروني باستخدام Java.  
- نصائح لتحسين الأداء عند التعامل مع مرفقات كبيرة.  
- سيناريوهات واقعية حيث تضيف العلامات المائية قيمة للمرفقات البريدية.

دعنا نتأكد من أن لديك كل ما تحتاجه قبل المتابعة.

## إجابات سريعة
- **ماذا يعني “إنشاء علامة مائية نصية”؟** يعني ذلك إنشاء كائن `TextWatermark` يحدد النص الظاهر، الخط، الحجم، والنمط لتراكبه على المستند.  
- **هل يمكنني وضع علامة مائية على مرفقات مشفرة؟** لا – لا يدعم GroupDocs.Watermark الملفات المشفرة لأسباب أمنية.  
- **ما هي أنواع الملفات المدعومة؟** PDFs، Word، Excel، PowerPoint، الصور، والعديد غيرها – راجع الوثائق الرسمية للقائمة الكاملة.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي يعمل للتطوير؛ الترخيص التجاري مطلوب للاستخدام في الإنتاج.  
- **ما مدى سرعة العملية؟** وضع علامة مائية على مرفق بحجم 2 ميغابايت عادةً يستغرق أقل من ثانية على الأجهزة الحديثة.

## المتطلبات المسبقة

- **Java Development Kit (JDK)** – الإصدار 8 أو أحدث.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- **GroupDocs.Watermark للغة Java** مضاف إلى مشروعك (انظر خطوات الإعداد أدناه).  
- الوصول إلى ملف بريد إلكتروني (`.msg`، `.eml`، إلخ) يحتوي على المرفقات التي تريد حمايتها.

## إعداد GroupDocs.Watermark للغة Java

### إعداد Maven

إذا كنت تدير الاعتمادات باستخدام Maven، أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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

بدلاً من ذلك، قم بتحميل أحدث ملف JAR من الموقع الرسمي:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### الحصول على الترخيص
- **تجريبي:** سجّل على موقع GroupDocs واطلب ترخيصًا مؤقتًا.  
- **تجاري:** اشترِ ترخيصًا كاملًا هنا: [purchase page](https://purchase.groupdocs.com/temporary-license/).

### التهيئة الأساسية

استورد الفئات الأساسية التي ستحتاجها في ملف Java الخاص بك:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## ما هي العلامة المائية النصية؟

**العلامة المائية النصية** هي قطعة نص شبه شفافة تُعرض فوق كل صفحة من المستند. باستخدام GroupDocs.Watermark يمكنك التحكم في الخط، الحجم، اللون، الدوران، والشفافية، مما يمنحك مرونة كاملة لإنشاء إشعار علامة تجارية أو سرية يندمج طبيعياً مع المحتوى الأصلي.

## لماذا تستخدم GroupDocs.Watermark لمرفقات البريد الإلكتروني؟

- **تأمين مرفقات البريد الإلكتروني** بوضع علامة مرئية عليها كسرية.  
- **الحفاظ على اتساق العلامة التجارية** عبر جميع المستندات الصادرة.  
- **معالجة دفعات** متعددة من الرسائل الإلكترونية بحلقة واحدة، مما يوفر الوقت ويقلل الأخطاء اليدوية.  
- **دعم صيغ متعددة** – يعمل نفس الكود مع PDFs، ملفات Word، الصور، وأكثر.

## دليل التنفيذ

سنستعرض كل خطوة، موضحين *السبب* وراء الكود حتى تتمكن من تكييفه مع مشاريعك الخاصة.

### الخطوة 1: إنشاء علامة مائية نصية

أولاً، أنشئ كائن `TextWatermark` بالنص الذي تريد عرضه وإعدادات الخط المطلوبة.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **نصيحة احترافية:** اضبط حجم الخط أو لونه ليتماشى مع دليل نمط الشركة. يمكنك أيضًا ضبط الشفافية عبر `watermark.setOpacity(0.5)` إذا كنت تحتاج إلى تأثير أكثر خفوتًا.

### الخطوة 2: إعداد خيارات تحميل البريد الإلكتروني

`EmailLoadOptions` تخبر المكتبة كيفية تفسير ملف البريد الإلكتروني الوارد.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### الخطوة 3: تهيئة Watermarker لملف البريد الإلكتروني الخاص بك

وجه مُنشئ `Watermarker` إلى ملف `.msg` (أو `.eml`) الذي ترغب في معالجته.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### الخطوة 4: استرجاع محتوى البريد الإلكتروني

استخرج الهيكل الداخلي للبريد حتى تتمكن من التكرار عبر مرفقاته.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### الخطوة 5: التكرار عبر المرفقات

لكل مرفق، نتحقق من أن نوع الملف مدعوم وأنه غير مشفر.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### الخطوة 6‑9: إضافة علامة مائية إلى المرفقات المدعومة

داخل كتلة الشرط، ننشئ `Watermarker` مخصصًا للمرفق، نطبق العلامة المائية، ثم نعيد المحتوى المعدل إلى البريد الإلكتروني.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### الخطوة 10: حفظ البريد الإلكتروني المموسوم

اكتب البريد الإلكتروني المحدث إلى ملف جديد بحيث يبقى الأصلي دون تعديل.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### الخطوة 11: التنظيف

دائمًا حرّر الموارد لتجنب تسرب الذاكرة.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|--------|-----|
| **العلامة المائية غير مرئية** | تم ضبط الشفافية منخفضة جدًا أو لون الخط يطابق الخلفية. | زيادة الشفافية (`watermark.setOpacity(0.7)`) أو اختيار لون متباين. |
| **نوع مرفق غير مدعوم** | تنسيق الملف غير موجود في قائمة الصيغ المدعومة من GroupDocs. | تحويل الملف إلى صيغة مدعومة أولاً (مثل PDF) أو تخطيه مع تسجيل رسالة. |
| **OutOfMemoryError على ملفات PDF الكبيرة** | تحميل مرفقات ضخمة يستهلك الكثير من الذاكرة. | زيادة حجم Heap للـ JVM (`-Xmx2g`) أو معالجة المرفقات على دفعات أصغر. |

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامات مائية إلى الملفات المشفرة؟**  
ج: لا، لا يدعم GroupDocs.Watermark إضافة علامات مائية إلى الملفات المشفرة بسبب قيود الأمان.

**س: ما هي أنواع الملفات المدعومة للعلامات المائية؟**  
ج: تشمل الأنواع المدعومة PDFs، مستندات Word، جداول Excel، عروض PowerPoint، وصيغ الصور الشائعة. راجع الوثائق الرسمية للقائمة الكاملة.

**س: كيف يمكنني تخصيص مظهر علامتي المائية؟**  
ج: استخدم فئة `Font` لتحديد الحجم، النمط، واللون، واستدعِ طرقًا مثل `setOpacity` و `setRotationAngle` على كائن `TextWatermark`.

**س: هل يمكن معالجة عدة رسائل بريد إلكتروني دفعةً واحدة؟**  
ج: نعم. ضع سير العمل بالكامل داخل حلقة تتكرر على الملفات في دليل، مع إعادة استخدام نفس كائن `TextWatermark` لتحقيق الكفاءة.

**س: علامتي المائية تظهر مقطوعة في الصفحة الأخيرة—ما الخطأ؟**  
ج: تأكد من أن العلامة المائية تناسب هوامش الصفحة. يمكنك تعديل موضعها باستخدام `watermark.setHorizontalAlignment` و `watermark.setVerticalAlignment`.

## التطبيقات العملية

1. **مشاركة المستندات الداخلية:** دمج هوية الشركة أو إشعارات السرية قبل توزيع التقارير داخل المنظمة.  
2. **الاتصالات مع العملاء:** وضع علامة “سري” على العقود والعروض لتذكير المستلمين بسياسات التعامل مع البيانات.  
3. **التسويق عبر البريد الإلكتروني:** إضافة علامة تجارية خفيفة إلى ملفات PDF المرفقة بالنشرات الإخبارية، مما يعزز تذكر العلامة دون إفساد التصميم.

## اعتبارات الأداء

- **إدارة الذاكرة:** أغلق كل `attachedWatermarker` فورًا (كما هو موضح في الخطوة 9) لتحرير الموارد الأصلية.  
- **حدود حجم الملفات:** للمرفقات التي تتجاوز 10 ميغابايت، فكر في بث الملف أو زيادة حجم Heap للـ JVM.  
- **المعالجة المتوازية:** استخدم `ExecutorService` في Java لمعالجة عدة رسائل بريد إلكتروني في وقت واحد، لكن راقب استهلاك المعالج لتجنب التنافس.

## الخلاصة

أصبح لديك الآن وصفة جاهزة للإنتاج حول كيفية **إنشاء كائنات علامة مائية نصية** وتطبيقها على كل مرفق مدعوم داخل ملف بريد إلكتروني باستخدام GroupDocs.Watermark للغة Java. من خلال دمج هذا سير العمل في خط أنابيب معالجة البريد الإلكتروني الحالي، ستعزز أمان المستندات، وتفرض العلامة التجارية، وتضمن الامتثال بأقل جهد ممكن.

هل أنت مستعد للخطوة التالية؟ جرّب توسيع الكود لمعالجة مجلد كامل من ملفات `.msg`، أو استكشف أنواع علامات مائية إضافية مثل الصور ورموز QR.

---

**آخر تحديث:** 2026-04-07  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

**الموارد**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)