---
title: เพิ่มลายน้ำให้กับสิ่งประดิษฐ์ของรูปภาพในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับสิ่งประดิษฐ์ของรูปภาพในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: ปกป้องไฟล์ PDF ของคุณด้วยลายน้ำส่วนตัวโดยใช้ GroupDocs.Watermark สำหรับ .NET เพิ่มลายน้ำข้อความหรือรูปภาพให้กับสิ่งประดิษฐ์ของรูปภาพในเอกสาร PDF ได้อย่างง่ายดาย
weight: 18
url: /th/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# เพิ่มลายน้ำให้กับสิ่งประดิษฐ์ของรูปภาพในรูปแบบ PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มลายน้ำให้กับส่วนที่เป็นรูปภาพในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถปกป้องไฟล์ PDF ของคุณด้วยลายน้ำส่วนตัวได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Watermark for .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark for .NET จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. เส้นทางเอกสาร: มีเส้นทางไปยังเอกสาร PDF ที่คุณต้องการเพิ่มลายน้ำ
3. Output Directory: สร้างไดเร็กทอรีที่จะบันทึกเอกสารที่มีลายน้ำ

## นำเข้าเนมสเปซ
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสารและเริ่มต้นลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 2: รับเนื้อหา PDF และเพิ่มลายน้ำ
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// เริ่มต้นลายน้ำรูปภาพหรือข้อความ
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// เพิ่มลายน้ำให้กับภาพ
				artifact.Image.Add(watermark);
			}
		}
	}
```
## ขั้นตอนที่ 3: บันทึกเอกสารลายน้ำ
```csharp
	watermarker.Save(outputFileName);
}
```

## บทสรุป
ด้วย GroupDocs.Watermark สำหรับ .NET การเพิ่มลายน้ำให้กับส่วนต่างๆ ของรูปภาพในเอกสาร PDF กลายเป็นกระบวนการที่ราบรื่น ด้วยการทำตามบทช่วยสอนนี้ คุณสามารถปกป้องไฟล์ PDF ของคุณได้อย่างมีประสิทธิภาพด้วยลายน้ำที่ปรับแต่งเอง จึงมั่นใจในความปลอดภัยและความถูกต้อง
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มทั้งลายน้ำรูปภาพและข้อความลงในเอกสาร PDF ของฉันได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับการเพิ่มลายน้ำทั้งรูปภาพและข้อความพร้อมกัน
### มีการจำกัดจำนวนลายน้ำที่ฉันสามารถเพิ่มลงในเอกสารได้หรือไม่?
ไม่ คุณสามารถเพิ่มลายน้ำหลายลายลงในเอกสารได้โดยไม่มีข้อจำกัดใดๆ
### ฉันสามารถปรับแต่งลักษณะและตำแหน่งของลายน้ำได้หรือไม่?
คุณสามารถควบคุมลักษณะที่ปรากฏ ตำแหน่ง และคุณสมบัติของลายน้ำได้อย่างเต็มที่
### GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ รองรับรูปแบบเอกสารต่าง ๆ รวมถึง Word, Excel, PowerPoint และอีกมากมาย
### มีวิธีลบลายน้ำออกจากเอกสารหรือไม่?
ใช่ GroupDocs.Watermark สำหรับ .NET มีวิธีการลบลายน้ำออกจากเอกสารหากจำเป็น