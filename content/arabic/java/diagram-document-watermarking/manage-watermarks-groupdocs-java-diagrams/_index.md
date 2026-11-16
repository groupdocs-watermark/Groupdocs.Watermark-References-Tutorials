---
date: '2025-12-19'
description: تعلم كيفية استخدام GroupDocs Watermark Maven لإدارة العلامات المائية
  في ملفات المخططات مثل .vsdx باستخدام Java، مما يعزز سلامة المستندات ويحمي الملكية
  الفكرية.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – إدارة العلامات المائية للمخططات باستخدام Java
type: docs
url: /ar/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – إدارة علامات مائية للرسوم البيانية باستخدام Java

إدارة العلامات المائية في المستندات أمر أساسي لحماية الملكية الفكرية والحفاظ على سلامة المستند. **في هذا الدرس سنوضح لك كيفية استخدام groupdocs watermark maven لتحميل، البحث، وإزالة العلامات المائية من ملفات الرسوم البيانية مثل `.vsdx`**. سواءً كنت تبني برنامجًا مؤسسيًا أو تقوم بأتمتة سير عمل المستندات، ستمكنك إتقان هذه التقنيات من التحكم الكامل في إدارة العلامات المائية للرسوم البيانية.

## إجابات سريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark for Java (متاحة عبر Maven).  
- **ما صيغ الرسوم البيانية المدعومة؟** `.vsdx`، `.vdx`، وغيرها من صيغ Visio.  
- **هل يمكنني البحث عن كل من العلامات النصية والصورية؟** نعم – اجمع معايير البحث باستخدام `or()`.  
- **هل تحتاج إلى ترخيص للإنتاج؟** يتطلب ترخيص صالح من GroupDocs.Watermark.  
- **كيف أدمج ذلك في Maven؟** أضف المستودع والاعتماد الموضحين أدناه.

## ما هو groupdocs watermark maven؟
`groupdocs watermark maven` يشير إلى التكامل القائم على Maven لمكتبة GroupDocs.Watermark للغة Java. من خلال إعلان المكتبة في ملف `pom.xml` الخاص بك، يقوم Maven تلقائيًا بحل جميع الثنائيات المطلوبة، مما يتيح لك التركيز على الكود الذي يحمل الرسوم البيانية، يبحث عن العلامات المائية، ويزيلها برمجيًا.

## لماذا نستخدم GroupDocs.Watermark لإدارة العلامات المائية للرسوم البيانية؟
- **API كامل الميزات** – يدعم العلامات النصية، الصورية، والشكلية عبر العديد من أنواع الرسوم البيانية.  
- **إزالة دقيقة** – يزيل العلامات المائية دون إفساد تخطيط الرسم الأصلي.  
- **قابلية التوسع** – مناسب للمعالجة الدفعة لمجموعات كبيرة من الرسوم البيانية.  
- **ملائم لـ Maven** – إدارة تبعيات بسيطة، تحافظ على نظافة مشروعك.

## المتطلبات المسبقة
1. **مجموعة تطوير جافا (JDK) 8+** – لضمان التوافق مع المكتبة.  
2. **بيئة تطوير متكاملة (IDE)** – IntelliJ IDEA، Eclipse، أو أي محرر يدعم Java.  
3. **GroupDocs.Watermark for Java** – يُضاف عبر Maven (مُفضَّل) أو تحميل JAR مباشر.  

### المكتبات والاعتمادات المطلوبة
#### إعداد Maven
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

#### التحميل المباشر
بدلاً من ذلك، حمّل أحدث نسخة من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### الحصول على الترخيص
- **تجربة مجانية:** اختبر المكتبة باستخدام ترخيص تجريبي.  
- **ترخيص مؤقت:** اطلب مفتاحًا قصير الأمد للتقييم.  
- **شراء:** احصل على ترخيص إنتاج لاستخدام غير محدود.

## استخدام groupdocs watermark maven لتحميل مستند رسم بياني
تحميل مستند الرسم البياني هو الخطوة الأولى قبل أي عملية علامة مائية. المثال الأدنى يوضح إنشاء كائن `Watermarker` باستخدام `DiagramLoadOptions`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

- **المعلمات:**  
  - `inputFilePath` – مسار ملف `.vsdx` الخاص بك.  
  - `loadOptions` – يتيح لك التحكم في طريقة تحليل الرسم (مثل الحماية بكلمة مرور).

## البحث عن العلامات المائية باستخدام groupdocs watermark maven
### العلامات النصية
لتحديد العلامات المائية النصية، عرّف `TextSearchCriteria` واستعلم عن الصفحة الأولى من الرسم.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

- **الطرق الأساسية:**  
  - `TextSearchCriteria` – يحدد النص الدقيق للبحث عنه.  
  - `PossibleWatermarkCollection` – يخزن أي تطابقات تم العثور عليها.

### العلامات الصورية
إذا كان الرسم يحتوي على شعارات أو صور كعلامات مائية، استخدم `ImageDctHashSearchCriteria` للمقارنة مع صورة مرجعية.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

- **الطرق الأساسية:**  
  - `ImageDctHashSearchCriteria` – يُنشئ تجزئة إدراكية (perceptual hash) للصورة المرجعية لتطابق قوي.

## إزالة العلامات المائية
بعد تحديد العلامات غير المرغوب فيها، يمكنك مسحها وحفظ نسخة نظيفة من الرسم.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

- **الطريقة الأساسية:** `clear()` يزيل كل علامة مائية تم العثور عليها بالمعايير المدمجة، مع الحفاظ على الرسم دون تعديل.

## تطبيقات عملية
1. **تكامل برامج مؤسسية** – دمج إدارة العلامات المائية في تطبيقات الأعمال لحماية الرسوم البيانية المملوكة.  
2. **أنظمة إدارة المحتوى (CMS)** – أتمتة اكتشاف وإزالة الشعارات غير المصرح بها قبل النشر.  
3. **سير عمل المستندات القانونية** – إضافة أو إزالة العلامات المائية في مراحل مختلفة من معالجة العقود.  

## المشكلات الشائعة & استكشاف الأخطاء
- **أخطاء الترخيص:** تأكد من الإشارة إلى ملف الترخيص بشكل صحيح قبل إنشاء كائن `Watermarker`.  
- **الملفات الكبيرة:** استخدم واجهات برمجة التطبيقات المتدفقة أو زد حجم ذاكرة JVM (`-Xmx2g`) للرسوم التي يزيد حجمها عن 100 ميغابايت.  
- **عدم العثور على العلامات:** تحقق من أن معايير البحث (حالة النص، عتبة تشابه الصورة) تتطابق مع محتوى العلامة المائية الفعلي.

## الأسئلة المتكررة

**س: هل يمكنني البحث عن النصوص والصور في آنٍ واحد؟**  
ج: نعم. اجمع المعايير باستخدام `or()` كما هو موضح في مثال الإزالة.

**س: هل من الآمن إزالة العلامات المائية دون تعديل تخطيط الرسم؟**  
ج: بالتأكيد. تستهدف الـ API كائنات العلامة المائية بدقة، مع الحفاظ على جميع عناصر الرسم الأخرى.

**س: ما صيغ الرسوم البيانية التي يدعمها GroupDocs.Watermark؟**  
ج: يدعم صيغ Visio مثل `.vsdx`، `.vdx`، بالإضافة إلى أنواع أخرى من الرسوم المتجهية.

**س: كيف يمكنني معالجة مئات الرسوم البيانية بكفاءة؟**  
ج: نفّذ حلقة دفعة، أعد استخدام كائن `Watermarker` واحد عندما يكون ذلك ممكنًا، وفكّر في المعالجة المتوازية باستخدام `ExecutorService` في Java.

**س: هل يمكن دمج اكتشاف العلامات المائية في خط أنابيب CI/CD؟**  
ج: نعم. أدرج مقتطفات Java في سكريبتات البناء (مثل إضافات Maven أو مهام Gradle) للتحقق من الرسوم البيانية قبل النشر.

## الخلاصة
باستخدام **groupdocs watermark maven**، تحصل على طريقة قوية تُدار عبر Maven لتحميل، البحث، وإزالة العلامات المائية من ملفات الرسوم البيانية باستخدام Java. هذه القدرة تعزز أمان المستندات، تُبسط سير عمل المحتوى، وتُقابل بسهولة مجموعات كبيرة من المستندات.

---

**آخر تحديث:** 2025-12-19  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs  

---