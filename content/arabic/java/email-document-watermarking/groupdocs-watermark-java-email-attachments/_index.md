---
date: '2025-12-29'
description: تعلم كيفية إضافة علامة مائية إلى مرفقات البريد الإلكتروني باستخدام GroupDocs.Watermark
  للغة Java. يقدم هذا الدليل إرشادات خطوة بخطوة وأفضل الممارسات.
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: إضافة علامة مائية إلى مرفقات البريد الإلكتروني باستخدام GroupDocs.Watermark
  لجافا
type: docs
url: /ar/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# إضافة علامة مائية إلى مرفقات البريد الإلكتروني باستخدام GroupDocs.Watermark للغة Java

في المشهد الرقمي اليوم، حماية المعلومات الحساسة أمر حيوي—خاصة عندما **تضيف علامة مائية إلى مرفقات البريد الإلكتروني** قبل أن تغادر صندوق الوارد الخاص بك. سواء كنت مطورًا يسعى لتعزيز أمان المستندات أو شركة تريد وضع علامتها التجارية على كل ملف صادر، يوضح لك هذا الدليل كيفية استخدام GroupDocs.Watermark للغة Java لتطبيق علامات مائية نصية على جميع المرفقات المدعومة داخل رسالة بريد إلكتروني.

## إجابات سريعة
- **ماذا يحقق “إضافة علامة مائية إلى البريد الإلكتروني”؟** يدمج تسمية مرئية أو شبه شفافة (مثل “سري”) في كل مرفق مدعوم، مما يثني عن التوزيع غير المصرح به.  
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark للغة Java (أحدث إصدار).  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي يعمل للتطوير؛ الترخيص التجاري مطلوب للإنتاج.  
- **هل يمكن معالجة عدة رسائل بريد إلكتروني في آن واحد؟** نعم—قم بلف الخطوات داخل حلقة على مجلد ملفات *.msg*.  
- **ما أنواع الملفات المدعومة؟** PDFs، Word، Excel، PowerPoint، الصور والعديد غيرها (انظر الوثائق الرسمية).

## ما هو “إضافة علامة مائية إلى البريد الإلكتروني”؟
إضافة علامة مائية إلى البريد الإلكتروني تعني فتح ملف البريد برمجيًا، استخراج كل مرفق، وختم نص مخصص (أو صورة) على تلك المستندات قبل إرسال البريد أو تخزينه. يضمن ذلك أن العلامة المائية تسافر مع الملف، مما يعزز السرية وهوية العلامة التجارية.

## لماذا نستخدم GroupDocs.Watermark للغة Java؟
- **دعم واسع للأنساق** – يعمل مع PDFs، ملفات Office، الصور، وأكثر.  
- **واجهة برمجة تطبيقات بسيطة** – بضع أسطر من الشيفرة تمكنك من إنشاء، تطبيق، وحفظ العلامات المائية.  
- **مركز على الأداء** – استهلاك منخفض للذاكرة، مثالي للمعالجة على الخادم.  
- **ترخيص جاهز للمؤسسات** – تجريبي للتقييم، ترخيص مدفوع للإنتاج.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) مثبتة.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- إضافة GroupDocs.Watermark للغة Java إلى مشروعك (انظر خطوات الإعداد أدناه).  

## إعداد GroupDocs.Watermark للغة Java

