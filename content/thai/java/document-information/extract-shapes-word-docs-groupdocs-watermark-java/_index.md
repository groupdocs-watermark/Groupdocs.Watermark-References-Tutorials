---
date: '2026-02-05'
description: เรียนรู้วิธีดึงรูปทรงจากเอกสาร Word ด้วย GroupDocs.Watermark สำหรับ Java
  รวมถึงวิธีโหลดเอกสาร Word ใน Java และจัดการข้อมูลรูปทรง.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: วิธีดึงรูปทรงจากเอกสาร Word ด้วย GroupDocs.Watermark Java
type: docs
url: /th/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# วิธีการสกัดรูปทรงจากเอกสาร Word ด้วย GroupDocs.Watermark ใน Java

ในบทแนะนำนี้คุณจะได้ค้นพบ **วิธีการสกัดรูปทรง** จากเอกสาร Word ด้วยไลบรารี GroupDocs.Watermark สำหรับ Java ไม่ว่าคุณจะต้องการวิเคราะห์แผนภาพ ดึงภาพที่ฝังอยู่ หรืออัตโนมัติการสร้างรายงาน การสกัดเมตาดาต้ารูปทรงจะให้คุณควบคุมเพื่อสร้างกระบวนการประมวลผลเอกสารที่ชาญฉลาดยิ่งขึ้น เราจะเดินผ่านการตั้งค่าไลบรารี การโหลดเอกสาร Word และการดึงข้อมูลรายละเอียดของรูปทรง—ทั้งหมดในโค้ด Java ที่ชัดเจนและเป็นขั้นตอน

## คำตอบอย่างรวดเร็ว
- **'extract shapes' หมายถึงอะไร?** การดึงเมตาดาต้า (ประเภท, ขนาด, ตำแหน่ง, ข้อความ, ภาพ) สำหรับแต่ละวัตถุการวาดในไฟล์ Word.  
- **ไลบรารีที่ใช้ทำงานนี้คืออะไร?** GroupDocs.Watermark สำหรับ Java.  
- **ต้องการใบอนุญาตหรือไม่?** รุ่นทดลองทำงานได้สำหรับการพัฒนา; ใบอนุญาตเต็มจะลบข้อจำกัดการใช้งาน.  
- **สามารถดึงภาพจากรูปทรงได้หรือไม่?** ได้ – API เปิดเผยไบต์ของภาพสำหรับรูปทรงประเภท picture.  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือใหม่กว่า.

## “วิธีการสกัดรูปทรง” คืออะไรในบริบทของเอกสาร Word?
การสกัดรูปทรงหมายถึงการเข้าถึงแต่ละองค์ประกอบการวาดโดยโปรแกรม—ภาพ, WordArt, auto‑shapes, แผนภูมิ, และแม้กระทั่งรูปทรงที่ฝังอยู่ในส่วนหัวหรือส่วนท้าย ข้อมูลนี้สามารถนำไปใช้สำหรับการตรวจสอบ, การย้ายข้อมูล, หรือการวิเคราะห์ที่ขับเคลื่อนด้วยเนื้อหา.

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
GroupDocs.Watermark ให้ API ระดับสูงที่ใช้หน่วยความจำน้อยและทำให้ซับซ้อนของรูปแบบ Office Open XML ง่ายขึ้น มันช่วยให้คุณ:
- โหลดเอกสารอย่างรวดเร็ว (`WordProcessingLoadOptions`).  
- วนผ่านส่วนต่าง ๆ และรูปทรงโดยไม่ต้องจัดการ XML ระดับต่ำ.  
- ดึงข้อมูลภาพ, ข้อความ, การจัดแนว, และการหมุนในคำสั่งเดียว.  
- ผสานรวมอย่างราบรื่นกับบริการ Java หรือ micro‑services ที่มีอยู่แล้ว.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK)** 8 หรือสูงกว่า.  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse.  
- ความรู้พื้นฐานเกี่ยวกับ Java I/O.  
- เข้าถึงใบอนุญาต **GroupDocs.Watermark for Java** หรือรุ่นทดลอง.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
รวมไลบรารีผ่าน Maven หรือการดาวน์โหลดโดยตรง.

### การใช้ Maven
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
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับใบอนุญาต
รุ่นทดลองฟรีเพียงพอสำหรับการทดสอบ สำหรับการใช้งานจริงให้ขอใบอนุญาตถาวรเพื่อเปิดใช้งานคุณสมบัติทั้งหมด.

## คู่มือการใช้งาน
เราจะแบ่งการทำงานออกเป็นสองขั้นตอนชัดเจน: **การโหลดเอกสาร Word** และ **การสกัดข้อมูลรูปทรง**.

### ขั้นตอน 1: โหลดเอกสาร Word (load word document java)
ก่อนอื่นให้กำหนดค่า load options และสร้างอินสแตนซ์ `Watermarker` ซึ่งจะเตรียมเอกสารสำหรับการตรวจสอบต่อไป.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **เคล็ดลับ:** ให้จำกัดขอบเขตของอินสแตนซ์ `Watermarker` ให้แคบที่สุด; ปิดมันโดยเร็วจะช่วยปล่อยทรัพยากรเนทีฟและหลีกเลี่ยงการรั่วของหน่วยความจำ.

