---
title: เพิ่มไฟล์แนบลงใน PDF
linktitle: เพิ่มไฟล์แนบลงใน PDF
second_title: GroupDocs.Watermark .NET API
description: ปรับปรุงความสามารถในการจัดการเอกสาร .NET ของคุณด้วย GroupDocs.Watermark สำหรับลายน้ำและการจัดการไฟล์แนบที่ราบรื่น
weight: 12
url: /th/net/pdf-watermarking-attachments/add-attachment-pdf/
type: docs
---
# เพิ่มไฟล์แนบลงใน PDF

## การแนะนำ
ในขอบเขตของการพัฒนา .NET GroupDocs.Watermark มีความโดดเด่นในฐานะเครื่องมืออันทรงพลังสำหรับการจัดการลายน้ำ คำอธิบายประกอบ และอื่นๆ อีกมากมายภายในรูปแบบเอกสารต่างๆ ไม่ว่าคุณจะทำงานกับ PDF, เอกสาร Word หรือรูปภาพ GroupDocs.Watermark สำหรับ .NET มอบการบูรณาการที่ราบรื่นซึ่งช่วยให้นักพัฒนาสามารถจัดการเอกสารได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกถึงความซับซ้อนของการใช้ GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  การติดตั้ง: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Watermark สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[หน้าปล่อย](https://releases.groupdocs.com/Watermark/net/).
2. การเตรียมเอกสาร: เตรียมเอกสารที่คุณต้องการทำการใส่ลายน้ำหรือดำเนินการอื่นๆ ให้พร้อม
3. ความรู้พื้นฐานของ C#: ทำความคุ้นเคยกับพื้นฐานการเขียนโปรแกรม C# เนื่องจากเราจะใช้เพื่อโต้ตอบกับ GroupDocs.Watermark API

## นำเข้าเนมสเปซ
ก่อนที่จะเริ่มใช้งาน สิ่งสำคัญคือต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Watermark ด้านล่างนี้คือเนมสเปซที่จำเป็น:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 ในขั้นตอนนี้ เราระบุเส้นทางไปยังเอกสารที่เราต้องการทำงานด้วยและสร้าง`PdfLoadOptions` วัตถุสำหรับโหลดเอกสาร PDF จากนั้นเราเริ่มต้น a`Watermarker` วัตถุที่มีเส้นทางเอกสารและตัวเลือกการโหลด
## ขั้นตอนที่ 2: รับเนื้อหา PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 ที่นี่ เราได้รับเนื้อหาของเอกสาร PDF โดยใช้`GetContent<PdfContent>()` วิธี.
## ขั้นตอนที่ 3: เพิ่มไฟล์แนบ
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
ขั้นตอนนี้เกี่ยวข้องกับการเพิ่มไฟล์แนบลงในเอกสาร PDF คุณต้องระบุไบต์ ชื่อ และคำอธิบายของไฟล์แนบ
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
```csharp
watermarker.Save(outputFileName);
```
สุดท้ายนี้ เราจะบันทึกการเปลี่ยนแปลงที่ทำกับเอกสารพร้อมกับไฟล์แนบที่เพิ่มเข้ามา

## บทสรุป
GroupDocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพสำหรับการจัดการลายน้ำของเอกสารและไฟล์แนบได้อย่างราบรื่น ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถรวมฟังก์ชันลายน้ำและการแนบเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับกรอบงาน .NET ทั้งหมดหรือไม่
ใช่ GroupDocs.Watermark รองรับ .NET Framework 2.0 และสูงกว่า
### ฉันสามารถลบลายน้ำที่เพิ่มโดยใช้ GroupDocs.Watermark ได้หรือไม่
ใช่ GroupDocs.Watermark มีวิธีลบลายน้ำออกจากเอกสาร
### GroupDocs.Watermark รองรับการเข้ารหัสเอกสารหรือไม่
ใช่ GroupDocs.Watermark ช่วยให้คุณสามารถทำงานกับเอกสารที่เข้ารหัสได้
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
GroupDocs.Watermark มีตัวเลือกการปรับแต่งลายน้ำที่หลากหลาย
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/).