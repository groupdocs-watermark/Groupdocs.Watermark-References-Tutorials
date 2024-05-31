---
title: ลบคำอธิบายประกอบออกจาก PDF
linktitle: ลบคำอธิบายประกอบออกจาก PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบคำอธิบายประกอบออกจาก PDF โดยใช้ GroupDocs.Watermark สำหรับ .NET ปรับปรุงความสามารถในการอ่านเอกสารได้อย่างง่ายดาย
type: docs
weight: 29
url: /th/net/pdf-watermarking-attachments/remove-annotation-pdf/
---
## การแนะนำ
คำอธิบายประกอบในเอกสาร PDF บางครั้งอาจทำให้เนื้อหาเกะกะหรือรบกวนการอ่านเอกสารได้ ด้วย GroupDocs.Watermark สำหรับ .NET คุณสามารถลบคำอธิบายประกอบออกจากไฟล์ PDF ได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Watermark สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. เส้นทางเอกสาร: มีเส้นทางไปยังเอกสาร PDF ที่คุณต้องการลบคำอธิบายประกอบ
3. Output Directory: เตรียมไดเร็กทอรีที่จะบันทึกเอกสารที่แก้ไข
4. สภาพแวดล้อม .NET: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อม .NET เพื่อรันโค้ดที่ให้มา

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงลายน้ำ GroupDocs สำหรับฟังก์ชัน .NET
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
เริ่มต้นด้วยการโหลดเอกสาร PDF โดยใช้เส้นทางเอกสารที่ให้ไว้
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ขั้นตอนที่ 2: ลบคำอธิบายประกอบ
ตอนนี้ เรามาดำเนินการลบคำอธิบายประกอบออกจากเอกสาร PDF กัน คุณมีสองทางเลือกในการลบคำอธิบายประกอบ: ตามดัชนีหรือโดยการอ้างอิง
### ลบคำอธิบายประกอบตามดัชนี
หากต้องการลบคำอธิบายประกอบตามดัชนี:
```csharp
// ลบคำอธิบายประกอบตามดัชนี
pdfContent.Pages[0].Annotations.RemoveAt(0);
```
### ลบคำอธิบายประกอบโดยการอ้างอิง
หากต้องการลบคำอธิบายประกอบโดยการอ้างอิง:
```csharp
// ลบคำอธิบายประกอบโดยการอ้างอิง
pdfContent.Pages[0].Annotations.Remove(pdfContent.Pages[0].Annotations[0]);
```
## ขั้นตอนที่ 3: บันทึกเอกสาร
หลังจากลบคำอธิบายประกอบแล้ว ให้บันทึกเอกสารที่แก้ไขไปยังไดเร็กทอรีเอาต์พุตที่ระบุ
```csharp
    watermarker.Save(outputFileName);
}
```

## บทสรุป
การลบคำอธิบายประกอบออกจากเอกสาร PDF เป็นกระบวนการที่ไม่ซับซ้อนด้วย GroupDocs.Watermark สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถจัดการคำอธิบายประกอบและเพิ่มความสามารถในการอ่านไฟล์ PDF ของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถลบคำอธิบายประกอบหลายรายการพร้อมกันได้หรือไม่
ได้ คุณสามารถวนซ้ำคำอธิบายประกอบและลบออกได้ตามต้องการโดยใช้ GroupDocs.Watermark สำหรับ .NET
### GroupDocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### คำอธิบายประกอบสามารถแก้ไขได้แทนที่จะลบออกทั้งหมดหรือไม่
ใช่ GroupDocs.Watermark มีวิธีแก้ไขคำอธิบายประกอบที่มีอยู่ด้วย
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเพิ่มเติมได้จากที่ไหน?
 คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Watermark[ที่นี่](https://forum.groupdocs.com/c/watermark/19) หากมีข้อสงสัยหรือความช่วยเหลือ