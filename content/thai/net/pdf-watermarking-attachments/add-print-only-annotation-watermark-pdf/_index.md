---
title: เพิ่มลายน้ำคำอธิบายประกอบพิมพ์เฉพาะลงใน PDF
linktitle: เพิ่มลายน้ำคำอธิบายประกอบพิมพ์เฉพาะลงใน PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำคำอธิบายประกอบสำหรับการพิมพ์เท่านั้นลงใน PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ปรับปรุงความปลอดภัยของเอกสารและการสร้างแบรนด์ได้อย่างง่ายดาย
weight: 13
url: /th/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# เพิ่มลายน้ำคำอธิบายประกอบพิมพ์เฉพาะลงใน PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกกระบวนการเพิ่มลายน้ำคำอธิบายประกอบสำหรับการพิมพ์เท่านั้นลงใน PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET การใส่ลายน้ำในเอกสารเป็นส่วนสำคัญของการรักษาความปลอดภัยของเอกสารและการสร้างแบรนด์ และ GroupDocs.Watermark มอบโซลูชันที่ราบรื่นสำหรับนักพัฒนา .NET เพื่อให้บรรลุเป้าหมายนี้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- GroupDocs.Watermark สำหรับไลบรารี .NET ที่ติดตั้งในโครงการของคุณ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณนำเข้าเนมสเปซที่จำเป็น:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
 ขั้นแรก คุณต้องโหลดเอกสาร PDF ที่คุณต้องการใส่ลายน้ำ แทนที่`"Your Document Path"` พร้อมเส้นทางไปยังไฟล์ PDF ของคุณและ`"Your Document Directory"` ด้วยไดเร็กทอรีที่คุณต้องการบันทึกไฟล์เอาต์พุต
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสลายน้ำจะถูกเพิ่มที่นี่
}
```
## ขั้นตอนที่ 2: เพิ่มลายน้ำ
จากนั้น สร้างวัตถุลายน้ำข้อความด้วยข้อความและแบบอักษรที่ต้องการ ชุด`isPrintOnly` ถึง`true` เพื่อให้แน่ใจว่าลายน้ำจะมองเห็นได้เฉพาะเมื่อพิมพ์เอกสารเท่านั้น ไม่ใช่ในโหมดดู
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกลายน้ำ
กำหนดตัวเลือกสำหรับลายน้ำ เช่น ดัชนีหน้าที่ควรจะเพิ่มลายน้ำ และระบุว่าเป็นคำอธิบายประกอบสำหรับการพิมพ์เท่านั้น
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## ขั้นตอนที่ 4: ใช้ลายน้ำ
เพิ่มลายน้ำให้กับเอกสารโดยใช้ตัวเลือกที่ระบุและบันทึกไฟล์เอาต์พุต
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำคำอธิบายประกอบสำหรับการพิมพ์เท่านั้นลงในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนาสามารถเพิ่มความปลอดภัยของเอกสารและการสร้างแบรนด์ได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย เช่น Word, Excel, PowerPoint และรูปภาพ
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
แน่นอนว่า GroupDocs.Watermark มีตัวเลือกมากมายในการปรับแต่งข้อความลายน้ำ แบบอักษร สี ขนาด และการวางตำแหน่ง
### GroupDocs.Watermark มีความสามารถในการประมวลผลเป็นชุดหรือไม่
แน่นอน นักพัฒนาสามารถใส่ลายน้ำให้กับเอกสารหลายชุดพร้อมกันได้โดยใช้คุณสมบัติการประมวลผลเป็นชุด
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
ใช่ คุณสามารถเข้าถึง GroupDocs.Watermark เวอร์ชันทดลองใช้ฟรีได้จากลิงก์ที่ให้ไว้
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Watermark ได้อย่างไร
คุณสามารถขอความช่วยเหลือด้านเทคนิคได้จากฟอรัม GroupDocs.Watermark ตามลิงก์สนับสนุนที่ให้ไว้