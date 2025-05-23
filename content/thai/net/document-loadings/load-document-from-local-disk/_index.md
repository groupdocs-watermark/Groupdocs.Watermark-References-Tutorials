---
title: โหลดเอกสารจากดิสก์ภายในเครื่อง
linktitle: โหลดเอกสารจากดิสก์ภายในเครื่อง
second_title: GroupDocs.Watermark .NET API
description: ปกป้องและจัดการเอกสารของคุณด้วย Groupdocs ลายน้ำสำหรับ .NET ปฏิบัติตามคำแนะนำโดยละเอียดของเราเพื่อเพิ่มลายน้ำได้อย่างราบรื่น
weight: 10
url: /th/net/document-loadings/load-document-from-local-disk/
---

# โหลดเอกสารจากดิสก์ภายในเครื่อง

## การแนะนำ
เอกสารลายน้ำถือเป็นสิ่งสำคัญในยุคดิจิทัลปัจจุบันเพื่อให้มั่นใจในการปกป้องเนื้อหา การยืนยันความเป็นเจ้าของ และการรักษาความลับ Groupdocs.Watermark สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถเพิ่ม ค้นหา และจัดการลายน้ำในรูปแบบเอกสารต่างๆ ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการใช้ Groupdocs.Watermark สำหรับ .NET เพื่อเพิ่มลายน้ำให้กับเอกสารของคุณพร้อมคำแนะนำทีละขั้นตอนโดยละเอียด
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้งาน ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. ติดตั้ง Visual Studio แล้ว: คุณจะต้องมี Visual Studio หรือ .NET IDE อื่นที่เข้ากันได้
2.  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดไลบรารีจากไฟล์[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework 4.6.1 หรือสูงกว่า
4. เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่างเพื่อทดสอบกระบวนการใส่ลายน้ำ
## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ สิ่งเหล่านี้จำเป็นสำหรับการเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับลายน้ำ
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสารจากดิสก์ในเครื่อง
ขั้นแรก คุณต้องโหลดเอกสารจากดิสก์ภายในเครื่องของคุณ เอกสารนี้จะเป็นเอกสารที่คุณจะเพิ่มลายน้ำ
กำหนดเส้นทางของเอกสารที่คุณต้องการใส่ลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: เริ่มต้นตัวเลือกการโหลด
 ถัดไป เริ่มต้นตัวเลือกการโหลด เช่น ถ้าคุณทำงานกับเอกสาร Word คุณจะใช้`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## ขั้นตอนที่ 3: สร้างและกำหนดค่าลายน้ำ
 ตอนนี้ คุณจะสร้างอินสแตนซ์ของ`Watermarker` ระดับ. อินสแตนซ์นี้จะใช้เพื่อจัดการและใช้ลายน้ำกับเอกสารของคุณ
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // บล็อกนี้จะมีขั้นตอนเพิ่มเติมในการเพิ่มและบันทึกลายน้ำ
}
```
## ขั้นตอนที่ 4: สร้างลายน้ำ
สร้างลายน้ำข้อความ ลายน้ำนี้สามารถมีข้อความที่คุณเลือกได้ ที่นี่เราจะใช้ "ทดสอบลายน้ำ"
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## ขั้นตอนที่ 5: เพิ่มลายน้ำให้กับเอกสาร
เพิ่มลายน้ำที่สร้างขึ้นให้กับเอกสารโดยใช้`Add` วิธีการของ`Watermarker` ระดับ.
```csharp
watermarker.Add(watermark);
```
## ขั้นตอนที่ 6: บันทึกเอกสารลายน้ำ
สุดท้าย ให้บันทึกเอกสารลายน้ำไปยังเส้นทางที่ระบุ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
การเพิ่มลายน้ำให้กับเอกสารของคุณโดยใช้ Groupdocs ลายน้ำสำหรับ .NET นั้นตรงไปตรงมาและมีประสิทธิภาพ คู่มือนี้จะอธิบายคุณตลอดกระบวนการทั้งหมดตั้งแต่การตั้งค่าสภาพแวดล้อมไปจนถึงการบันทึกเอกสารที่มีลายน้ำ ด้วยเครื่องมืออันทรงพลังนี้ คุณสามารถมั่นใจได้ว่าเอกสารของคุณจะได้รับการปกป้องและทรัพย์สินทางปัญญาของคุณปลอดภัย 
 สำหรับรายละเอียดเพิ่มเติม ตรวจสอบที่[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) และหากคุณพบปัญหาใดๆ[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19) เป็นสถานที่ที่ดีเยี่ยมในการให้ความช่วยเหลือ 
## คำถามที่พบบ่อย
### ฉันสามารถใช้แบบอักษรที่กำหนดเองสำหรับลายน้ำได้หรือไม่
ใช่ Groupdocs รองรับแบบอักษรที่กำหนดเอง คุณสามารถระบุแบบอักษรใด ๆ ที่ติดตั้งบนระบบของคุณ
### รองรับเอกสารประเภทใดบ้าง?
Groupdocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย เช่น Word, Excel, PDF, PowerPoint และอื่นๆ
### ฉันจะลบลายน้ำออกจากเอกสารได้อย่างไร
 คุณสามารถใช้`Remove` วิธีการที่กำหนดโดย`Watermarker` คลาสเพื่อลบลายน้ำ
### เป็นไปได้ไหมที่จะเพิ่มลายน้ำรูปภาพ?
 ใช่ คุณสามารถเพิ่มลายน้ำรูปภาพโดยใช้`ImageWatermark` ระดับ.
### ฉันสามารถลองใช้ Groupdocs.Watermark ได้ฟรีหรือไม่
 แน่นอนคุณสามารถดาวน์โหลด[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อประเมินห้องสมุดก่อนซื้อ