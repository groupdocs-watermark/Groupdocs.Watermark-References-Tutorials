---
date: '2025-12-19'
description: เรียนรู้วิธีเพิ่มลายน้ำข้อความลงในแผนภาพด้วย GroupDocs.Watermark สำหรับ
  Java ปกป้องเนื้อหาภาพของคุณอย่างมีประสิทธิภาพและรับประกันความสมบูรณ์ของเอกสาร
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: เพิ่มลายน้ำข้อความลงในแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java – คู่มือฉบับสมบูรณ์
type: docs
url: /th/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# เพิ่มลายน้ำข้อความลงในไดอะแกรมด้วย GroupDocs.Watermark สำหรับ Java: คู่มือฉบับสมบูรณ์

## บทนำ
การปกป้องเอกสารไดอะแกรมจากการใช้งานโดยไม่ได้รับอนุญาตเป็นสิ่งสำคัญ และ **การเพิ่มลายน้ำข้อความ** ให้เป็นวิธีที่ง่ายแต่มีประสิทธิภาพ ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีโหลดไฟล์ไดอะแกรม, สร้างลายน้ำข้อความที่ปรับแต่งได้, และนำไปใช้กับหน้าพื้นหลังหรือรูปร่างเฉพาะโดยใช้ **GroupDocs.Watermark for Java** เมื่อจบคู่มือคุณจะสามารถปกป้องทรัพย์สินภาพของคุณได้โดยยังคงรูปลักษณ์เดิมไว้ครบถ้วน

### คำตอบอย่างรวดเร็ว
- **“เพิ่มลายน้ำข้อความ” หมายถึงอะไร?**  
  หมายถึงการฝังข้อความกึ่งโปร่งใสลงบนเอกสารเพื่อบ่งบอกความเป็นเจ้าของหรือความลับ  
- **ไลบรารีใดรองรับการใส่ลายน้ำบนไดอะแกรม?**  
  GroupDocs.Watermark for Java ให้การสนับสนุนโดยตรงสำหรับรูปแบบไดอะแกรม (เช่น Visio, VSDX)  
- **ต้องการไลเซนส์หรือไม่?**  
  จำเป็นต้องมีไลเซนส์ชั่วคราวหรือเต็มสำหรับการใช้งานในสภาพแวดล้อมผลิต; มีรุ่นทดลองฟรีสำหรับการประเมินผล  
- **ฉันสามารถวางลายน้ำบนหน้าพื้นหลังได้หรือไม่?**  
  ได้ – ใช้ตัวเลือก `DiagramWatermarkPlacementType.SeparateBackgrounds` สำหรับ **ลายน้ำหน้าพื้นหลัง**  
- **โค้ดนี้เข้ากันได้กับ Java 8+ หรือไม่?**  
  แน่นอน – ไลบรารีทำงานกับ JDK 8 และรุ่นใหม่ต่อไป  

## สิ่งที่เรียกว่าลายน้ำข้อความสำหรับไดอะแกรมคืออะไร?
ลายน้ำข้อความคือข้อความที่อ่านได้ (มักเป็นกึ่งโปร่งใส) ที่แสดงบนหรืออยู่ด้านหลังองค์ประกอบของไดอะแกรม สามารถใช้เพื่อการสร้างแบรนด์, ปกป้องลิขสิทธิ์, หรือทำเครื่องหมายร่างที่เป็นความลับ  

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
- **รองรับรูปแบบหลากหลาย** – ทำงานกับ Visio, VSDX, และไดอะแกรมประเภทอื่น ๆ มากมาย  
- **การวางตำแหน่งละเอียด** – เลือกวางลายน้ำบนพื้นหน้า, พื้นหลัง, หรือรูปร่างเฉพาะได้  
- **API ที่เรียบง่าย** – สร้างและใช้ลายน้ำด้วยเพียงไม่กี่บรรทัดของโค้ด Java  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Watermark for Java** (เวอร์ชัน 24.11 หรือใหม่กว่า)  
- **Java Development Kit (JDK)** 8 หรือสูงกว่า  
- Maven (หรือการเพิ่ม JAR ด้วยตนเอง)  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
### การตั้งค่า Maven
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

### ดาวน์โหลดโดยตรง
ดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

### การรับไลเซนส์
- **รุ่นทดลองฟรี** – ประเมินคุณสมบัติทั้งหมดโดยไม่ต้องใช้คีย์ไลเซนส์  
- **ไลเซนส์ชั่วคราว** – ใช้ระหว่างการพัฒนาเพื่อเปิดใช้งานฟังก์ชันเต็ม  
- **การซื้อ** – รับไลเซนส์สำหรับการผลิตในโครงการเชิงพาณิชย์  

### การเริ่มต้นและตั้งค่าเบื้องต้น
ตรวจสอบให้แน่ใจว่ามีการนำเข้าต่อไปนี้ในคลาส Java ของคุณ:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## การดำเนินการตามขั้นตอน

### ขั้นตอนที่ 1: โหลดเอกสารไดอะแกรม
ก่อนอื่นให้ชี้ไลบรารีไปยังไฟล์ไดอะแกรมของคุณและกำหนดตัวเลือกการโหลด

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Explanation*: `DiagramLoadOptions` ให้คุณควบคุมวิธีการแยกวิเคราะห์ไดอะแกรมก่อนใส่ลายน้ำ  

