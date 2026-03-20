---
date: '2026-03-20'
description: เรียนรู้วิธีเพิ่มลายน้ำในสเปรดชีต Excel ด้วย GroupDocs.Watermark สำหรับ
  Java รวมถึงเทคนิคการเพิ่มลายน้ำข้อความใน Excel และการเพิ่มลายน้ำใน Excel ด้วย Java.
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: วิธีเพิ่มลายน้ำใน Excel ด้วย GroupDocs.Watermark Java
type: docs
url: /th/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# วิธีเพิ่มลายน้ำลงในสเปรดชีต Excel ด้วย GroupDocs.Watermark สำหรับ Java

การเพิ่มความสามารถ **how to add watermark** ลงในไฟล์ Excel ของคุณเป็นวิธีที่ใช้งานได้จริงในการปกป้องข้อมูลที่สำคัญและยืนยันความเป็นเจ้าของ ในคู่มือขั้นตอนนี้คุณจะได้เรียนรู้วิธีเพิ่มลายน้ำลงในสเปรดชีต Excel ปรับแต่งลักษณะของลายน้ำ และวางไว้ในส่วนหัวหรือส่วนท้ายของแผ่นงาน—ทั้งหมดนี้ด้วย GroupDocs.Watermark สำหรับ Java

## คำตอบสั้น

- **ไลบรารีที่ต้องการคืออะไร?** GroupDocs.Watermark for Java (24.11 หรือใหม่กว่า)  
- **ฉันสามารถปรับแต่งฟอนต์และสีได้หรือไม่?** ได้ โดยใช้คลาส `Font` และ `Color`  
- **ลายน้ำปรากฏที่ไหน?** ในส่วนหัวหรือส่วนท้ายของแผ่นงานที่เลือก  
- **ต้องใช้ไลเซนส์สำหรับการใช้งานจริงหรือไม่?** จำเป็นต้องมีไลเซนส์ GroupDocs ที่ถูกต้องสำหรับการใช้งานที่ไม่ใช่รุ่นทดลอง  
- **วิธีนี้ทำงานกับเวิร์กบุ๊กขนาดใหญ่ได้หรือไม่?** ได้ แต่ควรปิดอ็อบเจ็กต์ `Watermarker` เพื่อปล่อยทรัพยากร

## คำแนะนำ

คุณกำลังมองหาวิธีเพิ่มความปลอดภัยให้กับสเปรดชีต Excel ของคุณโดยการใส่ลายน้ำข้อความหรือไม่? ไม่ว่าจะเป็นการปกป้องข้อมูลลับหรือการยืนยันความเป็นเจ้าของ การฝังลายน้ำในส่วนหัวหรือส่วนท้ายของสเปรดชีตสามารถเป็นประโยชน์อย่างยิ่ง ในบทแนะนำนี้เราจะพาคุณผ่านการใช้งานฟีเจอร์นี้ด้วย GroupDocs.Watermark สำหรับ Java

**สิ่งที่คุณจะได้เรียนรู้**
- วิธีเพิ่มลายน้ำข้อความลงในสเปรดชีต Excel  
- การกำหนดค่าลายน้ำด้วยฟอนต์และสีที่กำหนดเอง  
- การตั้งค่าการจัดตำแหน่งส่วนหัว/ส่วนท้ายในเอกสารของคุณ  

ด้วยทักษะเหล่านี้ คุณจะพร้อมที่จะปกป้องสเปรดชีตของคุณได้อย่างมีประสิทธิภาพ ตอนนี้มาดูข้อกำหนดเบื้องต้นที่จำเป็นต้องเตรียมกัน

## “how to add watermark” คืออะไรใน Excel?

ลายน้ำคือข้อความหรือรูปภาพที่มีความโปร่งแสงเบา ๆ ปรากฏอยู่ด้านหลัง (หรือด้านหน้า) ของเนื้อหาหลัก ใน Excel ลายน้ำมักจะถูกวางไว้ในพื้นที่ส่วนหัวหรือส่วนท้ายของแผ่นงาน เพื่อให้ปรากฏบนทุกหน้าที่พิมพ์โดยไม่รบกวนข้อมูลในเซลล์

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?

- **ข้ามแพลตฟอร์ม**: ทำงานบนระบบปฏิบัติการใด ๆ ที่รองรับ Java  
- **การควบคุมเต็มรูปแบบ**: ปรับแต่งฟอนต์, ขนาด, สีและการจัดตำแหน่งได้ตามต้องการ  
- **เน้นประสิทธิภาพ**: จัดการเวิร์กบุ๊กขนาดใหญ่ได้อย่างมีประสิทธิภาพ  

