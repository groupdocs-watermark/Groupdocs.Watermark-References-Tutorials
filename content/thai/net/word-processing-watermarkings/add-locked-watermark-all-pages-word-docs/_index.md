---
title: เพิ่มลายน้ำที่ถูกล็อคลงในทุกหน้าในเอกสาร Word
linktitle: เพิ่มลายน้ำที่ถูกล็อคลงในทุกหน้าในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: รักษาความปลอดภัยเอกสารของคุณโดยเพิ่มลายน้ำที่ล็อคไว้โดยใช้ Groupdocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการนำไปปฏิบัติที่ง่ายดาย
weight: 11
url: /th/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# เพิ่มลายน้ำที่ถูกล็อคลงในทุกหน้าในเอกสาร Word

## การแนะนำ
การเพิ่มลายน้ำให้กับเอกสารของคุณเป็นขั้นตอนสำคัญในการรักษาความปลอดภัยและสร้างแบรนด์ให้กับเนื้อหาของคุณ ไม่ว่าคุณจะป้องกันการใช้งานโดยไม่ได้รับอนุญาตหรือเพียงเพิ่มความเป็นมืออาชีพ ลายน้ำก็สามารถใช้งานได้หลายวัตถุประสงค์ ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการเพิ่มลายน้ำที่ถูกล็อคให้กับทุกหน้าของเอกสาร Word โดยใช้ Groupdocs.Watermark สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกคำแนะนำทีละขั้นตอน เรามาตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่คุณต้องการ:
1. Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดเวอร์ชันล่าสุดจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องของคุณ
3. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนาเช่น Visual Studio
4.  ใบอนุญาต: คุณสามารถเลือกรับ[ทดลองฟรี](https://releases.groupdocs.com/) หรือซื้อก[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
## นำเข้าเนมสเปซ
ก่อนอื่น คุณต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณ สิ่งเหล่านี้จำเป็นสำหรับการเข้าถึงคลาสและวิธีการที่ได้รับจาก Groupdocs.Watermark
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

เปิดสภาพแวดล้อมการพัฒนาของคุณและสร้างโครงการ .NET ใหม่ นี่อาจเป็นแอปพลิเคชันคอนโซลหรือประเภทอื่นที่เหมาะกับความต้องการของคุณ

คุณต้องเพิ่มแพ็คเกจ Groupdocs.Watermark ให้กับโปรเจ็กต์ของคุณ ซึ่งสามารถทำได้ผ่าน NuGet Package Manager รันคำสั่งต่อไปนี้ในคอนโซล NuGet Package Manager:
```sh
Install-Package GroupDocs.Watermark
```
## ขั้นตอนที่ 2: โหลดเอกสาร Word
### กำหนดเส้นทางเอกสาร
ระบุเส้นทางไปยังเอกสาร Word ของคุณ นี่จะเป็นเอกสารที่คุณต้องการเพิ่มลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### ตั้งค่าตัวเลือกการโหลด
 สร้างอินสแตนซ์ของ`WordProcessingLoadOptions` เพื่อโหลดเอกสาร Word ของคุณด้วยตัวเลือกเฉพาะ
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## ขั้นตอนที่ 3: สร้างลายน้ำ
### เริ่มต้นลายน้ำ
 ใช้`Watermarker`คลาส ให้โหลดเอกสารด้วยตัวเลือกการโหลดที่ระบุ
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // ขั้นตอนเพิ่มเติมจะอยู่ในบล็อกนี้
}
```
### กำหนดคุณสมบัติลายน้ำ
 สร้างก`TextWatermark` พร้อมข้อความ แบบอักษร และสีที่คุณต้องการ
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## ขั้นตอนที่ 4: ใช้ลายน้ำกับทุกหน้า
### ตั้งค่าตัวเลือกลายน้ำ
 กำหนด`WordProcessingWatermarkPagesOptions` และตั้งค่า`IsLocked` คุณสมบัติเป็น true เพื่อล็อคลายน้ำ เพื่อให้แน่ใจว่าไม่สามารถลบลายน้ำออกได้อย่างง่ายดาย
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### ทางเลือก: เพิ่มการป้องกันด้วยรหัสผ่าน
หากคุณต้องการเพิ่มการรักษาความปลอดภัยอีกชั้น คุณสามารถตั้งรหัสผ่านสำหรับลายน้ำได้
```csharp
// เพื่อป้องกันด้วยรหัสผ่าน
// options.รหัสผ่าน = "7654321";
```
### เพิ่มลายน้ำ
 ใช้`Add` วิธีการของ`Watermarker` คลาสเพื่อเพิ่มลายน้ำให้กับเอกสารด้วยตัวเลือกที่ระบุ
```csharp
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
สุดท้าย ให้บันทึกเอกสารที่แก้ไขไปยังไฟล์เอาท์พุตที่ระบุ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเพิ่มลายน้ำที่ถูกล็อคลงในทุกหน้าของเอกสาร Word ของคุณได้อย่างง่ายดายโดยใช้ Groupdocs.Watermark สำหรับ .NET สิ่งนี้ไม่เพียงช่วยปกป้องเอกสารของคุณจากการใช้งานโดยไม่ได้รับอนุญาต แต่ยังเพิ่มความเป็นมืออาชีพให้กับเนื้อหาของคุณอีกด้วย Groupdocs.Watermark นำเสนอโซลูชันที่ครอบคลุมสำหรับความต้องการในการใส่ลายน้ำ เพื่อให้มั่นใจว่าเอกสารของคุณยังคงปลอดภัยและมีแบรนด์
## คำถามที่พบบ่อย
### ฉันสามารถใช้รูปภาพเป็นลายน้ำแทนข้อความได้หรือไม่
 ใช่ Groupdocs ลายน้ำรองรับทั้งลายน้ำข้อความและรูปภาพ คุณสามารถแทนที่ได้`TextWatermark` กับ`ImageWatermark` และระบุภาพของคุณ
### สามารถปรับตำแหน่งของลายน้ำได้หรือไม่?
 อย่างแน่นอน! คุณสามารถกำหนดตำแหน่งของลายน้ำโดยใช้คุณสมบัติเช่น`HorizontalAlignment` และ`VerticalAlignment`.
### ฉันสามารถใช้ลายน้ำที่แตกต่างกันกับหน้าต่างๆ ของเอกสารได้หรือไม่
 ใช่ คุณสามารถปรับแต่งลายน้ำสำหรับหน้าใดหน้าหนึ่งได้โดยใช้`PageIndex` ทรัพย์สินใน`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ Groupdocs รองรับรูปแบบต่างๆ รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### ข้อกำหนดของระบบสำหรับการใช้ Groupdocs.Watermark คืออะไร
คุณต้องมีระบบที่ติดตั้ง .NET Framework และสภาพแวดล้อมการพัฒนาเช่น Visual Studio