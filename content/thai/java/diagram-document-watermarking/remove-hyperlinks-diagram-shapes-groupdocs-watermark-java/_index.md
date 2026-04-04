---
date: '2026-04-04'
description: เรียนรู้วิธีการลบลิงก์ออกจากรูปร่างแผนภาพด้วย GroupDocs.Watermark Java
  เพื่อให้มั่นใจในความปลอดภัยและความชัดเจนของเอกสาร
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: วิธีลบลิงก์ออกจากรูปทรงแผนภาพโดยใช้ GroupDocs.Watermark Java
type: docs
url: /th/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# วิธีลบลิงก์จากรูปร่างแผนภาพโดยใช้ GroupDocs.Watermark Java

การจัดการเอกสารดิจิทัลมักเกี่ยวข้องกับการแก้ไขแผนภาพ โดยเฉพาะเมื่อคุณต้องการ **how to strip links** เพื่อความปลอดภัยหรือความชัดเจน ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีง่าย ๆ แบบขั้นตอนต่อขั้นตอนในการลบไฮเปอร์ลิงก์ที่ไม่ต้องการออกจากรูปร่างแผนภาพโดยใช้ไลบรารี **GroupDocs.Watermark** สำหรับ Java ที่มีประสิทธิภาพ เมื่อเสร็จแล้วคุณจะได้แผนภาพที่สะอาด ปราศจากลิงก์ และปลอดภัยต่อการแชร์

## คำตอบด่วน
- **What does “how to strip links” mean?** หมายถึงการลบวัตถุ hyperlink ที่ฝังอยู่ในรูปร่างของแผนภาพ.  
- **Which library handles this?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **Do I need a license?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์ที่ถูกต้องสำหรับการใช้งานจริง.  
- **Can I process many files at once?** ใช่ – สามารถใส่โค้ดในลูปหรือทำงานแบบแบตช์.  
- **Is this approach language‑specific?** ตัวอย่างใช้ Java แต่แนวคิดเดียวกันสามารถใช้กับ API ของ .NET/Java อื่น ๆ ได้.

## “how to strip links” คืออะไรในการแก้ไขแผนภาพ
การลบลิงก์หมายถึงการค้นหาวัตถุ hyperlink ที่แนบอยู่กับรูปร่างภายในแผนภาพ (เช่น Visio *.vsdx) แล้วทำการลบออก ซึ่งจะกำจัด URL ภายนอกที่อาจเปิดเผยข้อมูลที่สำคัญหรือทำให้การนำเสนอขัดจังหวะ

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java
- **Precision** – การเข้าถึงวัตถุรูปร่างและคอลเลกชันของ hyperlink โดยตรง.  
- **Performance** – ปรับให้เหมาะกับแผนภาพขนาดใหญ่โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ.  
- **Cross‑format support** – ทำงานกับหลายรูปแบบของแผนภาพ (Visio, Draw.io, เป็นต้น).

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (หรือการรวม JAR ด้วยตนเอง).  
- Java JDK 8 หรือใหม่กว่า.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
### การตั้งค่า Maven
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
หากคุณไม่ต้องการใช้ Maven ให้ดาวน์โหลด JAR ล่าสุดจากเว็บไซต์อย่างเป็นทางการ:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### ขั้นตอนการรับไลเซนส์
- เริ่มต้นด้วยการดาวน์โหลดรุ่นทดลองฟรี.  
- สำหรับการใช้งานจริง ให้รับไลเซนส์ชั่วคราวหรือเต็มจากพอร์ทัลของ GroupDocs.

#### การเริ่มต้นและตั้งค่าเบื้องต้น
สร้างอินสแตนซ์ `Watermarker` ที่ชี้ไปยังโฟลเดอร์ที่บรรจุแผนภาพของคุณ:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## วิธีลบลิงก์จากรูปร่างแผนภาพ
ด้านล่างเป็นกระบวนการสั้น ๆ สี่ขั้นตอนที่แสดง **remove hyperlinks java** ทำงาน.

### ขั้นตอนที่ 1: โหลดไฟล์แผนภาพ
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*ทำไม?* การโหลดไฟล์ทำให้คุณสามารถเข้าถึงหน้า, รูปร่าง, และคอลเลกชันของ hyperlink ของไฟล์ได้แบบโปรแกรม

### ขั้นตอนที่ 2: เข้าถึงเนื้อหารูปร่าง
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*ทำไม?* คุณต้องการอ้างอิงถึงรูปร่างเฉพาะที่อาจมี hyperlink.

### ขั้นตอนที่ 3: วนลูปและลบ Hyperlink
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*ทำไม?* การวนลูปย้อนกลับช่วยป้องกันปัญหา index‑shift เมื่อทำการลบรายการจากคอลเลกชัน.

### ขั้นตอนที่ 4: บันทึกและปิด
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*ทำไม?* การบันทึกจะเขียนแผนภาพที่ทำความสะอาดแล้วลงดิสก์ และการปิดจะปล่อยตัวจัดการไฟล์เพื่อหลีกเลี่ยงการรั่วของหน่วยความจำ.

## การประยุกต์ใช้งานจริงของการลบลิงก์
1. **Security** – ลบ URL ภายนอกที่อาจนำไปสู่การฟิชชิ่งหรือการรั่วไหลของข้อมูล.  
2. **Compliance** – ทำให้แน่ใจว่าแผนภาพสอดคล้องกับนโยบายภายในก่อนการแจกจ่าย.  
3. **Presentation Cleanliness** – กำจัดพื้นที่ที่คลิกได้โดยไม่จำเป็นซึ่งทำให้ผู้ชมเสียสมาธิ.

## พิจารณาด้านประสิทธิภาพ
- **Loop Efficiency** – ใช้รูปแบบการวนลูปย้อนกลับตามที่แสดงข้างต้น.  
- **Resource Management** – แนะนำให้ใช้ `try‑with‑resources` หรือเรียก `close()` อย่างชัดเจน.  
- **Large Files** – ตรวจสอบการใช้ CPU/หน่วยความจำ; พิจารณาการประมวลผลหน้าเป็นชุด.

## ปัญหาที่พบบ่อยและวิธีแก้
- **No hyperlinks found** – ตรวจสอบว่าแผนภาพมีวัตถุ hyperlink จริงหรือไม่; บางรูปแบบอาจจัดเก็บต่างกัน.  
- **IndexOutOfBoundsException** – ควรวนลูปย้อนกลับเสมอเมื่อทำการลบรายการจากคอลเลกชัน.  
- **License errors** – ตรวจสอบว่าไฟล์ไลเซนส์ถูกวางอย่างถูกต้องหรือส่งผ่านไปยังคอนสตรัคเตอร์ของ `Watermarker`.

## คำถามที่พบบ่อย

**Q: How do I handle multiple shapes on multiple pages?**  
A: วนลูปผ่าน `content.getPages()` แล้วต่อด้วยคอลเลกชัน `getShapes()` ของแต่ละหน้า โดยใช้ตรรกะการลบเดียวกันกับทุกรูปร่าง.

**Q: Can I filter links by domain instead of a full URL?**  
A: ใช่ – เปลี่ยนการตรวจสอบ `contains` ให้มองหาสตริงโดเมน (เช่น `"example.com"`).

**Q: Is there a way to log which links were removed?**  
A: ภายในลูป ให้ดึงค่า `shape.getHyperlinks().get_Item(i).getAddress()` ก่อนทำการลบและบันทึกลงไฟล์บันทึก.

**Q: Does this work with PDF diagrams embedded in other documents?**  
A: GroupDocs.Watermark รองรับหลายรูปแบบ; ตรวจสอบให้แน่ใจว่าไฟล์ถูกระบุเป็นแผนภาพ (Visio, VDX, เป็นต้น).

**Q: What licensing is required for batch processing?**  
A: จำเป็นต้องมีไลเซนส์การผลิตเต็มรูปแบบสำหรับการดำเนินการแบบไม่ใช่ทดลองและปริมาณสูง.

## สรุป
คุณมีวิธีที่ครบถ้วนและพร้อมใช้งานในระดับการผลิตสำหรับ **how to strip links** จากรูปร่างแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java แล้ว นำวิธีนี้ไปรวมในกระบวนการประมวลผลเอกสารของคุณเพื่อเพิ่มความปลอดภัย, การปฏิบัติตามกฎระเบียบ, และคุณภาพภาพ.

### ขั้นตอนต่อไป
- สำรวจคุณลักษณะการจัดการอื่น ๆ เช่น การเพิ่มลายน้ำหรือการประทับข้อความ.  
- ผสานกระบวนการนี้กับบริการ file‑watcher เพื่อทำความสะอาดแผนภาพโดยอัตโนมัติเมื่ออัปโหลด.

---

**อัปเดตล่าสุด:** 2026-04-04  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs  

## แหล่งข้อมูล
- [เอกสารประกอบ](https://docs.groupdocs.com/watermark/java/)
- [อ้างอิง API](https://reference.groupdocs.com/watermark/java)
- [ดาวน์โหลด](https://releases.groupdocs.com/watermark/java/)
- [ที่เก็บ GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/watermark/10)
- [การรับไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)