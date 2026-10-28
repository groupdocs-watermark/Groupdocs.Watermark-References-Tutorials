---
date: '2026-03-22'
description: เรียนรู้วิธีใส่ลายน้ำไฟล์ Excel โดยเพิ่มลายน้ำข้อความด้วย GroupDocs.Watermark
  สำหรับ Java ปกป้องสเปรดชีตของคุณและเสริมสร้างแบรนด์
keywords:
- text watermark Excel
- GroupDocs.Watermark Java
- Excel document security
title: วิธีใส่ลายน้ำข้อความบนแผ่นงาน Excel ด้วย GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/
weight: 1
---

# วิธีใส่ลายน้ำข้อความบนแผ่นงาน Excel ด้วย GroupDocs.Watermark สำหรับ Java

เมื่อคุณต้องการ **วิธีใส่ลายน้ำ Excel** workbook—โดยเฉพาะอย่างยิ่งที่มีข้อมูลที่สำคัญ—การเพิ่มลายน้ำข้อความที่ชัดเจนและเป็นมืออาชีพเป็นวิธีที่มีประสิทธิภาพที่สุดในการปกป้องเนื้อหาและเสริมสร้างอัตลักษณ์ของแบรนด์ ในบทแนะนำนี้เราจะอธิบายขั้นตอนที่แน่นอนเพื่อ **เพิ่มลายน้ำข้อความในไฟล์ Excel** ด้วยไลบรารี GroupDocs.Watermark สำหรับ Java ตั้งแต่การตั้งค่าโปรเจกต์จนถึงการบันทึก workbook ที่ปลอดภัยแล้ว

## คำตอบสั้น
- **ควรใช้ไลบรารีอะไร?** GroupDocs.Watermark สำหรับ Java  
- **สามารถเพิ่มลายน้ำข้อความในทุกแผ่นงานได้หรือไม่?** ได้ – ทำการวนลูปแต่ละ worksheet แล้วใช้ลายน้ำเดียวกัน  
- **ต้องมีลิขสิทธิ์หรือไม่?** ทดลองใช้ฟรีสำหรับการประเมิน; ต้องมีลิขสิทธิ์ถาวรสำหรับการใช้งานจริง  
- **รองรับเวอร์ชัน Java ใด?** JDK 8 หรือใหม่กว่า  
- **ลายน้ำจะส่งผลต่อข้อมูลในเซลล์หรือไม่?** ไม่, ลายน้ำจะวางทับเป็นภาพภายใน worksheet เท่านั้น  

## ลายน้ำ Excel คืออะไร?
การลายน้ำ Excel หมายถึงการฝังเครื่องหมายที่มองเห็นได้—ข้อความหรือรูปภาพ—โดยตรงบนองค์ประกอบภาพของ worksheet (เช่นรูปภาพ) เพื่อให้ผู้เปิดไฟล์เห็นข้อความแสดงความเป็นเจ้าของหรือการแจ้งความลับ เทคนิคนี้ช่วยป้องกันการแจกจ่ายโดยไม่ได้รับอนุญาตและเพิ่มความเป็นมืออาชีพให้กับรายงานของคุณ

## ทำไมต้องใส่ลายน้ำข้อความ Excel ด้วย Java?
- **ความปลอดภัย** – ชี้แจงอย่างชัดเจนว่าข้อมูลเป็นความลับหรือเป็นทรัพย์สินของบริษัท  
- **ความสอดคล้องของแบรนด์** – เสริมสร้างการแสดงแบรนด์ขององค์กรในทุกสเปรดชีตที่แชร์  
- **การทำงานอัตโนมัติ** – Java ช่วยให้คุณฝังลายน้ำโดยโปรแกรมได้ ประหยัดเวลาจากการแก้ไขด้วยมือ  
- **รองรับหลายรูปแบบ** – ทำงานได้กับไฟล์ `.xlsx` และไฟล์ `.xls` รุ่นเก่า  

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK)** 8 หรือใหม่กว่า  
- **Maven** สำหรับการจัดการ dependencies  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และแนวคิดเชิงวัตถุ  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
เริ่มต้นโดยเพิ่ม dependency ของ GroupDocs.Watermark ลงในโปรเจกต์ Maven ของคุณ

### ใช้ Maven
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
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

**การจัดหาใบอนุญาต**
- **ทดลองใช้ฟรี** – สำรวจคุณสมบัติทั้งหมดโดยไม่มีค่าใช้จ่าย  
- **ใบอนุญาตชั่วคราว** – ใช้สำหรับการทดสอบระยะสั้น  
- **ซื้อ** – ปลดล็อกความสามารถเต็มรูปแบบสำหรับการผลิต  

### การเริ่มต้นพื้นฐาน
```java
import com.groupdocs.watermark.Watermarker;
// Initialize watermarker instance for your document
Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
```

## คู่มือการทำงาน

### ฟีเจอร์ 1: การสร้างลายน้ำข้อความและการกำหนดคุณสมบัติ
การสร้างและปรับแต่งลายน้ำรวมถึงการตั้งค่าข้อความ, ฟอนต์, การจัดแนว, มุมการหมุน, และการสเกล  

#### ภาพรวมขั้นตอน
**กำหนดลายน้ำของคุณ**
```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a new TextWatermark object
text watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// Configure the watermark properties
text watermark.setHorizontalAlignment(HorizontalAlignment.Center);
text watermark.setVerticalAlignment(VerticalAlignment.Center);
text watermark.setRotateAngle(45); // Set rotation angle
text watermark.setSizingType(SizingType.ScaleToParentDimensions);
text watermark.setScaleFactor(1); // Maintain original size scale factor
```
- **ข้อความและฟอนต์** – เลือกข้อความที่ชัดเจนและฟอนต์ที่อ่านง่าย  
- **การจัดแนว** – การจัดกึ่งกลางทำงานได้ดีสำหรับภาพส่วนใหญ่  
- **การหมุนและสเกล** – การเอียง 45° ทำให้ลายน้ำโดดเด่นโดยไม่บังภาพ  

