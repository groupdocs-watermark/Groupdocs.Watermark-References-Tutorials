---
date: '2026-02-16'
description: เรียนรู้วิธีใส่น้ำลายน้ำในหน้าภาพแผนภาพเฉพาะด้วย GroupDocs.Watermark
  สำหรับ Java รวมถึงวิธีเพิ่มน้ำลายน้ำรูปภาพใน Java และปกป้องไฟล์ของคุณ
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: ใส่ลายน้ำบนหน้าภาพแผนภาพเฉพาะโดยใช้ GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# การใส่ลายน้ำในหน้าแผนภาพเฉพาะโดยใช้ GroupDocs.Watermark for Java

การปกป้องแผนภาพของคุณเป็นสิ่งสำคัญ โดยเฉพาะเมื่อคุณต้องการ **watermark specific diagram page** เพื่อความปลอดภัยของทรัพย์สินทางปัญญาหรือการระบุแบรนด์ ในบทแนะนำนี้คุณจะได้เรียนรู้ขั้นตอนการเพิ่มลายน้ำแบบข้อความและภาพลงในหน้าที่เลือกของไฟล์แผนภาพโดยใช้ **GroupDocs.Watermark for Java** เมื่อเสร็จแล้วคุณจะพร้อมที่จะรักษาความปลอดภัยของแผนภาพและควบคุมตำแหน่งที่ลายน้ำแต่ละอันปรากฏได้อย่างแม่นยำ

## คำตอบด่วน
- **วัตถุประสงค์หลักคืออะไร?** เพิ่มลายน้ำในหน้าแผนภาพที่เลือก.  
- **ไลบรารีที่จำเป็นคืออะไร?** GroupDocs.Watermark for Java (Maven หรือดาวน์โหลดโดยตรง).  
- **ฉันสามารถเพิ่มลายน้ำภาพใน Java ได้หรือไม่?** ใช่ – ใช้ `ImageWatermark` กับตัวเลือกเฉพาะหน้า.  
- **ฉันต้องการใบอนุญาตหรือไม่?** ใบอนุญาตทดลองชั่วคราวทำงานสำหรับการทดสอบ; จำเป็นต้องใช้ใบอนุญาตเต็มสำหรับการผลิต.  
- **ต้องใช้โค้ดกี่บรรทัด?** น้อยกว่า 30 บรรทัดสำหรับกระบวนการลายน้ำข้อความ + ภาพครบวงจร.

## “watermark specific diagram page” คืออะไร?
**watermark specific diagram page** หมายถึงการใส่เครื่องหมายภาพ—ข้อความหรือรูปภาพ—เฉพาะบนหน้าที่คุณเลือกภายในแผนภาพหลายหน้า (เช่น Visio . vsdx) ซึ่งช่วยให้คุณควบคุมการใส่แบรนด์, ประกาศความลับ, หรือข้อความลิขสิทธิ์ได้อย่างละเอียดโดยไม่กระทบต่อเอกสารทั้งหมด

## ทำไมต้องใช้ GroupDocs.Watermark for Java?
- **การควบคุมหน้าระดับเต็ม** – เลือกดัชนีหน้าที่ต้องการได้ตามต้องการ.  
- **การจัดรูปแบบที่หลากหลาย** – ฟอนต์, สี, ความทึบ, การหมุน, และการปรับขนาดภาพทั้งหมดสามารถกำหนดค่าได้.  
- **ประสิทธิภาพที่ปรับให้เหมาะสม** – ประมวลผลแผนภาพขนาดใหญ่ได้อย่างมีประสิทธิภาพและรวมเข้ากับการสร้าง Maven ได้อย่างราบรื่น.  
- **รองรับหลายรูปแบบ** – ทำงานกับ Visio, SVG, และรูปแบบแผนภาพอื่น ๆ อีกมากมาย.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Watermark for Java** เวอร์ชัน 24.11 หรือใหม่กว่า.  
- Maven หรือดาวน์โหลด JAR โดยตรง.  
- การตั้งค่าพัฒนา Java พื้นฐาน (แนะนำ JDK 8+).

## การตั้งค่า GroupDocs.Watermark for Java
### การใช้ Maven groupdocs watermark
เพิ่ม GroupDocs.Watermark ในโปรเจกต์ของคุณผ่าน Maven โดยใส่โค้ดต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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

#### การรับใบอนุญาต
เริ่มต้นด้วยการทดลองฟรีโดยดาวน์โหลดใบอนุญาตชั่วคราว ตัวเลือกการซื้อพร้อมให้บริการบนเว็บไซต์อย่างเป็นทางการของพวกเขาหากคุณต้องการใช้ GroupDocs.Watermark ต่อเนื่อง

### การเริ่มต้นและตั้งค่าเบื้องต้น
หลังจากติดตั้งแล้ว ให้เริ่มต้นคลาส `Watermarker` สำหรับการทำงานลายน้ำ:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## คู่มือการใช้งาน
### การเพิ่มลายน้ำข้อความในหน้าเฉพาะ
เพื่อเพิ่มลายน้ำข้อความ ให้สร้างและกำหนดค่าก่อนระบุหน้าที่เป้าหมาย

#### สร้างลายน้ำข้อความ
กำหนดลายน้ำข้อความของคุณด้วยเนื้อหาที่ปรับได้, รูปแบบฟอนต์, ขนาด, ฯลฯ:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### กำหนดดัชนีหน้าสำหรับลายน้ำ
ระบุว่าหน้าแผนภาพใดจะแสดงลายน้ำโดยใช้ `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### เพิ่มลายน้ำข้อความ
เพิ่มลายน้ำที่กำหนดค่าแล้วลงในแผนภาพ:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### การเพิ่มลายน้ำภาพในหน้าเฉพาะ
ทำตามขั้นตอนคล้ายกันสำหรับลายน้ำภาพโดยใช้วัตถุ `ImageWatermark`

#### สร้างลายน้ำภาพ
สร้างอินสแตนซ์ของ `ImageWatermark` พร้อมเส้นทางภาพลายน้ำที่ต้องการ:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### กำหนดดัชนีหน้าสำหรับลายน้ำ
ระบุว่าหน้าใดควรแสดงลายน้ำภาพ:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### เพิ่มลายน้ำภาพ
เพิ่มภาพลงในหน้าแผนภาพที่คุณระบุ:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### บันทึกและปิดทรัพยากร
อย่าลืมบันทึกการเปลี่ยนแปลงและปิดทรัพยากรเพื่อป้องกันการรั่วไหล:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## การประยุกต์ใช้งานจริง
- **ความปลอดภัยของเอกสาร** – ใส่ลายน้ำความลับเฉพาะบนหน้าที่มีแผนผังที่สำคัญ.  
- **การสร้างแบรนด์** – วางโลโก้บริษัทบนหน้าปกขณะที่หน้าภายในยังคงสะอาด.  
- **การปกป้องลิขสิทธิ์** – เพิ่มข้อความลิขสิทธิ์บนหน้าสุดท้ายของชุดแผนภาพเทคนิค.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ** – ปิดวัตถุลายน้ำแต่ละอันหลังจากบันทึกเพื่อปลดปล่อยทรัพยากรเนทีฟ.  
- **การปรับรูปภาพ** – ใช้ไฟล์ PNG/JPEG ขนาดเหมาะเพื่อให้การประมวลผลเร็ว.  
- **การประมวลผลเป็นชุด** – เมื่อจัดการแผนภาพหลายไฟล์ ให้ใช้อินสแตนซ์ `Watermarker` ตัวเดียวซ้ำได้เท่าที่เป็นไปได้.

## ปัญหาที่พบบ่อยและวิธีแก้ไข
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| ลายน้ำไม่ปรากฏ | `pageIndex` ผิด (เริ่มจากศูนย์) | ตรวจสอบให้แน่ใจว่าดัชนีตรงกับหน้าที่ต้องการ. |
| ภาพบิดเบี้ยว | ภาพต้นฉบับความละเอียดสูง | ปรับขนาดภาพก่อนสร้าง `ImageWatermark`. |
| เกิดข้อผิดพลาดใบอนุญาตในผลิตภัณฑ์ | ใช้ใบอนุญาตทดลองเกินระยะเวลาที่กำหนด | ใช้ไฟล์ใบอนุญาตเต็มผ่าน `License.setLicense("path/to/license.json")`. |

## คำถามที่พบบ่อย

**Q1: ฉันสามารถเพิ่มลายน้ำหลายรายการในหน้าแผนภาพเดียวได้หรือไม่?**  
A1: ใช่ เพียงเรียก `watermarker.add()` ด้วยวัตถุลายน้ำที่แตกต่างกันสำหรับดัชนีหน้าเดียวกัน.

**Q2: ไฟล์รูปแบบใดบ้างที่ GroupDocs.Watermark for Java รองรับ?**  
A2: รองรับรูปแบบแผนภาพและรูปภาพหลายประเภท ดูรายละเอียดเต็มใน [API documentation](https://reference.groupdocs.com/watermark/java).

**Q3: ฉันจะจัดการกับปัญหาใบอนุญาตเมื่อใช้เวอร์ชันทดลองได้อย่างไร?**  
A3: เริ่มต้นด้วยใบอนุญาตชั่วคราวฟรีจาก GroupDocs. ซื้อใบอนุญาตเต็มเพื่อเปิดใช้งานคุณสมบัติทั้งหมดสำหรับการผลิต.

**Q4: มีเคล็ดลับการแก้ไขปัญหาที่พบบ่อยเมื่อลายน้ำไม่แสดงตามที่คาดหวังหรือไม่?**  
A4: ตรวจสอบให้แน่ใจว่าดัชนีหน้าถูกต้องและตรวจสอบเส้นทางไฟล์ภาพอีกครั้ง นอกจากนี้ตรวจสอบว่าความทึบของลายน้ำไม่ได้ตั้งเป็น 0.

**Q5: ฉันจะปรับแต่งลักษณะลายน้ำให้ละเอียดขึ้นได้อย่างไร?**  
A5: ปรับขนาดฟอนต์, ความทึบ, การหมุน, และตำแหน่งโดยใช้เมธอดที่มีใน `TextWatermark` หรือ `ImageWatermark`.

## แหล่งข้อมูล
- [เอกสาร GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/)
- [คู่มืออ้างอิง API](https://reference.groupdocs.com/watermark/java)
- [ดาวน์โหลดไลบรารี](https://releases.groupdocs.com/watermark/java/)
- [ที่เก็บ GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/watermark/10)
- [ข้อมูลใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

สำรวจแหล่งข้อมูลเหล่านี้เพื่อเพิ่มพูนความเข้าใจและความสามารถของคุณกับ GroupDocs.Watermark for Java. ขอให้สนุกกับการใส่ลายน้ำ!

---

**Last Updated:** 2026-02-16  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs