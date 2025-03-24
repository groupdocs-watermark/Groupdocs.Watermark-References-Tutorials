---
title: รับขนาด PDF
linktitle: รับขนาด PDF
second_title: GroupDocs.Watermark .NET API
description: ปกป้องเอกสารของคุณอย่างง่ายดายโดยใช้ Groupdocs.Watermark สำหรับ .NET เพิ่มลายน้ำ ตราประทับ และคำอธิบายประกอบได้อย่างง่ายดาย
weight: 26
url: /th/net/pdf-watermarking-attachments/get-pdf-dimensions/
---

# รับขนาด PDF

## การแนะนำ
ในยุคดิจิทัลปัจจุบัน การปกป้องเอกสารของคุณเป็นสิ่งสำคัญยิ่ง ไม่ว่าคุณจะเป็นนักธุรกิจ ผู้เชี่ยวชาญด้านกฎหมาย หรือศิลปินที่มีความคิดสร้างสรรค์ การปกป้องทรัพย์สินทางปัญญาของคุณถือเป็นสิ่งสำคัญ Groupdocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพในการเพิ่มลายน้ำ ตราประทับ และคำอธิบายประกอบให้กับเอกสารของคุณ เพื่อให้มั่นใจในความปลอดภัยและความถูกต้อง
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำดิ่งสู่โลกของ Groupdocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  การติดตั้ง Groupdocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้ง Groupdocs.Watermark สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
2.  รหัสใบอนุญาต (ไม่บังคับ): แม้ว่า Groupdocs.Watermark สำหรับ .NET จะมีให้ทดลองใช้ฟรี แต่คุณสามารถเลือกรับใบอนุญาตชั่วคราวหรือซื้อใบอนุญาตแบบเต็มได้จาก[ที่นี่](https://purchase.groupdocs.com/buy) เพื่อการใช้งานที่ขยายออกไป
3. ความคุ้นเคยกับ C#: แนะนำให้มีความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# เพื่อทำความเข้าใจและนำตัวอย่างที่ให้มาไปใช้
4. เอกสารที่จะป้องกัน: เตรียมเอกสารตัวอย่าง (เช่น PDF, Word, Excel) ให้พร้อมบนเครื่องท้องถิ่นของคุณเพื่อทำการทดลอง

## นำเข้าเนมสเปซ
หากต้องการเริ่มทำงานกับ Groupdocs.Watermark สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### ขั้นตอนที่ 1: ประกาศตัวแปร
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### ขั้นตอนที่ 2: โหลดเอกสาร
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### ขั้นตอนที่ 3: รับเนื้อหา PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### ขั้นตอนที่ 4: ดึงข้อมูลมิติ
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## บทสรุป
โดยสรุป Groupdocs.Watermark สำหรับ .NET นำเสนอโซลูชันที่ครอบคลุมเพื่อปกป้องเอกสารของคุณจากการใช้และการแจกจ่ายโดยไม่ได้รับอนุญาต ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้นและใช้ประโยชน์จาก Groupdocs.Watermark สำหรับ .NET คุณสามารถมั่นใจในความปลอดภัยและความสมบูรณ์ของสินทรัพย์ดิจิทัลอันมีค่าของคุณได้
## คำถามที่พบบ่อย
### ฉันสามารถใช้ Groupdocs.Watermark สำหรับ .NET ได้ฟรีหรือไม่
ใช่ Groupdocs.Watermark สำหรับ .NET มีเวอร์ชันทดลองใช้ฟรีเพื่อวัตถุประสงค์ในการประเมินผล อย่างไรก็ตาม สำหรับฟังก์ชันการทำงานเพิ่มเติม คุณอาจพิจารณาซื้อใบอนุญาตแบบเต็ม
### Groupdocs.Watermark รองรับเอกสารหลายรูปแบบหรือไม่
ใช่ Groupdocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถปรับแต่งลายน้ำและแสตมป์ด้วย Groupdocs.Watermark ได้หรือไม่
อย่างแน่นอน! Groupdocs.Watermark มีตัวเลือกการปรับแต่งลายน้ำ ตราประทับ และคำอธิบายประกอบที่ครอบคลุมเพื่อให้เหมาะกับความต้องการเฉพาะของคุณ
### มีการสนับสนุนด้านเทคนิคสำหรับผู้ใช้ Groupdocs.Watermark หรือไม่
 ใช่ คุณสามารถรับความช่วยเหลือด้านเทคนิคและมีส่วนร่วมกับชุมชน Groupdocs ได้ผ่านทาง[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/watermark/19).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ Groupdocs.Watermark ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวสำหรับ Groupdocs.Watermark ได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).