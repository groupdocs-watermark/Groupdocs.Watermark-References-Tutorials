---
title: ค้นหารูปภาพในไฟล์แนบของ PDF
linktitle: ค้นหารูปภาพในไฟล์แนบของ PDF
second_title: GroupDocs.Watermark .NET API
description: ค้นหารูปภาพภายในไฟล์แนบ PDF อย่างมีประสิทธิภาพโดยใช้ GroupDocs.Watermark สำหรับ .NET ลดความซับซ้อนของกระบวนการจัดการลายน้ำของคุณได้อย่างง่ายดาย
type: docs
weight: 46
url: /th/net/pdf-watermarking-attachments/search-image-attachment-pdf/
---
## การแนะนำ
GroupDocs.Watermark สำหรับ .NET เป็น API ที่ทรงพลังซึ่งออกแบบมาเพื่ออำนวยความสะดวกในการจัดการและจัดการลายน้ำในรูปแบบเอกสารต่างๆ รวมถึง PDF ได้อย่างราบรื่น ไม่ว่าคุณจะต้องเพิ่ม ลบ หรือค้นหาลายน้ำในไฟล์แนบ PDF เครื่องมืออเนกประสงค์นี้ก็นำเสนอโซลูชั่นที่ครอบคลุม
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้ GroupDocs.Watermark สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา .NET: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้บนเครื่องของคุณ
2.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Watermark สำหรับ .NET จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
3. เอกสารพร้อมไฟล์แนบ PDF: เตรียมเอกสาร PDF ที่มีไฟล์แนบพร้อมรูปภาพสำหรับการค้นหาลายน้ำ
4. ความเข้าใจพื้นฐานของการเขียนโปรแกรม C#: ทำความคุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C# เพื่อติดตามพร้อมกับตัวอย่าง

## นำเข้าเนมสเปซ
ก่อนที่จะใช้ GroupDocs.Watermark สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโค้ด C# ของคุณ:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search.Objects;
```
## ขั้นตอนที่ 1: โหลดเอกสารและตั้งค่าไฟล์เอาท์พุต
ขั้นแรก ระบุเส้นทางของเอกสารที่คุณต้องการค้นหาลายน้ำและกำหนดเส้นทางไฟล์เอาต์พุต:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการโหลด
เริ่มต้นตัวเลือกการโหลด โดยเฉพาะหากเอกสารของคุณเป็น PDF ขั้นตอนนี้ช่วยให้มั่นใจได้ถึงการจัดการไฟล์แนบ PDF อย่างเหมาะสม:
```csharp
var loadOptions = new PdfLoadOptions();
```
## ขั้นตอนที่ 3: เริ่มต้นลายน้ำ
 สร้างก`Watermarker` วัตถุโดยผ่านเส้นทางเอกสารและตัวเลือกการโหลด:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 4: ตั้งค่าวัตถุที่ค้นหาได้
ระบุประเภทของออบเจ็กต์ที่จะค้นหาภายในเอกสาร ในกรณีนี้ เราเน้นที่รูปภาพที่แนบมาภายใน PDF:
```csharp
watermarker.SearchableObjects.PdfSearchableObjects = PdfSearchableObjects.AttachedImages;
```
## ขั้นตอนที่ 5: ค้นหาลายน้ำ
 เรียกใช้`GetImages()` วิธีค้นหารูปภาพที่สามารถใส่ลายน้ำภายในเอกสารได้:
```csharp
WatermarkableImageCollection possibleWatermarks = watermarker.GetImages();
```
## ขั้นตอนที่ 6: ผลลัพธ์ผลลัพธ์
สุดท้าย แสดงจำนวนภาพที่ค้นพบ:
```csharp
Console.WriteLine("Found {0} image(s).", possibleWatermarks.Count);
```

## บทสรุป
GroupDocs.Watermark สำหรับ .NET มอบวิธีที่ตรงไปตรงมาแต่ทรงพลังในการค้นหารูปภาพภายในไฟล์แนบ PDF ด้วยการทำตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณสามารถรวมฟังก์ชันการค้นหาลายน้ำเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Watermark สามารถค้นหาลายน้ำในรูปแบบเอกสารอื่นนอกเหนือจาก PDF ได้หรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึงเอกสาร Word, สเปรดชีต Excel, งานนำเสนอ PowerPoint และอื่นๆ
### GroupDocs.Watermark มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Watermark ได้อย่างไร
 สำหรับการสนับสนุนและความช่วยเหลือคุณสามารถเยี่ยมชมได้ที่[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19).
### ฉันสามารถซื้อใบอนุญาตชั่วคราวสำหรับ GroupDocs.Watermark ได้หรือไม่
 ใช่ คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[หน้าซื้อใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Watermark มีตัวเลือกการปรับแต่งสำหรับการวางลายน้ำหรือไม่
GroupDocs.Watermark มอบคุณสมบัติการปรับแต่งที่ครอบคลุมสำหรับการวางลายน้ำ รวมถึงตำแหน่ง ขนาด การหมุน และอื่นๆ อีกมากมาย