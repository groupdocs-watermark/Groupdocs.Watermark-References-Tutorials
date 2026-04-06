---
date: '2026-03-27'
description: เรียนรู้วิธีเพิ่มลายน้ำในไฟล์ Excel ด้วย GroupDocs.Watermark สำหรับ Java
  คู่มือนี้จะอธิบายขั้นตอนการตั้งค่า โค้ด และแนวปฏิบัติที่ดีที่สุดสำหรับการใส่ลายน้ำในสเปรดชีต.
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: เพิ่มลายน้ำใน Excel ด้วย GroupDocs.Watermark Java
type: docs
url: /th/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# เพิ่มลายน้ำใน Excel ด้วย GroupDocs.Watermark Java

การใส่ลายน้ำในไฟล์ Excel ของคุณสามารถเปลี่ยนเกมได้—ไม่ว่าจะเป็นการปกป้องข้อมูลที่สำคัญ, การทำแบรนด์ให้กับรายงานของคุณ, หรือเพียงแค่เพิ่มสัมผัสระดับมืออาชีพ ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีเพิ่มลายน้ำใน Excel** ด้วย GroupDocs.Watermark สำหรับ Java พร้อมคำอธิบายที่ชัดเจน, ตัวอย่างการใช้งานจริง, และเคล็ดลับเพื่อหลีกเลี่ยงข้อผิดพลาดทั่วไป

## คำตอบสั้น ๆ
- **ต้องใช้ไลบรารีอะไร?** GroupDocs.Watermark สำหรับ Java (เวอร์ชันล่าสุด)  
- **รองรับรูปแบบไฟล์ Excel ใด?** ไฟล์ .xlsx และ .xls (ที่ไม่ได้เข้ารหัส)  
- **สามารถเพิ่มลายน้ำรูปภาพได้หรือไม่?** ได้ – SDK รองรับทั้งลายน้ำข้อความและรูปภาพ  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานจริงหรือไม่?** จำเป็นต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานที่ไม่ใช่แบบทดลอง  
- **ใช้เวลานำไปใช้เท่าไหร่?** ประมาณ 10‑15 นาทีสำหรับลายน้ำข้อความพื้นฐาน

## **add watermark to excel** คืออะไร?
การเพิ่มลายน้ำในเวิร์กบุ๊กของ Excel หมายถึงการประทับข้อความ (หรือภาพ) ที่มองเห็นได้ (หรือกึ่งโปร่งใส) ลงบนทุกแผ่นงานหรือเอกสารที่ฝังอยู่ ซึ่งช่วยให้คุณยืนยันความเป็นเจ้าของ, ระบุความลับ, หรือเสริมแบรนด์ทั่วทั้งไฟล์

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
GroupDocs.Watermark มี API ระดับสูงที่ทำให้การจัดการโครงสร้าง Office Open XML ง่ายขึ้น มันทำให้คุณสามารถ:

- ใส่ลายน้ำหลายแผ่นงานในคำสั่งเดียว  
- จัดการไฟล์แนบที่ฝังอยู่ (เช่น PDF ที่ฝัง) อัตโนมัติ  
- รักษาการจัดรูปแบบและสูตรเดิมไว้  
- ทำงานกับลายน้ำข้อความและรูปภาพ (เช่น **add image watermark java**)

## ข้อกำหนดเบื้องต้น

