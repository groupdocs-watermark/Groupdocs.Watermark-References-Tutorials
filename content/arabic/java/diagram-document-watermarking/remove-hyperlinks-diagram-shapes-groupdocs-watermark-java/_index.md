---
date: '2026-04-04'
description: تعرّف على كيفية إزالة الروابط من أشكال المخططات باستخدام GroupDocs.Watermark
  Java، مع ضمان أمان المستند ووضوحه.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: كيفية إزالة الروابط من أشكال المخطط باستخدام GroupDocs.Watermark Java
type: docs
url: /ar/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# كيفية إزالة الروابط من أشكال المخطط باستخدام GroupDocs.Watermark Java

إدارة المستندات الرقمية غالبًا ما تتضمن تحرير المخططات، خاصةً عندما تحتاج إلى **how to strip links** للأمان أو الوضوح. في هذا الدرس ستتعلم طريقة بسيطة، خطوة بخطوة لإزالة الروابط الفائضة من أشكال المخطط باستخدام مكتبة **GroupDocs.Watermark** القوية لجافا. في النهاية، ستحصل على مخططات نظيفة خالية من الروابط وآمنة للمشاركة.

## إجابات سريعة
- **What does “how to strip links” mean?** إنه يشير إلى إزالة كائنات الروابط الفائضة المدمجة في أشكال المخطط.  
- **Which library handles this?** GroupDocs.Watermark for Java (الإصدار 24.11 أو أحدث).  
- **Do I need a license?** نسخة تجريبية مجانية تعمل للاختبار؛ يلزم الحصول على ترخيص صالح للإنتاج.  
- **Can I process many files at once?** نعم – ضع الشيفرة داخل حلقة أو مهمة دفعة.  
- **Is this approach language‑specific?** المثال هو جافا، لكن نفس الفكرة تنطبق على واجهات برمجة التطبيقات الأخرى .NET/Java.

## ما هو “how to strip links” في تحرير المخططات؟
إزالة الروابط يعني تحديد كائنات الروابط الفائضة المرتبطة بالأشكال داخل المخطط (مثل Visio *.vsdx) وحذفها. هذا يزيل عناوين URL الخارجية التي قد تكشف معلومات حساسة أو تعطل تدفق العرض.

## لماذا تستخدم GroupDocs.Watermark لجافا؟
- **Precision** – وصول مباشر إلى كائنات الشكل ومجموعات الروابط الفائضة الخاصة بها.  
- **Performance** – محسّن للمخططات الكبيرة دون تحميل المستند بالكامل في الذاكرة.  
- **Cross‑format support** – يعمل مع العديد من صيغ المخططات (Visio، Draw.io، إلخ).

## المتطلبات المسبقة
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (أو تضمين JAR يدوي).  
- Java JDK 8 أو أحدث.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.

## إعداد GroupDocs.Watermark لجافا
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
إذا كنت تفضل عدم استخدام Maven، احصل على أحدث JAR من الموقع الرسمي:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### خطوات الحصول على الترخيص
- ابدأ بتنزيل نسخة تجريبية مجانية.  
- للإنتاج، احصل على ترخيص مؤقت أو كامل من بوابة GroupDocs.

#### التهيئة الأساسية والإعداد
Create a `Watermarker` instance that points to the folder containing your diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## كيفية إزالة الروابط من أشكال المخطط
فيما يلي عملية مختصرة من أربع خطوات تُظهر **remove hyperlinks java** عمليًا.

### الخطوة 1: تحميل ملف المخطط
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*لماذا؟* تحميل الملف يمنحك وصولًا برمجيًا إلى صفحاته، أشكاله، ومجموعات الروابط الفائضة.

### الخطوة 2: الوصول إلى محتوى الشكل
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*لماذا؟* تحتاج إلى مرجع للشكل المحدد الذي قد يحتوي على روابط.

