---
title: เพิ่มลายน้ำให้กับรูปภาพคำอธิบายประกอบในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับรูปภาพคำอธิบายประกอบในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีปกป้องเอกสาร PDF ของคุณโดยการเพิ่มลายน้ำให้กับภาพคำอธิบายประกอบโดยใช้ Groupdocs.Watermark สำหรับ .NET
weight: 17
url: /th/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
type: docs
---
# เพิ่มลายน้ำให้กับรูปภาพคำอธิบายประกอบในรูปแบบ PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีเพิ่มลายน้ำให้กับรูปภาพคำอธิบายประกอบในเอกสาร PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ลายน้ำเป็นสิ่งสำคัญในการปกป้องเอกสารของคุณจากการใช้หรือการแจกจ่ายโดยไม่ได้รับอนุญาต ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณจะได้เรียนรู้วิธีใส่ลายน้ำข้อความกับรูปภาพคำอธิบายประกอบใน PDF ได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
2. ติดตั้ง Groupdocs.Watermark สำหรับไลบรารี .NET แล้ว
3. เข้าถึงสภาพแวดล้อมการพัฒนาเช่น Visual Studio
4. เอกสาร PDF พร้อมรูปภาพคำอธิบายประกอบเป็นลายน้ำ

## การนำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังโค้ด C# ของคุณ:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## ขั้นตอนที่ 2: รับเนื้อหา PDF และเริ่มต้นลายน้ำ
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // เริ่มต้นลายน้ำรูปภาพหรือข้อความ
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## ขั้นตอนที่ 3: วนซ้ำผ่านหน้า PDF และรูปภาพคำอธิบายประกอบ
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // เพิ่มลายน้ำให้กับภาพ
                annotation.Image.Add(watermark);
            }
        }
    }
```
## ขั้นตอนที่ 4: บันทึกเอกสารด้วยลายน้ำ
```csharp
    watermarker.Save(outputFileName);
}
```
หลังจากดำเนินการขั้นตอนเหล่านี้ เอกสาร PDF ของคุณจะมีลายน้ำที่ระบุเพิ่มลงในรูปภาพคำอธิบายประกอบ

## บทสรุป
การเพิ่มลายน้ำให้กับรูปภาพคำอธิบายประกอบใน PDF ถือเป็นสิ่งสำคัญในการปกป้องความสมบูรณ์ของเอกสารและรับรองว่าจะไม่ถูกนำไปใช้ในทางที่ผิด ด้วย Groupdocs.Watermark สำหรับ .NET กระบวนการนี้จะง่ายและมีประสิทธิภาพ ช่วยให้คุณสามารถปกป้องไฟล์ PDF ของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสาร PDF เดียวกันได้หรือไม่
ได้ คุณสามารถเพิ่มลายน้ำหลายลายลงในเอกสาร PDF เดียวกันได้โดยใช้ Groupdocs.Watermark สำหรับ .NET
### Groupdocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ Groupdocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### เป็นไปได้ไหมที่จะปรับแต่งลักษณะที่ปรากฏของลายน้ำ?
แน่นอน คุณสามารถปรับแต่งข้อความ แบบอักษร สี ขนาด และตำแหน่งของลายน้ำได้ตามความต้องการของคุณ
### ฉันสามารถลบลายน้ำออกจากเอกสาร PDF โดยใช้ Groupdocs.Watermark ได้หรือไม่
ใช่ Groupdocs.Watermark มีฟังก์ชันในการลบลายน้ำออกจากเอกสาร PDF ได้อย่างง่ายดาย
### มีการทดลองใช้ Groupdocs.Watermark สำหรับ .NET ฟรีหรือไม่
ใช่ คุณสามารถทดลองใช้ Groupdocs.Watermark สำหรับ .NET ได้ฟรีจากเว็บไซต์