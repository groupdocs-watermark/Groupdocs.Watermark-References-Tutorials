---
title: รับข้อมูลรูปร่างในเอกสาร Word
linktitle: รับข้อมูลรูปร่างในเอกสาร Word
second_title: GroupDocs.Watermark .NET API
description: ปลดล็อกข้อมูลเชิงลึกอันมีค่าจากเอกสาร Word ได้อย่างง่ายดายด้วย GroupDocs Watermark สำหรับ .NET แยกข้อมูลรูปร่างได้อย่างลงตัวเพื่อการวิเคราะห์ข้อมูลที่ได้รับการปรับปรุง
weight: 24
url: /th/net/word-processing-watermarkings/get-shapes-information-word-docs/
---
## การแนะนำ
ในโลกดิจิทัลที่ข้อมูลเป็นสิ่งสำคัญที่สุด การแยกข้อมูลเชิงลึกที่มีความหมายจากเอกสารเป็นสิ่งสำคัญยิ่ง GroupDocs.Watermark สำหรับ .NET ช่วยให้นักพัฒนาสามารถเจาะลึกโครงสร้างเอกสาร และดึงข้อมูลอันมีค่าออกมาได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ประโยชน์จากเครื่องมืออันทรงพลังนี้เพื่อรับข้อมูลรูปร่างจากเอกสาร Word ทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Watermark สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[เว็บไซต์](https://releases.groupdocs.com/Watermark/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET รวมถึง Visual Studio หรือโปรแกรมแก้ไขข้อความที่ต้องการ
3. เข้าถึงเอกสาร Word: เข้าถึงเอกสาร Word ที่คุณต้องการดึงข้อมูลรูปร่าง

## การนำเข้าเนมสเปซที่จำเป็น
ก่อนที่จะดำเนินการโค้ดต่อไป จำเป็นต้องนำเข้าเนมสเปซที่จำเป็นก่อน:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Path"` ด้วยเส้นทางจริงไปยังเอกสาร Word ของคุณ
## ขั้นตอนที่ 2: แยกข้อมูลรูปร่าง
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
ตัวอย่างนี้จะดึงเนื้อหาของเอกสาร Word และวนซ้ำแต่ละส่วนและรูปร่างภายใน
## ขั้นตอนที่ 3: วิเคราะห์คุณลักษณะรูปร่าง
```csharp
			if (shape.HeaderFooter != null)
			{
				Console.WriteLine("In header/footer");
			}
			Console.WriteLine(shape.ShapeType);
			Console.WriteLine(shape.Width);
			Console.WriteLine(shape.Height);
			Console.WriteLine(shape.IsWordArt);
			Console.WriteLine(shape.RotateAngle);
			Console.WriteLine(shape.AlternativeText);
			Console.WriteLine(shape.Name);
			Console.WriteLine(shape.X);
			Console.WriteLine(shape.Y);
			Console.WriteLine(shape.Text);
			if (shape.Image != null)
			{
				Console.WriteLine(shape.Image.Width);
				Console.WriteLine(shape.Image.Height);
				Console.WriteLine(shape.Image.GetBytes().Length);
			}
			Console.WriteLine(shape.HorizontalAlignment);
			Console.WriteLine(shape.VerticalAlignment);
			Console.WriteLine(shape.RelativeHorizontalPosition);
			Console.WriteLine(shape.RelativeVerticalPosition);
		}
	}
}
```
ส่วนนี้ของข้อมูลโค้ดจะดึงแอตทริบิวต์ต่างๆ ของแต่ละรูปร่าง เช่น ประเภท ขนาด ตำแหน่ง ข้อความ และอื่นๆ

## บทสรุป
GroupDocs.Watermark สำหรับ .NET ช่วยให้การแยกข้อมูลรูปร่างจากเอกสาร Word ง่ายขึ้น ช่วยให้นักพัฒนามีโซลูชันที่ราบรื่นในการเจาะลึกโครงสร้างเอกสารได้อย่างง่ายดาย ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถปลดล็อกข้อมูลเชิงลึกอันมีค่าจากเอกสารของคุณ และเพิ่มความสามารถในการวิเคราะห์ข้อมูลของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Watermark เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ GroupDocs รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### ฉันสามารถใช้ลายน้ำกับเอกสารโดยใช้ GroupDocs.Watermark ได้หรือไม่
GroupDocs.Watermark ช่วยให้คุณสามารถเพิ่มลายน้ำให้กับเอกสารโดยทางโปรแกรมได้อย่างง่ายดาย
### GroupDocs.Watermark รองรับการแยกวิเคราะห์เอกสารแบบกำหนดเองหรือไม่
GroupDocs.Watermark มีตัวเลือกที่ยืดหยุ่นสำหรับการแยกวิเคราะห์เอกสารแบบกำหนดเองเพื่อให้เหมาะกับกรณีการใช้งานที่หลากหลาย
### GroupDocs.Watermark เหมาะสำหรับการประมวลผลเอกสารระดับองค์กรหรือไม่
ใช่ GroupDocs.Watermark ได้รับการออกแบบมาเพื่อตอบสนองความต้องการการประมวลผลเอกสารระดับองค์กร โดยนำเสนอฟีเจอร์ที่แข็งแกร่งและความสามารถในการปรับขนาด
### ฉันสามารถรวม GroupDocs.Watermark เข้ากับโปรเจ็กต์ .NET ที่มีอยู่ของฉันได้หรือไม่
แน่นอนว่า GroupDocs.Watermark ผสานรวมเข้ากับโปรเจ็กต์ .NET ได้อย่างราบรื่น มอบโซลูชันที่ครอบคลุมสำหรับการจัดการเอกสาร