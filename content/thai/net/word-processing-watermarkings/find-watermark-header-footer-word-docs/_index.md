---
title: ค้นหาลายน้ำในส่วนหัว/ท้ายกระดาษในเอกสาร Word
linktitle: ค้นหาลายน้ำในส่วนหัว/ท้ายกระดาษในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีค้นหาและลบลายน้ำออกจากเอกสาร Word อย่างมีประสิทธิภาพโดยใช้ GroupDocs สำหรับ .NET เพื่อให้มั่นใจถึงความสมบูรณ์ของเอกสารและความเป็นมืออาชีพ
weight: 22
url: /th/net/word-processing-watermarkings/find-watermark-header-footer-word-docs/
---

# ค้นหาลายน้ำในส่วนหัว/ท้ายกระดาษในเอกสาร Word

## การแนะนำ
ในโลกของการจัดการและการป้องกันเอกสาร ลายน้ำมีบทบาทสำคัญ ไม่ว่าจะเพื่อวัตถุประสงค์ในการสร้างแบรนด์ การคุ้มครองลิขสิทธิ์ หรือการติดตามเอกสาร การเพิ่มลายน้ำให้กับเอกสารของคุณถือเป็นสิ่งสำคัญ อย่างไรก็ตาม การค้นหาและลบลายน้ำอย่างมีประสิทธิภาพ โดยเฉพาะอย่างยิ่งในชุดเอกสารขนาดใหญ่ อาจเป็นงานที่น่ากังวล นี่คือจุดที่ GroupDocs.Watermark สำหรับ .NET เข้ามามีบทบาท ในบทช่วยสอนนี้ เราจะเจาะลึกวิธีค้นหาลายน้ำในส่วนหัวและส่วนท้ายของเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET โดยแจกแจงรายละเอียดแต่ละขั้นตอนเพื่อให้แน่ใจว่ามีความเข้าใจที่ครอบคลุม
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. GroupDocs.Watermark for .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและกำหนดค่าไลบรารี GroupDocs.Watermark for .NET ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดห้องสมุดได้จาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. เข้าถึงเอกสาร Word: เข้าถึงเอกสาร Word ที่มีลายน้ำที่คุณต้องการจัดการ
3. ความรู้พื้นฐานของ C#: ทำความคุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C# เนื่องจากบทช่วยสอนนี้จะเกี่ยวข้องกับโค้ด C#
## นำเข้าเนมสเปซ
ก่อนที่จะเริ่มต้นใช้งานโค้ด ให้นำเข้าเนมสเปซที่จำเป็น:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอกสารและชื่อไฟล์เอาท์พุต
ขั้นแรก กำหนดเส้นทางของเอกสารที่มีลายน้ำและชื่อไฟล์เอาต์พุตที่จะบันทึกเอกสารที่แก้ไข
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ขั้นตอนที่ 2: เริ่มต้นลายน้ำ
 เริ่มต้น`Watermarker` วัตถุที่มีเส้นทางเอกสารและตัวเลือกการโหลด
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสสำหรับการจัดการลายน้ำจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: กำหนดเกณฑ์การค้นหา
กำหนดเกณฑ์การค้นหาเพื่อค้นหาลายน้ำ ซึ่งอาจขึ้นอยู่กับรูปภาพหรือข้อความ
```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## ขั้นตอนที่ 4: ค้นหาลายน้ำ
ค้นหาลายน้ำในส่วนหัวหลักของเอกสารโดยใช้เกณฑ์การค้นหาที่กำหนดไว้
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
PossibleWatermarkCollection possibleWatermarks = content.Sections[0]
                                                        .HeadersFooters[OfficeHeaderFooterType.HeaderPrimary]
                                                        .Search(textSearchCriteria.Or(imageSearchCriteria));
```
## ขั้นตอนที่ 5: ลบลายน้ำ
ลบลายน้ำที่พบทั้งหมดออกจากเอกสาร
```csharp
for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
{
    possibleWatermarks.RemoveAt(i);
}
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
บันทึกเอกสารที่แก้ไขโดยมีลายน้ำที่ถูกลบออก
```csharp
watermarker.Save(outputFileName);
```

## บทสรุป
GroupDocs.Watermark for .NET มอบโซลูชันที่มีประสิทธิภาพสำหรับการค้นหาและลบลายน้ำออกจากเอกสาร Word ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถค้นหาและกำจัดลายน้ำจากส่วนหัวและส่วนท้ายได้อย่างมีประสิทธิภาพ รับประกันความสมบูรณ์และความเป็นมืออาชีพของเอกสารของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ GroupDocs.Watermark รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, PDF และอีกมากมาย
### ฉันสามารถปรับแต่งเกณฑ์การค้นหาลายน้ำได้หรือไม่
GroupDocs.Watermark มีเกณฑ์การค้นหาที่ยืดหยุ่น ช่วยให้คุณสามารถค้นหาลายน้ำตามพารามิเตอร์ต่างๆ เช่น ข้อความ รูปภาพ รูปร่าง หรือคุณสมบัติของวัตถุ
### GroupDocs.Watermark จะรักษารูปแบบเอกสารต้นฉบับไว้หรือไม่
ใช่ GroupDocs.Watermark ช่วยให้มั่นใจได้ว่าการจัดรูปแบบต้นฉบับของเอกสารยังคงสภาพเดิมในขณะที่ลบลายน้ำออกไป โดยรักษาความสวยงามและเค้าโครงของเอกสาร
### GroupDocs.Watermark เหมาะสำหรับการประมวลผลเอกสารเป็นชุดหรือไม่
แน่นอนว่า GroupDocs.Watermark มี API สำหรับการประมวลผลเป็นชุด ช่วยให้คุณสามารถจัดการเอกสารหลายฉบับพร้อมกันได้อย่างง่ายดาย
### ฉันจะขอความช่วยเหลือหรือสนับสนุน GroupDocs.Watermark ได้ที่ไหน
 หากมีข้อสงสัยหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Watermark คุณสามารถไปที่[GroupDocs ฟอรั่มลายน้ำ](https://forum.groupdocs.com/c/watermark/19) หรือติดต่อทีมสนับสนุน