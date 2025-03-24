---
title: Удалить фигуру в документах Word
linktitle: Удалить фигуру в документах Word
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как удалять фигуры из документов Word с помощью GroupDocs.Watermark для .NET. Простое, эффективное и мощное манипулирование документами.
weight: 30
url: /ru/net/word-processing-watermarkings/remove-shape-word-docs/
---

# Удалить фигуру в документах Word

## Введение
В области обработки документов и манипулирования ими GroupDocs.Watermark для .NET представляет собой мощный набор инструментов, позволяющий разработчикам легко интегрировать функции создания водяных знаков в свои .NET-приложения. В этой статье рассматриваются тонкости использования GroupDocs.Watermark для .NET для удаления фигур из документов Word. Следуя пошаговому руководству, разработчики смогут легко и эффективно разобраться в этом процессе.
## Предварительные условия
Прежде чем приступить к удалению фигур в документах Word с помощью GroupDocs.Watermark для .NET, убедитесь, что выполнены следующие предварительные условия:
### 1. Получите GroupDocs.Watermark для .NET.
 Начните с приобретения библиотеки GroupDocs.Watermark для .NET. Вы можете скачать библиотеку с сайта[страница выпуска](https://releases.groupdocs.com/Watermark/net/).
### 2. Знакомство с разработкой .NET.
Крайне важно иметь базовое понимание разработки .NET. Убедитесь, что вы владеете программированием на C# и имеете базовые знания о работе с библиотеками и зависимостями в экосистеме .NET.
### 3. Интегрированная среда разработки (IDE).
Установите в своей системе интегрированную среду разработки, например Visual Studio, обеспечивающую благоприятную среду для разработки .NET. 
### 4. Образец документа Word
Подготовьте образец документа Word, содержащий фигуры, которые вы хотите удалить. Этот документ послужит испытательной площадкой для вашей реализации.

## Импортировать пространства имен
Чтобы запустить процесс удаления фигур в документах Word с помощью GroupDocs.Watermark для .NET, импортируйте необходимые пространства имен в свой проект:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ
Начните с указания пути к документу Word, которым вы хотите манипулировать, и создайте имя выходного файла для обработанного документа:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Шаг 2. Инициализируйте водяной знак
 Инициализировать`Watermarker` объект, передав путь к документу и дополнительные параметры загрузки:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Шаг 3. Доступ к содержимому документа
Получите содержимое документа Word, чтобы получить доступ к его разделам и фигурам:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Шаг 4. Удаление фигуры по индексу
 Удалите фигуру из документа, указав ее индекс внутри`Shapes` коллекция:
```csharp
content.Sections[0].Shapes.RemoveAt(0);
```
## Шаг 5. Удаление фигуры по ссылке
 Альтернативно можно удалить фигуру, указав на нее прямую ссылку внутри`Shapes` коллекция:
```csharp
content.Sections[0].Shapes.Remove(content.Sections[0].Shapes[0]);
```
## Шаг 6: Сохраните документ
Сохраните измененный документ в указанный выходной файл:
```csharp
watermarker.Save(outputFileName);
```

## Заключение
В заключение, GroupDocs.Watermark для .NET дает разработчикам возможность с легкостью манипулировать документами Word. Следуя этому пошаговому руководству, вы сможете легко удалять фигуры из документов Word, улучшая рабочий процесс обработки документов.
## Часто задаваемые вопросы
### Может ли GroupDocs.Watermark для .NET обрабатывать документы других форматов, кроме Word?
Да, GroupDocs.Watermark для .NET поддерживает широкий спектр форматов документов, включая Excel, PowerPoint, PDF и другие.
### Доступна ли бесплатная пробная версия GroupDocs.Watermark для .NET?
 Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Watermark для .NET на сайте[страница выпуска](https://releases.groupdocs.com/).
### Как получить временные лицензии для GroupDocs.Watermark для .NET?
 Временные лицензии для GroupDocs.Watermark для .NET можно получить на сайте[страница временной лицензии](https://purchase.groupdocs.com/temporary-license/).
### Где я могу найти документацию и поддержку для GroupDocs.Watermark для .NET?
 Ресурсы документации и поддержки для GroupDocs.Watermark для .NET доступны на сайте[Форум](https://forum.groupdocs.com/c/watermark/19) и[Справочная страница](https://tutorials.groupdocs.com/Watermark/net/).
### Какие версии .NET совместимы с GroupDocs.Watermark?
GroupDocs.Watermark для .NET совместим с различными версиями .NET, включая .NET Framework и .NET Core.