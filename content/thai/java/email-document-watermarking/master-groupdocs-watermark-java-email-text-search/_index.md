---
date: '2026-04-07'
description: เรียนรู้วิธีค้นหาข้อความในอีเมลด้วย Java โดยใช้ GroupDocs.Watermark รวมถึงวิธีค้นหาคำสำคัญหลายคำในอีเมลและวิธีลบลายน้ำจากอีเมล
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'ค้นหาข้อความอีเมลใน Java ด้วย GroupDocs.Watermark: คู่มือฉบับสมบูรณ์'
type: docs
url: /th/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# ค้นหาเนื้อหาอีเมล Java ด้วย GroupDocs.Watermark

หากคุณต้องการ **search email body java** อย่างรวดเร็วและเชื่อถือได้ คุณมาถูกที่แล้ว ในบทแนะนำนี้เราจะอธิบายว่า GroupDocs.Watermark สำหรับ Java ช่วยให้คุณค้นหาข้อความเฉพาะในหัวเรื่องอีเมล, เนื้อหา HTML, และเนื้อหาแบบข้อความธรรมดาได้อย่างไร และคุณจะทำความสะอาดลายน้ำที่ไม่ต้องการหลังจากนั้นได้อย่างไร เมื่อเสร็จสิ้นคุณจะสามารถนำไปใช้สร้างโซลูชันที่แข็งแรงซึ่งทำงานกับคีย์เวิร์ดเดียวหรือหลายคีย์เวิร์ดและแม้กระทั่งลบลายน้ำในอีเมลเมื่อจำเป็น

## คำตอบอย่างรวดเร็ว
- **search email body java หมายถึงอะไร?** มันหมายถึงการใช้โค้ด Java (กับ GroupDocs.Watermark) เพื่อค้นหาข้อความภายในเนื้อหาอีเมล  
- **สามารถค้นหาหลายคีย์เวิร์ดในอีเมลพร้อมกันได้หรือไม่?** ใช่ – สร้างอ็อบเจกต์ `SearchCriteria` แยกกันและรวมเข้าด้วยกัน  
- **วิธีการลบลายน้ำในอีเมล?** ใช้เมธอด `PossibleWatermarkCollection.clear()` หลังการค้นหา  
- **ฉันต้องการไลเซนส์หรือไม่?** ทดลองใช้ฟรีสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานจริง  
- **IDE ใดทำงานได้ดีที่สุด?** IntelliJ IDEA หรือ Eclipse รองรับเต็มที่ทั้งสองตัว

## สิ่งที่คุณจะได้เรียนรู้
- การติดตั้งและกำหนดค่า GroupDocs.Watermark สำหรับ Java  
- การตั้งค่าเกณฑ์การค้นหาเพื่อ **search email body java** ครอบคลุมหัวเรื่องและเนื้อหา  
- เทคนิคสำหรับ **search multiple keywords email** ในการทำงานครั้งเดียว  
- ขั้นตอนที่แม่นยำ **how to remove email watermarks** หลังจากค้นพบแล้ว  

## ทำไมต้องค้นหาเนื้อหาอีเมล Java ด้วย GroupDocs.Watermark?
GroupDocs.Watermark ให้ API ระดับสูงที่แยกความซับซ้อนของการแยกไฟล์ .msg, การจัดการรูปแบบเนื้อหาต่าง ๆ, และการจัดการลายน้ำออกไป ซึ่งช่วยประหยัดเวลาเมื่อเทียบกับการสร้างพาร์เซอร์แบบกำหนดเองและทำให้ผลลัพธ์สอดคล้องกันในชุดอีเมลขนาดใหญ่

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK) 8 หรือใหม่กว่า  
- Maven (หรือความสามารถในการเพิ่ม JAR ด้วยตนเอง)  
- ความคุ้นเคยพื้นฐานกับ Java และรูปแบบไฟล์อีเมล (.msg, .eml)  

## การตั้งค่า GroupDocs.Watermark สำหรับ Java
GroupDocs.Watermark สำหรับ Java ทำให้การใส่ลายน้ำและการค้นหาข้อความในเอกสารรวมถึงอีเมลเป็นเรื่องง่าย ด้านล่างนี้เป็นสองวิธีที่พบบ่อยที่สุดในการเพิ่มไลบรารีลงในโปรเจกต์ของคุณ

### การตั้งค่า Maven
ใส่โค้ดต่อไปนี้ในไฟล์ `pom.xml` ของคุณเพื่อเพิ่ม GroupDocs.Watermark เป็น dependency:
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

### ขั้นตอนการรับไลเซนส์
- **Free Trial:** เริ่มต้นด้วยการทดลองใช้ฟรีเพื่อทดสอบฟังก์ชันพื้นฐาน  
- **Temporary License:** รับไลเซนส์ชั่วคราวสำหรับการเข้าถึงและการทดสอบที่ขยายเวลา  
- **Purchase:** พิจารณาซื้อไลเซนส์หาก GroupDocs.Watermark ตรงกับความต้องการของคุณ  

#### การเริ่มต้นพื้นฐาน
เริ่มต้นคลาส `Watermarker` ตามตัวอย่างด้านล่าง:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## คู่มือการใช้งาน

### ฟีเจอร์ 1: ค้นหาข้อความในเนื้อหาอีเมล
ฟีเจอร์นี้ช่วยให้คุณค้นหาข้อความเฉพาะในหัวเรื่องและเนื้อหาอีเมลได้

#### ภาพรวม
เราจะสาธิตวิธีกำหนดค่า GroupDocs.Watermark เพื่อค้นหาผ่านส่วนต่าง ๆ ของข้อความอีเมลโดยใช้โค้ด Java

##### ขั้นตอนที่ 1: กำหนดเส้นทางไฟล์เอกสาร
ตั้งค่าเส้นทางอินพุตและเอาต์พุตสำหรับการจัดการอีเมล:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### ขั้นตอนที่ 2: ตั้งค่า Load Options และ Watermarker
เริ่มต้น `EmailLoadOptions` และ `Watermarker` เพื่อทำงานกับเอกสารอีเมลของคุณ
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### ขั้นตอนที่ 3: สร้างเกณฑ์การค้นหา
กำหนดเกณฑ์การค้นหาข้อความ เราจะใช้การค้นหาแบบไม่แยกแยะตัวพิมพ์สำหรับคีย์เวิร์ด **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### ขั้นตอนที่ 4: ระบุตำแหน่งการค้นหา
กำหนดให้การค้นหาครอบคลุมทั้งหัวเรื่องและเนื้อหาของอีเมล:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### ขั้นตอนที่ 5: ดำเนินการค้นหาและลบลายน้ำ
ทำการค้นหาและลบลายน้ำที่พบ:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### ขั้นตอนที่ 6: บันทึกการเปลี่ยนแปลง
หลังจากประมวลผลเสร็จ ให้บันทึกการเปลี่ยนแปลงลงในเอกสารใหม่:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### เคล็ดลับการแก้ปัญหา
- **ปัญหาทั่วไป:** หากผลลัพธ์การค้นหาว่างเปล่า ให้ตรวจสอบว่าข้อความมีอยู่ในเนื้อหาอีเมลหรือหัวเรื่องหรือไม่  
- **เคล็ดลับประสิทธิภาพ:** ปรับให้ค้นหาเฉพาะส่วนที่คุณต้องการจริง ๆ เพื่อเพิ่มความเร็ว

### ฟีเจอร์ 2: ตัวเลือกการโหลดเอกสารอีเมล
ส่วนนี้อธิบายวิธีตั้งค่าตัวเลือกเพิ่มเติมเมื่อโหลดเอกสารอีเมลเพื่อประมวลผลด้วย GroupDocs.Watermark

#### ภาพรวม
การกำหนดค่า load options ให้การควบคุมการจัดการเอกสารมากขึ้น เช่น การกำหนดรหัสผ่านหรือการตั้งค่า encoding

##### ขั้นตอนที่ 1: กำหนดค่า Load Options
นี่คือตัวอย่างการตั้งค่าเบื้องต้นสำหรับ `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### ตัวเลือกการกำหนดค่าหลัก
- **Password Protection:** ระบุรหัสผ่านหากอีเมลของคุณถูกเข้ารหัส  
- **Encoding Settings:** กำหนดประเภทการเข้ารหัสที่ต้องการตามความจำเป็น  

## วิธีการค้นหาหลายคีย์เวิร์ดในอีเมล
หากคุณต้องการค้นหาหลายคำในครั้งเดียว ให้สร้างอ็อบเจกต์ `SearchCriteria` หลายตัวและรวมเข้าด้วยกันโดยใช้ตัวดำเนินการ **OR** หรือ **AND** API ช่วยให้คุณเชื่อมต่อเกณฑ์ได้ ดังนั้นคุณสามารถค้นหา “invoice” **or** “receipt” ได้โดยไม่ต้องวนลูปแยกต่างหาก

## วิธีการลบลายน้ำในอีเมล
หลังจากคุณค้นพบลายน้ำ (หรือข้อความใด ๆ ที่ตรงกับเกณฑ์) เมธอด `PossibleWatermarkCollection.clear()` จะลบลายน้ำออกจากเอกสารอีเมล นี่คือขั้นตอนที่ใช้ใน **ขั้นตอน 5** ข้างต้นและทำงานกับจำนวนแมตช์ใด ๆ ก็ได้

## การประยุกต์ใช้งานจริง

### กรณีใช้งาน 1: การประมวลผลอีเมลอัตโนมัติ
อัตโนมัติการกรองและประมวลผลข้อมูลอีเมลจำนวนมากเพื่อค้นหาเนื้อหาเฉพาะอย่างมีประสิทธิภาพ

### กรณีใช้งาน 2: การตรวจสอบความสอดคล้องตามกฎหมาย
ตรวจสอบความสอดคล้องโดยการค้นหาข้อมูลที่ละเอียดอ่อนภายในอีเมลขององค์กร

### กรณีใช้งาน 3: การอัตโนมัติการสนับสนุนลูกค้า
ทำให้กระบวนการสนับสนุนเป็นไปอย่างราบรื่นโดยการค้นหาคีย์เวิร์ดหรือวลีในคำถามของลูกค้าอย่างรวดเร็ว

## พิจารณาด้านประสิทธิภาพ
เมื่อใช้ GroupDocs.Watermark ควรคำนึงถึงสิ่งต่อไปนี้เพื่อเพิ่มประสิทธิภาพ:

- **การจัดการทรัพยากร:** จัดการหน่วยความจำและพลังการประมวลผลอย่างมีประสิทธิภาพเพื่อจัดการชุดข้อมูลอีเมลขนาดใหญ่  
- **Java Memory Management Best Practices:** ตรวจสอบการใช้ทรัพยากรเป็นประจำและปล่อยทรัพยากรเมื่อไม่จำเป็น

## คำถามที่พบบ่อย

**Q:** วิธีการจัดการอีเมลที่เข้ารหัสด้วย GroupDocs.Watermark?  
**A:** ใช้ `EmailLoadOptions` เพื่อระบุรหัสผ่านเมื่อเริ่มต้น `Watermarker`

**Q:** สามารถค้นหาหลายคีย์เวิร์ดพร้อมกันได้หรือไม่?  
**A:** ใช่, สร้างอินสแตนซ์ `SearchCriteria` แยกกันและรวมโดยใช้ตัวดำเนินการเชิงตรรกะ

**Q:** GroupDocs.Watermark Java ใช้ได้ฟรีหรือไม่?  
**A:** มีการทดลองใช้ฟรี; พิจารณาซื้อไลเซนส์สำหรับฟีเจอร์ที่ขยายเพิ่มเติม

**Q:** จะจัดการกับปริมาณอีเมลจำนวนมากอย่างมีประสิทธิภาพอย่างไร?  
**A:** ปรับการค้นหาให้มุ่งเป้าไปยังส่วนเฉพาะของอีเมลและจัดการทรัพยากรอย่างเหมาะสม

**Q:** จะหาแหล่งช่วยเหลือหรือสนับสนุนเพิ่มเติมได้จากที่ไหน?  
**A:** เยี่ยมชม [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) เพื่อรับการสนับสนุนจากชุมชนหรือช่องทางสนับสนุนฟรีของพวกเขา

## แหล่งข้อมูล
- **Documentation:** สำรวจคู่มือโดยละเอียดที่ [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API Reference:** เข้าถึงรายละเอียดทางเทคนิคที่ [GroupDocs API](https://apireference.groupdocs.com/watermark/java/)  

---

**Last Updated:** 2026-04-07  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs