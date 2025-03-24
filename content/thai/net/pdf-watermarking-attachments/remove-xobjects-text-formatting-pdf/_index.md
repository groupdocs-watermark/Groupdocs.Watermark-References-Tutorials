---
title: ลบ XObjects ด้วยการจัดรูปแบบข้อความเฉพาะในรูปแบบ PDF
linktitle: ลบ XObjects ด้วยการจัดรูปแบบข้อความเฉพาะในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: ลบ XObjects ด้วยการจัดรูปแบบข้อความเฉพาะจาก PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำของเราเพื่อการจัดการเอกสารที่ราบรื่น
weight: 36
url: /th/net/pdf-watermarking-attachments/remove-xobjects-text-formatting-pdf/
---
## การแนะนำ
เอกสารลายน้ำเป็นส่วนสำคัญในการรับรองความถูกต้องและการปกป้องข้อมูลที่ละเอียดอ่อน GroupDocs.Watermark สำหรับ .NET มอบโซลูชันที่ครอบคลุมสำหรับการเพิ่ม แก้ไข และลบลายน้ำจากรูปแบบเอกสารต่างๆ ในบทช่วยสอนนี้ เราจะเจาะลึกถึงวิธีที่คุณสามารถลบ XObjects ด้วยการจัดรูปแบบข้อความเฉพาะจากเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่จำเป็นในการปฏิบัติตาม:
1. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนาที่ตั้งค่าด้วย .NET Framework Visual Studio เป็นตัวเลือกที่ยอดเยี่ยม
2.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET คุณสามารถรับได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
3.  ใบอนุญาต: เพื่อการใช้งานเต็มรูปแบบ โปรดขอรับ a[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-ใบอนุญาต/) หรือพิจารณาซื้อก[license](https://purchase.groupdocs.com/buy).
4. ตัวอย่างเอกสาร PDF: เตรียมเอกสาร PDF ตัวอย่างให้พร้อมซึ่งมี XObjects พร้อมการจัดรูปแบบข้อความเฉพาะ (เช่น ส่วนของข้อความที่เป็นสีแดง)

## นำเข้าเนมสเปซ
ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณ รายการเนมสเปซที่คุณต้องการมีดังนี้:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ
ก่อนที่คุณจะเขียนโค้ดใดๆ ให้ตั้งค่าโปรเจ็กต์ของคุณใน Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET ที่คุณต้องการ
1. สร้างโครงการใหม่: เริ่มต้นด้วยการสร้างโครงการแอปพลิเคชันคอนโซลใหม่ใน Visual Studio
2. เพิ่มข้อมูลอ้างอิง: เพิ่มข้อมูลอ้างอิงไปยังไลบรารี GroupDocs.Watermark สำหรับ .NET
## ขั้นตอนที่ 2: กำหนดเส้นทาง
ถัดไป กำหนดเส้นทางสำหรับไฟล์อินพุตและเอาต์พุตของคุณ เพื่อให้แน่ใจว่าโค้ดของคุณรู้ว่าจะหาเอกสาร PDF ได้ที่ไหน และจะบันทึกเอกสารที่แก้ไขได้ที่ไหน
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Output Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"` และ`"Your Output Directory"` ด้วยเส้นทางจริงในระบบของคุณ
## ขั้นตอนที่ 3: โหลดเอกสาร PDF
 ตอนนี้ มาโหลดเอกสาร PDF โดยใช้ GroupDocs.Watermark กัน นี้จะกระทำด้วยความช่วยเหลือของ`PdfLoadOptions` และ`Watermarker` ระดับ.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
 ที่`using` คำสั่งทำให้มั่นใจได้ว่า`Watermarker` วัตถุจะถูกกำจัดอย่างเหมาะสมเมื่อเราทำเสร็จแล้ว
## ขั้นตอนที่ 4: เข้าถึงเนื้อหา PDF
 เพื่อจัดการเนื้อหา PDF เราจำเป็นต้องได้รับไฟล์`PdfContent` วัตถุจาก`Watermarker`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
สิ่งนี้ทำให้เราสามารถเข้าถึงหน้าและองค์ประกอบภายในแต่ละหน้าของ PDF
## ขั้นตอนที่ 5: วนซ้ำผ่านเพจและ XObjects
ตอนนี้ เราต้องวนซ้ำแต่ละหน้าของ PDF จากนั้นจึงผ่าน XObject แต่ละหน้าภายในหน้าเหล่านั้น
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    for (int i = page.XObjects.Count - 1; i >= 0; i--)
    {
```
 เราวนซ้ำย้อนกลับผ่าน`XObjects` เพื่อหลีกเลี่ยงปัญหาในการลบรายการออกจากคอลเลกชัน
## ขั้นตอนที่ 6: ตรวจสอบการจัดรูปแบบข้อความและลบ XObjects
สำหรับแต่ละ XObject เราจะตรวจสอบว่ามีส่วนของข้อความที่มีการจัดรูปแบบเฉพาะหรือไม่ (เช่น สีแดง) หากเป็นเช่นนั้น เราจะลบ XObject ออกจากเพจ
```csharp
        foreach (FormattedTextFragment fragment in page.XObjects[i].FormattedTextFragments)
        {
            if (fragment.ForegroundColor.Equals(Color.Red))
            {
                page.XObjects.RemoveAt(i);
                break;
            }
        }
    }
}
```
เพื่อให้แน่ใจว่าเฉพาะ XObjects ที่มีการจัดรูปแบบข้อความที่ระบุเท่านั้นที่จะถูกลบออก
## ขั้นตอนที่ 7: บันทึก PDF ที่แก้ไขแล้ว
สุดท้าย ให้บันทึกเอกสาร PDF ที่แก้ไขแล้วไปยังเส้นทางไฟล์เอาต์พุตที่ระบุ
```csharp
    watermarker.Save(outputFileName);
}
```
เสร็จสิ้นกระบวนการลบ XObjects ที่มีการจัดรูปแบบข้อความเฉพาะออกจากเอกสาร PDF

## บทสรุป
ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถลบ XObjects ด้วยการจัดรูปแบบข้อความเฉพาะจากเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ได้อย่างมีประสิทธิภาพ ไลบรารีอันทรงพลังนี้ไม่เพียงแต่ทำให้งานลายน้ำง่ายขึ้น แต่ยังมอบความสามารถที่แข็งแกร่งสำหรับการจัดการเอกสารอีกด้วย สำหรับเอกสารรายละเอียดเพิ่มเติม โปรดไปที่[GroupDocs.Watermark สำหรับเอกสาร .NET](https://tutorials.groupdocs.com/Watermark/net/) - หากคุณประสบปัญหาใด ๆ หรือมีคำถามใด ๆ[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19) เป็นสถานที่ที่ดีเยี่ยมในการขอความช่วยเหลือ
## คำถามที่พบบ่อย
### ฉันสามารถลบ XObjects ที่มีรูปแบบข้อความอื่นได้หรือไม่
ได้ คุณสามารถแก้ไขโค้ดเพื่อตรวจสอบแอตทริบิวต์การจัดรูปแบบข้อความต่างๆ เช่น ขนาดแบบอักษร ลักษณะแบบอักษร หรือสี
### เป็นไปได้หรือไม่ที่จะประมวลผลเอกสารรูปแบบอื่นด้วย GroupDocs.Watermark
อย่างแน่นอน! GroupDocs.Watermark รองรับรูปแบบเอกสารหลากหลาย รวมถึง DOCX, PPTX และอื่นๆ
### ฉันจะทดสอบการทำงานโดยไม่มีใบอนุญาตได้อย่างไร
 คุณสามารถขอ[ทดลองฟรี](https://releases.groupdocs.com/) หรือได้รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อทดสอบการทำงานเต็มรูปแบบของ GroupDocs.Watermark
### จะเกิดอะไรขึ้นหากฉันประสบปัญหาขณะใช้งานห้องสมุด?
 ที่[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19) เป็นแหล่งข้อมูลที่มีประโยชน์ซึ่งคุณสามารถถามคำถามและรับความช่วยเหลือจากชุมชน GroupDocs และทีมสนับสนุน
### ฉันสามารถทำให้กระบวนการใส่ลายน้ำเป็นอัตโนมัติได้หรือไม่?
ใช่ คุณสามารถทำให้กระบวนการใส่ลายน้ำเป็นอัตโนมัติได้โดยการผสานรวม GroupDocs.Watermark เข้ากับขั้นตอนการทำงานของคุณ และใช้สคริปต์หรือแอปพลิเคชันเพื่อจัดการการประมวลผลเอกสารโดยอัตโนมัติ