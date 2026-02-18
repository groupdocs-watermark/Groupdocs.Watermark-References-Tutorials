---
date: '2026-02-18'
description: เรียนรู้วิธีเพิ่มลายน้ำและวิธีลบลายน้ำในไฟล์แผนภาพเช่น .vsdx ด้วย GroupDocs.Watermark
  สำหรับ Java. ปกป้องความสมบูรณ์ของเอกสารด้วย GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: วิธีเพิ่มลายน้ำลงในแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java
type: docs
url: /th/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# วิธีเพิ่มลายน้ำในแผนภาพโดยใช้ GroupDocs.Watermark สำหรับ Java

การจัดการลายน้ำในไฟล์แผนภาพเป็นส่วนสำคัญของการปกป้องทรัพย์สินทางปัญญาและทำให้เอกสารพร้อมสำหรับการเผยแพร่สาธารณะ ในคู่มือนี้คุณจะได้เรียนรู้ **วิธีเพิ่มลายน้ำ** ลงในแผนภาพ Visio รวมถึง **วิธีลบลายน้ำ** เมื่อไม่ต้องการใช้งานอีกต่อไป ทั้งหมดนี้ใช้ไลบรารี **groupdocs watermark java** ไม่ว่าคุณจะสร้าง pipeline เอกสารระดับองค์กรหรือสคริปต์ยูทิลิตี้อย่างรวดเร็ว ขั้นตอนเหล่านี้จะให้คุณควบคุมการใส่ลายน้ำในแผนภาพได้อย่างเต็มที่

## คำตอบสั้น ๆ
- **ไลบรารีใดที่จัดการลายน้ำในแผนภาพสำหรับ Java?** GroupDocs.Watermark for Java.  
- **ฉันสามารถเพิ่มและลบลายน้ำในรอบการทำงานเดียวได้หรือไม่?** ได้ – โหลดแผนภาพครั้งเดียวแล้วทำการเพิ่มและลบได้พร้อมกัน.  
- **ไฟล์ฟอร์แมตใดบ้างที่รองรับ?** ฟอร์แมต Visio เช่น `.vsdx`, `.vdx` รวมถึงประเภทแผนภาพอื่น ๆ.  
- **ต้องใช้ไลเซนส์หรือไม่?** ไลเซนส์ทดลองใช้ได้สำหรับการพัฒนา; ต้องมีไลเซนส์เต็มสำหรับการใช้งานในโปรดักชัน.  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า.

## “วิธีเพิ่มลายน้ำ” ในบริบทของแผนภาพคืออะไร?
การเพิ่มลายน้ำหมายถึงการฝังเครื่องหมายที่มองเห็นหรือไม่มองเห็น—ข้อความ, โลโก้ หรือรูปภาพ—เข้าไปในไฟล์แผนภาพ เครื่องหมายนี้จะเดินทางพร้อมไฟล์ ทำให้ง่ายต่อการพิสูจน์ความเป็นเจ้าของหรือระบุว่าเป็นเวอร์ชันร่าง.

## ทำไมต้องใช้ GroupDocs.Watermark สำหรับ Java?
* **Rich API** – ค้นหา, เพิ่ม, และลบลายน้ำทั้งข้อความและรูปภาพด้วยไม่กี่บรรทัดของโค้ด.  
* **Cross‑format support** – ทำงานกับ Visio (`.vsdx`, `.vdx`) และแผนภาพประเภทอื่น ๆ มากมาย.  
* **Performance‑focused** – โหลดเฉพาะส่วนของแผนภาพที่จำเป็นสำหรับการทำงานกับลายน้ำ ลดการใช้หน่วยความจำ.

## ข้อกำหนดเบื้องต้น
1. **Java Development Kit (JDK) 8+** – ตรวจสอบว่า `java -version` แสดง 1.8 หรือใหม่กว่า.  
2. **IDE** – IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไขที่คุณชอบ.  
3. **GroupDocs.Watermark for Java** – เพิ่มลงในโปรเจกต์ผ่าน Maven หรือดาวน์โหลด JAR โดยตรง.  

### ไลบรารีและ Dependencies ที่ต้องใช้
เพิ่ม repository และ dependency ลงใน `pom.xml` ของคุณ:

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

*หากคุณไม่ต้องการใช้ Maven สามารถดาวน์โหลด JAR ล่าสุดได้จาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### การจัดหาไลเซนส์
- **Free Trial:** ทดสอบทุกฟีเจอร์โดยไม่ต้องใช้คีย์ไลเซนส์.  
- **Temporary License:** ขอคีย์แบบจำกัดเวลาเพื่อการประเมิน.  
- **Full License:** ซื้อสมัครสมาชิกเพื่อใช้ในโปรดักชันโดยไม่มีข้อจำกัด.

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
1. **เพิ่มไลบรารี** ลงในโปรเจกต์ (Maven หรือ JAR แบบแมนนวล).  
2. **สร้างอินสแตนซ์ `Watermarker`** – วัตถุนี้เป็นจุดเริ่มต้นสำหรับการโหลดแผนภาพ, ค้นหา, เพิ่ม, และลบลายน้ำ.

## คู่มือการใช้งาน

### การโหลดเอกสารแผนภาพ
การโหลดเป็นขั้นตอนแรกก่อนที่คุณจะ **เพิ่มลายน้ำ** หรือ **ลบลายน้ำ** โค้ดด้านล่างแสดงวิธีเปิดไฟล์ `.vsdx` พร้อมตัวเลือกการโหลดแบบกำหนดเอง.

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

### การค้นหาลายน้ำข้อความ
ก่อนที่คุณจะเพิ่มลายน้ำใหม่ คุณอาจต้องตรวจสอบว่ามีลายน้ำข้อความอยู่แล้วหรือไม่ ตัวอย่างนี้ค้นหาวลี “Company Name”.

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

### การค้นหาลายน้ำรูปภาพ
หากต้องการค้นหาโลโก้หรือรูปภาพใด ๆ ที่ใช้เป็นลายน้ำ ให้ใช้ `ImageDctHashSearchCriteria` ซึ่งสะดวกเมื่อคุณต้องการ **ลบลายน้ำ** ที่ตรงกับโลโก้ที่รู้จัก.

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

### การลบลายน้ำ
เมื่อคุณระบุตำแหน่งลายน้ำ—ไม่ว่าจะเป็นข้อความ, รูปภาพ หรือทั้งสองอย่าง—คุณสามารถลบออกจากแผนภาพได้ ตัวอย่างต่อไปนี้แสดงการลบแบบรวมกัน.

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

## การประยุกต์ใช้งานจริง
1. **Enterprise Software Integration** – ฝังการจัดการลายน้ำเข้าไปใน ERP หรือแพลตฟอร์มสร้างเอกสารของคุณเพื่อบังคับใช้แบรนด์.  
2. **Content Management Systems (CMS)** – สแกนแผนภาพที่อัปโหลดโดยอัตโนมัติเพื่อค้นหาโลโก้ที่ไม่ได้รับอนุญาตและลบออก.  
3. **Legal Document Handling** – เพิ่มลายน้ำข้อความ “Confidential” ในขั้นตอนร่างและ **ลบลายน้ำ** ก่อนการยื่นไฟล์ขั้นสุดท้าย.

## ปัญหาที่พบบ่อยและวิธีแก้
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| ไม่พบลายน้ำใด ๆ | ข้อความ/รูปภาพที่ค้นหาไม่ตรงกันอย่างแม่นยำ | ใช้ `or()` เพื่อรวม criteria หรือปรับการตั้งค่าความไวต่อขนาดตัวอักษร. |
| `OutOfMemoryError` กับไฟล์ขนาดใหญ่ | โหลดแผนภาพทั้งหมดเข้าสู่หน่วยความจำ | ใช้ `DiagramLoadOptions.setLoadPages()` เพื่อโหลดเฉพาะหน้าที่ต้องการ. |
| ไฟล์ที่บันทึกเสีย | เรียก `watermarker.save()` ก่อนทำความสะอาดลายน้ำทั้งหมด | ตรวจสอบให้ `possibleWatermarks.clear()` เสร็จสมบูรณ์และเรียก `watermarker.close()` หลังบันทึก. |

## คำถามที่พบบ่อย

**Q: ฉันสามารถค้นหาทั้งข้อความและรูปภาพพร้อมกันได้หรือไม่?**  
A: ได้. ผสาน `TextSearchCriteria` กับ `ImageDctHashSearchCriteria` ด้วยเมธอด `or()` ตามที่แสดงในตัวอย่างการลบ.

**Q: สามารถลบลายน้ำโดยไม่ทำให้แผนภาพเสียหายได้หรือไม่?**  
A: แน่นอน. ไลบรารีแยกวัตถุลายน้ำออกจากส่วนอื่นของแผนภาพ ดังนั้นการเรียก `clear()` จะลบเฉพาะชั้นลายน้ำโดยคงเนื้อหาเดิมไว้.

**Q: GroupDocs.Watermark รองรับหลายฟอร์แมตของแผนภาพหรือไม่?**  
A: รองรับ. ฟอร์แมตเช่น `.vsdx`, `.vdx` และไฟล์ Visio‑compatible อื่น ๆ ได้อย่างเต็มที่.

**Q: จะจัดการกับปริมาณเอกสารจำนวนมากอย่างมีประสิทธิภาพอย่างไร?**  
A: ใช้ลูปประมวลผลแบบ batch, ใช้ `Watermarker` อินสแตนซ์เดียวซ้ำได้เมื่อเป็นไปได้, และจำกัดการโหลดหน้าโดยใช้ `DiagramLoadOptions`.

**Q: มีวิธีอัตโนมัติการตรวจจับลายน้ำใน pipeline CI/CD หรือไม่?**  
A: คุณสามารถฝังโค้ด Java ที่ให้ไว้ในสคริปต์การสร้างของคุณ (เช่น Maven หรือ Gradle) เพื่อยืนยันว่าไม่มีลายน้ำที่ไม่ได้รับอนุญาตก่อนปล่อย artifact.

---

**Last Updated:** 2026-02-18  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs