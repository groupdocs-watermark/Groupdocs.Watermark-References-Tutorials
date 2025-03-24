---
title: ลบรูปร่างในเอกสาร Word
linktitle: ลบรูปร่างในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีลบรูปร่างออกจากเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET การจัดการเอกสารที่ง่าย มีประสิทธิภาพ และทรงพลัง
weight: 30
url: /th/net/word-processing-watermarkings/remove-shape-word-docs/
---
## การแนะนำ
ในขอบเขตของการประมวลผลและการจัดการเอกสาร GroupDocs.Watermark สำหรับ .NET กลายเป็นชุดเครื่องมืออันทรงพลัง ช่วยให้นักพัฒนาสามารถรวมฟังก์ชันลายน้ำเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น บทความนี้เจาะลึกความซับซ้อนของการใช้ประโยชน์จาก GroupDocs.Watermark สำหรับ .NET เพื่อลบรูปร่างภายในเอกสาร Word ด้วยการทำตามคำแนะนำทีละขั้นตอน นักพัฒนาสามารถเข้าใจกระบวนการได้อย่างง่ายดายและมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มต้นการเดินทางของการลบรูปร่างในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET โปรดตรวจสอบให้แน่ใจว่าได้มีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. รับ GroupDocs.Watermark สำหรับ .NET
 เริ่มต้นด้วยการรับไลบรารี GroupDocs.Watermark สำหรับ .NET คุณสามารถดาวน์โหลดห้องสมุดได้จาก[หน้าปล่อย](https://releases.groupdocs.com/Watermark/net/).
### 2. ความคุ้นเคยกับการพัฒนา .NET
ความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา .NET ถือเป็นสิ่งสำคัญ ตรวจสอบให้แน่ใจว่าคุณมีความเชี่ยวชาญในการเขียนโปรแกรม C# และมีความเข้าใจพื้นฐานในการทำงานกับไลบรารีและการขึ้นต่อกันในระบบนิเวศ .NET
### 3. สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE)
ติดตั้ง IDE เช่น Visual Studio บนระบบของคุณ เพื่อให้มีสภาพแวดล้อมที่เอื้ออำนวยสำหรับการพัฒนา .NET 
### 4. ตัวอย่างเอกสาร Word
เตรียมเอกสาร Word ตัวอย่างที่มีรูปร่างที่คุณต้องการลบ เอกสารนี้จะทำหน้าที่เป็นพื้นที่ทดสอบสำหรับการใช้งานของคุณ

## นำเข้าเนมสเปซ
หากต้องการเริ่มต้นกระบวนการลบรูปร่างในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
เริ่มต้นด้วยการระบุเส้นทางไปยังเอกสาร Word ที่คุณต้องการจัดการและสร้างชื่อไฟล์เอาต์พุตสำหรับเอกสารที่ประมวลผล:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำ
 เริ่มต้นก`Watermarker` วัตถุโดยผ่านเส้นทางเอกสารและตัวเลือกการโหลดเพิ่มเติม:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ขั้นตอนที่ 3: เข้าถึงเนื้อหาเอกสาร
ดึงเนื้อหาของเอกสาร Word เพื่อเข้าถึงส่วนและรูปร่าง:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ขั้นตอนที่ 4: ลบรูปร่างตามดัชนี
 ลบรูปร่างออกจากเอกสารโดยระบุดัชนีภายใน`Shapes` ของสะสม:
```csharp
content.Sections[0].Shapes.RemoveAt(0);
```
## ขั้นตอนที่ 5: ลบรูปร่างโดยการอ้างอิง
 อีกทางหนึ่ง ลบรูปร่างโดยการอ้างอิงโดยตรงภายใน`Shapes` ของสะสม:
```csharp
content.Sections[0].Shapes.Remove(content.Sections[0].Shapes[0]);
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
บันทึกเอกสารที่แก้ไขไปยังไฟล์เอาต์พุตที่ระบุ:
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
โดยสรุป GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนาสามารถจัดการเอกสาร Word ได้อย่างง่ายดาย ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณสามารถลบรูปร่างออกจากเอกสาร Word ของคุณได้อย่างราบรื่น ซึ่งจะช่วยปรับปรุงเวิร์กโฟลว์การประมวลผลเอกสารของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สำหรับ .NET สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก Word ได้หรือไม่
ใช่ GroupDocs.Watermark สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Excel, PowerPoint, PDF และอื่นๆ
### GroupDocs.Watermark สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Watermark สำหรับ .NET รุ่นทดลองใช้ฟรีได้จาก[หน้าปล่อย](https://releases.groupdocs.com/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark สำหรับ .NET ได้อย่างไร
 สามารถรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark สำหรับ .NET ได้จาก[หน้าใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะหาเอกสารและการสนับสนุนสำหรับ GroupDocs.Watermark สำหรับ .NET ได้ที่ไหน
 เอกสารและทรัพยากรสนับสนุนสำหรับ GroupDocs.Watermark สำหรับ .NET มีอยู่ใน[ฟอรั่ม](https://forum.groupdocs.com/c/watermark/19) และ[หน้าอ้างอิง](https://tutorials.groupdocs.com/Watermark/net/).
### .NET เวอร์ชันใดบ้างที่เข้ากันได้กับ GroupDocs.Watermark
GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET เวอร์ชันต่างๆ รวมถึง .NET Framework และ .NET Core