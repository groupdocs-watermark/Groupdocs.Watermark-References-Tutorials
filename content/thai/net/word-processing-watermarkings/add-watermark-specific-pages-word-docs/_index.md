---
title: เพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word
linktitle: เพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Groupdocs ปรับปรุงความปลอดภัยของเอกสารและการสร้างแบรนด์
weight: 18
url: /th/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word โดยใช้ Groupdocs.Watermark สำหรับ .NET ลายน้ำเป็นส่วนสำคัญของการจัดการเอกสาร โดยมอบความปลอดภัยและการสร้างแบรนด์ให้กับเอกสารของคุณ ด้วย Groupdocs.Watermark สำหรับ .NET คุณสามารถเพิ่มลายน้ำข้อความหรือรูปภาพลงในเอกสาร Word ของคุณได้อย่างง่ายดายอย่างแม่นยำและมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง Groupdocs.Watermark สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. เอกสาร: เตรียมเอกสาร Word ที่คุณต้องการใส่ลายน้ำให้พร้อม
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วย Visual Studio หรือเครื่องมือพัฒนา .NET อื่นๆ

## นำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกโค้ด มานำเข้าเนมสเปซที่จำเป็นก่อน:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
ขั้นแรก เราต้องโหลดเอกสาร Word ลงในวัตถุลายน้ำ
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // เพิ่มรหัสลายน้ำจะไปที่นี่
}
```
## ขั้นตอนที่ 2: เพิ่มลายน้ำ
ตอนนี้ เรามาเพิ่มลายน้ำข้อความในหน้าเฉพาะของเอกสารกันดีกว่า
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // ระบุหน้าที่จะเพิ่มลายน้ำ
};
watermarker.Add(textWatermark);
```
## ขั้นตอนที่ 3: บันทึกเอกสาร
สุดท้าย ให้บันทึกเอกสารที่ใส่ลายน้ำไว้ในตำแหน่งที่ต้องการ
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มลายน้ำให้กับหน้าเฉพาะในเอกสาร Word โดยใช้ Groupdocs.Watermark สำหรับ .NET ด้วยโค้ดเพียงไม่กี่บรรทัด คุณสามารถเพิ่มความปลอดภัยและการสร้างแบรนด์ให้กับเอกสารของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### ฉันสามารถเพิ่มลายน้ำหลายลายลงในเอกสารเดียวได้หรือไม่
ใช่ คุณสามารถเพิ่มลายน้ำได้หลายลายโดยทำซ้ำขั้นตอนการเพิ่มลายน้ำสำหรับแต่ละลายน้ำ
### Groupdocs.Watermark รองรับรูปแบบเอกสารอื่นนอกเหนือจาก Word หรือไม่
ใช่ Groupdocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### มีรุ่นทดลองใช้งานหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันสามารถปรับแต่งลักษณะของลายน้ำได้หรือไม่?
แน่นอน คุณสามารถปรับแต่งลายน้ำในด้านต่างๆ ได้ เช่น แบบอักษร ขนาด สี และความทึบ
### มีการสนับสนุนด้านเทคนิคหรือไม่?
 ใช่ คุณสามารถค้นหาการสนับสนุนทางเทคนิคและแหล่งข้อมูลได้ในฟอรัม Groupdocs[ที่นี่](https://forum.groupdocs.com/c/watermark/19).