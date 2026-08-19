---
date: '2026-08-19'
description: เรียนรู้วิธีแทนที่ภาพแผนภาพใน Java ด้วย GroupDocs.Watermark รวมถึงการเพิ่มลายน้ำให้แผนภาพอย่างมีประสิทธิภาพ
  โค้ดขั้นตอนต่อขั้นตอนและแนวปฏิบัติที่ดีที่สุด
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: เรียนรู้วิธีแทนที่ภาพแผนภาพใน Java ด้วย GroupDocs.Watermark รวมถึงการเพิ่มลายน้ำให้แผนภาพอย่างมีประสิทธิภาพ
  โค้ดขั้นตอนต่อขั้นตอนและแนวปฏิบัติที่ดีที่สุด
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: แทนที่ภาพแผนภาพใน Java ด้วย GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: แทนที่ภาพแผนภาพใน Java ด้วย GroupDocs.Watermark
type: docs
url: /th/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# แทนที่ภาพแผนภาพใน Java ด้วย GroupDocs.Watermark

การอัปเดตภาพภายในไฟล์แผนภาพด้วยตนเองใช้เวลานานและเสี่ยงต่อข้อผิดพลาด ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **แทนที่ภาพแผนภาพใน Java** ด้วยเพียงไม่กี่บรรทัดของโค้ด และคุณยังจะเห็นวิธี **เพิ่มลายน้ำให้แผนภาพ** เมื่อจำเป็น เมื่อเสร็จแล้วคุณจะมีโค้ดส่วนนำกลับมาใช้ใหม่ที่สามารถใส่ลงในโครงการ Java ใด ๆ ที่ทำงานกับ Visio, Draw.io หรือรูปแบบแผนภาพที่รองรับอื่น ๆ

## คำตอบสั้น
- **ไลบรารีที่จัดการการแทนที่ภาพแผนภาพคืออะไร?** GroupDocs.Watermark สำหรับ Java  
- **ต้องใช้กี่บรรทัดของโค้ดสำหรับการแทนที่พื้นฐาน?** เพียงสามบรรทัดหลังจากสร้าง Watermarker  
- **สามารถเพิ่มลายน้ำได้พร้อมกันหรือไม่?** ได้ – ใช้ Watermarker ตัวเดียวกันพร้อมอ็อบเจกต์ลายน้ำ  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในผลิตภัณฑ์หรือไม่?** ต้องมีลิขสิทธิ์ GroupDocs.Watermark ที่ถูกต้อง; มีรุ่นทดลองฟรีให้ใช้  

## Replace diagram images java คืออะไร?
การแทนที่ภาพแผนภาพใน Java หมายถึงการค้นหาและเปลี่ยนรูปทรงที่มีกราฟิกบิตแมพภายในไฟล์แผนภาพ (เช่น .vsdx, .drawio หรือ .svg) ด้วยภาพใหม่โดยใช้ GroupDocs.Watermark API วิธีนี้ทำให้การอัปเดตอัตโนมัติที่โดยปกติจะต้องแก้ไขด้วยมือในโปรแกรมแก้ไขแผนภาพ

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับการแทนที่ภาพแผนภาพ?
GroupDocs.Watermark รองรับ **รูปแบบไฟล์เข้าและออกกว่า 50 รูปแบบ** – รวมถึง Visio, Draw.io และ SVG – และสามารถประมวลผล **ไฟล์ขนาดสูงสุดถึง 500 MB** โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ ทำให้คุณได้รับ **การลดการใช้ CPU ลง 30 %** เมื่อเทียบกับวิธีการสตรีมไฟล์แบบธรรมดา

## ข้อกำหนดเบื้องต้น
- ติดตั้ง JDK 8 หรือใหม่กว่า  
- IDE (IntelliJ IDEA, Eclipse หรือ VS Code) สำหรับการพัฒนา Java  
- Maven (หรือความสามารถในการเพิ่ม JAR ด้วยตนเอง)  
- ลิขสิทธิ์ GroupDocs.Watermark ที่ถูกต้อง (รุ่นทดลองหรือถาวร) คุณสามารถรับลิขสิทธิ์ได้จาก [GroupDocs](https://purchase.groupdocs.com/temporary-license/)

### ไลบรารีที่ต้องการ, เวอร์ชัน, และการพึ่งพา
เพิ่มรีโพซิทอรีและการพึ่งพาของ GroupDocs.Watermark ไปยัง `pom.xml` ของคุณ:

```xml
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
```

หากคุณต้องการจัดการ JAR ด้วยตนเอง ให้ดาวน์โหลดเวอร์ชันล่าสุดจากเว็บไซต์อย่างเป็นทางการ: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

## วิธีแทนที่ภาพแผนภาพใน Java ทีละขั้นตอน

### วิธีการเริ่มต้น Watermarker สำหรับไฟล์แผนภาพ
Watermarker คือคลาสหลักที่แทนเอกสารและให้เมธอดสำหรับการจัดการเนื้อหา เพื่อเริ่มต้น ให้สร้างอ็อบเจกต์ `Watermarker` ที่โหลดไฟล์แผนภาพเข้าสู่หน่วยความจำ `Watermarker` เป็นจุดเริ่มต้นของ GroupDocs.Watermark ที่ให้คุณอ่าน, แก้ไข, และบันทึกเอกสาร ใช้ `DiagramLoadOptions` เพื่อระบุการตั้งค่าเฉพาะรูปแบบ เช่น DPI หรือช่วงหน้า `DiagramLoadOptions` กำหนดวิธีการโหลดแผนภาพ เช่น การตั้งค่า DPI หรือโหมดการโหลด

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### วิธีเข้าถึงเนื้อหาแผนภาพเพื่อค้นหารูปทรง
หลังจากโหลดไฟล์แล้ว ให้ดึงอ็อบเจกต์ `DiagramContent` จาก `Watermarker` `DiagramContent` แสดงโครงสร้างภายในของแผนภาพที่ประกอบด้วยหน้าและรูปทรง โมเดลนี้ให้คอลเลกชันของหน้าและรูปทรงที่คุณสามารถวนลูปเพื่อค้นหาองค์ประกอบเฉพาะ เช่น ภาพหรือข้อความ

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### วิธีแทนที่ภาพรูปทรงในแผนภาพ
วนลูปผ่านแต่ละ `DiagramShape` บนหน้าที่ต้องการ ตรวจสอบว่ารูปทรงนั้นมีภาพหรือไม่ และแทนที่ไบต์ของภาพด้วยไฟล์ใหม่ `DiagramShape` คือโมเดลของรูปทรงเดี่ยวในแผนภาพ ส่วน `DiagramWatermarkableImage` เก็บข้อมูลภาพที่สามารถนำไปใช้กับรูปทรงได้

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### วิธีบันทึกการเปลี่ยนแปลงและปิด Watermarker
เมื่อทำการแก้ไขทั้งหมดเสร็จแล้ว ให้เรียก `save` บน `Watermarker` เพื่อเขียนแผนภาพที่อัปเดตลงไฟล์ แล้วเรียก `close` เพื่อปล่อยทรัพยากรเนทีฟ การทำเช่นนี้จะทำให้ตัวจัดการไฟล์ถูกปล่อยและป้องกันการรั่วของหน่วยความจำ โดยเฉพาะเมื่อประมวลผลแผนภาพจำนวนมากในงานแบตช์

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## การเพิ่มลายน้ำให้แผนภาพเดียวกัน (ไม่บังคับ)

หากคุณต้องการทำแบรนด์ให้กับแผนภาพ คุณสามารถเพิ่มลายน้ำก่อนหรือหลังการแทนที่ภาพได้:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## ปัญหาที่พบบ่อยและการแก้ไขข้อผิดพลาด

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| ไม่เห็นการเปลี่ยนแปลงของภาพหลังรันโค้ด | `DiagramShape.hasImage()` คืนค่า false | ตรวจสอบประเภทของรูปทรง; บางรูปทรงเวกเตอร์เก็บภาพในรูปแบบอื่น |
| OutOfMemoryError กับไฟล์ขนาดใหญ่ | โหลดแผนภาพทั้งหมดพร้อมกัน | ใช้ `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` เพื่อประมวลผลหน้าแบบต่อเนื่อง |
| ลายน้ำไม่ปรากฏ | ลายน้ำถูกวางไว้ด้านหลังเนื้อหาเดิม | เรียก `watermarker.setWatermarkPosition(Position.Foreground)` ก่อนบันทึก |

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถแทนที่ภาพในแผนภาพที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
ตอบ: ได้. ส่งรหัสผ่านไปยัง `DiagramLoadOptions` เมื่อสร้าง `Watermarker`

**ถาม: ไลบรารีรองรับไฟล์ .drawio (XML) หรือไม่?**  
ตอบ: รองรับอย่างเต็มที่ – GroupDocs.Watermark รองรับรูปแบบ XML ของ Draw.io และถือแต่ละโหนดเป็นรูปทรง

**ถาม: สามารถประมวลผลแผนภาพพร้อมกันได้กี่รายการ?**  
ตอบ: ไลบรารีปลอดภัยต่อเธรดสำหรับการอ่านอย่างเดียว; สำหรับการเขียนควรจำกัดความพร้อมกันให้เท่ากับจำนวนคอร์ CPU เพื่อหลีกเลี่ยงการแย่งตัวจัดการไฟล์

**ถาม: มีขีดจำกัดขนาดของภาพหรือไม่?**  
ตอบ: รองรับภาพขนาดสูงสุด 100 MB; ไฟล์ที่ใหญ่กว่านั้นควรปรับขนาดก่อนเพื่อรักษาการใช้หน่วยความจำให้ต่ำ

**ถาม: ตัวเลือกการให้ลิขสิทธิ์มีอะไรบ้าง?**  
ตอบ: คุณสามารถเริ่มต้นด้วยรุ่นทดลองฟรี 30 วัน; การใช้งานในผลิตภัณฑ์ต้องมีลิขสิทธิ์แบบชำระเงิน ซึ่งสามารถซื้อได้จากร้านค้า GroupDocs

---

**อัปเดตล่าสุด:** 2026-08-19  
**ทดสอบด้วย:** GroupDocs.Watermark 23.9 สำหรับ Java  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [บทแนะนำการใส่น้ำลายน้ำแผนภาพสำหรับ GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [การลบไฮเปอร์ลิงก์จากรูปทรงแผนภาพด้วย GroupDocs.Watermark Java เพื่อเพิ่มความปลอดภัยของเอกสาร](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [วิธีเพิ่มลายน้ำรูปภาพใน Java ด้วย GroupDocs.Watermark: คู่มือขั้นตอนโดยละเอียด](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)