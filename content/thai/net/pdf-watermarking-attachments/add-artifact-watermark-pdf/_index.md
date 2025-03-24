---
title: เพิ่มลายน้ำสิ่งประดิษฐ์ลงใน PDF
linktitle: เพิ่มลายน้ำสิ่งประดิษฐ์ลงใน PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำสิ่งประดิษฐ์ให้กับไฟล์ PDF ได้อย่างง่ายดายโดยใช้ Groupdocs.Watermark สำหรับ .NET ปกป้องเอกสารของคุณได้อย่างง่ายดาย
weight: 11
url: /th/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## การแนะนำ
การเพิ่มลายน้ำให้กับไฟล์ PDF เป็นส่วนสำคัญของการจัดการเอกสาร โดยเฉพาะอย่างยิ่งเมื่อต้องปกป้องทรัพย์สินทางปัญญาหรือเอกสารการสร้างแบรนด์ Groupdocs.Watermark for .NET มอบโซลูชันที่มีประสิทธิภาพสำหรับการเพิ่มลายน้ำให้กับไฟล์ PDF ได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการเพิ่มลายน้ำอาร์ติแฟกต์ให้กับไฟล์ PDF ทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง Groupdocs.Watermark สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: มีการตั้งค่าสภาพแวดล้อมการพัฒนา .NET
3. เอกสาร PDF: เตรียมเอกสาร PDF ที่คุณต้องการเพิ่มลายน้ำ
4. ไดเรกทอรีผลลัพธ์: สร้างไดเรกทอรีเพื่อบันทึกไฟล์ PDF ที่ใส่ลายน้ำ

## การนำเข้าเนมสเปซ
ขั้นแรก ให้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 2: กำหนดตัวเลือกลายน้ำ
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## ขั้นตอนที่ 3: เพิ่มลายน้ำข้อความ
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## ขั้นตอนที่ 4: เพิ่มลายน้ำรูปภาพ
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## ขั้นตอนที่ 5: บันทึก PDF ที่ใส่ลายน้ำ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำสิ่งประดิษฐ์ให้กับไฟล์ PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมฟังก์ชันลายน้ำเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น เพื่อให้มั่นใจในความปลอดภัยและความสมบูรณ์ของเอกสารของคุณ
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำข้อความได้หรือไม่
ใช่ คุณสามารถปรับแต่งลักษณะต่างๆ เช่น แบบอักษร ขนาด สี และการจัดแนวของลายน้ำข้อความได้ตามความต้องการของคุณ
### Groupdocs.Watermark รองรับการเพิ่มลายน้ำให้กับรูปแบบเอกสารอื่นๆ หรือไม่
ใช่ Groupdocs.Watermark รองรับการเพิ่มลายน้ำให้กับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ Groupdocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับปัญหาหรือข้อสงสัยที่เกี่ยวข้องกับ Groupdocs.Watermark ได้อย่างไร
 คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน Groupdocs[ที่นี่](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถใช้ Groupdocs.Watermark เพื่อวัตถุประสงค์ทางการค้าได้หรือไม่
ใช่ คุณสามารถซื้อใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์ได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).