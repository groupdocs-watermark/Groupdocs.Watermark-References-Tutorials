---
title: แยกข้อมูลคำอธิบายประกอบจาก PDF
linktitle: แยกข้อมูลคำอธิบายประกอบจาก PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีดึงข้อมูลคำอธิบายประกอบจากเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ในคำแนะนำโดยละเอียดทีละขั้นตอนนี้
weight: 23
url: /th/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# แยกข้อมูลคำอธิบายประกอบจาก PDF

## การแนะนำ
คุณมักจะพบว่าตัวเองจำเป็นต้องดึงข้อมูลคำอธิบายประกอบโดยละเอียดจากเอกสาร PDF ของคุณหรือไม่? ไม่ว่าคุณจะเป็นนักพัฒนาที่ทำงานเกี่ยวกับระบบการจัดการเอกสารหรือนักธุรกิจมืออาชีพที่จัดการ PDF จำนวนมาก การแยกและประมวลผลคำอธิบายประกอบอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญ ด้วย GroupDocs.Watermark สำหรับ .NET คุณจะมีชุดเครื่องมืออันทรงพลังเพื่อทำให้งานนี้ตรงไปตรงมาและมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่จำเป็นในการเริ่มต้น:
1. Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio แล้ว นี่จะเป็น IDE ของเราสำหรับการเขียนและรันโค้ด
2.  GroupDocs.Watermark สำหรับ .NET: คุณต้องมีไลบรารี GroupDocs.Watermark สำหรับ .NET คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.groupdocs.com/Watermark/net/).
3. ความรู้พื้นฐานของ C#: จำเป็นต้องมีความคุ้นเคยกับการเขียนโปรแกรม C# พร้อมกับตัวอย่าง
## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้มีคลาสและวิธีการที่จำเป็นในการทำงานกับไฟล์ PDF และแยกคำอธิบายประกอบ
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ
ขั้นแรก มาตั้งค่าโครงการของเราใน Visual Studio กัน สร้างโครงการแอปคอนโซล (.NET Core) ใหม่ เมื่อสร้างโปรเจ็กต์ของคุณแล้ว คุณจะต้องเพิ่มการอ้างอิงไปยังไลบรารี GroupDocs.Watermark สำหรับ .NET
1. เปิดตัวจัดการแพ็คเกจ NuGet
2.  ค้นหา`GroupDocs.Watermark`.
3.  ติดตั้ง`GroupDocs.Watermark` บรรจุุภัณฑ์.
## ขั้นตอนที่ 2: กำหนดเส้นทางเอกสาร
ถัดไป คุณจะต้องระบุเส้นทางสำหรับเอกสาร PDF ที่ป้อนเข้าและไดเร็กทอรีเอาต์พุตที่จะบันทึกข้อมูลที่แยกออกมา เพื่อให้แน่ใจว่าแอปพลิเคชันของคุณรู้ว่าจะหาไฟล์ PDF ได้ที่ไหน และจะเก็บผลลัพธ์ไว้ที่ไหน
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 3: โหลดเอกสาร PDF
 ในการทำงานกับเอกสาร PDF เราจำเป็นต้องโหลดโดยใช้`PdfLoadOptions`- คลาสนี้มีตัวเลือกในการกำหนดค่ากระบวนการโหลด
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // โค้ดสำหรับแยกคำอธิบายประกอบจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 4: เข้าถึงเนื้อหา PDF
เมื่อโหลดเอกสารแล้วเราจะสามารถเข้าถึงเนื้อหาได้ โดยเฉพาะอย่างยิ่ง เราต้องการรับเนื้อหา PDF เพื่อให้เราสามารถวนซ้ำหน้าต่างๆ และคำอธิบายประกอบได้
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ขั้นตอนที่ 5: วนซ้ำหน้าต่างๆ และคำอธิบายประกอบ
ด้วยเนื้อหา PDF ที่อยู่ในมือ เราสามารถวนซ้ำแต่ละหน้าและผ่านแต่ละคำอธิบายประกอบบนหน้าเหล่านั้นได้ สิ่งนี้ช่วยให้เราสามารถดึงข้อมูลที่เราต้องการได้
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // แยกรายละเอียดคำอธิบายประกอบได้ที่นี่
    }
}
```
## ขั้นตอนที่ 6: แยกรายละเอียดคำอธิบายประกอบ
ภายในลูปที่ซ้อนกัน เราจะแยกรายละเอียดต่างๆ เกี่ยวกับคำอธิบายประกอบแต่ละรายการ ซึ่งรวมถึงประเภทของคำอธิบายประกอบ รูปภาพที่เกี่ยวข้อง ข้อความ และข้อมูลตำแหน่ง
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## ขั้นตอนที่ 7: บันทึกหรือประมวลผลข้อมูลที่แยกออกมา
สุดท้าย ตัดสินใจว่าคุณต้องการทำอะไรกับข้อมูลคำอธิบายประกอบที่แยกออกมา คุณสามารถพิมพ์ลงในคอนโซล บันทึกเป็นไฟล์ หรือแม้แต่จัดเก็บไว้ในฐานข้อมูลก็ได้ ขึ้นอยู่กับความต้องการของคุณ
```csharp
// ตัวอย่างการบันทึกข้อมูลที่แยกออกมาเป็นไฟล์
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## บทสรุป
การแยกข้อมูลคำอธิบายประกอบจากเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อนซึ่งช่วยให้คุณประหยัดเวลาและความพยายามได้มาก ด้วยการทำตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณสามารถรวมฟังก์ชันนี้เข้ากับโปรเจ็กต์ของคุณได้อย่างง่ายดาย และทำให้การแยกข้อมูลคำอธิบายประกอบอันมีค่าเป็นแบบอัตโนมัติ
 ไม่ว่าคุณจะจัดการ PDF จำนวนมากหรือเพียงต้องการดึงข้อมูลเฉพาะ GroupDocs.Watermark สำหรับ .NET มอบโซลูชันที่เชื่อถือได้และมีประสิทธิภาพ อย่าลืมเข้าไปดูที่[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) สำหรับคุณสมบัติขั้นสูงและตัวเลือกการปรับแต่งเพิ่มเติม
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET คืออะไร
GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่ครอบคลุมซึ่งช่วยให้นักพัฒนาสามารถเพิ่ม ค้นหา และลบลายน้ำออกจากรูปแบบเอกสารต่างๆ รวมถึง PDF, เอกสาร Word และรูปภาพ
### ฉันสามารถทดลองใช้ GroupDocs.Watermark ได้ฟรีหรือไม่
 ใช่ คุณจะได้รับ[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อทดสอบคุณสมบัติของห้องสมุดก่อนตัดสินใจซื้อ
### ฉันจะได้รับความช่วยเหลือได้อย่างไรหากฉันประสบปัญหา
 คุณสามารถรับการสนับสนุนจากทีม GroupDocs ได้โดยไปที่พวกเขา[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### เป็นไปได้ไหมที่จะได้รับใบอนุญาตชั่วคราวสำหรับการทดสอบ?
 ใช่ คุณสามารถขอ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)เพื่อวัตถุประสงค์ในการทดสอบ
### ฉันจะซื้อ GroupDocs.Watermark สำหรับ .NET เวอร์ชันเต็มได้ที่ไหน
 คุณสามารถซื้อเวอร์ชันเต็มได้จาก[เว็บไซต์กรุ๊ปดอคส์](https://purchase.groupdocs.com/buy).