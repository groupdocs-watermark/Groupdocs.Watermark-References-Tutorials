---
date: '2025-12-19'
description: เรียนรู้วิธีใช้ GroupDocs Watermark Maven เพื่อจัดการลายน้ำในไฟล์แผนภาพเช่น
  .vsdx ด้วย Java เพื่อเพิ่มความสมบูรณ์ของเอกสารและปกป้องทรัพย์สินทางปัญญา
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – จัดการลายน้ำแผนภาพด้วย Java
type: docs
url: /th/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – จัดการลายน้ำแผนภาพด้วย Java

การจัดการลายน้ำในเอกสารเป็นสิ่งสำคัญสำหรับการปกป้องทรัพย์สินทางปัญญาและการรักษาความสมบูรณ์ของเอกสาร **ในบทแนะนำนี้เราจะแสดงวิธีใช้ groupdocs watermark maven เพื่อโหลด ค้นหา และลบลายน้ำจากไฟล์แผนภาพเช่น `.vsdx` อย่างมีประสิทธิภาพ** ไม่ว่าคุณจะกำลังพัฒนาซอฟต์แวร์ระดับองค์กรหรืออัตโนมัติขั้นตอนการทำงานของเอกสาร การเชี่ยวชาญเทคนิคเหล่านี้จะทำให้คุณควบคุมการจัดการลายน้ำแผนภาพได้อย่างเต็มที่

## คำตอบอย่างรวดเร็ว
- **ต้องการไลบรารีอะไร?** GroupDocs.Watermark for Java (available via Maven).  
- **รูปแบบแผนภาพใดที่รองรับ?** `.vsdx`, `.vdx`, และรูปแบบ Visio อื่นๆ.  
- **ฉันสามารถค้นหาลายน้ำทั้งข้อความและรูปภาพได้หรือไม่?** ได้ – รวมเกณฑ์การค้นหาด้วย `or()`.  
- **ต้องการใบอนุญาตสำหรับการใช้งานจริงหรือไม่?** ต้องมีใบอนุญาต GroupDocs.Watermark ที่ถูกต้อง.  
- **ฉันจะรวมเข้ากับ Maven อย่างไร?** เพิ่ม repository และ dependency ตามที่แสดงด้านล่าง.

## groupdocs watermark maven คืออะไร?
`groupdocs watermark maven` หมายถึงการบูรณาการแบบ Maven ของไลบรารี GroupDocs.Watermark สำหรับ Java โดยการประกาศไลบรารีใน `pom.xml` ของคุณ Maven จะดึงไบนารีที่จำเป็นทั้งหมดโดยอัตโนมัติ ทำให้คุณมุ่งเน้นที่โค้ดที่โหลดแผนภาพ ค้นหาลายน้ำ และลบลายน้ำโดยโปรแกรม

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับการจัดการลายน้ำแผนภาพ?
- **API ครบถ้วน** – รองรับลายน้ำข้อความ, รูปภาพ, และรูปทรงในหลายประเภทของแผนภาพ.  
- **การลบที่แม่นยำ** – กำจัดลายน้ำโดยไม่ทำให้โครงสร้างแผนภาพต้นฉบับเสียหาย.  
- **ขยายได้** – เหมาะสำหรับการประมวลผลเป็นชุดของแผนภาพจำนวนมาก.  
- **เป็นมิตรกับ Maven** – การจัดการ dependency ง่าย ทำให้โครงการของคุณสะอาด.

## ข้อกำหนดเบื้องต้น
1. **Java Development Kit (JDK) 8+** – เพื่อให้เข้ากันได้กับไลบรารี.  
2. **IDE** – IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไขที่รองรับ Java ใดก็ได้.  
3. **GroupDocs.Watermark for Java** – เพิ่มผ่าน Maven (แนะนำ) หรือดาวน์โหลด JAR โดยตรง.  

### ไลบรารีและ Dependency ที่จำเป็น
#### การตั้งค่า Maven
Add the following configuration to your `pom.xml` file:

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

#### ดาวน์โหลดโดยตรง
Alternatively, download the latest version from [การปล่อย GroupDocs.Watermark สำหรับ Java](https://releases.groupdocs.com/watermark/java/).

### การรับใบอนุญาต
- **ทดลองใช้ฟรี:** ทดสอบไลบรารีด้วยใบอนุญาตทดลอง.  
- **ใบอนุญาตชั่วคราว:** ขอคีย์ระยะสั้นเพื่อการประเมิน.  
- **ซื้อ:** รับใบอนุญาตการใช้งานจริงสำหรับการใช้ไม่จำกัด.

## การใช้ groupdocs watermark maven เพื่อโหลดเอกสารแผนภาพ
การโหลดเอกสารแผนภาพเป็นขั้นตอนแรกก่อนการดำเนินการลายน้ำใดๆ ด้านล่างเป็นตัวอย่างขั้นต่ำที่สร้างอินสแตนซ์ `Watermarker` ด้วย `DiagramLoadOptions`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

- **พารามิเตอร์:**  
  - `inputFilePath` – เส้นทางไปยังไฟล์ `.vsdx` ของคุณ.  
  - `loadOptions` – ให้คุณควบคุมวิธีการแยกวิเคราะห์แผนภาพ (เช่น การป้องกันด้วยรหัสผ่าน).

## การค้นหาลายน้ำด้วย groupdocs watermark maven
### ลายน้ำข้อความ
To locate text‑based watermarks, define a `TextSearchCriteria` and query the first page of the diagram.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

- **เมธอดสำคัญ:**  
  - `TextSearchCriteria` – ระบุข้อความที่ต้องการค้นหาอย่างแม่นยำ.  
  - `PossibleWatermarkCollection` – เก็บผลลัพธ์ที่พบ.

### ลายน้ำรูปภาพ
If your diagram contains logo or picture watermarks, use `ImageDctHashSearchCriteria` to compare against a reference image.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

- **เมธอดสำคัญ:**  
  - `ImageDctHashSearchCriteria` – สร้างแฮชเชิงรับรู้ของภาพอ้างอิงเพื่อการจับคู่ที่ทนทาน.

## การลบลายน้ำ
Once you’ve identified unwanted watermarks, you can clear them and save a clean copy of the diagram.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

- **เมธอดสำคัญ:** `clear()` จะลบลายน้ำทั้งหมดที่พบโดยเกณฑ์ที่รวมกัน ทำให้แผนภาพคงสภาพเดิม.

## การประยุกต์ใช้งานจริง
1. **การบูรณาการซอฟต์แวร์ระดับองค์กร** – ฝังการจัดการลายน้ำเข้าในแอปธุรกิจเพื่อปกป้องแผนภาพที่เป็นทรัพย์สินของบริษัท.  
2. **ระบบจัดการเนื้อหา (CMS)** – ทำให้การตรวจจับและลบโลโก้ที่ไม่ได้รับอนุญาตเป็นอัตโนมัติก่อนการเผยแพร่.  
3. **กระบวนการทำงานของเอกสารทางกฎหมาย** – เพิ่มหรือลบลายน้ำในขั้นตอนต่างๆ ของการประมวลผลสัญญา.

## ปัญหาที่พบบ่อยและการแก้ไข
- **ข้อผิดพลาดใบอนุญาต:** ตรวจสอบให้แน่ใจว่าไฟล์ใบอนุญาตถูกอ้างอิงอย่างถูกต้องก่อนสร้าง `Watermarker`.  
- **ไฟล์ขนาดใหญ่:** ใช้ API แบบสตรีมมิ่งหรือเพิ่มขนาด heap ของ JVM (`-Xmx2g`) สำหรับแผนภาพที่ใหญ่กว่า 100 MB.  
- **ลายน้ำไม่พบ:** ตรวจสอบว่าเกณฑ์การค้นหา (ตัวอักษร, เกณฑ์ความคล้ายของภาพ) ตรงกับเนื้อหาลายน้ำจริง.

## คำถามที่พบบ่อย
**ถาม: ฉันสามารถค้นหาทั้งข้อความและรูปภาพพร้อมกันได้หรือไม่?**  
ตอบ: ได้. รวมเกณฑ์ด้วย `or()` ตามที่แสดงในตัวอย่างการลบ.

**ถาม: การลบลายน้ำปลอดภัยโดยไม่ทำให้โครงสร้างแผนภาพเปลี่ยนแปลงหรือไม่?**  
ตอบ: แน่นอน. API จะกำหนดเป้าหมายลายน้ำอย่างแม่นยำ ทำให้ส่วนอื่นของแผนภาพคงเดิม.

**ถาม: GroupDocs.Watermark รองรับรูปแบบแผนภาพใดบ้าง?**  
ตอบ: รองรับรูปแบบ Visio เช่น `.vsdx`, `.vdx` รวมถึงประเภทแผนภาพเวกเตอร์อื่นๆ.

**ถาม: ฉันจะประมวลผลแผนภาพหลายร้อยไฟล์ได้อย่างมีประสิทธิภาพอย่างไร?**  
ตอบ: สร้างลูปแบบแบช, ใช้ `Watermarker` ตัวเดียวซ้ำเมื่อเป็นไปได้, และพิจารณาการประมวลผลแบบขนานด้วย `ExecutorService` ของ Java.

**ถาม: ฉันสามารถรวมการตรวจจับลายน้ำเข้าใน pipeline CI/CD ได้หรือไม่?**  
ตอบ: ได้. ใส่โค้ด Java ลงในสคริปต์การสร้าง (เช่น Maven plugins หรือ Gradle tasks) เพื่อยืนยันแผนภาพก่อนการปรับใช้.

## สรุป
โดยการใช้ **groupdocs watermark maven** คุณจะได้วิธีที่ทรงพลังและจัดการด้วย Maven เพื่อโหลด, ค้นหา, และลบลายน้ำจากไฟล์แผนภาพด้วย Java ความสามารถนี้ช่วยเสริมความปลอดภัยของเอกสาร, ทำให้กระบวนการทำงานของเนื้อหาเป็นระบบ, และขยายได้อย่างง่ายดายในคอลเลกชันเอกสารขนาดใหญ่.

---

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบกับ:** GroupDocs.Watermark 24.11 for Java  
**ผู้เขียน:** GroupDocs