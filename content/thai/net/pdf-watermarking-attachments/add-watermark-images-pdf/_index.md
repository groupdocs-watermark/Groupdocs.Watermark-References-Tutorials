---
title: เพิ่มลายน้ำให้กับรูปภาพในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับรูปภาพในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้การเพิ่มลายน้ำให้กับรูปภาพในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET พร้อมบทช่วยสอนแบบละเอียดทีละขั้นตอนของเรา รักษาความปลอดภัย PDF ของคุณได้อย่างง่ายดาย
weight: 19
url: /th/net/pdf-watermarking-attachments/add-watermark-images-pdf/
type: docs
---
# เพิ่มลายน้ำให้กับรูปภาพในรูปแบบ PDF

## การแนะนำ
การเพิ่มลายน้ำให้กับรูปภาพภายในเอกสาร PDF อาจเป็นสิ่งจำเป็นในการปกป้องทรัพย์สินทางปัญญาของคุณหรือรับรองความถูกต้องของเอกสารของคุณ การใช้ GroupDocs.Watermark สำหรับ .NET ช่วยให้งานนี้สำเร็จลุล่วงได้อย่างมีประสิทธิภาพและง่ายดาย บทช่วยสอนนี้จะแนะนำคุณตลอดแต่ละขั้นตอนของกระบวนการ ตั้งแต่การตั้งค่าสภาพแวดล้อมไปจนถึงการเพิ่มลายน้ำไปจนถึงการบันทึกเอกสารขั้นสุดท้าย มาดำน้ำกันเถอะ!
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio, Integrated Development Environment (IDE) สำหรับแอปพลิเคชัน .NET
2.  GroupDocs.Watermark for .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark for .NET จาก[หน้าปล่อย](https://releases.groupdocs.com/Watermark/net/).
3. เอกสาร PDF: เตรียมเอกสาร PDF พร้อมรูปภาพเพื่อทดสอบฟังก์ชันการใส่ลายน้ำ
4.  ใบอนุญาตชั่วคราว: รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) หากคุณกำลังประเมินผลิตภัณฑ์
## นำเข้าเนมสเปซ
ขั้นแรก ตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณ ซึ่งจะรวมถึงเนมสเปซหลักที่จำเป็นในการทำงานกับเอกสาร PDF และลายน้ำ
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
ในการเริ่มต้น ให้กำหนดเส้นทางสำหรับเอกสารอินพุตและไดเร็กทอรีเอาต์พุตที่จะบันทึกเอกสารที่มีลายน้ำ ขั้นตอนนี้มีความสำคัญเพื่อให้แน่ใจว่าโปรแกรมของคุณรู้ว่าจะหาเอกสารต้นฉบับได้ที่ไหน และจะเก็บไฟล์ที่ประมวลผลได้ที่ไหน
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: โหลดเอกสาร PDF
 จากนั้น คุณจะต้องโหลดเอกสาร PDF โดยใช้`PdfLoadOptions`- คลาสนี้อนุญาตให้คุณระบุตัวเลือกสำหรับการโหลด PDF เช่น การป้องกันด้วยรหัสผ่าน หากจำเป็น
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสสำหรับใส่ลายน้ำของคุณจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างลายน้ำ
ตอนนี้เริ่มต้นลายน้ำ ในตัวอย่างนี้ เรากำลังสร้างลายน้ำข้อความที่ระบุว่า "รูปภาพที่ได้รับการป้องกัน" ปรับแต่งแบบอักษร การจัดตำแหน่ง การหมุน และการปรับขนาดตามความต้องการของคุณ
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ขั้นตอนที่ 4: เข้าถึงเนื้อหา PDF
ดึงเนื้อหาของเอกสาร PDF โดยเฉพาะเราจำเป็นต้องเข้าถึงรูปภาพภายใน PDF ในส่วนนี้ เรากำลังเน้นที่หน้าแรก แต่คุณสามารถขยายไปยังหน้าอื่นๆ ได้ตามต้องการ
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// รับภาพทั้งหมดจากหน้าแรก
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## ขั้นตอนที่ 5: ใช้ลายน้ำกับรูปภาพ
วนซ้ำแต่ละภาพที่พบในหน้าแรกแล้วใส่ลายน้ำ เพื่อให้แน่ใจว่ารูปภาพทั้งหมดในหน้าที่ระบุจะมีลายน้ำติดอยู่
```csharp
// เพิ่มลายน้ำให้กับรูปภาพที่พบทั้งหมด
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## ขั้นตอนที่ 6: บันทึกเอกสารลายน้ำ
สุดท้าย ให้บันทึก PDF ที่ใส่ลายน้ำลงในไดเร็กทอรีเอาต์พุตที่ระบุ ขั้นตอนนี้จะสิ้นสุดกระบวนการโดยการเขียนการเปลี่ยนแปลงลงในไฟล์ใหม่
```csharp
watermarker.Save(outputFileName);
```
## บทสรุป
และคุณก็ได้แล้ว! การเพิ่มลายน้ำให้กับรูปภาพภายใน PDF โดยใช้ GroupDocs ลายน้ำสำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อนซึ่งช่วยเพิ่มความปลอดภัยและความถูกต้องของเอกสารของคุณได้อย่างมาก ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถมั่นใจได้ว่าทรัพย์สินทางปัญญาของคุณได้รับการคุ้มครองและเอกสารของคุณมีความปลอดภัย
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET คืออะไร
GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่ครอบคลุมที่ช่วยให้นักพัฒนาสามารถเพิ่ม ค้นหา และลบลายน้ำในรูปแบบเอกสารต่างๆ รวมถึง PDF
### ฉันสามารถเพิ่มลายน้ำทั้งข้อความและรูปภาพโดยใช้ GroupDocs.Watermark ได้หรือไม่
ใช่ GroupDocs.Watermark รองรับทั้งลายน้ำข้อความและรูปภาพ ซึ่งให้ความยืดหยุ่นสำหรับความต้องการลายน้ำประเภทต่างๆ
### เป็นไปได้ไหมที่จะใส่ลายน้ำหลายหน้าใน PDF
อย่างแน่นอน! คุณสามารถวนซ้ำแต่ละหน้าใน PDF และใช้ลายน้ำกับรูปภาพในแต่ละหน้าได้
### ฉันต้องมีใบอนุญาตเพื่อใช้ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ จำเป็นต้องมีใบอนุญาต คุณสามารถรับก[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อวัตถุประสงค์ในการประเมินผล
### ฉันจะหาเอกสารเพิ่มเติมเกี่ยวกับ GroupDocs.Watermark สำหรับ .NET ได้ที่ไหน
 คุณสามารถค้นหาเอกสารที่ครอบคลุมได้ที่[หน้าเอกสาร GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).