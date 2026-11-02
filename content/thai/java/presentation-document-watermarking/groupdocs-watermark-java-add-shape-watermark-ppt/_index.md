---
date: '2026-05-27'
description: เรียนรู้วิธีใช้ GroupDocs เพื่อเพิ่ม shape watermarks ให้กับไฟล์ PPT
  ด้วย Java คู่มือขั้นตอนต่อขั้นตอน, เคล็ดลับการกำหนดค่า, และข้อมูลเชิงประสิทธิภาพ
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: วิธีใช้ GroupDocs เพื่อเพิ่ม Shape Watermarks ใน Java สำหรับการนำเสนอ PowerPoint
type: docs
url: /th/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# วิธีใช้ GroupDocs เพื่อเพิ่มลายน้ำรูปทรงใน Java สำหรับการนำเสนอ PowerPoint

การปกป้องสไลด์ PowerPoint ของคุณเป็นสิ่งสำคัญสำหรับความสอดคล้องของแบรนด์และความปลอดภัยของข้อมูล ในบทเรียนนี้คุณจะได้ค้นพบ **วิธีใช้ GroupDocs** เพื่อฝังลายน้ำรูปทรงโดยตรงลงในไฟล์ PPTX ด้วย Java ให้คุณมีวิธีที่เชื่อถือได้และเป็นโปรแกรมเพื่อทำแบรนด์ให้กับทุกสไลด์

## คำตอบสั้น
- **ไลบรารีใดที่เพิ่มลายน้ำให้กับ PPTX ใน Java?** GroupDocs.Watermark.  
- **คลาสใดที่โหลดการนำเสนอ?** `PresentationLoadOptions`.  
- **คลาสใดที่ใช้ใส่ลายน้ำ?** `Watermarker`.  
- **ฉันต้องการไลเซนส์สำหรับการพัฒนาหรือไม่?** เวอร์ชันทดลองฟรีใช้ได้สำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์แบบชำระเงินสำหรับการใช้งานจริง.  
- **ฉันสามารถใส่ลายน้ำไฟล์ขนาดใหญ่ (>500 MB) ได้หรือไม่?** ได้ – GroupDocs ประมวลผลไฟล์ได้ถึง 2 GB โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ.

## GroupDocs.Watermark คืออะไร?
`GroupDocs.Watermark` เป็น Java SDK ที่ช่วยให้คุณเพิ่มลายน้ำข้อความ, รูปภาพ หรือรูปทรงลงในเอกสารกว่า 100 รูปแบบ รวมถึง PPT, PPTX, PDF, และ DOCX มันประมวลผลไฟล์ได้ถึง 2 GB พร้อมการใช้หน่วยความจำน้อย ไลบรารียังให้ API สำหรับปรับความทึบ, การหมุน, และตำแหน่ง เพื่อให้ลายน้ำรวมเข้ากับเลย์เอาต์สไลด์ที่มีอยู่อย่างไร้รอยต่อ

## ทำไมต้องเพิ่มลายน้ำรูปทรงในการนำเสนอ PowerPoint?
ลายน้ำรูปทรงช่วยรักษาความสอดคล้องของภาพทั่วสไลด์และสามารถกำหนดตำแหน่งได้อย่างแม่นยำด้วยพิกัดเวกเตอร์ ทำให้คุณจัดตำแหน่งองค์ประกอบแบรนด์ได้ตรงตามที่ต้องการ พวกมันยังคงแก้ไขได้เป็นรูปทรง PowerPoint ดั้งเดิม เพื่อให้การแก้ไขต่อไปของการนำเสนอไม่ทำให้ลักษณะและตำแหน่งของลายน้ำเปลี่ยนไป ประโยชน์ที่วัดได้รวมถึง:
- **50+** สไตล์ลายน้ำ (ข้อความ, รูปภาพ, รูปทรง) ที่รองรับ.  
- **100 %** ความแม่นยำของเลย์เอาต์ – รูปทรงยังคงจัดตำแหน่งหลังการแก้ไข.  
- **รองรับไฟล์ขนาดถึง 2 GB** โดยไม่ต้องโหลดเอกสารทั้งหมด ลดการใช้หน่วยความจำลง **70 %** เมื่อเทียบกับวิธีที่ไม่ประหยัด.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8+** ติดตั้งแล้ว.  
- **Maven** สำหรับการจัดการ dependencies.  
- IDE เช่น **IntelliJ IDEA** หรือ **Eclipse**.  
- ความรู้พื้นฐาน Java และความคุ้นเคยกับ Maven.  
- เข้าถึงไลเซนส์ **GroupDocs.Watermark** (ทดลองหรือเชิงพาณิชย์).

### ไลบรารีและเวอร์ชันที่ต้องการ
- **GroupDocs.Watermark for Java** เวอร์ชัน **24.11** หรือใหม่กว่า.

### ข้อกำหนดการตั้งค่าสภาพแวดล้อม
- ตรวจสอบให้แน่ใจว่า `JAVA_HOME` ชี้ไปยัง JDK ของคุณ.  
- กำหนดค่า `pom.xml` ของโปรเจกต์ของคุณตามที่แสดงด้านล่าง.

