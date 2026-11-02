---
date: '2026-03-17'
description: เรียนรู้วิธีบันทึกภาพแผนภูมิ PowerPoint และตั้งค่าพื้นหลังแผนภูมิโดยใช้
  Java และ GroupDocs.Watermark ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อการแสดงข้อมูลที่ดียิ่งขึ้น
keywords:
- set chart background image PowerPoint
- Java GroupDocs.Watermark
- PowerPoint presentation enhancement
title: บันทึกภาพแผนภูมิ PowerPoint ด้วย Java & GroupDocs.Watermark
type: docs
url: /th/java/presentation-document-watermarking/set-chart-background-image-powerpoint-java-groupdocs-watermark/
weight: 1
---

# บันทึกภาพแผนภูมิ PowerPoint ด้วย Java & GroupDocs.Watermark

ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีบันทึกภาพแผนภูมิ PowerPoint** และการใช้พื้นหลังแบบกำหนดเอง เพื่อให้การนำเสนอของคุณดูเรียบหรูและสอดคล้องกับแบรนด์ เราจะเดินผ่านกระบวนการทั้งหมดด้วย Java และ GroupDocs.Watermark ตั้งแต่การตั้งค่าห้องสมุดจนถึงการกำหนดค่าความโปร่งแสงและตัวเลือกการทำลายภาพ (tiling).

## คำตอบอย่างรวดเร็ว
- **“save PowerPoint chart” หมายถึงอะไร?** หมายถึงการส่งออกแผนภูมิเป็นส่วนหนึ่งของไฟล์ PowerPoint หลังจากปรับแต่งภาพตามต้องการ.  
- **ไลบรารีใดที่เพิ่มภาพพื้นหลังให้แผนภูมิ?** GroupDocs.Watermark for Java มี API ง่าย ๆ สำหรับตั้งค่าภาพพื้นหลังของแผนภูมิ.  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีสามารถใช้งานเพื่อประเมินได้; จำเป็นต้องมีไลเซนส์เต็มเพื่อการใช้งานในสภาพแวดล้อมการผลิต.  
- **ฉันสามารถทำให้ภาพพื้นหลังเป็นลายต่อเนื่อง (tile) ได้หรือไม่?** ใช่ – ใช้เมธอด `setTileAsTexture(true)` เพื่อทำซ้ำภาพเป็นเทกซ์เจอร์.  
- **Java 8 เพียงพอหรือไม่?** ไลบรารีนี้รองรับ JDK 8 และเวอร์ชันที่ใหม่กว่า.

## “save PowerPoint chart” คืออะไร?
การบันทึกแผนภูมิ PowerPoint หมายถึงการฝังแผนภูมิลงในสไลด์และบันทึกการเปลี่ยนแปลงภาพใด ๆ — เช่นภาพพื้นหลังแบบกำหนดเอง — ลงในไฟล์ `.pptx` สุดท้าย ซึ่งทำให้คุณสามารถแจกจ่ายการนำเสนอที่มีรูปลักษณ์และความรู้สึกตามที่ต้องการแล้ว.

## ทำไมต้องตั้งค่าพื้นหลังแผนภูมิด้วย GroupDocs.Watermark?
- **Brand consistency:** ใช้โลโก้ของบริษัทหรือเทกซ์เจอร์ธีมโดยตรงอยู่ด้านหลังข้อมูลของแผนภูมิ.  
- **Improved readability:** ปรับความโปร่งแสงเพื่อให้จุดข้อมูลยังคงชัดเจนในขณะที่พื้นหลังเพิ่มบริบทภาพ.  
- **Automation:** ผสานกระบวนการนี้เข้ากับบริการ back‑end, pipeline การประมวลผลแบบ batch, หรือ workflow ของ CI/CD.  
- **Performance:** GroupDocs.Watermark จัดการงานนำเสนอขนาดใหญ่ได้อย่างมีประสิทธิภาพ โดยเฉพาะเมื่อคุณทำตามเคล็ดลับการเพิ่มประสิทธิภาพที่ระบุในคู่มือนี้ต่อไป.

## ข้อกำหนดเบื้องต้น

