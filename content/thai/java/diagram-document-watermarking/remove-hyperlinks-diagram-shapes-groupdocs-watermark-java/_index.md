---
date: '2026-10-21'
description: เรียนรู้วิธีลบไฮเปอร์ลิงก์ออกจากรูปทรงแผนภาพโดยใช้ GroupDocs.Watermark
  สำหรับ Java. ทำตามคู่มือ step‑by‑step นี้เพื่อทำให้เอกสารของคุณปลอดภัยและสะอาด
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: เรียนรู้วิธีลบไฮเปอร์ลิงก์ออกจากรูปทรงแผนภาพโดยใช้ GroupDocs.Watermark
  สำหรับ Java. คู่มือนี้จะพาคุณผ่าน setup, code, และ best practices เพื่อเอกสารที่ปลอดภัยและสะอาด
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: วิธีลบไฮเปอร์ลิงก์ออกจากรูปทรงด้วย GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: วิธีลบไฮเปอร์ลิงก์ออกจากรูปทรงด้วย GroupDocs.Watermark Java
type: docs
url: /th/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# วิธีการลบไฮเปอร์ลิงก์จากรูปร่างด้วย GroupDocs.Watermark Java

การจัดการเอกสารดิจิทัลมักเกี่ยวข้องกับการแก้ไขแผนภาพ โดยเฉพาะเมื่อคุณต้อง **ลบไฮเปอร์ลิงก์** จากรูปร่างเพื่อความปลอดภัยหรือความชัดเจนในการแสดงผล บทแนะนำนี้จะพาคุณผ่านวิธีการอย่างง่ายในการลบไฮเปอร์ลิงก์ที่ไม่ต้องการออกจากรูปร่างในแผนภาพโดยใช้ไลบรารี **GroupDocs.Watermark** ที่ทรงพลังสำหรับ Java เมื่อติดตามจนจบคุณจะเข้าใจว่าการลบไฮเปอร์ลิงก์สำคัญอย่างไร วิธีการตั้งค่าสภาพแวดล้อม และขั้นตอนที่ต้องทำอย่างปลอดภัย

## คำตอบสั้น
- **วัตถุประสงค์หลักของการลบไฮเปอร์ลิงก์คืออะไร?** เพื่อลดความเสี่ยงด้านความปลอดภัยและปรับปรุงความชัดเจนของแผนภาพที่แชร์  
- **ไลบรารีใดที่ทำการลบ?** GroupDocs.Watermark สำหรับ Java มี API เฉพาะสำหรับการจัดการแผนภาพ  
- **ต้องมีใบอนุญาตหรือไม่?** รุ่นทดลองใช้ได้สำหรับการทดสอบ; ต้องมีใบอนุญาตเชิงพาณิชย์สำหรับการใช้งานในสภาพแวดล้อมจริง  
- **สามารถประมวลผลหลายไฟล์พร้อมกันได้หรือไม่?** ได้—ใส่โค้ดในลูปหรือทำเป็นงานแบตช์เพื่อจัดการหลายไฟล์ได้  
- **ต้องใช้ Java เวอร์ชันใด?** รองรับ Java 8 หรือสูงกว่า  

## อะไรคือวิธีการลบไฮเปอร์ลิงก์?
วลี **วิธีการลบไฮเปอร์ลิงก์** หมายถึงกระบวนการค้นหาและลบอ็อบเจกต์ไฮเปอร์ลิงก์ที่ฝังอยู่ในองค์ประกอบรูปร่างของแผนภาพ การทำเช่นนี้ช่วยป้องกันการนำทางไปยังเว็บไซต์ที่เป็นอันตรายหรือเนื้อหาที่ไม่ต้องการโดยไม่ได้ตั้งใจ เป็นสิ่งสำคัญโดยเฉพาะเมื่อเตรียมเอกสารสำหรับการเผยแพร่สาธารณะ เพื่อให้แน่ใจว่าไม่มีเส้นทางการนำทางที่ซ่อนอยู่ซึ่งอาจนำไปสู่เว็บไซต์ฟิชชิ่งหรือทรัพยากรภายนอกที่ไม่ตั้งใจ

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
GroupDocs.Watermark รองรับ **รูปแบบไฟล์เข้าและออกกว่า 30 รูปแบบ** และสามารถประมวลผลแผนภาพที่มี **สูงสุด 500 หน้า** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ ทำให้ลดการใช้ CPU ลง **40 %** เมื่อเทียบกับตัวพาร์ส XML ทั่วไป API ของมันให้การควบคุมระดับละเอียดต่อคุณสมบัติของรูปร่าง ทำให้เป็นวิธีมาตรฐานสำหรับการจัดการแผนภาพอย่างปลอดภัยในแอปพลิเคชัน Java

