---
title: แทนที่ข้อความด้วยการจัดรูปแบบสำหรับ XObject ใน PDF
linktitle: แทนที่ข้อความด้วยการจัดรูปแบบสำหรับ XObject ใน PDF
second_title: GroupDocs.Watermark .NET API
description: ปรับปรุงความสามารถในการจัดการเอกสาร .NET ของคุณด้วย GroupDocs Watermark สำหรับ .NET เรียนรู้วิธีแทนที่ข้อความด้วยการจัดรูปแบบใน PDF ได้อย่างง่ายดาย
weight: 45
url: /th/net/pdf-watermarking-attachments/replace-text-formatting-xobject-pdf/
type: docs
---
# แทนที่ข้อความด้วยการจัดรูปแบบสำหรับ XObject ใน PDF

## การแนะนำ
ในขอบเขตของการจัดการและจัดการเอกสาร GroupDocs.Watermark สำหรับ .NET มีความโดดเด่นในฐานะโซลูชันที่แข็งแกร่งสำหรับนักพัฒนา .NET ที่ต้องการจัดการลายน้ำ ข้อความ และรูปภาพภายในรูปแบบเอกสารต่างๆ บทช่วยสอนนี้จะเจาะลึกถึงหนึ่งในคุณสมบัติอันทรงพลังของมัน: การแทนที่ข้อความด้วยการจัดรูปแบบสำหรับ XObject ใน PDF ในตอนท้ายของคู่มือนี้ คุณจะพร้อมที่จะรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: มีการตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสม โดยเฉพาะ Visual Studio หรือ IDE ที่เข้ากันได้กับ .NET
3. เอกสาร: เตรียมเอกสาร PDF ที่คุณต้องการแทนที่ข้อความด้วยการจัดรูปแบบ

## นำเข้าเนมสเปซ
ในโปรเจ็กต์ .NET ของคุณ ตรวจสอบให้แน่ใจว่าคุณนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ประโยชน์จากฟังก์ชัน GroupDocs.Watermark:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร PDF
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
 ให้แน่ใจว่าคุณเปลี่ยน`"Your Document Path"`พร้อมเส้นทางไปยังไฟล์ PDF ของคุณและระบุไดเร็กทอรีเอาต์พุตสำหรับเอกสารที่แก้ไข
## ขั้นตอนที่ 2: เข้าถึงเนื้อหา PDF
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfXObject xObject in pdfContent.Pages[0].XObjects)
    {
```
 ใช้`GetContent<PdfContent>()` วิธีการเข้าถึงเนื้อหาของเอกสาร PDF วนซ้ำ XObjects ของหน้าแรก
## ขั้นตอนที่ 3: แทนที่ข้อความด้วยการจัดรูปแบบ
```csharp
        // แทนที่ข้อความ
        if (xObject.Text.Contains("Test"))
        {
            xObject.FormattedTextFragments.Clear();
            xObject.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
```
ตรวจสอบว่า XObject มีข้อความที่คุณต้องการแทนที่หรือไม่ หากพบ ให้ล้างส่วนของข้อความที่มีอยู่และเพิ่มข้อความที่จัดรูปแบบใหม่
## ขั้นตอนที่ 4: บันทึกเอกสาร
```csharp
    // บันทึกเอกสาร
    watermarker.Save(outputFileName);
}
```
บันทึกเอกสารที่แก้ไขไปยังไดเร็กทอรีเอาต์พุตที่ระบุ

## บทสรุป
GroupDocs.Watermark สำหรับ .NET มอบวิธีที่ราบรื่นในการแทนที่ข้อความด้วยการจัดรูปแบบสำหรับ XObject ในเอกสาร PDF เมื่อทำตามบทช่วยสอนนี้ คุณได้เรียนรู้วิธีรวมฟังก์ชันนี้เข้ากับแอปพลิเคชัน .NET ของคุณ ซึ่งช่วยเพิ่มความสามารถในการจัดการเอกสารของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก PDF ได้หรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### GroupDocs.Watermark มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/).
### ฉันสามารถปรับแต่งการจัดรูปแบบของข้อความที่ถูกแทนที่ได้หรือไม่
คุณสามารถควบคุมการจัดรูปแบบได้อย่างเต็มที่ รวมถึงขนาดตัวอักษร สไตล์ สี และอื่นๆ อีกมากมาย
### GroupDocs.Watermark ให้การสนับสนุนทางเทคนิคหรือไม่
 ใช่ คุณสามารถขอความช่วยเหลือด้านเทคนิคได้จาก[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### GroupDocs.Watermark เหมาะสำหรับใช้ในเชิงพาณิชย์หรือไม่
 ใช่ คุณสามารถซื้อใบอนุญาตได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy) เพื่อใช้ในเชิงพาณิชย์