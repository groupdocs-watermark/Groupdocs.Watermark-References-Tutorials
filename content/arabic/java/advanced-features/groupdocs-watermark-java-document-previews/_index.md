---
date: '2025-12-16'
description: تعلم كيفية معاينة المستندات باستخدام GroupDocs.Watermark للغة Java، وتوليد
  الصور المصغرة بسهولة مع تكامل Maven لـ GroupDocs Watermark.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 'كيفية معاينة المستندات باستخدام GroupDocs.Watermark في جافا: دليل متقدم'
type: docs
url: /ar/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# كيفية معاينة المستندات باستخدام GroupDocs.Watermark في Java: دليل متقدم

## المقدمة

في هذا الدليل، ستتعلم **كيفية معاينة المستندات** بكفاءة باستخدام مكتبة GroupDocs.Watermark للـ Java. إنشاء معاينات المستندات هو ميزة حاسمة للتطبيقات التي تدير كميات كبيرة من الملفات، مما يسمح للمستخدمين بإلقاء نظرة سريعة على المحتوى دون فتح المستند بالكامل. باتباع الخطوات أدناه، ستتعرف أيضًا على كيفية **java generate thumbnail** وإنشاء صور مصغرة وتكامل المكتبة عبر **maven groupdocs watermark**. لنبدأ بإعداد بيئة التطوير الخاصة بك.

## إجابات سريعة

- **ما هو الهدف الأساسي؟** إنشاء معاينات خفيفة الوزن صفحة‑بصفحة (thumbnails) لأي مستند مدعوم.  
- **ما المكتبة المطلوبة؟** GroupDocs.Watermark for Java (الإصدار 24.11).  
- **كيف يمكنني إضافة المكتبة؟** استخدم مقتطف Maven المقدم في قسم الإعداد.  
- **هل يمكنني إنشاء معاينات لجميع الصفحات؟** نعم – الـ API يبث كل صفحة إلى ملف صورة.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية تعمل للاختبار الأساسي؛ الترخيص الكامل مطلوب للاستخدام في الإنتاج.  

## ما هو إنشاء معاينة المستند؟

يقوم إنشاء معاينة المستند بتحويل كل صفحة من ملف المصدر (PDF، DOCX، VDX، إلخ) إلى تنسيق صورة مثل PNG. تعمل هذه الصور المعاينة كـ thumbnails يمكن عرضها في مستعرضات الملفات، البوابات الإلكترونية، أو تطبيقات الهواتف المحمولة، مما يحسن تجربة المستخدم بشكل كبير ويقلل من أوقات التحميل.

## لماذا نستخدم GroupDocs.Watermark للـ Java؟

- **السرعة والقابلية للتوسع** – الكود الأصلي المُحسّن يتعامل مع المستندات الكبيرة بسرعة.  
- **دعم صيغ واسع** – يعمل مع أكثر من 100 نوع ملف مباشرة.  
- **العلامة المائية المدمجة** – يمكنك إضافة علامات مائية أثناء إنشاء المعاينات، مما يحافظ على حماية أصولك.  
- **API بسيط** – يتطلب القليل من الكود لإنتاج thumbnails عالية الجودة.  

## المتطلبات المسبقة

1. **Java Development Kit (JDK)** – JDK 8 أو أحدث مثبت.  
2. **IDE** – IntelliJ IDEA، Eclipse، أو أي محرر تفضله.  
3. **Maven** – لإدارة التبعيات (انظر إعداد Maven أدناه).  
4. **معرفة أساسية بـ Java** – الإلمام بملفات الإدخال/الإخراج والبرمجة الكائنية.  

## إعداد GroupDocs.Watermark للـ Java

لبدء استخدام GroupDocs.Watermark في مشروعك، أضفه كاعتماد Maven:

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

بدلاً من ذلك، يمكنك تنزيل أحدث JAR مباشرةً من صفحة الإصدار الرسمية:

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### الحصول على الترخيص

- **نسخة تجريبية مجانية** – اختبار المكتبة بوظائف محدودة.  
- **ترخيص مؤقت** – الحصول على مفتاح قصير الأمد لتقييم كامل الميزات.  
- **ترخيص كامل** – الشراء للاستخدام غير المحدود والدعم ذو الأولوية.  

## دليل التنفيذ

### تهيئة Watermarker

#### نظرة عامة
الخطوة الأولى هي إنشاء كائن `Watermarker` يشير إلى المستند المصدر.

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

*نقطة رئيسية:* استبدل `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` بالمسار الفعلي للملف الذي تريد معاينته.

### إنشاء تدفق صفحة لإنشاء المعاينة

#### نظرة عامة
مُنشئ تدفق مخصص يُخبر الـ API أين يكتب صورة المعاينة لكل صفحة.

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

