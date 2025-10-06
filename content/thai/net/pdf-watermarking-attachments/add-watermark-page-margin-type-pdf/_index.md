---
title: เพิ่มลายน้ำด้วยประเภทขอบหน้าใน PDF
linktitle: เพิ่มลายน้ำด้วยประเภทขอบหน้าใน PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำด้วยประเภทระยะขอบหน้าใน PDF โดยใช้ Groupdocs รักษาความปลอดภัยเอกสารของคุณได้อย่างง่ายดาย
weight: 21
url: /th/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
type: docs
---
# เพิ่มลายน้ำด้วยประเภทขอบหน้าใน PDF

## การแนะนำ
ในยุคดิจิทัลปัจจุบัน การรักษาความปลอดภัยเอกสารมีความสำคัญมากกว่าที่เคย วิธีหนึ่งที่จะรับประกันความสมบูรณ์และความถูกต้องของเอกสารของคุณคือการเพิ่มลายน้ำ Groupdocs.Watermark สำหรับ .NET เป็นเครื่องมือพิเศษที่ออกแบบมาเพื่อทำให้กระบวนการนี้ง่ายดาย ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนในการเพิ่มลายน้ำที่มีประเภทระยะขอบหน้าใน PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
-  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง[รุ่นล่าสุด](https://releases.groupdocs.com/Watermark/net/) ของ Groupdocs.Watermark สำหรับ .NET
- สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET เช่น Visual Studio
- ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#
- เอกสาร PDF: เอกสาร PDF ที่คุณต้องการเพิ่มลายน้ำ
## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ เนมสเปซเหล่านี้จะให้การเข้าถึงฟังก์ชันลายน้ำของ Groupdocs
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
ตอนนี้ เรามาแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้ ปฏิบัติตามแต่ละขั้นตอนอย่างระมัดระวังเพื่อเพิ่มลายน้ำให้กับเอกสาร PDF ของคุณ
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอกสารและไดเรกทอรีผลลัพธ์ของคุณ
ขั้นแรก คุณจะต้องระบุเส้นทางไปยังเอกสารของคุณและไดเร็กทอรีเอาต์พุตที่จะบันทึก PDF ที่มีลายน้ำไว้
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: โหลดเอกสาร PDF ของคุณ
 จากนั้น คุณจะโหลดเอกสาร PDF ของคุณโดยใช้ไฟล์`PdfLoadOptions` ระดับ. คลาสนี้อนุญาตให้คุณระบุตัวเลือกที่จำเป็นสำหรับการโหลด PDF ของคุณ
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 3: สร้างลายน้ำข้อความ
ตอนนี้ได้เวลาสร้างลายน้ำแล้ว ในตัวอย่างนี้ เราจะสร้างลายน้ำข้อความพร้อมคุณสมบัติเฉพาะ เช่น แบบอักษร ขนาด และการจัดตำแหน่ง
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ขั้นตอนที่ 4: ตั้งค่าประเภทระยะขอบของหน้า
 หากต้องการวางตำแหน่งลายน้ำให้เหมาะสม คุณจะต้องตั้งค่าประเภทระยะขอบหน้า ที่นี่เราตั้งค่าประเภทระยะขอบของหน้าเป็น`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## ขั้นตอนที่ 5: เพิ่มและบันทึกลายน้ำ
สุดท้าย เพิ่มลายน้ำลงในเอกสารของคุณและบันทึก PDF ที่แก้ไขแล้วลงในไดเร็กทอรีเอาต์พุตที่ระบุ
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## บทสรุป
และคุณก็ได้แล้ว! เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเพิ่มลายน้ำที่มีประเภทระยะขอบหน้าเฉพาะลงในเอกสาร PDF ของคุณได้อย่างง่ายดายโดยใช้ Groupdocs.Watermark สำหรับ .NET สิ่งนี้ไม่เพียงช่วยในการปกป้องเอกสารของคุณ แต่ยังรับประกันความถูกต้องอีกด้วย ไม่ว่าคุณจะจัดการกับรายงานที่เป็นความลับ เอกสารทางกฎหมาย หรืองานสร้างสรรค์ การใส่ลายน้ำเป็นวิธีที่เรียบง่ายแต่มีประสิทธิภาพในการปกป้องเนื้อหาของคุณ
## คำถามที่พบบ่อย
### Groupdocs.Watermark สำหรับ .NET คืออะไร
Groupdocs.Watermark for .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการเพิ่มลายน้ำให้กับรูปแบบเอกสารต่างๆ โดยทางโปรแกรม รองรับรูปภาพ ข้อความ และอื่นๆ ช่วยให้ปรับแต่งได้หลากหลาย
### ฉันสามารถใช้วิธีนี้เพื่อใส่ลายน้ำให้กับเอกสารประเภทอื่นได้หรือไม่
ใช่ Groupdocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และรูปภาพ กระบวนการนี้คล้ายกันแต่อาจเกี่ยวข้องกับตัวเลือกและคลาสที่แตกต่างกัน
### ฉันจะทดลองใช้ Groupdocs.Watermark สำหรับ .NET ได้ฟรีได้อย่างไร
 คุณสามารถ[ดาวน์โหลดรุ่นทดลองใช้ฟรี](https://releases.groupdocs.com/) จากเว็บไซต์ Groupdocs เพื่อสำรวจคุณสมบัติและฟังก์ชันการทำงานของห้องสมุด
### เป็นไปได้ไหมที่จะปรับแต่งลักษณะที่ปรากฏของลายน้ำ?
อย่างแน่นอน! คุณสามารถปรับแต่งแบบอักษร ขนาด สี ความทึบ การจัดตำแหน่ง และคุณสมบัติอื่นๆ ของลายน้ำให้เหมาะกับความต้องการของคุณได้
### ฉันจะรับการสนับสนุนสำหรับ Groupdocs.Watermark สำหรับ .NET ได้ที่ไหน
 สำหรับการสนับสนุนคุณสามารถเยี่ยมชมที่[ฟอรัมสนับสนุนลายน้ำ Groupdocs](https://forum.groupdocs.com/c/watermark/19) โดยคุณสามารถถามคำถามและรับความช่วยเหลือจากชุมชนและทีมงาน Groupdocs