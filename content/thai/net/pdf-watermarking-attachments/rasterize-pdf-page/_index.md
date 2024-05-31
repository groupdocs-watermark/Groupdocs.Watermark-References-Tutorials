---
title: แปลงหน้า PDF เป็นแรสเตอร์
linktitle: แปลงหน้า PDF เป็นแรสเตอร์
second_title: GroupDocs.Watermark .NET API
description: เพิ่มความปลอดภัยให้กับเอกสารด้วย GroupDocs ลายน้ำสำหรับ .NET เพิ่มลายน้ำให้กับ PDF และรูปแบบอื่นๆ ได้อย่างราบรื่น
type: docs
weight: 28
url: /th/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถเพิ่มลายน้ำให้กับรูปแบบเอกสารต่างๆ ได้อย่างราบรื่น รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย ด้วยอินเทอร์เฟซที่ใช้งานง่ายและฟีเจอร์ที่ครอบคลุม GroupDocs.Watermark ช่วยลดความยุ่งยากในการเพิ่มลายน้ำข้อความหรือรูปภาพลงในเอกสาร ทำให้ผู้ใช้สามารถปกป้องทรัพย์สินทางปัญญาและเพิ่มความปลอดภัยของเอกสารได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้ GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. การติดตั้ง: ดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET จากไฟล์[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2.  ใบอนุญาต: รับใบอนุญาตสำหรับ GroupDocs.Watermark สำหรับ .NET คุณสามารถขอรับใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/) หรือซื้อใบอนุญาตฉบับสมบูรณ์จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy).
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องพัฒนาของคุณ
4. เอกสาร: เตรียมเอกสารที่คุณต้องการเพิ่มลายน้ำ

## นำเข้าเนมสเปซ
หากต้องการเริ่มใช้ GroupDocs.Watermark สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำ
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## ขั้นตอนที่ 3: เพิ่มลายน้ำ
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 4: ทำให้หน้าเป็นแรสเตอร์
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
โดยสรุป GroupDocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่ราบรื่นสำหรับการเพิ่มลายน้ำให้กับ PDF และรูปแบบเอกสารอื่นๆ ด้วยการทำตามคำแนะนำทีละขั้นตอนที่อธิบายไว้ข้างต้น นักพัฒนาสามารถแรสเตอร์หน้า PDF และเพิ่มความปลอดภัยของเอกสารได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, Visio และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายน้ำที่เพิ่มลงในเอกสารได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark มีตัวเลือกการปรับแต่งมากมายสำหรับลายน้ำข้อความและรูปภาพ ซึ่งช่วยให้ผู้ใช้สามารถปรับแบบอักษร ขนาด สี ความทึบ และตำแหน่งได้ตามความต้องการ
### GroupDocs.Watermark เหมาะสำหรับการใช้งานส่วนตัวและเชิงพาณิชย์หรือไม่
ใช่ GroupDocs.Watermark นำเสนอตัวเลือกสิทธิ์การใช้งานที่ยืดหยุ่นเพื่อตอบสนองความต้องการของทั้งส่วนบุคคลและองค์กร ทำให้เหมาะสำหรับโครงการส่วนบุคคลตลอดจนแอปพลิเคชันเชิงพาณิชย์ขนาดใหญ่
### GroupDocs.Watermark ให้การสนับสนุนทางเทคนิคสำหรับนักพัฒนาหรือไม่
ใช่ นักพัฒนาสามารถเข้าถึงการสนับสนุนด้านเทคนิคที่ครอบคลุมผ่านฟอรัม GroupDocs.Watermark ซึ่งพวกเขาสามารถขอความช่วยเหลือ แบ่งปันประสบการณ์ และมีส่วนร่วมกับเพื่อนๆ นักพัฒนาได้
### ฉันสามารถลองใช้ GroupDocs.Watermark ก่อนตัดสินใจซื้อได้หรือไม่
แน่นอน! คุณสามารถใช้ประโยชน์จาก GroupDocs.Watermark เวอร์ชันทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/)ช่วยให้คุณสำรวจคุณสมบัติและฟังก์ชันต่างๆ ก่อนตัดสินใจซื้อ