---
title: เพิ่มลายน้ำให้กับไฟล์แนบทั้งหมดในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับไฟล์แนบทั้งหมดในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับไฟล์แนบ PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET รักษาความปลอดภัยเอกสารของคุณด้วยลายน้ำแบบกำหนดเองได้อย่างง่ายดาย
weight: 16
url: /th/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
type: docs
---
# เพิ่มลายน้ำให้กับไฟล์แนบทั้งหมดในรูปแบบ PDF

## การแนะนำ
การเพิ่มลายน้ำให้กับไฟล์แนบ PDF อาจเป็นขั้นตอนสำคัญในการจัดการเอกสาร โดยเฉพาะอย่างยิ่งเมื่อมั่นใจในความปลอดภัยหรือการสร้างแบรนด์ GroupDocs.Watermark for .NET นำเสนอโซลูชันที่ครอบคลุมสำหรับการฝังลายน้ำลงในไฟล์ PDF ได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มลายน้ำให้กับไฟล์แนบทั้งหมดภายในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Watermark for .NET: หากคุณยังไม่ได้ดาวน์โหลด ให้ดาวน์โหลดและติดตั้ง GroupDocs.Watermark for .NET จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมด้วย Visual Studio หรือ IDE ที่เข้ากันได้กับ .NET อื่นๆ
3. เอกสาร PDF: เตรียมเอกสาร PDF ที่คุณต้องการเพิ่มลายน้ำ พร้อมด้วยไฟล์แนบที่คุณต้องการใส่ลายน้ำ

## การนำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกโค้ด ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน GroupDocs.Watermark สำหรับ .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
ขั้นแรก กำหนดเส้นทางไปยังเอกสาร PDF ที่คุณป้อน และไดเร็กทอรีที่จะบันทึกเอกสารลายน้ำ:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: เริ่มต้นตัวเลือกการโหลดและลายน้ำ
ถัดไป เริ่มต้นตัวเลือกการโหลดสำหรับเอกสาร PDF และสร้างลายน้ำข้อความ:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## ขั้นตอนที่ 3: โหลดเอกสารและไฟล์แนบ
โหลดเอกสาร PDF และวนซ้ำผ่านไฟล์แนบ:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## ขั้นตอนที่ 4: ตรวจสอบการสนับสนุนไฟล์แนบ
ตรวจสอบว่าไฟล์ที่แนบมาได้รับการสนับสนุนโดย GroupDocs.Watermark หรือไม่:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## ขั้นตอนที่ 5: เพิ่มลายน้ำให้กับไฟล์แนบ
โหลดเอกสารที่แนบมาและเพิ่มลายน้ำ:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## ขั้นตอนที่ 6: บันทึกการเปลี่ยนแปลง
สุดท้าย ให้บันทึกการเปลี่ยนแปลงในเอกสาร PDF ที่ใส่ลายน้ำ:
```csharp
    watermarker.Save(outputFileName);
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีเพิ่มลายน้ำให้กับไฟล์แนบทั้งหมดภายในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอน คุณสามารถรวมลายน้ำเข้ากับไฟล์ PDF ของคุณได้อย่างราบรื่น มั่นใจในความปลอดภัยของเอกสารและการสร้างแบรนด์
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
ใช่ คุณสามารถปรับแต่งลักษณะต่างๆ เช่น ข้อความ แบบอักษร ขนาด สี และตำแหน่งของลายน้ำได้ตามความต้องการของคุณ
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Microsoft Word, Excel, PowerPoint, Visio, Outlook และรูปภาพ
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Watermark ได้โดยการดาวน์โหลดเวอร์ชันทดลองใช้ฟรีจากเว็บไซต์
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสารเดียวได้หรือไม่
GroupDocs.Watermark ช่วยให้คุณสามารถเพิ่มลายน้ำได้หลายแบบ รวมถึงข้อความ รูปภาพ และคำอธิบายประกอบพร้อมกัน เพื่อเพิ่มความปลอดภัยให้กับเอกสารและการสร้างแบรนด์
### มีการสนับสนุนด้านเทคนิคสำหรับผู้ใช้ GroupDocs.Watermark หรือไม่
ใช่ GroupDocs ให้การสนับสนุนด้านเทคนิคอย่างครอบคลุมผ่านทางฟอรัมและช่องทางการสนับสนุนเฉพาะเพื่อช่วยเหลือผู้ใช้ในการสอบถามหรือปัญหาที่อาจพบ