### ขั้นตอน 2: สกัดข้อมูลรูปทรง (extract images from shapes)
ต่อไปเราจะดึงรายละเอียดของทุกรูปทรงรวมถึงภาพที่ฝังอยู่ โค้ดจะวนผ่านแต่ละส่วนและแต่ละรูปทรงและพิมพ์เมตาดาต้าที่เป็นประโยชน์.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**สิ่งที่โค้ดนี้ทำ:**  
- ดึง **type** ของแต่ละรูปทรง (เช่น picture, WordArt).  
- พิมพ์ค่า **size**, **position**, และ **rotation**.  
- แสดง **alternative text** และ **name** ซึ่งมีประโยชน์สำหรับการตรวจสอบการเข้าถึง.  
- หากรูปทรงมีภาพ จะพิมพ์ **pixel dimensions** และ **byte size** ของภาพ—เหมาะสำหรับการสกัดภาพจากรูปทรง.

### ข้อผิดพลาดทั่วไปและวิธีแก้
| Issue | Cause | Solution |
|-------|-------|----------|
| `FileNotFoundException` | เส้นทางไฟล์ไม่ถูกต้องหรือไม่มีสิทธิ์ | ตรวจสอบเส้นทางแบบ absolute/relative และให้แน่ใจว่าไฟล์สามารถอ่านได้. |
| Null `shape.getImage()` | รูปทรงไม่ใช่ภาพ (เช่น auto‑shape) | ตรวจสอบด้วย `if (shape.getImage() != null)` ตามตัวอย่าง. |
| การใช้หน่วยความจำสูงกับเอกสารขนาดใหญ่ | โหลดเอกสารทั้งหมดในครั้งเดียว | ประมวลผลส่วนหนึ่งส่วนหนึ่งหรือเพิ่ม heap ของ JVM (`-Xmx`). |
| รูปทรงใน header/footer หาย | ไม่ได้ตรวจสอบ `shape.getHeaderFooter()` | ตัวอย่างจะบันทึกเมื่อรูปทรงอยู่ใน header/footer. |

## การประยุกต์ใช้งานจริง
1. **Automated Report Generation** – ดึงแผนภูมิและแผนภาพเพื่อนำไปฝังใน PDF ที่ต่อจากนั้น.  
2. **Compliance Auditing** – ตรวจสอบว่ารูปทรงทั้งหมดมี alternative text ที่เหมาะสมสำหรับการเข้าถึง.  
3. **Content Migration** – ส่งออกภาพที่ฝังอยู่จากไฟล์ Word เก่าไปยังระบบจัดการสินทรัพย์ดิจิทัล.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Release resources**: ควรเรียก `watermarker.close()` ในบล็อก `finally` หรือใช้ try‑with‑resources หากห่อหุ้ม API.  
- **Chunk processing**: สำหรับเอกสารที่ใหญ่กว่า 50 MB ควรประมวลผลแต่ละส่วนแยกกันเพื่อให้ใช้หน่วยความจำน้อยลง.  
- **Thread safety**: อินสแตนซ์ `Watermarker` ไม่ปลอดภัยต่อหลายเธรด; สร้างอินสแตนซ์ใหม่ต่อเธรด.

## สรุป
คุณได้เรียนรู้ **วิธีการสกัดรูปทรง** จากเอกสาร Word ด้วย GroupDocs.Watermark สำหรับ Java ตั้งแต่การโหลดไฟล์จนถึงการอ่านเมตาดาต้าและข้อมูลภาพที่ฝังอยู่ ความสามารถนี้เปิดประตูสู่การวิเคราะห์เอกสารขั้นสูง, การสร้างสายงานอัตโนมัติ, และการตรวจสอบการเข้าถึง.

### ขั้นตอนต่อไป
- ทดลองแก้ไขคุณสมบัติของรูปทรง (เช่น การปรับขนาดหรือการย้ายตำแหน่ง).  
- ผสานวิธีนี้กับ **GroupDocs.Parser** เพื่อสกัดข้อความรอบ ๆ.  
- รวมตรรกะการสกัดเข้าในบริการ REST เพื่อประมวลผลตามความต้องการ.

## ส่วนคำถามที่พบบ่อย
**Q: GroupDocs.Watermark for Java คืออะไร?**  
A: เป็นไลบรารีครบวงจรที่ออกแบบมาเพื่อจัดการวอเตอร์มาร์กและเนื้อหาเอกสารในหลายรูปแบบ, รองรับงานเช่นการสกัดรูปทรง, การดึงภาพ, และการจัดการข้อความ.

**Q: สามารถสกัดภาพจากรูปทรงได้โดยไม่ต้องมีใบอนุญาตหรือไม่?**  
A: รุ่นทดลองอนุญาตให้สกัดได้, แต่ใบอนุญาตเต็มจะลบข้อจำกัดการใช้งานและเปิดใช้งานการปรับใช้เชิงพาณิชย์.

**Q: วิธีนี้ทำงานกับไฟล์ `.doc` (binary) หรือไม่?**  
A: ใช่, API รองรับทั้งรูปแบบ `.docx` และ `.doc` แบบเก่า.

**Q: จะจัดการกับเอกสารที่มีรหัสผ่านอย่างไร?**  
A: ให้ตั้งค่ารหัสผ่านผ่าน `WordProcessingLoadOptions.setPassword("yourPassword")` ก่อนสร้าง `Watermarker`.

**Q: มีวิธีส่งออกข้อมูลรูปทรงที่สกัดเป็น JSON หรือไม่?**  
A: คุณสามารถแมปค่าที่พิมพ์ออกเป็น POJO แล้วใช้ไลบรารี JSON ใด ๆ (เช่น Jackson) เพื่อทำการซีเรียลไลซ์คอลเลกชัน.

**อัปเดตล่าสุด:** 2026-02-05  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs