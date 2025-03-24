---
title: Добавить водяной знак аннотации только для печати в PDF
linktitle: Добавить водяной знак аннотации только для печати в PDF
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как добавлять водяные знаки аннотаций только для печати в PDF-файлы с помощью GroupDocs.Watermark для .NET. Повысьте безопасность документов и брендинг без особых усилий.
weight: 13
url: /ru/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## Введение
В этом руководстве мы углубимся в процесс добавления водяного знака аннотации только для печати в PDF-файл с помощью GroupDocs.Watermark для .NET. Использование водяных знаков в документах является важнейшим аспектом безопасности документов и брендинга, и GroupDocs.Watermark предоставляет разработчикам .NET простое решение для достижения этой цели.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
- Базовое понимание языка программирования C#.
- Visual Studio установлена на вашем компьютере.
- GroupDocs.Watermark для библиотеки .NET, установленной в вашем проекте.

## Импортировать пространства имен
Для начала убедитесь, что вы импортировали необходимые пространства имен:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Загрузите документ
 Во-первых, вам необходимо загрузить PDF-документ, на который вы хотите поставить водяной знак. Заменять`"Your Document Path"` с путем к вашему PDF-файлу и`"Your Document Directory"` с каталогом, в котором вы хотите сохранить выходной файл.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Здесь будет добавлен код водяного знака.
}
```
## Шаг 2. Добавьте водяной знак
Затем создайте текстовый объект водяного знака с нужным текстом и шрифтом. Набор`isPrintOnly` к`true` чтобы водяной знак был виден только при печати документа, а не в режиме просмотра.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Шаг 3. Настройте параметры водяных знаков
Определите параметры водяного знака, например указатель страницы, на которую следует добавить водяной знак, и укажите его как аннотацию только для печати.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Шаг 4: Примените водяной знак
Добавьте водяной знак в документ, используя указанные параметры, и сохраните выходной файл.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Заключение
В этом руководстве мы узнали, как добавить водяной знак аннотации только для печати в PDF-документ с помощью GroupDocs.Watermark для .NET. Это позволяет разработчикам с легкостью повысить безопасность документов и брендинг.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Watermark с другими форматами документов, кроме PDF?
Да, GroupDocs поддерживает различные форматы документов, такие как Word, Excel, PowerPoint и изображения.
### Могу ли я настроить внешний вид водяного знака?
Конечно, GroupDocs.Watermark предоставляет широкие возможности для настройки текста, шрифта, цвета, размера и расположения водяного знака.
### Предлагает ли GroupDocs.Watermark возможности пакетной обработки?
Разумеется, разработчики могут добавлять водяные знаки на несколько документов одновременно, используя функции пакетной обработки.
### Доступна ли пробная версия для GroupDocs.Watermark?
Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Watermark по предоставленной ссылке.
### Как я могу получить техническую поддержку для GroupDocs.Watermark?
Вы можете обратиться за технической помощью на форум GroupDocs.Watermark, доступный по предоставленной ссылке поддержки.