---
title: เลิกป้องกันเอกสารใน Word Docs
linktitle: เลิกป้องกันเอกสารใน Word Docs
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีป้องกันเอกสาร Word อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเรา
type: docs
weight: 38
url: /th/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับลายน้ำในรูปแบบเอกสารที่หลากหลาย รวมถึงเอกสาร Word ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการยกเลิกการป้องกันเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้นพัฒนา .NET คำแนะนำทีละขั้นตอนนี้จะช่วยให้คุณทำงานสำเร็จได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark for .NET: คุณต้องมี GroupDocs.Watermark for .NET API ติดตั้งอยู่ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET รวมถึง Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้
3. เอกสาร Word: เตรียมเอกสาร Word ที่คุณต้องการยกเลิกการป้องกันให้พร้อมในระบบไฟล์ของคุณ

## นำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกโค้ด คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังโปรเจ็กต์ .NET ของคุณ ซึ่งช่วยให้คุณเข้าถึงฟังก์ชันการทำงานที่ GroupDocs.Watermark สำหรับ .NET มอบให้ได้อย่างราบรื่น
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: ระบุเส้นทางเอกสาร
กำหนดเส้นทางไปยังเอกสาร Word ที่คุณต้องการยกเลิกการป้องกัน
```csharp
string documentPath = "Your Document Path";
```
 แทนที่`"Your Document Path"` ด้วยเส้นทางจริงไปยังเอกสาร Word ของคุณ
## ขั้นตอนที่ 2: ตั้งชื่อไฟล์เอาท์พุต
ระบุไดเร็กทอรีที่คุณต้องการบันทึกเอกสารที่ไม่มีการป้องกัน และระบุชื่อสำหรับไฟล์เอาต์พุต
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Directory"` ด้วยเส้นทางไดเร็กทอรีที่คุณต้องการบันทึกไฟล์เอาต์พุต
## ขั้นตอนที่ 3: โหลดเอกสารพร้อมตัวเลือก
 สร้างอินสแตนซ์ของ`WordProcessingLoadOptions` เพื่อโหลดเอกสาร Word พร้อมตัวเลือกเฉพาะ
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## ขั้นตอนที่ 4: ยกเลิกการป้องกันเอกสาร
 ยกตัวอย่าง`Watermarker` คลาสพร้อมเส้นทางเอกสารและตัวเลือกการโหลด จากนั้นรับเนื้อหาของเอกสารเป็น WordProcessingContent และยกเลิกการป้องกัน
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## บทสรุป
เมื่อทำตามขั้นตอนเหล่านี้ คุณสามารถยกเลิกการป้องกันเอกสาร Word ได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET API นี้มอบวิธีที่ตรงไปตรงมาในการจัดการกับลายน้ำและปกป้องเอกสารของคุณอย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET Framework 2.0 และเวอร์ชันที่ใหม่กว่า รวมถึง .NET Core และ .NET Standard
### ฉันสามารถใช้ลายน้ำกับเอกสารในรูปแบบอื่นนอกเหนือจาก Word ได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถรับเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 ท่านสามารถเยี่ยมชมได้ที่[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19) สำหรับความช่วยเหลือด้านเทคนิคและการสนับสนุนชุมชน
### ฉันสามารถซื้อใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
 ใช่ คุณสามารถซื้อใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).