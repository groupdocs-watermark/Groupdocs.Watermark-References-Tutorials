---
date: '2025-12-31'
description: เรียนรู้วิธีค้นหาข้อความอีเมลด้วย GroupDocs.Watermark สำหรับ Java จัดการเนื้อหา
  เรื่อง และไฟล์แนบอย่างมีประสิทธิภาพ
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: วิธีค้นหาข้อความอีเมลด้วย GroupDocs.Watermark Java – คู่มือฉบับสมบูรณ์
type: docs
url: /th/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# วิธีค้นหาข้อความอีเมลด้วย GroupDocs.Watermark Java

การค้นหาวลีเฉพาะในหัวเรื่อง, เนื้อหา หรือไฟล์แนบของอีเมลอาจทำให้ศีรษะปวด—โดยเฉพาะเมื่อคุณต้องจัดการกับหลายสิบหรือหลายร้อยข้อความ ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีค้นหาอีเมล** อย่างรวดเร็วและแม่นยำโดยใช้ **GroupDocs.Watermark for Java** เราจะอธิบายขั้นตอนการตั้งค่า, โค้ด, และเคล็ดลับการปฏิบัติที่ดีที่สุด เพื่อให้คุณสามารถรวมการค้นหาข้อความอีเมลเข้าไปในแอปพลิเคชันของคุณได้อย่างมั่นใจ.

## คำตอบด่วน
- **ไลบรารีใดที่ให้ฉันค้นหาข้อความอีเมลใน Java?** GroupDocs.Watermark for Java.  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์แบบชำระเงินสำหรับการใช้งานจริง.  
- **ฉันสามารถค้นหาทั้งหัวเรื่องและเนื้อหาได้หรือไม่?** ได้—กำหนดค่า `EmailSearchableObjects` ให้รวม Subject, HtmlBody, และ PlainTextBody.  
- **API มีความไวต่อขนาดตัวอักษรหรือไม่?** คุณสามารถเลือกการค้นหาแบบไม่สนใจขนาดตัวอักษรโดยตั้งค่าสถานะที่เหมาะสมใน `TextSearchCriteria`.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า; แนะนำให้ใช้ Maven สำหรับการจัดการ dependencies.

## “วิธีค้นหาอีเมล” กับ GroupDocs.Watermark คืออะไร?
GroupDocs.Watermark ให้ API แบบรวมศูนย์สำหรับการค้นหา, ลบ, หรือแก้ไขลายน้ำและข้อความธรรมดาในหลายประเภทเอกสาร—including **ข้อความอีเมล** (`.msg`, `.eml`). ด้วยการใช้โมเดล searchable objects ของมัน คุณสามารถกำหนดเป้าหมายส่วนที่ต้องการของอีเมลได้อย่างแม่นยำ ทำให้การประมวลผลเป็นกลุ่มเร็วและเชื่อถือได้.

## ทำไมต้องใช้ GroupDocs.Watermark Java สำหรับการค้นหาอีเมล?
- **Unified API** – ทำงานกับ PDF, รูปภาพ, ไฟล์ Office, และอีเมลโดยใช้รูปแบบโค้ดเดียวกัน.  
- **Performance‑optimized** – การค้นหาทำงานในหน่วยความจำโดยไม่ต้องพึ่งบริการภายนอก.  
- **Robust handling** – รองรับเนื้อหา HTML และ plain‑text, ไฟล์แนบ, และแม้กระทั่งอีเมลที่มีการป้องกันด้วยรหัสผ่าน.  
- **Easy integration** – พร้อมใช้กับ Maven/Gradle, มีเอกสารที่ชัดเจนและการสนับสนุนที่พร้อมใช้งาน.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK)** 8 หรือใหม่กว่า.  
- **Maven** (หรือ Gradle) สำหรับการจัดการ dependencies.  
- IDE เช่น **IntelliJ IDEA** หรือ **Eclipse**.  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และรูปแบบไฟล์อีเมล (`.msg`, `.eml`).

## การตั้งค่า GroupDocs.Watermark สำหรับ Java

### การตั้งค่า Maven
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

### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### การรับไลเซนส์
- **Free Trial:** ทดสอบฟีเจอร์หลักโดยไม่ต้องใช้คีย์ไลเซนส์.  
- **Temporary License:** ขอคีย์ที่มีระยะเวลาจำกัดสำหรับการประเมินผลต่อเนื่อง.  
- **Paid License:** ซื้อเพื่อการใช้งานในผลิตภัณฑ์โดยไม่มีขีดจำกัด.

#### การเริ่มต้นพื้นฐาน
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## คู่มือการใช้งาน

### ฟีเจอร์ 1: ค้นหาข้อความในเนื้อหาอีเมล

#### ภาพรวม
เราจะกำหนดค่า API เพื่อสแกน **หัวเรื่อง**, **เนื้อหา HTML**, และ **เนื้อหา plain‑text** ของอีเมลตามคีย์เวิร์ดที่กำหนด

#### ขั้นตอนที่ 1: กำหนดเส้นทางเอกสาร
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### ขั้นตอนที่ 2: ตั้งค่า Load Options และ Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### ขั้นตอนที่ 3: สร้าง Search Criteria
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### ขั้นตอนที่ 4: ระบุตำแหน่งการค้นหา
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### ขั้นตอนที่ 5: ดำเนินการค้นหาและลบลายน้ำ
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### ขั้นตอนที่ 6: บันทึกการเปลี่ยนแปลง
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### เคล็ดลับการแก้ไขปัญหา
- **Empty results:** ตรวจสอบว่าคีย์เวิร์ดปรากฏจริงในส่วนของอีเมลที่เลือก.  
- **Performance:** จำกัด searchable objects ให้เหลือเฉพาะที่คุณต้องการ (เช่น Subject + PlainTextBody) เพื่อเร่งความเร็วในชุดข้อมูลขนาดใหญ่.

### ฟีเจอร์ 2: ตัวเลือกการโหลดเอกสารอีเมล

#### ภาพรวม
`EmailLoadOptions` ให้คุณควบคุมวิธีการแยกวิเคราะห์อีเมล—มีประโยชน์สำหรับข้อความที่เข้ารหัสหรือการเข้ารหัสแบบกำหนดเอง.

#### ขั้นตอนที่ 1: กำหนดค่า Load Options
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### ตัวเลือกการกำหนดค่าหลัก
- **Password Protection:** ตั้งค่า `loadOptions.setPassword("yourPassword")` สำหรับไฟล์ `.msg` ที่เข้ารหัส.  
- **Encoding Settings:** ปรับ `loadOptions.setEncoding(Charset.forName("UTF-8"))` เมื่อทำงานกับชุดอักขระที่ไม่เป็นมาตรฐาน.

## การประยุกต์ใช้งานจริง
- **Automated Email Processing:** สแกนอีเมลสนับสนุนที่เข้ามาเป็นกลุ่มเพื่อค้นหาคำสำคัญเช่น “refund” หรือ “error”.**  
- **Legal Compliance Checks:** ค้นหาเงื่อนไขที่เป็นความลับ (เช่น SSN, หมายเลขบัตรเครดิต) อย่างรวดเร็วในคลังอีเมลขององค์กร.**  
- **Customer Support Automation:** ส่งต่ออีเมลตามวลีที่ตรวจพบไปยังทีมสนับสนุนที่เหมาะสม.**

## การพิจารณาด้านประสิทธิภาพ
- **Resource Management:** เรียก `watermarker.close()` ทันทีที่เสร็จสิ้นการประมวลผลเพื่อปล่อยทรัพยากร native.  
- **Memory Best Practices:** เมื่อจัดการกับข้อความหลายพันรายการ, ประมวลผลเป็นชุดและใช้ instance ของ `Watermarker` ซ้ำเมื่อเป็นไปได้.

## สรุป
ตอนนี้คุณมีวิธีการที่มั่นคงและพร้อมใช้งานในผลิตภัณฑ์สำหรับ **วิธีค้นหาอีเมล** ด้วย GroupDocs.Watermark Java. ความยืดหยุ่นของ API ทำให้คุณสามารถกำหนดเป้าหมายส่วนเฉพาะของอีเมล, ลบลายน้ำที่ไม่ต้องการ, และรวมตรรกะนี้เข้าไปในกระบวนการทำงานที่ใหญ่ขึ้น.

### ขั้นตอนต่อไป
- ทดลองใช้ **multiple search criteria** (เช่น รวม “invoice” + “overdue”).  
- สำรวจ **watermark addition** เพื่อทำเครื่องหมายอีเมลที่มีข้อมูลที่ละเอียดอ่อน.  
- ศึกษาประเภทเอกสารอื่น (PDF, DOCX) ด้วย workflow ของ Watermarker เดียวกัน.

## คำถามที่พบบ่อย

**Q1:** ฉันจะจัดการกับอีเมลที่เข้ารหัสด้วย GroupDocs.Watermark อย่างไร?  
**A1:** ใช้ `EmailLoadOptions.setPassword("yourPassword")` ก่อนสร้าง instance ของ `Watermarker`.

**Q2:** ฉันสามารถค้นหาคำหลายคำพร้อมกันได้หรือไม่?  
**A2:** ได้—สร้างอ็อบเจกต์ `SearchCriteria` แยกสำหรับแต่ละคีย์เวิร์ดและรวมกันด้วยตัวดำเนินการตรรกะ (เช่น `OrSearchCriteria`).

**Q3:** GroupDocs.Watermark Java ใช้ได้ฟรีหรือไม่?  
**A3:** มีการทดลองใช้ฟรีสำหรับการประเมินผล สำหรับการใช้งานในผลิตภัณฑ์ จำเป็นต้องมีไลเซนส์แบบชำระเงิน.

**Q4:** ฉันจะจัดการกับปริมาณอีเมลจำนวนมากอย่างมีประสิทธิภาพได้อย่างไร?  
**A4:** จำกัด searchable objects ให้เหลือเฉพาะที่จำเป็น, ประมวลผลอีเมลเป็นชุด, และปิด `Watermarker` เสมอเพื่อปล่อยทรัพยากร.

**Q5:** ฉันจะหาแหล่งช่วยเหลือหรือสนับสนุนเพิ่มเติมได้จากที่ไหน?  
**A5:** เยี่ยมชม [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) เพื่อรับความช่วยเหลือจากชุมชนหรือ ติดต่อฝ่ายสนับสนุนของ GroupDocs โดยตรง.

## แหล่งข้อมูล
- **Documentation:** สำรวจคู่มือโดยละเอียดที่ [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** เข้าถึงรายละเอียดทางเทคนิคที่ [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Last Updated:** 2025-12-31  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---