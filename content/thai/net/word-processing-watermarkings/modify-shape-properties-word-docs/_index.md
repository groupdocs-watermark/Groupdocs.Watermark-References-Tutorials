---
title: แก้ไขคุณสมบัติของรูปร่างในเอกสาร Word
linktitle: แก้ไขคุณสมบัติของรูปร่างในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: ปกป้องเอกสาร Word ของคุณด้วย GroupDocs ลายน้ำสำหรับ .NET ปรับเปลี่ยนคุณสมบัติรูปร่างได้อย่างง่ายดายเพื่อเพิ่มความปลอดภัย
weight: 27
url: /th/net/word-processing-watermarkings/modify-shape-properties-word-docs/
---

# แก้ไขคุณสมบัติของรูปร่างในเอกสาร Word

## การแนะนำ
ในยุคดิจิทัลปัจจุบัน การรับรองความปลอดภัยของเอกสารของคุณเป็นสิ่งสำคัญยิ่ง ไม่ว่าคุณจะเป็นนักธุรกิจ ผู้เชี่ยวชาญด้านกฎหมาย หรือนักเขียนเชิงสร้างสรรค์ การปกป้องข้อมูลที่ละเอียดอ่อนของคุณเป็นสิ่งสำคัญ นี่คือจุดที่ GroupDocs.Watermark สำหรับ .NET เข้ามามีบทบาท โดยนำเสนอโซลูชั่นที่ครอบคลุมเพื่อปกป้องเอกสารของคุณจากการใช้และการแจกจ่ายโดยไม่ได้รับอนุญาต
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark for .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark for .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสาร Word ที่คุณต้องการแก้ไขให้พร้อม
3. ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# จะเป็นประโยชน์

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโค้ด C# ของคุณ:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
ตอนนี้ เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: โหลดเอกสาร
ขั้นแรก ระบุเส้นทางไปยังเอกสาร Word ของคุณและชื่อไฟล์เอาต์พุต ตรวจสอบให้แน่ใจว่าได้รวมตัวเลือกการโหลดที่จำเป็น:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
```
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำ
สร้างอินสแตนซ์ของ`Watermarker` คลาสและโหลดเอกสารโดยใช้ตัวเลือกการโหลดที่ระบุ:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ขั้นตอนที่ 3: แก้ไขคุณสมบัติของรูปร่าง
วนซ้ำรูปร่างในส่วนของเอกสารและใช้การแก้ไขที่ต้องการ:
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.AlternativeText = "watermark";
        shape.RotateAngle = 30;
        shape.X = 200;
        shape.Y = 200;
        shape.Height = 100;
        shape.Width = 400;
        shape.BehindText = false;
    }
}
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
เมื่อนำการแก้ไขไปใช้แล้ว ให้บันทึกเอกสารที่มีการเปลี่ยนแปลง:
```csharp
watermarker.Save(outputFileName);
```
## บทสรุป
GroupDocs.Watermark สำหรับ .NET ช่วยให้คุณสามารถเพิ่มความปลอดภัยให้กับเอกสาร Word ของคุณโดยการปรับเปลี่ยนคุณสมบัติรูปร่างได้อย่างง่ายดาย ด้วย API ที่ใช้งานง่ายและคุณสมบัติที่ครอบคลุม การปกป้องข้อมูลที่ละเอียดอ่อนของคุณง่ายกว่าที่เคย

## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, PDF และอีกมากมาย
### ฉันสามารถปรับแต่งข้อความลายน้ำและลักษณะที่ปรากฏได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark มีตัวเลือกมากมายในการปรับแต่งข้อความลายน้ำ แบบอักษร สี ความทึบ และตำแหน่ง
### GroupDocs.Watermark มีความสามารถในการประมวลผลเป็นชุดหรือไม่
ใช่ คุณสามารถประมวลผลเอกสารหลายชุดพร้อมกันด้วย GroupDocs ซึ่งช่วยประหยัดเวลาและความพยายาม
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Watermark ได้ด้วยการดาวน์โหลดเวอร์ชันทดลองใช้ฟรีจาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Watermark ได้อย่างไร
 หากมีข้อสงสัยหรือความช่วยเหลือ คุณสามารถไปที่ฟอรัม GroupDocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19).