### ฟีเจอร์ 2: โหลดเอกสารสเปรดชีตเพื่อใส่ลายน้ำ
โหลด workbook พร้อมตัวเลือกที่เหมาะสมเพื่อให้ GroupDocs สามารถเข้าถึงภาพภายในได้  

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
// Load your Excel spreadsheet
documentLoadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", documentLoadOptions);
```

### ฟีเจอร์ 3: ใส่ลายน้ำข้อความลงในภาพของ Worksheet
วนลูปผ่านภาพใน worksheet แรกและใช้ลายน้ำที่กำหนดค่าไว้  

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.WatermarkableImageCollection;

// Access content from your loaded document
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
WatermarkableImageCollection images = content.getWorksheets().get_Item(0).findImages();

for (com.groupdocs.watermark.contents.WatermarkableImage image : images) {
    // Add the configured watermark to each image in the worksheet
    image.add(watermark);
}
```

### ฟีเจอร์ 4: บันทึกและปิดเอกสารสเปรดชีตที่มีลายน้ำ
บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่และทำความสะอาดทรัพยากร  

```java
// Save the changes to a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx");
// Close the watermarker instance to free resources
watermarker.close();
```

## การใช้งานในเชิงปฏิบัติ
- **ความปลอดภัยของเอกสาร** – ปกป้องโมเดลการเงินหรือข้อมูล HR ที่เป็นความลับ  
- **การสร้างแบรนด์** – แทรกสโลแกนหรือข้อความกฎหมายของบริษัทในรายงานที่แชร์ทั้งหมด  
- **การปกป้องลิขสิทธิ์** – ป้องกันการคัดลอกโดยทำเครื่องหมายทุกภาพที่ส่งออก  

## พิจารณาด้านประสิทธิภาพ
- คอยอัปเดต GroupDocs.Watermark ให้เป็นเวอร์ชันล่าสุดเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพ  
- ปิดอินสแตนซ์ `Watermarker` ทันที (`close()`) เพื่อคืนหน่วยความจำ  
- สำหรับ workbook ขนาดใหญ่มาก ให้ประมวลผล worksheet เป็นชุดเพื่อหลีกเลี่ยงการใช้หน่วยความจำสูง  

## ปัญหาที่พบบ่อยและวิธีแก้
| ปัญหา | วิธีแก้ |
|-------|----------|
| ลายน้ำไม่ปรากฏ | ตรวจสอบว่าแผ่นงานมีรูปภาพจริงหรือไม่; API จะใส่ลายน้ำเฉพาะรูปภาพ ไม่ใช่เซลล์ |
| ลายน้ำตำแหน่งไม่ตรง | ปรับ `HorizontalAlignment` / `VerticalAlignment` หรือเปลี่ยน `RotateAngle` |
| ข้อผิดพลาดหน่วยความจำไม่พอในไฟล์ขนาดใหญ่ | เพิ่มขนาด heap ของ JVM (`-Xmx`) หรือประมวลผลแต่ละแผ่นงานแยกกัน |
| ข้อผิดพลาดใบอนุญาต | ตรวจสอบว่าไฟล์ใบอนุญาตทดลองหรือถาวรถูกอ้างอิงอย่างถูกต้องในโปรเจกต์ของคุณ |

## คำถามที่พบบ่อย

**ถาม: สามารถใช้กับ Excel เวอร์ชันทั้งหมดได้หรือไม่?**  
ตอบ: ใช่, GroupDocs รองรับทั้งรูปแบบ `.xlsx` และ `.xls`

**ถาม: ถ้าลายน้ำไม่แสดงอย่างถูกต้องจะทำอย่างไร?**  
ตอบ: ตรวจสอบการตั้งค่าการจัดแนวและให้แน่ใจว่าขนาดภาพเหมาะสมกับสเกลที่เลือก

**ถาม: จะปรับแต่งสไตล์ฟอนต์เพิ่มเติมได้อย่างไร?**  
ตอบ: ใช้คลาส `Font` เพื่อตั้งค่าเป็นตัวหนา, ตัวเอียง, สี หรือคุณสมบัติการพิมพ์อื่น ๆ

**ถาม: สามารถใส่ลายน้ำในทุกแผ่นงานของ workbook ได้หรือไม่?**  
ตอบ: แน่นอน—วนลูป `content.getWorksheets()` แล้วใช้ตรรกะ `image.add(watermark)` กับแต่ละแผ่นงาน

**ถาม: จะจัดการไฟล์ Excel ขนาดใหญ่อย่างมีประสิทธิภาพได้อย่างไร?**  
ตอบ: ประมวลผล worksheet ทีละส่วน, ปิด `Watermarker` หลังบันทึกแต่ละครั้ง, และพิจารณาเพิ่มขนาด heap ของ JVM  

## แหล่งข้อมูล
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)  

โดยการบูรณาการขั้นตอนเหล่านี้ในโปรเจกต์ Java ของคุณ คุณสามารถ **java add watermark excel** ไฟล์ได้อย่างรวดเร็ว พร้อมทั้งรับประกันความปลอดภัยและความสอดคล้องของแบรนด์  

---

**อัปเดตล่าสุด:** 2026-03-22  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs  

---