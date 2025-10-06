---
title: เพิ่มลายน้ำข้อความ
linktitle: เพิ่มลายน้ำข้อความ
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำข้อความลงในเอกสารของคุณโดยใช้ Groupdocs ลายน้ำสำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนนี้
weight: 11
url: /th/net/watermarking-basics/add-text-watermark/
type: docs
---
# เพิ่มลายน้ำข้อความ

## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถเพิ่ม ค้นหา และลบลายน้ำออกจากรูปแบบเอกสารต่างๆ ในแอปพลิเคชัน .NET ในบทช่วยสอนนี้ เราจะเน้นที่การเพิ่มลายน้ำข้อความลงในเอกสารโดยใช้ GroupDocs.Watermark
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
2. ติดตั้ง Visual Studio บนระบบของคุณแล้ว
3.  ติดตั้ง GroupDocs.Watermark สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
กำหนดเส้นทางไปยังเอกสารอินพุตของคุณและไดเร็กทอรีเอาต์พุตที่จะบันทึกเอกสารที่มีลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"` ด้วยเส้นทางสัมบูรณ์หรือสัมพัทธ์ไปยังเอกสารอินพุตของคุณ ตัวอย่างเช่น:`@"C:\Docs\document.pdf"`- นอกจากนี้ ให้ระบุไดเร็กทอรีที่คุณต้องการบันทึกเอกสารลายน้ำ
## ขั้นตอนที่ 2: เพิ่มลายน้ำข้อความ
 ยกตัวอย่าง`Watermarker` คลาสที่มีเส้นทางเอกสารอินพุต จากนั้นให้สร้าง`TextWatermark` วัตถุด้วยการตั้งค่าข้อความและแบบอักษรที่ต้องการ
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำข้อความลงในเอกสารโดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วย API ที่ใช้งานง่าย นักพัฒนาสามารถจัดการลายน้ำในรูปแบบเอกสารต่างๆ ได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับเอกสารทุกรูปแบบหรือไม่
GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำข้อความได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ได้ เช่น แบบอักษร สี การจัดตำแหน่ง และความทึบของลายน้ำข้อความ
### GroupDocs.Watermark รองรับการลบลายน้ำออกจากเอกสารหรือไม่
ใช่ GroupDocs.Watermark มีฟังก์ชันการค้นหาและลบลายน้ำออกจากเอกสาร
### ฉันสามารถลองใช้ GroupDocs.Watermark สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Watermark ได้อย่างไร
 คุณสามารถรับการสนับสนุนทางเทคนิคได้โดยไปที่[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19).