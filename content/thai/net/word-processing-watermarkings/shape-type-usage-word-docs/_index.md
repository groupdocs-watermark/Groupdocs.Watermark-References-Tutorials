---
title: การใช้ประเภทรูปร่างในเอกสาร Word
linktitle: การใช้ประเภทรูปร่างในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีจัดการรูปร่างในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET บทช่วยสอนนี้ให้คำแนะนำสำหรับการประมวลผลเอกสารอย่างมีประสิทธิภาพ
weight: 37
url: /th/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ประเภทรูปร่างในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET รูปร่างในเอกสาร Word อาจแตกต่างกัน และการทำความเข้าใจวิธีจัดการอาจเป็นสิ่งสำคัญสำหรับงานประมวลผลเอกสารต่างๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. เส้นทางเอกสาร: เตรียมเอกสาร Word ให้พร้อมสำหรับการประมวลผล
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมด้วยการรองรับ .NET Framework

## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้จะให้การเข้าถึงคลาสและวิธีการที่จำเป็นในการทำงานกับเอกสาร Word
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
เริ่มต้นด้วยการโหลดเอกสาร Word ลงในวัตถุลายน้ำ ตรวจสอบให้แน่ใจว่าได้ระบุเส้นทางของเอกสารและตัวเลือกเพิ่มเติมใดๆ ที่จำเป็นในระหว่างกระบวนการโหลด
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสการประมวลผลเอกสารอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: เข้าถึงเนื้อหาเอกสาร
 เข้าถึงเนื้อหาของเอกสาร Word ที่โหลดโดยใช้`GetContent<WordProcessingContent>()` วิธี. ซึ่งจะทำให้สามารถเข้าถึงส่วน ย่อหน้า และรูปร่างที่มีอยู่ในเอกสารได้
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ขั้นตอนที่ 3: วนซ้ำส่วนและรูปร่าง
วนซ้ำแต่ละส่วนและรูปร่างภายในเอกสารเพื่อตรวจสอบและจัดการตามที่ต้องการ
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // รหัสการจัดการรูปร่างอยู่ที่นี่
    }
}
```
## ขั้นตอนที่ 4: ตรวจสอบประเภทรูปร่าง
ภายในลูป ให้ตรวจสอบประเภทรูปร่างเฉพาะโดยใช้`ShapeType` คุณสมบัติ. ตัวอย่างนี้สาธิตการระบุและการจัดการรูปร่างโค้งมนของมุมทแยงมุม
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // โค้ดการจัดการเฉพาะรูปร่างอยู่ที่นี่
}
```
## ขั้นตอนที่ 5: จัดการรูปร่าง
ดำเนินการต่างๆ เช่น การเพิ่มข้อความ การปรับเปลี่ยนการจัดรูปแบบ หรือใช้การเปลี่ยนแปลงภาพกับรูปร่างที่ระบุ
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
เมื่อทำการแก้ไขที่จำเป็นทั้งหมดแล้ว ให้บันทึกเอกสารพร้อมกับการเปลี่ยนแปลงที่นำไปใช้กับไฟล์เอาต์พุตที่ระบุ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
การจัดการรูปร่างในเอกสาร Word อาจจำเป็นสำหรับงานประมวลผลเอกสารต่างๆ ด้วย GroupDocs.Watermark สำหรับ .NET คุณสามารถระบุ ปรับเปลี่ยน และจัดการรูปร่างเพื่อให้ตรงตามความต้องการของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### GroupDocs.Watermark สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/).
### GroupDocs.Watermark สำหรับ .NET ให้การสนับสนุนทางเทคนิคหรือไม่
 ใช่ คุณสามารถขอความช่วยเหลือและมีส่วนร่วมกับชุมชนผ่านทาง[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถปรับแต่งกระบวนการใส่ลายน้ำให้เหมาะกับข้อกำหนดเฉพาะของเอกสารได้หรือไม่
แน่นอนว่า GroupDocs.Watermark สำหรับ .NET มีตัวเลือกการปรับแต่งที่หลากหลายเพื่อปรับแต่งกระบวนการใส่ลายน้ำตามความต้องการของคุณ
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[หน้าซื้อใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อวัตถุประสงค์ในการทดสอบและประเมินผล