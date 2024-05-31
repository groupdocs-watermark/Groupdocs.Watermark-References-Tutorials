---
title: เพิ่มลายน้ำพร้อมเอฟเฟกต์ข้อความในเอกสาร Word
linktitle: เพิ่มลายน้ำพร้อมเอฟเฟกต์ข้อความในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำแบบกำหนดเองพร้อมเอฟเฟกต์ข้อความลงในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET การรักษาความปลอดภัยเอกสารและรูปลักษณ์ที่น่าดึงดูดได้อย่างง่ายดาย
type: docs
weight: 21
url: /th/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีเพิ่มลายน้ำพร้อมเอฟเฟกต์ข้อความลงในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET เมื่อทำตามคำแนะนำทีละขั้นตอนเหล่านี้ คุณจะสามารถปรับปรุงเอกสารของคุณด้วยลายน้ำที่กำหนดเองซึ่งรวมถึงเอฟเฟกต์ข้อความต่างๆ
## ข้อกำหนดเบื้องต้น
ก่อนเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. Document Path: รู้เส้นทางของเอกสาร Word ที่คุณต้องการเพิ่มลายน้ำ
3. Output Directory: มีไดเร็กทอรีที่คุณต้องการบันทึกเอกสารที่แก้ไข

## นำเข้าเนมสเปซ
ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
โหลดเอกสาร Word ที่คุณต้องการเพิ่มลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสสำหรับการเพิ่มลายน้ำอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: เพิ่มลายน้ำพร้อมเอฟเฟกต์ข้อความ
สร้างลายน้ำข้อความด้วยข้อความและแบบอักษรที่ต้องการ จากนั้นกำหนดเอฟเฟกต์ข้อความ เช่น รูปแบบของเส้น
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## ขั้นตอนที่ 3: ปรับแต่งตัวเลือกลายน้ำ
กำหนดตัวเลือกส่วนของลายน้ำ เช่น เอฟเฟกต์ข้อความ และกำหนดให้กับลายน้ำ
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
บันทึกเอกสารที่แก้ไขด้วยการเพิ่มลายน้ำ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
การเพิ่มลายน้ำพร้อมเอฟเฟกต์ข้อความลงในเอกสาร Word สามารถเพิ่มความสวยงามและการปกป้องให้กับเอกสารได้อย่างมาก ด้วย GroupDocs.Watermark สำหรับ .NET กระบวนการนี้จะมีความคล่องตัวและปรับแต่งได้ ช่วยให้คุณสร้างเอกสารที่ดูเป็นมืออาชีพได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งแบบอักษรและขนาดของข้อความลายน้ำได้หรือไม่
ได้ คุณสามารถระบุแบบอักษรและขนาดในขณะที่สร้างออบเจ็กต์ TextWatermark ได้
### เป็นไปได้ไหมที่จะเพิ่มลายน้ำหลายลายลงในเอกสารเดียว?
แน่นอนว่า GroupDocs.Watermark สำหรับ .NET รองรับการเพิ่มลายน้ำหลายแบบด้วยการตั้งค่าที่แตกต่างกันลงในเอกสารฉบับเดียว
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอีกมากมาย
### ฉันสามารถลบลายน้ำเมื่อเพิ่มลงในเอกสารได้หรือไม่
ใช่ ห้องสมุดมีวิธีการลบลายน้ำออกจากเอกสารอย่างง่ายดาย
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).