---
title: เพิ่มลายน้ำให้กับรูปภาพส่วนในเอกสาร Word
linktitle: เพิ่มลายน้ำให้กับรูปภาพส่วนในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับรูปภาพในเอกสาร Word โดยใช้ Groupdocs ลายน้ำสำหรับ .NET ปฏิบัติตามคำแนะนำของเราเพื่อการปกป้องเอกสารที่ปลอดภัยและเป็นมืออาชีพ
weight: 16
url: /th/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
type: docs
---
# เพิ่มลายน้ำให้กับรูปภาพส่วนในเอกสาร Word

## การแนะนำ
ในโลกดิจิทัลปัจจุบัน การปกป้องเอกสารของคุณถือเป็นสิ่งสำคัญ การเพิ่มลายน้ำให้กับเอกสาร Word ของคุณเป็นวิธีที่เรียบง่ายแต่มีประสิทธิภาพในการรักษาความปลอดภัยเนื้อหาของคุณ บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการเพิ่มลายน้ำให้กับรูปภาพส่วนในเอกสาร Word โดยใช้ Groupdocs.Watermark สำหรับ .NET ไม่ว่าคุณจะเป็นนักพัฒนาที่ต้องการรวมฟีเจอร์นี้เข้ากับแอปพลิเคชันของคุณ หรือเพียงต้องการปกป้องเอกสารของคุณ คู่มือนี้เหมาะสำหรับคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกรายละเอียด ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องของคุณ
3. เอกสาร Word: เตรียมเอกสาร Word ที่คุณต้องการเพิ่มลายน้ำให้พร้อม
4. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE ที่รองรับ .NET อื่นๆ
5.  ใบอนุญาตชั่วคราว: รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) สำหรับ Groupdocs.ลายน้ำ
## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ นี่เป็นขั้นตอนสำคัญเพื่อให้แน่ใจว่าฟังก์ชันทั้งหมดของ Groupdocs.Watermark พร้อมใช้งาน
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
ตอนนี้ เรามาแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้
## ขั้นตอนที่ 1: การตั้งค่าโครงการของคุณ
ขั้นแรก ให้ตั้งค่าโปรเจ็กต์ของคุณใน IDE ที่คุณต้องการ สร้างโครงการ .NET ใหม่และติดตั้งไลบรารี Groupdocs.Watermark
```bash
dotnet add package GroupDocs.Watermark
```
## ขั้นตอนที่ 2: โหลดเอกสาร Word
โหลดเอกสาร Word ที่คุณต้องการใส่ลายน้ำ ตรวจสอบให้แน่ใจว่าเส้นทางไปยังเอกสารของคุณถูกต้อง
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 3: สร้างลายน้ำ
สร้างลายน้ำข้อความที่คุณจะนำไปใช้กับรูปภาพในเอกสาร Word ปรับแต่งข้อความ แบบอักษร ขนาด และการจัดแนวให้เหมาะกับความต้องการของคุณ
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ขั้นตอนที่ 4: ดึงรูปภาพจากส่วนแรก
เข้าถึงเนื้อหาของเอกสาร Word และค้นหารูปภาพทั้งหมดในส่วนแรก ขั้นตอนนี้มีความสำคัญเนื่องจากเป็นการระบุรูปภาพที่จะใช้ลายน้ำ
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## ขั้นตอนที่ 5: ใช้ลายน้ำกับรูปภาพ
วนซ้ำแต่ละภาพในส่วนแรกแล้วใส่ลายน้ำที่สร้างขึ้น เพื่อให้แน่ใจว่ารูปภาพทั้งหมดในส่วนนี้ได้รับการปกป้อง
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
สุดท้าย ให้บันทึกเอกสารลายน้ำไปยังเส้นทางที่ระบุ เสร็จสิ้นกระบวนการเพิ่มลายน้ำให้กับรูปภาพส่วนต่างๆ ในเอกสาร Word
```csharp
watermarker.Save(outputFileName);
```
## บทสรุป
การเพิ่มลายน้ำให้กับรูปภาพภายในเอกสาร Word ของคุณเป็นวิธีที่มีประสิทธิภาพในการปกป้องเนื้อหาของคุณ ด้วย Groupdocs.Watermark สำหรับ .NET กระบวนการนี้ตรงไปตรงมาและมีประสิทธิภาพ ทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้เพื่อให้แน่ใจว่าเอกสารของคุณปลอดภัยและได้รับการปกป้องอย่างดี
 สำหรับเอกสารรายละเอียดเพิ่มเติม โปรดไปที่[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) - หากคุณมีคำถามหรือต้องการความช่วยเหลือเพิ่มเติม โปรดดูที่[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งข้อความลายน้ำได้หรือไม่?
ใช่ คุณสามารถปรับแต่งข้อความลายน้ำ แบบอักษร ขนาด การจัดตำแหน่ง และการหมุนให้เหมาะกับความต้องการของคุณได้
### เป็นไปได้ไหมที่จะเพิ่มลายน้ำให้กับหลายส่วน?
ได้ คุณสามารถวนซ้ำแต่ละส่วนและใช้ลายน้ำกับรูปภาพในทุกส่วนได้
### ฉันสามารถใช้วิธีนี้กับเอกสารรูปแบบอื่นได้หรือไม่
 Groupdocs ลายน้ำรองรับรูปแบบเอกสารต่างๆ ตรวจสอบ[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) สำหรับรายละเอียดเพิ่มเติม
### ฉันจะขอรับใบอนุญาตชั่วคราวได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### จะเกิดอะไรขึ้นหากฉันพบปัญหาขณะใช้ Groupdocs.Watermark
 เยี่ยมชม[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19)เพื่อช่วยเหลือในทุกปัญหาที่คุณอาจพบ