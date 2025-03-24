---
title: เพิ่มลายน้ำให้กับ XObjects ในรูปแบบ PDF
linktitle: เพิ่มลายน้ำให้กับ XObjects ในรูปแบบ PDF
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับ XObjects ใน PDF โดยใช้ Groupdocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการนำไปปฏิบัติที่ง่ายดาย
weight: 20
url: /th/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---

# เพิ่มลายน้ำให้กับ XObjects ในรูปแบบ PDF

## การแนะนำ
ลายน้ำ PDF เป็นขั้นตอนสำคัญในการทำให้แน่ใจว่าเอกสารของคุณได้รับการปกป้องจากการใช้งานโดยไม่ได้รับอนุญาต ด้วย Groupdocs.Watermark สำหรับ .NET การเพิ่มลายน้ำให้กับ XObjects ภายใน PDF ของคุณง่ายกว่าที่เคย ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการทีละขั้นตอน เพื่อให้มั่นใจว่าคุณสามารถใช้ลายน้ำกับเอกสาร PDF ของคุณได้อย่างมั่นใจ มาเริ่มกันเลย!
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทแนะนำ โปรดตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่จำเป็นในการปฏิบัติตามได้อย่างราบรื่น:
-  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้งเวอร์ชันล่าสุดจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องพัฒนาของคุณ
- สภาพแวดล้อมการพัฒนา: ใช้ Visual Studio หรือ IDE อื่น ๆ ที่รองรับการพัฒนา .NET
-  ใบอนุญาตชั่วคราว: รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) หากคุณกำลังประเมินผลิตภัณฑ์
เมื่อคุณมีข้อกำหนดเบื้องต้นเหล่านี้แล้ว คุณก็พร้อมที่จะเริ่มลายน้ำ PDF ของคุณ
## นำเข้าเนมสเปซ
ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ เปิดโครงการ C# ของคุณและเพิ่มสิ่งต่อไปนี้โดยใช้คำสั่ง:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอกสารของคุณ
ขั้นตอนแรกเกี่ยวข้องกับการตั้งค่าเส้นทางสำหรับเอกสารของคุณ กำหนดเส้นทางที่ไฟล์ PDF ของคุณตั้งอยู่ และตำแหน่งที่คุณต้องการบันทึกไฟล์ PDF ที่ใส่ลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 แทนที่`"Your Document Path"` และ`"Your Document Directory"` ด้วยเส้นทางจริงบนเครื่องของคุณ
## ขั้นตอนที่ 2: เริ่มต้นตัวเลือกการโหลด PDF
ถัดไป คุณจะต้องเริ่มต้นตัวเลือกการโหลด PDF นี่เป็นสิ่งสำคัญสำหรับการโหลดเนื้อหา PDF อย่างถูกต้อง
```csharp
var loadOptions = new PdfLoadOptions();
```
## ขั้นตอนที่ 3: โหลดเอกสาร PDF
ใช้ตัวเลือกการโหลด โหลดเอกสาร PDF ด้วย`Watermarker` ระดับ.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ขั้นตอนที่ 4: สร้างลายน้ำ
ตอนนี้ คุณต้องสร้างลายน้ำที่จะเพิ่มลงใน PDF สำหรับบทช่วยสอนนี้ เราจะสร้างลายน้ำข้อความ
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## ขั้นตอนที่ 5: เพิ่มลายน้ำให้กับ XObjects
วนซ้ำแต่ละหน้าและแต่ละ XObject ภายใน PDF เพื่อใช้ลายน้ำ
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // เพิ่มลายน้ำให้กับภาพ
            xObject.Image.Add(watermark);
        }
    }
}
```
## ขั้นตอนที่ 6: บันทึก PDF ที่ใส่ลายน้ำ
สุดท้าย ให้บันทึก PDF ที่ใส่ลายน้ำลงในไฟล์เอาท์พุตที่ระบุ
```csharp
    watermarker.Save(outputFileName);
}
```
และคุณก็ได้แล้ว! ขณะนี้ PDF ของคุณมีลายน้ำบน XObjects ทั้งหมด
## บทสรุป
 การเพิ่มลายน้ำให้กับเอกสาร PDF ของคุณโดยใช้ Groupdocs ลายน้ำสำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อนซึ่งช่วยเพิ่มระดับความปลอดภัย ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถมั่นใจได้ว่าเอกสารของคุณได้รับการปกป้องจากการใช้งานโดยไม่ได้รับอนุญาต โปรดจำไว้ว่า คุณสามารถอ้างถึง[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) สำหรับข้อมูลรายละเอียดเพิ่มเติมและคุณสมบัติขั้นสูง
## คำถามที่พบบ่อย
### ฉันสามารถใช้รูปภาพเป็นลายน้ำแทนข้อความได้หรือไม่
ใช่ Groupdocs.Watermark สำหรับ .NET รองรับทั้งลายน้ำข้อความและรูปภาพ
### ฉันจะทดสอบ Groupdocs.Watermark โดยไม่ต้องซื้อมันได้อย่างไร
 คุณสามารถใช้ก[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อประเมินผลิตภัณฑ์
### เป็นไปได้ไหมที่จะปรับแต่งรูปลักษณ์ของลายน้ำ?
อย่างแน่นอน! คุณสามารถปรับแต่งแบบอักษร ขนาด มุมการหมุน และอื่นๆ ได้
### Groupdocs.Watermark รองรับเอกสารรูปแบบอื่นหรือไม่
ใช่ รองรับรูปแบบต่าง ๆ รวมถึง Word, Excel และ PowerPoint
### ฉันจะรับการสนับสนุนได้ที่ไหนหากฉันประสบปัญหา
 คุณสามารถรับการสนับสนุนจาก[ฟอรั่ม Groupdocs](https://forum.groupdocs.com/c/watermark/19).