## ข้อกำหนดเบื้องต้น

- **GroupDocs.Watermark for Java** (เวอร์ชัน 24.11 หรือใหม่กว่า)  
- **Java Development Kit (JDK)** ที่ติดตั้งและกำหนดค่าแล้ว  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- Maven (หากคุณต้องการจัดการ dependencies)

### ไลบรารีที่ต้องใช้

- **GroupDocs.Watermark for Java** – ให้ API สำหรับการใส่ลายน้ำ  

### ความรู้พื้นฐานที่ต้องมี

- การเขียนโปรแกรม Java เบื้องต้น  
- ความคุ้นเคยกับ Maven หรือการจัดการ JAR ด้วยตนเอง  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

คุณสามารถติดตั้งไลบรารีผ่าน Maven หรือดาวน์โหลดไฟล์ JAR โดยตรง

**การติดตั้งด้วย Maven**

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

**ดาวน์โหลดโดยตรง**  
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

### การรับไลเซนส์
- **รุ่นทดลองฟรี** – ทดลองใช้ API ได้โดยไม่มีค่าใช้จ่าย  
- **ไลเซนส์ชั่วคราว** – ระยะเวลาประเมินผลที่ขยายออกไป  
- **การซื้อ** – ใช้งานเต็มรูปแบบ ไม่จำกัดจำนวน  

เพื่อเริ่มต้นใช้งาน GroupDocs.Watermark ให้เพิ่มคำสั่ง import ดังนี้:

```java
import com.groupdocs.watermark.Watermarker;
```

## วิธีเพิ่มลายน้ำลงในสเปรดชีต Excel

ด้านล่างเป็นโค้ดที่สมบูรณ์และสามารถรันได้ แบ่งเป็นขั้นตอนที่ชัดเจน แต่ละขั้นตอนจะมีคำอธิบายสั้น ๆ ก่อนบล็อกโค้ด เพื่อให้คุณไม่พลาดบริบทของแต่ละส่วน

### ขั้นตอนที่ 1: โหลดสเปรดชีต

แรกเริ่มให้โหลดเวิร์กบุ๊กพร้อมกับตัวเลือกการโหลดที่เหมาะสม

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**คำอธิบาย**: โค้ดนี้สร้างอินสแตนซ์ `Watermarker` ที่เชื่อมโยงกับไฟล์ Excel ของคุณ พร้อมสำหรับการทำงานกับลายน้ำ

### ขั้นตอนที่ 2: สร้างลายน้ำข้อความ

กำหนดลักษณะการแสดงผลของลายน้ำ

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**คำอธิบาย**: เราตั้งค่าข้อความลายน้ำ เลือกฟอนต์ **Segoe UI** แบบหนา และกำหนดสีพื้นหน้าและพื้นหลังที่ตัดกันอย่างชัดเจน

### ขั้นตอนที่ 3: กำหนดตำแหน่งการวางลายน้ำ

เลือกแผ่นงานและส่วนของหน้า (ส่วนหัวหรือส่วนท้าย) ที่จะใส่ลายน้ำ

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**คำอธิบาย**: อ็อบเจ็กต์ `SpreadsheetWatermarkHeaderFooterOptions` บอก API ให้ใส่ลายน้ำในส่วนหัว/ส่วนท้ายของแผ่นงานแรก

### ขั้นตอนที่ 4: เพิ่มลายน้ำและบันทึก

นำลายน้ำไปใช้และเขียนผลลัพธ์ลงไฟล์ใหม่

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**คำอธิบาย**: เมธอด `add` แทรกลายน้ำ, `save` เขียนเวิร์กบุ๊กที่แก้ไขแล้ว, และ `close` ปล่อยทรัพยากรที่ใช้

## เพิ่มลายน้ำข้อความใน Excel – เคล็ดลับขั้นสูง

- **หลายแผ่นงาน**: วนลูปผ่านดัชนีแผ่นงานและเรียก `options.setWorksheetIndex(i)` สำหรับแต่ละแผ่นงาน  
- **ข้อความแบบไดนามิก**: ดึงข้อความลายน้ำจากฐานข้อมูลหรือไฟล์กำหนดค่าเพื่อทำให้เอกสารแต่ละไฟล์เป็นแบบเฉพาะตัว  
- **การควบคุมความทึบ**: ใช้ `watermark.setOpacity(0.5)` เพื่อทำให้ลายน้ำดูอ่อนลง  

## ปัญหาและวิธีแก้ไขที่พบบ่อย

| ปัญหา | วิธีแก้ไข |
|-------|-----------|
| **File Not Found** | ตรวจสอบว่าเส้นทาง (`YOUR_DOCUMENT_DIRECTORY/...`) ถูกต้องและใช้เส้นทางแบบเต็มระหว่างการทดสอบ |
| **License Not Found** | วางไฟล์ `GroupDocs.Watermark.lic` ไว้ที่โฟลเดอร์รากของโปรเจกต์ หรือกำหนดไลเซนส์โดยโปรแกรมด้วย `License license = new License(); license.setLicense("path/to/license.lic");` |
| **Unsupported Format** | ตรวจสอบว่าเวิร์กบุ๊กบันทึกเป็น `.xlsx` หรือ `.xls` รูปแบบเก่าอาจต้องแปลงเป็นรูปแบบใหม่ก่อน |
| **Performance Lag on Large Files** | ประมวลผลหนึ่งแผ่นงานต่อครั้งและเรียก `watermarker.close()` ทันทีหลังจากบันทึกไฟล์แต่ละไฟล์ |

## การประยุกต์ใช้งานจริง

1. **การปกป้องข้อมูลลับ** – ป้องกันการคัดลอกโดยการทำเครื่องหมายทุกหน้าที่พิมพ์ด้วยลายน้ำที่มองเห็นได้ชัดเจน  
2. **การยืนยันความเป็นเจ้าของ** – ฝังชื่อบริษัทหรือโลโก้เป็นลายน้ำเพื่อแสดงแหล่งที่มาของเอกสาร  
3. **การติดตามเอกสาร** – ใส่ตัวระบุเฉพาะในลายน้ำเพื่อสืบค้นเส้นทางการกระจายเอกสาร  

## ข้อควรพิจารณาด้านประสิทธิภาพ

- ลดจำนวนลายน้ำต่อเซสชันให้เหลือน้อยที่สุด  
- ปิดอ็อบเจ็กต์ `Watermarker` ทันทีหลังการใช้งานเพื่อปล่อยไฟล์แฮนด์เดิล  
- สำหรับเวิร์กบุ๊กขนาดใหญ่มาก ให้เพิ่มขนาด heap ของ JVM (`-Xmx2g`)  

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถเปลี่ยนสไตล์ฟอนต์ของลายน้ำได้หรือไม่?**  
ตอบ: ได้ คุณสามารถปรับแต่งอ็อบเจ็กต์ `Font` ด้วยฟอนต์ที่ติดตั้งอยู่ใดก็ได้ รวมถึงขนาดและ `FontStyle` (Bold, Italic ฯลฯ)

**ถาม: สามารถใส่ลายน้ำหลายแผ่นงานได้หรือไม่?**  
ตอบ: แน่นอน ให้วนลูปผ่านดัชนีแผ่นงานและใช้ `SpreadsheetWatermarkHeaderFooterOptions` เดียวกันสำหรับแต่ละแผ่นงาน

**ถาม: GroupDocs.Watermark รองรับรูปแบบไฟล์ Excel ใดบ้าง?**  
ตอบ: รองรับไฟล์ XLS, XLSX และรูปแบบ Office Open XML อื่น ๆ อย่างเต็มที่

**ถาม: ควรจัดการกับเอกสารขนาดใหญ่อย่างไรให้มีประสิทธิภาพ?**  
ตอบ: ประมวลผลหนึ่งเวิร์กบุ๊กต่อครั้ง ปิด `Watermarker` หลังการบันทึก และตรวจสอบการใช้หน่วยความจำของ JVM อย่างสม่ำเสมอ

**ถาม: สามารถลบลายน้ำออกได้ในภายหลังหรือไม่?**  
ตอบ: การลบโดยตรงไม่ได้จัดให้ แต่คุณสามารถสร้างไฟล์ต้นฉบับใหม่โดยไม่ใส่ลายน้ำหรือเก็บสำเนาไฟล์ที่ไม่มีลายน้ำไว้สำหรับใช้ในอนาคต  

## แหล่งข้อมูล

- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)  

---

**อัปเดตล่าสุด:** 2026-03-20  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs