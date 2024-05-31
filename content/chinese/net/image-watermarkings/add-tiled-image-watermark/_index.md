---
title: 添加平铺图像水印
linktitle: 添加平铺图像水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 将平铺图像水印添加到文档中。简单、高效且可定制。
type: docs
weight: 10
url: /zh/net/image-watermarkings/add-tiled-image-watermark/
---
## 介绍
GroupDocs.Watermark for .NET 是一个功能强大的 API，允许开发人员以编程方式添加、删除和搜索各种文档格式的水印。在本教程中，我们将指导您完成使用 GroupDocs.Watermark for .NET 将平铺图像水印添加到文档的过程。
## 先决条件
在开始之前，请确保您具备以下条件：
- C# 编程语言的基础知识。
- Visual Studio 安装在您的系统上。
- GroupDocs.Watermark for .NET 库已添加到您的项目中。您可以从以下位置下载：[这里](https://releases.groupdocs.com/Watermark/net/).

## 导入命名空间
确保在 C# 文件的开头导入必要的命名空间：
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 第1步：设置文档路径和输出目录
定义输入文档的路径和要保存输出文档的目录：
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
代替`"Your Document Path"`输入文档的绝对或相对路径。
## 第2步：初始化水印对象
使用输入文档路径创建 Watermarker 对象：
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //在此添加水印
}
```
## 步骤3：添加平铺图像水印
使用要用作水印的图像文件的路径实例化 ImageWatermark 对象：
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    //配置图块选项
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    //为文档添加水印
    watermarker.Add(watermark);
    //保存修改后的文档
    watermarker.Save(outputFileName);
}
```
代替`"Path to Your Image"`与水印图像文件的实际路径。

## 结论
通过执行以下步骤，您可以使用 GroupDocs.Watermark for .NET 轻松地将平铺图像水印添加到文档中。尝试不同的选项和配置以获得所需的结果。
## 常见问题解答
### 我可以在单个文档中添加多个水印吗？
是的，您可以使用 GroupDocs.Watermark for .NET 将多个不同类型的水印添加到文档中。
### GroupDocs.Watermark 支持所有文档格式吗？
GroupDocs.Watermark 支持多种文档格式，包括 PDF、Word、Excel、PowerPoint 等。
### GroupDocs.Watermark 是否有试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 我可以自定义水印的外观吗？
是的，您可以自定义水印的各个方面，例如位置、大小、旋转、透明度等。
### GroupDocs.Watermark 提供技术支持吗？
是的，您可以从 GroupDocs.Watermark 论坛获得技术支持[这里](https://forum.groupdocs.com/c/watermark/19).