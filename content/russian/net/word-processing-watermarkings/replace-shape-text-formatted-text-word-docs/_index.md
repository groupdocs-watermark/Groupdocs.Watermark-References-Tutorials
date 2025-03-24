---
title: Заменить текст фигуры форматированным текстом в документах Word
linktitle: Заменить текст фигуры форматированным текстом в документах Word
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как заменить текст фигуры форматированным текстом в документах Word с помощью GroupDocs.Watermark для .NET. Ваши возможности редактирования документов без особых усилий.
weight: 34
url: /ru/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---

# Заменить текст фигуры форматированным текстом в документах Word

## Введение
В этом руководстве мы покажем вам процесс замены текста фигуры форматированным текстом в документах Word с помощью GroupDocs.Watermark для .NET. Эта библиотека предоставляет мощные функции для работы с водяными знаками, включая замену текста внутри фигур.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Watermark для .NET: убедитесь, что вы установили и настроили GroupDocs.Watermark для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/Watermark/net/).
2. Путь к документу: у вас должен быть путь к документу Word, в котором вы хотите заменить текст.

## Импортировать пространства имен
Прежде чем писать код, импортируйте необходимые пространства имен:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ
 Загрузите документ Word, используя`Watermarker` сорт:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ваш код продолжается здесь...
}
```
## Шаг 2. Получите контент и замените текст
После загрузки документа получите содержимое и замените текст внутри фигур:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Шаг 3. Сохраните документ
После замены текста сохраните измененный документ:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Заключение
Заменить текст формы форматированным текстом в документах Word стало проще с помощью GroupDocs для .NET. Следуя шагам, описанным в этом руководстве, вы сможете эффективно управлять текстом в своих документах и манипулировать им.

## Часто задаваемые вопросы
### Могу ли я заменить текст в других типах документов с помощью GroupDocs.Watermark для .NET?
Да, GroupDocs поддерживает различные форматы документов, такие как PDF, Excel, PowerPoint и другие.
### Совместим ли GroupDocs.Watermark с .NET Core?
Да, GroupDocs.Watermark поддерживает как .NET Framework, так и .NET Core.
### Предоставляет ли GroupDocs.Watermark поддержку добавления изображений в качестве водяных знаков?
Конечно, GroupDocs.Watermark позволяет добавлять в документы как текстовые, так и графические водяные знаки.
### Могу ли я настроить внешний вид водяных знаков, добавленных с помощью GroupDocs.Watermark?
Да, вы имеете полный контроль над внешним видом, положением и другими свойствами водяных знаков.
### Доступна ли пробная версия GroupDocs.Watermark для .NET?
 Да, вы можете загрузить бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).