---
title: รับรูปแบบไฟล์ที่รองรับ
linktitle: รับรูปแบบไฟล์ที่รองรับ
second_title: GroupDocs.Watermark .NET API
description: เพิ่มลายน้ำให้กับเอกสารของคุณได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนที่ครอบคลุมของเราเพื่อปกป้องทรัพย์สินดิจิทัลของคุณ
weight: 13
url: /th/net/document-manipulation/get-supported-file-formats/
type: docs
---
# รับรูปแบบไฟล์ที่รองรับ

## การแนะนำ
การใส่ลายน้ำในเอกสารของคุณเป็นขั้นตอนสำคัญในการปกป้องทรัพย์สินดิจิทัลของคุณ ไม่ว่าจะเป็นการปกป้องทรัพย์สินทางปัญญา การรักษาความลับ หรือเพียงแค่การสร้างแบรนด์ ลายน้ำก็มีบทบาทสำคัญ หากคุณเป็นนักพัฒนา .NET ที่ต้องการรวมความสามารถด้านลายน้ำเข้ากับแอปพลิเคชันของคุณ GroupDocs.Watermark สำหรับ .NET เป็นเครื่องมือที่ทรงพลังและอเนกประสงค์ที่คุณควรพิจารณา บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับสิ่งสำคัญของการใช้ GroupDocs.Watermark ตั้งแต่การติดตั้งไปจนถึงการใช้ลายน้ำแรกของคุณ โดยแจกแจงแต่ละขั้นตอนเพื่อให้แน่ใจว่าคุณสามารถปฏิบัติตามได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกข้อมูลเฉพาะ เรามาตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่จำเป็นในการเริ่มต้น:
1.  Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์วิชวลสตูดิโอ](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark รองรับ .NET Framework เวอร์ชันต่างๆ ตรวจสอบให้แน่ใจว่าโปรเจ็กต์ของคุณกำหนดเป้าหมายเป็นเวอร์ชันที่เข้ากันได้
3. GroupDocs.Watermark สำหรับ .NET: คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[หน้าปล่อย](https://releases.groupdocs.com/Watermark/net/).
4. ความรู้พื้นฐานของ C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นในโครงการของคุณกันก่อน เปิดไฟล์ C# ของคุณและเพิ่มสิ่งต่อไปนี้โดยใช้คำสั่งที่ด้านบน:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
เมื่อนำเข้าเนมสเปซเหล่านี้แล้ว คุณก็พร้อมที่จะเริ่มเพิ่มลายน้ำให้กับเอกสารของคุณแล้ว

## ขั้นตอนที่ 1: เริ่มต้นเอ็นจิ้นลายน้ำ
 ขั้นตอนแรกคือการเริ่มต้นเอ็นจิ้นลายน้ำ สิ่งนี้เกี่ยวข้องกับการสร้างอินสแตนซ์ของ`Watermarker` คลาสที่มีเอกสารที่คุณต้องการใส่ลายน้ำ
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 ข้อมูลโค้ดนี้ตั้งค่า`Watermarker` วัตถุที่คุณจะใช้ในการใส่ลายน้ำให้กับเอกสารของคุณ
## ขั้นตอนที่ 2: เพิ่มลายน้ำข้อความ
ตอนนี้ มาเพิ่มลายน้ำข้อความธรรมดาลงในเอกสารของคุณกันดีกว่า ลายน้ำข้อความเหมาะสำหรับการเพิ่มป้ายกำกับ เช่น "ข้อมูลลับ" หรือ "ฉบับร่าง"
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 ที่นี่เราได้สร้าง`TextWatermark`วัตถุที่มีข้อความ "เป็นความลับ" ให้ตั้งค่าแบบอักษรและสี และจัดแนวให้อยู่กึ่งกลางของเอกสาร
## ขั้นตอนที่ 3: เพิ่มลายน้ำรูปภาพ
หากคุณต้องการใช้รูปภาพเป็นลายน้ำ GroupDocs.Watermark ช่วยให้ดำเนินการดังกล่าวได้อย่างง่ายดาย
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 ในตัวอย่างนี้ เราสร้างไฟล์`ImageWatermark` วัตถุ กำหนดขนาด และจัดแนวให้อยู่ที่มุมขวาบนของเอกสาร
## ขั้นตอนที่ 4: บันทึกเอกสาร
หลังจากเพิ่มลายน้ำที่ต้องการแล้ว ขั้นตอนสุดท้ายคือบันทึกเอกสารที่แก้ไข
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 การดำเนินการนี้จะบันทึกเอกสารลายน้ำไปยังเส้นทางที่ระบุและปล่อยทรัพยากรใด ๆ ที่ใช้โดยเอกสารนั้น`Watermarker` ตัวอย่าง.
## ขั้นตอนที่ 5: รับรูปแบบไฟล์ที่รองรับ
หากต้องการดูว่า GroupDocs.Watermark รองรับรูปแบบไฟล์ใด คุณสามารถใช้ข้อมูลโค้ดต่อไปนี้:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
การดำเนินการนี้จะพิมพ์ไฟล์ทุกประเภทที่ GroupDocs.Watermark สามารถจัดการได้ ทำให้คุณเห็นความสามารถที่ครอบคลุม
## บทสรุป
การใส่ลายน้ำให้กับเอกสารของคุณด้วย GroupDocs ลายน้ำสำหรับ .NET นั้นตรงไปตรงมาและมีประสิทธิภาพ เมื่อทำตามบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีการเริ่มต้นเอ็นจิ้นลายน้ำ เพิ่มลายน้ำข้อความและรูปภาพ บันทึกเอกสารลายน้ำของคุณ และแสดงรายการรูปแบบไฟล์ที่รองรับ ด้วยเครื่องมือเหล่านี้ คุณสามารถปกป้องเอกสารของคุณได้อย่างมั่นใจ
 หากคุณมีคำถามหรือต้องการความช่วยเหลือเพิ่มเติม อย่าลังเลที่จะเยี่ยมชม[ฟอรัมสนับสนุน GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## คำถามที่พบบ่อย
### ฉันจะติดตั้ง GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 คุณสามารถดาวน์โหลดได้จาก[หน้าปล่อย](https://releases.groupdocs.com/Watermark/net/) และเพิ่ม DLL ในโครงการของคุณ
### ฉันสามารถทดลองใช้ GroupDocs.Watermark ได้ฟรีหรือไม่
 ใช่ คุณสามารถขอ[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อประเมินซอฟต์แวร์ก่อนซื้อ
### GroupDocs.Watermark รองรับไฟล์รูปแบบใดบ้าง
คุณสามารถใช้ข้อมูลโค้ดที่ให้มาเพื่อแสดงรายการรูปแบบไฟล์ที่รองรับทั้งหมด
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Watermark ได้อย่างไร
 สามารถซื้อใบอนุญาตได้โดยตรงจาก[หน้าซื้อ](https://purchase.groupdocs.com/buy).
### มีเอกสารสำหรับ GroupDocs.Watermark หรือไม่
 ใช่ มีเอกสารประกอบครบถ้วน[ที่นี่](https://tutorials.groupdocs.com/Watermark/net/).