---
date: '2026-01-23'
description: เรียนรู้วิธีใส่ลายน้ำไฟล์ PDF ด้วยลายน้ำข้อความและภาพโดยใช้ GroupDocs.Watermark
  สำหรับ Java – คู่มือฉบับสมบูรณ์สำหรับความปลอดภัยของเอกสาร PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: วิธีใส่ลายน้ำ PDF ด้วย GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# วิธีใส่ลายน้ำ PDF ด้วย GroupDocs.Watermark สำหรับ Java

ในโลกดิจิทัลของวันนี้ การ **how to watermark PDF** เป็นคำถามที่พบบ่อยสำหรับผู้ที่ต้องการปกป้องทรัพย์สินทางปัญญาหรือสินทรัพย์ของแบรนด์ การเพิ่มลายน้ำ—ไม่ว่าจะเป็นข้อความหรือรูปภาพ—ช่วยให้คุณบังคับใช้ **PDF document security** และทำให้การแจกจ่ายโดยไม่ได้รับอนุญาตยากขึ้นมาก ในบทแนะนำนี้ คุณจะได้เรียนรู้ขั้นตอนโดยละเอียดว่าต้องใช้ **GroupDocs.Watermark for Java** อย่างไรเพื่อเพิ่มลายน้ำทั้งแบบข้อความและรูปภาพลงในเอกสาร PDF

## คำตอบอย่างรวดเร็ว
- **ไลบรารีใดที่เพิ่มลายน้ำให้กับ PDF ใน Java?** GroupDocs.Watermark for Java.  
- **ฉันสามารถเพิ่มลายน้ำข้อความและรูปภาพได้หรือไม่?** ใช่, API รองรับทั้งสองประเภท.  
- **ฉันต้องการใบอนุญาตหรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการประเมิน; ใบอนุญาตแบบชำระเงินจะลบข้อจำกัด.  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า.  
- **Maven รองรับหรือไม่?** แน่นอน – เพียงเพิ่มรีโพซิทอรีและการพึ่งพา.

## ลายน้ำ PDF คืออะไรและทำไมต้องใช้?
การใส่ลายน้ำใน PDF จะฝังเครื่องหมายที่มองเห็นได้หรือไม่มองเห็นได้ซึ่งระบุความเป็นเจ้าของ ความลับ หรือการสร้างแบรนด์ มันเป็นวิธีที่เบาแต่ทรงพลังในการป้องกันการคัดลอก ยืนยันความเป็นผู้เขียน และปฏิบัติตามนโยบายขององค์กร

## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่ม โปรดตรวจสอบว่าคุณมี:

1. **Java Development Kit (JDK) 8+** ติดตั้งบนเครื่องของคุณ.  
2. **GroupDocs.Watermark for Java** (เวอร์ชันล่าสุด).  
3. **Maven** (หรือความสามารถในการเพิ่ม JAR ด้วยตนเอง).

### การตั้งค่าสภาพแวดล้อม

#### การกำหนดค่า Maven
เพิ่มรีโพซิทอรีของ GroupDocs และการพึ่งพาลายน้ำลงในไฟล์ `pom.xml` ของคุณ:

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

#### ดาวน์โหลดโดยตรง
หากคุณไม่ต้องการใช้ Maven คุณสามารถดาวน์โหลดไฟล์ JAR โดยตรงจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับใบอนุญาต
เพื่อเริ่มต้นด้วยการทดลองใช้ฟรีหรือรับใบอนุญาตชั่วคราว ให้เยี่ยมชม [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license) สำหรับการใช้งานในสภาพแวดล้อมการผลิต ให้ซื้อการสมัครสมาชิกเพื่อเปิดใช้งานคุณสมบัติทั้งหมด

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
นำเข้าคลาสหลักที่ใช้ดำเนินการลายน้ำทั้งหมด:

```java
import com.groupdocs.watermark.Watermarker;
```

การนำเข้านี้ทำให้คุณเข้าถึงคลาส `Watermarker` ซึ่งเป็นจุดเริ่มต้นสำหรับการเพิ่มลายน้ำให้กับเอกสารประเภทใดก็ได้ที่รองรับ

## การดำเนินการแบบขั้นตอนต่อขั้นตอน
ด้านล่างเราจะแบ่งกระบวนการออกเป็นส่วนที่เป็นตรรกะ: การสร้างลายน้ำข้อความ, การสร้างลายน้ำรูปภาพ, และสุดท้ายการนำไปใช้กับรูปภาพภายใน PDF

### 1. เริ่มต้นลายน้ำข้อความ
**Why a text watermark?** มันเบา, สามารถค้นหาได้, และเหมาะสำหรับการเพิ่มประกาศลิขสิทธิ์หรือข้อความความลับ

