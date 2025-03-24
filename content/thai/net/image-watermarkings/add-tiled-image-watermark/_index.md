---
title: เพิ่มลายน้ำรูปภาพแบบเรียงต่อกัน
linktitle: เพิ่มลายน้ำรูปภาพแบบเรียงต่อกัน
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำรูปภาพแบบเรียงต่อกันลงในเอกสารของคุณโดยใช้ GroupDocs.Watermark สำหรับ .NET ง่าย มีประสิทธิภาพ และปรับแต่งได้
weight: 10
url: /th/net/image-watermarkings/add-tiled-image-watermark/
---
## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถเพิ่ม ลบ และค้นหาลายน้ำในรูปแบบเอกสารต่างๆ โดยทางโปรแกรม ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มลายน้ำรูปภาพแบบเรียงต่อกันลงในเอกสารของคุณโดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- เพิ่มไลบรารี GroupDocs.Watermark สำหรับ .NET ในโครงการของคุณ คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).

## นำเข้าเนมสเปซ
ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นที่จุดเริ่มต้นของไฟล์ C# ของคุณ:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
กำหนดเส้นทางของเอกสารอินพุตและไดเร็กทอรีที่คุณต้องการบันทึกเอกสารเอาต์พุต:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"` ด้วยเส้นทางสัมบูรณ์หรือสัมพัทธ์ไปยังเอกสารอินพุตของคุณ
## ขั้นตอนที่ 2: เริ่มต้นวัตถุลายน้ำ
สร้างวัตถุลายน้ำโดยใช้เส้นทางเอกสารอินพุต:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // เพิ่มลายน้ำที่นี่
}
```
## ขั้นตอนที่ 3: เพิ่มลายน้ำรูปภาพแบบเรียงต่อกัน
สร้างอินสแตนซ์ของวัตถุ ImageWatermark ด้วยเส้นทางไปยังไฟล์ภาพที่คุณต้องการใช้เป็นลายน้ำ:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // กำหนดค่าตัวเลือกไทล์
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // เพิ่มลายน้ำให้กับเอกสาร
    watermarker.Add(watermark);
    // บันทึกเอกสารที่แก้ไข
    watermarker.Save(outputFileName);
}
```
 แทนที่`"Path to Your Image"` พร้อมเส้นทางจริงไปยังไฟล์ภาพลายน้ำของคุณ

## บทสรุป
เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเพิ่มลายน้ำรูปภาพเรียงต่อกันลงในเอกสารของคุณได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ทดลองใช้ตัวเลือกและการกำหนดค่าต่างๆ เพื่อให้ได้ผลลัพธ์ตามที่ต้องการ
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสารเดียวได้หรือไม่
ได้ คุณสามารถเพิ่มลายน้ำหลายประเภทลงในเอกสารได้โดยใช้ GroupDocs.Watermark สำหรับ .NET
### GroupDocs.Watermark รองรับเอกสารทุกรูปแบบหรือไม่
GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
ใช่ คุณสามารถปรับแต่งลายน้ำในด้านต่างๆ ได้ เช่น ตำแหน่ง ขนาด การหมุน ความโปร่งใส ฯลฯ
### GroupDocs.Watermark ให้การสนับสนุนทางเทคนิคหรือไม่
 ใช่ คุณสามารถรับการสนับสนุนทางเทคนิคได้จากฟอรัม GroupDocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19).