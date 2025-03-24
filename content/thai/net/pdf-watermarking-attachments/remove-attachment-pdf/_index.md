---
title: ลบไฟล์แนบออกจาก PDF
linktitle: ลบไฟล์แนบออกจาก PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบไฟล์แนบออกจากเอกสาร PDF อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET เพิ่มประสิทธิภาพการจัดการเอกสารของคุณ
weight: 33
url: /th/net/pdf-watermarking-attachments/remove-attachment-pdf/
---
## การแนะนำ
ในโลกของการพัฒนาซอฟต์แวร์ การจัดการเอกสารอย่างมีประสิทธิภาพถือเป็นงานที่สำคัญ ไม่ว่าจะเป็นการใช้งานส่วนตัวหรือเพื่ออาชีพ มีหลายครั้งที่เราจำเป็นต้องจัดการหรือควบคุมองค์ประกอบต่างๆ ภายในเอกสาร GroupDocs.Watermark สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งออกแบบมาเพื่อตอบสนองความต้องการนี้ โดยนำเสนอชุดเครื่องมือที่ครอบคลุมเพื่อทำงานกับเอกสารรูปแบบต่างๆ ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกขอบเขตของ GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. การติดตั้ง GroupDocs.Watermark สำหรับ .NET
 ก่อนอื่น คุณต้องดาวน์โหลดและติดตั้ง GroupDocs.Watermark สำหรับ .NET คุณสามารถรับห้องสมุดได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
### 2. ความเข้าใจพื้นฐานของ .NET Framework
การมีความเข้าใจพื้นฐานเกี่ยวกับ .NET Framework จะช่วยให้คุณเข้าใจแนวคิดและเทคนิคต่างๆ ที่กล่าวถึงในบทช่วยสอนนี้ได้อย่างมาก
### 3. ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#
เนื่องจาก GroupDocs.Watermark สำหรับ .NET ใช้กับภาษา C# เป็นหลัก จึงจำเป็นต้องทำความคุ้นเคยกับพื้นฐานการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
หากต้องการเริ่มทำงานกับ GroupDocs.Watermark สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ สิ่งนี้ช่วยให้คุณเข้าถึงฟังก์ชั่นที่ห้องสมุดมอบให้ได้อย่างราบรื่น

```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;
```
การลบเอกสารแนบออกจากเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET เกี่ยวข้องกับหลายขั้นตอน มาแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอกสารและไดเรกทอรีผลลัพธ์
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
ในขั้นตอนนี้ คุณจะต้องระบุเส้นทางของเอกสาร PDF ที่คุณต้องการลบไฟล์แนบ นอกจากนี้ ให้กำหนดไดเร็กทอรีที่จะบันทึกเอกสารที่แก้ไข
## ขั้นตอนที่ 2: โหลดเอกสาร PDF พร้อมตัวเลือก
```csharp
var loadOptions = new PdfLoadOptions();
```
 ที่นี่ คุณสร้างอินสแตนซ์ของ`PdfLoadOptions` เพื่อระบุตัวเลือกเพิ่มเติมสำหรับการโหลดเอกสาร PDF
## ขั้นตอนที่ 3: เริ่มต้นลายน้ำ
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 เริ่มต้น`Watermarker` วัตถุโดยผ่านเส้นทางเอกสารและตัวเลือกการโหลด ออบเจ็กต์นี้ให้การเข้าถึงฟังก์ชันต่างๆ สำหรับการจัดการเอกสาร
## ขั้นตอนที่ 4: รับเนื้อหา PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 ดึงเนื้อหาของเอกสาร PDF โดยใช้`GetContent<PdfContent>()` วิธี. ซึ่งช่วยให้คุณเข้าถึงไฟล์แนบและองค์ประกอบอื่นๆ ภายใน PDF ได้
## ขั้นตอนที่ 5: วนซ้ำผ่านไฟล์แนบและลบออก
```csharp
for (int i = pdfContent.Attachments.Count - 1; i >= 0; i--)
{
    PdfAttachment attachment = pdfContent.Attachments[i];
    if (attachment.Name.Contains("sample") && attachment.GetDocumentInfo().FileType == FileType.DOCX)
    {
        pdfContent.Attachments.RemoveAt(i);
    }
}
```
ทำซ้ำผ่านไฟล์แนบของเอกสาร PDF หากตรงตามเงื่อนไขเฉพาะ (เช่น ชื่อไฟล์แนบมี "ตัวอย่าง" และประเภทไฟล์คือ DOCX) ให้ลบไฟล์แนบออกจากเอกสาร
## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไข
```csharp
watermarker.Save(outputFileName);
```
สุดท้าย ให้บันทึกเอกสาร PDF ที่แก้ไขแล้วไปยังไดเร็กทอรีเอาต์พุตที่ระบุพร้อมชื่อไฟล์ที่ต้องการ

## บทสรุป
GroupDocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพสำหรับการจัดการไฟล์แนบภายในเอกสาร PDF ด้วยการทำตามคำแนะนำทีละขั้นตอนที่ให้ไว้ในบทช่วยสอนนี้ คุณสามารถลบไฟล์แนบออกจาก PDF ได้อย่างราบรื่น ซึ่งช่วยเพิ่มประสิทธิภาพการจัดการเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย เช่น Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถเพิ่มลายน้ำแบบกำหนดเองให้กับเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ได้หรือไม่
อย่างแน่นอน! GroupDocs.Watermark สำหรับ .NET ช่วยให้คุณสามารถเพิ่มลายน้ำข้อความหรือรูปภาพลงในเอกสาร PDF ได้อย่างง่ายดาย
### GroupDocs.Watermark สำหรับ .NET มีความเข้ากันได้ข้ามแพลตฟอร์มหรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET ได้รับการออกแบบมาให้ทำงานได้อย่างราบรื่นบนแพลตฟอร์มต่างๆ รวมถึง Windows, Linux และ macOS
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Watermark สำหรับ .NET เวอร์ชันทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะรับความช่วยเหลือด้านเทคนิคหรือการสนับสนุนสำหรับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 หากต้องการความช่วยเหลือหรือการสนับสนุนด้านเทคนิค คุณสามารถไปที่ฟอรัม GroupDocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19).