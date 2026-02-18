---
date: '2026-02-18'
description: تعلم كيفية إضافة العلامة المائية وكيفية إزالتها في ملفات المخططات مثل
  .vsdx باستخدام GroupDocs.Watermark للغة Java. احمِ سلامة المستند باستخدام GroupDocs
  Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: كيفية إضافة علامة مائية إلى المخططات باستخدام GroupDocs.Watermark لجافا
type: docs
url: /ar/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

 careful to preserve code block placeholders exactly.

Also ensure no extra spaces that might break formatting.

Proceed to produce final answer.# كيفية إضافة علامة مائية إلى المخططات باستخدام GroupDocs.Watermark للـ Java

إدارة العلامات المائية في ملفات المخططات هي جزء أساسي من حماية الملكية الفكرية والحفاظ على نظافة المستندات للتوزيع العام. في هذا الدليل ستتعلم **كيفية إضافة علامة مائية** إلى مخطط Visio، وكذلك **كيفية إزالة العلامة المائية** عندما لا تكون بحاجة إليها، كل ذلك باستخدام مكتبة **groupdocs watermark java**. سواء كنت تبني خط أنابيب مستندات على مستوى المؤسسة أو سكريبت أداة سريع، ستمنحك هذه الخطوات السيطرة الكاملة على وضع العلامات المائية في المخططات.

## إجابات سريعة
- **ما هي المكتبة التي تتعامل مع علامات مائية للمخططات في Java؟** GroupDocs.Watermark for Java.  
- **هل يمكنني إضافة وإزالة العلامات المائية في نفس التشغيل؟** نعم – حمّل المخطط مرة واحدة وطبق عمليات الإضافة والإزالة معًا.  
- **ما هي صيغ الملفات المدعومة؟** صيغ Visio مثل `.vsdx`، `.vdx`، بالإضافة إلى أنواع مخططات أخرى.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي يعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.

## ما هو “كيفية إضافة علامة مائية” في سياق المخططات؟
إضافة علامة مائية تعني تضمين علامة مرئية أو غير مرئية — نص، شعار أو صورة — داخل ملف المخطط. هذه العلامة تنتقل مع الملف، مما يجعل من السهل إثبات الملكية أو الإشارة إلى إصدارات مسودة.

## لماذا تستخدم GroupDocs.Watermark للـ Java؟
* **Rich API** – البحث، الإضافة، والحذف لكل من العلامات النصية والصورية ببضع أسطر من الشيفرة.  
* **Cross‑format support** – يعمل مع Visio (`.vsdx`, `.vdx`) والعديد من أنواع المخططات الأخرى.  
* **Performance‑focused** – يحمل فقط الأجزاء المطلوبة من المخطط لعمليات العلامة المائية، مما يحافظ على انخفاض استهلاك الذاكرة.

## المتطلبات المسبقة
1. **Java Development Kit (JDK) 8+** – تأكد من أن `java -version` يعرض 1.8 أو أحدث.  
2. **IDE** – IntelliJ IDEA، Eclipse، أو أي محرر تفضله.  
3. **GroupDocs.Watermark for Java** – أضفه إلى مشروعك عبر Maven أو تحميل JAR مباشر.  

### المكتبات والاعتمادات المطلوبة
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

*إذا كنت تفضل عدم استخدام Maven، يمكنك تنزيل أحدث JAR من [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### الحصول على الترخيص
- **Free Trial:** اختبار جميع الميزات بدون مفتاح ترخيص.  
- **Temporary License:** طلب مفتاح مؤقت لتقييم المنتج.  
- **Full License:** شراء اشتراك للاستخدام غير المقيد في بيئة الإنتاج.

## إعداد GroupDocs.Watermark للـ Java
1. **Add the library** إلى مشروعك (Maven أو JAR يدوي).  
2. **Create a `Watermarker` instance** – هذا الكائن هو نقطة الدخول لتحميل المخططات، البحث، الإضافة، وإزالة العلامات المائية.

## دليل التنفيذ

### تحميل مستند مخطط
التحميل هو الخطوة الأولى قبل أن تتمكن من **إضافة علامة مائية** أو **إزالة العلامة المائية**. الشيفرة أدناه توضح كيفية فتح ملف `.vsdx` مع خيارات تحميل مخصصة.

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

### البحث عن علامات مائية نصية
قبل أن تضيف علامة مائية جديدة، قد ترغب في التحقق مما إذا كانت علامة مائية نصية موجودة بالفعل. هذا المقتطف يبحث عن العبارة “Company Name”.

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

### البحث عن علامات مائية صور
إذا كنت بحاجة إلى تحديد موقع شعار أو أي صورة استُخدمت كعلامة مائية، استخدم `ImageDctHashSearchCriteria`. هذا مفيد عندما تريد **إزالة العلامة المائية** التي تطابق شعارًا معروفًا.

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

### إزالة العلامات المائية
بمجرد أن تحدد العلامات المائية — نصية، صورية، أو كليهما — يمكنك مسحها من المخطط. المثال أدناه يوضح عملية إزالة مركبة.

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

## التطبيقات العملية
1. **Enterprise Software Integration** – دمج إدارة العلامات المائية في نظام ERP أو منصة توليد المستندات لتطبيق العلامة التجارية.  
2. **Content Management Systems (CMS)** – فحص المخططات المرفوعة تلقائيًا للبحث عن شعارات غير مصرح بها وإزالتها.  
3. **Legal Document Handling** – إضافة علامة مائية نصية “Confidential” خلال مراحل المسودة ثم **إزالة العلامة المائية** قبل الإيداع النهائي.

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لم يتم العثور على أي علامات مائية | نص/صورة البحث لا يتطابق تمامًا | استخدم `or()` لدمج المعايير أو عدّل إعدادات حساسية الحالة. |
| `OutOfMemoryError` على ملفات كبيرة | تم تحميل المخطط بالكامل في الذاكرة | استخدم `DiagramLoadOptions.setLoadPages()` لتحميل الصفحات المطلوبة فقط. |
| الملف المحفوظ تالف | تم استدعاء `watermarker.save()` قبل مسح جميع العلامات المائية | تأكد من إكمال `possibleWatermarks.clear()` واستدعاء `watermarker.close()` بعد الحفظ. |

## الأسئلة المتكررة

**س: هل يمكنني البحث عن كل من النصوص والصور في آنٍ واحد؟**  
ج: نعم. دمج `TextSearchCriteria` و `ImageDctHashSearchCriteria` باستخدام طريقة `or()`، كما هو موضح في مثال الإزالة.

**س: هل من الممكن إزالة العلامات المائية دون الإضرار بالمخطط؟**  
ج: بالتأكيد. المكتبة تعزل كائنات العلامة المائية، لذا استدعاء `clear()` يزيل فقط طبقات العلامة المائية مع الحفاظ على محتوى المخطط الأصلي.

**س: هل يدعم GroupDocs.Watermark صيغ مخططات متعددة؟**  
ج: نعم. صيغ مثل `.vsdx`، `.vdx` وغيرها من الملفات المتوافقة مع Visio مدعومة بالكامل.

**س: كيف يمكنني التعامل مع حجم كبير من المستندات بكفاءة؟**  
ج: نفّذ حلقات معالجة دفعات، أعد استخدام كائن `Watermarker` واحد حيثما أمكن، وحدد تحميل الصفحات باستخدام `DiagramLoadOptions`.

**س: هل هناك طريقة لأتمتة اكتشاف العلامات المائية في خط أنابيب CI/CD؟**  
ج: يمكنك دمج مقتطفات Java المقدمة في سكريبتات البناء (مثل Maven أو Gradle) للتحقق من عدم وجود علامات مائية غير مصرح بها قبل إصدار القطع البرمجية.

---

**آخر تحديث:** 2026-02-18  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs