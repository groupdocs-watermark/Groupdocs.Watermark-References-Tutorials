---
date: '2026-08-04'
description: เรียนรู้วิธีใช้ GroupDocs เพื่อเพิ่ม image effects—brightness, contrast,
  chroma key, borders—ให้กับ shape watermarks ใน Java presentations ด้วย GroupDocs.Watermark.
keywords:
- how to use groupdocs
- apply image effects to shape watermarks in java
- groupdocs watermark java
lastmod: '2026-08-04'
og_description: ค้นพบวิธีใช้ GroupDocs เพื่อเพิ่ม brightness, contrast, chroma key
  และ border effects ให้กับ shape watermarks ใน Java presentations. คู่มือขั้นตอนต่อขั้นสำหรับนักพัฒนา.
og_image_alt: Guide showing GroupDocs.Watermark Java code for applying image effects
  to shape watermarks
og_title: วิธีใช้ GroupDocs – Apply image effects ให้กับ shape watermarks ใน Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use GroupDocs to add image effects—brightness, contrast,
    chroma key, borders—to shape watermarks in Java presentations with GroupDocs.Watermark.
  headline: How to use GroupDocs to apply image effects to shape watermarks in Java
  type: TechArticle
- description: Learn how to use GroupDocs to add image effects—brightness, contrast,
    chroma key, borders—to shape watermarks in Java presentations with GroupDocs.Watermark.
  name: How to use GroupDocs to apply image effects to shape watermarks in Java
  steps:
  - name: load the presentation file
    text: The `Watermarker` class is the entry point for all watermark operations
      on a document.
  - name: create an image watermark instance
    text: The `ImageWatermark` class represents a raster image (e.g., a logo) that
      can be placed onto a shape as a watermark.
  - name: configure image effects
    text: The `PresentationImageEffects` class lets you modify brightness, contrast,
      chroma‑key transparency, and border settings for image watermarks in presentations.
  - name: add the configured watermark to the presentation
    text: The `PresentationWatermarkOptions` class specifies where and how a watermark
      is applied, such as target slides and positioning.
  - name: save the modified presentation and release resources
    text: Always close the `Watermarker` to free file handles and memory buffers.
  type: HowTo
- questions:
  - answer: Call `setOpacity(double opacity)` on the `PresentationImageEffects` object;
      values range from 0.0 (fully transparent) to 1.0 (fully opaque).
    question: How do I adjust the transparency of an image watermark?
  - answer: Yes. Use `PresentationWatermarkOptions.setSlideIndices(int... indices)`
      to target individual slide numbers.
    question: Can I apply watermarks to specific slides only?
  - answer: PNG, JPEG, BMP, GIF, TIFF, and WebP are all supported, giving you flexibility
      for logos and graphics.
    question: What image formats are supported for watermarking?
  - answer: Wrap the workflow in a try‑catch block and catch `WatermarkException`
      to obtain detailed error codes and messages.
    question: How should I handle errors during watermark processing?
  - answer: Absolutely. Iterate over a collection of file paths, instantiate a `Watermarker`
      for each, and apply the same watermark configuration.
    question: Is batch processing of many presentations possible?
  type: FAQPage
tags:
- groupdocs watermark
- java image effects
- shape watermarks
- presentation security
title: วิธีใช้ GroupDocs เพื่อ apply image effects ให้กับ shape watermarks ใน Java
type: docs
url: /th/java/image-watermarks/apply-image-effects-shape-watermarks-java-groupdocs-watermark/
weight: 1
---

# วิธีใช้ GroupDocs เพื่อใช้เอฟเฟกต์ภาพกับลายน้ำรูปทรงใน Java