## วิธีเพิ่มลายน้ำรูปทรงในไฟล์ PowerPoint ด้วย GroupDocs.Watermark ใน Java?
`PresentationLoadOptions` ระบุตัวเลือกสำหรับการโหลดไฟล์ PowerPoint เช่น การเลือกสไลด์และการจัดการรหัสผ่าน.  
`Watermarker` เป็นคลาสหลักที่โหลดเอกสารและใส่ลายน้ำ.  

โหลดการนำเสนอด้วย `PresentationLoadOptions`, สร้างอินสแตนซ์ `Watermarker`, กำหนดลายน้ำรูปทรง, ใส่ลงในแต่ละสไลด์, และสุดท้ายบันทึกไฟล์ การไหลงานแบบครบวงจรนี้ต้องใช้เพียงไม่กี่บรรทัดของโค้ดและทำงานภายในไม่กี่วินาทีสำหรับชุดสไลด์ประมาณ 10 สไลด์.

### การกำหนดค่า Maven
Add the following dependency to your `pom.xml` file:

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

### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับไลเซนส์
รับไลเซนส์ทดลองหรือไลเซนส์ชั่วคราวเพื่อสำรวจคุณสมบัติทั้งหมดของ GroupDocs.Watermark สำหรับการใช้งานในสภาพแวดล้อมจริง ให้ซื้อไลเซนส์ที่ตรงกับขนาดการปรับใช้ของคุณ.

#### การเริ่มต้นและตั้งค่าพื้นฐาน
`Watermarker` เป็นคลาสหลักที่โหลดเอกสารและใส่ลายน้ำ.  
`PresentationLoadOptions` ให้ตัวเลือกสำหรับการโหลดไฟล์ PowerPoint เช่น การจัดการสไลด์และการรักษาแอนิเมชัน.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### ขั้นตอน 1: สร้างลายน้ำรูปทรง
`ShapeWatermarkOptions` กำหนดคุณสมบัติดีไซน์ของลายน้ำรูปทรง รวมถึงขนาด, สี, ความทึบ, และการหมุน.

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### ขั้นตอน 2: ใส่ลายน้ำลงในทุกสไลด์
วนลูปผ่านแต่ละสไลด์ในการนำเสนอและเพิ่มลายน้ำรูปทรง.

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### ขั้นตอน 3: บันทึกการนำเสนอที่มีลายน้ำ
เลือกรูปแบบเอาต์พุต (PPTX) และบันทึกไฟล์ SDK จะรักษาเนื้อหาและแอนิเมชันของสไลด์เดิมไว้.

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### ปัญหาและวิธีแก้ไขทั่วไป
- **ข้อผิดพลาดไลเซนส์หาย:** ตรวจสอบให้แน่ใจว่าไฟล์ไลเซนส์อยู่ใน classpath หรือกำหนดผ่าน `License.setLicense("path/to/license.lic")`.  
  คลาส `License` โหลดและใช้ไฟล์ไลเซนส์ของ GroupDocs เพื่อเปิดใช้งานฟังก์ชันเต็มของ SDK.  
- **รูปทรงไม่แสดง:** เพิ่มความทึบของรูปทรงหรือความคอนทราสต์ของสี; ความทึบเริ่มต้นคือ 0.2.  
- **ความช้าของไฟล์ขนาดใหญ่:** ใช้ `PresentationLoadOptions.setLoadAllSlides(false)` เพื่อโหลดสไลด์ตามต้องการ ลดการใช้หน่วยความจำ.

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถเพิ่มลายน้ำหลายรายการในสไลด์เดียวได้หรือไม่?**  
ตอบ: ได้ – เรียก `watermarker.add()` หลายครั้งพร้อม `ShapeWatermarkOptions` ที่แตกต่างกันสำหรับแต่ละลายน้ำ.

**ถาม: GroupDocs.Watermark รองรับไฟล์ PPTX ที่มีการป้องกันด้วยรหัสผ่านหรือไม่?**  
ตอบ: แน่นอน. ให้ใส่รหัสผ่านใน `PresentationLoadOptions.setPassword("yourPassword")` ก่อนการโหลด.

**ถาม: สามารถใส่ลายน้ำเฉพาะสไลด์ที่เลือกได้หรือไม่?**  
ตอบ: ได้ – ระบุดัชนีสไลด์ในเมธอด `add` แทนการวนลูปทั้งหมด.

**ถาม: เวอร์ชัน Java ใดที่เข้ากันได้?**  
ตอบ: SDK ทำงานกับ Java 8 ถึง Java 21 ครอบคลุมทั้งสภาพแวดล้อมเก่าและใหม่.

**ถาม: ไลบรารีจัดการกับรูปทรงที่มีแอนิเมชันอย่างไร?**  
ตอบ: ลายน้ำรูปทรงเป็นแบบคงที่ตามการออกแบบ; ไม่ขัดแย้งกับแอนิเมชันที่มีอยู่บนสไลด์.

---

**อัปเดตล่าสุด:** 2026-05-27  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [เพิ่มลายน้ำในการนำเสนอ PowerPoint ด้วย GroupDocs.Watermark สำหรับ Java](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [วิธีเพิ่มลายน้ำข้อความในรูปภาพ PowerPoint ด้วย GroupDocs.Watermark สำหรับ Java](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [วิธีเพิ่มลายน้ำเอฟเฟกต์เส้นใน PowerPoint ด้วย GroupDocs.Watermark และ Java](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)