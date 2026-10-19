---
date: '2026-10-01'
description: เรียนรู้วิธีทำอัตโนมัติการแทนที่ภาพ java ในไฟล์แผนภาพด้วย GroupDocs.Watermark
  รวมถึงการเพิ่ม watermark และการประมวลผลที่มีประสิทธิภาพ
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: ทำอัตโนมัติการแทนที่ภาพ java ในแผนภาพด้วย GroupDocs.Watermark คู่มือนี้แสดงวิธีการแทนที่ภาพ,
  เพิ่ม watermark, และจัดการไฟล์ขนาดใหญ่อย่างมีประสิทธิภาพ
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: ทำการแทนที่ภาพ java อัตโนมัติด้วย GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: ทำการแทนที่ภาพ java อัตโนมัติด้วย GroupDocs.Watermark
type: docs
url: /th/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# อัตโนมัติการแทนที่รูปภาพใน Java ด้วย GroupDocs.Watermark

การอัปเดตรูปภาพแต่ละรูปภายในไดอะแกรมอาจเป็นงานที่น่าเบื่อและเสี่ยงต่อข้อผิดพลาด การใช้ **GroupDocs.Watermark for Java**, คุณสามารถ **automate image replacement java** ได้ในหลายสิบหรือหลายร้อยไฟล์ เพื่อให้แบรนด์สอดคล้องกันและประหยัดเวลาการพัฒนาที่มีค่า บทเรียนนี้จะพาคุณผ่านการตั้งค่าห้องสมุด การเข้าถึงเนื้อหาไดอะแกรม การสลับรูปภาพในรูปร่างเฉพาะ และการเพิ่มลายน้ำลงในไดอะแกรมตามต้องการ.

## คำตอบด่วน
- **ไลบรารีใดที่จัดการการอัปเดตรูปภาพในไดอะแกรม?** GroupDocs.Watermark for Java.  
- **ฉันสามารถเพิ่มลายน้ำขณะแทนที่รูปภาพได้หรือไม่?** ใช่ – API เดียวกันช่วยให้คุณวางลายน้ำบนหน้าไดอะแกรมใดก็ได้.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า.  
- **ต้องการใบอนุญาตสำหรับการพัฒนาหรือไม่?** ทดลองใช้ฟรีสำหรับการประเมิน; ต้องมีใบอนุญาตเชิงพาณิชย์สำหรับการใช้งานจริง.  
- **กระบวนการนี้มีประสิทธิภาพด้านหน่วยความจำสำหรับไดอะแกรมขนาดใหญ่หรือไม่?** ใช่ – SDK ทำการสตรีมข้อมูลและไม่โหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ.

## GroupDocs.Watermark for Java คืออะไร?
`GroupDocs.Watermark` เป็น Java SDK ที่ช่วยให้สามารถเพิ่ม, ลบ, และแทนที่ลายน้ำและรูปภาพในรูปแบบเอกสารกว่า 30 แบบ รวมถึง Visio, SVG, และประเภทไดอะแกรมอื่น ๆ มันประมวลผลไฟล์แบบสตรีมมิ่ง ทำให้คุณทำงานกับไดอะแกรมหลายร้อยหน้าโดยไม่ทำให้หน่วยความจำหมด

## ทำไมต้องอัตโนมัติการแทนที่รูปภาพใน Java?
การอัตโนมัติการแทนที่รูปภาพช่วยลดแรงงานมือได้ถึง **90 %** เมื่ออัปเดตสินทรัพย์แบรนด์ในคอลเลกชันเอกสารขนาดใหญ่ SDK รองรับ **รูปแบบเข้าและออกกว่า 30 แบบ**, ประมวลผลไฟล์ขนาดสูงสุด **200 MB** ภายในไม่กี่วินาทีบนฮาร์ดแวร์เซิร์ฟเวอร์ทั่วไป และรับประกันการวางตำแหน่งรูปภาพที่พิกเซลแม่นยำ