### ขั้นตอนที่ 2: สร้างลายน้ำข้อความ
ต่อไปให้สร้างข้อความลายน้ำและกำหนดสไตล์การแสดงผล

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Explanation*: โค้ดนี้สร้าง `TextWatermark` ด้วยข้อความ **“Test watermark 1”** โดยใช้ฟอนต์ Calibri ขนาด 19  

### ขั้นตอนที่ 3: กำหนดการวางตำแหน่ง – ลายน้ำหน้าพื้นหลัง
เลือกตำแหน่งที่ต้องการให้ลายน้ำปรากฏ สำหรับ **ลายน้ำหน้าพื้นหลัง** ให้ใช้ตัวเลือกต่อไปนี้

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Explanation*: `DiagramShapeWatermarkOptions` ควบคุมตำแหน่งที่แน่นอน การตั้งค่า placement type เป็น `SeparateBackgrounds` จะเพิ่มลายน้ำให้กับแต่ละหน้าพื้นหลังของไดอะแกรม  

### ขั้นตอนที่ 4: ใส่ลายน้ำและบันทึก
สุดท้ายให้เพิ่มลายน้ำลงในเอกสาร, บันทึกผลลัพธ์, แล้วปล่อยทรัพยากร

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Explanation*: เมธอด `add` ใช้ `textWatermark` พร้อมตัวเลือกการวางตำแหน่ง จากนั้นบันทึกไดอะแกรมที่แก้ไขไปยัง `outputPath`  

## การประยุกต์ใช้งานจริง
- **การปกป้องทรัพย์สินทางปัญญา** – ป้องกันคู่แข่งไม่ให้ใช้ไดอะแกรมที่เป็นกรรมสิทธิ์ของคุณได้  
- **การเสริมสร้างแบรนด์** – ฝังชื่อบริษัทหรือโลโก้เป็นลายน้ำข้อความบนไดอะแกรมที่ส่งออกทั้งหมด  
- **เอกสารทางกฎหมาย** – ทำเครื่องหมายร่างที่เป็นความลับของแผนผังวิศวกรรม  
- **การส่งงานทางการศึกษา** – เพิ่มรหัสนักศึกษา หรือรหัสวิชาในไดอะแกรมเพื่อการตรวจสอบการคัดลอก  

## พิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ** – ปิดอินสแตนซ์ `Watermarker` (`watermarker.close()`) เพื่อปล่อยทรัพยากรเนทีฟ โดยเฉพาะเมื่อประมวลผลไฟล์ขนาดใหญ่  
- **การประมวลผลเป็นชุด** – วนลูปผ่านคอลเลกชันของเส้นทางไดอะแกรมและใช้ `Watermarker` ตัวเดียวซ้ำเมื่อเป็นไปได้ เพื่อลดภาระการทำงาน  

## ปัญหาที่พบบ่อยและวิธีแก้
| ปัญหา | วิธีแก้ |
|-------|----------|
| **OutOfMemoryError บนไดอะแกรมขนาดใหญ่** | เพิ่มขนาด heap ของ JVM (`-Xmx2g`) และประมวลผลไฟล์ทีละไฟล์ |
| **ลายน้ำไม่ปรากฏ** | ตรวจสอบให้แน่ใจว่าความเข้มของสีลายน้ำมีความคอนทราสต์เพียงพอ; ตั้งค่าความทึบผ่าน `textWatermark.setOpacity(0.5)` |
| **รูปแบบไดอะแกรมที่ไม่รองรับ** | ยืนยันว่ารูปแบบนั้นอยู่ในรายการรูปแบบที่สนับสนุนโดย GroupDocs.Watermark ตามเอกสาร |

## คำถามที่พบบ่อย

**ถาม: ขนาดฟอนต์ที่เหมาะสมสำหรับลายน้ำคือเท่าไหร่?**  
ตอบ: ขนาดที่เหมาะสมขึ้นอยู่กับมิติของไดอะแกรม; 12‑20 pt ทำงานได้ดีในกรณีส่วนใหญ่  

**ถาม: สามารถปรับสีของลายน้ำได้หรือไม่?**  
ตอบ: ได้, ใช้ `textWatermark.setColor(Color.GRAY)` (หรือ `java.awt.Color` ใดก็ได้)  

**ถาม: จะจัดการกับชุดเอกสารขนาดใหญ่อย่างไร?**  
ตอบ: ใช้ API การประมวลผลเป็นชุดของไลบรารีหรือเขียนลูปที่ใช้วัตถุ `Watermarker` ซ้ำเพื่อให้ใช้ทรัพยากรน้อยลง  

**ถาม: มีข้อจำกัดใดกับ GroupDocs.Watermark หรือไม่?**  
ตอบ: ไลบรารีรองรับรูปแบบไดอะแกรมส่วนใหญ่, แต่บางส่วนขยายที่เป็นกรรมสิทธิ์อาจไม่แสดงผลเต็มที่ ตรวจสอบ [documentation](https://docs.groupdocs.com/watermark/java/) สำหรับรายละเอียด  

**ถาม: จะขอรับการสนับสนุนหากเจอปัญหาได้อย่างไร?**  
ตอบ: เยี่ยมชม [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) เพื่อรับความช่วยเหลือจากชุมชน หรือ ติดต่อฝ่ายสนับสนุนของ GroupDocs โดยตรง  

## แหล่งข้อมูลเพิ่มเติม
- **เอกสาร**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **อ้างอิง API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **ดาวน์โหลด**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Repository บน GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **ฟอรั่มสนับสนุนฟรี**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **ไลเซนส์ชั่วคราว**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs