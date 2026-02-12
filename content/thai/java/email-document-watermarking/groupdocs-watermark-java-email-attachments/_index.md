---
date: '2025-12-29'
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับไฟล์แนบในอีเมลโดยใช้ GroupDocs.Watermark
  สำหรับ Java คู่มือนี้ให้คำแนะนำแบบทีละขั้นตอนและแนวปฏิบัติที่ดีที่สุด
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: เพิ่มลายน้ำให้ไฟล์แนบอีเมลด้วย GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# เพิ่มลายน้ำให้ไฟล์แนบอีเมลด้วย GroupDocs.Watermark สำหรับ Java

ในยุคดิจิทัลปัจจุบัน การปกป้องข้อมูลที่สำคัญเป็นสิ่งสำคัญ—โดยเฉพาะเมื่อคุณ **เพิ่มลายน้ำให้ไฟล์แนบอีเมล** ก่อนที่ไฟล์จะออกจากกล่องจดหมายของคุณ ไม่ว่าคุณจะเป็นนักพัฒนาที่ต้องการเสริมความปลอดภัยของเอกสารหรือธุรกิจที่ต้องการใส่แบรนด์ลงในทุกไฟล์ที่ส่งออก คู่มือนี้จะแสดงวิธีใช้ GroupDocs.Watermark สำหรับ Java เพื่อใส่ลายน้ำข้อความลงในไฟล์แนบที่รองรับทั้งหมดภายในข้อความอีเมล

## คำตอบโดยสรุป
- **“add watermark to email” ทำอะไรได้บ้าง?** มันฝังป้ายที่มองเห็นได้หรือกึ่งโปร่งใส (เช่น “Confidential”) ลงในไฟล์แนบที่รองรับทุกไฟล์ เพื่อป้องกันการแจกจ่ายโดยไม่ได้รับอนุญาต.  
- **ต้องใช้ไลบรารีอะไร?** GroupDocs.Watermark for Java (รุ่นล่าสุด).  
- **ต้องมีลิขสิทธิ์หรือไม่?** ลิขสิทธิ์ทดลองใช้ได้สำหรับการพัฒนา; ต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง.  
- **สามารถประมวลผลหลายอีเมลพร้อมกันได้หรือไม่?** ได้—ใส่ขั้นตอนทั้งหมดในลูปที่วนผ่านโฟลเดอร์ของไฟล์ *.msg*.  
- **ไฟล์ประเภทใดบ้างที่รองรับ?** PDF, Word, Excel, PowerPoint, รูปภาพและอื่น ๆ อีกหลายประเภท (ดูเอกสารอย่างเป็นทางการ).

## “add watermark to email” คืออะไร?
การเพิ่มลายน้ำให้ไฟล์แนบอีเมลหมายถึงการเปิดไฟล์อีเมลโดยโปรแกรม, ดึงไฟล์แนบแต่ละไฟล์ออกมา, แล้วใส่ข้อความ (หรือรูปภาพ) ที่กำหนดเองลงบนเอกสารเหล่านั้นก่อนที่อีเมลจะถูกส่งหรือบันทึกไว้ การทำเช่นนี้ทำให้ลายน้ำติดตามไฟล์ไปด้วย, เสริมความลับและเอกลักษณ์ของแบรนด์.

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
- **รองรับรูปแบบไฟล์หลากหลาย** – ทำงานกับ PDF, ไฟล์ Office, รูปภาพและอื่น ๆ.  
- **API ที่ง่าย** – เพียงไม่กี่บรรทัดของโค้ดคุณก็สามารถสร้าง, ใส่และบันทึกลายน้ำได้.  
- **เน้นประสิทธิภาพ** – ใช้หน่วยความจำน้อย, เหมาะสำหรับการประมวลผลบนเซิร์ฟเวอร์.  
- **ลิขสิทธิ์ระดับองค์กร** – มีรุ่นทดลองเพื่อการประเมิน, มีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง.

## ข้อกำหนดเบื้องต้น
- ติดตั้ง Java Development Kit (JDK).  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- เพิ่ม GroupDocs.Watermark สำหรับ Java ลงในโปรเจกต์ของคุณ (ดูขั้นตอนการตั้งค่าด้านล่าง).

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การตั้งค่า Maven
หากคุณใช้ Maven ให้เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

