---
date: '2026-02-18'
description: เรียนรู้วิธีเพิ่มลายน้ำลงในแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java.
  ปกป้องเนื้อหาภาพของคุณอย่างมีประสิทธิภาพและรับประกันความสมบูรณ์ของเอกสาร.
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: 'วิธีเพิ่มลายน้ำลงในแผนภาพด้วย GroupDocs.Watermark สำหรับ Java: คู่มือฉบับสมบูรณ์'
type: docs
url: /th/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# วิธีเพิ่มลายน้ำในแผนภาพด้วย GroupDocs.Watermark สำหรับ Java: คู่มือฉบับสมบูรณ์  

## บทนำ  
ในบทแนะนำนี้คุณจะได้ค้นพบ **วิธีเพิ่มลายน้ำ** ให้กับไฟล์แผนภาพของคุณเพื่อให้ไฟล์เหล่านั้นได้รับการปกป้องจากการใช้งานโดยไม่ได้รับอนุญาต การเพิ่มลายน้ำข้อความเป็นวิธีที่ง่ายแต่ทรงพลังในการระบุความเป็นเจ้าของ, ทำแบรนด์ให้กับสินทรัพย์ของคุณ, หรือปฏิบัติตามข้อกำหนดทางกฎหมาย คู่มือฉบับสมบูรณ์นี้จะแสดงวิธีการผสานลายน้ำข้อความลงในแผนภาพโดยใช้ **GroupDocs.Watermark for Java**—ไลบรารีที่แข็งแกร่งออกแบบมาสำหรับการใส่ลายน้ำในรูปแบบเอกสารหลากหลายประเภท  

### คำตอบสั้น  
- **วัตถุประสงค์หลักของลายน้ำคืออะไร?** เพื่อระบุความเป็นเจ้าของด้วยภาพและป้องกันการคัดลอกโดยไม่ได้รับอนุญาต.  
- **ไลบรารีใดที่รองรับการใส่ลายน้ำในแผนภาพด้วย Java?** GroupDocs.Watermark for Java.  
- **ฉันต้องใช้ Maven เพื่อใช้ไลบรารีหรือไม่?** ใช่, คุณสามารถเพิ่มได้ผ่าน Maven (ดูส่วน “groupdocs watermark maven”).  
- **ฉันสามารถปรับแต่งฟอนต์, ขนาด, และสีได้หรือไม่?** แน่นอน—ใช้ API `TextWatermark` เพื่อกำหนดคุณสมบัติเหล่านี้.  
- **ต้องการใบอนุญาตสำหรับการใช้งานในสภาพแวดล้อมการผลิตหรือไม่?** จำเป็นต้องมีใบอนุญาต GroupDocs.Watermark ที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  

## “วิธีเพิ่มลายน้ำ” หมายถึงอะไรในบริบทของแผนภาพ?  
การเพิ่มลายน้ำหมายถึงการฝังชั้นข้อความกึ่งโปร่งใสลงในแต่ละหน้า หรือรูปทรงของไฟล์แผนภาพ (เช่น Visio, SVG) ลายน้ำจะเดินทางพร้อมกับไฟล์ ทำให้ผู้ที่เปิดเอกสารเห็นได้ในขณะที่ไม่รบกวนการออกแบบเดิม.  

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?  
- **รองรับหลายรูปแบบ** – จัดการ Visio, SVG, และประเภทแผนภาพอื่น ๆ มากมาย.  
- **การรวม Maven อย่างง่าย** – ทำตามขั้นตอน “groupdocs watermark maven” เพื่อเริ่มต้นอย่างรวดเร็ว.  
- **การวางตำแหน่งละเอียด** – ควบคุมตำแหน่งที่ลายน้ำปรากฏ (พื้นหลัง, ด้านหน้า, รูปทรงเฉพาะ).  
- **ประสิทธิภาพที่ปรับแต่ง** – ออกแบบมาสำหรับไฟล์ขนาดใหญ่โดยใช้หน่วยความจำน้อยที่สุด.  

## ข้อกำหนดเบื้องต้น  
- **GroupDocs.Watermark for Java** (เวอร์ชัน 24.11 หรือใหม่กว่า)  
- **Java Development Kit (JDK)** 8+  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- Maven สำหรับการจัดการ dependencies (ไม่บังคับแต่แนะนำ).  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java  

### การกำหนดค่า Maven (groupdocs watermark maven)  
เพิ่ม repository และ dependency ต่อไปนี้ลงในไฟล์ `pom.xml` ของคุณ:  

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

**ดาวน์โหลดโดยตรง** – คุณยังสามารถรับ JAR ล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).  

### การรับใบอนุญาต  
- **Free Trial** – ประเมินไลบรารีโดยไม่ต้องใช้คีย์ใบอนุญาต.  
- **Temporary License** – ใช้คีย์ชั่วคราวในระหว่างการพัฒนาเพื่อเปิดใช้งานคุณสมบัติทั้งหมด.  
- **Purchase** – ซื้อใบอนุญาตการใช้งานในสภาพแวดล้อมการผลิตเพื่อการใช้ไม่จำกัด.  

### การเริ่มต้นและการตั้งค่าเบื้องต้น  
เพิ่ม import ที่จำเป็นในคลาส Java ของคุณ:  

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## วิธีเพิ่มลายน้ำในเอกสารแผนภาพ  

### ขั้นตอนที่ 1: โหลดเอกสารแผนภาพ  
แรกสุด, ระบุไฟล์แผนภาพที่คุณต้องการปกป้องให้ไลบรารีและสร้างอินสแตนซ์ `Watermarker`.  

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*คำอธิบาย*: `DiagramLoadOptions` ให้คุณปรับแต่งวิธีการแยกวิเคราะห์แผนภาพ (เช่น การจัดการฟอนต์ที่ฝังอยู่).  

### ขั้นตอนที่ 2: กำหนดค่าลายน้ำข้อความ (configure text watermark)  
สร้างอ็อบเจ็กต์ `TextWatermark` และตั้งค่าคุณสมบัติดูภาพเช่น ฟอนต์, ขนาด, และสี.  

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*คำอธิบาย*: บรรทัดนี้สร้างลายน้ำที่แสดงข้อความ **“Test watermark 1”** ด้วยฟอนต์ Calibri ขนาด 19‑point. คุณสามารถปรับแต่งเพิ่มเติมด้วย `setColor()`, `setOpacity()`, เป็นต้น.  

### ขั้นตอนที่ 3: กำหนดตัวเลือกการวางตำแหน่งสำหรับรูปทรงแผนภาพ  
ระบุตำแหน่งที่ลายน้ำควรปรากฏในแผนภาพ (พื้นหลัง, ด้านหน้า, หรือรูปทรงเฉพาะ).  

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*คำอธิบาย*: คลาส `DiagramShapeWatermarkOptions` ควบคุมการวางตำแหน่ง. ที่นี่เราเลือก `SeparateBackgrounds` เพื่อให้ลายน้ำแสดงบนแต่ละชั้นพื้นหลัง.  

### ขั้นตอนที่ 4: เพิ่มลายน้ำและบันทึกเอกสาร  
สุดท้าย, ใช้ลายน้ำและเขียนไฟล์ที่ได้รับการปกป้องลงดิสก์.  

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*คำอธิบาย*: `add()` แทรกลายน้ำที่กำหนดค่าโดยใช้ตัวเลือกที่ระบุ, `save()` เขียนผลลัพธ์, และ `close()` ปล่อยทรัพยากรเนทีฟ.  

## การประยุกต์ใช้จริง  
- **Intellectual Property Protection** – ป้องกันคู่แข่งจากการใช้แผนภาพที่เป็นทรัพย์สินของคุณซ้ำ.  
- **Branding** – แสดงชื่อบริษัทหรือโลโก้ของคุณอย่างสม่ำเสมอบนสินทรัพย์ที่ส่งออกทั้งหมด.  
- **Legal & Compliance** – ทำเครื่องหมายแผนผังที่เป็นความลับด้วยลายน้ำ “Confidential”.  
- **Academic Submissions** – ใส่แท็กงานของนักเรียนด้วยตัวระบุเฉพาะสำหรับการติดตามการคัดลอก.  

## การพิจารณาด้านประสิทธิภาพ  
- **Memory Management** – ใช้ซ้ำอินสแตนซ์ `Watermarker` เมื่อประมวลผลไฟล์เป็นชุด.  
- **Resource Cleanup** – เรียกใช้ `watermarker.close()` เสมอในบล็อก `finally` หรือใช้ try‑with‑resources หากรองรับ.  
- **Large Files** – สำหรับแผนภาพหลายเมกะไบต์, พิจารณาประมวลผลแต่ละหน้าแยกกันเพื่อลดการใช้หน่วยความจำสูงสุด.  

## สรุป  
คุณตอนนี้มีวิธีการครบถ้วนแบบขั้นตอนต่อขั้นตอนสำหรับ **วิธีเพิ่มลายน้ำ** ในเอกสารแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java. โดยการโหลดแผนภาพของคุณ, กำหนดค่า `TextWatermark`, ตั้งค่าตัวเลือกการวางตำแหน่ง, และบันทึกผลลัพธ์, คุณสามารถปกป้องทรัพย์สินภาพของคุณได้ด้วยความพยายามเพียงเล็กน้อย.  

ต่อไป, ทดลองใช้ฟอนต์, สี, และระดับความโปร่งใสที่แตกต่างกัน, หรือสำรวจการประมวลผลเป็นชุดเพื่อใส่ลายน้ำให้กับไลบรารีแผนภาพทั้งหมดโดยอัตโนมัติ.  

## ส่วนคำถามที่พบบ่อย  
**1. ขนาดฟอนต์ที่ดีที่สุดสำหรับลายน้ำคืออะไร?**  
ขนาดฟอนต์ที่เหมาะสมขึ้นอยู่กับประเภทของเอกสารและความต้องการด้านการมองเห็น.  

**2. ฉันสามารถปรับสีของลายน้ำได้หรือไม่?**  
ใช่, ตั้งค่าสีที่กำหนดเองโดยใช้เมธอด `textWatermark.setColor()`.  

**3. ฉันจะจัดการกับชุดเอกสารขนาดใหญ่ได้อย่างไร?**  
ใช้เมธอด API ที่ออกแบบมาสำหรับการประมวลผลเป็นชุดเพื่อเพิ่มประสิทธิภาพ.  

**4. มีข้อจำกัดใดกับ GroupDocs.Watermark หรือไม่?**  
ตรวจสอบ [documentation](https://docs.groupdocs.com/watermark/java/) เพื่อดูรายละเอียดการสนับสนุนฟีเจอร์และบันทึกความเข้ากันได้.  

**5. ฉันจะขอรับการสนับสนุนหากพบปัญหาได้อย่างไร?**  
เยี่ยมชม [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) เพื่อรับการสนับสนุนและคำแนะนำฟรี.  

## คำถามที่พบบ่อยเพิ่มเติม  

**Q: ฉันสามารถเปลี่ยนความโปร่งใสของลายน้ำได้หรือไม่?**  
A: ใช่, เรียก `textWatermark.setOpacity(0.5)` (ค่าระหว่าง 0 – 1).  

**Q: สามารถใส่ลายน้ำเฉพาะหน้าเลือกได้หรือไม่?**  
A: ใช้ `DiagramPageWatermarkOptions` เพื่อกำหนดเป้าหมายที่หน้า หรือรูปทรงเฉพาะ.  

**Q: ไลบรารีรองรับแผนภาพ SVG หรือไม่?**  
A: แน่นอน—GroupDocs.Watermark รองรับ SVG, Visio, และรูปแบบแผนภาพอื่น ๆ มากมาย.  

**Q: ฉันจะใส่ลายน้ำในแผนภาพที่มีการป้องกันด้วยรหัสผ่านได้อย่างไร?**  
A: ให้รหัสผ่านผ่าน `DiagramLoadOptions.setPassword("yourPassword")` ก่อนทำการโหลด.  

**Q: ต้องการเวอร์ชัน Java ใด?**  
A: รองรับ Java 8 หรือใหม่กว่าอย่างเต็มที่.  

## แหล่งข้อมูล  
- **Documentation**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub Repository**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support Forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

---  

**Last Updated:** 2026-02-18  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---