---
title: 在 Word 文档中添加带有文本效果的水印
linktitle: 在 Word 文档中添加带有文本效果的水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 将具有文本效果的自定义水印添加到 Word 文档。轻松记录安全性和视觉吸引力。
weight: 21
url: /zh/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Watermark for .NET 向 Word 文档添加具有文本效果的水印。通过遵循这些分步说明，您将能够使用包含各种文本效果的自定义水印来增强文档。
## 先决条件
在开始之前，请确保您具备以下条件：
1.  GroupDocs.Watermark for .NET：从以下位置下载并安装该库[网站](https://releases.groupdocs.com/Watermark/net/).
2. 文档路径：了解要添加水印的Word文档的路径。
3. 输出目录：有一个要保存修改后的文档的目录。

## 导入命名空间
确保导入必要的命名空间以访问所需的类和方法：
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 第 1 步：加载文档
加载要添加水印的Word文档。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //添加水印的代码在这里
}
```
## 第2步：添加带有文字效果的水印
使用所需的文本和字体创建文本水印，然后定义文本效果，例如线条格式。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## 第 3 步：自定义水印选项
定义水印部分选项，例如文本效果，并将它们分配给水印。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## 步骤 4：保存文档
保存修改后的文档并添加水印。
```csharp
watermarker.Save(outputFileName);
```

## 结论
向 Word 文档添加具有文本效果的水印可以显着增强其视觉吸引力和保护。借助 GroupDocs.Watermark for .NET，此过程变得简化且可自定义，使您能够高效地创建具有专业外观的文档。
## 常见问题解答
### 我可以自定义水印文字的字体和大小吗？
是的，您可以在创建 TextWatermark 对象时指定字体和大小。
### 是否可以向单个文档添加多个水印？
当然，GroupDocs.Watermark for .NET 支持向单个文档添加具有不同设置的多个水印。
### GroupDocs.Watermark 是否支持除 Word 之外的其他文档格式？
是的，它支持多种文档格式，包括 PDF、Excel、PowerPoint 等。
### 水印添加到文档后可以将其删除吗？
是的，该库提供了轻松删除文档水印的方法。
### 是否有可用于测试目的的试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).