#### การรับลิขสิทธิ์
- สำหรับการทดลองใช้ฟรี, ลงทะเบียนบนเว็บไซต์ของ GroupDocs และขอรับลิขสิทธิ์ชั่วคราว.  
- สำหรับการใช้งานเชิงพาณิชย์, ซื้อลิขสิทธิ์เต็มรูปแบบ. เยี่ยมชม [purchase page](https://purchase.groupdocs.com/temporary-license/) เพื่อดูรายละเอียดเพิ่มเติม.

### การเริ่มต้นพื้นฐาน
นำเข้าคลาสหลักที่คุณจะต้องใช้:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## วิธีเพิ่มลายน้ำให้ไฟล์แนบอีเมล – คู่มือขั้นตอนโดยละเอียด

### ขั้นตอนที่ 1: สร้างลายน้ำข้อความ
แรกสุด, กำหนดข้อความลายน้ำและลักษณะการแสดงผลของมัน.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### ขั้นตอนที่ 2: ตั้งค่า Email Load Options
กำหนดค่าตัวโหลดเพื่อให้ GroupDocs สามารถอ่านไฟล์ *.msg* ได้.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### ขั้นตอนที่ 3: เริ่มต้น Watermarker สำหรับไฟล์อีเมลของคุณ
ชี้ `Watermarker` ไปยังไฟล์อีเมลที่คุณต้องการประมวลผล.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### ขั้นตอนที่ 4: ดึงเนื้อหาอีเมล
ดึงโครงสร้างภายในของอีเมลเพื่อให้คุณสามารถทำงานกับไฟล์แนบได้.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### ขั้นตอนที่ 5: วนลูปไฟล์แนบ
วนลูปผ่านไฟล์แนบแต่ละไฟล์และตรวจสอบว่ามันสามารถใส่ลายน้ำได้หรือไม่.

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

### ขั้นตอนที่ 6‑9: ใส่ลายน้ำลงในไฟล์แนบที่รองรับ
สำหรับไฟล์ที่มีคุณสมบัติเหมาะสม, เปิดไฟล์ด้วย `Watermarker` ใหม่, ใส่ลายน้ำ, แล้วบันทึกการเปลี่ยนแปลงกลับไปยังอีเมล.

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
บันทึกอีเมลที่แก้ไขแล้วเป็นไฟล์ใหม่เพื่อให้ไฟล์ต้นฉบับยังคงไม่ถูกแก้ไข.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### ขั้นตอนที่ 11: ทำความสะอาด
ปล่อยทรัพยากรโดยการปิด `Watermarker` หลัก.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## การประยุกต์ใช้งานจริง
1. **การแชร์เอกสารภายใน** – ใส่แบรนด์ของบริษัทหรือข้อความความลับลงในทุกไฟล์แนบก่อนการแจกจ่ายภายใน.  
2. **การสื่อสารกับลูกค้า** – ปกป้องสัญญา, ข้อเสนอ, และงบการเงินด้วยป้าย “Confidential” ที่ชัดเจน.  
3. **แคมเปญการตลาดผ่านอีเมล** – ใส่ลายน้ำแบรนด์ที่ละเอียดอ่อนลงใน PDF หรือรูปภาพที่แนบกับอีเมลโปรโมชั่น, เสริมการจดจำแบรนด์.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ** – ประมวลผลไฟล์แนบหนึ่งไฟล์ต่อครั้งและปิด `Watermarker` แต่ละอันโดยเร็ว.  
- **ขนาดไฟล์แนบ** – ไฟล์ขนาดใหญ่ทำให้เวลาประมวลผลเพิ่มขึ้น; พิจารณาบีบอัดหรือจำกัดขนาดก่อนใส่ลายน้ำ.  
- **การประมวลผลเป็นชุด** – วนลูปผ่านไดเรกทอรีของไฟล์ *.msg* เพื่อกระจายภาระเมื่อจัดการอีเมลจำนวนมาก.

## คำถามที่พบบ่อย

**Q: ฉันสามารถใส่ลายน้ำลงในไฟล์ที่เข้ารหัสได้หรือไม่?**  
A: ไม่. GroupDocs.Watermark ไม่รองรับการใส่ลายน้ำในเอกสารที่เข้ารหัสเพื่อเหตุผลด้านความปลอดภัย.

**Q: ไฟล์ประเภทใดบ้างที่รองรับการใส่ลายน้ำ?**  
A: PDF, Word, Excel, PowerPoint, รูปภาพ (PNG, JPEG, BMP) และรูปแบบทั่วไปอื่น ๆ อีกหลายประเภท. ดูเอกสารอย่างเป็นทางการสำหรับรายการเต็ม.

**Q: ฉันจะปรับแต่งลักษณะของลายน้ำได้อย่างไร?**  
A: คุณสามารถเปลี่ยนฟอนต์, ขนาด, สี, ความทึบ, การหมุน, และตำแหน่งโดยใช้คอนสตรัคเตอร์ `TextWatermark` และคุณสมบัติต่าง ๆ ของมัน.

**Q: การประมวลผลหลายอีเมลเป็นชุดเป็นไปได้หรือไม่?**  
A: ได้. ใส่ขั้นตอนทั้งหมดในลูป `for` ที่วนผ่านโฟลเดอร์ของไฟล์ *.msg* และใช้ตรรกะเดียวกันกับแต่ละไฟล์.

**Q: ลายน้ำของฉันไม่แสดง—ควรตรวจสอบอะไรบ้าง?**  
A: ตรวจสอบว่าไฟล์แนบเป็นประเภทที่รองรับ, ตรวจสอบว่าขนาดลายน้ำพอดีกับมิติของหน้า, และยืนยันว่าเอกสารไม่ได้ถูกป้องกันด้วยรหัสผ่าน.

## แหล่งข้อมูล
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

**อัปเดตล่าสุด:** 2025-12-29  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs  

---