### ไลบรารีที่จำเป็น
- **GroupDocs.Watermark for Java** (รุ่นล่าสุด)  
- Java Development Kit (JDK) ที่ติดตั้งบนเครื่องของคุณ

### การตั้งค่าสภาพแวดล้อม
- IDE เช่น IntelliJ IDEA หรือ Eclipse ที่กำหนดค่าให้ใช้ JDK.  
- Maven สำหรับการจัดการ dependencies.

### ความรู้เบื้องต้นที่ต้องมี
- การเขียนโปรแกรม Java เบื้องต้นและการทำงานกับไฟล์ I/O.  
- ความคุ้นเคยกับโครงสร้างสไลด์และแผนภูมิของ PowerPoint.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การติดตั้งผ่าน Maven
เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดโดยตรงจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับไลเซนส์
- **Free Trial:** สำรวจคุณสมบัติทั้งหมดโดยไม่มีค่าใช้จ่าย.  
- **Temporary License:** ใช้สำหรับช่วงเวลาการประเมินที่ยาวนานขึ้น.  
- **Purchase:** รับไลเซนส์เต็มเพื่อการใช้งานในสภาพแวดล้อมการผลิตโดยไม่มีข้อจำกัด.

## คู่มือการดำเนินการ

### การโหลดไฟล์การนำเสนอ
ขั้นแรก โหลดไฟล์ PowerPoint ที่มีแผนภูมิที่คุณต้องการแก้ไข:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\presentation.pptx", loadOptions);
```
- **Why:** สิ่งนี้สร้างอินสแตนซ์ `Watermarker` ที่ให้คุณเข้าถึงเนื้อหาการนำเสนอผ่านโปรแกรม.

### การดึงและแก้ไขคุณสมบัติของแผนภูมิ
ต่อไป ค้นหาแผนภูมิและโหลดภาพที่คุณต้องการใช้เป็นพื้นหลัง:

```java
PresentationContent content = watermarker.getContent(PresentationContent.class);

// Load image to be set as background for chart.
File imageFile = new File("YOUR_DOCUMENT_DIRECTORY\\test_image.png");
byte[] imageBytes = new byte[(int) imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
```
- **Why:** การแปลงภาพเป็นอาร์เรย์ของไบต์ทำให้ GroupDocs.Watermark สามารถฝังภาพนั้นโดยตรงลงในรูปแบบการเติมของแผนภูมิ.

### การตั้งค่าภาพพื้นหลัง
ตอนนี้ผูกภาพเข้ากับแผนภูมิแรกบนสไลด์แรก:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setBackgroundImage(new PresentationWatermarkableImage(imageBytes));
```
- **Why:** คำเรียกนี้จะแทนที่พื้นหลังแผนภูมิมาตรฐานด้วยภาพที่คุณกำหนดเอง ทำให้ได้ผลลัพธ์ **set chart background**.

### การกำหนดค่าความโปร่งแสงและการทำลายภาพ (Tiling)
ปรับแต่งลักษณะการแสดงผลด้วยความโปร่งแสงและการทำลายเทกซ์เจอร์:

```java
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTransparency(0.5);
content.getSlides().get_Item(0).getCharts().get_Item(0).getImageFillFormat()
    .setTileAsTexture(true);
```
- **Why:** ความโปร่งแสง (`0.5`) ทำให้ข้อมูลยังคงมองเห็นได้ ในขณะที่ `setTileAsTexture(true)` **tile chart background** เพื่อสร้างลายต่อเนื่องที่ไม่มีรอยต่อ.

### การบันทึกและปิดทรัพยากร
สุดท้าย เขียนการนำเสนอที่แก้ไขแล้วลงดิสก์และปล่อยทรัพยากร:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY\\updated_presentation.pptx");
watermarker.close();
```
- **Why:** การบันทึกการเปลี่ยนแปลงทำให้สร้างไฟล์ใหม่ที่คุณสามารถแจกจ่ายได้ และการปิด `Watermarker` จะปล่อยทรัพยากรของระบบ.

## การประยุกต์ใช้งานจริง
1. **Corporate Reports:** แทรกโลโก้หรือสีของบริษัทเป็นพื้นหลังของแผนภูมิ.  
2. **Educational Slides:** ใช้ภาพธีม (เช่น แผนที่, โมเลกุล) เพื่อทำให้ข้อมูลน่าสนใจยิ่งขึ้น.  
3. **Marketing Decks:** เพิ่มเทกซ์เจอร์หรือกราฟิกสไตล์ลายน้ำเพื่อทำให้สไลด์ของคุณแตกต่างจากคู่แข่ง.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Resize images** ก่อนฝังเพื่อให้ขนาดไฟล์อยู่ในระดับที่จัดการได้.  
- **Use try‑with‑resources** สำหรับสตรีมเพื่อรับประกันการทำความสะอาดอัตโนมัติ.  
- **Avoid loading large presentations** เข้าไปในหน่วยความจำทั้งหมดพร้อมกัน; ประมวลผลสไลด์แบบเพิ่มทีละส่วนเมื่อทำได้.

## ข้อผิดพลาดทั่วไปและการแก้ปัญหา

| ปัญหา | วิธีแก้ |
|-------|----------|
| `OutOfMemoryError` เมื่อจัดการกับภาพขนาดใหญ่ | ปรับขนาดภาพหรือใช้การโหลดแบบอิง `InputStream` แทนการอ่านไฟล์ทั้งหมดเป็นอาร์เรย์ไบต์. |
| ภาพพื้นหลังไม่ปรากฏ | ตรวจสอบว่า `ImageFillFormat` ของแผนภูมิไม่ได้ถูกเขียนทับในโค้ดภายหลัง. |
| ความโปร่งแสงดูมืดเกินไป | ปรับค่าที่ส่งให้กับ `setTransparency()` (ช่วง 0.0–1.0). |

## คำถามที่พบบ่อย

**Q: ความแตกต่างระหว่าง `setBackgroundImage` กับ `add watermark chart` คืออะไร?**  
A: `setBackgroundImage` แทนที่การเติมของแผนภูมิด้วยภาพ, ในขณะที่การเพิ่ม watermark chart จะวางข้อความหรือกราฟิกกึ่งโปร่งแสงทับบนข้อมูลของแผนภูมิ.

**Q: ฉันสามารถใช้พื้นหลังเดียวกันกับหลายแผนภูมิพร้อมกันได้หรือไม่?**  
A: ใช่—วนลูปผ่าน `content.getSlides().get_Item(i).getCharts()` และใช้ `PresentationWatermarkableImage` เดียวกันกับ `ImageFillFormat` ของแต่ละแผนภูมิ.

**Q: GroupDocs.Watermark รองรับ GIF แบบเคลื่อนไหวเป็นพื้นหลังของแผนภูมิหรือไม่?**  
A: ไลบรารีจะถือ GIF เป็นภาพคงที่; ใช้เฉพาะเฟรมแรกเท่านั้น.

**Q: ฉันจะทำให้พื้นหลังสเกลอย่างถูกต้องบนสไลด์ที่มีขนาดต่างกันได้อย่างไร?**  
A: ใช้ `setTileAsTexture(true)` เพื่อทำให้ภาพเป็นลายต่อเนื่อง หรือคำนวณขนาดที่เหมาะสมตามความกว้างและความสูงของสไลด์ก่อนตั้งค่าพื้นหลัง.

**Q: มีวิธีตรวจสอบโปรแกรมmatically ว่าแผนภูมิมีภาพพื้นหลังหรือไม่?**  
A: คุณสามารถตรวจสอบ `getImageFillFormat().getBackgroundImage()`; หากคืนค่า `null` แสดงว่าไม่มีการตั้งค่าภาพ.

## แหล่งข้อมูล
- **เอกสาร**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)
- **อ้างอิง API**: [GroupDocs.Watermark API Reference](https://reference.groupdocs.com/watermark/java)
- **ดาวน์โหลด**: [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)
- **ที่เก็บ GitHub**: [GroupDocs.Watermark on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **ฟอรั่มสนับสนุนฟรี**: [GroupDocs Watermark Forum](https://forum.groupdocs.com/c/watermark/10)
- **ไลเซนส์ชั่วคราว**: [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**อัปเดตล่าสุด:** 2026-03-17  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs