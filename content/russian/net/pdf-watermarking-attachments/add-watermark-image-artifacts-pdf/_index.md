---
title: Добавить водяной знак к артефактам изображения в PDF
linktitle: Добавить водяной знак к артефактам изображения в PDF
second_title: GroupDocs.Watermark .NET API
description: Защитите свои PDF-файлы с помощью персонализированных водяных знаков с помощью GroupDocs.Watermark для .NET. Легко добавляйте текстовые или графические водяные знаки к изображениям в PDF-документах.
weight: 18
url: /ru/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# Добавить водяной знак к артефактам изображения в PDF

## Введение
В этом руководстве мы покажем вам процесс добавления водяного знака к артефактам изображения в PDF-документе с помощью GroupDocs.Watermark для .NET. Следуя этим шагам, вы сможете эффективно защитить свои PDF-файлы с помощью персонализированных водяных знаков.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Watermark для .NET: загрузите и установите библиотеку GroupDocs.Watermark для .NET с сайта[здесь](https://releases.groupdocs.com/Watermark/net/).
2. Путь к документу: укажите путь к PDF-документу, в который вы хотите добавить водяной знак.
3. Выходной каталог: создайте каталог, в котором будет сохранен документ с водяным знаком.

## Импортировать пространства имен
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ и инициализируйте водяной знак.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Шаг 2. Получите PDF-контент и добавьте водяной знак
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Инициализация изображения или текстового водяного знака
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Добавьте водяной знак к изображению
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Шаг 3. Сохраните документ с водяным знаком
```csharp
	watermarker.Save(outputFileName);
}
```

## Заключение
Благодаря GroupDocs.Watermark для .NET добавление водяных знаков к изображениям в PDF-документах становится простым процессом. Следуя этому руководству, вы сможете эффективно защитить свои PDF-файлы с помощью настраиваемых водяных знаков, гарантируя их безопасность и подлинность.
## Часто задаваемые вопросы
### Могу ли я добавить в PDF-документ как графические, так и текстовые водяные знаки?
Да, GroupDocs.Watermark для .NET поддерживает одновременное добавление как графических, так и текстовых водяных знаков.
### Есть ли какие-либо ограничения на количество водяных знаков, которые я могу добавить в документ?
Нет, вы можете добавить в документ несколько водяных знаков без каких-либо ограничений.
### Могу ли я настроить внешний вид и положение водяного знака?
Разумеется, вы имеете полный контроль над внешним видом, положением и свойствами водяного знака.
### Поддерживает ли GroupDocs.Watermark для .NET другие форматы документов, кроме PDF?
Да, он поддерживает различные форматы документов, включая Word, Excel, PowerPoint и другие.
### Есть ли способ удалить водяные знаки из документа?
Да, GroupDocs.Watermark для .NET предоставляет методы для удаления водяных знаков из документов, если это необходимо.