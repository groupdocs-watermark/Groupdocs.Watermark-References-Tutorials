---
date: '2026-01-31'
description: เรียนรู้วิธีเพิ่มลายน้ำในไฟล์ PDF ด้วย GroupDocs.Watermark สำหรับ Java
  ปกป้องเอกสาร ทำแบรนด์ให้กับ PDF และจัดการลายน้ำอย่างมีประสิทธิภาพ
keywords:
- GroupDocs Watermark for Java PDF
- PDF watermarking guide
- Java watermark application
title: วิธีเพิ่มลายน้ำใน PDF ด้วย GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/pdf-document-watermarking/groupdocs-watermark-java-pdf-watermark-guide/
weight: 1
---

# วิธีเพิ่มลายน้ำลงใน PDF ด้วย GroupDocs.Watermark สำหรับ Java

การเพิ่มลายน้ำลงในไฟล์ PDF ของคุณเป็นสิ่งสำคัญเพื่อปกป้องทรัพย์สินทางปัญญา, แสดงแบรนด์, หรือทำเครื่องหมายเอกสารว่าเป็นความลับ **ในคู่มือนี้ คุณจะได้เรียนรู้Docs.Watermark สำหรับ Java โดยกระบวนการจะง่ายและผลลัพธ์มีคุณภาพสูง

## คำตอบอย่างรวดเร็ว
- **วัตถุประสงค์หลักของการเพิ่มลายน้ำลงใน PDF คืออะไร?** เพื่อปกป้องความเป็นเจ้าของ, แสดงบรารีที่บทเรียนนี้ใช้คืออะไร?** GroupDocs.Watermark สำหรับ Java.  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีเพียงพอสำหรับการประเมิน; จำเป็นต้องมีไลเซนส์แบบชำระเงินสำหรับการใช้งานจริง.  
- **ฉันสามารถปรับแต่งฟอนต์, ขนาด, และตำแหน่งได้หรือไม่?** ได้ – API ให้คุณตั้งค่าฟอนต์, การจัดตำแหน่ง, ขนาด, และการพิจารณาขอบ.  
- **โซลูชันนี้เข้ากันได้กับโปรเจกต์ Maven หรือไม่?** แน่นอน; ไลบรารีนี้จัดจำหน่ายผ่าน Maven repositories.

## ลายน้ำ PDF คืออะไร?
ลายน้ำ PDF คือการซ้อนภาพแบบ視覺—โดยทั่วไปเป็นข้อความหรือรูปภาพ—ที่ปรากฏบนแต่ละหน้าของเอกสาร PDF สามารถเป็นแบบกึ่งโปร่งใส, หมุน, หรือวางตำแหน่งตามที่คุณต้องการ ช่วยให้คุณยืนยันความเป็นเจ้าของหรือสื่อสารข้อมูลสำคัญโดยไม่เปลี่ยนแปลงเนื้อหาพื้นฐาน

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
- **การผสานรวมง่าย** กับ Maven หรือ Gradle.  
- **การควบคุมเต็มรูปแบบ** บนการจัดรูปแบบข้อความ, การจัดตำแหน่ง, การสเกล, และการจัดการขอบ.  
- **ประสิทธิภาพสูง** สำหรับเอกสารขนาดใหญ่ด้วยการจัดการทรัพยากรที่มีประสิทธิภาพ.  
- **รองรับหลายแพลตฟอร์ม** ทำให้โค้ดเดียวทำงานบน Windows, Linux, และ macOS.

## ข้อกำหนดเบื้องต้น
- ติดตั้ง Java Development Kit (JDK).  
- Maven (หรือผู้จัดการ dependency อื่น) สำหรับจัดการไลบรารี.  
- IDE เช่น IntelliJ IDEA, Eclipse, หรือ NetBeans.  
- ความรู้พื้นฐานเกี่ยวกับ Java และแนวคิด PDF.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
เพื่อเริ่มใช้ **GroupDocs.Watermark**, ให้เพิ่มไลบรารีลงในโปรเจกต์ของคุณ:

**การกำหนดค่า Maven**  
เพิ่มการกำหนดค่าดังต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับไลเซนส์
เริ่มต้นด้วยการทดลองใช้ฟรีหรือขอไลเซนส์ชั่วคราวเพื่อสำรวจฟีเจอร์ทั้งหมด. ซื้อไลเซนส์สำหรับการใช้งานในระยะยาว.

