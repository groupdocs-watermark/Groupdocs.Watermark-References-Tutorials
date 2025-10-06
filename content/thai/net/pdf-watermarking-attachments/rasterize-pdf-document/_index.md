---
title: แปลงเอกสาร PDF เป็นแรสเตอร์
linktitle: แปลงเอกสาร PDF เป็นแรสเตอร์
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีแรสเตอร์เอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET เพิ่มความปลอดภัยให้กับเอกสารและดึงดูดสายตาได้อย่างง่ายดาย
weight: 27
url: /th/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# แปลงเอกสาร PDF เป็นแรสเตอร์

## การแนะนำ
ในขอบเขตของการจัดการและการจัดการเอกสาร GroupDocs.Watermark สำหรับ .NET ถือเป็นเครื่องมือที่ทรงพลัง โดยนำเสนอความสามารถที่แข็งแกร่งในการเพิ่ม ลบ และค้นหาลายน้ำในรูปแบบเอกสารต่างๆ ไม่ว่าจะเป็นการปกป้องเอกสารของคุณด้วยประกาศลิขสิทธิ์ การเพิ่มโลโก้บริษัทสำหรับการสร้างแบรนด์ หรือเพียงแค่ใส่คำอธิบายประกอบเอกสารด้วยตราประทับ GroupDocs.Watermark จะทำให้กระบวนการง่ายขึ้นด้วย API ที่ใช้งานง่ายและชุดคุณสมบัติที่ครอบคลุม
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำดิ่งสู่โลกแห่งลายน้ำด้วย GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง .NET Framework
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องพัฒนาของคุณ คุณสามารถดาวน์โหลดได้จากเว็บไซต์ Microsoft หรือใช้ตัวจัดการแพ็คเกจที่คุณต้องการ
#### ขั้นตอนที่ 1: ดาวน์โหลด .NET Framework
ไปที่หน้าดาวน์โหลด Microsoft .NET Framework
#### ขั้นตอนที่ 2: ติดตั้ง .NET Framework
ทำตามคำแนะนำการติดตั้งที่ให้ไว้ในหน้าดาวน์โหลดเพื่อติดตั้ง .NET Framework บนระบบของคุณ
### 2. รับ GroupDocs.Watermark License
หากต้องการใช้ความสามารถเต็มรูปแบบของ GroupDocs.Watermark คุณต้องมีใบอนุญาตที่ถูกต้อง คุณสามารถซื้อใบอนุญาตหรือขอรับใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้
#### ขั้นตอนที่ 1: รับใบอนุญาต
ไปที่หน้าการซื้อ GroupDocs.Watermark
#### ขั้นตอนที่ 2: ซื้อหรือรับใบอนุญาตชั่วคราว
เลือกตัวเลือกใบอนุญาตที่เหมาะสมตามความต้องการของคุณ—ซื้อใบอนุญาตสำหรับการใช้งานต่อเนื่องหรือรับใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมิน

## นำเข้าเนมสเปซ
ก่อนที่คุณจะเริ่มลายน้ำในเอกสารของคุณ ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันของ GroupDocs ได้อย่างราบรื่น
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

ตอนนี้คุณได้ตั้งค่าทุกอย่างเรียบร้อยแล้ว เรามาเจาะลึกเรื่องการแรสเตอร์เอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET กันดีกว่า การแรสเตอร์จะแปลงแต่ละหน้าของเอกสาร PDF เป็นรูปแบบภาพแรสเตอร์ เช่น PNG
## ขั้นตอนที่ 1: เริ่มต้นตัวแปร
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
ตรวจสอบให้แน่ใจว่าคุณแทนที่ "เส้นทางเอกสารของคุณ" และ "ไดเรกทอรีเอกสารของคุณ" ด้วยเส้นทางจริงไปยังเอกสาร PDF ของคุณและไดเรกทอรีผลลัพธ์ที่ต้องการตามลำดับ
## ขั้นตอนที่ 2: โหลดเอกสารและเพิ่มลายน้ำ
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // เริ่มต้นลายน้ำรูปภาพหรือข้อความ
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // เพิ่มลายน้ำประเภทใดก็ได้ก่อน
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // แรสเตอร์ทุกหน้า
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // เนื้อหาของทุกหน้าจะถูกแทนที่ด้วยภาพแรสเตอร์
    watermarker.Save(outputFileName);
}
```
ในขั้นตอนนี้ เราจะโหลดเอกสาร PDF และเริ่มต้นลายน้ำข้อความด้วยคุณสมบัติที่ระบุ เช่น ข้อความ แบบอักษร การจัดตำแหน่ง มุมการหมุน ประเภทขนาด ปัจจัยมาตราส่วน และความทึบ จากนั้นเราเพิ่มลายน้ำให้กับเอกสาร ต่อไป เราจะดึงเนื้อหาของเอกสาร PDF และแรสเตอร์หน้าทั้งหมดเป็นรูปแบบ PNG ด้วยความละเอียด 100 DPI สุดท้ายนี้ เราจะบันทึกเอกสารที่แก้ไขด้วยเนื้อหาแบบแรสเตอร์

## บทสรุป
GroupDocs.Watermark for .NET นำเสนอโซลูชันที่ครอบคลุมสำหรับการเพิ่มลายน้ำให้กับรูปแบบเอกสารต่างๆ ได้อย่างง่ายดาย ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถแรสเตอร์เอกสาร PDF ได้อย่างมีประสิทธิภาพ และปรับปรุงความปลอดภัยและรูปลักษณ์ที่สวยงาม
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Microsoft Word, Excel, PowerPoint, Visio, Outlook และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำที่เพิ่มโดยใช้ GroupDocs.Watermark ได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark มีตัวเลือกมากมายสำหรับการปรับแต่งคุณสมบัติของลายน้ำ เช่น ข้อความ แบบอักษร สี ขนาด ความทึบ การหมุน และตำแหน่ง
### GroupDocs.Watermark รองรับการประมวลผลเป็นชุดหรือไม่
ใช่ คุณสามารถประมวลผลเอกสารหลายชุดในโหมดแบทช์ได้อย่างง่ายดายโดยใช้ GroupDocs ซึ่งช่วยประหยัดเวลาและความพยายามในการใส่ลายน้ำให้กับไฟล์ชุดใหญ่
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
ใช่ คุณสามารถดาวน์โหลด GroupDocs.Watermark เวอร์ชันทดลองใช้ฟรีได้จากเว็บไซต์เพื่อประเมินคุณสมบัติต่างๆ ก่อนตัดสินใจซื้อ
### ฉันจะรับความช่วยเหลือได้อย่างไรหากฉันพบปัญหาหรือมีคำถามเกี่ยวกับ GroupDocs.Watermark
คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Watermark เพื่อขอความช่วยเหลือจากชุมชนหรือติดต่อทีมสนับสนุน GroupDocs เพื่อขอความช่วยเหลือ