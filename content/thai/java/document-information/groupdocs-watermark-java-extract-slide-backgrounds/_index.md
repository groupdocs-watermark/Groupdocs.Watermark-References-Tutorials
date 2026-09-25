---
date: '2026-09-11'
description: เรียนรู้วิธีดึงพื้นหลังสไลด์ Java และอ่านขนาดสไลด์ PowerPoint ด้วย GroupDocs.Watermark
  สำหรับ Java. รับขนาดภาพ, ขนาดไฟล์, และเมตาดาต้าในไม่กี่นาที.
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: ดึงพื้นหลังสไลด์ Java และอ่านขนาดสไลด์ PowerPoint ด้วย GroupDocs.Watermark
  สำหรับ Java. คู่มือโดยละเอียดพร้อมการตั้งค่า, โค้ด, และการแก้ไขปัญหา.
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: ดึงพื้นหลังสไลด์ Java ด้วย GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: วิธีดึงพื้นหลังสไลด์ด้วย Java
type: docs
url: /th/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# วิธีการดึงพื้นหลังสไลด์ด้วย Java

## บทนำ

การดึงพื้นหลังสไลด์ด้วย Java เป็นความต้องการทั่วไปเมื่อคุณต้องการวิเคราะห์, ใช้ซ้ำ, หรือบันทึกข้อมูลสินทรัพย์ภาพภายในไฟล์ PowerPoint ด้วย GroupDocs.Watermark for Java คุณสามารถดึงข้อมูลขนาดภาพ, ขนาดไฟล์, และเมตาดาต้าอื่น ๆ ได้โดยโปรแกรมโดยไม่ต้องเปิดงานนำเสนอใน PowerPoint บทเรียนนี้จะพาคุณผ่านขั้นตอนการทำงานทั้งหมด — ตั้งแต่การตั้งค่าสภาพแวดล้อมจนถึงการดึงและตีความรายละเอียดพื้นหลัง — เพื่อให้คุณสามารถผสานความสามารถนี้เข้าไปในสายงานอัตโนมัติที่ใช้ Java ได้

### คำตอบอย่างรวดเร็ว
- **ไลบรารีที่จัดการการดึงพื้นหลังสไลด์คืออะไร?** GroupDocs.Watermark for Java.  
- **เมธอดใดที่คืนค่าขนาดภาพ?** `getBackground().getImageInfo().getWidth()` และ `getHeight()`.  
- **ฉันสามารถรับขนาดไฟล์ของภาพพื้นหลังได้หรือไม่?** ได้, ผ่าน `getBackground().getImageInfo().getSize()`.  
- **ฉันต้องการไลเซนส์สำหรับฟีเจอร์นี้หรือไม่?** ไลเซนส์ชั่วคราวหรือเต็มจะเปิดใช้งานฟังก์ชันทั้งหมด; โหมดทดลองทำงานโดยมีข้อจำกัด.  
- **Maven รองรับหรือไม่?** แน่นอน — เพิ่ม dependency ของ GroupDocs.Watermark ไปยัง `pom.xml`.

## อะไรคือการดึงพื้นหลังสไลด์ด้วย Java?

การดึงพื้นหลังสไลด์ด้วย Java หมายถึงกระบวนการอ่านพื้นหลังภาพของแต่ละสไลด์ในงานนำเสนอ PowerPoint โดยใช้โค้ด Java อย่างโปรแกรมเมติก การดำเนินการนี้ให้เมตาดาต้าเช่น ความกว้าง, ความสูง, และขนาดไฟล์ของภาพ ทำให้สามารถประมวลผลต่อได้ เช่น การตรวจสอบการใช้แบรนด์หรือการนำสินทรัพย์กลับมาใช้ใหม่

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับงานนี้?

GroupDocs.Watermark รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 30 ประเภท**, ประมวลผลงานนำเสนอที่มีสูงสุด **500 สไลด์** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ, และมี API เฉพาะสำหรับการเข้าถึงพื้นหลังสไลด์ ความสามารถที่วัดได้เหล่านี้ทำให้เป็นตัวเลือกที่เชื่อถือได้สำหรับการอัตโนมัติระดับองค์กร

## ข้อกำหนดเบื้องต้น
- **Java 11+** ติดตั้งบนเครื่องพัฒนาของคุณ.  
- **Maven** สำหรับการจัดการ dependency.  
- **GroupDocs.Watermark 24.11** (หรือใหม่กว่า) – ไลบรารีนี้มีคลาส `PresentationLoadOptions` และ `PresentationContent` ที่ใช้ในคู่มือนี้.  
- ไลเซนส์ **ที่ถูกต้อง** (ชั่วคราวหรือเต็ม) เพื่อเปิดใช้งานฟีเจอร์ทั้งหมด.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การกำหนดค่า Maven
เพิ่ม dependency ของ GroupDocs.Watermark ไปยังไฟล์ `pom.xml` ของคุณ:

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
หากคุณต้องการติดตั้งด้วยตนเอง, ดาวน์โหลด JAR ล่าสุดจากหน้ารีลีสอย่างเป็นทางการ: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับไลเซนส์
ไลเซนส์ชั่วคราวช่วยให้คุณประเมิน API, ในขณะที่ไลเซนส์เต็มจะลบข้อจำกัดของโหมดทดลองทั้งหมด. รับไลเซนส์ของคุณได้ที่พอร์ทัลการให้ไลเซนส์: [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license/).

#### การเริ่มต้นและตั้งค่าพื้นฐาน
ขั้นตอนแรกคือการสร้างอินสแตนซ์ `Watermarker` ที่ชี้ไปยังไฟล์ PowerPoint ของคุณ:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## วิธีการดึงพื้นหลังสไลด์ด้วย Java?
กระบวนการเริ่มต้นด้วยการโหลดไฟล์ PowerPoint โดยใช้อินสแตนซ์ Watermarker, จากนั้นสร้าง load options ที่เหมาะสม หลังจากเปิดเอกสารแล้ว, คุณสามารถเข้าถึงเนื้อหาของแต่ละสไลด์, ดึงภาพพื้นหลัง, และสกัดเมตาดาต้าเช่น ขนาดและขนาดไฟล์. สุดท้าย, ปิด Watermarker เพื่อปล่อยทรัพยากร. ขั้นตอนต่อไปนี้อธิบายลำดับที่ต้องทำอย่างละเอียด, และตำแหน่งโค้ด placeholder แสดงว่าตำแหน่งที่สคริปต์ของคุณควรอยู่.

### ขั้นตอนที่ 1: สร้าง load options
`PresentationLoadOptions` กำหนดค่าการโหลดเช่น การจัดการรหัสผ่านและการใช้หน่วยความจำ.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### ขั้นตอนที่ 2: เปิดไฟล์ PowerPoint
สร้างอินสแตนซ์ `Watermarker` ด้วยพาธไปยังไฟล์ `.pptx` ของคุณและ load options ที่สร้างไว้ก่อนหน้า.

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### ขั้นตอนที่ 3: เข้าถึงเนื้อหาสไลด์
`PresentationContent` เป็นจุดเริ่มต้นสำหรับการดึงออบเจ็กต์ระดับสไลด์, รวมถึงภาพพื้นหลัง.

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### ขั้นตอนที่ 4: วนลูปสไลด์และอ่านรายละเอียดพื้นหลัง
Slide แทนสไลด์แต่ละอันภายในงานนำเสนอและให้การเข้าถึงองค์ประกอบภาพของมัน.  
สำหรับแต่ละออบเจ็กต์ `Slide`, เรียก `getBackground()` เพื่อรับภาพ, จากนั้นอ่านขนาดและขนาดไฟล์.

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
ควรปิดอินสแตนซ์ `Watermarker` เสมอเพื่อปล่อยทรัพยากรเนทีฟและหลีกเลี่ยงการรั่วของหน่วยความจำ.

```java
watermarker.close();
```

## วิธีอ่านขนาดสไลด์ PowerPoint ด้วย GroupDocs.Watermark?
API เปิดเผยความกว้างและความสูงผ่านอ็อบเจ็กต์ `ImageInfo` ที่แนบกับพื้นหลังของสไลด์. ดึงค่าด้วย `getWidth()` และ `getHeight()`, ซึ่งคืนค่าเป็นพิกเซลที่คุณสามารถใช้ในการคำนวณการจัดวางหรือการตรวจสอบตามแนวทางแบรนด์.

## ปัญหาทั่วไปและการแก้ไขข้อผิดพลาด
- **ไฟล์ไม่พบ** – ตรวจสอบว่าพาธไฟล์เป็นแบบ absolute หรือสัมพันธ์อย่างถูกต้องกับโฟลเดอร์รากของโปรเจค.  
- **รูปแบบไม่รองรับ** – GroupDocs.Watermark รองรับ PPTX, PPT, และ ODP; ไฟล์ PPT แบบไบนารีเก่าอาจต้องแปลงก่อน.  
- **ไลเซนส์ไม่ได้ถูกนำไปใช้** – ตรวจสอบว่าคุณเรียก `License.setLicense("path/to/license.file")` ก่อนการใช้ API ใด ๆ.

## การประยุกต์ใช้ในทางปฏิบัติ
1. **การตรวจสอบการใช้แบรนด์อัตโนมัติ** – สแกนพื้นหลังสไลด์เพื่อยืนยันว่าตรงกับพาเลตสีขององค์กรหรือขนาดโลโก้.  
2. **การสำรวจสินทรัพย์** – สร้างแคตตาล็อกของภาพพื้นหลังในคลังเอกสารเพื่อใช้ซ้ำในสินทรัพย์การตลาด.  
3. **การย้ายเนื้อหา** – ดึงภาพพื้นหลัง, เก็บไว้ในระบบจัดการสินทรัพย์ดิจิทัล, และนำกลับไปใช้ในงานนำเสนอใหม่โดยอัตโนมัติ.  
4. **การตรวจสอบประสิทธิภาพ** – บันทึกสถิติขนาดภาพเพื่อค้นหาสินทรัพย์ที่ใหญ่ผิดปกติซึ่งอาจทำให้การแสดงสไลด์ช้าลง.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การทำความสะอาดทรัพยากร** – การปิด `Watermarker` อย่างรวดเร็วจะปล่อยหน่วยความจำเนทีฟ, ซึ่งสำคัญเมื่อประมวลผลเด็คขนาดใหญ่.  
- **รอยเท้าหน่วยความจำ** – ไลบรารีสตรีมข้อมูลสไลด์; คุณสามารถลดการใช้ได้โดยประมวลผลสไลด์ทีละหนึ่งแทนการโหลดงานนำเสนอทั้งหมด.  
- **เคล็ดลับการประมวลผลเป็นชุด** – เมื่อจัดการหลายสิบไฟล์, ใช้ `License` อินสแตนซ์เดียวและสร้าง `Watermarker` ใหม่ต่อไฟล์เพื่อรักษา heap ของ JVM ให้เสถียร.

## สรุป
ตอนนี้คุณมีคู่มือที่ครบถ้วนและพร้อมใช้งานในสภาพการผลิตสำหรับการดึงพื้นหลังสไลด์ด้วย Java ด้วย GroupDocs.Watermark. โดยทำตามขั้นตอนข้างต้นคุณสามารถดึงขนาดภาพ, ขนาดไฟล์, และเมตาดาต้าอื่น ๆ, แล้วนำข้อมูลนั้นไปใช้ในการตรวจสอบแบรนด์, การจัดการสินทรัพย์, หรือเวิร์กโฟลว์ที่คุณออกแบบ

**ขั้นตอนต่อไป**
- ทดลองใช้ `PresentationLoadOptions` ต่าง ๆ (เช่น ไฟล์ที่มีรหัสผ่าน).  
- สำรวจ API การใส่น้ำหนักเพื่อเพิ่มหรือแทนที่พื้นหลังโดยอัตโนมัติ.  
- ผสานตรรกะการดึงนี้กับบริการ REST เพื่อเปิดเผย endpoint ของเมตาเดตาสไลด์.

## คำถามที่พบบ่อย

**Q: เวอร์ชัน Java ขั้นต่ำที่ต้องการคืออะไร?**  
A: จำเป็นต้องใช้ Java 11 หรือใหม่กว่า; เวอร์ชันก่อนหน้าขาดคุณลักษณะภาษาที่จำเป็นสำหรับไลบรารี.

**Q: ฉันสามารถดึงพื้นหลังจากงานนำเสนอที่มีรหัสผ่านได้หรือไม่?**  
A: ได้ — ตั้งรหัสผ่านใน `PresentationLoadOptions` ก่อนเปิดไฟล์.

**Q: โหมดทดลองจำกัดจำนวนสไลด์ที่ฉันสามารถประมวลผลได้หรือไม่?**  
A: โหมดทดลองใส่น้ำหนักบนไฟล์ผลลัพธ์แต่ไม่จำกัดจำนวนสไลด์สำหรับการสกัดเมตาดาต้า.

**Q: สามารถบันทึกภาพพื้นหลังที่ดึงออกมาไปยังดิสก์ได้หรือไม่?**  
A: แน่นอน — ใช้ `ImageInfo.save("output.png")` หลังจากดึงอ็อบเจ็กต์ `ImageInfo`.

**Q: ฉันสามารถส่งออกภาพที่ดึงออกมาเป็นรูปแบบใดได้บ้าง?**  
A: API รองรับ PNG, JPEG, BMP, และ GIF สำหรับการส่งออกภาพพื้นหลัง.

## แหล่งข้อมูล

- **เอกสาร:** [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/)  
- **เอกสาร:** [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **อ้างอิง API:** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **ดาวน์โหลด:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **ที่เก็บ GitHub:** [GroupDocs GitHub Page](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **ฟอรั่มสนับสนุน:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/10)

---

**อัปเดตล่าสุด:** 2026-09-11  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [วิธีการดึงขนาดสไลด์ PowerPoint ด้วย GroupDocs.Watermark Java API](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)
- [ลบพื้นหลังสไลด์ PowerPoint ใน Java ด้วยไลบรารี GroupDocs.Watermark](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)
- [วิธีดึงข้อมูลเอกสารโดยใช้ GroupDocs.Watermark for Java: คู่มือขั้นตอนต่อขั้นตอน](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)