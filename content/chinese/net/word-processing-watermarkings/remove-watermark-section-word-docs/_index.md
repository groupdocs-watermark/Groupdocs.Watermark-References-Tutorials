---
title: 从 Word 文档中的部分中删除水印
linktitle: 从 Word 文档中的部分中删除水印
second_title: GroupDocs.Watermark .NET API
description: 了解如何使用 GroupDocs.Watermark for .NET 从 Word 文档中的特定部分删除水印。此处提供综合教程。
type: docs
weight: 32
url: /zh/net/word-processing-watermarkings/remove-watermark-section-word-docs/
---
## 介绍
在数字时代，保护文档的完整性至关重要，尤其是涉及敏感信息或专有内容时。水印是一种常用的技术，用于声明所有权、品牌标识或简单地指示文档的状态。然而，在某些情况下，由于编辑要求或隐私问题，有必要删除水印。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Watermark for .NET 库：从以下位置下载并安装 GroupDocs.Watermark for .NET 库[这里](https://releases.groupdocs.com/Watermark/net/).
2. 带水印的文档：准备一个包含要删除的水印的Word文档。

## 导入命名空间
在开始编码之前，让我们导入必要的命名空间来访问 GroupDocs.Watermark 的功能：
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## 第 1 步：加载文档
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 第 2 步：初始化搜索条件
```csharp
    //初始化搜索条件
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## 第三步：搜索水印
```csharp
    //调用该部分的搜索方法
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    PossibleWatermarkCollection possibleWatermarks = content.Sections[0].Search(textSearchCriteria.Or(imageSearchCriteria));
```
## 第 4 步：删除水印
```csharp
    //删除所有找到的水印
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
```
## 第 5 步：保存文档
```csharp
    watermarker.Save(outputFileName);
}
```
认真执行这些步骤将使您能够使用 GroupDocs.Watermark for .NET 有效地从 Word 文档中的特定部分删除水印。

## 结论
总之，GroupDocs.Watermark for .NET 为开发人员提供了管理各种文档格式中的水印的无缝解决方案。通过遵循概述的教程，您可以轻松地从目标部分删除水印，确保文档完整性并满足不同的业务需求。
## 常见问题解答
### GroupDocs.Watermark 是否与除 Word 之外的其他文档格式兼容？
是的，GroupDocs.Watermark 支持多种文档格式，包括 PDF、Excel、PowerPoint 等。
### 我可以自定义水印识别的搜索条件吗？
当然，GroupDocs.Watermark 提供灵活的搜索条件，允许您根据您的特定需求定制搜索过程。
### GroupDocs.Watermark 是否提供批处理支持？
是的，您可以使用 GroupDocs.Watermark 以批处理模式高效处理多个文档，从而简化您的工作流程。
### GroupDocs.Watermark 适合个人和企业使用吗？
事实上，GroupDocs.Watermark 可满足个人用户、小型企业和大型企业的需求，提供可扩展的解决方案。
### GroupDocs.Watermark 多久更新一次？
GroupDocs 定期更新其产品以纳入新功能、增强功能和兼容性改进，确保最佳性能和可靠性。