---
title: Удаление фигур с определенным форматированием текста в документах Word
linktitle: Удаление фигур с определенным форматированием текста в документах Word
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как удалять фигуры с определенным форматированием текста в документах Word с помощью GroupDocs.Watermark для .NET. Следуйте нашему руководству для эффективного манипулирования водяными знаками.
weight: 31
url: /ru/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
type: docs
---
# Удаление фигур с определенным форматированием текста в документах Word

## Введение
GroupDocs.Watermark для .NET — это мощный API, который позволяет разработчикам программно манипулировать водяными знаками в различных форматах документов. В этом уроке мы сосредоточимся на удалении фигур с определенным форматированием текста в документах Word с помощью GroupDocs.Watermark для .NET. Независимо от того, являетесь ли вы опытным разработчиком или только начинаете, это пошаговое руководство поможет вам понять процесс эффективного и результативного удаления фигур.
## Предварительные условия
Прежде чем мы углубимся в руководство, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Watermark для .NET: убедитесь, что в вашей среде разработки установлена библиотека GroupDocs.Watermark для .NET. Вы можете скачать его с сайта[Веб-сайт](https://releases.groupdocs.com/Watermark/net/).
2. Среда разработки: настройте подходящую среду разработки с установленной Visual Studio или любой другой .NET IDE.
3. Документ Word: подготовьте документ Word, содержащий фигуры с определенным форматированием текста, которое вы хотите удалить.

## Импортировать пространства имен
Прежде чем приступить к реализации, давайте импортируем необходимые пространства имен:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Здесь идет реализация
}
```
## Шаг 2. Получите контент и пройдитесь по разделам
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    // Здесь идет реализация
}
```
## Шаг 3. Перебор фигур и удаление на основе форматирования текста
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## Шаг 4. Сохраните документ
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Заключение
В этом уроке мы узнали, как удалять фигуры с определенным форматированием текста в документах Word с помощью GroupDocs.Watermark для .NET. Следуя пошаговому руководству и используя предоставленные примеры кода, разработчики могут легко манипулировать водяными знаками в соответствии со своими требованиями.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Watermark для .NET с другими форматами документов, кроме Word?
Да, GroupDocs.Watermark для .NET поддерживает различные форматы документов, включая Excel, PowerPoint, PDF и другие.
### Могу ли я настроить критерии удаления фигур на основе форматирования текста?
Абсолютно! Вы можете изменить код, чтобы настроить таргетинг на определенные атрибуты текста, такие как размер шрифта, стиль, цвет и т. д.
### Предоставляет ли GroupDocs.Watermark для .NET поддержку добавления водяных знаков?
Да, помимо удаления вы также можете добавлять в документы текстовые или графические водяные знаки с помощью GroupDocs.Watermark для .NET.
### Доступна ли пробная версия для тестирования перед покупкой?
 Да, вы можете загрузить бесплатную пробную версию с GroupDocs.[Веб-сайт](https://releases.groupdocs.com/).
### Как я могу получить техническую поддержку или помощь по GroupDocs.Watermark для .NET?
 Для получения технической помощи вы можете посетить форум поддержки по адресу[Форум GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).