- **สภาพแวดล้อมการพัฒนา Java** – Java 8 หรือสูงกว่า (JDK)  
- **GroupDocs.Watermark สำหรับ Java SDK** – ดาวน์โหลดเวอร์ชันล่าสุดจาก [ที่นี่](https://releases.groupdocs.com/watermark/java/)  
- **IDE** – IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไขที่รองรับ Java ใดก็ได้  
- **สเปรดชีตตัวอย่าง** – ไฟล์ .xlsx ที่คุณต้องการปกป้อง

คุณสามารถเพิ่ม SDK ไปยังโปรเจกต์ของคุณได้ผ่าน Maven, Gradle หรือโดยการวางไฟล์ JAR ลงใน classpath ด้วยตนเอง

## นำเข้าแพ็กเกจ

การนำเข้าต่อไปนี้จะทำให้คุณเข้าถึงคลาสหลักสำหรับการใส่ลายน้ำ, การจัดการสเปรดชีต, และยูทิลิตี้ฟอนต์

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## วิธี **watermark spreadsheet** – คำแนะนำขั้นตอนโดยละเอียด

ต่อไปนี้เป็นขั้นตอนแบบลำดับเลขที่แสดงอย่างชัดเจน **วิธีใส่ลายน้ำในสเปรดชีต** ด้วย Java แต่ละขั้นตอนมีคำอธิบายสั้น ๆ ตามด้วยบล็อกโค้ดต้นฉบับ (ไม่เปลี่ยนแปลง)

### ขั้นตอนที่ 1: ตั้งค่าอ็อบเจกต์ลายน้ำของคุณ  
**ทำไม?** อ็อบเจกต์นี้กำหนดลักษณะการมองเห็นของตราประทับที่คุณจะใช้

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### ขั้นตอนที่ 2: โหลดสเปรดชีต  
**ทำไม?** การเปิดเวิร์กบุ๊กทำให้ SDK มีตัวจัดการเพื่อแก้ไข

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### ขั้นตอนที่ 3: เข้าถึงเนื้อหาและแผ่นงานของสเปรดชีต  
**ทำไม?** ไฟล์ Excel อาจมีหลายแผ่น; คุณต้องวนลูปผ่านแต่ละแผ่น

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### ขั้นตอนที่ 4: วนลูปผ่านไฟล์แนบในแต่ละแผ่นงาน  
**ทำไม?** บางแผ่นงานฝังเอกสารอื่น (เช่น PDF) การจัดการเหล่านี้ทำให้ลายน้ำสอดคล้องทั่วทั้งไฟล์

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### ขั้นตอนที่ 5: ใส่ลายน้ำในแต่ละเอกสารที่แนบมา  
**ทำไม?** คุณต้องการตราประทับ “Confidential” เดียวกันบนไฟล์ที่ฝังทุกไฟล์

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### ขั้นตอนที่ 6: บันทึกการเปลี่ยนแปลงทั้งหมด  
**ทำไม?** บันทึกการแก้ไขลงในเวิร์กบุ๊กใหม่

```java
watermarker.save("your-output-file.xlsx");
```

### ขั้นตอนที่ 7: ปิดทรัพยากร  
**ทำไม?** การปล่อยทรัพยากรช่วยป้องกันการรั่วของหน่วยความจำ โดยเฉพาะเมื่อประมวลผลเวิร์กบุ๊กขนาดใหญ่

```java
watermarker.close();
```

## รวมทุกอย่างเข้าด้วยกัน: ตัวอย่างเต็ม

คลาสต่อไปนี้รวมทุกขั้นตอนเป็นโปรแกรมที่สามารถรันได้ **ห้ามแก้ไขบล็อกโค้ด** – เนื้อหาเหมือนกับตัวอย่างต้นฉบับ

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## ปัญหาที่พบบ่อยและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| **เวิร์กบุ๊กที่เข้ารหัสจะถูกข้าม** | SDK ไม่สามารถอ่านไฟล์ที่เข้ารหัสโดยไม่มีรหัสผ่าน | ถอดรหัสไฟล์ก่อนหรือระบุรหัสผ่านผ่าน `SpreadsheetLoadOptions.setPassword("pwd")` |
| **ลายน้ำไม่ปรากฏบนบางแผ่น** | แผ่นอาจมีมุมมองหรือการป้องกันที่ซ่อนวัตถุการวาด | ปิดการป้องกันแผ่นก่อนเพิ่มลายน้ำ แล้วเปิดการป้องกันใหม่หากต้องการ |
| **ประสิทธิภาพช้าบนไฟล์ขนาดใหญ่** | การโหลดเวิร์กบุ๊กทั้งหมดเข้าสู่หน่วยความจำทำให้หนัก | ประมวลผลแผ่นงานเป็นชุดหรือเพิ่มขนาด heap ของ JVM (`-Xmx2g`) |
| **ลายน้ำรูปภาพบิดเบี้ยว** | การตั้งค่าการสเกลไม่ถูกต้อง | ใช้ `ImageWatermark` พร้อมพารามิเตอร์ความกว้าง/สูงที่ระบุเพื่อรักษาอัตราส่วน |

## คำถามที่พบบ่อย

**ถาม: สามารถเพิ่มลายน้ำรูปภาพแทนข้อความได้หรือไม่?**  
ตอบ: ได้ ใช้ `ImageWatermark` จาก SDK และส่งอ็อบเจกต์ `java.awt.Image` ซึ่งครอบคลุมสถานการณ์ **add image watermark java**  

**ถาม: จะควบคุมตำแหน่งของลายน้ำได้อย่างไร?**  
ตอบ: คลาส `TextWatermark` (หรือ `ImageWatermark`) มีคุณสมบัติอย่าง `setHorizontalAlignment`, `setVerticalAlignment`, และ `setOpacity` เพื่อปรับตำแหน่งและความโปร่งใสได้ละเอียด  

**ถาม: สามารถใส่ลายน้ำหลายไฟล์ Excel พร้อมกันได้หรือไม่?**  
ตอบ: แน่นอน ใส่ขั้นตอนทั้งหมดไว้ในลูป `for` ที่วนผ่านไดเรกทอรีของไฟล์ และใช้อ็อบเจกต์ `TextWatermark` เดียวกันซ้ำได้  

**ถาม: หากสเปรดชีตมีแผนภูมิจะเกิดอะไรขึ้น?**  
ตอบ: แผนภูมิจัดเป็นวัตถุการวาดแยกต่างหาก; ลายน้ำจะถูกใส่บนแคนวาสของแผ่นงาน ดังนั้นแผนภูมิจะไม่ถูกแก้ไขแต่ยังอยู่ภายใต้ตราประทับโปร่งใส  

**ถาม: สามารถลบลายน้ำที่เพิ่มไว้ก่อนหน้านี้ได้หรือไม่?**  
ตอบ: SDK มีเมธอด `watermarker.remove(watermark)` แต่คุณต้องเก็บอ้างอิงของอ็อบเจกต์ลายน้ำเดิมหรือค้นหาตามข้อความ/เนื้อหาเพื่อระบุลายน้ำที่ต้องการลบ  

---

**อัปเดตล่าสุด:** 2026-03-27  
**ทดสอบกับ:** GroupDocs.Watermark 23.12 (Java)  
**ผู้เขียน:** GroupDocs