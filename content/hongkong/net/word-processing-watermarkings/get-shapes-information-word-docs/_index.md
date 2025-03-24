---
title: 在 Word 文件中取得形狀訊息
linktitle: 在 Word 文件中取得形狀訊息
second_title: GroupDocs.Watermark .NET API
description: 使用 GroupDocs for .NET 輕鬆從 Word 文件中獲取有價值的見解。無縫提取形狀資訊以增強資料分析。
weight: 24
url: /zh-hant/net/word-processing-watermarkings/get-shapes-information-word-docs/
---
## 介紹
在資料為王的數位環境中，從文件中提取有意義的見解至關重要。 GroupDocs.Watermark for .NET 讓開發人員能夠深入研究文件結構，輕鬆提取有價值的資訊。在本教程中，我們將逐步探索如何利用這個強大的工具從Word文件中獲取形狀資訊。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
1.  GroupDocs.Watermark for .NET：從以下位置下載並安裝此程式庫[網站](https://releases.groupdocs.com/Watermark/net/).
2. 開發環境：設定 .NET 開發環境，包括 Visual Studio 或任何首選的文字編輯器。
3. 存取 Word 文件：可以存取您希望從中提取形狀資訊的 Word 文件。

## 導入必要的命名空間
在繼續編寫程式碼之前，必須匯入所需的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## 第 1 步：載入文檔
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
確保更換`"Your Document Path"`與 Word 文件的實際路徑。
## 第 2 步：提取形狀訊息
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
此程式碼片段取得 Word 文件的內容並迭代其中的每個部分和形狀。
## 第 3 步：分析形狀屬性
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
這部分程式碼片段檢索每個形狀的各種屬性，例如其類型、尺寸、位置、文字等。

## 結論
GroupDocs.Watermark for .NET 簡化了從 Word 文件中提取形狀資訊的過程，為開發人員提供了一個無縫的解決方案，可以輕鬆地深入研究文件結構。透過遵循本教程中概述的步驟，您可以從文件中獲得有價值的見解，從而增強您的資料分析能力。
## 常見問題解答
### GroupDocs.Watermark 是否與其他文件格式相容？
是的，GroupDocs 支援各種文件格式，包括 PDF、Excel、PowerPoint 等。
### 我可以使用 GroupDocs.Watermark 將浮水印套用到文件嗎？
當然，GroupDocs.Watermark 使您能夠輕鬆地以程式設計方式為文件添加浮水印。
### GroupDocs.Watermark 是否提供自訂文件解析的支援？
事實上，GroupDocs.Watermark 為自訂文件解析提供了靈活的選項，以適應不同的用例。
### GroupDocs.Watermark適合企業級文件處理嗎？
是的，GroupDocs.Watermark 旨在滿足企業級文件處理的需求，提供強大的功能和可擴展性。
### 我可以將 GroupDocs.Watermark 整合到我現有的 .NET 專案中嗎？
當然，GroupDocs.Watermark 可以無縫整合到 .NET 專案中，為文件操作提供全面的解決方案。