การปกป้องไฟล์การนำเสนอของคุณเป็นสิ่งสำคัญอันดับแรกสำหรับผู้เชี่ยวชาญทุกคนที่แชร์สไลด์สาธารณะหรือภายใน **วิธีใช้ GroupDocs** เพื่อเพิ่มเอฟเฟกต์ภาพ—เช่น ความสว่าง, ความคอนทราสต์, ความโปร่งใสแบบ chroma‑key, และกรอบที่กำหนดเอง—จะให้การควบคุมอย่างละเอียดว่าลายน้ำดูเป็นอย่างไรในขณะที่รักษาเนื้อหาเดิมไว้ไม่เปลี่ยนแปลง. ในบทเรียนนี้คุณจะได้เรียนรู้ขั้นตอนทำงานทั้งหมด ตั้งแต่การตั้งค่าโครงการจนถึงการบันทึกไฟล์สุดท้าย และคุณจะเห็นว่า GroupDocs.Watermark เป็นไลบรารีที่มีคุณสมบัติมากที่สุดสำหรับงานนี้.

## คำตอบสั้น
- **ไลบรารีใดที่เพิ่มเอฟเฟกต์ภาพให้กับลายน้ำ?** GroupDocs.Watermark for Java.  
- **ฉันสามารถปรับความสว่างและความคอนทราสต์พร้อมกันได้หรือไม่?** Yes, via `PresentationImageEffects`.  
- **กรอบเป็นตัวเลือกหรือไม่?** You can enable or disable it with `setBorderColor` and `setBorderWidth`.  
- **ฉันต้องการใบอนุญาตสำหรับการใช้งานในผลิตภัณฑ์หรือไม่?** A valid GroupDocs license is required for unrestricted use.  
- **รูปแบบไฟล์ใดบ้างที่รองรับ?** Over 50 formats, including PPTX, PPT, and PDF.

## GroupDocs.Watermark for Java คืออะไร?
GroupDocs.Watermark for Java เป็นไลบรารีที่ครอบคลุมซึ่งช่วยให้นักพัฒนาสามารถเพิ่ม, แก้ไข, และลบลายน้ำบนรูปแบบเอกสารและภาพกว่า 50 ประเภท. มันทำงานทั้งหมดบนเซิร์ฟเวอร์, ไม่ต้องพึ่งพาแอปพลิเคชันของบุคคลที่สาม, และให้ API ที่เต็มไปด้วยความสามารถสำหรับการปรับแต่งภาพอย่างละเอียด, การประมวลผลเป็นชุด, และการสตรีมประสิทธิภาพสูง.

## ทำไมต้องใช้เอฟเฟกต์ภาพบนลายน้ำรูปทรง?
การใช้เอฟเฟกต์ภาพช่วยให้คุณปรับแต่งผลกระทบทางภาพของลายน้ำโดยไม่ทำให้การอ่านลดลง การปรับความสว่างหรือความคอนทราสต์สามารถทำให้โลโก้ผสมกับพื้นหลังสไลด์อย่างละเอียดอ่อน, ในขณะที่ความโปร่งใสแบบ chroma‑key จะลบสีที่ไม่ต้องการ การเพิ่มกรอบสร้างขอบเขตภาพที่ชัดเจน, เสริมสร้างอัตลักษณ์แบรนด์และทำให้ลายน้ำยากต่อการลบหรือเพิกเฉย.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Watermark for Java** — Version 24.11 or later.  
- Java Development Kit 8 or newer.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- ความรู้พื้นฐานการเขียนโปรแกรม Java และความคุ้นเคยกับไฟล์การนำเสนอ (PPTX).

## วิธีตั้งค่า GroupDocs.Watermark for Java
โหลดไลบรารีเข้าสู่โครงการ Maven ของคุณและตรวจสอบให้แน่ใจว่าใบอนุญาตพร้อมใช้งานก่อนการเรียกใช้ API ใด ๆ.

**การกำหนดค่า Maven**  
เพิ่ม dependency ต่อไปนี้ลงในไฟล์ `pom.xml` ของคุณ:

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

**ดาวน์โหลดโดยตรง**  
คุณยังสามารถดาวน์โหลดไฟล์ JAR จากหน้าปล่อยอย่างเป็นทางการ: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับใบอนุญาต
มีการทดลองใช้ฟรีสำหรับการประเมินผล สำหรับการใช้งานในผลิตภัณฑ์, ขอใบอนุญาตชั่วคราวหรือซื้อใบอนุญาตเต็มจากพอร์ทัลของ GroupDocs.

## วิธีใช้เอฟเฟกต์ภาพกับลายน้ำรูปทรงในงานนำเสนอ
โหลดงานนำเสนอของคุณ, สร้างลายน้ำภาพ, กำหนดค่าเอฟเฟกต์ที่ต้องการ, และบันทึกผลลัพธ์. ขั้นตอนด้านล่างให้วิธีแก้ไขที่กระชับและครบวงจร, และแต่ละขั้นตอนมีตัวอย่างโค้ดสั้นที่คุณสามารถคัดลอกไปยังโครงการของคุณได้โดยตรง.

### ขั้นตอน 1: โหลดไฟล์งานนำเสนอ
คลาส `Watermarker` เป็นจุดเริ่มต้นสำหรับการดำเนินการลายน้ำทั้งหมดบนเอกสาร.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### ขั้นตอน 2: สร้างอินสแตนซ์ลายน้ำภาพ
คลาส `ImageWatermark` แสดงภาพแรสเตอร์ (เช่น โลโก้) ที่สามารถวางบนรูปทรงเป็นลายน้ำได้.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### ขั้นตอน 3: กำหนดค่าเอฟเฟกต์ภาพ
คลาส `PresentationImageEffects` ให้คุณปรับความสว่าง, ความคอนทราสต์, ความโปร่งใสแบบ chroma‑key, และการตั้งค่ากรอบสำหรับลายน้ำภาพในงานนำเสนอ.

```java
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
```

### ขั้นตอน 4: เพิ่มลายน้ำที่กำหนดค่าแล้วลงในงานนำเสนอ
คลาส `PresentationWatermarkOptions` ระบุตำแหน่งและวิธีการที่ลายน้ำจะถูกนำไปใช้, เช่น สไลด์เป้าหมายและการจัดตำแหน่ง.

```java
PresentationImageEffects effects = new PresentationImageEffects();
effects.setBrightness(0.7); // Set brightness to 70% of original.
effects.setContrast(0.6);   // Set contrast to 60% of original.
effects.setChromaKey(Color.getRed()); // Apply chroma key using the color red for transparency.

// Enable and configure border line settings
effects.getBorderLineFormat().setEnabled(true);
effects.getBorderLineFormat().setWeight(1); // Set border weight to 1.
```

### ขั้นตอน 5: บันทึกงานนำเสนอที่แก้ไขและปล่อยทรัพยากร
ควรปิด `Watermarker` เสมอเพื่อปล่อยตัวจัดการไฟล์และบัฟเฟอร์หน่วยความจำ.

```java
PresentationWatermarkSlideOptions options = new PresentationWatermarkSlideOptions();
options.setEffects(effects);

watermarker.add(watermark, options);
```

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
- **เส้นทางไฟล์ไม่ถูกต้อง** – ใช้เส้นทางแบบเต็มหรือแก้ไขเส้นทางสัมพันธ์โดยอ้างอิงจาก `System.getProperty("user.dir")`.  
- **รูปแบบภาพที่ไม่รองรับ** – ตรวจสอบว่าภาพเป็น PNG, JPEG, BMP, หรือประเภทที่รองรับอื่น ๆ.  
- **ไม่ได้โหลดใบอนุญาต** – ตรวจสอบให้แน่ใจว่าไฟล์ใบอนุญาตอยู่ใน classpath และถูกกำหนดค่าเริ่มต้นก่อนการเรียก API ใด ๆ.  
- **งานนำเสนอขนาดใหญ่** – เปิดใช้งานโหมดสตรีม (`Watermarker.setStreaming(true)`) เพื่อรักษาการใช้หน่วยความจำให้ต่ำ.

