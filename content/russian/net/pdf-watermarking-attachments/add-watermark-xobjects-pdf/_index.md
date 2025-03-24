---
title: Добавить водяной знак в XObjects в PDF
linktitle: Добавить водяной знак в XObjects в PDF
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как добавлять водяные знаки к объектам XObject в PDF с помощью Groupdocs.Watermark для .NET. Следуйте нашему пошаговому руководству, чтобы упростить реализацию.
weight: 20
url: /ru/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Введение
Добавление водяных знаков в PDF-файлы — важный шаг для защиты ваших документов от несанкционированного использования. Благодаря Groupdocs.Watermark для .NET добавление водяных знаков к объектам XObject в ваших PDF-файлах стало еще проще. В этом руководстве мы шаг за шагом проведем вас через весь процесс, чтобы вы могли уверенно наносить водяные знаки на свои PDF-документы. Давайте начнем!
## Предварительные условия
Прежде чем погрузиться в руководство, давайте убедимся, что у вас есть все необходимое для беспрепятственного выполнения:
-  Groupdocs.Watermark для .NET: загрузите и установите последнюю версию с сайта[здесь](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: убедитесь, что на вашем компьютере разработки установлена .NET Framework.
- Среда разработки: используйте Visual Studio или любую другую среду разработки, поддерживающую разработку .NET.
-  Временная лицензия: получите[временная лицензия](https://purchase.groupdocs.com/temporary-license/) если вы оцениваете продукт.
Если у вас есть все необходимые условия, вы готовы приступить к нанесению водяных знаков на свои PDF-файлы.
## Импортировать пространства имен
Сначала вам нужно будет импортировать необходимые пространства имен в ваш проект. Откройте проект C# и добавьте следующие директивы:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Настройте пути к документам
Первый шаг включает настройку путей для вашего документа. Определите путь, по которому находится ваш PDF-файл, и место, где вы хотите сохранить PDF-файл с водяными знаками.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Заменять`"Your Document Path"` и`"Your Document Directory"` с фактическими путями на вашей машине.
## Шаг 2. Инициализируйте параметры загрузки PDF
Далее вам нужно будет инициализировать параметры загрузки PDF. Это имеет решающее значение для правильной загрузки содержимого PDF.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Шаг 3. Загрузите PDF-документ
Используя параметры загрузки, загрузите PDF-документ с`Watermarker` сорт.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Шаг 4: Создайте водяной знак
Теперь вам нужно создать водяной знак, который будет добавлен в PDF-файл. В этом уроке мы создадим текстовый водяной знак.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Шаг 5. Добавьте водяной знак в XObjects
Перейдите по каждой странице и каждому XObject в PDF-файле, чтобы применить водяной знак.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Добавьте водяной знак к изображению
            xObject.Image.Add(watermark);
        }
    }
}
```
## Шаг 6. Сохраните PDF-файл с водяными знаками
Наконец, сохраните PDF-файл с водяными знаками в указанном выходном файле.
```csharp
    watermarker.Save(outputFileName);
}
```
И вот оно! Ваш PDF-файл теперь содержит водяные знаки на всех объектах XObject.
## Заключение
 Добавление водяных знаков в PDF-документы с помощью Groupdocs — это простой процесс, обеспечивающий дополнительный уровень безопасности. Выполнив действия, описанные в этом руководстве, вы можете быть уверены, что ваши документы защищены от несанкционированного использования. Помните, вы всегда можете обратиться к[документация](https://tutorials.groupdocs.com/Watermark/net/) для получения более подробной информации и расширенных функций.
## Часто задаваемые вопросы
### Могу ли я использовать изображение в качестве водяного знака вместо текста?
Да, Groupdocs.Watermark для .NET поддерживает как текстовые, так и графические водяные знаки.
### Как я могу протестировать Groupdocs.Watermark, не покупая его?
 Вы можете использовать[временная лицензия](https://purchase.groupdocs.com/temporary-license/) оценить товар.
### Можно ли настроить внешний вид водяного знака?
Абсолютно! Вы можете настроить шрифт, размер, угол поворота и многое другое.
### Поддерживает ли Groupdocs.Watermark другие форматы документов?
Да, он поддерживает различные форматы, включая Word, Excel и PowerPoint.
### Где я могу получить поддержку, если у меня возникнут проблемы?
 Вы можете получить поддержку от[Форум групповой документации](https://forum.groupdocs.com/c/watermark/19).