---
title: 保存文档到指定位置
linktitle: 保存文档到指定位置
second_title: GroupDocs.Watermark .NET API
description: 通过此分步指南，了解如何使用 GroupDocs.Watermark for .NET 轻松向文档添加水印。增强文档安全性。
weight: 11
url: /zh/net/document-savings/save-document-specified-location/
---

# 保存文档到指定位置

## 介绍
在数字时代，保护文档变得比以往任何时候都更加重要。水印是保护您的文档免遭未经授权使用的有效方法。 GroupDocs.Watermark for .NET 提供了一个强大的解决方案，用于向文档添加水印。无论您是希望将水印集成到应用程序中的开发人员还是有兴趣保护文档的开发人员，本教程都将逐步指导您完成该过程。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
- .NET 开发环境：确保安装了 Visual Studio 或任何其他 .NET 开发环境。
-  GroupDocs.Watermark for .NET 库：下载并在项目中引用该库。[下载 .NET 版 GroupDocs.Watermark](https://releases.groupdocs.com/Watermark/net/)
- C# 编程基础知识：了解基本的 C# 编程概念将会有所帮助。
- 文档到水印：准备好要应用水印的示例文档。
## 导入命名空间
在我们开始示例之前，您需要导入必要的命名空间。在代码文件顶部添加以下 using 语句：
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
让我们将使用 GroupDocs.Watermark for .NET 向文档添加水印的过程分解为可管理的步骤。按照以下步骤成功应用水印并将文档保存到指定位置。
## 第 1 步：设置您的项目
首先在 Visual Studio 中创建一个新的 .NET 项目。为了简单起见，您可以选择控制台应用程序。
1. 打开视觉工作室。
2. 选择`File`>`New`>`Project`.
3. 选择`Console App (.NET Core)`或者`Console App (.NET Framework)`.
4. 为您的项目命名并单击`Create`.

## 第 2 步：准备文档和水印文本
### 指定文档路径
定义要加水印的文档的路径。对于此示例，我们使用占位符路径。
```csharp
string documentPath = "Your Document Path";
```
### 定义输出路径
设置要保存带水印的文档的输出路径。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 第 3 步：加载文档
使用`Watermarker`类来加载您的文档。此类提供添加、删除和编辑水印的方法。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //在这里添加水印逻辑
}
```
## 第 4 步：创建并添加水印

### 创建文本水印
实例化一个`TextWatermark`具有所需文本和字体属性的对象。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### 为文档添加水印
使用以下命令将创建的水印添加到您的文档中`Add`的方法`Watermarker`班级。
```csharp
watermarker.Add(watermark);
```
## 第 5 步：保存文档
最后将带水印的文档保存到指定位置。
```csharp
watermarker.Save(outputFileName);
```
## 结论
使用 GroupDocs for .NET 对文档添加水印是一个简单的过程，可以显着增强文档的安全性。通过遵循此分步指南，您可以轻松地向文档添加水印并将其保存到您所需的位置。无论您是保护知识产权、确保文档真实性，还是只是添加专业风格，GroupDocs.Watermark for .NET 都能提供您所需的工具。
## 常见问题解答
### 我可以通过 GroupDocs.Watermark for .NET 使用图像作为水印吗？
是的，您可以通过 GroupDocs for .NET 使用文本和图像水印。该库支持各种类型的水印以满足您的需求。
### GroupDocs.Watermark for .NET 是否有免费试用版？
是的，您可以从以下位置下载免费试用版：[网站](https://releases.groupdocs.com/).
### 如何购买 GroupDocs.Watermark for .NET 的许可证？
您可以从以下位置购买许可证[购买页面](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark for .NET 支持批量水印吗？
是的，您可以通过迭代文档列表并应用水印来在批处理过程中为多个文档添加水印。
### 在哪里可以获得 GroupDocs.Watermark for .NET 的支持？
支持可在[集团文档论坛](https://forum.groupdocs.com/c/watermark/19).