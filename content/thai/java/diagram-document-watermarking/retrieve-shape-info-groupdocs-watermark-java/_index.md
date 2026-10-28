---
date: '2026-02-13'
description: เรียนรู้วิธีสกัดรูปทรงและสกัดภาพจากรูปทรงด้วย GroupDocs.Watermark สำหรับ
  Java เพื่อดึงข้อมูลแผนภาพโดยละเอียดอย่างมีประสิทธิภาพ
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: วิธีดึงรูปทรงจากแผนภาพโดยใช้ GroupDocs.Watermark ใน Java
type: docs
url: /th/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

ed With:" -> "**ทดสอบกับ:**". "Author:" -> "**ผู้เขียน:**". Keep values unchanged.

Now produce final markdown with Thai translations.

Check for any missing placeholders: CODE_BLOCK_0 etc. Keep them.

Make sure no extra spaces that break formatting.

Now produce final answer.# วิธีการดึงรูปร่างจากแผนภาพโดยใช้ GroupDocs.Watermark ใน Java

เมื่อคุณต้องการ **วิธีการดึงรูปร่าง** จากแผนภาพสไตล์ Visio อย่างเป็นโปรแกรม, ไลบรารี GroupDocs.Watermark จะมอบวิธีที่สะอาดและเน้น Java เพื่อดึงรายละเอียดทั้งหมด—ขนาด, ตำแหน่ง, ภาพที่ฝังอยู่, และแม้แต่ข้อความภายในแต่ละรูปร่าง ในบทแนะนำนี้คุณจะได้เห็น **วิธีการดึงรูปร่าง** อย่างชัดเจน, เหตุผลที่สำคัญ, และโค้ดขั้นตอนต่อขั้นตอนที่คุณสามารถคัดลอกไปใช้ในโปรเจคของคุณ

## คำตอบอย่างรวดเร็ว
- **ไลบรารีที่จัดการการดึงรูปร่างคืออะไร?** GroupDocs.Watermark for Java  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า  
- **สามารถรับข้อมูลภาพจากรูปร่างได้หรือไม่?** ใช่ – ใช้ `shape.getImage()`  
- **ข้อความภายในรูปร่างสามารถเข้าถึงได้หรือไม่?** แน่นอน, ผ่าน `shape.getText()`  
- **ต้องการใบอนุญาตสำหรับการผลิตหรือไม่?** จำเป็นต้องมีใบอนุญาต GroupDocs.Watermark ที่ถูกต้อง  

## บทนำ

การจัดการแผนภาพที่ซับซ้อนมักต้องการการเข้าถึงข้อมูลรายละเอียดของส่วนประกอบต่าง ๆ เช่น รูปร่างและภาพ หากคุณเคยต้องการดึงข้อมูลเช่น ขนาด, ตำแหน่ง, หรือข้อความที่เชื่อมโยงกับรูปร่างในแผนภาพโดยใช้ Java อย่างเป็นโปรแกรม, บทแนะนำนี้เหมาะกับคุณ การใช้ประโยชน์จากพลังของไลบรารี GroupDocs.Watermark สามารถทำให้กระบวนการนี้ง่ายขึ้นในแอปพลิเคชัน Java ในคู่มือนี้เราจะอธิบาย **วิธีการดึงรูปร่าง** จากไฟล์แผนภาพและยังแสดงวิธี **ดึงภาพจากรูปร่าง** และ **ดึงข้อความจากรูปร่าง**

## “วิธีการดึงรูปร่าง” คืออะไร?

การดึงรูปร่างหมายถึงการอ่านวัตถุภายในของแผนภาพ (หน้า, รูปร่าง, ภาพ, ข้อความ) เพื่อให้คุณสามารถวิเคราะห์, แปลง, หรือใช้ซ้ำในแอปพลิเคชันอื่น ๆ—เหมาะสำหรับการอัตโนมัติ, รายงาน, หรือการรวมเข้ากับเครื่องมือ CAD

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับการดึงรูปร่าง?

- **รองรับรูปแบบเต็ม** – ทำงานกับ VSDX, VDX, และหลายประเภทแผนภาพอื่น ๆ  
- **โมเดลวัตถุที่ครอบคลุม** – ให้การเข้าถึงโดยตรงต่อเรขาคณิตของรูปร่าง, ภาพ, และข้อความ  
- **ไม่มีการพึ่งพาภายนอก** – Java แท้, ง่ายต่อการฝังในโปรเจค Maven  

## ข้อกำหนดเบื้องต้น

- **GroupDocs.Watermark for Java** (เวอร์ชัน 24.11 หรือใหม่กว่า)  
- Java Development Kit (JDK) 8 หรือสูงกว่า  
- Maven สำหรับการจัดการ dependencies  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

Add the library to your Maven `pom.xml`:

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

You can also download the latest binaries from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### ขั้นตอนการรับใบอนุญาต
- **ทดลองใช้ฟรี:** ดาวน์โหลดแพ็คเกจทดลองเพื่อประเมิน API.  
- **ใบอนุญาตชั่วคราว:** ขอคีย์ชั่วคราวสำหรับการทดสอบต่อเนื่อง.  
- **ซื้อ:** รับใบอนุญาตเต็มสำหรับการใช้งานในผลิตภัณฑ์.  

### การเริ่มต้นและการตั้งค่าเบื้องต้น

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## วิธีการดึงรูปร่าง – คู่มือการทำงาน

### โหลดและดึงเนื้อหา

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

### วนลูปผ่านรูปร่าง

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

### วิธีการดึงภาพจากรูปร่าง

`shape.getImage()` จะคืนค่าอ็อบเจกต์ที่มีบิตแมพดิบ, ขนาดของมัน, และอาร์เรย์ของไบต์ ใช้คุณสมบัติที่แสดงข้างต้นเพื่อบันทึกภาพลงดิสก์หรือส่งต่อไปยังกระบวนการประมวลผลอื่น

### วิธีการดึงข้อความจากรูปร่าง

`shape.getText()` จะคืนค่าข้อความธรรมดาภายในรูปร่าง หากรูปร่างไม่มีข้อความเมธอดจะคืนค่า `null` ลูปตัวอย่างได้พิมพ์ข้อความแล้วและคุณสามารถจัดการต่อได้ เช่น การสร้างดัชนีของป้ายชื่อทั้งหมดของรูปร่าง

## เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบเส้นทางไฟล์และสิทธิ์การอ่าน.  
- ตรวจสอบว่าคุณกำลังใช้รูปแบบแผนภาพที่รองรับ (VSDX, VDX, ฯลฯ).  
- หากรูปร่างปรากฏโดยไม่มีข้อมูลที่คาดหวัง ให้ตรวจสอบบันทึกการปล่อยของไลบรารีสำหรับข้อผิดพลาดเฉพาะรูปแบบ.  

## การประยุกต์ใช้งานจริง

1. **การวิเคราะห์แผนภาพ:** ตรวจสอบแผนภาพโดยอัตโนมัติเพื่อความสอดคล้องโดยการตรวจสอบขนาดของรูปร่างหรือป้ายชื่อที่หายไป.  
2. **การแสดงข้อมูล:** ส่งขนาดที่ดึงออกมาลงในแดชบอร์ดรายงานเพื่อแสดงความหนาแน่นของการจัดวาง.  
3. **การรวมกับ CAD:** รวมข้อมูลรูปร่างกับ API ของ CAD เพื่อซิงโครไนซ์สเปคการออกแบบระหว่างเครื่องมือต่าง ๆ.  

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **ปิดทรัพยากร:** เรียก `watermarker.close()` เมื่อเสร็จเพื่อปล่อยทรัพยากรเนทีฟ.  
- **การจัดการหน่วยความจำ:** แผนภาพขนาดใหญ่อาจใช้ heap มาก; ควรตรวจสอบหน่วยความจำและเพิ่ม `-Xmx` หากจำเป็น.  
- **การประมวลผลเป็นชุด:** ประมวลผลไฟล์เป็นชุดและใช้ `Watermarker` ตัวเดียวซ้ำเมื่อทำได้.  

## สรุป

โดยการทำตามคู่มือนี้คุณจะรู้ **วิธีการดึงรูปร่าง**, วิธี **ดึงภาพจากรูปร่าง**, และวิธี **ดึงข้อความจากรูปร่าง** ด้วย GroupDocs.Watermark สำหรับ Java เทคนิคเหล่านี้เปิดประตูสู่การวิเคราะห์แผนภาพอัตโนมัติ, รายงาน, และการรวมกับระบบวิศวกรรมอื่น ๆ ขั้นตอนต่อไปคือสำรวจ API ทั้งหมดโดยดูที่ [documentation](https://docs.groupdocs.com/watermark/java/) และลองผสานการดึงรูปร่างกับตรรกะธุรกิจที่กำหนดเอง

## ส่วนคำถามที่พบบ่อย

1. **GroupDocs.Watermark คืออะไร?**  
   - ไลบรารี Java ครบวงจรที่ออกแบบมาสำหรับการใส่ลายน้ำและการดึงข้อมูลจากรูปแบบเอกสารต่าง ๆ รวมถึงแผนภาพ.  

2. **ฉันสามารถใช้ไลบรารีนี้ประมวลผลไฟล์แผนภาพทุกประเภทได้หรือไม่?**  
   - ได้, แต่ต้องตรวจสอบว่ารูปแบบไฟล์ได้รับการสนับสนุนโดยดูที่ [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **ฉันจะดึงมิติและตำแหน่งของรูปร่างจากแผนภาพโดยใช้ Java และ GroupDocs.Watermark อย่างไร?**  
   - โหลดแผนภาพ, เข้าถึง `DiagramContent`, แล้ววนลูปรูปร่างเพื่อรับคุณสมบัติเช่น ความกว้าง, ความสูง, X, และ Y.  

4. **GroupDocs.Watermark สามารถดึงภาพที่ฝังอยู่ในรูปร่างของแผนภาพด้วย Java ได้หรือไม่?**  
   - ได้, มันมีเมธอดเพื่อเข้าถึงข้อมูลภาพภายในรูปร่าง รวมถึงขนาดและข้อมูลพิกเซล, มีประโยชน์สำหรับการวิเคราะห์หรือการแก้ไข.  

5. **ข้อกำหนดเบื้องต้นสำหรับการดึงข้อมูลรูปร่างของแผนภาพใน Java มีอะไรบ้าง?**  
   - Java JDK 8+, การตั้งค่า Maven, ไลบรารี GroupDocs.Watermark (24.11+), และความรู้พื้นฐานของ Java เป็นสิ่งจำเป็นสำหรับการนำไปใช้.  

---

**อัปเดตล่าสุด:** 2026-02-13  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs