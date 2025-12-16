---
date: '2025-12-16'
description: เรียนรู้วิธีแสดงตัวอย่างเอกสารด้วย GroupDocs.Watermark สำหรับ Java และสร้างภาพย่อได้อย่างง่ายดายด้วยการผสานรวม
  Maven GroupDocs Watermark.
keywords:
- GroupDocs Watermark Java
- generate document previews
- Java watermarking library
title: 'วิธีดูตัวอย่างเอกสารด้วย GroupDocs.Watermark ใน Java: คู่มือขั้นสูง'
type: docs
url: /th/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# วิธีดูตัวอย่างเอกสารด้วย GroupDocs.Watermark ใน Java: คู่มือขั้นสูง

## บทนำ

ในคู่มือนี้ คุณจะได้เรียนรู้ **วิธีดูตัวอย่างเอกสาร** อย่างมีประสิทธิภาพโดยใช้ไลบรารี GroupDocs.Watermark สำหรับ Java การสร้างตัวอย่างเอกสารเป็นฟีเจอร์สำคัญสำหรับแอปพลิเคชันที่จัดการไฟล์จำนวนมาก ช่วยให้ผู้ใช้สามารถมองเนื้อหาโดยไม่ต้องเปิดเอกสารทั้งหมด ด้วยการทำตามขั้นตอนด้านล่าง คุณจะได้เห็นวิธี **java generate thumbnail** รูปภาพและการรวมไลบรารีผ่าน **maven groupdocs watermark** เริ่มต้นโดยการเตรียมสภาพแวดล้อมการพัฒนาของคุณ

## คำตอบอย่างรวดเร็ว
- **What is the primary purpose?** สร้างตัวอย่างหน้า‑ต่อ​หน้าแบบเบา (thumbnail) ของเอกสารที่รองรับทั้งหมด.  
- **Which library is required?** GroupDocs.Watermark for Java (เวอร์ชัน 24.11).  
- **How do I add the library?** ใช้สแนปเป็ท Maven ที่ให้ไว้ในส่วนการตั้งค่า.  
- **Can I generate previews for all pages?** ใช่ – API จะสตรีมแต่ละหน้าเป็นไฟล์รูปภาพ.  
- **Do I need a license?** รุ่นทดลองใช้ได้สำหรับการทดสอบพื้นฐาน; จำเป็นต้องมีไลเซนส์เต็มสำหรับการใช้งานในโปรดักชัน.  

## การสร้างตัวอย่างเอกสาร (Document Preview Generation) คืออะไร?

การสร้างตัวอย่างเอกสารจะแปลงแต่ละหน้าของไฟล์ต้นฉบับ (PDF, DOCX, VDX ฯลฯ) เป็นรูปแบบภาพเช่น PNG ตัวอย่างภาพเหล่านี้ทำหน้าที่เป็น thumbnail ที่สามารถแสดงในตัวจัดการไฟล์, พอร์ทัลเว็บ, หรือแอปมือถือ, ช่วยปรับประสบการณ์ผู้ใช้และลดเวลาโหลดอย่างมาก.

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?

- **Speed & Scalability** – โค้ดเนทีฟที่ปรับแต่งแล้วจัดการเอกสารขนาดใหญ่ได้อย่างรวดเร็ว.  
- **Broad Format Support** – รองรับไฟล์มากกว่า 100 ประเภทโดยไม่ต้องตั้งค่าเพิ่มเติม.  
- **Built‑in Watermarking** – คุณสามารถเพิ่มลายน้ำขณะสร้างตัวอย่าง เพื่อปกป้องทรัพย์สินของคุณ.  
- **Simple API** – ต้องใช้โค้ดเพียงเล็กน้อยเพื่อสร้าง thumbnail คุณภาพสูง.

## ข้อกำหนดเบื้องต้น

1. **Java Development Kit (JDK)** – ติดตั้ง JDK 8 หรือใหม่กว่า  
2. **IDE** – IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไขใด ๆ ที่คุณชอบ  
3. **Maven** – สำหรับการจัดการ dependencies (ดูการตั้งค่า Maven ด้านล่าง)  
4. **Basic Java knowledge** – ความคุ้นเคยกับการทำงานไฟล์ I/O และการเขียนโปรแกรมเชิงวัตถุ  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

เพื่อเริ่มใช้ GroupDocs.Watermark ในโปรเจกต์ของคุณ ให้เพิ่มเป็น dependency ของ Maven:

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

หรือคุณสามารถดาวน์โหลด JAR เวอร์ชันล่าสุดโดยตรงจากหน้าปล่อยอย่างเป็นทางการ:

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

### การรับไลเซนส์

- **Free Trial** – ทดสอบไลบรารีด้วยฟังก์ชันจำกัด.  
- **Temporary License** – รับคีย์ระยะสั้นสำหรับการประเมินฟีเจอร์เต็ม.  
- **Full License** – ซื้อเพื่อใช้งานไม่จำกัดและรับการสนับสนุนระดับพรีเมียม.  

## คู่มือการใช้งาน

### เริ่มต้น Watermarker

#### ภาพรวม
ขั้นตอนแรกคือการสร้างอินสแตนซ์ `Watermarker` ที่ชี้ไปยังเอกสารต้นฉบับ.

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

*Key point:* แทนที่ `YOUR_DOCUMENT_DIRECTORY/diagram.vdx` ด้วยพาธจริงของไฟล์ที่คุณต้องการดูตัวอย่าง.

### สร้าง Page Stream สำหรับการสร้างตัวอย่าง

#### ภาพรวม
ตัวสร้าง stream แบบกำหนดเองบอก API ว่าจะเขียนภาพตัวอย่างของแต่ละหน้าไปที่ไหน.

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

`fileNameTemplate` ใช้ placeholder (`%s`) ที่ API จะแทนที่ด้วยหมายเลขหน้าปัจจุบัน ทำให้ได้ไฟล์เช่น `page1.png`, `page2.png` เป็นต้น.

### ปล่อย Page Stream

#### ภาพรวม
หลังจากเขียนภาพตัวอย่างเสร็จแล้ว จำเป็นต้องปิด stream เพื่อปลดปล่อยทรัพยากรของระบบ.

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

การปล่อย stream อย่างถูกต้องช่วยป้องกันการรั่วไหลของหน่วยความจำ โดยเฉพาะเมื่อประมวลผลเอกสารจำนวนมากเป็นชุด.

### สร้างตัวอย่างเอกสาร

#### ภาพรวม
เมื่อมี `Watermarker`, ตัวสร้าง stream, และตัวจัดการการปล่อยพร้อมใช้งาน คุณสามารถสร้างตัวอย่างสำหรับทุกหน้าได้.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

*คำอธิบายของอ็อบเจ็กต์สำคัญ:*
- `createPageStream` – กำหนดตำแหน่งที่บันทึกไฟล์ PNG แต่ละไฟล์.  
- `releasePageStream` – ทำให้แน่ใจว่าไฟล์แฮนด์เดิลถูกปิดหลังการเขียน.  
- `previewOptions` – รวมตัวจัดการทั้งสองสำหรับการเรียก `generatePreview`.  

## การประยุกต์ใช้งานจริง

การสร้างตัวอย่างเอกสารมีประโยชน์ในหลายสถานการณ์จริง:
1. **PDF Viewer Apps** – แสดงแถบ thumbnail โดยไม่ต้องโหลด PDF เต็มไฟล์.  
2. **Content Management Systems (CMS)** – ให้ผู้แก้ไขเรียกดูเอกสารได้อย่างรวดเร็ว.  
3. **Cloud Storage Services** – ให้ thumbnail ภาพสำหรับไฟล์ที่จัดเก็บ ช่วยปรับปรุงการนำทาง.  

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **Memory Management** – ใช้รูปแบบการปล่อย stream ที่แสดงด้านบนเพื่อรักษาการใช้หน่วยความจำน้อย.  
- **I/O Optimization** – Buffered stream สามารถลดความหน่วงของดิสก์เมื่อจัดการหลายพันหน้า.  
- **Parallel Processing** – สำหรับการดำเนินการเป็นกลุ่ม พิจารณาประมวลผลหลายเอกสารพร้อมกันโดยใช้ `ExecutorService` ของ Java.  

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| ไม่มีไฟล์ตัวอย่างที่สร้างขึ้น | พาธไดเรกทอรีเอาต์พุตไม่ถูกต้องหรือไม่มีสิทธิ์เขียน | ตรวจสอบว่า `YOUR_OUTPUT_DIRECTORY` มีอยู่และสามารถเขียนได้ |
| ข้อผิดพลาด Out‑of‑memory บน PDF ขนาดใหญ่ | Stream ไม่ได้ถูกปล่อยอย่างทันท่วงที | ตรวจสอบว่า `FeatureReleasePageStream` ถูกนำไปใช้อย่างถูกต้อง |
| รูปแบบไฟล์ที่ไม่รองรับ | ประเภทเอกสารไม่อยู่ในขอบเขตที่ GroupDocs.Watermark รองรับ | ตรวจสอบรายการรูปแบบที่ไลบรารีรองรับ; แปลงเป็นประเภทที่รองรับหากจำเป็น |

## คำถามที่พบบ่อย

**Q: ฉันสามารถสร้างตัวอย่างสำหรับเอกสารที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ใช่. โหลดเอกสารพร้อมรหัสผ่านที่เหมาะสมโดยใช้คอนสตรัคเตอร์ของ `Watermarker` ที่รับพารามิเตอร์รหัสผ่าน, จากนั้นดำเนินการสร้างตัวอย่างตามที่แสดง.

**Q: ไลบรารีรองรับรูปแบบภาพอื่นนอกจาก PNG หรือไม่?**  
A: API ตัวอย่างส่งออกเป็น PNG โดยค่าเริ่มต้น, แต่คุณสามารถแปลง stream ที่ได้เป็น JPEG หรือ BMP โดยใช้ไลบรารีภาพมาตรฐานของ Java หากต้องการ.

**Q: ฉันสามารถสร้างตัวอย่างได้กี่หน้าภายในการรันเดียว?**  
A: ไม่มีขีดจำกัดที่แน่นอน; อย่างไรก็ตาม การประมวลผลเอกสารขนาดใหญ่มากอาจได้ประโยชน์จากการทำเป็นชุดหรือเพิ่มขนาด heap ของ JVM.

**Q: จำเป็นต้องมีไลเซนส์สำหรับการสร้างตัวอย่างหรือไม่?**  
A: ไลเซนส์ทดลองใช้ได้สำหรับการประเมิน, แต่ต้องมีไลเซนส์เต็มสำหรับการใช้งานในโปรดักชันเพื่อเอาลายน้ำออกและเปิดใช้งานฟีเจอร์ทั้งหมด.

**Q: ฉันสามารถปรับความละเอียดของภาพตัวอย่างได้หรือไม่?**  
A: ใช่. `PreviewOptions` มีคุณสมบัติเช่น `setResolution` ที่คุณสามารถกำหนดค่าการตั้งค่า DPI ก่อนเรียก `generatePreview`.

## สรุป

ตอนนี้คุณมีเวิร์กโฟลว์ที่ครบถ้วนและพร้อมใช้งานในโปรดักชันสำหรับ **วิธีดูตัวอย่างเอกสาร** ด้วย GroupDocs.Watermark ใน Java โดยการเริ่มต้น `Watermarker`, จัดการ page stream, และปล่อยทรัพยากรอย่างเหมาะสม คุณสามารถสร้าง thumbnail คุณภาพสูงในปริมาณมาก ใช้เทคนิคเหล่านี้เพื่อปรับปรุงประสบการณ์ผู้ใช้ในแอปพลิเคชันที่จัดการเอกสารจำนวนมาก.

---

**อัปเดตล่าสุด:** 2025-12-16  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs