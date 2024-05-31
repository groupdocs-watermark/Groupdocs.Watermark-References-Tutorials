---
title: แทนที่ข้อความสำหรับรูปร่างเฉพาะในเอกสาร Word
linktitle: แทนที่ข้อความสำหรับรูปร่างเฉพาะในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีแทนที่ข้อความสำหรับรูปร่างเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเรา
type: docs
weight: 35
url: /th/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Watermark สำหรับ .NET เพื่อแทนที่ข้อความสำหรับรูปร่างเฉพาะในเอกสาร Word GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งมีคุณสมบัติมากมายสำหรับการทำงานกับลายน้ำในรูปแบบเอกสารต่างๆ รวมถึงเอกสาร Word
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสาร Word ที่คุณต้องการแทนที่ข้อความสำหรับรูปร่างเฉพาะ
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วยเครื่องมือและการขึ้นต่อกันที่จำเป็น

## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นสำหรับการทำงานกับ GroupDocs.Watermark สำหรับ .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณอยู่ที่นี่
}
```
 ในขั้นตอนนี้ เราระบุเส้นทางไปยังเอกสาร Word และสร้างอินสแตนซ์ของ`WordProcessingLoadOptions` เพื่อโหลดเอกสาร
## ขั้นตอนที่ 2: รับเนื้อหาเอกสาร
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 ที่นี่เราดึงเนื้อหาของเอกสาร Word โดยใช้`GetContent<T>()` วิธีการของ`Watermarker`คลาส โดยระบุประเภทเป็น`WordProcessingContent`.
## ขั้นตอนที่ 3: แทนที่ข้อความสำหรับรูปร่างเฉพาะ
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
ในขั้นตอนนี้ เราจะวนซ้ำแต่ละรูปร่างในเอกสาร หากรูปร่างมีข้อความที่ระบุ ("ข้อความบางส่วน" ในตัวอย่างนี้) เราจะแทนที่ด้วยข้อความที่ต้องการ ("ข้อความอื่น")
## ขั้นตอนที่ 4: บันทึกเอกสาร
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
สุดท้าย เราจะบันทึกเอกสารที่แก้ไขไปยังไดเร็กทอรีที่ระบุ

## บทสรุป
GroupDocs.Watermark สำหรับ .NET นำเสนอวิธีที่สะดวกและมีประสิทธิภาพในการจัดการกับลายน้ำในเอกสาร Word ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถแทนที่ข้อความสำหรับรูปร่างที่ต้องการได้อย่างง่ายดาย โดยให้ความยืดหยุ่นและตัวเลือกการปรับแต่งตามความต้องการในการประมวลผลเอกสารของคุณ
## คำถามที่พบบ่อย
### ฉันสามารถแทนที่ข้อความสำหรับรูปร่างในรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ คุณสามารถแทนที่ข้อความสำหรับรูปร่างในรูปแบบต่างๆ ได้โดยใช้วิธีการที่คล้ายกัน
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
คุณสามารถรับการสนับสนุนทางเทคนิคได้โดยไปที่ฟอรัม GroupDocs[ที่นี่](https://forum.groupdocs.com/c/watermark/19).
### ฉันจำเป็นต้องมีใบอนุญาตชั่วคราวเพื่อใช้ GroupDocs.Watermark สำหรับ .NET หรือไม่
 หากคุณต้องการคุณสมบัติเพิ่มเติมหรือการใช้งานแบบขยาย คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะซื้อใบอนุญาตฉบับเต็มสำหรับ GroupDocs.Watermark สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตฉบับสมบูรณ์ได้จากเว็บไซต์ GroupDocs[ที่นี่](https://purchase.groupdocs.com/buy).