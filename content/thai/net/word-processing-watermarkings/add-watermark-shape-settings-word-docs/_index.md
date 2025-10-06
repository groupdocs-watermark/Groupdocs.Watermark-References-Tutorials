---
title: เพิ่มลายน้ำด้วยการตั้งค่ารูปร่างในเอกสาร Word
linktitle: เพิ่มลายน้ำด้วยการตั้งค่ารูปร่างในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำด้วยการตั้งค่ารูปร่างให้กับเอกสาร Word โดยใช้ GroupDocs สำหรับ .NET ปกป้องเอกสารของคุณอย่างมีประสิทธิภาพ
weight: 20
url: /th/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# เพิ่มลายน้ำด้วยการตั้งค่ารูปร่างในเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการเพิ่มลายน้ำพร้อมการตั้งค่ารูปร่างให้กับเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  ติดตั้ง GroupDocs.Watermark สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
3. ความเข้าใจในการประมวลผลเอกสาร Word

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็น
```csharp
using GroupDocs.Watermark.Common;
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
    // รหัสเพิ่มลายน้ำอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: เพิ่มลายน้ำ
 ยกตัวอย่าง`TextWatermark` วัตถุและระบุข้อความที่คุณต้องการใช้เป็นลายน้ำ
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## ขั้นตอนที่ 3: ปรับแต่งการตั้งค่าลายน้ำ
ตั้งค่าต่างๆ สำหรับลายน้ำ เช่น การจัดแนว มุมการหมุน สี และความทึบ
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## ขั้นตอนที่ 4: กำหนดตัวเลือกส่วนลายน้ำ
กำหนดตัวเลือกสำหรับส่วนลายน้ำ เช่น ชื่อรูปร่างและข้อความแสดงแทน
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## ขั้นตอนที่ 5: เพิ่มลายน้ำลงในเอกสาร
เพิ่มลายน้ำให้กับเอกสารด้วยตัวเลือกที่ระบุ
```csharp
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
บันทึกเอกสารด้วยการเพิ่มลายน้ำ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
การเพิ่มลายน้ำพร้อมการตั้งค่ารูปร่างให้กับเอกสาร Word โดยใช้ GroupDocs ลายน้ำสำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อน ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถปกป้องเอกสารของคุณด้วยลายน้ำแบบกำหนดเองได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสารเดียวกันได้หรือไม่
ได้ คุณสามารถเพิ่มลายน้ำหลายลายด้วยการตั้งค่าที่แตกต่างกันลงในเอกสารเดียวกันได้
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารหลากหลาย รวมถึง Excel, PowerPoint, PDF และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำเพิ่มเติมได้หรือไม่
แน่นอน คุณสามารถปรับเปลี่ยนพารามิเตอร์ต่างๆ เช่น ขนาดตัวอักษร สไตล์ สี และตำแหน่งให้เหมาะกับความต้องการของคุณได้
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Watermark ได้ที่ไหน
 คุณสามารถค้นหาการสนับสนุนและถามคำถามได้ในฟอรัม GroupDocs[ที่นี่](https://forum.groupdocs.com/c/watermark/19).