### الخطوة 3: التكرار وإزالة الروابط الفائضة
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*لماذا؟* التكرار بالعكس يمنع مشاكل تغيير الفهارس عند حذف عناصر من المجموعة.

### الخطوة 4: الحفظ والإغلاق
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*لماذا؟* الحفظ يكتب المخطط المنظف إلى القرص، والإغلاق يحرر مقبض الملف لتجنب تسرب الذاكرة.

## تطبيقات عملية لإزالة الروابط
1. **Security** – إزالة عناوين URL الخارجية التي قد تؤدي إلى التصيد أو تسريب البيانات.  
2. **Compliance** – ضمان أن المخططات تتوافق مع السياسات الداخلية قبل التوزيع.  
3. **Presentation Cleanliness** – القضاء على المناطق القابلة للنقر غير الضرورية التي تشوش المشاهدين.

## اعتبارات الأداء
- **Loop Efficiency** – استخدم نمط التكرار العكسي الموضح أعلاه.  
- **Resource Management** – يفضَّل `try‑with‑resources` أو استدعاءات `close()` الصريحة.  
- **Large Files** – راقب استهلاك CPU/الذاكرة؛ فكر في معالجة الصفحات على دفعات.

## المشكلات الشائعة والحلول
- **No hyperlinks found** – تحقق من أن المخطط يحتوي فعليًا على كائنات روابط؛ بعض الصيغ تخزنها بطريقة مختلفة.  
- **IndexOutOfBoundsException** – دائمًا قم بالتكرار بالعكس عند إزالة عناصر من مجموعة.  
- **License errors** – تأكد من وضع ملف الترخيص بشكل صحيح أو تمريره إلى مُنشئ `Watermarker`.

## الأسئلة المتكررة
**س: كيف أتعامل مع أشكال متعددة على صفحات متعددة؟**  
ج: قم بالتكرار عبر `content.getPages()` ثم عبر مجموعة `getShapes()` لكل صفحة، مع تطبيق نفس منطق الإزالة على كل شكل.

**س: هل يمكنني تصفية الروابط حسب النطاق بدلاً من عنوان URL كامل؟**  
ج: نعم – غيّر فحص `contains` للبحث عن سلسلة النطاق (مثال: `"example.com"`).

**س: هل هناك طريقة لتسجيل الروابط التي تم إزالتها؟**  
ج: داخل الحلقة، احصل على `shape.getHyperlinks().get_Item(i).getAddress()` قبل الإزالة واكتبها إلى ملف سجل.

**س: هل يعمل هذا مع مخططات PDF المدمجة في مستندات أخرى؟**  
ج: GroupDocs.Watermark يدعم العديد من الصيغ؛ تأكد من أن نوع الملف يُعترف به كمخطط (Visio، VDX، إلخ).

**س: ما الترخيص المطلوب للمعالجة الدفعية؟**  
ج: يحتاج إلى ترخيص إنتاج كامل لأي عمليات غير تجريبية ذات حجم كبير.

## الخاتمة
أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج **how to strip links** من أشكال المخطط باستخدام GroupDocs.Watermark لجافا. دمجها في خطوط معالجة المستندات الخاصة بك لتعزيز الأمان، والامتثال، وجودة العرض.

### الخطوات التالية
- استكشف ميزات تعديل أخرى مثل إضافة العلامات المائية أو ختم النص.  
- اجمع هذه العملية مع خدمة مراقبة الملفات لتنظيف المخططات تلقائيًا عند تحميلها.

---

**آخر تحديث:** 2026-04-04  
**تم الاختبار مع:** GroupDocs.Watermark 24.11 for Java  
**المؤلف:** GroupDocs  

## الموارد
- [التوثيق](https://docs.groupdocs.com/watermark/java/)
- [مرجع API](https://reference.groupdocs.com/watermark/java)
- [تحميل](https://releases.groupdocs.com/watermark/java/)
- [مستودع GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/watermark/10)
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)