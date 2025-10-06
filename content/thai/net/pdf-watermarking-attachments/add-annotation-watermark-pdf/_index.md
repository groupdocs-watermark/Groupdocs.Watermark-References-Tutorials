---
title: เพิ่มลายน้ำคำอธิบายประกอบลงใน PDF
linktitle: เพิ่มลายน้ำคำอธิบายประกอบลงใน PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำคำอธิบายประกอบให้กับเอกสาร PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปรับปรุงการสร้างแบรนด์เอกสารและความปลอดภัยได้อย่างง่ายดาย
weight: 10
url: /th/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
type: docs
---
# เพิ่มลายน้ำคำอธิบายประกอบลงใน PDF

## การแนะนำ
ในขอบเขตของการจัดการเอกสาร การเพิ่มลายน้ำให้กับไฟล์ PDF ถือเป็นส่วนสำคัญ โดยเฉพาะอย่างยิ่งสำหรับวัตถุประสงค์ในการสร้างแบรนด์ ความปลอดภัย และการระบุเอกสาร GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งอำนวยความสะดวกในการรวมลายน้ำเข้ากับรูปแบบเอกสารต่างๆ รวมถึง PDF ได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะเจาะลึกกระบวนการเพิ่มลายน้ำคำอธิบายประกอบให้กับเอกสาร PDF ทีละขั้นตอน โดยใช้ฟังก์ชันที่ได้รับจาก GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะดำเนินการบทช่วยสอนต่อ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสม เช่น Visual Studio หรือ .NET IDE อื่น ๆ
3. ความเข้าใจพื้นฐานของ C#: แนะนำให้คุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C#

## การนำเข้าเนมสเปซที่จำเป็น
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
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
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## ขั้นตอนที่ 3: เพิ่มลายน้ำข้อความ
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## ขั้นตอนที่ 4: เพิ่มลายน้ำรูปภาพ
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## ขั้นตอนที่ 5: บันทึกเอกสารด้วยลายน้ำ
```csharp
	watermarker.Save(outputFileName);
}
```

## บทสรุป
โดยสรุป GroupDocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่ครอบคลุมสำหรับการเพิ่มลายน้ำคำอธิบายประกอบให้กับเอกสาร PDF โดยทางโปรแกรม ด้วยการทำตามขั้นตอนที่ระบุไว้ ผู้ใช้สามารถรวมลายน้ำข้อความและรูปภาพลงในไฟล์ PDF ได้อย่างราบรื่น ซึ่งจะช่วยปรับปรุงการสร้างแบรนด์และความปลอดภัยในเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
อย่างแน่นอน! GroupDocs.Watermark มีตัวเลือกการปรับแต่งมากมายสำหรับลายน้ำทั้งข้อความและรูปภาพ ทำให้ผู้ใช้สามารถปรับขนาด ตำแหน่ง ความทึบ และพารามิเตอร์อื่นๆ ได้
### GroupDocs.Watermark เหมาะสำหรับการประมวลผลเอกสารเป็นชุดหรือไม่
แน่นอน! GroupDocs.Watermark นำเสนอความสามารถในการประมวลผลเป็นชุดที่มีประสิทธิภาพ ทำให้ผู้ใช้สามารถใส่ลายน้ำกับเอกสารหลายชุดพร้อมกันได้
### GroupDocs.Watermark รองรับการพัฒนา .NET Core หรือไม่
ใช่ GroupDocs.Watermark รองรับ .NET Core ช่วยให้นักพัฒนาสามารถรวมฟังก์ชันการใส่ลายน้ำเข้ากับแอปพลิเคชันข้ามแพลตฟอร์มได้
### มีการสนับสนุนด้านเทคนิคสำหรับผู้ใช้ GroupDocs.Watermark หรือไม่
ใช่ GroupDocs ให้การสนับสนุนด้านเทคนิคอย่างครอบคลุมผ่านทางฟอรัมเฉพาะและช่องทางการบริการลูกค้า