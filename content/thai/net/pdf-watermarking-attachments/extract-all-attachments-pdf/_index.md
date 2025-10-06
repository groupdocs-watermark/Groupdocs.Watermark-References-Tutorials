---
title: แยกไฟล์แนบทั้งหมดออกจาก PDF
linktitle: แยกไฟล์แนบทั้งหมดออกจาก PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีแยกไฟล์แนบทั้งหมดจาก PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อกระบวนการสกัดที่ราบรื่น
weight: 22
url: /th/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
type: docs
---
# แยกไฟล์แนบทั้งหมดออกจาก PDF

## การแนะนำ
คุณต้องการแยกไฟล์แนบออกจากเอกสาร PDF ได้อย่างง่ายดายหรือไม่? คุณอยู่ในสถานที่ที่เหมาะสม! ในบทช่วยสอนที่ครอบคลุมนี้ เราจะแนะนำคุณตลอดกระบวนการแยกไฟล์แนบทั้งหมดออกจาก PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ไลบรารีอันทรงพลังนี้ช่วยให้นักพัฒนาสามารถจัดการลายน้ำในรูปแบบเอกสารต่าง ๆ ได้ แต่ยังมีความสามารถที่แข็งแกร่งในการแยกไฟล์ที่ฝังไว้อีกด้วย ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น คำแนะนำทีละขั้นตอนนี้จะทำให้กระบวนการง่ายขึ้น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกโค้ด เรามาพูดถึงข้อมูลพื้นฐานที่คุณต้องใช้ในการเริ่มต้นกันก่อน ต่อไปนี้เป็นรายการตรวจสอบสั้นๆ เพื่อให้แน่ใจว่าคุณพร้อม:
1. สภาพแวดล้อม .NET: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET แล้ว คุณสามารถใช้ Visual Studio หรือ .NET IDE อื่นๆ ได้ตามต้องการ
2.  Groupdocs.Watermark for .NET: ดาวน์โหลดและติดตั้ง Groupdocs.Watermark for .NET เวอร์ชันล่าสุดจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
3. ทักษะการพัฒนา: ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และความคุ้นเคยกับไลบรารี .NET
4. ตัวอย่างเอกสาร PDF: มีเอกสาร PDF ตัวอย่างพร้อมไฟล์แนบที่คุณสามารถใช้สำหรับการทดสอบ
## นำเข้าเนมสเปซ
ก่อนที่คุณจะเริ่มเขียนโค้ด คุณจะต้องนำเข้าเนมสเปซที่จำเป็นก่อน ซึ่งจะช่วยจัดระเบียบโค้ดของคุณและช่วยให้คุณเข้าถึงคลาสและวิธีการที่คุณจะใช้
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ
ก่อนอื่น มาตั้งค่าโครงการของคุณกันก่อน เปิดสภาพแวดล้อมการพัฒนา .NET ของคุณและสร้างแอปพลิเคชันคอนโซลใหม่
### สร้างโครงการใหม่
1. เปิด Visual Studio
2. เลือก "สร้างโครงการใหม่"
3. เลือก "แอปคอนโซล (.NET Core)" หรือ ".NET Framework" ขึ้นอยู่กับความต้องการของคุณ
4. ตั้งชื่อโครงการของคุณแล้วคลิก "สร้าง"
### เพิ่ม Groupdocs.Watermark สำหรับ .NET
1. คลิกขวาที่โครงการของคุณใน Solution Explorer
2. เลือก "จัดการแพ็คเกจ NuGet"
3. ค้นหา "Groupdocs.Watermark" และติดตั้งเวอร์ชันล่าสุด
## ขั้นตอนที่ 2: กำหนดเส้นทางของคุณ
ถัดไป คุณต้องกำหนดเส้นทางสำหรับเอกสารและไดเร็กทอรีเอาต์พุตของคุณ นี่คือที่ที่ PDF ของคุณและไฟล์แนบที่แยกออกมาจะถูกเก็บไว้

 ในตัวคุณ`Program.cs` ให้เพิ่มโค้ดต่อไปนี้เพื่อกำหนดเส้นทางของคุณ:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"` และ`"Your Document Directory"` ด้วยเส้นทางจริงในระบบของคุณ
## ขั้นตอนที่ 3: โหลดเอกสาร PDF ของคุณ
 ตอนนี้ มาโหลดเอกสาร PDF ของคุณโดยใช้ Groupdocs.Watermark กัน ขั้นตอนนี้เกี่ยวข้องกับการสร้างตัวเลือกการโหลดและการเริ่มต้น`Watermarker` ระดับ.
### สร้างตัวเลือกการโหลด
 ขั้นแรก ให้สร้างอินสแตนซ์ของ`PdfLoadOptions`-
```csharp
var loadOptions = new PdfLoadOptions();
```
### เริ่มต้นลายน้ำ
 ต่อไปให้ใช้`Watermarker` คลาสที่จะโหลดเอกสารของคุณ:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 4: แยกไฟล์แนบ
เมื่อโหลดเอกสารของคุณแล้ว ก็ถึงเวลาแตกไฟล์แนบ คุณจะใช้`PdfContent` เพื่อเข้าถึงไฟล์แนบแล้วบันทึกลงในไดเร็กทอรีเอาต์พุตที่คุณระบุ
### รับเนื้อหา PDF
 ข้างใน`using` บล็อก รับเนื้อหา PDF:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### วนซ้ำสิ่งที่แนบมา
วนซ้ำแต่ละไฟล์แนบใน PDF:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // บันทึกไฟล์ที่แนบมาลงในดิสก์
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
โค้ดนี้จะแยกแต่ละไฟล์แนบและบันทึกลงในไดเร็กทอรีเอาต์พุตของคุณ นอกจากนี้ยังพิมพ์ข้อมูลพื้นฐานเกี่ยวกับไฟล์แนบแต่ละรายการไปยังคอนโซลด้วย
## บทสรุป
และคุณก็ได้แล้ว! คุณแยกไฟล์แนบจาก PDF ได้สำเร็จโดยใช้ Groupdocs.Watermark สำหรับ .NET บทช่วยสอนนี้จะอธิบายขั้นตอนการตั้งค่าโปรเจ็กต์ โหลดเอกสาร และแตกไฟล์แนบทีละขั้นตอน ด้วยทักษะเหล่านี้ คุณสามารถจัดการและจัดการไฟล์แนบ PDF ในแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### Groupdocs.Watermark สำหรับ .NET คืออะไร
Groupdocs.Watermark for .NET เป็นไลบรารีที่ครอบคลุมสำหรับการเพิ่ม ลบ และจัดการลายน้ำในรูปแบบเอกสารต่างๆ รวมถึง PDF นอกจากนี้ยังมีความสามารถในการแตกไฟล์ที่ฝังอยู่
### ฉันสามารถแยกไฟล์ประเภทอื่นที่ฝังอยู่ใน PDF ได้หรือไม่
ใช่ Groupdocs.Watermark สำหรับ .NET ช่วยให้คุณสามารถแตกไฟล์ประเภทใดก็ได้ที่ฝังอยู่ใน PDF ไม่ใช่แค่ไฟล์แนบ
### มีการทดลองใช้ฟรีหรือไม่?
 ใช่ คุณสามารถดาวน์โหลด Groupdocs.Watermark สำหรับ .NET รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนได้อย่างไรหากฉันประสบปัญหา
 คุณสามารถรับการสนับสนุนได้โดยไปที่[Groupdocs.Watermark ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### ฉันต้องมีใบอนุญาตเพื่อใช้ Groupdocs.Watermark สำหรับ .NET หรือไม่
 ใช่ คุณต้องมีใบอนุญาตจึงจะใช้ห้องสมุดในการผลิตได้ คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy) หรือได้รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).