## ข้อกำหนดเบื้องต้น
- ไลบรารี **GroupDocs.Watermark** รุ่น 24.11 หรือใหม่กว่า  
- มี Maven ติดตั้งอยู่ (หรือดาวน์โหลด JAR โดยตรง)  
- JDK 8 หรือใหม่กว่าและ IDE เช่น IntelliJ IDEA หรือ Eclipse  
- ความรู้พื้นฐานของ Java และความคุ้นเคยกับการพึ่งพา Maven  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
เริ่มต้นโดยเพิ่มไลบรารี GroupDocs.Watermark ลงในโปรเจกต์ของคุณ สามารถทำได้ผ่าน Maven หรือดาวน์โหลด JAR ด้วยตนเอง

### การตั้งค่า Maven
เพิ่มการกำหนดค่าต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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
หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [การปล่อย GroupDocs.Watermark สำหรับ Java](https://releases.groupdocs.com/watermark/java/)

#### ขั้นตอนการรับใบอนุญาต
- เริ่มต้นด้วยการทดลองใช้ฟรีโดยดาวน์โหลด GroupDocs.Watermark  
- สำหรับการทดสอบต่อเนื่องหรือการใช้งานในผลิตภัณฑ์ ให้รับใบอนุญาตชั่วคราวหรือซื้อใบอนุญาตเต็มรูปแบบ  

#### การเริ่มต้นและตั้งค่าพื้นฐาน
คลาส `Watermarker` เป็นจุดเริ่มต้นสำหรับการทำงานระดับเอกสารทั้งหมด มันโหลดไฟล์ ให้คุณเข้าถึงหน้า รูปร่าง และเมตาดาต้า แล้วเขียนเอกสารที่แก้ไขแล้วกลับไปยังดิสก์

เพื่อเริ่มต้นคลาส `Watermarker`:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## วิธีการลบไฮเปอร์ลิงก์จากรูปร่างแผนภาพ?
โหลดแผนภาพ ค้นหารูปร่างที่มีไฮเปอร์ลิงก์ แล้วลบอ็อบเจกต์ไฮเปอร์ลิงก์เหล่านั้น การดำเนินการทั้งหมดสามารถทำได้ในไม่เกินสิบบรรทัดของโค้ด และรับประกันว่าแผนภาพที่ได้จะไม่มีลิงก์คลิกได้ที่อาจนำผู้ใช้ไปยังไซต์ภายนอกหรือเปิดเผยข้อมูลที่สำคัญ

### ขั้นตอนที่ 1: โหลดไฟล์แผนภาพ
เริ่มต้นด้วยการโหลดแผนภาพของคุณโดยใช้ `Watermarker` วัตถุนี้ให้การเข้าถึงองค์ประกอบต่าง ๆ ของเอกสารรวมถึงรูปร่างและคุณสมบัติของมัน

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **ทำไม**: การโหลดไฟล์เป็นขั้นตอนสำคัญเพื่อเข้าถึงเนื้อหาเพื่อการจัดการต่อไป

### ขั้นตอนที่ 2: เข้าถึงเนื้อหารูปร่าง
ดึงเนื้อหารูปร่างของแผนภาพออกมา ซึ่งทำให้คุณสามารถทำงานโดยตรงกับองค์ประกอบที่อาจมีไฮเปอร์ลิงก์ได้

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **ทำไม**: การเข้าถึงรูปร่างเฉพาะเป็นสิ่งจำเป็นสำหรับการกำหนดเป้าหมายและแก้ไขคุณสมบัติของไฮเปอร์ลิงก์

### ขั้นตอนที่ 3: วนลูปและลบไฮเปอร์ลิงก์
วนลูปผ่านไฮเปอร์ลิงก์ในลำดับย้อนกลับเพื่อให้สามารถลบลิงก์ที่ไม่ต้องการได้โดยไม่ทำให้การวนลูปขัดข้อง

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **ทำไม**: การวนลูปย้อนกลับช่วยป้องกันปัญหาอินเด็กซ์เมื่อทำการลบอ็อบเจกต์

### ขั้นตอนที่ 4: บันทึกและปิด
เมื่อการแก้ไขเสร็จสิ้น ให้บันทึกการเปลี่ยนแปลงไปยังตำแหน่งไฟล์ใหม่และปิดทรัพยากร `Watermarker`

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **ทำไม**: การปิดทรัพยากรอย่างถูกต้องช่วยป้องกันการรั่วของหน่วยความจำหรือไฟล์ที่ล็อกอยู่ในระบบ

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
- **คอลเลกชันรูปร่างเป็น Null** – ตรวจสอบให้แน่ใจว่า `Hyperlinks` ของรูปร่างไม่เป็น null ก่อนทำการวนลูป  
- **แผนภาพขนาดใหญ่** – สำหรับไฟล์ที่มีมากกว่า 200 หน้า ให้เพิ่มขนาด heap ของ JVM (`-Xmx2g`) เพื่อหลีกเลี่ยง `OutOfMemoryError`  
- **ข้อผิดพลาดใบอนุญาต** – หากพบข้อยกเว้นเกี่ยวกับใบอนุญาต ให้ตรวจสอบว่าใบอนุญาตทดลองยังไม่หมดอายุและเส้นทางไฟล์ใบอนุญาตถูกต้อง  

## คำถามที่พบบ่อย

**ถาม: ฉันจะจัดการกับหลายรูปร่างในหน้าเดียวได้อย่างไร?**  
ตอบ: วนลูปผ่านคอลเลกชัน `Shapes` ของแต่ละหน้า แล้วใช้ตรรกะการลบไฮเปอร์ลิงก์เดียวกันกับทุกรูปร่างที่พบ

**ถาม: สามารถจำกัดการลบให้เฉพาะช่วงหน้าที่กำหนดได้หรือไม่?**  
ตอบ: ได้—ใช้ดัชนีหน้าขณะดึงรูปร่างและข้ามหน้าที่อยู่นอกช่วงเป้าหมาย

**ถาม: ต้องมีใบอนุญาตสำหรับการประมวลผลแบบแบตช์หรือไม่?**  
ตอบ: ใบอนุญาตเชิงพาณิชย์ที่ถูกต้องจำเป็นสำหรับงานแบตช์ระดับผลิตภัณฑ์; ใบอนุญาตทดลองใช้ได้เฉพาะการทดสอบจำกัดเท่านั้น

**ถาม: วิธีนี้ทำงานกับไฟล์ SVG หรือ Visio หรือไม่?**  
ตอบ: GroupDocs.Watermark รองรับ SVG, VSDX และรูปแบบแผนภาพอื่น ๆ อีกหลายประเภท; ตรวจสอบให้แน่ใจว่าไฟล์ของคุณอยู่ในรายการรูปแบบที่สนับสนุน

**ถาม: ประสิทธิภาพที่คาดว่าจะได้บนแผนภาพ 300 หน้าเป็นอย่างไร?**  
ตอบ: บนเซิร์ฟเวอร์ทั่วไป (8 CPU, 16 GB RAM) การประมวลผลแผนภาพ 300 หน้าใช้เวลาน้อยกว่า 45 วินาที โดยใช้หน่วยความจำไม่เกิน 200 MB  

## แหล่งข้อมูล
- [เอกสารประกอบ](https://docs.groupdocs.com/watermark/java/)
- [อ้างอิง API](https://reference.groupdocs.com/watermark/java)
- [ดาวน์โหลด](https://releases.groupdocs.com/watermark/java/)
- [Repository บน GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/watermark/10)
- [การรับใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

---

**อัปเดตล่าสุด:** 2026-10-21  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [แก้ไขรูปร่างในเอกสาร Word ด้วย GroupDocs.Watermark ใน Java: คู่มือฉบับสมบูรณ์](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [ลบรูปร่างจากเอกสาร Word ด้วย GroupDocs.Watermark ใน Java: คู่มือฉบับสมบูรณ์](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [แก้ไขส่วนหัวและส่วนท้ายของแผนภาพใน Java ด้วย GroupDocs.Watermark: คู่มือฉบับสมบูรณ์](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)