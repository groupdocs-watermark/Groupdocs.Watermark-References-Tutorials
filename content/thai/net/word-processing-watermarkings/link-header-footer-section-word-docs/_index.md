---
title: ลิงก์ส่วนหัว/ส่วนท้ายในส่วนในเอกสาร Word
linktitle: ลิงก์ส่วนหัว/ส่วนท้ายในส่วนในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีการเชื่อมโยงส่วนหัวและส่วนท้ายภายในส่วนของเอกสาร Word อย่างมีประสิทธิภาพโดยใช้ GroupDocs.Watermark สำหรับ .NET การจัดการเอกสารและการรักษาความปลอดภัย
type: docs
weight: 26
url: /th/net/word-processing-watermarkings/link-header-footer-section-word-docs/
---
## การแนะนำ
ในโลกของการพัฒนา .NET การจัดการลายน้ำในเอกสาร Word อาจเป็นงานที่สำคัญ ไม่ว่าคุณจะปกป้องข้อมูลที่ละเอียดอ่อนหรือเพิ่มองค์ประกอบแบรนด์ก็ตาม โชคดีที่ GroupDocs.Watermark สำหรับ .NET มอบโซลูชันอันทรงพลังในการจัดการกับลายน้ำได้อย่างมีประสิทธิภาพ ในบทช่วยสอนนี้ เราจะสำรวจวิธีลิงก์ส่วนหัวและส่วนท้ายในส่วนของเอกสาร Word โดยใช้ GroupDocs.Watermark
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. GroupDocs.Watermark สำหรับ .NET: ติดตั้งไลบรารี GroupDocs.Watermark สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสาร Word ที่คุณต้องการเชื่อมโยงส่วนหัวและส่วนท้ายภายในส่วนต่างๆ ให้พร้อม

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน GroupDocs.Watermark
## ขั้นตอนที่ 1: นำเข้าเนมสเปซ
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
ตอนนี้ เรามาแบ่งขั้นตอนการเชื่อมโยงส่วนหัวและส่วนท้ายภายในส่วนของเอกสาร Word ออกเป็นหลายขั้นตอน
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 2: รับเนื้อหาเอกสาร
```csharp
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ขั้นตอนที่ 3: ลิงก์ส่วนท้ายสำหรับหน้าเลขคู่
```csharp
    // ลิงก์ส่วนท้ายสำหรับหน้าเลขคู่ไปยังส่วนท้ายที่เกี่ยวข้องในส่วนก่อนหน้า
    content.Sections[1].HeadersFooters[OfficeHeaderFooterType.FooterEven].IsLinkedToPrevious = true;
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
```csharp
    watermarker.Save(outputFileName);
}
```

## บทสรุป
โดยสรุป GroupDocs.Watermark สำหรับ .NET ช่วยให้กระบวนการเชื่อมโยงส่วนหัวและส่วนท้ายภายในส่วนของเอกสาร Word ง่ายขึ้น ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถจัดการลายน้ำและเพิ่มความปลอดภัยของเอกสารหรือการสร้างแบรนด์ได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถใช้ GroupDocs.Watermark สำหรับ .NET กับรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย เช่น Excel, PowerPoint, PDF และอื่นๆ
### GroupDocs.Watermark สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุน GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 คุณสามารถค้นหาการสนับสนุนและแหล่งข้อมูลได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/watermark/19).
### GroupDocs.Watermark สำหรับ .NET มีใบอนุญาตชั่วคราวหรือไม่
 ใช่ สามารถรับใบอนุญาตชั่วคราวได้จาก[หน้าการซื้อ GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Watermark สำหรับ .NET มีเอกสารประกอบสำหรับนักพัฒนาหรือไม่
 ใช่ มีเอกสารประกอบครบถ้วน[ที่นี่](https://reference.groupdocs.com/Watermark/net/).