### การเริ่มต้นและตั้งค่าเบื้องต้น
เมื่อเพิ่มไลบรารีแล้ว, ให้เริ่มต้นโปรเจกต์ของคุณดังนี้:

```java
import com.groupdocs.watermark.Watermarker;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize watermarker with input PDF path.
        Watermarker watermarker = new Watermarker("input.pdf");
        
        System.out.println("Watermarker initialized successfully!");
        
        // Close the resource once done
        watermarker.close();
    }
}
```

## คู่มือการใช้งาน

### ฟีเจอร์: การสร้างและกำหนดค่าลายน้ำ
#### ภาพรวม
สร้างลายน้ำข้อความ, ตั้งค่าการจัดตำแหน่ง, และกำหนดขนาดให้พอดีกับหน้า PDF ของคุณ.

##### สร้างลายน้ำข้อความด้วยการตั้งค่าฟอนต์เฉพาะ
เริ่มต้นด้วยการสร้างอ็อบเจ็กต์ `TextWatermark`. ตัวอย่างนี้ใช้ **Arial** ขนาด **42**:

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a text watermark with specific font settings.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
```

##### ตั้งค่าการจัดตำแหน่งแนวนอนและแนวตั้ง
จัดตำแหน่งลายน้ำตามตำแหน่งที่คุณต้องการ:

```java
// Set the horizontal alignment of the watermark to the right.
watermark.setHorizontalAlignment(HorizontalAlignment.Right);

// Set the vertical alignment of the watermark to the top.
watermark.setVerticalAlignment(VerticalAlignment.Top);
```

##### กำหนดประเภทการปรับขนาด
ปรับขนาดเพื่อให้พอดีกับมิติของเอกสาร:

```java
// Configure the sizing type to scale to parent dimensions.
watermark.setSizingType(SizingType.ScaleToParentDimensions);

// Set the scaling factor for the watermark.
watermark.setScaleFactor(1);
```

### ฟีเจอร์: การใช้ลายน้ำพร้อมประเภทขอบหน้า
#### ภาพรวม
ใช้ลายน้ำโดยคำนึงถึงขอบหน้ากระดาษ เพื่อให้ตำแหน่งวางถูกต้องภายในเอกสาร.

##### เริ่มต้น Load Options และโหลดเอกสาร PDF
ตั้งค่า load options และเริ่มต้น watermarker ของคุณ:

```java
import com.groupdocs.watermark.options.PdfLoadOptions;
import com.groupdocs.watermark.contents.PdfContent;

// Initialize load options for the PDF document.
PdfLoadOptions loadOptions = new PdfLoadOptions();

Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/in_document_pdf.pdf", loadOptions);
```

##### ตั้งค่าประเภทขอบหน้าและพิจารณาขอบของพาเรนต์
ปรับวิธีที่ขอบกระดาษมีผลต่อการวางลายน้ำ:

```java
import com.groupdocs.watermark.contents.PdfPageMarginType;

// Get the content of the loaded PDF and set the page margin type to BleedBox.
PdfContent pdfContent = watermarker.getContent(PdfContent.class);
pdfContent.setPageMarginType(PdfPageMarginType.BleedBox);

watermark.setConsiderParentMargins(true);
```

##### เพิ่มลายน้ำและบันทึกเอกสาร
ใช้ลายน้ำและบันทึกเอกสารของคุณ:

```java
// Add the configured watermark to the PDF document.
watermarker.add(watermark);

// Save the watermarked PDF to the specified output directory. Replace 'YOUR_OUTPUT_DIRECTORY' with your path.
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_document_pdf.pdf");

