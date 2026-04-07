---
date: '2026-04-07'
description: เรียนรู้วิธีสร้างลายน้ำข้อความสำหรับไฟล์แนบอีเมลโดยใช้ GroupDocs.Watermark
  สำหรับ Java เพื่อรักษาความปลอดภัยของไฟล์แนบอีเมลและปกป้องข้อมูลที่เป็นความลับ
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: สร้างลายน้ำข้อความสำหรับไฟล์แนบอีเมลด้วย GroupDocs Java
type: docs
url: /th/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# วิธีเพิ่มลายน้ำให้ไฟล์แนบอีเมลโดยใช้ GroupDocs.Watermark สำหรับ Java

ในบทแนะนำนี้คุณจะ **สร้างวัตถุลายน้ำข้อความ** และนำไปใช้กับไฟล์แนบที่รองรับทั้งหมดในข้อความอีเมล การเพิ่มลายน้ำเป็นวิธีที่มีประสิทธิภาพในการ **ปกป้องไฟล์แนบของอีเมล**, แสดงความลับ, และเสริมสร้างอัตลักษณ์ของแบรนด์ — ทั้งหมดนี้ด้วยเพียงไม่กี่บรรทัดของโค้ด Java

## บทนำ

การปกป้องข้อมูลที่ละเอียดอ่อนเมื่อส่งผ่านอีเมลเป็นเรื่องสำคัญยิ่งขึ้น ไม่ว่าคุณจะต้องการระบุรายงานภายใน, ทำเครื่องหมายสัญญากฎหมาย, หรือเพียงแค่ใส่แบรนด์ให้กับสื่อการตลาด ลายน้ำข้อความจะให้ชั้นการปกป้องที่เบาและตรวจจับการดัดแปลงได้ คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมดของการใช้ **GroupDocs.Watermark สำหรับ Java** เพื่อเพิ่มลายน้ำที่กำหนดเองให้กับไฟล์แนบแต่ละไฟล์ในไฟล์ Outlook `.msg`

### สิ่งที่คุณจะได้เรียนรู้
- วิธี **สร้างวัตถุลายน้ำข้อความ** ด้วยฟอนต์และสีที่กำหนดเอง  
- การบูรณาการลายน้ำแบบขั้นตอนต่อขั้นตอนเข้าสู่กระบวนการประมวลผลอีเมลด้วย Java  
- เคล็ดลับการเพิ่มประสิทธิภาพเมื่อจัดการไฟล์แนบขนาดใหญ่  
- สถานการณ์จริงที่การใส่ลายน้ำในไฟล์แนบอีเมลเพิ่มคุณค่า  

ให้เราตรวจสอบว่าคุณมีทุกอย่างที่ต้องการก่อนที่เราจะเริ่มดำเนินการ

## คำตอบอย่างรวดเร็ว
- **“สร้างวัตถุลายน้ำข้อความ” หมายถึงอะไร?** หมายถึงการสร้างอ็อบเจ็กต์ `TextWatermark` ที่กำหนดข้อความที่มองเห็นได้, ฟอนต์, ขนาด, และสไตล์เพื่อวางทับบนเอกสาร  
- **ฉันสามารถใส่ลายน้ำในไฟล์แนบที่เข้ารหัสได้หรือไม่?** ไม่ – GroupDocs.Watermark ไม่รองรับไฟล์ที่เข้ารหัสเนื่องจากเหตุผลด้านความปลอดภัย  
- **ไฟล์ประเภทใดบ้างที่รองรับ?** PDF, Word, Excel, PowerPoint, รูปภาพ, และอื่น ๆ อีกมาก – ดูเอกสารอย่างเป็นทางการสำหรับรายการเต็ม  
- **ฉันต้องการไลเซนส์หรือไม่?** ไลเซนส์ทดลองใช้ได้สำหรับการพัฒนา; ไลเซนส์เชิงพาณิชย์จำเป็นสำหรับการใช้งานในสภาพแวดล้อมการผลิต  
- **กระบวนการเร็วแค่ไหน?** การใส่ลายน้ำในไฟล์แนบขนาดประมาณ 2 MB ใช้เวลาน้อยกว่าวินาทีบนฮาร์ดแวร์สมัยใหม่  

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK)** – เวอร์ชัน 8 หรือใหม่กว่า  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- **GroupDocs.Watermark for Java** เพิ่มในโปรเจคของคุณ (ดูขั้นตอนการตั้งค่าด้านล่าง)  
- เข้าถึงไฟล์อีเมล (`.msg`, `.eml`, ฯลฯ) ที่มีไฟล์แนบที่คุณต้องการปกป้อง  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การตั้งค่า Maven

หากคุณจัดการ dependencies ด้วย Maven, เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจากเว็บไซต์อย่างเป็นทางการ:  
[รุ่น GroupDocs.Watermark สำหรับ Java](https://releases.groupdocs.com/watermark/java/)

#### การรับไลเซนส์
- **ทดลอง:** ลงทะเบียนบนเว็บไซต์ GroupDocs และขอไลเซนส์ชั่วคราว  
- **เชิงพาณิชย์:** ซื้อไลเซนส์เต็มที่นี่: [หน้าการซื้อ](https://purchase.groupdocs.com/temporary-license/)

### การเริ่มต้นพื้นฐาน

นำเข้าคลาสหลักที่คุณจะต้องใช้ในไฟล์ซอร์ส Java ของคุณ:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## ลายน้ำข้อความคืออะไร?

**ลายน้ำข้อความ** คือข้อความกึ่งโปร่งใสที่แสดงบนแต่ละหน้าของเอกสาร ด้วย GroupDocs.Watermark คุณสามารถควบคุมฟอนต์, ขนาด, สี, การหมุน, และความทึบแสง, ให้ความยืดหยุ่นเต็มที่ในการสร้างแบรนด์หรือประกาศความลับที่ผสมผสานกับเนื้อหาต้นฉบับอย่างเป็นธรรมชาติ

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับไฟล์แนบอีเมล?

- **ปกป้องไฟล์แนบอีเมล** ด้วยการทำเครื่องหมายให้เห็นว่าเป็นความลับ  
- **รักษาความสอดคล้องของแบรนด์** ในเอกสารที่ส่งออกทั้งหมด  
- **ประมวลผลเป็นชุด** หลายอีเมลด้วยลูปเดียว, ประหยัดเวลาและลดข้อผิดพลาดจากการทำมือ  
- **รองรับหลายรูปแบบ** – โค้ดเดียวทำงานกับ PDF, ไฟล์ Word, รูปภาพ, และอื่น ๆ  

## คู่มือการดำเนินการ

เราจะเดินผ่านแต่ละขั้นตอน, อธิบายเหตุผล *ทำไม* ของโค้ดเพื่อให้คุณปรับใช้กับโครงการของคุณเอง

### ขั้นตอนที่ 1: สร้างลายน้ำข้อความ

แรกสุด, สร้างอ็อบเจ็กต์ `TextWatermark` พร้อมข้อความที่ต้องการแสดงและการตั้งค่าฟอนต์ที่ต้องการ

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **เคล็ดลับ:** ปรับขนาดฟอนต์หรือสีให้ตรงกับคู่มือสไตล์ขององค์กร คุณยังสามารถตั้งค่าความทึบแสงผ่าน `watermark.setOpacity(0.5)` หากต้องการเอฟเฟกต์ที่อ่อนโยนกว่า

### ขั้นตอนที่ 2: ตั้งค่า Email Load Options

`EmailLoadOptions` บอกไลบรารีว่าต้องตีความไฟล์อีเมลที่เข้ามาอย่างไร

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### ขั้นตอนที่ 3: เริ่มต้น Watermarker สำหรับไฟล์อีเมลของคุณ

ชี้ตัวสร้าง `Watermarker` ไปที่ไฟล์ `.msg` (หรือ `.eml`) ที่คุณต้องการประมวลผล

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### ขั้นตอนที่ 4: ดึงเนื้อหาอีเมล

สกัดโครงสร้างภายในของอีเมลเพื่อให้คุณสามารถวนลูปผ่านไฟล์แนบของมัน

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### ขั้นตอนที่ 5: วนลูปไฟล์แนบ

สำหรับแต่ละไฟล์แนบ, เราตรวจสอบว่าประเภทไฟล์รองรับและไม่ได้เข้ารหัส

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### ขั้นตอนที่ 6‑9: เพิ่มลายน้ำให้ไฟล์แนบที่รองรับ

ภายในบล็อกเงื่อนไข, เราสร้าง `Watermarker` เฉพาะสำหรับไฟล์แนบ, ใส่ลายน้ำ, แล้วส่งเนื้อหาที่แก้ไขกลับเข้าไปในอีเมล

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### ขั้นตอนที่ 10: บันทึกอีเมลที่มีลายน้ำ

เขียนอีเมลที่อัปเดตลงในไฟล์ใหม่เพื่อให้ไฟล์ต้นฉบับไม่ถูกแก้ไข

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### ขั้นตอนที่ 11: ทำความสะอาด

ควรปล่อยทรัพยากรเสมอเพื่อหลีกเลี่ยงการรั่วไหลของหน่วยความจำ

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|----------|
| **ลายน้ำไม่ปรากฏ** | ความทึบแสงตั้งค่าต่ำเกินไปหรือสีฟอนต์ตรงกับพื้นหลัง | เพิ่มความทึบแสง (`watermark.setOpacity(0.7)`) หรือเลือกสีที่ตัดกัน |
| **ประเภทไฟล์แนบที่ไม่รองรับ** | รูปแบบไฟล์ไม่ได้อยู่ในรายการที่ GroupDocs รองรับ | แปลงไฟล์เป็นรูปแบบที่รองรับก่อน (เช่น PDF) หรือข้ามไฟล์โดยบันทึกข้อความลงบันทึก |
| **OutOfMemoryError บน PDF ขนาดใหญ่** | การโหลดไฟล์แนบขนาดใหญ่มากใช้หน่วยความจำ heap มากเกินไป | เพิ่มขนาด heap ของ JVM (`-Xmx2g`) หรือประมวลผลไฟล์แนบเป็นชุดเล็กลง |

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถเพิ่มลายน้ำในไฟล์ที่เข้ารหัสได้หรือไม่?**  
ตอบ: ไม่, GroupDocs.Watermark ไม่รองรับการเพิ่มลายน้ำในไฟล์ที่เข้ารหัสเนื่องจากข้อจำกัดด้านความปลอดภัย  

**ถาม: ไฟล์ประเภทใดบ้างที่รองรับการใส่ลายน้ำ?**  
ตอบ: ประเภทที่รองรับรวมถึง PDF, เอกสาร Word, แผ่นงาน Excel, งานนำเสนอ PowerPoint, และรูปแบบภาพทั่วไป ดูเอกสารอย่างเป็นทางการสำหรับรายการเต็ม  

**ถาม: ฉันจะปรับแต่งลักษณะของลายน้ำได้อย่างไร?**  
ตอบ: ใช้คลาส `Font` เพื่อตั้งค่าขนาด, สไตล์, และสี, และเรียกเมธอดเช่น `setOpacity` และ `setRotationAngle` บนอินสแตนซ์ `TextWatermark`  

**ถาม: สามารถประมวลผลหลายอีเมลเป็นชุดได้หรือไม่?**  
ตอบ: ได้. ห่อกระบวนการทั้งหมดในลูปที่วนไฟล์ในไดเรกทอรี, ใช้อ็อบเจ็กต์ `TextWatermark` เดียวกันเพื่อประสิทธิภาพ  

**ถาม: ลายน้ำของฉันถูกตัดบนหน้าสุดท้าย—มีอะไรผิดพลาด?**  
ตอบ: ตรวจสอบให้แน่ใจว่าลายน้ำพอดีกับขอบกระดาษ. คุณสามารถปรับตำแหน่งด้วย `watermark.setHorizontalAlignment` และ `watermark.setVerticalAlignment`  

## การประยุกต์ใช้ในทางปฏิบัติ

1. **การแชร์เอกสารภายใน:** ฝังแบรนด์ของบริษัทหรือประกาศความลับก่อนแจกจ่ายรายงานทั่วองค์กร  
2. **การสื่อสารกับลูกค้า:** ใส่แท็ก “Confidential” บนสัญญาและข้อเสนอเพื่อเตือนผู้รับเกี่ยวกับนโยบายการจัดการข้อมูล  
3. **การตลาดผ่านอีเมล:** เพิ่มลายน้ำแบรนด์ที่ละเอียดอ่อนใน PDF โปรโมชั่นที่แนบกับจดหมายข่าว, เสริมการจดจำแบรนด์โดยไม่รบกวนการออกแบบ  

## พิจารณาด้านประสิทธิภาพ

- **การจัดการหน่วยความจำ:** ปิด `attachedWatermarker` แต่ละอันโดยเร็ว (ตามที่แสดงในขั้นตอน 9) เพื่อปล่อยทรัพยากรเนทีฟ  
- **ขีดจำกัดขนาดไฟล์:** สำหรับไฟล์แนบที่ใหญ่กว่า 10 MB, พิจารณา stream ไฟล์หรือเพิ่มขนาด heap ของ JVM  
- **การประมวลผลแบบขนาน:** ใช้ `ExecutorService` ของ Java เพื่อใส่ลายน้ำหลายอีเมลพร้อมกัน, แต่ควรตรวจสอบการใช้ CPU เพื่อหลีกเลี่ยงการแย่งกัน  

## สรุป

ตอนนี้คุณมีสูตรที่ครบถ้วนและพร้อมใช้งานในสภาพแวดล้อมการผลิตสำหรับวิธี **สร้างวัตถุลายน้ำข้อความ** และนำไปใช้กับไฟล์แนบที่รองรับทั้งหมดในไฟล์อีเมลโดยใช้ GroupDocs.Watermark สำหรับ Java การบูรณาการกระบวนการนี้เข้าสู่ pipeline การจัดการอีเมลของคุณจะเพิ่มความปลอดภัยของเอกสาร, บังคับใช้แบรนด์, และรักษาการปฏิบัติตามกฎระเบียบด้วยภาระงานที่น้อยที่สุด  

พร้อมก้าวต่อไปหรือยัง? ลองขยายโค้ดเพื่อประมวลผลโฟลเดอร์ทั้งหมดของไฟล์ `.msg`, หรือสำรวจประเภทลายน้ำเพิ่มเติมเช่นรูปภาพและ QR code  

---  

**อัปเดตล่าสุด:** 2026-04-07  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs  

**แหล่งข้อมูล**  
- [เอกสาร](https://docs.groupdocs.com/watermark/java/)  
- [อ้างอิง API](https://reference.groupdocs.com/watermark/java)  
- [ดาวน์โหลด GroupDocs.Watermark สำหรับ Java](https://releases.groupdocs.com/watermark/java/)