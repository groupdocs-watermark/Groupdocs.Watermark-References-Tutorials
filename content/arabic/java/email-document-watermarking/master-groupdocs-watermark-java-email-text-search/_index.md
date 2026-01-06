---
date: '2025-12-31'
description: تعلم كيفية البحث في نص البريد الإلكتروني باستخدام GroupDocs.Watermark
  للغة Java، وإدارة النصوص، والموضوعات، والمرفقات بفعالية.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: كيفية البحث في نص البريد الإلكتروني باستخدام GroupDocs.Watermark Java – دليل
  شامل
type: docs
url: /ar/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# كيفية البحث في نص البريد الإلكتروني باستخدام GroupDocs.Watermark Java

العثور على عبارة محددة داخل موضوع البريد الإلكتروني أو محتواه أو مرفقاته قد يكون مرهقًا—خاصةً عندما تتعامل مع العشرات أو المئات من الرسائل. في هذا البرنامج التعليمي ستكتشف **كيفية البحث في البريد الإلكتروني** بسرعة ودقة باستخدام **GroupDocs.Watermark for Java**. سنستعرض الإعداد، الكود، ونصائح أفضل الممارسات حتى تتمكن من دمج البحث في نص البريد الإلكتروني في تطبيقاتك بثقة.

## إجابات سريعة
- **ما المكتبة التي تسمح لي بالبحث في نص البريد الإلكتروني في Java؟** GroupDocs.Watermark for Java.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يعمل للاختبار؛ الترخيص المدفوع مطلوب للإنتاج.  
- **هل يمكنني البحث في كل من الموضوع والمحتوى؟** نعم—قم بتكوين `EmailSearchableObjects` لتشمل Subject و HtmlBody و PlainTextBody.  
- **هل الـ API حسّاس لحالة الأحرف؟** يمكنك اختيار بحث غير حساس لحالة الأحرف عن طريق ضبط العلامة المناسبة في `TextSearchCriteria`.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى؛ يُنصح باستخدام Maven لإدارة الاعتمادات.

## ما هو “كيفية البحث في البريد الإلكتروني” باستخدام GroupDocs.Watermark؟
يوفر GroupDocs.Watermark API موحدًا لتحديد وإزالة أو تعديل العلامات المائية والنص العادي عبر العديد من أنواع المستندات—بما في ذلك **رسائل البريد الإلكتروني** (`.msg`, `.eml`). من خلال الاستفادة من نموذج الكائنات القابلة للبحث، يمكنك استهداف الأجزاء المحددة من البريد الإلكتروني التي تهمك، مما يجعل المعالجة الجماعية سريعة وموثوقة.

## لماذا نستخدم GroupDocs.Watermark Java للبحث في البريد الإلكتروني؟
- **API موحد** – يعمل مع ملفات PDF، الصور، ملفات Office، والبريد الإلكتروني باستخدام نفس أنماط الكود.  
- **محسّن للأداء** – عمليات البحث تُنفّذ في الذاكرة دون الحاجة إلى خدمات خارجية.  
- **معالجة قوية** – يدعم محتويات HTML والنص العادي، المرفقات، وحتى رسائل البريد المحمية بكلمة مرور.  
- **تكامل سهل** – جاهز لـ Maven/Gradle، مع وثائق واضحة ودعم نشط.

## المتطلبات المسبقة

- **Java Development Kit (JDK)** 8 أو أحدث.  
- **Maven** (أو Gradle) لإدارة الاعتمادات.  
- بيئة تطوير متكاملة مثل **IntelliJ IDEA** أو **Eclipse**.  
- إلمام أساسي بصيغة Java وتنسيقات ملفات البريد الإلكتروني (`.msg`, `.eml`).

## إعداد GroupDocs.Watermark لـ Java

### إعداد Maven
أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، يمكنك تنزيل أحدث JAR من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **الإصدار التجريبي المجاني:** اختبار الميزات الأساسية دون مفتاح ترخيص.  
- **ترخيص مؤقت:** طلب مفتاح محدود الزمن للتقييم الموسع.  
- **ترخيص مدفوع:** شراء للاستخدام الإنتاجي غير المحدود.

#### التهيئة الأساسية
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## دليل التنفيذ

### الميزة 1: البحث عن نص في جسم البريد الإلكتروني

#### نظرة عامة
سنقوم بتكوين الـ API لفحص **الموضوع**، **جسم HTML**، و **جسم النص العادي** للبريد الإلكتروني للبحث عن كلمة مفتاحية معينة.

#### الخطوة 1: تعريف مسارات المستندات
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### الخطوة 2: إعداد خيارات التحميل و Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### الخطوة 3: إنشاء معايير البحث
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### الخطوة 4: تحديد مواقع البحث
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### الخطوة 5: تنفيذ البحث وإزالة العلامات المائية
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### الخطوة 6: حفظ التغييرات
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### نصائح استكشاف الأخطاء وإصلاحها
- **نتائج فارغة:** تأكد من أن الكلمة المفتاحية تظهر فعليًا في أجزاء البريد الإلكتروني المحددة.  
- **الأداء:** قلل الكائنات القابلة للبحث إلى ما تحتاجه فقط (مثال: Subject + PlainTextBody) لتسريع الدفعات الكبيرة.

### الميزة 2: خيارات تحميل مستند البريد الإلكتروني

#### نظرة عامة
`EmailLoadOptions` يتيح لك التحكم في طريقة تحليل البريد الإلكتروني—مفيد للرسائل المشفرة أو الترميزات المخصصة.

#### الخطوة 1: تكوين خيارات التحميل
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### خيارات التكوين الأساسية
- **حماية بكلمة مرور:** اضبط `loadOptions.setPassword("yourPassword")` لملفات `.msg` المشفرة.  
- **إعدادات الترميز:** عدّل `loadOptions.setEncoding(Charset.forName("UTF-8"))` عند التعامل مع مجموعات أحرف غير قياسية.

## تطبيقات عملية

- **معالجة البريد الإلكتروني الآلية:** فحص دفعة من تذاكر الدعم الواردة للبحث عن كلمات مثل “refund” أو “error”.  
- **فحص الامتثال القانوني:** تحديد سريع للمصطلحات السرية (مثل SSN، أرقام بطاقات الائتمان) عبر أرشيف البريد المؤسسي.  
- **أتمتة دعم العملاء:** توجيه الرسائل بناءً على العبارات المكتشفة إلى فريق الدعم المناسب.

## اعتبارات الأداء
- **إدارة الموارد:** استدعِ `watermarker.close()` فور الانتهاء من المعالجة لتحرير الموارد الأصلية.  
- **أفضل ممارسات الذاكرة:** عند معالجة آلاف الرسائل، عالجها على دفعات وأعد استخدام كائن `Watermarker` حيثما أمكن.

## الخلاصة
أصبح لديك الآن نهج قوي وجاهز للإنتاج للبحث عن محتوى **البريد الإلكتروني** باستخدام GroupDocs.Watermark Java. تسمح لك مرونة الـ API باستهداف أجزاء محددة من البريد الإلكتروني، إزالة العلامات المائية غير المرغوبة، ودمج المنطق في سير عمل أكبر.

### الخطوات التالية
- جرّب **معايير بحث متعددة** (مثال: دمج “invoice” + “overdue”).  
- استكشف **إضافة علامة مائية** لتعليم الرسائل التي تحتوي على بيانات حساسة.  
- تعمق في أنواع مستندات أخرى (PDF، DOCX) باستخدام نفس سير عمل Watermarker.

## الأسئلة المتكررة

**س1:** كيف يمكنني التعامل مع رسائل البريد المشفرة باستخدام GroupDocs.Watermark؟  
**ج1:** استخدم `EmailLoadOptions.setPassword("yourPassword")` قبل إنشاء كائن `Watermarker`.

**س2:** هل يمكنني البحث عن عدة كلمات مفتاحية في آن واحد؟  
**ج2:** نعم—أنشئ كائنات `SearchCriteria` منفصلة لكل كلمة مفتاحية وادمجها باستخدام عوامل منطقية (مثال: `OrSearchCriteria`).

**س3:** هل GroupDocs.Watermark Java مجاني للاستخدام؟  
**ج3:** يتوفر إصدار تجريبي مجاني للتقييم. للاستخدام الإنتاجي، يلزم الحصول على ترخيص مدفوع.

**س4:** كيف يمكنني معالجة حجم كبير من الرسائل بكفاءة؟  
**ج4:** قلل الكائنات القابلة للبحث إلى ما تحتاجه فقط، عالج الرسائل على دفعات، وتأكد دائمًا من إغلاق `Watermarker` لتحرير الموارد.

**س5:** أين يمكنني العثور على مساعدة أو دعم إضافي؟  
**ج5:** زر [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10) للحصول على مساعدة المجتمع أو تواصل مباشرةً مع دعم GroupDocs.

## الموارد
- **الوثائق:** استكشف أدلة مفصلة على [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **مرجع API:** احصل على تفاصيل تقنية على [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**آخر تحديث:** 2025-12-31  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 لـ Java  
**المؤلف:** GroupDocs