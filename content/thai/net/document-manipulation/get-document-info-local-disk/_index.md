---
title: รับข้อมูลเอกสารจาก Local Disk
linktitle: รับข้อมูลเอกสารจาก Local Disk
second_title: GroupDocs.Watermark .NET API
description: เรียนรู้วิธีเพิ่ม ลบ และแยกลายน้ำในเอกสารโดยใช้ GroupDocs ลายน้ำสำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนที่ครอบคลุมนี้
weight: 11
url: /th/net/document-manipulation/get-document-info-local-disk/
---
## การแนะนำ
ยินดีต้อนรับสู่คำแนะนำขั้นสุดยอดเกี่ยวกับการใช้ GroupDocs.Watermark สำหรับ .NET! ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น บทความนี้จะแนะนำคุณเกี่ยวกับสิ่งสำคัญของการใส่ลายน้ำในเอกสารของคุณด้วยเครื่องมืออันทรงพลังนี้ ในตอนท้าย คุณจะเป็นมืออาชีพในการฝังลายน้ำในเอกสารของคุณ ทำให้มั่นใจได้ว่าลายน้ำเหล่านั้นได้รับการปกป้องและสร้างแบรนด์ตามข้อกำหนดเฉพาะของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกคำแนะนำทีละขั้นตอน มีข้อกำหนดเบื้องต้นบางประการที่คุณจะต้องปฏิบัติตาม:
1.  .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนระบบของคุณ GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET Framework เวอร์ชันต่างๆ ดังนั้นให้ตรวจสอบ[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) สำหรับรายละเอียดความเข้ากันได้
2.  GroupDocs.Watermark สำหรับ .NET Library: ดาวน์โหลดและติดตั้งเวอร์ชันล่าสุดจาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
3. สภาพแวดล้อมการพัฒนา: คุณควรมีการตั้งค่าสภาพแวดล้อมการพัฒนา Visual Studio เป็นตัวเลือกยอดนิยมสำหรับการพัฒนา .NET
4. ความรู้พื้นฐาน C#: การทำความเข้าใจพื้นฐานของการเขียนโปรแกรม C# จะช่วยให้คุณทำตามตัวอย่างได้
## นำเข้าเนมสเปซ
ก่อนที่คุณจะสามารถใช้ GroupDocs.Watermark สำหรับ .NET ได้ คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณก่อน นี่เป็นกระบวนการที่ไม่ซับซ้อนและจำเป็นสำหรับการเข้าถึงคุณลักษณะต่างๆ ของห้องสมุด
```csharp
using System;
using GroupDocs.Watermark.Common;
```
เรามาแจกแจงขั้นตอนการใส่ลายน้ำในเอกสารเป็นขั้นตอนที่ชัดเจนและจัดการได้ แต่ละขั้นตอนได้รับการออกแบบมาเพื่อช่วยให้คุณเข้าใจและใช้งานฟังก์ชันต่างๆ ได้อย่างง่ายดาย
## ขั้นตอนที่ 1: โหลดเอกสารของคุณ
 ขั้นตอนแรกคือการโหลดเอกสารที่คุณต้องการใส่ลายน้ำ นี้จะกระทำโดยใช้`Watermarker` คลาสซึ่งช่วยให้คุณเข้าถึงและจัดการเอกสารของคุณได้
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // ขณะนี้เอกสารได้รับการโหลดและพร้อมสำหรับการใส่ลายน้ำแล้ว
}
```
 ในขั้นตอนนี้ ให้เปลี่ยน`"Your Document Path"` พร้อมเส้นทางจริงไปยังเอกสารของคุณ สิ่งนี้จะเริ่มต้น`Watermarker`วัตถุทำให้คุณสามารถเข้าถึงฟังก์ชันลายน้ำต่างๆ
## ขั้นตอนที่ 2: รับข้อมูลเอกสาร
ก่อนที่จะเพิ่มลายน้ำ คุณอาจต้องการรวบรวมข้อมูลบางอย่างเกี่ยวกับเอกสาร สิ่งนี้มีประโยชน์สำหรับการปรับแต่งลายน้ำของคุณตามคุณสมบัติของเอกสาร

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 ในขั้นตอนนี้`GetDocumentInfo` วิธีการดึงรายละเอียดเช่นประเภทไฟล์ จำนวนหน้า และขนาดเอกสาร ข้อมูลนี้ถูกพิมพ์ไปยังคอนโซล แต่คุณสามารถใช้ในแอปพลิเคชันของคุณได้ตามต้องการ
## ขั้นตอนที่ 3: เพิ่มลายน้ำข้อความ
เมื่อคุณโหลดเอกสารและข้อมูลเรียบร้อยแล้ว ก็ถึงเวลาเพิ่มลายน้ำ เราจะเริ่มต้นด้วยลายน้ำข้อความธรรมดา

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 ที่นี่คุณสร้าง`TextWatermark` วัตถุด้วยข้อความ แบบอักษร และสไตล์ที่คุณต้องการ ปรับคุณสมบัติ เช่น สี ความทึบ และมุมการหมุนให้เหมาะกับความต้องการของคุณ สุดท้าย ลายน้ำจะถูกเพิ่มลงในเอกสารและบันทึกลงในเส้นทางที่ระบุ
## ขั้นตอนที่ 4: เพิ่มลายน้ำรูปภาพ
ลายน้ำข้อความเป็นสิ่งที่ดี แต่ถ้าคุณต้องการเพิ่มโลโก้หรือรูปภาพอื่นล่ะ ขั้นตอนนี้ครอบคลุมถึงวิธีการเพิ่มลายน้ำรูปภาพ

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 แทนที่`"Path to Your Image"` พร้อมเส้นทางไปยังภาพลายน้ำของคุณ ตั้งค่าคุณสมบัติ เช่น ความทึบและมุมการหมุน เพื่อปรับแต่งลักษณะที่ปรากฏของลายน้ำรูปภาพของคุณ กระบวนการเพิ่มและบันทึกลายน้ำจะคล้ายกับลายน้ำข้อความ
## ขั้นตอนที่ 5: ลบลายน้ำที่มีอยู่
 บางครั้ง คุณอาจต้องลบลายน้ำที่มีอยู่ออกจากเอกสาร ซึ่งสามารถทำได้โดยใช้`Remove` วิธีการที่กำหนดโดย`Watermarker` ระดับ.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 นี่.`Remove` วิธีการใช้ในการลบลายน้ำข้อความออกจากเอกสาร คุณสามารถระบุลายน้ำประเภทต่างๆ ที่จะลบได้ เช่น รูปภาพหรือข้อความ ขึ้นอยู่กับความต้องการของคุณ บันทึกเอกสารไปยังเส้นทางใหม่เพื่อดูการเปลี่ยนแปลง
## ขั้นตอนที่ 6: แยกลายน้ำ
หากคุณต้องการแยกและตรวจสอบลายน้ำจากเอกสาร GroupDocs.Watermark สำหรับ .NET จะช่วยให้สิ่งนี้เป็นไปได้อย่างง่ายดาย

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // คุณสมบัติและตรรกะเพิ่มเติมสำหรับลายน้ำแต่ละอัน
    }
}
```
 ขั้นตอนนี้เกี่ยวข้องกับการใช้`GetWatermarks`วิธีการดึงลายน้ำทั้งหมดในเอกสาร จากนั้นคุณสามารถวนซ้ำรายการลายน้ำและตรวจสอบคุณสมบัติหรือดำเนินการเพิ่มเติมได้ตามต้องการ
## บทสรุป
 ยินดีด้วย! ตอนนี้คุณได้เรียนรู้วิธีใช้ GroupDocs.Watermark สำหรับ .NET เพื่อเพิ่ม ลบ และแยกลายน้ำออกจากเอกสารของคุณแล้ว ด้วยทักษะเหล่านี้ คุณสามารถปกป้องและสร้างแบรนด์เอกสารของคุณได้อย่างมีประสิทธิภาพ จำไว้.[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) พร้อมให้บริการเสมอหากคุณต้องการข้อมูลโดยละเอียดเพิ่มเติมหรือฟังก์ชันการทำงานขั้นสูง
## คำถามที่พบบ่อย
### ฉันสามารถใช้ GroupDocs.Watermark สำหรับ .NET กับ .NET เวอร์ชันใดก็ได้ได้หรือไม่
 ใช่ GroupDocs.Watermark สำหรับ .NET เข้ากันได้กับ .NET Framework เวอร์ชันต่างๆ ตรวจสอบ[เอกสารประกอบ](https://tutorials.groupdocs.com/Watermark/net/) สำหรับข้อมูลเฉพาะ
### ฉันจะดาวน์โหลด GroupDocs.Watermark สำหรับ .NET ได้ที่ไหน
 คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/Watermark/net/).
### ฉันจะรับใบอนุญาตชั่วคราวได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[หน้าใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### มีการทดลองใช้ฟรีหรือไม่?
 ใช่ คุณสามารถเริ่มทดลองใช้ฟรีได้โดยไปที่[หน้าทดลองใช้ฟรี](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนได้ที่ไหนหากฉันประสบปัญหา
 การสนับสนุนมีอยู่ที่[ฟอรัมลายน้ำ GroupDocs](https://forum.groupdocs.com/c/watermark/19).