---
title: Добавить водяной знак мозаичного изображения
linktitle: Добавить водяной знак мозаичного изображения
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как добавлять водяные знаки мозаичных изображений в документы с помощью GroupDocs.Watermark для .NET. Простой, эффективный и настраиваемый.
weight: 10
url: /ru/net/image-watermarkings/add-tiled-image-watermark/
---

# Добавить водяной знак мозаичного изображения

## Введение
GroupDocs.Watermark для .NET — это мощный API, который позволяет разработчикам программно добавлять, удалять и искать водяные знаки в различных форматах документов. В этом руководстве мы покажем вам процесс добавления водяного знака мозаичного изображения в ваши документы с помощью GroupDocs.Watermark для .NET.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующее:
- Базовые знания языка программирования C#.
- Visual Studio установлена в вашей системе.
- Библиотека GroupDocs.Watermark для .NET добавлена в ваш проект. Вы можете скачать его с[здесь](https://releases.groupdocs.com/Watermark/net/).

## Импортировать пространства имен
Обязательно импортируйте необходимые пространства имен в начало файла C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Шаг 1. Установите путь к документу и выходной каталог
Определите путь к входному документу и каталог, в котором вы хотите сохранить выходной документ:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Заменять`"Your Document Path"` с абсолютным или относительным путем к входному документу.
## Шаг 2. Инициализация объекта водяного знака
Создайте объект Watermarker, используя путь к входному документу:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Добавьте сюда водяной знак
}
```
## Шаг 3. Добавьте водяной знак мозаичного изображения
Создайте экземпляр объекта ImageWatermark, указав путь к файлу изображения, который вы хотите использовать в качестве водяного знака:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Настройка параметров плитки
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
    // Добавить водяной знак в документ
    watermarker.Add(watermark);
    // Сохраните измененный документ
    watermarker.Save(outputFileName);
}
```
 Заменять`"Path to Your Image"` с фактическим путем к файлу изображения водяного знака.

## Заключение
Выполнив эти шаги, вы можете легко добавить мозаичный водяной знак в свои документы с помощью GroupDocs.Watermark для .NET. Экспериментируйте с различными опциями и конфигурациями для достижения желаемого результата.
## Часто задаваемые вопросы
### Могу ли я добавить несколько водяных знаков в один документ?
Да, вы можете добавить в документ несколько водяных знаков разных типов, используя GroupDocs.Watermark для .NET.
### Поддерживает ли GroupDocs.Watermark все форматы документов?
GroupDocs.Watermark поддерживает широкий спектр форматов документов, включая PDF, Word, Excel, PowerPoint и многие другие.
### Доступна ли пробная версия для GroupDocs.Watermark?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Могу ли я настроить внешний вид водяного знака?
Да, вы можете настроить различные аспекты водяного знака, такие как положение, размер, поворот, прозрачность и т. д.
### Предлагает ли GroupDocs.Watermark техническую поддержку?
 Да, вы можете получить техническую поддержку на форуме GroupDocs.Watermark.[здесь](https://forum.groupdocs.com/c/watermark/19).