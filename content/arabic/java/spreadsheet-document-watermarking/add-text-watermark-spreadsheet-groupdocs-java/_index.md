---
date: '2026-03-22'
description: تعلم كيفية وضع علامة مائية على ملفات Excel بإضافة علامة مائية نصية سرية
  باستخدام GroupDocs.Watermark للغة Java. اتبع التعليمات خطوة بخطوة لتطبيق علامة مائية
  خلفية على Excel.
keywords:
- text watermark spreadsheet Java
- GroupDocs.Watermark for Java
- add watermark to spreadsheets
title: 'كيفية وضع علامة مائية على Excel: إضافة علامة مائية نصية إلى جدول بيانات باستخدام
  GroupDocs.Watermark في Java'
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-text-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# كيفية وضع علامة مائية على Excel: إضافة علامة مائية نصية إلى جدول بيانات باستخدام GroupDocs.Watermark في Java

حماية البيانات الحساسة في دفاتر Excel هي متطلب شائع للعديد من الشركات. في هذا الدليل، **ستتعلم كيفية وضع علامة مائية على ملفات Excel** باستخدام GroupDocs.Watermark للغة Java، مما يضمن أن يرى كل مشاهد إشعارًا واضحًا “سري” مباشرةً على خلفية المستند.

## إجابات سريعة
- **ماذا يعني “كيفية وضع علامة مائية على Excel”؟** يشير إلى إضافة طبقة مرئية (نص أو صورة) تحدد الملف على أنه محمي أو سري.  
- **ما المكتبة التي يجب أن أستخدمها؟** توفر GroupDocs.Watermark للغة Java واجهة برمجة تطبيقات بسيطة لإضافة علامات مائية نصية أو صورة على ملفات Excel.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي يعمل للتقييم؛ يتطلب الترخيص الدائم للاستخدام في الإنتاج.  
- **هل يمكنني تخصيص الشفافية والدوران؟** نعم—خيارات مثل `setOpacity` و `setRotateAngle` وتغيير الحجم مدعومة بالكامل.  
- **هل المعالجة الدفعية ممكنة؟** بالطبع؛ يمكنك التكرار عبر عدة دفاتر عمل مع إعادة استخدام نفس كائن `Watermarker`.

## ما معنى “كيفية وضع علامة مائية على Excel”؟
وضع علامة مائية على Excel يعني دمج طبقة نصية أو صورة شبه شفافة داخل ورقة العمل بحيث يتم تمييز المحتوى على أنه سري أو يحمل علامة تجارية أو مُعرف بطريقة أخرى. هذه الطبقة لا تتداخل مع إدخال البيانات لكنها تظل مرئية عند فتح الملف أو طباعته.

## لماذا نستخدم GroupDocs.Watermark للغة Java؟
- **التوافق عبر الأنظمة:** يعمل على أي بيئة تعتمد على JVM.  
- **خيارات تنسيق غنية:** التحكم في الخط، الحجم، الدوران، الشفافية، وتغيير الحجم.  
- **محسن للأداء:** يتعامل مع دفاتر عمل كبيرة بكفاءة، خاصةً عند إغلاق `Watermarker` بسرعة.  
- **سهولة التكامل:** اعتماد Maven بسيط واستدعاءات API مباشرة.

## المتطلبات المسبقة
- **مجموعة تطوير جافا (JDK):** الإصدار 8 أو أعلى.  
- **بيئة التطوير المتكاملة (IDE):** IntelliJ IDEA أو Eclipse أو أي محرر متوافق مع Java.  
- **Maven:** لإدارة الاعتمادات.  
- **GroupDocs.Watermark للغة Java:** الإصدار 24.11 (أو أحدث إصدار).  

## إعداد GroupDocs.Watermark للغة Java

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
إذا كنت تفضل عدم استخدام Maven، احصل على أحدث ملف JAR من [إصدارات GroupDocs.Watermark للغة Java](https://releases.groupdocs.com/watermark/java/).

#### خطوات الحصول على الترخيص
1. **تجربة مجانية:** ابدأ بتجربة لمدة 30 يومًا لاستكشاف الميزات.  
2. **ترخيص مؤقت:** احصل على مفتاح قصير الأجل من موقع GroupDocs إذا لزم الأمر.  
3. **الشراء:** احصل على ترخيص كامل عبر [شراء GroupDocs](https://purchase.groupdocs.com/) للمشاريع المستمرة.

### التهيئة الأساسية
استورد الفئة الأساسية قبل البدء:

```java
import com.groupdocs.watermark.Watermarker;
```

## دليل التنفيذ

### إضافة علامة مائية سرية إلى Excel (الخطوة 1: تحميل جدول البيانات)
أولاً، قم بتحميل دفتر العمل الخاص بك باستخدام `SpreadsheetLoadOptions` وأنشئ كائن `Watermarker`.

```java
// Load options for the spreadsheet file
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### إنشاء وتكوين علامة مائية نصية (الخطوة 2)
حدد نص العلامة المائية، الخط، والخصائص البصرية. هنا حيث **تطبق إعدادات العلامة المائية الخلفية على Excel**.

```java
// Create and configure the text watermark
TextWatermark watermark = new TextWatermark("Confidential", new Font("Segoe UI", 19));
watermark.setHorizontalAlignment(HorizontalAlignment.Center); // Center horizontally
watermark.setVerticalAlignment(VerticalAlignment.Center); // Center vertically
watermark.setRotateAngle(45); // Rotate by 45 degrees
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scale to fit dimensions
watermark.setScaleFactor(0.5); // Set scaling factor
watermark.setOpacity(0.5); // Define opacity
```

### الحصول على محتوى جدول البيانات وتعيين خيارات الخلفية (الخطوة 3)
استرجع أبعاد ورقة العمل بحيث تغطي العلامة المائية كامل الورقة.

```java
// Get spreadsheet content and define background options
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
SpreadsheetBackgroundWatermarkOptions options = new SpreadsheetBackgroundWatermarkOptions();
options.setBackgroundWidth(content.getWorksheets().get_Item(0).getContentAreaWidthPx());
options.setBackgroundHeight(content.getWorksheets().get_Item(0).getContentAreaHeightPx());
```

### إضافة العلامة المائية (الخطوة 4)
طبق العلامة المائية المكوّنة كطبقة خلفية.

```java
// Add watermark to the spreadsheet as a background
watermarker.add(watermark, options);
```

### حفظ وإغلاق (الخطوة 5)
احفظ التغييرات في ملف جديد وأطلق الموارد.

```java
// Save the modified spreadsheet
current watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_with_watermark.xlsx");

// Close the Watermarker instance
watermarker.close();
```

## نصائح استكشاف الأخطاء وإصلاحها
- **الاعتمادات المفقودة:** تحقق مرة أخرى من ملف `pom.xml` للتأكد من صحة مجموعة ومعرف الأداة.  
- **أخطاء الترخيص:** تأكد من وضع ملف الترخيص (`GroupDocs.Watermark.lic`) في جذر المشروع أو توفيره عبر `License.setLicense`.  
- **التحجيم غير الصحيح:** إذا ظهرت العلامة المائية صغيرة جدًا أو كبيرة جدًا، عدّل `setScaleFactor` أو استخدم `SizingType.FitToParentDimensions`.

## تطبيقات عملية
1. **أمان المستندات:** وضع علامة سرية على نماذج مالية أو بيانات الموارد البشرية.  
2. **الوعي بالعلامة التجارية:** وضع شعارات الشركة أو شعاراتها عبر التقارير المشتركة.  
3. **سجل التدقيق:** تضمين تواريخ الإنشاء أو أرقام الإصدارات مباشرةً في الورقة.  
4. **وضوح التعاون:** الإشارة بوضوح إلى الملكية عند تبادل الملفات بين فرق متعددة.

## اعتبارات الأداء
- **إدارة الذاكرة:** دائمًا استدعِ `watermarker.close()` بعد الحفظ لتحرير الموارد الأصلية.  
- **المعالجة الدفعية:** تكرار عبر قائمة من الملفات، وإعادة استخدام كائن `Watermarker` واحد حيثما أمكن لتقليل الحمل.  
- **عوامل التحجيم:** بالنسبة لدفاتر عمل كبيرة جدًا، يمكن أن يؤدي `setScaleFactor` أقل (مثلاً 0.3) إلى تحسين سرعة العرض دون التضحية بالقراءة.

## الخلاصة
أصبح لديك الآن حل كامل وجاهز للإنتاج لـ **كيفية وضع علامة مائية على ملفات Excel** باستخدام GroupDocs.Watermark للغة Java. باتباع الخطوات أعلاه، يمكنك حماية جداول البيانات الحساسة، تعزيز العلامة التجارية، والحفاظ على سجل تدقيق بأقل قدر من الشيفرة.

**الخطوات التالية**
- جرّب خطوطًا، ألوانًا، وزوايا دوران مختلفة.  
- استكشف العلامات المائية الصورية للحصول على نهج بصري أكثر للعلامة التجارية.  
- دمج هذه العملية في خط أنابيب إنشاء المستندات الحالي الخاص بك.

## الأسئلة المتكررة

**س: ما هو استخدام GroupDocs.Watermark Java؟**  
ج: إنها مكتبة لإضافة علامات مائية—نصية أو صور— إلى مجموعة واسعة من أنواع المستندات، بما في ذلك دفاتر عمل Excel.

**س: كيف أضمن ظهور العلامة المائية بشكل صحيح عبر الأجهزة المختلفة؟**  
ج: استخدم خيارات التحجيم والمحاذاة المتوفرة في `SpreadsheetBackgroundWatermarkOptions` لتتكيف مع اختلاف دقة الشاشات.

**س: هل يمكن لـ GroupDocs.Watermark التعامل مع الملفات الكبيرة بكفاءة؟**  
ج: نعم، تم تحسين API للأداء، لكن يُنصح بمراقبة استهلاك الذاكرة أثناء العمليات الدفعية.

**س: هل هناك حد لعدد العلامات المائية التي يمكنني إضافتها؟**  
ج: لا يوجد حد صريح، إلا أن إضافة العديد من الطبقات قد يؤثر على زمن المعالجة وحجم الملف.

**س: كيف أستكشف الأخطاء الشائعة في وضع العلامات المائية باستخدام Java؟**  
ج: تحقق من اعتماديات Maven، تأكد من الإشارة الصحيحة إلى ملف الترخيص، واستشر الوثائق الرسمية لأكواد الأخطاء.

---

**آخر تحديث:** 2026-03-22  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 للغة Java  
**المؤلف:** GroupDocs  

## الموارد

- **الوثائق:** [توثيق GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)  
- **مرجع API:** [مرجع GroupDocs API](https://reference.groupdocs.com/watermark/java)  
- **التنزيل:** [تنزيلات GroupDocs](https://releases.groupdocs.com/watermark/java/)  
- **GitHub:** [مستودع GroupDocs على GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **دعم مجاني:** [منتدى GroupDocs](https://forum.groupdocs.com/c/watermark/10)  
- **ترخيص مؤقت:** [ترخيص GroupDocs المؤقت](https://purchase.groupdocs.com/temporary-license/)