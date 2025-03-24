---
title: เพิ่มลายน้ำที่ล็อคไว้ในส่วนในเอกสาร Word
linktitle: เพิ่มลายน้ำที่ล็อคไว้ในส่วนในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำที่ล็อคไว้ในส่วนเฉพาะในเอกสาร Word โดยใช้ Groupdocs ลายน้ำสำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนที่ครอบคลุมนี้
weight: 13
url: /th/net/word-processing-watermarkings/add-locked-watermark-section-word-docs/
---

# เพิ่มลายน้ำที่ล็อคไว้ในส่วนในเอกสาร Word

## การแนะนำ
คุณกำลังมองหาวิธีที่มีประสิทธิภาพในการเพิ่มลายน้ำที่ล็อคไว้ให้กับส่วนในเอกสาร Word ของคุณหรือไม่? ไม่ต้องมองอีกต่อไป! ด้วย Groupdocs.Watermark สำหรับ .NET คุณสามารถแทรกลายน้ำลงในเอกสาร Word ได้อย่างราบรื่น ในขณะเดียวกันก็รับประกันว่าลายน้ำจะยังคงล็อคและป้องกันการงัดแงะ เครื่องมืออันทรงพลังนี้นำเสนอฟีเจอร์ที่หลากหลายเพื่อตอบสนองความต้องการลายน้ำของคุณ ไม่ว่าจะเป็นเพื่อการสร้างแบรนด์ การรักษาความลับ หรือการรักษาความปลอดภัย ในบทช่วยสอนทีละขั้นตอนนี้ เราจะอธิบายวิธีการเพิ่มลายน้ำที่ถูกล็อคให้กับส่วนเฉพาะของเอกสาร Word โดยใช้ Groupdocs.Watermark สำหรับ .NET มาดำน้ำกันเถอะ!
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  Groupdocs.Watermark สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Groupdocs.Watermark แล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่า .NET Framework ไว้ในสภาพแวดล้อมการพัฒนาของคุณ
3. IDE: ใช้สภาพแวดล้อมการพัฒนาแบบรวม (IDE) เช่น Visual Studio
4. เอกสาร: เอกสาร Word (.docx) เพื่อใช้ลายน้ำ
## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ ต่อไปนี้เป็นวิธีดำเนินการ:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสารของคุณ
 ขั้นแรก คุณต้องโหลดเอกสารที่คุณต้องการเพิ่มลายน้ำ ขั้นตอนนี้เกี่ยวข้องกับการระบุเส้นทางของเอกสารของคุณและโหลดโดยใช้`Watermarker` ระดับ.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสลายน้ำของคุณจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: สร้างลายน้ำ
จากนั้น สร้างลายน้ำที่คุณต้องการเพิ่มลงในเอกสารของคุณ ในตัวอย่างนี้ เราจะสร้างลายน้ำข้อความพร้อมการตั้งค่าแบบอักษรและสีเฉพาะ
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกลายน้ำ
ตอนนี้ กำหนดค่าตัวเลือกลายน้ำเพื่อระบุดัชนีส่วนและการตั้งค่าการล็อค เพื่อให้แน่ใจว่าลายน้ำจะถูกเพิ่มไปยังส่วนที่ถูกต้องและถูกล็อค
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.SectionIndex = 0; // เพิ่มไปยังส่วนแรก
options.IsLocked = true; // ล็อคลายน้ำ
options.LockType = WordProcessingLockType.ReadOnlyWithEditableContent; // ประเภทล็อค
```
## ขั้นตอนที่ 4: เพิ่มลายน้ำลงในเอกสาร
 เมื่อกำหนดค่าลายน้ำและตัวเลือกของคุณแล้ว ก็ถึงเวลาเพิ่มลายน้ำลงในเอกสารโดยใช้`Add` วิธีการของ`Watermarker` ระดับ.
```csharp
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไข
สุดท้าย ให้บันทึกเอกสารที่มีลายน้ำเพิ่มไปยังตำแหน่งเอาต์พุตที่คุณต้องการ
```csharp
watermarker.Save(outputFileName);
```
## บทสรุป
การเพิ่มลายน้ำที่ล็อคไว้ในส่วนเฉพาะในเอกสาร Word โดยใช้ Groupdocs ลายน้ำสำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อน เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเพิ่มความปลอดภัยและความสมบูรณ์ของเอกสารได้ ทำให้มั่นใจได้ว่าข้อมูลสำคัญได้รับการปกป้อง ไม่ว่าคุณจะปกป้องข้อมูลที่ละเอียดอ่อนหรือเพิ่มความเป็นมืออาชีพให้กับเอกสารของคุณ Groupdocs.Watermark สำหรับ .NET ก็มีเครื่องมือที่คุณต้องการเพื่อให้บรรลุเป้าหมายอย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### Groupdocs.Watermark สำหรับ .NET คืออะไร
Groupdocs.Watermark สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถเพิ่มลายน้ำให้กับเอกสารประเภทต่างๆ รวมถึง Word, PDF และรูปภาพ พร้อมการปรับแต่งขั้นสูงและคุณสมบัติความปลอดภัย
### ฉันสามารถล็อคลายน้ำด้วยรหัสผ่านได้หรือไม่?
 ใช่ คุณสามารถป้องกันลายน้ำด้วยรหัสผ่านได้โดยการตั้งค่า`options.Password` ทรัพย์สินใน`WordProcessingWatermarkSectionOptions` ระดับ.
### เป็นไปได้ไหมที่จะใช้ลายน้ำที่แตกต่างกันกับส่วนต่างๆ ของเอกสาร
 อย่างแน่นอน! โดยการตั้งค่าที่แตกต่างกัน`SectionIndex` ค่านิยมใน`WordProcessingWatermarkSectionOptions`คุณสามารถใส่ลายน้ำเฉพาะให้กับส่วนต่างๆ ของเอกสารได้
### ลายน้ำประเภทใดที่ฉันสามารถเพิ่มได้โดยใช้ Groupdocs.Watermark
Groupdocs.Watermark รองรับลายน้ำหลายประเภท รวมถึงลายน้ำข้อความ รูปภาพ และรูปร่าง โดยเสนอตัวเลือกการปรับแต่งที่หลากหลายสำหรับแต่ละประเภท
### ฉันจะหาข้อมูลเพิ่มเติมเกี่ยวกับ Groupdocs.Watermark สำหรับ .NET ได้ที่ไหน
 สำหรับข้อมูลเพิ่มเติมสามารถเยี่ยมชมได้ที่[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) และ[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).