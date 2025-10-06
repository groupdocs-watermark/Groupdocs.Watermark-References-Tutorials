---
title: Добавить водяной знак артефакта в PDF
linktitle: Добавить водяной знак артефакта в PDF
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как легко добавлять артефактные водяные знаки в файлы PDF с помощью Groupdocs.Watermark для .NET. Защитите свои документы с легкостью.
weight: 11
url: /ru/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
type: docs
---
# Добавить водяной знак артефакта в PDF

## Введение
Добавление водяных знаков в PDF-файлы — важнейший аспект управления документами, особенно когда речь идет о защите интеллектуальной собственности или фирменных документах. Groupdocs.Watermark для .NET предоставляет надежное решение для легкого добавления водяных знаков в файлы PDF. В этом уроке мы шаг за шагом рассмотрим процесс добавления водяного знака артефакта в файлы PDF.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  Groupdocs.Watermark для .NET: загрузите и установите Groupdocs.Watermark для .NET с сайта[здесь](https://releases.groupdocs.com/Watermark/net/).
2. Среда разработки: настройте среду разработки .NET.
3. PDF-документ: подготовьте PDF-документ, в который вы хотите добавить водяной знак.
4. Выходной каталог: создайте каталог для сохранения PDF-файла с водяными знаками.

## Импорт пространств имен
Для начала импортируйте необходимые пространства имен в ваш проект C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите PDF-документ
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Шаг 2. Определите параметры водяного знака
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Шаг 3. Добавьте текстовый водяной знак
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Шаг 4. Добавьте водяной знак изображения
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Шаг 5. Сохраните PDF-файл с водяными знаками
```csharp
watermarker.Save(outputFileName);
```

## Заключение
В этом руководстве мы узнали, как добавлять водяные знаки артефактов в файлы PDF с помощью Groupdocs.Watermark для .NET. Выполнив эти шаги, вы сможете легко интегрировать функцию создания водяных знаков в свои приложения .NET, гарантируя безопасность и целостность ваших документов.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид текстового водяного знака?
Да, вы можете настроить различные аспекты, такие как шрифт, размер, цвет и выравнивание текстового водяного знака, в соответствии со своими предпочтениями.
### Поддерживает ли Groupdocs.Watermark добавление водяных знаков в другие форматы документов?
Да, Groupdocs.Watermark поддерживает добавление водяных знаков в широкий спектр форматов документов, включая Word, Excel, PowerPoint и другие.
### Доступна ли пробная версия Groupdocs.Watermark для .NET?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по любым вопросам или вопросам, связанным с Groupdocs.Watermark?
 Вы можете получить поддержку на форуме сообщества Groupdocs.[здесь](https://forum.groupdocs.com/c/watermark/19).
### Могу ли я использовать Groupdocs.Watermark в коммерческих целях?
Да, вы можете приобрести лицензию для коммерческого использования на сайте[здесь](https://purchase.groupdocs.com/buy).