---
title: Добавить текстовый водяной знак
linktitle: Добавить текстовый водяной знак
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как добавлять текстовые водяные знаки в документы с помощью Groupdocs for .NET, с помощью этого пошагового руководства.
weight: 11
url: /ru/net/watermarking-basics/add-text-watermark/
---

# Добавить текстовый водяной знак

## Введение
GroupDocs.Watermark для .NET — это мощная библиотека, которая позволяет разработчикам добавлять, искать и удалять водяные знаки из документов различных форматов в приложениях .NET. В этом уроке мы сосредоточимся на добавлении текстового водяного знака в документ с помощью GroupDocs.Watermark.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1. Базовые знания языка программирования C#.
2. Visual Studio установлена в вашей системе.
3.  Установлена библиотека GroupDocs.Watermark для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/Watermark/net/).

## Импортировать пространства имен
Сначала вам необходимо импортировать необходимые пространства имен в ваш проект C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Шаг 1. Определите путь к документу и выходной каталог
Определите путь к входному документу и выходной каталог, в котором будет сохранен документ с водяным знаком.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Заменять`"Your Document Path"` с абсолютным или относительным путем к входному документу, например:`@"C:\Docs\document.pdf"`. Также укажите каталог, в котором вы хотите сохранить документ с водяным знаком.
## Шаг 2. Добавьте текстовый водяной знак
 Создайте экземпляр`Watermarker` class с путем к входному документу. Затем создайте`TextWatermark` объект с нужными настройками текста и шрифта.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Заключение
В этом уроке мы узнали, как добавить текстовый водяной знак в документ с помощью GroupDocs.Watermark для .NET. Благодаря интуитивно понятному API разработчики могут легко манипулировать водяными знаками в различных форматах документов.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Watermark для .NET со всеми форматами документов?
GroupDocs.Watermark поддерживает широкий спектр форматов документов, включая PDF, Microsoft Word, Excel, PowerPoint и многие другие.
### Могу ли я настроить внешний вид текстового водяного знака?
Да, вы можете настроить различные свойства, такие как шрифт, цвет, выравнивание и непрозрачность текстового водяного знака.
### Предоставляет ли GroupDocs.Watermark поддержку удаления водяных знаков из документов?
Да, GroupDocs.Watermark предлагает функции поиска и удаления водяных знаков из документов.
### Могу ли я попробовать GroupDocs.Watermark для .NET перед покупкой?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Как я могу получить техническую поддержку для GroupDocs.Watermark?
 Вы можете получить техническую поддержку, посетив[Форум GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).