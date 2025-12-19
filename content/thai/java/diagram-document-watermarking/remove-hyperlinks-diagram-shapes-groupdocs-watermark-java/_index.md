---
date: '2025-12-19'
description: เรียนรู้วิธีการลบไฮเปอร์ลิงก์จากรูปทรงแผนภาพด้วย GroupDocs.Watermark
  Java ซึ่งเป็นขั้นตอนสำคัญสำหรับความปลอดภัยของเอกสาร Java และการลบไฮเปอร์ลิงก์เป็นกลุ่ม
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: วิธีลบไฮเปอร์ลิงก์จากรูปทรงแผนภาพโดยใช้ GroupDocs.Watermark Java
type: docs
url: /th/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# วิธีการลบไฮเปอร์ลิงก์จากรูปร่างแผนภาพโดยใช้ GroupDocs.Watermark Java

การจัดการเอกสารดิจิทัลมักเกี่ยวข้องกับการแก้ไขแผนภาพ โดยเฉพาะเมื่อ **ลบไฮเปอร์ลิงก์** เพื่อความปลอดภัยหรือความชัดเจน ในบทแนะนำนี้ คุณจะได้เรียนรู้ **วิธีการลบไฮเปอร์ลิงก์** จากรูปร่างแผนภาพด้วย GroupDocs.Watermark สำหรับ Java เพื่อให้ไฟล์ของคุณสะอาด ปลอดภัย และเป็นมืออาชีพ

## Quick Answers
- **วัตถุประสงค์หลักคืออะไร?** เพื่อลบไฮเปอร์ลิงก์ที่ไม่ต้องการออกจากรูปร่างแผนภาพเพื่อเพิ่มความปลอดภัยของเอกสาร  
- **ใช้ไลบรารีใด?** GroupDocs.Watermark for Java (เวอร์ชัน 24.11 หรือใหม่กว่า)  
- **ต้องการไลเซนส์หรือไม่?** สามารถใช้รุ่นทดลองเพื่อทดสอบได้; ต้องมีไลเซนส์ที่ถูกต้องสำหรับการใช้งานในโปรดักชัน  
- **สามารถประมวลผลหลายไฟล์พร้อมกันได้หรือไม่?** ได้ – สามารถใส่ตรรกะเดียวกันไว้ในลูปแบชได้  
- **Java 8 เพียงพอหรือไม่?** รองรับ Java 8+; แนะนำให้ใช้ JDK ที่ใหม่กว่า

## What is “how to remove hyperlinks” in the context of diagrams?
การลบไฮเปอร์ลิงก์หมายถึงการลบการอ้างอิง URL ที่แนบอยู่กับรูปร่างภายในไฟล์แผนภาพ (เช่น Visio *.vsdx) การดำเนินการนี้ช่วยป้องกันการนำทางโดยบังเอิญไปยังเว็บไซต์ภายนอกและช่วยให้สอดคล้องกับนโยบายการปฏิบัติตามหรือความปลอดภัยภายใน

## Why use GroupDocs.Watermark Java for this task?
- **รองรับรูปแบบที่หลากหลาย** – ทำงานกับประเภทแผนภาพหลายรูปแบบ  
- **API ระดับละเอียด** – ให้คุณกำหนดเป้าหมายที่รูปร่างแต่ละอันและคอลเลกชันไฮเปอร์ลิงก์ของมันได้  
- **ประสิทธิภาพสูง** – เหมาะสำหรับการประมวลผลไฟล์เดี่ยวหรือแบบจำนวนมาก  

## Prerequisites
- ไลบรารี **GroupDocs.Watermark** เวอร์ชัน 24.11 หรือใหม่กว่า  
- Maven หรือการดาวน์โหลด JAR โดยตรง (ดูขั้นตอนการตั้งค่าด้านล่าง)  
- Java Development Kit (JDK 8 หรือใหม่กว่า) และ IDE เช่น IntelliJ IDEA หรือ Eclipse  

## Setting Up GroupDocs.Watermark for Java
เพื่อเริ่มต้น ให้เพิ่มไลบรารีในโปรเจกต์ของคุณผ่าน Maven หรือดาวน์โหลด JAR

### Maven Setup
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

### Direct Download
หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### License Acquisition Steps
- เริ่มต้นด้วยรุ่นทดลองฟรีเพื่อประเมิน API  
- สำหรับการใช้งานในโปรดักชัน ให้รับไลเซนส์ชั่วคราวหรือเต็มรูปแบบจากพอร์ทัลของ GroupDocs  

#### Basic Initialization and Setup
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## How to Remove Hyperlinks from Diagram Shapes
ด้านล่างเป็นคำแนะนำแบบขั้นตอนที่พาคุณผ่านการโหลดแผนภาพ, การค้นหารูปร่าง, และการลบไฮเปอร์ลิงก์ที่ไม่ต้องการออก

### Step 1: Load the Diagram File
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*ทำไม?* การโหลดไฟล์ทำให้คุณสามารถเข้าถึงโครงสร้างภายในของไฟล์ได้โดยโปรแกรม

### Step 2: Access Shape Content
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*ทำไม?* คุณต้องการอ้างอิงถึงรูปร่างเฉพาะที่อาจมีไฮเปอร์ลิงก์อยู่

### Step 3: Iterate and Remove Hyperlinks
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*ทำไม?* การวนลูปย้อนกลับช่วยป้องกันข้อผิดพลาดของดัชนีเมื่อคุณลบรายการจากคอลเลกชัน

### Step 4: Save and Close
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*ทำไม?* การบันทึกการเปลี่ยนแปลงและการปล่อยทรัพยากรช่วยหลีกเลี่ยงการรั่วไหลของหน่วยความจำและไฟล์ที่ถูกล็อก

## Batch Remove Hyperlinks (Advanced Use Case)
หากต้องทำความสะอาดแผนภาพหลายไฟล์พร้อมกัน ให้นำตรรกะข้างต้นใส่ไว้ในลูปที่วนผ่านรายการเส้นทางไฟล์ การเรียก API เดียวกันใช้ได้; เพียงเปลี่ยนไดเรกทอรีอินพุตและเอาต์พุตสำหรับแต่ละรอบ วิธีนี้สอดคล้องกับความต้องการ **batch remove hyperlinks** สำหรับคลังเอกสารขนาดใหญ่

## Practical Applications
การลบไฮเปอร์ลิงก์จากรูปร่างแผนภาพมีประโยชน์ในหลายสถานการณ์จริง:

1. **เพื่อความปลอดภัย** – ป้องกันลิงก์ภายนอกที่อาจทำให้เครือข่ายของคุณเสี่ยงต่อฟิชชิ่งหรือมัลแวร์  
2. **เพื่อการปฏิบัติตาม** – สอดคล้องกับนโยบายองค์กรที่ห้าม URL ออกสู่ภายนอกในเอกสารที่แชร์  
3. **เพื่อความชัดเจน** – สร้างการนำเสนอที่สะอาดตาโดยไม่มีไฮเปอร์ลิงก์ที่ไม่จำเป็นหรือทำให้สับสน  

## Performance Considerations
### Optimizing Performance
- ใช้รูปแบบการวนลูปย้อนกลับตามที่แสดงข้างต้นเพื่อให้ลูปทำงานได้อย่างมีประสิทธิภาพ  
- ปิดวัตถุ `Watermarker` ทันทีเมื่อทำงานเสร็จเพื่อคืนหน่วยความจำ

### Resource Usage Guidelines
- ตรวจสอบการใช้ CPU และ RAM เมื่อประมวลผลแผนภาพขนาดใหญ่  
- สำหรับงานแบบแบช ควรพิจารณาการสตรีมไฟล์แทนการโหลดทั้งหมดพร้อมกัน

### Best Practices for Java Memory Management
- หลีกเลี่ยงการสร้างออบเจ็กต์ภายในลูปที่แคบ  
- ใช้ `try‑with‑resources` เมื่อเป็นไปได้เพื่อทำความสะอาดอัตโนมัติ

## Frequently Asked Questions
1. **ฉันจะจัดการกับหลายรูปร่างได้อย่างไร?**  
   วนลูปผ่านทุกหน้าและรูปร่างของมันโดยใช้ตรรกะการลบไฮเปอร์ลิงก์เดียวกันสำหรับแต่ละรูปร่าง  

2. **กระบวนการนี้สามารถทำอัตโนมัติสำหรับแบชของแผนภาพจำนวนมากได้หรือไม่?**  
   ได้ – ฝังโค้ดในรูทีนการประมวลผลแบชหรือรวมเข้ากับระบบจัดการเอกสารของคุณ  

3. **ถ้าต้องการลบไฮเปอร์ลิงก์เฉพาะหน้าใดหน้าหนึ่งจะทำอย่างไร?**  
   เข้าถึงหน้าที่ต้องการโดยใช้ดัชนี (`content.getPages().get_Item(pageIndex)`) แล้วกำหนดเป้าหมายที่รูปร่างบนหน้านั้นเท่านั้น  

4. **ต้องมีไลเซนส์สำหรับการใช้งานในโปรดักชันของ GroupDocs.Watermark หรือไม่?**  
   จำเป็นต้องมีไลเซนส์เชิงพาณิชย์ที่ถูกต้องหลังจากช่วงทดลองหมดอายุ  

5. **วิธีนี้ทำงานกับรูปแบบแผนภาพอื่นได้หรือไม่?**  
   GroupDocs.Watermark รองรับหลายประเภทแผนภาพ; ตรวจสอบความเข้ากันได้ในเอกสารอย่างเป็นทางการ  

**Additional Q&A**

**Q:** *สามารถบันทึกว่าไฮเปอร์ลิงก์ใดบ้างที่ถูกลบได้หรือไม่?*  
**A:** ได้ – ก่อนเรียก `removeAt(i)` ให้ดึง `shape.getHyperlinks().get_Item(i).getAddress()` แล้วเขียนลงไฟล์บันทึก

**Q:** *การลบไฮเปอร์ลิงก์จะส่งผลต่อรูปลักษณ์ของรูปร่างหรือไม่?*  
**A:** ไม่. รูปร่างยังคงมีเรขาคณิตเหมือนเดิม; เพียงเมตาดาต้าลิงก์ถูกลบออก

**Q:** *ต้องทำการปรับสไตล์ใหม่หลังการลบหรือไม่?*  
**A:** ปกติไม่จำเป็น; การลบไฮเปอร์ลิงก์ไม่ทำให้สีเติม, เส้น, หรือสไตล์ข้อความเปลี่ยนแปลง

## Conclusion
คุณมีวิธีที่ครบถ้วนและพร้อมใช้งานในโปรดักชันสำหรับ **วิธีการลบไฮเปอร์ลิงก์** จากรูปร่างแผนภาพโดยใช้ GroupDocs.Watermark for Java แล้ว การทำตามขั้นตอนเหล่านี้จะช่วยให้แผนภาพของคุณปลอดภัย ปฏิบัติตามนโยบาย และดูเป็นมืออาชีพ

---

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs  

**Resources**  
- [เอกสารประกอบ](https://docs.groupdocs.com/watermark/java/)  
- [อ้างอิง API](https://reference.groupdocs.com/watermark/java)  
- [ดาวน์โหลด](https://releases.groupdocs.com/watermark/java/)  
- [ที่เก็บ GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/watermark/10)  
- [การรับใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)