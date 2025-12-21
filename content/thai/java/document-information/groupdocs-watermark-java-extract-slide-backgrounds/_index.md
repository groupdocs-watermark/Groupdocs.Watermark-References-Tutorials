---
date: '2025-12-21'
description: เรียนรู้วิธีดึงพื้นหลังจากสไลด์ PowerPoint ด้วย GroupDocs.Watermark สำหรับ
  Java รวมถึงขนาดภาพและขนาดไฟล์
keywords:
- extract slide background information Java
- GroupDocs.Watermark PowerPoint
- slide background details Java
title: วิธีแยกพื้นหลังจากสไลด์โดยใช้ GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# วิธีการดึงพื้นหลังจากสไลด์โดยใช้ GroupDocs.Watermark สำหรับ Java

การดึงข้อมูลพื้นหลังของสไลด์เป็นความต้องการทั่วไปเมื่อคุณต้องการวิเคราะห์ ปรับแต่ง หรือบันทึกเอกสารการนำเสนอ PowerPoint ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีการดึงพื้นหลัง** รายละเอียดเช่น ขนาดภาพ, ขนาดไฟล์, และอื่น ๆ โดยใช้ GroupDocs.Watermark สำหรับ Java เราจะอธิบายขั้นตอนการตั้งค่าเต็มรูปแบบ การเขียนโค้ด และเคล็ดลับปฏิบัติ เพื่อให้คุณเริ่มใช้ความสามารถนี้ได้ทันที.

## คำตอบเร็ว
- **“extract background” หมายถึงอะไร?** หมายถึงการดึงเมตาดาต้า (ขนาด, มิติ, ไบต์) ของภาพพื้นหลังของสไลด์  
- **ต้องใช้ไลบรารีอะไร?** GroupDocs.Watermark for Java (เวอร์ชัน 24.11 หรือใหม่กว่า).  
- **ต้องมีลิขสิทธิ์หรือไม่?** จำเป็นต้องมีลิขสิทธิ์ชั่วคราวหรือเต็มสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **สามารถประมวลผลการนำเสนอขนาดใหญ่ได้หรือไม่?** ได้—เพียงปิด `Watermarker` อย่างรวดเร็วและจัดการหน่วยความจำอย่างมีประสิทธิภาพ.  
- **ใช้ภาษาโปรแกรมอะไร?** Java, พร้อม Maven สำหรับการจัดการ dependencies.  

## “how to extract background” หมายถึงอะไรในบริบทของ PowerPoint?
เมื่อสไลด์ใช้ภาพเป็นพื้นหลัง ภาพนั้นจะถูกเก็บเป็นทรัพยากรไบนารีภายในไฟล์ .pptx การดึงพื้นหลังหมายถึงการเข้าถึงข้อมูลไบนารีนั้น อ่านความกว้าง, ความสูง, และขนาดไฟล์ และอาจบันทึกหรือวิเคราะห์ต่อไป

## ทำไมต้องดึงข้อมูลพื้นหลังด้วย GroupDocs.Watermark?
- **Automation:** ตรวจสอบหลายสิบการนำเสนออย่างรวดเร็วเพื่อให้แน่ใจว่าพื้นหลังสอดคล้องกับแบรนด์.  
- **Analytics:** รวบรวมสถิติขนาดภาพทั่วทั้งชุดสไลด์.  
- **Integration:** ส่งเมตาดาต้าพื้นหลังไปยัง CMS หรือระบบรายงานโดยไม่ต้องตรวจสอบด้วยตนเอง.  

## ข้อกำหนดเบื้องต้น
- **Java 17+** (หรือ JDK ล่าสุด) พร้อมติดตั้ง Maven.  
- **GroupDocs.Watermark for Java** เวอร์ชัน 24.11 หรือใหม่กว่า.  
- **ลิขสิทธิ์ชั่วคราวหรือเต็ม** เพื่อเปิดใช้งานคุณสมบัติทั้งหมด.  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การกำหนดค่า Maven
เพิ่มรีโพซิทอรีของ GroupDocs และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

### การรับลิขสิทธิ์
รับลิขสิทธิ์ชั่วคราวหรือเต็มได้ที่ [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license/).

### การเริ่มต้นและตั้งค่าเบื้องต้น
นี่คือตัวอย่างโค้ดขนาดเล็กที่สร้างอินสแตนซ์ `Watermarker` สำหรับไฟล์ PowerPoint:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## คู่มือการดำเนินการ – วิธีดึงข้อมูลพื้นหลัง

### ขั้นตอนที่ 1: สร้าง Load Options
สร้างอ็อบเจกต์ `PresentationLoadOptions` เพื่อระบุการตั้งค่าการโหลดที่ต้องการ:

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### ขั้นตอนที่ 2: เปิดเอกสาร PowerPoint
ใช้คลาส `Watermarker` เพื่อเปิดไฟล์ PowerPoint ของคุณ:

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### ขั้นตอนที่ 3: เข้าถึงเนื้อหาสไลด์
ดึงเนื้อหาการนำเสนอโดยใช้ `PresentationContent`:

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### ขั้นตอนที่ 4: วนลูปสไลด์และ **java extract image dimensions**
วนลูปผ่านแต่ละสไลด์ ตรวจสอบว่ามีภาพพื้นหลังหรือไม่ แล้วดึงความกว้าง, ความสูง, และขนาดเป็นไบต์ของภาพ:

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### ขั้นตอนที่ 5: ปิด Watermarker
สุดท้าย ปิด `Watermarker` เพื่อปล่อยทรัพยากร:

```java
watermarker.close();
```

## ปัญหาที่พบบ่อยและวิธีแก้
- **File not found:** ตรวจสอบเส้นทางไฟล์อีกครั้งและให้แน่ใจว่าแอปพลิเคชันมีสิทธิ์อ่าน.  
- **No background image returned:** บางสไลด์ใช้สีทึบหรือไล่สี; จะได้ผลเฉพาะสไลด์ที่ใช้ภาพเป็นพื้นหลัง.  
- **Memory spikes on large decks:** ประมวลผลสไลด์เป็นชุดและเรียก `watermarker.close()` เสมอเมื่อทำเสร็จ.  

## การประยุกต์ใช้งานจริง
1. **Custom Slide Design:** แทนที่หรือปรับขนาดภาพพื้นหลังโดยอัตโนมัติเพื่อให้สอดคล้องกับสไตล์องค์กรใหม่.  
2. **Data Analysis:** สร้างรายงานขนาดเฉลี่ยของภาพพื้นหลังในคลังการนำเสนอ.  
3. **CMS Integration:** ซิงค์เมตาดาต้าพื้นหลังกับระบบจัดการเนื้อหาเพื่อให้ค้นหาได้.  
4. **Audit & Compliance:** ตรวจสอบว่าพื้นหลังของทุกสไลด์สอดคล้องกับแนวทางแบรนด์ก่อนเผยแพร่.  

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Resource Management:** ปิดอินสแตนซ์ `Watermarker` เสมอเพื่อปล่อยทรัพยากรเนทีฟ.  
- **Large Files:** สำหรับชุดสไลด์ที่มีหลายร้อยสไลด์ ควรพิจารณา stream เนื้อหา หรือประมวลผลเป็นส่วนย่อย.  
- **Profiling:** ใช้เครื่องมือ profiling ของ Java (เช่น VisualVM) เพื่อตรวจหาจุดคอขวดในลูปการดึงข้อมูล.  

## สรุป
คุณมีคู่มือครบถ้วนและพร้อมใช้งานในสภาพแวดล้อมการผลิตเกี่ยวกับ **วิธีดึงข้อมูลพื้นหลัง** จากสไลด์ PowerPoint โดยใช้ GroupDocs.Watermark สำหรับ Java แล้ว ด้วยการทำตามขั้นตอนข้างต้น คุณสามารถดึงขนาดภาพ, ขนาดไฟล์, และเมตาดาต้าที่เป็นประโยชน์อื่น ๆ ทำให้คุณสามารถสร้างการตรวจสอบการออกแบบอัตโนมัติ, ระบบวิเคราะห์ข้อมูล, และอื่น ๆ ได้

**ขั้นตอนต่อไป**
- ทดลองใช้ `PresentationLoadOptions` ต่าง ๆ (เช่น โหลดเฉพาะสไลด์ที่ต้องการ).  
- สำรวจคุณลักษณะอื่นของ GroupDocs.Watermark เช่น การตรวจจับหรือการลบลายน้ำ.  
- ผสานข้อมูลที่ดึงได้เข้ากับระบบรายงานหรือ pipeline CI/CD ของคุณ.  

## คำถามที่พบบ่อย

**Q: เวอร์ชันขั้นต่ำของ GroupDocs.Watermark ที่ต้องการคืออะไร?**  
A: ต้องใช้เวอร์ชัน 24.11 หรือใหม่กว่าเพื่อเข้าถึง API `PresentationContent` ที่ใช้ในบทแนะนำนี้.

**Q: ฉันสามารถดึงภาพพื้นหลังจากการนำเสนอที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ได้ ให้กำหนดรหัสผ่านผ่าน `PresentationLoadOptions.setPassword("yourPassword")` ก่อนเปิดไฟล์.

**Q: ไลบรารีนี้รองรับรูปแบบการนำเสนออื่น ๆ (เช่น .key, .otp) หรือไม่?**  
A: GroupDocs.Watermark รองรับหลัก ๆ คือ .pptx และ .ppt. สำหรับรูปแบบอื่น ๆ คุณต้องแปลงเป็นรูปแบบที่รองรับก่อน.

**Q: ฉันจะหาเอกสารรายละเอียดเพิ่มเติมได้จากที่ไหน?**  
A: เยี่ยมชม [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/) อย่างเป็นทางการสำหรับคู่มือและอ้างอิง API อย่างละเอียด.

**Q: มีวิธีบันทึกภาพพื้นหลังที่ดึงได้ลงดิสก์หรือไม่?**  
A: มี—ใช้ `slide.getImageFillFormat().getBackgroundImage().save("output.png")` หลังจากดึงอ็อบเจกต์ภาพแล้ว.

---

**อัปเดตล่าสุด:** 2025-12-21  
**ทดสอบด้วย:** GroupDocs.Watermark 24.11  
**ผู้เขียน:** GroupDocs  

**แหล่งข้อมูล**  
- **Documentation:** [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference:** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **Download:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **GitHub Repository:** [GroupDocs GitHub Page](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Support Forum:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/10)