// Close the Watermarker resource to release any associated system resources.
watermarker.close();
```

## เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบให้แน่ใจว่าเส้นทางไฟล์ทั้งหมดถูกต้องและเข้าถึงได้จากแอปพลิเคชันของคุณ.  
- ตรวจสอบว่าฟอนต์ที่ต้องการ (เช่น Arial) ติดตั้งอยู่ในระบบ; หากไม่มีก็เลือกฟอนต์ที่มีอยู่.  
- หากพบปัญหาหน่วยความจำกับ PDF ขนาดใหญ่, ให้ประมวลผลเอกสารเป็นชุดย่อยหรือเพิ่มขนาด heap ของ JVM.

## การใช้งานเชิงปฏิบัติ
1. **การปกป้องเอกสาร** – ทำเครื่องหมายไฟล์ที่เป็นความลับด้วยลายน้ำ “CONFIDENTIAL”.  
2. **การสร้างแบรนด์** – เพิ่มชื่อบริษัทหรือโลโก้ใน PDF ที่ส่งออกทั้งหมด.  
3. **การควบคุมเวอร์ชัน** – แยกฉบับร่างจากเวอร์ชันสุดท้ายด้วยลายน้ำ “DRAFT”.  
4. **เอกสารทางกฎหมาย** – เสริมความเป็นของแท้ของสัญญาและข้อตกลง.  
5. **สื่อการศึกษา** – ป้องกันการแจกจ่าย PDF ของคอร์สโดยไม่ได้รับอนุญาต.

## การพิจารณาประสิทธิภาพ
- ปิดอินสแตนซ์ `Watermarker` ทันทีเพื่อคืนทรัพยากร.  
- สำหรับ PDF ขนาดใหญ่มาก, ให้โหลดและประมวลผลหน้าแบบเพิ่มทีละส่วนแทนการโหลดไฟล์ทั้งหมดพร้อมกัน.  
- ใช้โครงสร้างข้อมูลที่มีประสิทธิภาพเมื่อจัดการหลายลายน้ำ.

## สรุป
การทำ **วิธีเพิ่มลายน้ำลงใน PDF** ด้วย GroupDocs.Watermark สำหรับ Java นั้นง่ายและช่วยปรับปรุงกระบวนการจัดการเอกสารของคุณ. ด้วยการทำตามคู่มือนี้, คุณได้เรียนรู้การสร้าง, กำหนดค่า, และใช้ลายน้ำข้อความโดยคำนึงถึงขอบหน้าและการตั้งค่าการออกแบบ.

**ขั้นตอนต่อไป**
- ทดลองใช้ลายน้ำรูปภาพสำหรับโลโก้หรือตราประทับ.  
- ทำให้การใส่ลายน้ำเป็นอัตโนมัติเป็นส่วนหนึ่งของกระบวนการประมวลผลเอกสารที่ใหญ่ขึ้น.  

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้ไลบรารีนี้ใส่ลายน้ำบนรูปภาพได้หรือไม่?**  
A: ได้, GroupDocs.Watermark รองรับรูปแบบไฟล์หลายประเภท รวมถึงรูปภาพทั่วไปเช่น PNG และ JPEG.

**Q: สามารถใส่ลายน้ำหลายรายการพร้อมกันได้หรือไม่?**  
A: แน่นอน. คุณสามารถสร้างอ็อบเจ็กต์ `TextWatermark` (หรือ `ImageWatermark`) หลายตัวและเพิ่มลงในอินสแตนซ์ `Watermarker` เดียวกันตามลำดับ.

**Q: ฉันจะจัดการกับขนาดหน้าต่างๆ ใน PDF อย่างไร?**  
A: GroupDocs.Watermark จะปรับลายน้ำแต่ละอันให้เข้ากับมิติของหน้าที่มันถูกวางโดยอัตโนมัติ, ดังนั้นคุณไม่ต้องเขียนโค้ดเพิ่มเติมสำหรับความแตกต่างของขนาด.

**Q: ถ้าฟอนต์ที่ต้องการไม่มีในเซิร์ฟเวอร์จะทำอย่างไร?**  
A: ตรวจสอบให้แน่ใจว่าไฟล์ฟอนต์ได้ติดตั้งบนเครื่องโฮสต์, หรือฝังฟอนต์ที่กำหนดเองโดยให้เส้นทางเต็มไปยังไฟล์ `.ttf` หรือ `.otf` เมื่อสร้างอ็อบเจ็กต์ `Font`.

**Q: ไลบรารีทำงานกับ PDF ที่มีการป้องกันด้วยรหัสผ่านหรือไม่?**  
A: ได้. คุณสามารถส่งรหัสผ่านของเอกสารผ่าน `PdfLoadOptions` เมื่อเริ่มต้น `Watermarker`.

---

**อัปเดตล่าสุด:** 2026-01-31  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs