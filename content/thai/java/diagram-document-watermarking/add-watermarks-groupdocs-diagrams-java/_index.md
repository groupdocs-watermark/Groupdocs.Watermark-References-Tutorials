---
date: '2025-12-17'
description: เรียนรู้วิธีใส่ลายน้ำในหน้าตารางเฉพาะโดยใช้ GroupDocs.Watermark สำหรับ
  Java, เพิ่มลายน้ำลงในแผนภาพและเพิ่มลายน้ำรูปภาพใน Java. คู่มือขั้นตอนต่อขั้นตอนเพื่อปกป้องทรัพย์สินทางปัญญาของคุณ.
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: ใส่ลายน้ำหน้ากราฟิกแผนภาพเฉพาะโดยใช้ GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# ใส่น้ำหนักบนหน้าแผนภาพเฉพาะโดยใช้ GroupDocs.Watermark สำหรับ Java

การปกป้องแผนภาพของคุณเป็นสิ่งสำคัญ โดยเฉพาะเมื่อเกี่ยวข้องกับการรักษาสิทธิ์ทรัพย์สินทางปัญญาหรือการให้เครดิตที่เหมาะสม ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีใส่น้ำหนักบนหน้าแผนภาพเฉพาะ** ด้วย GroupDocs.Watermark สำหรับ Java ไม่ว่าคุณจะต้องการ **เพิ่มน้ำหนักลงในแผนภาพ** เป็นข้อความหรือ **เพิ่มโลโก้สไตล์ image watermark java** ในรูปแบบภาพก็ตาม เมื่อจบคู่มือคุณจะสามารถ:

- ใส่น้ำหนักข้อความลงในหน้าแผนภาพที่เลือกได้อย่างราบรื่น  
- แทรกน้ำหนักภาพลงในส่วนที่กำหนดของแผนภาพได้  
- ปรับปรุงประสิทธิภาพการทำงานเมื่อใช้ GroupDocs.Watermark  

มาทำให้แน่ใจว่าสภาพแวดล้อมพร้อมก่อนที่เราจะลงมือเขียนโค้ดกัน

## คำตอบสั้น ๆ
- **“watermark specific diagram page” หมายถึงอะไร?** หมายถึงการใส่น้ำหนักเฉพาะบนหน้าไฟล์แผนภาพที่เลือกไว้ โดยไม่กระทบกับหน้าอื่น  
- **ต้องใช้เวอร์ชันของไลบรารีใด?** GroupDocs.Watermark 24.11 หรือใหม่กว่า  
- **สามารถใช้ทั้งข้อความและภาพบนหน้าเดียวกันได้หรือไม่?** ได้ – เรียก `watermarker.add()` สำหรับแต่ละประเภทของน้ำหนัก  
- **ต้องมีไลเซนส์สำหรับการพัฒนาหรือไม่?** ไลเซนส์ทดลองชั่วคราวใช้ได้สำหรับการทดสอบ; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง  
- **Maven เป็นวิธีเดียวที่เพิ่มไลบรารีหรือไม่?** ไม่ – สามารถดาวน์โหลด JAR โดยตรงได้ (ดู “Direct Download” ด้านล่าง)

## “watermark specific diagram page” คืออะไร?
การทำ **watermark specific diagram page** คือการทำงานที่มุ่งเป้าไปที่หน้าเดียว (หรือหลายหน้า) ภายในเอกสารแผนภาพ (เช่น Visio *.vsdx*) และวางชั้นข้อความหรือภาพบนหน้าเหล่านั้น การทำเช่นนี้เหมาะสำหรับร่างที่เป็นความลับ, การสร้างแบรนด์, หรือการใส่ประกาศลิขสิทธิ์โดยไม่ต้องแก้ไขไฟล์ทั้งหมด

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
GroupDocs.Watermark ให้ API ระดับสูงที่ซ่อนความซับซ้อนของรูปแบบแผนภาพ, รองรับการประมวลผลเป็นชุด, และให้การควบคุมละเอียดเกี่ยวกับความทึบ, การวางตำแหน่ง, และการเลือกหน้า อีกทั้งยังผสานรวมได้อย่างราบรื่นกับ Maven และเครื่องมือสร้าง Java มาตรฐาน

## ข้อกำหนดเบื้องต้น
- ไลบรารี **GroupDocs.Watermark for Java** เวอร์ชัน 24.11 หรือใหม่กว่าได้ถูกติดตั้งแล้ว  
- สภาพแวดล้อมการพัฒนาที่มี Maven (หรือความสามารถในการเพิ่ม JAR ด้วยตนเอง)  
- ความรู้พื้นฐานของ Java และการเข้าถึงระบบไฟล์  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### ใช้ Maven
เพิ่ม GroupDocs.Watermark ในโปรเจกต์ของคุณผ่าน Maven โดยใส่โค้ดต่อไปนี้ลงใน `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดโดยตรงจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### การรับไลเซนส์
เริ่มต้นด้วยการทดลองฟรีโดยดาวน์โหลดไลเซนส์ชั่วคราว ตัวเลือกการซื้อไลเซนส์เต็มมีให้บนเว็บไซต์อย่างเป็นทางการหากคุณต้องการใช้งานต่อเนื่องกับ GroupDocs.Watermark  

### การเริ่มต้นและตั้งค่าเบื้องต้น
เมื่อไลบรารีพร้อมแล้ว ให้สร้างอินสแตนซ์ `Watermarker` ที่ชี้ไปยังแผนภาพที่คุณต้องการปกป้อง:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## วิธี **add watermark to diagram** – น้ำหนักข้อความ

### สร้างน้ำหนักข้อความ
กำหนดข้อความ, ฟอนต์, สี, และความทึบที่คุณต้องการใช้:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

### ตั้งค่าดัชนีหน้าสำหรับน้ำหนักข้อความ
ระบุหน้าที่ต้องการใส่น้ำหนักอย่างแม่นยำ ดัชนีหน้าเริ่มจากศูนย์:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

### เพิ่มน้ำหนักข้อความ
นำน้ำหนักไปใช้กับหน้าที่เลือก:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

## วิธี **add image watermark java** – น้ำหนักภาพ

### สร้างน้ำหนักภาพ
โหลดภาพที่ต้องการวางทับ (เช่นโลโก้บริษัท):

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

### ตั้งค่าดัชนีหน้าสำหรับน้ำหนักภาพ
เลือกหน้าที่จะแสดงน้ำหนักภาพ:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

### เพิ่มน้ำหนักภาพ
แทรกน้ำหนักภาพลงบนหน้าที่เลือก:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

## บันทึกและปิดทรัพยากร
หลังจากเพิ่มน้ำหนักทั้งหมดที่ต้องการแล้ว ให้บันทึกการเปลี่ยนแปลงและทำความสะอาด:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## การประยุกต์ใช้งานจริง
- **ความปลอดภัยของเอกสาร** – ใส่ป้าย “Confidential” บนร่างแผนภาพก่อนแชร์ให้พันธมิตร  
- **การสร้างแบรนด์** – ประทับโลโก้ของคุณบนหน้าเฉพาะของแผนภาพเชิงเทคนิค  
- **การปกป้องลิขสิทธิ์** – ฝังประกาศลิขสิทธิ์บนแผนภาพมูลค่าสูงเพื่อป้องกันการนำไปใช้โดยไม่ได้รับอนุญาต  

## พิจารณาประสิทธิภาพ
- จัดการหน่วยความจำอย่างมีประสิทธิภาพ โดยเฉพาะไฟล์ขนาดใหญ่  
- ปรับขนาดภาพให้เหมาะสมก่อนใช้เป็นน้ำหนักเพื่อเร่งการประมวลผล  
- ใช้การเก็บกวาดของ Java โดยปิดออบเจกต์น้ำหนักทั้งหมดหลังบันทึก  

## ปัญหาที่พบบ่อยและวิธีแก้
| Symptom | Likely Cause | Fix |
|---|---|---|
| Watermark not visible | Wrong page index | Verify the zero‑based index matches the intended page. |
| Image appears distorted | High‑resolution source image | Resize the image to a reasonable dimension (e.g., 300 × 300 px). |
| License error on production | Using trial license only | Apply a full license file via `License.setLicense("path/to/license.file")`. |
| Slow processing on big diagrams | Large file size & unclosed resources | Close `Watermarker` and individual watermark objects promptly. |

## คำถามที่พบบ่อย

**Q1: สามารถใส่น้ำหนักหลายชั้นบนหน้าแผนภาพเดียวได้หรือไม่?**  
A: ได้ เพียงเรียก `watermarker.add()` กับออบเจกต์น้ำหนักที่แตกต่างกันสำหรับ `DiagramPageWatermarkOptions` เดียวกัน  

**Q2: GroupDocs.Watermark for Java รองรับรูปแบบไฟล์ใดบ้าง?**  
A: รองรับรูปแบบแผนภาพและรูปภาพหลายประเภท ดูรายละเอียดเต็มใน [API documentation](https://reference.groupdocs.com/watermark/java)  

**Q3: จะจัดการกับปัญหาไลเซนส์เมื่อใช้รุ่นทดลองอย่างไร?**  
A: เริ่มต้นด้วยไลเซนส์ชั่วคราวฟรีจาก GroupDocs สำหรับการใช้งานจริงให้ซื้อไลเซนส์เต็มเพื่อเปิดใช้งานฟีเจอร์ทั้งหมด  

**Q4: มีเคล็ดลับการแก้ปัญหาที่น้ำหนักไม่แสดงตามคาดอย่างไร?**  
A: ตรวจสอบดัชนีหน้าให้ถูกต้อง, ยืนยันเส้นทางไฟล์ภาพ, และตรวจสอบว่าการตั้งค่าความทึบไม่ได้เป็น 0  

**Q5: จะปรับแต่งลักษณะของน้ำหนักเพิ่มเติมได้อย่างไร?**  
A: ปรับขนาดฟอนต์, ความทึบ, การหมุน, และตำแหน่งโดยใช้เมธอดของ `TextWatermark` หรือ `ImageWatermark`  

**Q6: สามารถใส่น้ำหนักหลายหน้าในคำสั่งเดียวได้หรือไม่?**  
A: ได้ – สร้างอินสแตนซ์ `DiagramPageWatermarkOptions`, ตั้งค่ารายการดัชนีหน้า, แล้วส่งให้ `watermarker.add()`  

**Q7: GroupDocs.Watermark รองรับไฟล์แผนภาพที่มีการป้องกันด้วยรหัสผ่านหรือไม่?**  
A: รองรับ – สามารถกำหนดรหัสผ่านผ่าน `DiagramLoadOptions.setPassword("yourPassword")` ก่อนโหลดไฟล์  

## แหล่งข้อมูล
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference Guide](https://reference.groupdocs.com/watermark/java)  
- [Download Library](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Information](https://purchase.groupdocs.com/temporary-license/)  

สำรวจแหล่งข้อมูลเหล่านี้เพื่อเพิ่มพูนความเข้าใจและศักยภาพของคุณกับ GroupDocs.Watermark สำหรับ Java ขอให้สนุกกับการใส่น้ำหนัก!

---

**Last Updated:** 2025-12-17  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs