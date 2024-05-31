---
title: Растрировать PDF-страницу
linktitle: Растрировать PDF-страницу
second_title: GroupDocs.Watermark .NET API
description: Повысьте безопасность документов с помощью GroupDocs Watermark для .NET. Легко добавляйте водяные знаки в PDF и другие форматы.
type: docs
weight: 28
url: /ru/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Введение
GroupDocs.Watermark для .NET — это мощный API, который позволяет разработчикам легко добавлять водяные знаки в различные форматы документов, включая PDF, Word, Excel, PowerPoint и другие. Благодаря интуитивно понятному интерфейсу и обширным функциям GroupDocs.Watermark упрощает процесс добавления текстовых или графических водяных знаков в документы, позволяя пользователям легко защитить свою интеллектуальную собственность и повысить безопасность документов.
## Предварительные условия
Прежде чем приступить к использованию GroupDocs.Watermark для .NET, убедитесь, что у вас есть следующие предварительные условия:
1. Установка: Загрузите и установите GroupDocs.Watermark для .NET с сайта[страница загрузки](https://releases.groupdocs.com/Watermark/net/).
2.  Лицензия: приобретите лицензию на GroupDocs.Watermark для .NET. Вы можете получить временную лицензию для ознакомительных целей на сайте[здесь](https://purchase.groupdocs.com/temporary-license/) или приобретите полную лицензию на сайте[страница покупки](https://purchase.groupdocs.com/buy).
3. .NET Framework: убедитесь, что на вашем компьютере разработки установлена .NET Framework.
4. Документ: подготовьте документ, к которому вы хотите добавить водяные знаки.

## Импортировать пространства имен
Чтобы начать использовать GroupDocs.Watermark для .NET, импортируйте необходимые пространства имен в свой проект:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ваш код находится здесь
}
```
## Шаг 2. Инициализируйте водяной знак
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Шаг 3: Добавьте водяной знак
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Шаг 4. Растеризуйте страницу
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Шаг 5: Сохраните документ
```csharp
watermarker.Save(outputFileName);
```

## Заключение
В заключение, GroupDocs.Watermark для .NET предлагает простое решение для добавления водяных знаков в PDF и другие форматы документов. Следуя пошаговому руководству, изложенному выше, разработчики могут эффективно растрировать PDF-страницы и с легкостью повысить безопасность документов.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Watermark с другими форматами документов, кроме PDF?
Да, GroupDocs.Watermark поддерживает широкий спектр форматов документов, включая Word, Excel, PowerPoint, Visio и другие.
### Могу ли я настроить внешний вид водяного знака, добавленного в документ?
Абсолютно! GroupDocs.Watermark предоставляет широкие возможности настройки текстовых и графических водяных знаков, позволяя пользователям настраивать шрифт, размер, цвет, непрозрачность и расположение в соответствии со своими предпочтениями.
### Подходит ли GroupDocs.Watermark как для личного, так и для коммерческого использования?
Да, GroupDocs.Watermark предлагает гибкие варианты лицензирования для удовлетворения как индивидуальных, так и корпоративных потребностей, что делает его подходящим как для личных проектов, так и для крупномасштабных коммерческих приложений.
### Предлагает ли GroupDocs.Watermark техническую поддержку для разработчиков?
Да, разработчики могут получить доступ к комплексной технической поддержке через форум GroupDocs.Watermark, где они могут обращаться за помощью, делиться опытом и взаимодействовать с другими разработчиками.
### Могу ли я попробовать GroupDocs.Watermark перед покупкой?
Конечно! Вы можете воспользоваться бесплатной пробной версией GroupDocs.Watermark на сайте[страница релизов](https://releases.groupdocs.com/), что позволяет вам изучить его возможности и возможности перед совершением покупки.