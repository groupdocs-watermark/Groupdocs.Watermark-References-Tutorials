---
title: เพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word
linktitle: เพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word โดยใช้ GroupDocs ปกป้องเนื้อหาของคุณได้อย่างง่ายดาย
weight: 14
url: /th/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---

# เพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word

## การแนะนำ
การใส่ลายน้ำในเอกสารเป็นส่วนสำคัญของการรักษาความปลอดภัยของเอกสารและการสร้างแบรนด์ ในบทช่วยสอนนี้ เราจะสำรวจวิธีเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio IDE แล้ว
- GroupDocs.Watermark สำหรับ .NET ติดตั้งในโครงการของคุณ

## การนำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกโค้ด ตรวจสอบให้แน่ใจว่าคุณนำเข้าเนมสเปซที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 2: เพิ่มลายน้ำ
```csharp
// กำหนดข้อความและสไตล์ลายน้ำ
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// เพิ่มลายน้ำในหน้าสุดท้าย
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## ขั้นตอนที่ 3: บันทึกเอกสาร
```csharp
// บันทึกเอกสารที่มีลายน้ำ
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถปกป้องเอกสารของคุณและเพิ่มองค์ประกอบการสร้างตราสินค้าได้อย่างมีประสิทธิภาพตามต้องการ
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งข้อความและสไตล์ของลายน้ำได้หรือไม่
ใช่ คุณสามารถปรับแต่งข้อความ แบบอักษร ขนาด สี และตำแหน่งของลายน้ำได้ตามความต้องการของคุณ
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารอื่นๆ หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, PDF และอีกมากมาย
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสารเดียวได้หรือไม่
แน่นอน คุณสามารถเพิ่มลายน้ำหลายลายพร้อมเนื้อหาและสไตล์ที่แตกต่างกันลงในเอกสารเดียวกันได้
### GroupDocs.Watermark สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Watermark ได้ด้วยการทดลองใช้ฟรี เพียงไปที่ลิงก์ที่ให้ไว้เพื่อเริ่มต้น[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Watermark ได้ที่ไหน
 คุณสามารถค้นหาแหล่งข้อมูลที่เป็นประโยชน์และรับการสนับสนุนทางเทคนิคได้จาก[ที่นี่](https://forum.groupdocs.com/c/watermark/19)ฟอรัม GroupDocs.Watermark เยี่ยมชมลิงค์ที่ให้ไว้เพื่อเข้าร่วมชุมชน