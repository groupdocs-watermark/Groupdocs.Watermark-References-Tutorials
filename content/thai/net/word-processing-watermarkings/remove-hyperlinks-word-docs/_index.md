---
title: ลบไฮเปอร์ลิงก์ในเอกสาร Word
linktitle: ลบไฮเปอร์ลิงก์ในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบไฮเปอร์ลิงก์ออกจากเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET เพิ่มความปลอดภัยให้กับเอกสารได้อย่างง่ายดาย
weight: 29
url: /th/net/word-processing-watermarkings/remove-hyperlinks-word-docs/
type: docs
---
# ลบไฮเปอร์ลิงก์ในเอกสาร Word

## การแนะนำ
ในโลกดิจิทัลปัจจุบัน ที่ข้อมูลไหลอย่างราบรื่น การปกป้องเอกสารของคุณเป็นสิ่งสำคัญยิ่ง ไม่ว่าคุณจะแบ่งปันข้อมูลทางธุรกิจที่ละเอียดอ่อนหรือสร้างสรรค์ผลงานชิ้นเอก การปกป้องเนื้อหาของคุณจากการเข้าถึงและการบิดเบือนโดยไม่ได้รับอนุญาตถือเป็นสิ่งสำคัญ ด้วยการถือกำเนิดของ GroupDocs.Watermark สำหรับ .NET คุณสามารถรับประกันความสมบูรณ์ของเอกสารของคุณได้โดยการเพิ่ม ลบ และตรวจจับลายน้ำได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำดิ่งสู่โลกแห่งลายน้ำในเอกสารด้วย GroupDocs.Watermark สำหรับ .NET มีข้อกำหนดเบื้องต้นบางประการที่คุณต้องมี:
1.  การติดตั้ง GroupDocs.Watermark สำหรับ .NET: ไปที่[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/) เพื่อรับไฟล์ที่จำเป็นสำหรับการติดตั้ง ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้ในเอกสารประกอบ
2. ความเข้าใจพื้นฐานของ .NET Framework: ทำความคุ้นเคยกับ .NET Framework และพื้นฐานของมัน เพื่อสำรวจตัวอย่างการเขียนโค้ดได้อย่างง่ายดาย
3. การเข้าถึงตัวแก้ไขข้อความหรือ IDE: ตรวจสอบให้แน่ใจว่าคุณมีโปรแกรมแก้ไขข้อความหรือ Integrated Development Environment (IDE) เช่น Visual Studio ติดตั้งอยู่บนระบบของคุณเพื่อวัตถุประสงค์ในการเขียนโค้ด

## นำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกคำแนะนำทีละขั้นตอน ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 2: รับเนื้อหาการประมวลผลคำ
```csharp
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ขั้นตอนที่ 3: แทนที่ไฮเปอร์ลิงก์
```csharp
    // แทนที่ไฮเปอร์ลิงก์
    content.Sections[0].Shapes[0].Hyperlink = "https://www.groupdocs.com/”;
```
## ขั้นตอนที่ 4: ลบไฮเปอร์ลิงก์
```csharp
    // ลบไฮเปอร์ลิงก์
    content.Sections[0].Shapes[1].Hyperlink = null;
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
    watermarker.Save(outputFileName);
}
```

## บทสรุป
GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนาจัดการลายน้ำได้อย่างง่ายดาย ช่วยให้มั่นใจในความปลอดภัยและความสมบูรณ์ของเอกสาร ด้วยการทำตามคำแนะนำทีละขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถลบไฮเปอร์ลิงก์ออกจากเอกสาร Word ได้อย่างราบรื่น ซึ่งช่วยเพิ่มการรักษาความลับและความเป็นมืออาชีพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำโดยใช้ GroupDocs.Watermark ได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark นำเสนอตัวเลือกการปรับแต่งลายน้ำที่ครอบคลุม ซึ่งช่วยให้คุณปรับตำแหน่ง ขนาด ความทึบ และอื่นๆ ได้
### GroupDocs.Watermark รองรับการประมวลผลเป็นชุดหรือไม่
ใช่ คุณสามารถประมวลผลเอกสารหลายชุดพร้อมกันด้วย GroupDocs ซึ่งช่วยประหยัดเวลาและแรงงาน
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Watermark ได้ด้วยการดาวน์โหลดเวอร์ชันทดลองใช้ฟรีจาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark ได้อย่างไร
 สามารถรับสิทธิ์การใช้งาน GroupDocs ชั่วคราวได้จากเว็บไซต์[ที่นี่](https://purchase.groupdocs.com/temporary-license/).