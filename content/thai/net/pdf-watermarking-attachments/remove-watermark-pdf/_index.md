---
title: ลบลายน้ำออกจาก PDF
linktitle: ลบลายน้ำออกจาก PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบลายน้ำออกจากไฟล์ PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ขั้นตอนง่ายๆ สำหรับการแก้ไขเอกสารอย่างมืออาชีพ
type: docs
weight: 34
url: /th/net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## การแนะนำ
ในยุคดิจิทัลปัจจุบัน การปกป้องเอกสารสำคัญด้วยลายน้ำถือเป็นเรื่องปกติ อย่างไรก็ตาม มีกรณีที่คุณอาจต้องลบลายน้ำออกจากไฟล์ PDF ด้วยเหตุผลหลายประการ ไม่ว่าคุณกำลังแก้ไขเอกสารหรือเพียงต้องการเวอร์ชันที่สะอาดตาสำหรับการนำเสนอ GroupDocs.Watermark สำหรับ .NET มอบโซลูชันที่ราบรื่นสำหรับการลบลายน้ำออกจากไฟล์ PDF
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกในการลบลายน้ำออกจากไฟล์ PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ IDE ที่เข้ากันได้ในระบบของคุณ
3. เอกสารที่มีลายน้ำ: เตรียมเอกสาร PDF ที่มีลายน้ำที่คุณต้องการลบ

## การนำเข้าเนมสเปซ
ในโปรเจ็กต์ C# ของคุณ ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร PDF
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
ในขั้นตอนนี้ ให้ระบุเส้นทางไปยังเอกสาร PDF ของคุณและไดเร็กทอรีที่คุณต้องการบันทึกไฟล์เอาต์พุต
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำและเกณฑ์การค้นหา
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
เริ่มต้นวัตถุ Watermarker ด้วยเส้นทางเอกสาร PDF และตัวเลือกการโหลด จากนั้น กำหนดเกณฑ์การค้นหาสำหรับลายน้ำที่คุณต้องการลบ คุณสามารถค้นหาลายน้ำตามรูปภาพหรือข้อความได้
## ขั้นตอนที่ 3: ค้นหาและลบลายน้ำ
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // ลบลายน้ำที่พบทั้งหมด
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
ค้นหาลายน้ำที่เป็นไปได้ในหน้าแรกของเอกสาร PDF ตามเกณฑ์การค้นหาที่กำหนด จากนั้น ทำซ้ำการรวบรวมลายน้ำที่เป็นไปได้และลบออกทีละรายการ สุดท้าย ให้บันทึกเอกสาร PDF ที่แก้ไขโดยไม่มีลายน้ำ

## บทสรุป
การลบลายน้ำออกจากไฟล์ PDF เป็นงานสำคัญในสถานการณ์ต่างๆ ตั้งแต่การแก้ไขเอกสารไปจนถึงการเตรียมการนำเสนอ ด้วย GroupDocs.Watermark สำหรับ .NET คุณสามารถลบลายน้ำออกจากไฟล์ PDF ได้อย่างง่ายดายโดยใช้โค้ด C# ง่ายๆ เพื่อให้มั่นใจว่าเอกสารของคุณสะอาดและเป็นมืออาชีพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ Visual Studio ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ Visual Studio ทุกเวอร์ชัน รวมถึง Visual Studio 2019 และ Visual Studio 2022
### ฉันสามารถลบลายน้ำหลายอันออกจากเอกสาร PDF เดียวโดยใช้ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
ใช่ คุณสามารถค้นหาและลบลายน้ำหลายอันออกจากเอกสาร PDF เดียวได้โดยระบุเกณฑ์การค้นหาที่เหมาะสม
### GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึงเอกสาร Word, สเปรดชีต Excel, งานนำเสนอ PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลด GroupDocs.Watermark สำหรับ .NET เวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนและความช่วยเหลือเพิ่มเติมสำหรับ GroupDocs.Watermark for .NET ได้ที่ไหน
 หากต้องการการสนับสนุนเพิ่มเติม โปรดไปที่ฟอรัม GroupDocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19).