---
date: '2026-02-13'
description: تعلم كيفية استخراج الأشكال واستخراج الصورة من الشكل باستخدام GroupDocs.Watermark
  للغة جافا، مع استرجاع معلومات المخطط التفصيلية بكفاءة.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: كيفية استخراج الأشكال من المخططات باستخدام GroupDocs.Watermark في جافا
type: docs
url: /ar/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# كيفية استخراج الأشكال من المخططات باستخدام GroupDocs.Watermark في Java

عندما تحتاج إلى **كيفية استخراج الأشكال** من مخطط على نمط Visio برمجياً، توفر لك مكتبة GroupDocs.Watermark طريقة نظيفة وموجهة للـ Java لسحب كل التفاصيل—الأبعاد، المواقع، الصور المدمجة، وحتى النص داخل كل شكل. في هذا الدرس ستشاهد بالضبط **كيفية استخراج الأشكال**، لماذا ذلك مهم، وكود خطوة بخطوة يمكنك نسخه إلى مشروعك.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع استخراج الأشكال؟** GroupDocs.Watermark for Java  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى  
- **هل يمكنني الحصول على بيانات الصورة من شكل؟** نعم – استخدم `shape.getImage()`  
- **هل يمكن الوصول إلى النص داخل الشكل؟** بالتأكيد، عبر `shape.getText()`  
- **هل أحتاج إلى ترخيص للإنتاج؟** يلزم وجود ترخيص صالح لـ GroupDocs.Watermark  

## المقدمة

إدارة المخططات المعقدة غالبًا ما تتطلب الوصول إلى معلومات تفصيلية حول مكوناتها، مثل الأشكال والصور. إذا احتجت يومًا إلى استرجاع بيانات برمجياً مثل الأبعاد، المواقع، أو النص المرتبط بأشكال المخطط باستخدام Java، فهذا الدرس لك. الاستفادة من قوة مكتبة GroupDocs.Watermark يمكن أن تبسط هذه العملية في تطبيق Java. في هذا الدليل، سنستعرض **كيفية استخراج الأشكال** من ملف مخطط وسنوضح لك أيضًا **كيفية استخراج الصورة من الشكل** و**كيفية استخراج النص من الشكل**.

## ما هو “كيفية استخراج الأشكال”؟

استخراج الأشكال يعني قراءة الكائنات الداخلية للمخطط (الصفحات، الأشكال، الصور، النص) بحيث يمكنك تحليلها أو تحويلها أو إعادة استخدامها في تطبيقات أخرى—مثالي للأتمتة، إعداد التقارير، أو التكامل مع أدوات CAD.

## لماذا تستخدم GroupDocs.Watermark لاستخراج الأشكال؟

- **دعم كامل للملفات** – يعمل مع VSDX، VDX، والعديد من أنواع المخططات الأخرى.  
- **نموذج كائن غني** – يتيح وصولاً مباشراً إلى هندسة الشكل، الصور، والنص.  
- **بدون تبعيات خارجية** – جافا صافية، سهل الإدماج في مشاريع Maven.  

## المتطلبات المسبقة

- **GroupDocs.Watermark for Java** (الإصدار 24.11 أو أحدث)  
- مجموعة تطوير جافا (JDK) 8 أو أعلى  
- Maven لإدارة التبعيات  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse  

## إعداد GroupDocs.Watermark للـ Java

أضف المكتبة إلى ملف Maven `pom.xml` الخاص بك:

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

يمكنك أيضًا تنزيل أحدث الملفات الثنائية من [إصدارات GroupDocs.Watermark للـ Java](https://releases.groupdocs.com/watermark/java/).

### خطوات الحصول على الترخيص
- **نسخة تجريبية مجانية:** قم بتنزيل حزمة تجريبية لتقييم الـ API.  
- **ترخيص مؤقت:** اطلب مفتاحًا مؤقتًا للاختبار الموسع.  
- **شراء:** احصل على ترخيص كامل للاستخدام في الإنتاج.  

### التهيئة الأساسية والإعداد

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## كيفية استخراج الأشكال – دليل التنفيذ

### تحميل واسترجاع المحتوى

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### التكرار عبر الأشكال

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### كيفية استخراج الصورة من الشكل

استدعاء `shape.getImage()` يُعيد كائنًا يحتوي على الـ bitmap الخام، أبعاده، ومصفوفة البايتات. استخدم الخصائص المعروضة أعلاه لتخزين الصورة على القرص أو تمريرها إلى خط معالجة آخر.

### كيفية استخراج النص من الشكل

طريقة `shape.getText()` تُعيد النص العادي داخل الشكل. إذا كان الشكل لا يحتوي على نص، تُعيد الطريقة `null`. الحلقة النموذجية تطبع النص بالفعل، ويمكنك تعديلها أكثر—مثلاً بناء فهرس لجميع تسميات الأشكال.

## نصائح استكشاف الأخطاء وإصلاحها
- تحقق من مسار الملف وأذونات القراءة.  
- تأكد من أنك تستخدم تنسيق مخطط مدعوم (VSDX، VDX، إلخ).  
- إذا ظهر شكل بدون البيانات المتوقعة، راجع ملاحظات إصدار المكتبة للعثور على خصائص خاصة بالتنسيق.  

## التطبيقات العملية

1. **تحليل المخططات:** تدقيق المخططات تلقائيًا للتحقق من الامتثال عبر فحص أحجام الأشكال أو العلامات المفقودة.  
2. **تصوير البيانات:** إدخال الأبعاد المستخرجة إلى لوحة تقارير لتصوير كثافة التخطيط.  
3. **تكامل CAD:** دمج بيانات الأشكال مع واجهات CAD لمزامنة مواصفات التصميم عبر الأدوات.  

## اعتبارات الأداء

- **إغلاق الموارد:** استدعِ `watermarker.close()` عند الانتهاء لتحرير الموارد الأصلية.  
- **إدارة الذاكرة:** المخططات الكبيرة قد تستهلك مساحة كبيرة من الذاكرة؛ راقب الذاكرة وزد `-Xmx` إذا لزم الأمر.  
- **معالجة دفعات:** عالج الملفات على دفعات وأعد استخدام كائن `Watermarker` واحد عندما يكون ذلك ممكنًا.  

## الخلاصة

باتباعك لهذا الدليل الآن تعرف **كيفية استخراج الأشكال**، وكيفية **استخراج الصورة من الشكل**، وكيفية **استخراج النص من الشكل** باستخدام GroupDocs.Watermark للـ Java. تفتح هذه التقنيات الباب أمام تحليل المخططات تلقائيًا، إعداد التقارير، والتكامل مع أنظمة هندسية أخرى. كخطوة تالية، استكشف الـ API بالكامل عبر مراجعة [التوثيق](https://docs.groupdocs.com/watermark/java/) وجرب دمج استخراج الأشكال مع منطق أعمال مخصص.

## قسم الأسئلة المتكررة

1. **ما هو GroupDocs.Watermark؟**  
   - مكتبة Java شاملة صُممت لإضافة العلامات المائية واستخراج المعلومات من صيغ مستندات متعددة، بما في ذلك المخططات.  

2. **هل يمكنني استخدام هذه المكتبة لمعالجة جميع أنواع ملفات المخططات؟**  
   - نعم، لكن تأكد من أن تنسيق الملف مدعوم عبر فحص [مرجع API](https://reference.groupdocs.com/watermark/java/).  

3. **كيف يمكنني استخراج أبعاد ومواقع الأشكال من مخطط باستخدام Java وGroupDocs.Watermark؟**  
   - حمّل المخطط، وصول إلى `DiagramContent`، ثم تكرار الأشكال للحصول على خصائص مثل العرض، الارتفاع، X، وY.  

4. **هل يستطيع GroupDocs.Watermark استخراج الصور المدمجة في أشكال المخطط باستخدام Java؟**  
   - نعم، توفر المكتبة طرقًا للوصول إلى بيانات الصورة داخل الأشكال، بما في ذلك الحجم وبيانات البكسل، مفيدة للتحليل أو التعديل.  

5. **ما هي المتطلبات المسبقة لاستخراج معلومات أشكال المخطط في Java؟**  
   - Java JDK 8+، إعداد Maven، مكتبة GroupDocs.Watermark (24.11+)، ومعرفة أساسية بـ Java ضرورية للتنفيذ.  

---

**آخر تحديث:** 2026-02-13  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs