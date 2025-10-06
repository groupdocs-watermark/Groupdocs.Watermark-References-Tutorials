---
title: แยกข้อมูล XObject จาก PDF
linktitle: แยกข้อมูล XObject จาก PDF
second_title: GroupDocs.Watermark .NET API
description: ปลดล็อกพลังของลายน้ำเอกสารด้วย GroupDocs.Watermark สำหรับ .NET จัดการลายน้ำใน PDF, เอกสาร Word และรูปภาพได้อย่างราบรื่น
weight: 25
url: /th/net/pdf-watermarking-attachments/extract-xobject-information-pdf/
type: docs
---
# แยกข้อมูล XObject จาก PDF

## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API ลายน้ำเอกสารที่มีประสิทธิภาพ ซึ่งออกแบบมาเพื่อจัดการลายน้ำในรูปแบบเอกสารต่างๆ เช่น PDF, Word, Excel, PowerPoint และรูปภาพ ช่วยให้นักพัฒนามีวิธีที่ตรงไปตรงมาในการเพิ่ม ลบ ค้นหา และแทนที่ลายน้ำในเอกสารโดยทางโปรแกรม ไม่ว่าคุณจะต้องเพิ่มโลโก้บริษัท ประกาศลิขสิทธิ์ หรือการประทับตราที่เป็นความลับลงในเอกสารของคุณ GroupDocs.Watermark จะทำให้กระบวนการง่ายขึ้นด้วย API ที่ใช้งานง่าย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึก GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. การติดตั้ง: ดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET จากไฟล์[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ .NET IDE อื่น ๆ ในระบบของคุณ
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ที่จำเป็นในเครื่องพัฒนาของคุณ

## การนำเข้าเนมสเปซ
หากต้องการเริ่มใช้ GroupDocs.Watermark สำหรับ .NET ในโปรเจ็กต์ของคุณ คุณจะต้องนำเข้าเนมสเปซที่จำเป็น
ในโครงการ .NET ของคุณ ให้เพิ่มการอ้างอิงไปยัง GroupDocs.Watermark.dll
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## ขั้นตอนที่ 2: เข้าถึงเนื้อหา PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ขั้นตอนที่ 3: วนซ้ำผ่านหน้าต่างๆ
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## ขั้นตอนที่ 4: เข้าถึง XObjects
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## ขั้นตอนที่ 5: แยกข้อมูล
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## บทสรุป
GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนาสามารถจัดการลายน้ำของเอกสารได้อย่างราบรื่นในแอปพลิเคชัน .NET ด้วย API ที่ใช้งานง่ายและฟีเจอร์ที่แข็งแกร่ง จึงเป็นโซลูชั่นที่ตอบโจทย์ทุกความต้องการด้านลายน้ำ ด้วยการทำตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณจะสามารถควบคุมศักยภาพของ GroupDocs ได้อย่างเต็มที่ และปรับปรุงขั้นตอนการทำงานการจัดการเอกสารของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับกรอบงาน .NET ทั้งหมดหรือไม่
ใช่ GroupDocs.Watermark รองรับ .NET Frameworks ที่หลากหลาย รวมถึง .NET Core และ .NET Framework
### ฉันสามารถใช้ลายน้ำหลายลายกับเอกสารเดียวโดยใช้ GroupDocs.Watermark ได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark ช่วยให้คุณสามารถเพิ่มลายน้ำหลายประเภทลงในเอกสารเดียวได้
### GroupDocs.Watermark รองรับการเข้ารหัสเอกสารหรือไม่
ใช่ GroupDocs.Watermark นำเสนอความสามารถในการเข้ารหัสเพื่อรักษาความปลอดภัยเอกสารของคุณจากการเข้าถึงโดยไม่ได้รับอนุญาต
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Watermark เวอร์ชันทดลองใช้ฟรีได้จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนและทรัพยากรเพิ่มเติมสำหรับ GroupDocs.Watermark ได้จากที่ไหน
คุณสามารถสำรวจเอกสาร GroupDocs.Watermark เข้าร่วมฟอรัมชุมชน หรือติดต่อทีมสนับสนุนเพื่อขอความช่วยเหลือได้