### إعداد Maven
إذا كنت تستخدم Maven، أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، حمّل أحدث نسخة من [إصدارات GroupDocs.Watermark للغة Java](https://releases.groupdocs.com/watermark/java/).

#### الحصول على الترخيص
- للحصول على نسخة تجريبية مجانية، سجّل في موقع GroupDocs واطلب ترخيصًا مؤقتًا.  
- للاستخدام التجاري، اشترِ ترخيصًا كاملًا. زر صفحة [الشراء](https://purchase.groupdocs.com/temporary-license/) لمزيد من المعلومات.

### التهيئة الأساسية
استورد الفئات الأساسية التي ستحتاجها:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## كيفية إضافة علامة مائية إلى مرفقات البريد الإلكتروني – دليل خطوة بخطوة

### الخطوة 1: إنشاء علامة مائية نصية
أولاً، عرّف نص العلامة المائية ومظهرها.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### الخطوة 2: إعداد خيارات تحميل البريد الإلكتروني
قم بتكوين القارئ بحيث يتمكن GroupDocs من قراءة ملف *.msg*.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### الخطوة 3: تهيئة Watermarker لملف البريد الإلكتروني الخاص بك
وجّه كائن `Watermarker` إلى البريد الإلكتروني الذي تريد معالجته.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### الخطوة 4: استرجاع محتوى البريد الإلكتروني
احصل على البنية الداخلية للبريد حتى تتمكن من التعامل مع مرفقاته.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### الخطوة 5: التكرار على المرفقات
قم بالتجول عبر كل مرفق وتحقق من إمكانية إضافة علامة مائية له.

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
لكل ملف مؤهل، افتحه باستخدام `Watermarker` جديد، طبّق العلامة المائية، واكتب التغييرات مرة أخرى إلى البريد الإلكتروني.

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

### الخطوة 10: حفظ البريد الإلكتروني المطبّق عليه علامة مائية
اكتب البريد الإلكتروني المعدل إلى ملف جديد بحيث يبقى الأصلي دون تغيير.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### الخطوة 11: التنظيف
حرّر الموارد بإغلاق كائن `Watermarker` الرئيسي.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## تطبيقات عملية
1. **مشاركة المستندات الداخلية** – دمج علامة الشركة أو إشعارات السرية في كل مرفق قبل التوزيع الداخلي.  
2. **الاتصالات مع العملاء** – حماية العقود، العروض، والبيانات المالية بعلامة “سري” واضحة.  
3. **حملات التسويق عبر البريد الإلكتروني** – إضافة علامات مائية خفيفة إلى ملفات PDF أو الصور المرفقة بالرسائل الترويجية، لتعزيز تذكر العلامة التجارية.

## اعتبارات الأداء
- **إدارة الذاكرة** – عالج مرفقًا واحدًا في كل مرة وأغلق كل `Watermarker` فور الانتهاء.  
- **حجم المرفق** – الملفات الكبيرة تزيد من زمن المعالجة؛ فكر في ضغطها أو تحديد حجمها قبل إضافة العلامة المائية.  
- **المعالجة الدفعية** – كرّر على دليل يحتوي على ملفات *.msg* لتقليل العبء عند التعامل مع عدد كبير من الرسائل.

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامات مائية إلى ملفات مشفرة؟**  
ج: لا. لا يدعم GroupDocs.Watermark إضافة علامات مائية إلى المستندات المشفرة لأسباب أمنية.

**س: ما أنواع الملفات المدعومة لإضافة العلامات المائية؟**  
ج: PDFs، Word، Excel، PowerPoint، الصور (PNG، JPEG، BMP)، والعديد من الصيغ الشائعة الأخرى. راجع الوثائق الرسمية للقائمة الكاملة.

**س: كيف يمكنني تخصيص مظهر علامتي المائية؟**  
ج: يمكنك تغيير عائلة الخط، الحجم، اللون، الشفافية، الدوران، والموضع باستخدام مُنشئ `TextWatermark` وخصائصه.

**س: هل المعالجة الدفعية لعدة رسائل بريد إلكتروني ممكنة؟**  
ج: نعم. ضع الخطوات داخل حلقة `for` تتنقل عبر مجلد ملفات *.msg* وطبق المنطق نفسه على كل ملف.

**س: علامتي المائية لا تظهر—ما الذي يجب فحصه؟**  
ج: تحقق من أن نوع ملف المرفق مدعوم، وتأكد من أن حجم العلامة المائية يناسب أبعاد الصفحة، وتأكد من أن المستند غير محمي بكلمة مرور.

## موارد
- [الوثائق](https://docs.groupdocs.com/watermark/java/)  
- [مرجع API](https://reference.groupdocs.com/watermark/java)  
- [تحميل GroupDocs.Watermark للغة Java](https://releases.groupdocs.com/watermark/java/)

---

**آخر تحديث:** 2025-12-29  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

---