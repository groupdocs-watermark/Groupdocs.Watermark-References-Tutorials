---
title: ตั้งค่าส่วนหัว/ส่วนท้ายของหน้าแรกที่แตกต่างกันในเอกสาร Word
linktitle: ตั้งค่าส่วนหัว/ส่วนท้ายของหน้าแรกที่แตกต่างกันในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีตั้งค่าส่วนหัวและส่วนท้ายต่างๆ บนหน้าแรกของเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET
type: docs
weight: 36
url: /th/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---
## การแนะนำ
ในขอบเขตของการจัดการและการจัดการเอกสาร GroupDocs.Watermark สำหรับ .NET กลายเป็นเครื่องมืออันทรงพลังที่นำเสนอการผสานรวมที่ราบรื่นและฟังก์ชันการทำงานที่แข็งแกร่งสำหรับการใส่ลายน้ำในเอกสาร ข้อกำหนดทั่วไปอย่างหนึ่งในการประมวลผลเอกสารคือการตั้งค่าส่วนหัวและส่วนท้ายที่แตกต่างกันบนหน้าแรกของเอกสาร Word บทช่วยสอนนี้จะอธิบายกระบวนการในการบรรลุภารกิจนี้โดยใช้ GroupDocs.Watermark สำหรับ .NET โดยแจกแจงแต่ละขั้นตอนออกเป็นส่วนต่างๆ ที่เข้าใจได้ง่าย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำดิ่งสู่การนำไปปฏิบัติ ตรวจสอบให้แน่ใจว่าเป็นไปตามข้อกำหนดเบื้องต้นต่อไปนี้:
1.  การติดตั้ง GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. การเตรียมเอกสาร: เตรียมเอกสาร Word ให้พร้อมซึ่งต้องมีการตั้งค่าส่วนหัวและส่วนท้ายที่แตกต่างกันในหน้าแรก

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นสำหรับการใช้ GroupDocs.Watermark สำหรับฟังก์ชัน .NET:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
ในขั้นตอนนี้ เรากำหนดเส้นทางไปยังเอกสารที่ต้องดำเนินการ และระบุชื่อไฟล์เอาต์พุตและไดเร็กทอรี นอกจากนี้ เรายังเริ่มต้น a`Watermarker` วัตถุที่มีเส้นทางเอกสารและตัวเลือกการโหลด
## ขั้นตอนที่ 2: เข้าถึงเนื้อหาเอกสาร
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 ที่นี่เราดึงเนื้อหาของเอกสาร Word โดยใช้`GetContent<T>()` วิธีการของ`Watermarker` วัตถุ โดยระบุประเภทของเนื้อหาเป็น`WordProcessingContent`.
## ขั้นตอนที่ 3: กำหนดค่าการตั้งค่าหน้า
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
ในขั้นตอนนี้ เรากำหนดค่าตัวเลือกการตั้งค่าเพจเพื่อเปิดใช้งานส่วนหัวและส่วนท้ายที่แตกต่างกันสำหรับหน้าแรก (`DifferentFirstPageHeaderFooter`) เช่นเดียวกับหน้าคี่และหน้าคู่ (`OddAndEvenPagesHeaderFooter`-
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
```csharp
watermarker.Save(outputFileName);
```
 สุดท้าย เราจะบันทึกการแก้ไขที่ทำกับเอกสารโดยการเรียก`Save()` วิธีการของ`Watermarker` วัตถุส่งชื่อไฟล์เอาต์พุต

## บทสรุป
GroupDocs.Watermark สำหรับ .NET มอบโซลูชันที่ตรงไปตรงมาสำหรับการตั้งค่าส่วนหัวและส่วนท้ายต่างๆ บนหน้าแรกของเอกสาร Word ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ ผู้ใช้สามารถจัดการเนื้อหาเอกสารตามความต้องการได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
ใช่ ผู้ใช้สามารถทดลองใช้ GroupDocs.Watermark สำหรับ .NET ได้ฟรีจาก[หน้าเผยแพร่](https://releases.groupdocs.com/).
### GroupDocs.Watermark สำหรับ .NET มีการสนับสนุนทางเทคนิคหรือไม่
 ใช่ การสนับสนุนด้านเทคนิคสำหรับ GroupDocs สำหรับ .NET มีให้ผ่านทาง[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถซื้อใบอนุญาตชั่วคราวสำหรับการใช้งานระยะสั้นได้หรือไม่
 ใช่ สามารถรับสิทธิ์การใช้งานชั่วคราวสำหรับ GroupDocs สำหรับ .NET ได้[หน้าซื้อใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะหาเอกสารที่ครอบคลุมสำหรับ GroupDocs.Watermark for .NET ได้ที่ไหน
 เอกสารรายละเอียดสำหรับ GroupDocs.Watermark สำหรับ .NET มีอยู่ใน[หน้าอ้างอิง](https://reference.groupdocs.com/Watermark/net/).