#### 1.1 สร้างอินสแตนซ์ TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 ตั้งค่าการจัดตำแหน่ง
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 หมุนลายน้ำ
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 กำหนดขนาด
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. เริ่มต้นลายน้ำรูปภาพ
**When to use an image watermark?** เหมาะสำหรับการสร้างแบรนด์ด้วยโลโก้หรือการเพิ่มรูปแบบภาพที่ซับซ้อน

#### 2.1 โหลดไฟล์รูปภาพ
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 ตั้งค่าการจัดตำแหน่ง
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 หมุนลายน้ำรูปภาพ
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 กำหนดขนาด
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. เพิ่มลายน้ำให้กับรูปภาพภายใน PDF
ตอนนี้เราจะรวมทุกอย่างเข้าด้วยกัน: เปิดไฟล์ PDF, ค้นหารูปภาพทุกภาพ, และนำลายน้ำข้อความหรือรูปภาพไปใช้ตามขนาด

#### 3.1 เปิดเอกสาร PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 ดึงรูปภาพทั้งหมด
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 นำลายน้ำไปใช้ตามเงื่อนไข
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 ปล่อยทรัพยากรรูปภาพ
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 บันทึก PDF ที่แก้ไขแล้ว
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 ทำความสะอาด
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## การประยุกต์ใช้งานลายน้ำ PDF อย่างเป็นประโยชน์

| กรณีการใช้งาน | วิธีที่ลายน้ำช่วย |
|----------|------------------------|
| **Document Security** | ทำเครื่องหมายไฟล์ที่เป็นความลับเพื่อป้องกันการรั่วไหล |
| **Brand Protection** | ฝังโลโก้บน PDF การตลาดเพื่อเสริมสร้างอัตลักษณ์ของแบรนด์ |
| **Copyright Assertion** | เพิ่มชื่อผู้เขียนหรือสัญลักษณ์ © เพื่อยืนยันความเป็นเจ้าของ |
| **Version Control** | แสดงหมายเลขเวอร์ชันหรือวันที่โดยตรงบนหน้า |

## ข้อผิดพลาดทั่วไปและเคล็ดลับ
- **Path separators:** Use double backslashes (`\\`) on Windows or forward slashes (`/`) on Linux/macOS to avoid `FileNotFoundException`.  
- **Large PDFs:** Process images in batches or increase JVM heap size (`-Xmx2g`) to prevent OutOfMemory errors.  
- **License limits:** The trial version may limit the number of pages processed; upgrade for unlimited usage.  
- **Rotation confusion:** Remember that `setRotateAngle` expects degrees; negative values rotate counter‑clockwise.

## คำถามที่พบบ่อย

**Q: ฉันสามารถใส่ลายน้ำใน PDF ที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ใช่. เปิดเอกสารพร้อมรหัสผ่านโดยใช้คอนสตรัคเตอร์ `Watermarker` ที่รับสตริงรหัสผ่าน

**Q: ไลบรารีนี้รองรับรูปแบบอื่นเช่น DOCX หรือ PPTX หรือไม่?**  
A: แน่นอน. GroupDocs.Watermark ทำงานกับ Word, PowerPoint, Excel, และไฟล์รูปภาพเช่นกัน.

**Q: ฉันจะเปลี่ยนความทึบของลายน้ำได้อย่างไร?**  
A: ใช้ `setOpacity(float opacity)` บนวัตถุลายน้ำ (ค่าระหว่าง 0.0 ถึง 1.0).

**Q: สามารถใส่ลายน้ำเฉพาะหน้าแรกได้หรือไม่?**  
A: ดึงคอลเลกชันของหน้าโดยใช้ `watermarker.getPages()` แล้วนำลายน้ำไปใช้กับดัชนีหน้าที่ต้องการ.

**Q: ถ้าฉันต้องการใส่ลายน้ำใน PDF ที่เก็บอยู่ในคลาวด์บัคเก็ตจะทำอย่างไร?**  
A: โหลด PDF เข้า `InputStream` แล้วส่งให้คอนสตรัคเตอร์ `Watermarker`; หลังจากประมวลผล ให้เขียนสตรีมผลลัพธ์กลับไปยังคลาวด์.

## สรุป
ตอนนี้คุณมีวิธีที่ครบถ้วนและพร้อมใช้งานในสภาพแวดล้อมการผลิตสำหรับ **how to watermark PDF** ด้วย GroupDocs.Watermark for Java. ด้วยการผสานลายน้ำข้อความและรูปภาพ คุณสามารถบรรลุ **PDF document security** ที่แข็งแกร่งซึ่งตอบสนองต่อความต้องการด้านการสร้างแบรนด์และการปฏิบัติตามข้อกำหนดได้สำเร็จ สำรวจคุณลักษณะอื่นของไลบรารี เช่น การลบลายน้ำหรือการประมวลผลเป็นชุด เพื่อขยายการทำงานของเอกสารของคุณต่อไป

---

**อัปเดตล่าสุด:** 2026-01-23  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs