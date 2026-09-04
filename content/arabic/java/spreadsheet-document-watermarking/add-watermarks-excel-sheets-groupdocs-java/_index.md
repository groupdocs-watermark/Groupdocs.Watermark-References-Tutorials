---
date: '2026-03-25'
description: تعلم كيفية إضافة علامة مائية إلى جداول Excel باستخدام GroupDocs.Watermark
  للغة Java، بما في ذلك إضافة علامة مائية نصية إلى Excel وخيارات الصورة، لتأمين مستنداتك.
keywords:
- add watermark to excel
- remove watermark from excel
- add text watermark excel
- confidential watermark excel
title: إضافة علامة مائية إلى أوراق إكسل باستخدام جافا وGroupDocs.Watermark
type: docs
url: /ar/java/spreadsheet-document-watermarking/add-watermarks-excel-sheets-groupdocs-java/
weight: 1
---

# إضافة علامة مائية إلى أوراق Excel باستخدام Java و GroupDocs.Watermark

في بيئة الأعمال سريعة الحركة اليوم، **إضافة علامة مائية إلى Excel** ملفات هي طريقة بسيطة لكنها قوية لحماية البيانات الحساسة، وإثبات الملكية، وتعزيز العلامة التجارية. سواء كنت بحاجة إلى **علامة مائية سرية لExcel** للتقارير الداخلية أو تغطية شعار لدفاتر العمل الموجهة للعملاء، فإن GroupDocs.Watermark for Java يجعل العملية مباشرة. في هذا الدليل سنستعرض إعداد المكتبة، وإضافة كل من العلامات المائية النصية والصورية، وحتى نتطرق إلى كيفية **إزالة العلامة المائية من Excel** إذا دعت الحاجة.

## إجابات سريعة
- **ما هي المكتبة الأفضل لإضافة علامة مائية إلى Excel في Java؟** GroupDocs.Watermark for Java.  
- **هل يمكنني إضافة علامة مائية نصية تقول “سرية”?** نعم – فقط أنشئ `TextWatermark` بالنص المطلوب.  
- **هل يمكن وضع شعار على ورقة عمل محددة؟** بالتأكيد؛ استخدم `ImageWatermark` وحدد فهرس ورقة العمل.  
- **هل أحتاج إلى ترخيص للاستخدام الإنتاجي؟** الترخيص الكامل يفتح جميع الميزات؛ ترخيص التجربة يعمل للتقييم.  
- **هل ستؤثر دفاتر العمل الكبيرة على الأداء؟** قم بتحسين حجم الصورة وأغلق الموارد بسرعة للحفاظ على استهلاك الذاكرة منخفضًا.  

## ما هي “إضافة علامة مائية إلى Excel”؟
إضافة علامة مائية تعني دمج طبقة نصية أو صورية شبه شفافة داخل دفتر Excel بحيث تظهر على كل صفحة مطبوعة أو في العرض على الشاشة. هذه الإشارة البصرية تساعد على ردع التوزيع غير المصرح به وتوضح بوضوح مستوى سرية المستند.

## لماذا نستخدم GroupDocs.Watermark for Java؟
- **متعدد المنصات** – يعمل على أي نظام تشغيل يدعم Java.  
- **تحكم دقيق** – استهدف أوراق عمل فردية، واضبط الدوران، والشفافية، والموضع.  
- **أداء عالي** – مصمم لملفات Excel الكبيرة مع استهلاك ذاكرة منخفض.  
- **API غني** – يدعم العلامات المائية النصية، الصورية، وحتى الأشكال المخصصة.  

## المتطلبات المسبقة
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- **GroupDocs.Watermark for Java** (الإصدار 24.11 أو أحدث).  
- **Java Development Kit (JDK)** 8 أو أعلى.  
- بيئة تطوير متكاملة (IDE) مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية ببرمجة Java.  

## إعداد GroupDocs.Watermark for Java
البدء مع GroupDocs.Watermark في مشروع Java الخاص بك يتضمن بضع خطوات بسيطة. إليك كيفية إعداده باستخدام Maven:

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

بدلاً من ذلك، يمكنك تنزيل أحدث نسخة مباشرةً من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
يمكنك البدء بتجربة مجانية عن طريق تنزيل ترخيص مؤقت أو شراء ترخيص كامل لفتح جميع الميزات. اتبع التعليمات المتوفرة على موقعهم للحصول على الترخيص.

بمجرد أن تكون كل الأشياء جاهزة، قم بتهيئة GroupDocs.Watermark في مشروع Java الخاص بك:

```java
import com.groupdocs.watermark.Watermarker;

// Initialize Watermarker with your document
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx");
```

## كيفية إضافة علامة مائية إلى أوراق Excel – دليل خطوة بخطوة

### إضافة علامة مائية نصية إلى ورقة عمل
غالبًا ما تستخدم **علامة مائية سرية لExcel** نصًا غامقًا مثل “سرية” أو “عدم التوزيع”. أدناه سير العمل الكامل.

#### الخطوة 1: تحميل مستند الجدول
```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

#### الخطوة 2: إنشاء علامة مائية نصية
```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 12));
textWatermark.setRotateAngle(-45);
```
*نصيحة احترافية:* اضبط زاوية الدوران لجعل العلامة المائية بارزة دون إخفاء البيانات.

#### الخطوة 3: تكوين العلامة المائية لورقة محددة
```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkShapeOptions;

SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setWorksheetIndex(0); // Apply to the first worksheet

watermarker.add(textWatermark, options);
```

#### الخطوة 4: حفظ وإطلاق الموارد
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close();
textWatermark.close();
```

### إضافة علامة مائية صورية إلى ورقة عمل
العلامات المائية الصورية رائعة للعلامة التجارية—فكر في شعارات الشركة أو الأختام.

#### الخطوة 1: تحميل مستند الجدول
(أعد استخدام `SpreadsheetLoadOptions` من قسم العلامة المائية النصية.)

#### الخطوة 2: إنشاء علامة مائية صورية
```java
import com.groupdocs.watermark.watermarks.ImageWatermark;

ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.5);
```
ضبط الشفافية إلى 0.5 يحافظ على قابلية قراءة البيانات الأساسية.

#### الخطوة 3: تكوين العلامة المائية للورقة المطلوبة
```java
SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setWorksheetIndex(1); // Apply to the second worksheet

watermarker.add(imageWatermark, options);
```

#### الخطوة 4: حفظ وإطلاق الموارد
أعد استخدام خطوات الحفظ والإغلاق الموضحة سابقًا.

## حالات الاستخدام الشائعة
- **تقارير سرية** – أضف **علامة مائية سرية لExcel** إلى البيانات المالية.  
- **تعزيز العلامة التجارية** – دمج شعارك في كل دفتر عمل موجه للعملاء.  
- **تتبع المستند** – تضمين علامة مائية بمعرف فريد لتتبع التوزيع.  

## كيفية إزالة العلامة المائية من Excel (إذا لزم الأمر)
يوفر GroupDocs.Watermark أيضًا واجهة برمجة تطبيقات للإزالة. يمكنك تحميل دفتر العمل، استدعاء `watermarker.removeAll()` أو استهداف أشكال محددة، ثم حفظ الملف النظيف. تذكر عمل نسخة احتياطية من الأصل قبل الإزالة.

## نصائح الأداء
- **تحسين حجم الصورة** – PNG أصغر يحمل أسرع.  
- **إغلاق الكائنات بسرعة** – `watermarker.close()` يحرر الموارد الأصلية.  
- **المعالجة الدفعية** – تكرار عبر مجلد من دفاتر العمل لتطبيق العلامات المائية بالجملة.  

## الأسئلة المتكررة

**س: هل يمكنني إضافة علامات مائية إلى جميع أوراق العمل في دفتر؟**  
ج: نعم، قم بالتكرار على فهرس كل ورقة عمل وطبق العلامة المائية داخل حلقة.

**س: هل يمكن تغيير موضع العلامة المائية؟**  
ج: بالتأكيد! اضبط معلمات مثل `setX` و `setY` في خيارات الشكل للحصول على وضعية دقيقة.

**س: كيف يمكنني التعامل مع ملفات Excel الكبيرة بكفاءة؟**  
ج: فكر في تقسيم دفتر العمل إلى أجزاء أصغر أو استخدام صور منخفضة الدقة لتقليل استهلاك الذاكرة.

**س: ما هي صيغ الملفات التي يدعمها GroupDocs.Watermark؟**  
ج: بالإضافة إلى Excel، تدعم المكتبة ملفات PDF، مستندات Word، عروض PowerPoint، وصيغ الصور الشائعة.

**س: هل يمكنني إزالة العلامات المائية بعد إضافتها؟**  
ج: نعم، تشمل API طرق الإزالة، لكن كن حذرًا لتجنب حذف المحتوى المهم عن غير قصد.

## الموارد
- **التوثيق**: [GroupDocs.Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)
- **دليل مرجع API**: [API Reference Guide](https://reference.groupdocs.com/watermark/java)
- **تحميل GroupDocs**: [Download Latest Version](https://releases.groupdocs.com/watermark/java/)
- **مستودع GitHub**: [GroupDocs.Watermark for Java on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **منتدى الدعم**: [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- **ترخيص مؤقت**: [Acquire a Temporary License](https://purchase.groupdocs.com/temporary-license/)

باتباعك هذا الدليل، لديك الآن أساس قوي لـ **إضافة علامة مائية إلى ملفات Excel**، حماية البيانات الحساسة، وتعزيز علامتك التجارية—كل ذلك ببضع أسطر من كود Java. نتمنى لك إضافة علامات مائية سعيدة!

---

**آخر تحديث:** 2026-03-25  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs