---
title: แทนที่ข้อความด้วยการจัดรูปแบบสำหรับสิ่งประดิษฐ์ในรูปแบบ PDF
linktitle: แทนที่ข้อความด้วยการจัดรูปแบบสำหรับสิ่งประดิษฐ์ในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีแทนที่ข้อความด้วยการจัดรูปแบบสำหรับส่วนต่างๆ ในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ปรับปรุงการจัดการเอกสารได้อย่างง่ายดาย
type: docs
weight: 43
url: /th/net/pdf-watermarking-attachments/replace-text-formatting-artifact-pdf/
---
## การแนะนำ
ในขอบเขตของการพัฒนา .NET การจัดการสิ่งประดิษฐ์และเอกสารลายน้ำมักเป็นงานที่สำคัญ โชคดีที่ GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนามีชุดเครื่องมือที่มีประสิทธิภาพในการผสานรวมฟังก์ชันลายน้ำและการจัดการอาร์ติแฟกต์เข้ากับแอปพลิเคชันของตนได้อย่างราบรื่น ในบทช่วยสอนที่ครอบคลุมนี้ เราจะเจาะลึกกระบวนการแทนที่ข้อความด้วยการจัดรูปแบบสำหรับส่วนต่างๆ ในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Watermark for .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark for .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: มีสภาพแวดล้อมการพัฒนาที่เข้ากันได้ที่ตั้งค่าไว้สำหรับการพัฒนา .NET
3. ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# เป็นสิ่งสำคัญที่ต้องปฏิบัติตามพร้อมกับตัวอย่าง

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //รหัสการประมวลผลเอกสารจะไปที่นี่
}
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Path"` พร้อมเส้นทางไปยังเอกสาร PDF ของคุณ
## ขั้นตอนที่ 2: เข้าถึงเนื้อหา PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
ขั้นตอนนี้จะดึงเนื้อหาของเอกสาร PDF เพื่อการประมวลผลต่อไป
## ขั้นตอนที่ 3: วนซ้ำผ่านสิ่งประดิษฐ์
```csharp
foreach (PdfArtifact artifact in pdfContent.Pages[0].Artifacts)
{
    // รหัสการประมวลผลสิ่งประดิษฐ์จะอยู่ที่นี่
}
```
ที่นี่ เราจะวนดูส่วนต่างๆ ที่ปรากฏบนหน้าแรกของเอกสาร PDF
## ขั้นตอนที่ 4: แทนที่ข้อความด้วยการจัดรูปแบบ
```csharp
if (artifact.Text.Contains("Test"))
{
    artifact.FormattedTextFragments.Clear();
    artifact.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
}
```
ในขั้นตอนนี้ เราจะตรวจสอบว่าส่วนนั้นมีข้อความ "ทดสอบ" หรือไม่ และแทนที่ด้วยข้อความที่จัดรูปแบบแล้ว
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
watermarker.Save(outputFileName);
```
สุดท้าย เราจะบันทึกเอกสาร PDF ที่แก้ไขแล้วลงในไฟล์เอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีแทนที่ข้อความด้วยการจัดรูปแบบสำหรับส่วนต่างๆ ในเอกสาร PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและใช้ประโยชน์จากคุณลักษณะอันทรงพลังของไลบรารีนี้ นักพัฒนาสามารถจัดการสิ่งประดิษฐ์และงานลายน้ำภายในแอปพลิเคชัน .NET ของตนได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET Framework 4.5 ขึ้นไป
### ฉันสามารถใช้ใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินผลได้หรือไม่
 ใช่ ใบอนุญาตชั่วคราวมีไว้เพื่อวัตถุประสงค์ในการประเมิน คุณสามารถรับหนึ่งรายการได้จาก[หน้าใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### มีการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ มีการสนับสนุนด้านเทคนิคผ่านทาง[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถปรับแต่งการจัดรูปแบบของข้อความที่ถูกแทนที่ในอาร์ติแฟกต์ PDF ได้หรือไม่
แน่นอน คุณสามารถปรับแต่งแบบอักษร ขนาด สี และคุณสมบัติการจัดรูปแบบอื่นๆ ของข้อความที่ถูกแทนที่ได้ตามความต้องการของคุณ