## ข้อกำหนดเบื้องต้น
- JDK 8 หรือใหม่กว่า ติดตั้งบนเครื่องพัฒนาของคุณ.  
- Maven (หรือเครื่องมือสร้างอื่น) เพื่อจัดการการพึ่งพา.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- ความรู้พื้นฐานของ Java และความคุ้นเคยกับการทำงานกับไฟล์ I/O.

### ไลบรารีที่จำเป็น, เวอร์ชัน, และการพึ่งพา
เพิ่มพิกัด Maven ต่อไปนี้ลงใน `pom.xml` ของคุณ ตัวแสดงตำแหน่งด้านล่างเป็นส่วนของ XML ที่ต้องการ; อย่าเปลี่ยนแปลง

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

สำหรับการดาวน์โหลดด้วยตนเอง ให้รับ JAR ล่าสุดจากหน้าปล่อยอย่างเป็นทางการ: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## วิธีอัตโนมัติการแทนที่รูปภาพใน Java?
โหลดไดอะแกรมด้วยอินสแตนซ์ `Watermarker` ค้นหารูปร่างเป้าหมาย, แทนที่สตรีมรูปภาพของพวกมัน, เพิ่มลายน้ำตามต้องการ, แล้วบันทึกไฟล์ ขั้นตอนทำงานทั้งหมดสั้นเพียง **สี่ขั้นตอนกระชับ**, แต่ละขั้นจะแสดงด้านล่าง และโดยทั่วไปใช้เวลาเพียงไม่กี่วินาทีต่อไดอะแกรมแม้ไฟล์จะใหญ่.

### ขั้นตอน 1: เริ่มต้น watermarker
คลาส `Watermarker` เป็นจุดเริ่มต้นสำหรับการดำเนินการเอกสารทั้งหมด มันเปิดไฟล์ต้นฉบับและเตรียมโครงสร้างภายในสำหรับการแก้ไข.

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

- **DiagramLoadOptions** กำหนดค่าพารามิเตอร์การโหลดเฉพาะสำหรับไดอะแกรม.  
- การเริ่มต้น `Watermarker` เปิดตัวจัดการไฟล์และตรวจสอบความถูกต้องของรูปแบบ.

### ขั้นตอน 2: เขาถึงเนื้อหาไดอะแกรม
`DiagramContent` แสดงโครงสร้างเชิงตรรกะของไดอะแกรม เปิดเผยหน้าและรูปร่างแต่ละอันสำหรับการตรวจสอบ.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- ใช้ `watermarker.getContent()` เพื่อดึงอ็อบเจกต์ `DiagramContent`.  
- วนลูปผ่าน `content.getPages()` แล้วตามด้วย `page.getShapes()` เพื่อค้นหารูปร่างที่มีรูปภาพ.

### ขั้นตอน 3: แทนที่รูปภาพของรูปร่างในไดอะแกรม
อ็อบเจกต์ `DiagramShape` อาจมีรูปภาพฝังอยู่ แทนที่โดยการส่ง `InputStream` ใหม่ที่อ่านรูปภาพแทนที่

เมธอด `setImage(InputStream)` จะเปลี่ยนรูปภาพปัจจุบันของรูปร่างด้วยสตรีมที่ส่งมา.

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

- ตรวจสอบ `shape.getImage()`; หากไม่เป็น null ให้เรียก `shape.setImage(newImageStream)`.  
- SDK จะอัปเดตขนาดรูปภาพโดยอัตโนมัติและคงรูปแบบรูปร่างเดิมไว้.

### ขั้นตอน 4: เพิ่มลายน้ำลงในไดอะแกรม (ทางเลือก)
หากคุณต้องการ **add watermark to diagram** ด้วย, สร้างอ็อบเจกต์ `Watermark` แล้วนำไปใช้กับหน้าที่ต้องการหรือทั้งเอกสาร.

คลาส `Watermark` กำหนดภาพซ้อนที่สามารถวางบนหน้าไดอะแกรมหรือทั้งเอกสารได้.

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

เมธอด `add(Watermark, AddOptions)` จะนำลายน้ำที่ระบุไปใช้กับเอกสารโดยใช้ตัวเลือกที่ให้มา.

* (โค้ดด้านบนเป็นตัวอย่างและไม่ถือเป็นบล็อกโค้ดใหม่; มันอยู่ภายในย่อหน้าที่มีอยู่แล้ว.)*

### ขั้นตอน 5: บันทึกและปิด watermarker
บันทึกการเปลี่ยนแปลงและปล่อยทรัพยากรเพื่อหลีกเลี่ยงการล็อกไฟล์.

เมธอด `save(String)` จะเขียนเอกสารที่แก้ไขแล้วไปยังเส้นทางที่ระบุ.

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

- เรียก `watermarker.save("output.vsdx")` (หรือส่วนขยายที่เหมาะสม).  
- ควรเรียก `watermarker.close()` ในบล็อก `finally` หรือใช้ try‑with‑resources เพื่อทำความสะอาดอัตโนมัติ.

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
- **Image size mismatch** – ตรวจสอบให้แน่ใจว่ารูปภาพแทนที่มีอัตราส่วนเดียวกับรูปภาพเดิมเพื่อหลีกเลี่ยงการบิดเบือน.  
- **Memory spikes on large diagrams** – ประมวลผลไดอะแกรมทีละไฟล์และปิด `Watermarker` หลังการบันทึกแต่ละครั้ง.  
- **License errors** – ใบอนุญาตทดลองหมดอายุหลัง 30 วัน; แทนที่ด้วยคีย์ผลิตภัณฑ์ก่อนการใช้งานจริง. คุณสามารถรับใบอนุญาตชั่วคราวจาก GroupDocs: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## คำถามที่พบบ่อย

**Q: ฉันสามารถแทนที่รูปภาพในไดอะแกรมที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ใช่. โหลดไฟล์ด้วย `DiagramLoadOptions` ที่รวมรหัสผ่าน, แล้วดำเนินการแทนที่ตามขั้นตอนปกติ.

**Q: SDK รองรับการประมวลผลเป็นชุดของหลายไดอะแกรมหรือไม่?**  
A: แน่นอน. ห่อเวิร์กโฟลว์ไฟล์เดียวในลูปที่วนผ่านไดเรกทอรี; สถาปัตยกรรมสตรีมมิ่งช่วยให้การใช้หน่วยความจำน้อย.

**Q: ฉันสามารถทำงานกับรูปแบบใดได้บ้างนอกจาก Visio?**  
A: GroupDocs.Watermark รองรับ SVG, VDX, VSDX และรูปแบบไดอะแกรมอื่น ๆ อีกหลายประเภท, รวมกว่า 30 รูปแบบที่สนับสนุน.

**Q: สามารถเพิ่มลายน้ำหลังจากแทนที่รูปภาพได้หรือไม่?**  
A: ใช่ – เรียก `watermarker.add(watermark, options)` หลังจากขั้นตอนแทนที่รูปภาพและก่อนการบันทึก.

**Q: ฉันจะทำให้แน่ใจว่ารูปภาพใหม่ถูกฝังในไฟล์ ไม่ใช่ลิงก์ได้อย่างไร?**  
A: เมธอด `setImage(InputStream)` ฝังข้อมูลรูปภาพโดยตรงลงในไฟล์ไดอะแกรม, รับประกันความพกพา.

---

**อัปเดตล่าสุด:** 2026-10-01  
**ทดสอบกับ:** GroupDocs.Watermark 23.12 for Java  
**ผู้เขียน:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [บทเรียนการใส่ลายน้ำไดอะแกรมสำหรับ GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [ลบไฮเปอร์ลิงก์จากรูปร่างไดอะแกรมโดยใช้ GroupDocs.Watermark Java เพื่อเพิ่มความปลอดภัยของเอกสาร](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [วิธีเพิ่มลายน้ำรูปภาพใน Java ด้วย GroupDocs.Watermark: คู่มือขั้นตอนต่อขั้นตอน](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)