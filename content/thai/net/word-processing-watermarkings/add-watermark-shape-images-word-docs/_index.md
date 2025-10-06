---
title: เพิ่มลายน้ำเพื่อกำหนดรูปร่างรูปภาพในเอกสาร Word
linktitle: เพิ่มลายน้ำเพื่อกำหนดรูปร่างรูปภาพในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำเพื่อจัดรูปร่างรูปภาพในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ปรับปรุงความปลอดภัยของเอกสารด้วยบทช่วยสอนนี้
weight: 17
url: /th/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# เพิ่มลายน้ำเพื่อกำหนดรูปร่างรูปภาพในเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีเพิ่มลายน้ำเพื่อสร้างรูปร่างให้กับรูปภาพภายในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ลายน้ำเป็นส่วนสำคัญของการปกป้องเอกสาร โดยเฉพาะอย่างยิ่งเมื่อต้องจัดการกับข้อมูลที่ละเอียดอ่อนหรือเป็นความลับ การเพิ่มลายน้ำให้กับรูปภาพทำให้คุณสามารถมั่นใจในความสมบูรณ์และความปลอดภัยของเอกสารของคุณได้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสาร Word ที่คุณต้องการเพิ่มลายน้ำ
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่คุณต้องการ
## นำเข้าเนมสเปซ
ก่อนที่จะเขียนโค้ด ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นแล้ว:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
ขั้นแรก ให้กำหนดเส้นทางไปยังเอกสารของคุณและระบุชื่อไฟล์เอาต์พุต:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำ
 ยกตัวอย่าง`Watermarker` วัตถุโดยระบุเส้นทางเอกสารและตัวเลือกการโหลดเพิ่มเติม:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // เพิ่มตรรกะการใส่ลายน้ำที่นี่
}
```
## ขั้นตอนที่ 3: สร้างลายน้ำข้อความ
กำหนดลายน้ำข้อความด้วยคุณสมบัติที่ต้องการ เช่น ข้อความ แบบอักษร การจัดตำแหน่ง การหมุน การกำหนดขนาด ฯลฯ:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ขั้นตอนที่ 4: ใช้ลายน้ำเพื่อจัดรูปร่างรูปภาพ
วนซ้ำส่วนต่างๆ ของเอกสารและรูปร่างเพื่อระบุรูปภาพรูปร่างและเพิ่มลายน้ำ:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีลายน้ำเพิ่มลงในไฟล์เอาต์พุตที่ระบุ:
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำเพื่อสร้างรูปร่างให้กับรูปภาพในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและใช้ประโยชน์จากคุณสมบัติอันทรงพลังของ GroupDocs.Watermark คุณจะสามารถเพิ่มความปลอดภัยและการปกป้องเอกสารของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของข้อความลายน้ำได้หรือไม่
ได้ คุณสามารถปรับคุณสมบัติต่างๆ ได้ เช่น แบบอักษร ขนาด สี มุมการหมุน และการจัดตำแหน่ง เพื่อปรับแต่งลายน้ำตามความต้องการของคุณ
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ GroupDocs.Watermark ให้การสนับสนุนรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### เป็นไปได้ไหมที่จะเพิ่มลายน้ำหลายลายลงในเอกสารเดียว?
แน่นอน คุณสามารถเพิ่มลายน้ำหลายลายโดยมีเนื้อหา สไตล์ และตำแหน่งที่แตกต่างกันภายในเอกสารเดียวกันได้
### ฉันสามารถลบลายน้ำออกจากเอกสารโดยใช้ GroupDocs.Watermark ได้หรือไม่
ใช่ GroupDocs.Watermark นำเสนอคุณสมบัติในการตรวจจับและลบลายน้ำออกจากเอกสารได้อย่างมีประสิทธิภาพ
### GroupDocs.Watermark มีความเข้ากันได้ข้ามแพลตฟอร์มหรือไม่
ใช่ GroupDocs.Watermark เข้ากันได้กับ .NET Framework, .NET Core และ .NET Standard ทำให้มั่นใจได้ถึงการบูรณาการอย่างราบรื่นบนแพลตฟอร์มต่างๆ