## การประยุกต์ใช้งานจริง
1. **การปกป้องแบรนด์** – ฝังโลโก้บริษัทที่มีความโปร่งใสระดับกึ่งหนึ่งพร้อมความสว่างที่กำหนดเองเพื่อทำให้การคัดลอกไม่น่าสนใจ.  
2. **เนื้อหาการศึกษา** – ใส่ลายน้ำบนสไลด์บรรยายด้วยตรามหาวิทยาลัยที่ใช้เอฟเฟกต์ chroma‑key เพื่อผสมกับพื้นหลังสไลด์.  
3. **การรายงานขององค์กร** – เพิ่มลายน้ำที่มีกรอบบนชุดสไลด์การเงินที่เป็นความลับ, เพื่อให้สีกรอบตรงกับแนวทางแบรนด์ขององค์กร.

## เคล็ดลับด้านประสิทธิภาพ
- ประมวลผลงานนำเสนอเป็นชุดโดยใช้ thread‑pool executor เพื่อเพิ่มการใช้ CPU ให้สูงสุด.  
- ใช้ instance ของ `Watermarker` เดียวกันสำหรับหลายไฟล์เมื่อเป็นไปได้; เพียงรี‑initialize วัตถุลายน้ำเมื่อสไตล์ภาพเปลี่ยน.  
- ตรวจสอบ heap ของ JVM ด้วยเครื่องมือเช่น VisualVM เพื่อตรวจจับการเพิ่มขึ้นของหน่วยความจำที่ไม่คาดคิด.

## คำถามที่พบบ่อย

**Q: ฉันจะปรับความโปร่งใสของลายน้ำภาพได้อย่างไร?**  
A: เรียก `setOpacity(double opacity)` บนวัตถุ `PresentationImageEffects`; ค่าจะอยู่ระหว่าง 0.0 (โปร่งใสเต็ม) ถึง 1.0 (ทึบเต็ม).

**Q: ฉันสามารถใส่ลายน้ำลงในสไลด์เฉพาะได้หรือไม่?**  
A: ใช่. ใช้ `PresentationWatermarkOptions.setSlideIndices(int... indices)` เพื่อกำหนดสไลด์แต่ละหมายเลข.

**Q: รูปแบบภาพใดบ้างที่รองรับการใส่ลายน้ำ?**  
A: PNG, JPEG, BMP, GIF, TIFF, และ WebP ทั้งหมดรองรับ, ให้ความยืดหยุ่นสำหรับโลโก้และกราฟิก.

**Q: ฉันควรจัดการกับข้อผิดพลาดระหว่างการประมวลผลลายน้ำอย่างไร?**  
A: ห่อ workflow ด้วยบล็อก try‑catch และจับ `WatermarkException` เพื่อรับรหัสข้อผิดพลาดและข้อความรายละเอียด.

**Q: การประมวลผลเป็นชุดของงานนำเสนอหลายไฟล์เป็นไปได้หรือไม่?**  
A: แน่นอน. วนลูปผ่านคอลเลกชันของเส้นทางไฟล์, สร้าง `Watermarker` สำหรับแต่ละไฟล์, และใช้การกำหนดค่าลายน้ำเดียวกัน.

## แหล่งข้อมูลเพิ่มเติม
- [เอกสารประกอบ](https://docs.groupdocs.com/watermark/java/)  
- [อ้างอิง API](https://reference.groupdocs.com/watermark/java)  
- [ดาวน์โหลด GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [ที่เก็บ GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/watermark/10)  
- [ขอใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

---

**อัปเดตล่าสุด:** 2026-08-04  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_presentation.pptx");
watermarker.close();
```

## บทเรียนที่เกี่ยวข้อง

- [วิธีเพิ่มลายน้ำรูปทรงใน Java สำหรับการนำเสนอ PowerPoint ด้วย GroupDocs.Watermark](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/)
- [วิธีเพิ่มลายน้ำเอฟเฟกต์เส้นใน PowerPoint ด้วย GroupDocs.Watermark และ Java](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)
- [เพิ่มลายน้ำลงในการนำเสนอ PowerPoint ด้วย GroupDocs.Watermark for Java](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)