---
title: เพิ่มลายน้ำให้กับหน้าเฉพาะในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับหน้าเฉพาะในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้การเพิ่มลายน้ำข้อความและรูปภาพลงในหน้าเฉพาะใน PDF โดยใช้ Groupdocs ลายน้ำสำหรับ .NET ปฏิบัติตามคำแนะนำโดยละเอียดของเราเพื่อรักษาความปลอดภัยให้กับเอกสารของคุณ
weight: 15
url: /th/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
---

# เพิ่มลายน้ำให้กับหน้าเฉพาะในรูปแบบ PDF

## การแนะนำ
การเพิ่มลายน้ำให้กับเอกสาร PDF ของคุณเป็นขั้นตอนสำคัญในการปกป้องเนื้อหาและยืนยันความเป็นเจ้าของของคุณ ไม่ว่าคุณจะทำเครื่องหมายแบบร่าง รักษาความปลอดภัยข้อมูลที่ละเอียดอ่อน หรือเพียงเพิ่มแบรนด์ ลายน้ำก็เป็นเครื่องมือที่มีประสิทธิภาพ ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ Groupdocs.Watermark สำหรับ .NET เพื่อเพิ่มลายน้ำทั้งข้อความและรูปภาพลงในหน้าเฉพาะในไฟล์ PDF ของคุณ เราจะแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้ เพื่อให้มั่นใจว่าคุณสามารถปฏิบัติตามและนำคุณลักษณะเหล่านี้ไปใช้ในโครงการของคุณได้
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้งาน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio แล้ว: คุณจะต้องมี IDE เช่น Visual Studio เพื่อเขียนและเรียกใช้โค้ด .NET ของคุณ
- .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องของคุณ
-  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง Groupdocs.Watermark สำหรับ .NET คุณสามารถรับมันได้[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
- ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# จะเป็นประโยชน์
- เอกสาร PDF: เตรียมไฟล์ PDF ให้พร้อมซึ่งคุณสามารถใช้ทดสอบการเพิ่มลายน้ำได้
## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ ขั้นตอนนี้มีความสำคัญเนื่องจากช่วยให้คุณเข้าถึงคลาสและวิธีการของลายน้ำได้
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: การตั้งค่าโครงการ
### สร้างโครงการใหม่
ขั้นแรก เปิด Visual Studio และสร้างโปรเจ็กต์ C# ใหม่ คุณสามารถเลือกแอปพลิเคชันคอนโซลเพื่อความเรียบง่ายได้
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### ติดตั้ง Groupdocs.Watermark
จากนั้น ติดตั้งไลบรารี Groupdocs.Watermark ผ่าน NuGet Package Manager
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
ค้นหา "Groupdocs.Watermark" และติดตั้ง
## ขั้นตอนที่ 2: โหลดเอกสาร PDF ของคุณ
### กำหนดเส้นทางเอกสาร
ระบุเส้นทางไปยังเอกสาร PDF ของคุณและไดเร็กทอรีเอาต์พุตที่จะบันทึก PDF ที่ใส่ลายน้ำไว้
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### โหลดเอกสาร PDF
 ใช้`PdfLoadOptions` คลาสเพื่อโหลดเอกสาร PDF ของคุณ
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณสำหรับเพิ่มลายน้ำจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: เพิ่มลายน้ำข้อความลงในหน้าคี่
### สร้างลายน้ำข้อความ
 สร้างก`TextWatermark` วัตถุด้วยการตั้งค่าข้อความและแบบอักษรที่คุณต้องการ
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### ใช้ตัวเลือกลายน้ำข้อความ
 ใช้`PdfArtifactWatermarkOptions` เพื่อระบุวิธีการใส่ลายน้ำ
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## ขั้นตอนที่ 4: เพิ่มลายน้ำรูปภาพลงในหน้าแรก
โหลดรูปภาพเพื่อใช้เป็นลายน้ำ ตรวจสอบให้แน่ใจว่าเส้นทางของภาพถูกต้อง
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## ขั้นตอนที่ 5: บันทึก PDF ที่ใส่ลายน้ำ
สุดท้าย ให้บันทึก PDF ที่ใส่ลายน้ำของคุณลงในไดเร็กทอรีเอาต์พุตที่ระบุ
```csharp
watermarker.Save(outputFileName);
```
## บทสรุป
การเพิ่มลายน้ำให้กับ PDF ของคุณโดยใช้ Groupdocs ลายน้ำสำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อน เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเพิ่มลายน้ำข้อความและรูปภาพลงในหน้าเฉพาะในเอกสาร PDF ของคุณได้อย่างมีประสิทธิภาพ สิ่งนี้ไม่เพียงช่วยในการรักษาเอกสารของคุณให้ปลอดภัย แต่ยังรักษารูปลักษณ์ที่เป็นมืออาชีพอีกด้วย ลองใช้และสำรวจตัวเลือกการปรับแต่งต่างๆ ที่มีเพื่อทำให้ลายน้ำของคุณมีเอกลักษณ์และมีประสิทธิภาพ
## คำถามที่พบบ่อย
### Groupdocs.Watermark สำหรับ .NET คืออะไร
Groupdocs.Watermark for .NET เป็นไลบรารีที่ช่วยให้คุณสามารถเพิ่ม ค้นหา และลบลายน้ำในรูปแบบเอกสารต่างๆ รวมถึง PDF, Word, Excel และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะลายน้ำได้หรือไม่?
ใช่ คุณสามารถปรับแต่งแบบอักษร ขนาด สี และตำแหน่งของข้อความลายน้ำได้ และคุณสามารถปรับขนาด ความทึบ และตำแหน่งของลายน้ำรูปภาพได้
### เป็นไปได้ไหมที่จะเพิ่มลายน้ำเฉพาะบางหน้าเท่านั้น?
อย่างแน่นอน. Groupdocs.Watermark สำหรับ .NET มีตัวเลือกในการเพิ่มลายน้ำให้กับหน้าเฉพาะ หน้าคี่หรือหน้าคู่ หรือช่วงของหน้า
### ฉันจะทดลองใช้ Groupdocs.Watermark ฟรีได้อย่างไร
 คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[เว็บไซต์ Groupdocs](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารรายละเอียดเพิ่มเติมได้จากที่ไหน?
 สำหรับข้อมูลรายละเอียดเพิ่มเติม คุณสามารถดูได้ที่[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/).