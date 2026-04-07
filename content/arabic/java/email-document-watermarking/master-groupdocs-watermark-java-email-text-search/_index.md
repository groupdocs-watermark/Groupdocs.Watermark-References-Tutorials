---
date: '2026-04-07'
description: تعلم كيفية البحث في نص البريد الإلكتروني باستخدام Java وGroupDocs.Watermark،
  بما في ذلك كيفية البحث عن عدة كلمات مفتاحية في البريد الإلكتروني وكيفية إزالة العلامات
  المائية من البريد الإلكتروني.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'البحث في محتوى البريد الإلكتروني باستخدام Java وGroupDocs.Watermark: دليل
  شامل'
type: docs
url: /ar/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# بحث نص البريد الإلكتروني Java باستخدام GroupDocs.Watermark

إذا كنت بحاجة إلى **search email body java** بسرعة وموثوقية، فقد وصلت إلى المكان الصحيح. في هذا البرنامج التعليمي سنستعرض كيف يتيح لك GroupDocs.Watermark for Java تحديد نص محدد داخل عناوين البريد الإلكتروني، ومحتويات HTML، ومحتويات النص العادي، وكيف يمكنك إزالة العلامات المائية غير المرغوب فيها لاحقًا. في النهاية، ستكون قادرًا على تنفيذ حل قوي يعمل على كلمة مفتاحية واحدة أو متعددة وحتى يزيل العلامات المائية للبريد الإلكتروني عند الحاجة.

## إجابات سريعة
- **What does “search email body java” mean?** يشير إلى استخدام كود Java (مع GroupDocs.Watermark) للعثور على نص داخل محتوى البريد الإلكتروني.  
- **Can I search multiple keywords email at once?** نعم – أنشئ كائنات `SearchCriteria` منفصلة وادمجها.  
- **How to remove email watermarks?** استخدم طريقة `PossibleWatermarkCollection.clear()` بعد البحث.  
- **Do I need a license?** النسخة التجريبية المجانية تعمل للاختبار؛ يلزم الحصول على ترخيص دائم للإنتاج.  
- **Which IDE works best?** IntelliJ IDEA أو Eclipse كلاهما مدعومان بالكامل.

## ما ستتعلمه
- تثبيت وتكوين GroupDocs.Watermark for Java.  
- إعداد معايير البحث لـ **search email body java** عبر العناوين والمحتويات.  
- تقنيات لـ **search multiple keywords email** في تشغيل واحد.  
- الخطوات الدقيقة لـ **how to remove email watermarks** بعد تحديدها.  

## لماذا البحث في نص البريد الإلكتروني Java باستخدام GroupDocs.Watermark؟
يقدم GroupDocs.Watermark واجهة برمجة تطبيقات (API) عالية المستوى تُجرد تعقيدات تحليل ملفات .msg، ومعالجة صيغ المحتوى المختلفة، وإدارة العلامات المائية. هذا يوفر لك الوقت مقارنةً بإنشاء محلل مخصص ويضمن نتائج متسقة عبر دفعات البريد الإلكتروني الكبيرة.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) 8 أو أحدث.  
- Maven (أو القدرة على إضافة ملفات JAR يدويًا).  
- إلمام أساسي بـ Java وصيغ ملفات البريد الإلكتروني (.msg, .eml).  

## إعداد GroupDocs.Watermark لـ Java
يبسط GroupDocs.Watermark for Java عملية إضافة العلامات المائية والبحث عن النص داخل المستندات، بما في ذلك رسائل البريد الإلكتروني. أدناه طريقتان الأكثر شيوعًا لإضافة المكتبة إلى مشروعك.

### إعداد Maven
قم بإدراج ما يلي في ملف `pom.xml` الخاص بك لإضافة GroupDocs.Watermark كاعتماد:
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

### تحميل مباشر
بدلاً من ذلك، يمكنك تنزيل أحدث نسخة مباشرةً من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### خطوات الحصول على الترخيص
- **Free Trial:** ابدأ بنسخة تجريبية مجانية لاختبار الوظائف الأساسية.  
- **Temporary License:** احصل على ترخيص مؤقت للوصول الموسع والاختبار.  
- **Purchase:** فكر في الشراء إذا كان GroupDocs.Watermark يلبي احتياجاتك.

#### التهيئة الأساسية
قم بتهيئة الفئة `Watermarker` كما هو موضح أدناه:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## دليل التنفيذ

### الميزة 1: البحث عن نص في جسم البريد الإلكتروني
تمكنك هذه الميزة من البحث عن نص محدد داخل موضوع البريد الإلكتروني وجسده.

#### نظرة عامة
سنوضح كيفية تكوين GroupDocs.Watermark للبحث عبر أجزاء مختلفة من رسالة البريد الإلكتروني باستخدام كود Java.

##### الخطوة 1: تعريف مسارات المستندات
قم بإعداد مسارات الإدخال والإخراج لمعالجة رسائل البريد الإلكتروني:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### الخطوة 2: إعداد خيارات التحميل وWatermarker
قم بتهيئة `EmailLoadOptions` و `Watermarker` للعمل مع مستند البريد الإلكتروني الخاص بك.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### الخطوة 3: إنشاء معايير البحث
حدد معايير للبحث عن النص. سنستخدم بحثًا غير حساس لحالة الأحرف للكلمة المفتاحية **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### الخطوة 4: تحديد مواقع البحث
قم بتكوين البحث ليشمل كلًا من موضوع البريد الإلكتروني وجسده:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### الخطوة 5: تنفيذ البحث وإزالة العلامات المائية
نفّذ البحث وأزل أي علامات مائية تم العثور عليها:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### الخطوة 6: حفظ التغييرات
بعد المعالجة، احفظ التغييرات في مستند جديد:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### نصائح استكشاف الأخطاء وإصلاحها
- **Common Issue:** إذا كانت نتائج البحث فارغة، تأكد من وجود النص في جسم البريد الإلكتروني أو موضوعه.  
- **Performance Tip:** حسّن الأداء عن طريق تقييد البحث على الأقسام التي تحتاجها فعليًا.

### الميزة 2: خيارات تحميل مستند البريد الإلكتروني
تناقش هذه القسم كيفية إعداد خيارات إضافية عند تحميل مستند بريد إلكتروني للمعالجة باستخدام GroupDocs.Watermark.

#### نظرة عامة
يتيح تكوين خيارات التحميل مزيدًا من التحكم في طريقة معالجة المستندات، مثل تحديد حماية كلمة المرور أو إعدادات الترميز.

##### الخطوة 1: تكوين خيارات التحميل
إليك إعداد أساسي لـ `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### خيارات التكوين الرئيسية
- **Password Protection:** حدد كلمات المرور إذا كانت رسائل البريد الإلكتروني مشفرة.  
- **Encoding Settings:** عرّف أنواع الترميز المحددة حسب الحاجة.

## كيفية البحث عن عدة كلمات مفتاحية في البريد الإلكتروني
إذا كنت بحاجة إلى تحديد عدة مصطلحات في تمريرة واحدة، أنشئ كائنات `SearchCriteria` متعددة وادمجها باستخدام عوامل منطقية **OR** أو **AND**. تسمح لك الواجهة البرمجية (API) بسلسلة المعايير، بحيث يمكنك البحث عن “invoice” **or** “receipt” دون تشغيل حلقات منفصلة.

## كيفية إزالة العلامات المائية للبريد الإلكتروني
بعد تحديد العلامات المائية (أو أي نص يطابق معاييرك)، تقوم طريقة `PossibleWatermarkCollection.clear()` بإزالتها من مستند البريد الإلكتروني. هذه هي الخطوة الدقيقة التي استخدمناها في **Step 5** أعلاه، وتعمل مع أي عدد من المطابقات.

## تطبيقات عملية

### حالة الاستخدام 1: معالجة البريد الإلكتروني الآلية
قم بأتمتة تصفية ومعالجة بيانات البريد الإلكتروني الضخمة للعثور على محتوى محدد بكفاءة.

### حالة الاستخدام 2: فحص الامتثال القانوني
ضمان الامتثال من خلال البحث عن معلومات حساسة داخل رسائل البريد الإلكتروني المؤسسية.

### حالة الاستخدام 3: أتمتة دعم العملاء
تبسيط سير عمل الدعم من خلال تحديد الكلمات المفتاحية أو العبارات بسرعة في استفسارات العملاء.

## اعتبارات الأداء
عند استخدام GroupDocs.Watermark، ضع في اعتبارك ما يلي لتحسين الأداء:
- **Resource Management:** إدارة الذاكرة وقوة المعالجة بفعالية للتعامل مع مجموعات بيانات البريد الإلكتروني الكبيرة.  
- **Java Memory Management Best Practices:** راقب استخدام الموارد بانتظام وأطلق الموارد بسرعة.

## الأسئلة المتكررة

**Q:** كيف يمكنني التعامل مع رسائل البريد الإلكتروني المشفرة باستخدام GroupDocs.Watermark؟  
**A:** استخدم `EmailLoadOptions` لتحديد كلمات المرور عند تهيئة `Watermarker`.

**Q:** هل يمكنني البحث عن عدة كلمات مفتاحية في آن واحد؟  
**A:** نعم، أنشئ مثيلات `SearchCriteria` منفصلة وادمجها باستخدام عمليات منطقية.

**Q:** هل GroupDocs.Watermark Java مجاني للاستخدام؟  
**A:** تتوفر نسخة تجريبية مجانية؛ فكر في شراء ترخيص للحصول على ميزات موسعة.

**Q:** كيف يمكنني التعامل مع حجم كبير من رسائل البريد الإلكتروني بكفاءة؟  
**A:** حسّن عمليات البحث عن طريق استهداف أقسام معينة من البريد الإلكتروني وإدارة الموارد بفعالية.

**Q:** أين يمكنني العثور على مساعدة أو دعم إضافي؟  
**A:** زر [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10) للحصول على دعم المجتمع أو تواصل مع قناة الدعم المجانية الخاصة بهم.

## الموارد
- **Documentation:** استكشف أدلة مفصلة على [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** احصل على التفاصيل التقنية على [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**آخر تحديث:** 2026-04-07  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs