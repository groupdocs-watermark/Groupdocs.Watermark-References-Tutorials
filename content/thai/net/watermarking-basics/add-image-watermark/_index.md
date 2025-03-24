---
title: เพิ่มลายน้ำรูปภาพ
linktitle: เพิ่มลายน้ำรูปภาพ
second_title: GroupDocs.Watermark .NET API
description: เพิ่มลายน้ำรูปภาพลงในเอกสารของคุณได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปกป้องทรัพย์สินทางปัญญาของคุณได้อย่างง่ายดาย
weight: 10
url: /th/net/watermarking-basics/add-image-watermark/
---

# เพิ่มลายน้ำรูปภาพ

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกกระบวนการเพิ่มลายน้ำรูปภาพลงในเอกสารของคุณโดยใช้ GroupDocs.Watermark สำหรับ .NET เอกสารลายน้ำเป็นสิ่งจำเป็นสำหรับการปกป้องทรัพย์สินทางปัญญาและการสร้างแบรนด์ ด้วย GroupDocs.Watermark สำหรับ .NET คุณสามารถรวมลายน้ำเข้ากับรูปแบบเอกสารต่างๆ เช่น Word, Excel, PowerPoint, PDF และอื่นๆ อีกมากมายได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสารที่คุณต้องการเพิ่มลายน้ำให้พร้อม
3. รูปภาพสำหรับลายน้ำ: เตรียมไฟล์รูปภาพที่คุณต้องการใช้เป็นลายน้ำ

## นำเข้าเนมสเปซ
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## ขั้นตอนที่ 1: เริ่มต้นเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"`ด้วยเส้นทางสัมบูรณ์หรือสัมพัทธ์ไปยังเอกสารของคุณและ`"Your Document Directory"` ด้วยไดเร็กทอรีที่คุณต้องการบันทึกเอกสารลายน้ำ
## ขั้นตอนที่ 2: เปิดสตรีมเอกสารและเริ่มต้นลายน้ำ
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // กระบวนการใส่ลายน้ำจะไปที่นี่
    }
}
```
 เปิดสตรีมเอกสารโดยใช้`FileStream` และเริ่มต้นการ`Watermarker` วัตถุ.
## ขั้นตอนที่ 3: เพิ่มลายน้ำรูปภาพ
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 สร้าง`ImageWatermark` วัตถุที่มีเส้นทางไปยังไฟล์ภาพที่คุณต้องการใช้เป็นลายน้ำ ตั้งค่าการวางแนวแนวนอนและแนวตั้งของลายน้ำ
## ขั้นตอนที่ 4: บันทึกเอกสารลายน้ำ
```csharp
watermarker.Save(outputFileName);
```
บันทึกเอกสารลายน้ำไปยังไดเร็กทอรีเอาต์พุตที่ระบุด้วยชื่อไฟล์ที่ต้องการ

## บทสรุป
โดยสรุป GroupDocs.Watermark สำหรับ .NET มอบโซลูชันที่ครอบคลุมสำหรับการเพิ่มลายน้ำให้กับรูปแบบเอกสารต่างๆ ได้อย่างง่ายดาย ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณจะสามารถเพิ่มลายน้ำรูปภาพลงในเอกสารของคุณได้อย่างมีประสิทธิภาพและปกป้องทรัพย์สินทางปัญญาของคุณ
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มลายน้ำข้อความโดยใช้ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับการเพิ่มลายน้ำทั้งรูปภาพและข้อความลงในเอกสาร
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารที่แตกต่างกันหรือไม่
แน่นอนว่า GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, PDF และอีกมากมาย
### GroupDocs.Watermark สำหรับ .NET มีตัวเลือกการปรับแต่งลายน้ำหรือไม่
ใช่ คุณสามารถกำหนดลักษณะต่างๆ ของลายน้ำได้ เช่น ตำแหน่ง ขนาด ความทึบ และการหมุน
### ฉันสามารถลบลายน้ำออกจากเอกสารโดยใช้ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET มีฟังก์ชันในการตรวจจับและลบลายน้ำออกจากเอกสาร
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถใช้เวอร์ชันทดลองใช้ฟรีได้จากเว็บไซต์เพื่อสำรวจคุณสมบัติต่างๆ ก่อนซื้อ[ที่นี่](https://releases.groupdocs.com/).