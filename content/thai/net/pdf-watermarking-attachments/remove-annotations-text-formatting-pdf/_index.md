---
title: ลบคำอธิบายประกอบด้วยการจัดรูปแบบข้อความเฉพาะในรูปแบบ PDF
linktitle: ลบคำอธิบายประกอบด้วยการจัดรูปแบบข้อความเฉพาะในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบคำอธิบายประกอบด้วยการจัดรูปแบบข้อความเฉพาะในเอกสาร PDF โดยใช้ Groupdocs
weight: 30
url: /th/net/pdf-watermarking-attachments/remove-annotations-text-formatting-pdf/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการลบคำอธิบายประกอบที่มีการจัดรูปแบบข้อความเฉพาะในเอกสาร PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ไลบรารีนี้มีคุณสมบัติที่มีประสิทธิภาพสำหรับการทำงานกับลายน้ำ คำอธิบายประกอบ และองค์ประกอบเอกสารอื่น ๆ ในรูปแบบต่างๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  Groupdocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET ที่ตั้งค่าบนเครื่องของคุณ
3. เอกสาร PDF: มีเอกสาร PDF พร้อมคำอธิบายประกอบที่คุณต้องการแก้ไข

## การนำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร PDF
```csharp
string documentPath = "YourDocumentPath";
string outputDirectory = "YourDocumentDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 2: รับเนื้อหา PDF และวนซ้ำผ่านหน้าต่างๆ
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfPage page in pdfContent.Pages)
    {
```
## ขั้นตอนที่ 3: วนซ้ำคำอธิบายประกอบและตรวจสอบการจัดรูปแบบข้อความ
```csharp
        for (int i = page.Annotations.Count - 1; i >= 0; i--)
        {
            foreach (FormattedTextFragment fragment in page.Annotations[i].FormattedTextFragments)
            {
```
## ขั้นตอนที่ 4: ลบคำอธิบายประกอบด้วยการจัดรูปแบบข้อความเฉพาะ
```csharp
                if (fragment.Font.FamilyName == "Verdana")
                {
                    page.Annotations.RemoveAt(i);
                    break;
                }
            }
        }
    }
```
## ขั้นตอนที่ 5: บันทึกเอกสาร PDF ที่แก้ไข
```csharp
    watermarker.Save(outputFileName);
}
```
ตอนนี้ คุณได้ลบคำอธิบายประกอบที่มีการจัดรูปแบบข้อความเฉพาะออกจากเอกสาร PDF ของคุณโดยใช้ Groupdocs.Watermark สำหรับ .NET เรียบร้อยแล้ว

## บทสรุป
Groupdocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่สะดวกสำหรับการทำงานกับคำอธิบายประกอบและองค์ประกอบอื่นๆ ในเอกสาร PDF เมื่อทำตามบทช่วยสอนนี้ คุณสามารถจัดการคำอธิบายประกอบตามการจัดรูปแบบข้อความเฉพาะได้อย่างง่ายดาย ช่วยเพิ่มความสามารถในการอ่านและรูปลักษณ์ของไฟล์ PDF ของคุณ
## คำถามที่พบบ่อย
### ฉันสามารถใช้ Groupdocs.Watermark สำหรับ .NET กับเอกสารรูปแบบอื่นได้หรือไม่
ใช่ Groupdocs.Watermark รองรับรูปแบบเอกสารหลากหลาย รวมถึง DOCX, PPTX, XLSX, PDF และอื่นๆ
### Groupdocs.Watermark สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง Groupdocs.Watermark สำหรับ .NET รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ Groupdocs.Watermark for .NET ได้ที่ไหน
 คุณสามารถดูเอกสารประกอบโดยละเอียดและข้อมูลอ้างอิง API ได้[ที่นี่](https://tutorials.groupdocs.com/Watermark/net/).
### ฉันจะรับการสนับสนุนสำหรับปัญหาหรือข้อสงสัยที่เกี่ยวข้องกับ Groupdocs.Watermark ได้อย่างไร
 คุณสามารถโพสต์คำถามหรือปัญหาของคุณได้ในฟอรัม Groupdocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถซื้อใบอนุญาตชั่วคราวสำหรับ Groupdocs.Watermark สำหรับ .NET ได้หรือไม่
 ใช่ คุณสามารถซื้อใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).