يستخدم `fileNameTemplate` عنصرًا نائبًا (`%s`) يقوم الـ API باستبداله برقم الصفحة الحالي، مما ينتج ملفات مثل `page1.png`، `page2.png`، إلخ.

### تحرير تدفق الصفحة

#### نظرة عامة
بعد كتابة صورة المعاينة، يجب إغلاق التدفق لتحرير موارد النظام.

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

تحرير التدفقات بشكل صحيح يمنع تسرب الذاكرة، خاصةً عند معالجة دفعات كبيرة من المستندات.

### إنشاء معاينة المستند

#### نظرة عامة
مع وجود `Watermarker`، ومُنشئ التدفق، ومعالج التحرير جاهزين، يمكنك إنشاء معاينات لكل صفحة.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

*شرح الكائنات الرئيسية:*  
- `createPageStream` – يحدد مكان حفظ كل ملف PNG.  
- `releasePageStream` – يضمن إغلاق مقبض الملف بعد الكتابة.  
- `previewOptions` – يجمع المعالجين معًا لاستدعاء `generatePreview`.  

## التطبيقات العملية

إنشاء معاينات المستندات مفيد في العديد من السيناريوهات الواقعية:

1. **تطبيقات عارض PDF** – عرض أشرطة thumbnails دون تحميل ملف PDF بالكامل.  
2. **أنظمة إدارة المحتوى (CMS)** – تمكين المحررين من تصفح المستندات بسرعة.  
3. **خدمات التخزين السحابي** – توفير thumbnails مرئية للملفات المخزنة، مما يحسن التنقل.  

## اعتبارات الأداء

- **إدارة الذاكرة** – استخدم نمط تحرير التدفق الموضح أعلاه للحفاظ على استهلاك الذاكرة منخفضًا.  
- **تحسين الإدخال/الإخراج** – يمكن أن تقلل التدفقات المخبأة من زمن استجابة القرص عند معالجة آلاف الصفحات.  
- **المعالجة المتوازية** – للعمليات الضخمة، فكر في معالجة مستندات متعددة بشكل متزامن باستخدام `ExecutorService` في Java.  

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|-------|-----|
| لم يتم إنشاء ملفات المعاينة | مسار دليل الإخراج غير صحيح أو لا توجد أذونات كتابة | تحقق من أن `YOUR_OUTPUT_DIRECTORY` موجود وقابل للكتابة |
| خطأ نفاد الذاكرة في ملفات PDF الكبيرة | عدم تحرير التدفقات بسرعة | تأكد من تنفيذ `FeatureReleasePageStream` بشكل صحيح |
| تنسيق ملف غير مدعوم | نوع المستند غير مدعوم من قبل GroupDocs.Watermark | تحقق من قائمة صيغ الدعم للمكتبة؛ قم بتحويل الملف إلى نوع مدعوم إذا لزم الأمر |

## الأسئلة المتكررة

**س: هل يمكنني إنشاء معاينات للمستندات المحمية بكلمة مرور؟**  
ج: نعم. قم بتحميل المستند باستخدام كلمة المرور المناسبة عبر مُنشئ `Watermarker` الذي يقبل معامل كلمة المرور، ثم تابع إنشاء المعاينة كما هو موضح.

**س: هل تدعم المكتبة صيغ صور أخرى غير PNG؟**  
ج: تُخرج API المعاينة PNG بشكل افتراضي، لكن يمكنك تحويل التدفقات الناتجة إلى JPEG أو BMP باستخدام مكتبات الصور القياسية في Java إذا لزم الأمر.

**س: كم عدد الصفحات التي يمكنني معاينتها في تشغيل واحد؟**  
ج: لا يوجد حد ثابت؛ ومع ذلك، قد تستفيد معالجة المستندات الضخمة جدًا من التجزئة أو زيادة حجم الذاكرة المخصصة للـ JVM.

**س: هل الترخيص إلزامي لإنشاء المعاينات؟**  
ج: الترخيص التجريبي يعمل للتقييم، لكن الترخيص الكامل مطلوب للنشر في بيئات الإنتاج لإزالة العلامات المائية وإتاحة جميع الميزات.

**س: هل يمكنني تخصيص دقة الصورة للمعاينات؟**  
ج: نعم. توفر `PreviewOptions` خصائص مثل `setResolution` حيث يمكنك تحديد إعدادات DPI قبل استدعاء `generatePreview`.

## الخلاصة

أصبح لديك الآن سير عمل كامل وجاهز للإنتاج **كيفية معاينة المستندات** باستخدام GroupDocs.Watermark في Java. من خلال تهيئة `Watermarker`، وإدارة تدفقات الصفحات، وتحرير الموارد بشكل صحيح، يمكنك إنشاء thumbnails عالية الجودة على نطاق واسع. طبّق هذه التقنيات لتحسين تجربة المستخدم في أي تطبيق يتعامل مع كميات كبيرة من المستندات.

---

**آخر تحديث:** 2025-12-16  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs