---
title: ลบรูปร่างด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร Word
linktitle: ลบรูปร่างด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบรูปร่างด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำของเราเพื่อการจัดการลายน้ำอย่างมีประสิทธิภาพ
type: docs
weight: 31
url: /th/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
---
## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาจัดการลายน้ำในรูปแบบเอกสารต่างๆ โดยทางโปรแกรมได้ ในบทช่วยสอนนี้ เราจะเน้นไปที่การลบรูปร่างด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น คำแนะนำทีละขั้นตอนนี้จะช่วยให้คุณเข้าใจกระบวนการลบรูปร่างได้อย่างมีประสิทธิภาพและประสิทธิผล
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark for .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Watermark for .NET ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมด้วย Visual Studio หรือ .NET IDE อื่น ๆ ที่ติดตั้ง
3. เอกสาร Word: เตรียมเอกสาร Word ที่มีรูปร่างพร้อมการจัดรูปแบบข้อความเฉพาะที่คุณต้องการลบ

## นำเข้าเนมสเปซ
ก่อนที่เราจะเริ่มดำเนินการ เรามานำเข้าเนมสเปซที่จำเป็นก่อน:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // การใช้งานไปที่นี่
}
```
## ขั้นตอนที่ 2: รับเนื้อหาและทำซ้ำผ่านส่วนต่างๆ
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    // การใช้งานไปที่นี่
}
```
## ขั้นตอนที่ 3: วนซ้ำรูปร่างและลบออกตามการจัดรูปแบบข้อความ
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีลบรูปร่างด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและใช้ตัวอย่างโค้ดที่ให้มา นักพัฒนาจึงสามารถจัดการลายน้ำตามความต้องการได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Excel, PowerPoint, PDF และอื่นๆ
### ฉันสามารถปรับแต่งเกณฑ์ในการลบรูปร่างตามการจัดรูปแบบข้อความได้หรือไม่
อย่างแน่นอน! คุณสามารถแก้ไขโค้ดเพื่อกำหนดเป้าหมายคุณลักษณะข้อความเฉพาะ เช่น ขนาดแบบอักษร สไตล์ สี ฯลฯ
### GroupDocs.Watermark สำหรับ .NET รองรับการเพิ่มลายน้ำด้วยหรือไม่
ได้ นอกจากการลบออกแล้ว คุณยังสามารถเพิ่มลายน้ำข้อความหรือรูปภาพลงในเอกสารของคุณโดยใช้ GroupDocs.Watermark สำหรับ .NET
### มีรุ่นทดลองให้ทดสอบก่อนซื้อหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก GroupDocs[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 สำหรับความช่วยเหลือด้านเทคนิค คุณสามารถไปที่ฟอรัมสนับสนุนได้ที่[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19).