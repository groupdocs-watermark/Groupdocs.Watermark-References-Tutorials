---
title: แทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word
linktitle: แทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีแทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ความสามารถในการแก้ไขเอกสารของคุณได้อย่างง่ายดาย
weight: 34
url: /th/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# แทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการแทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ไลบรารีนี้มีคุณสมบัติอันทรงพลังสำหรับการทำงานกับลายน้ำ รวมถึงการแทนที่ข้อความภายในรูปร่าง
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและตั้งค่า GroupDocs.Watermark สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. เส้นทางเอกสาร: คุณควรมีเส้นทางไปยังเอกสาร Word ที่คุณต้องการแทนที่ข้อความ

## นำเข้าเนมสเปซ
ก่อนที่จะเขียนโค้ด ให้นำเข้าเนมสเปซที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
 โหลดเอกสาร Word โดยใช้ไฟล์`Watermarker` ระดับ:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณยังคงอยู่ที่นี่...
}
```
## ขั้นตอนที่ 2: รับเนื้อหาและแทนที่ข้อความ
เมื่อโหลดเอกสารแล้ว ให้รับเนื้อหาและแทนที่ข้อความภายในรูปร่าง:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## ขั้นตอนที่ 3: บันทึกเอกสาร
หลังจากแทนที่ข้อความแล้ว ให้บันทึกเอกสารที่แก้ไข:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## บทสรุป
การแทนที่ข้อความรูปร่างด้วยข้อความที่จัดรูปแบบในเอกสาร Word ทำได้ง่ายด้วย GroupDocs ลายน้ำสำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถจัดการและจัดการข้อความภายในเอกสารของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ฉันสามารถแทนที่ข้อความในเอกสารประเภทอื่นโดยใช้ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย เช่น PDF, Excel, PowerPoint และอื่นๆ
### GroupDocs.Watermark เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Watermark รองรับทั้ง .NET Framework และ .NET Core
### GroupDocs.Watermark รองรับการเพิ่มรูปภาพเป็นลายน้ำหรือไม่
GroupDocs.Watermark ช่วยให้คุณสามารถเพิ่มลายน้ำทั้งข้อความและรูปภาพลงในเอกสารของคุณได้
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำที่เพิ่มโดยใช้ GroupDocs.Watermark ได้หรือไม่
ใช่ คุณสามารถควบคุมลักษณะที่ปรากฏ ตำแหน่ง และคุณสมบัติอื่นๆ ของลายน้ำได้อย่างสมบูรณ์
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).