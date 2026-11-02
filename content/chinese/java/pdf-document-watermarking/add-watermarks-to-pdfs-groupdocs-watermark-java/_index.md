---
date: '2026-01-23'
description: 学习如何使用 GroupDocs.Watermark for Java 为 PDF 文件添加文字和图片水印——PDF 文档安全的完整指南。
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: 如何使用 GroupDocs.Watermark for Java 为 PDF 添加水印
type: docs
url: /zh/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# 使用 GroupDocs.Watermark for Java 为 PDF 添加水印

在当今的数字世界，**如何为 PDF 添加水印** 是所有需要保护知识产权或品牌资产的人的常见问题。添加文字或图片水印可以帮助您强化 **PDF 文档安全**，并使未经授权的分发变得更加困难。在本教程中，您将一步步学习如何使用 **GroupDocs.Watermark for Java** 为 PDF 文档添加文字和图片水印。

## 快速答案
- **哪个库可以在 Java 中为 PDF 添加水印？** GroupDocs.Watermark for Java。  
- **我可以同时添加文字和图片水印吗？** 可以，API 支持两种类型。  
- **需要许可证吗？** 免费试用可用于评估；付费许可证可去除限制。  
- **需要哪个 Java 版本？** JDK 8 或更高。  
- **支持 Maven 吗？** 当然——只需添加仓库和依赖即可。

## 什么是 PDF 水印以及为何使用它？
为 PDF 添加水印会嵌入可见或不可见的标记，用以标识所有权、保密性或品牌。它是一种轻量但强大的方式，可阻止复制、证明作者身份，并符合企业政策。

## 前置条件

在开始之前，请确保您已具备：

1. 已在机器上安装 **Java Development Kit (JDK) 8+**。  
2. **GroupDocs.Watermark for Java**（最新版本）。  
3. **Maven**（或手动添加 JAR 的能力）。

### 环境配置

#### Maven 配置
在 `pom.xml` 中添加 GroupDocs 仓库和 watermark 依赖：

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

#### 直接下载
如果不想使用 Maven，可以直接从 [GroupDocs.Watermark for Java 发布版](https://releases.groupdocs.com/watermark/java/) 下载 JAR。

### 许可证获取
要开始免费试用或获取临时许可证，请访问 [GroupDocs 许可证](https://purchase.groupdocs.com/temporary-license)。生产环境使用请购买订阅以解锁全部功能。

## 设置 GroupDocs.Watermark for Java

导入驱动所有水印操作的核心类：

```java
import com.groupdocs.watermark.Watermarker;
```

此导入让您能够使用 `Watermarker` 类，它是向任何受支持文档类型添加水印的入口点。

## 步骤实现

下面我们将过程划分为逻辑章节：创建文字水印、创建图片水印，最后将它们应用到 PDF 中的图片上。

### 1. 初始化文字水印

**为什么使用文字水印？** 它轻量、可搜索，非常适合添加版权声明或保密声明。

#### 1.1 创建 TextWatermark 实例
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 设置对齐方式
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 旋转水印
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 配置大小
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. 初始化图片水印

**何时使用图片水印？** 适合使用徽标进行品牌化或添加复杂的视觉图案。

#### 2.1 加载图片文件
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 设置对齐方式
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 旋转图片水印
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 配置大小
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. 为 PDF 中的图片添加水印

现在我们把所有内容组合起来：打开 PDF，定位每张图片，并根据尺寸应用文字或图片水印。

#### 3.1 打开 PDF 文档
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 获取所有图片
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 有条件地应用水印
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 释放图片资源
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 保存修改后的 PDF
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 清理工作
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## PDF 水印的实际应用

| 用例 | 水印的帮助方式 |
|----------|------------------------|
| **文档安全** | 标记机密文件，防止泄漏。 |
| **品牌保护** | 在营销 PDF 中嵌入徽标，强化品牌形象。 |
| **版权声明** | 添加作者姓名或 © 符号以主张所有权。 |
| **版本控制** | 在页面上直接显示版本号或日期。 |

## 常见陷阱与技巧

- **路径分隔符：** 在 Windows 上使用双反斜杠 (`\\`) 或在 Linux/macOS 上使用正斜杠 (`/`) 以避免 `FileNotFoundException`。  
- **大文件 PDF：** 将图片分批处理或增大 JVM 堆大小 (`-Xmx2g`) 以防止 OutOfMemory 错误。  
- **许可证限制：** 试用版可能限制处理的页数；升级后可无限制使用。  
- **旋转混淆：** 请记住 `setRotateAngle` 接受角度值，负数表示逆时针旋转。

## 常见问题

**问：我可以为受密码保护的 PDF 添加水印吗？**  
答：可以。使用接受密码字符串的 `Watermarker` 构造函数打开文档。

**问：库是否支持 DOCX、PPTX 等其他格式？**  
答：当然。GroupDocs.Watermark 同时支持 Word、PowerPoint、Excel 以及图片文件。

**问：如何更改水印的不透明度？**  
答：在水印对象上调用 `setOpacity(float opacity)`（取值范围 0.0~1.0）。

**问：能只在首页添加水印吗？**  
答：通过 `watermarker.getPages()` 获取页面集合，然后在所需的页面索引上应用水印。

**问：如果 PDF 存在云存储桶中怎么办？**  
答：将 PDF 加载到 `InputStream`，传入 `Watermarker` 构造函数；处理完后将输出流写回云端。

## 结论

现在，您已经掌握了使用 GroupDocs.Watermark for Java 为 **PDF 文件添加水印** 的完整、可投入生产的方法。通过结合文字和图片水印，您可以实现强大的 **PDF 文档安全**，满足品牌和合规需求。进一步探索库的其他功能——如水印移除或批量处理——以进一步提升文档工作流。

---

**最后更新：** 2026-01-23  
**测试环境：** GroupDocs.Watermark 24.11 for Java  
**作者：** GroupDocs  

---