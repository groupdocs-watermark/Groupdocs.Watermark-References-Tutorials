---
title: เพิ่มลายน้ำรูปภาพให้กับส่วนหัวทั้งหมดในเอกสาร Word
linktitle: เพิ่มลายน้ำรูปภาพให้กับส่วนหัวทั้งหมดในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: เพิ่มลายน้ำรูปภาพให้กับส่วนหัวทั้งหมดในเอกสาร Word ได้อย่างง่ายดายโดยใช้ GroupDocs.Watermark สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ดโดยละเอียด
weight: 10
url: /th/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
---
## การแนะนำ
ลายน้ำอาจเป็นส่วนสำคัญในการจัดการเอกสาร โดยเป็นวิธีการฝังข้อมูล เช่น ความเป็นเจ้าของ การรักษาความลับ หรือการสร้างแบรนด์ลงในเอกสาร ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนต่างๆ ในการเพิ่มลายน้ำรูปภาพให้กับส่วนหัวทั้งหมดในเอกสาร Word โดยใช้ GroupDocs.Watermark สำหรับ .NET ไม่ว่าคุณจะเพิ่งเริ่มเขียนโปรแกรมหรือเป็นนักพัฒนาที่มีประสบการณ์ คู่มือนี้จะช่วยให้คุณบรรลุเป้าหมายเรื่องลายน้ำได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกโค้ด เราต้องแน่ใจว่าเรามีทุกสิ่งที่เราต้องการก่อน ต่อไปนี้เป็นรายการตรวจสอบเพื่อช่วยคุณเริ่มต้น:
1.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดเวอร์ชันล่าสุดจาก[ที่นี่](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE ที่รองรับ .NET อื่นๆ
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework แล้ว
4. ตัวอย่างเอกสาร Word: เอกสาร Word ที่คุณต้องการเพิ่มลายน้ำ
5. รูปภาพสำหรับลายน้ำ: ไฟล์รูปภาพที่คุณต้องการใช้เป็นลายน้ำ
เมื่อคุณพร้อมแล้ว เราก็สามารถเริ่มตั้งโครงการของเราได้
## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นกันก่อน เนมสเปซเหล่านี้มีคลาสและวิธีการที่จะช่วยเราทำงานกับลายน้ำในเอกสารของเรา
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ขั้นตอนที่ 1: การตั้งค่าโครงการของคุณ
ในการเริ่มต้น ให้สร้างแอปพลิเคชันคอนโซลใหม่ใน Visual Studio เพิ่มการอ้างอิงถึง GroupDocs.Watermark DLL ในโครงการของคุณ ซึ่งสามารถทำได้โดยการติดตั้งแพ็คเกจ GroupDocs.Watermark NuGet
```bash
Install-Package GroupDocs.Watermark
```
## ขั้นตอนที่ 2: โหลดเอกสารของคุณ
 ขั้นตอนแรกในการเพิ่มลายน้ำคือการโหลดเอกสารที่จะเพิ่มลายน้ำ ในที่นี้เราจะใช้`WordProcessingLoadOptions` เพื่อโหลดเอกสาร Word
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // รหัสสำหรับใส่ลายน้ำจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างลายน้ำรูปภาพ
ต่อไปเราจะสร้างลายน้ำรูปภาพ ซึ่งเกี่ยวข้องกับการระบุไฟล์รูปภาพที่คุณต้องการใช้เป็นลายน้ำ
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // รหัสสำหรับใส่ลายน้ำจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 4: เพิ่มลายน้ำให้กับส่วนหัวของส่วนแรก
 เราจำเป็นต้องเพิ่มลายน้ำให้กับส่วนหัวทั้งหมดในส่วนแรกของเอกสาร Word สำหรับสิ่งนี้เราใช้`WordProcessingWatermarkSectionOptions` และระบุดัชนีส่วน
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## ขั้นตอนที่ 5: เชื่อมโยงส่วนหัวและส่วนท้าย
เพื่อให้แน่ใจว่าลายน้ำจะปรากฏในส่วนหัวของทุกส่วน เราจะเชื่อมโยงส่วนหัวและส่วนท้ายอื่นๆ ทั้งหมดเข้ากับส่วนหัวและส่วนท้ายของส่วนแรก
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## ขั้นตอนที่ 6: บันทึกเอกสาร
สุดท้าย เราจะบันทึกเอกสารที่มีลายน้ำไว้ในเส้นทางที่ระบุ ขั้นตอนนี้ช่วยให้แน่ใจว่าการเปลี่ยนแปลงของคุณถูกเขียนลงในไฟล์ใหม่ โดยคงเอกสารต้นฉบับไว้
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## บทสรุป
และคุณก็ได้แล้ว! คุณได้เพิ่มลายน้ำรูปภาพลงในส่วนหัวทั้งหมดในเอกสาร Word สำเร็จแล้วโดยใช้ GroupDocs.Watermark สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้ง่ายต่อการจัดการและใส่ลายน้ำกับเอกสารประเภทต่าง ๆ ทำให้มั่นใจได้ว่าเนื้อหาของคุณจะได้รับการปกป้องและมีแบรนด์อย่างมืออาชีพ
## คำถามที่พบบ่อย
### ฉันสามารถใช้ลายน้ำประเภทอื่นนอกเหนือจากรูปภาพได้หรือไม่
ใช่ GroupDocs รองรับลายน้ำข้อความ รูปภาพ และแม้กระทั่งลายน้ำผสม
### เป็นไปได้ไหมที่จะใส่ลายน้ำส่วนอื่นๆ ของเอกสารนอกเหนือจากส่วนหัว
อย่างแน่นอน! คุณสามารถใส่ลายน้ำส่วนท้าย เนื้อหา และแม้แต่หน้าหรือส่วนที่ต้องการได้
### GroupDocs.Watermark รองรับเอกสารรูปแบบอื่นหรือไม่
ใช่ รองรับรูปแบบที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอีกมากมาย
### ฉันสามารถปรับแต่งตำแหน่งและลักษณะของลายน้ำได้หรือไม่?
ได้ คุณสามารถปรับแต่งขนาด ตำแหน่ง ความทึบ และคุณสมบัติอื่นๆ ของลายน้ำได้
### GroupDocs.Watermark มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).