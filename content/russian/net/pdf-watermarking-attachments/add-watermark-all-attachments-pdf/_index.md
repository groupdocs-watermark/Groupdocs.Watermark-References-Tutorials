---
title: Добавить водяной знак ко всем вложениям в PDF
linktitle: Добавить водяной знак ко всем вложениям в PDF
second_title: GroupDocs.Watermark .NET API
description: Узнайте, как добавлять водяные знаки к вложениям PDF с помощью GroupDocs.Watermark для .NET. Легко защитите свои документы с помощью пользовательских водяных знаков.
weight: 16
url: /ru/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---

# Добавить водяной знак ко всем вложениям в PDF

## Введение
Добавление водяных знаков к вложениям PDF может стать решающим шагом в управлении документами, особенно при обеспечении безопасности или брендировании. GroupDocs.Watermark для .NET предлагает комплексное решение для легкого встраивания водяных знаков в файлы PDF. В этом руководстве мы покажем вам процесс добавления водяного знака ко всем вложениям в PDF-документе с помощью GroupDocs.Watermark для .NET.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
1.  GroupDocs.Watermark для .NET: если вы еще этого не сделали, загрузите и установите GroupDocs.Watermark для .NET с сайта[Веб-сайт](https://releases.groupdocs.com/Watermark/net/).
2. Среда разработки: настройте подходящую среду разработки с помощью Visual Studio или любой другой .NET-совместимой IDE.
3. PDF-документ: подготовьте PDF-документ, к которому вы хотите добавить водяные знаки, а также вложения, на которые вы хотите добавить водяные знаки.

## Импорт пространств имен
Прежде чем углубляться в код, обязательно импортируйте необходимые пространства имен для доступа к функциям GroupDocs.Watermark для .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Шаг 1. Определите путь к документу и выходной каталог
Сначала определите путь к входному PDF-документу и каталог, в котором будет сохранен документ с водяным знаком:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Шаг 2. Инициализируйте параметры загрузки и водяной знак
Затем инициализируйте параметры загрузки PDF-документа и создайте текстовый водяной знак:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Шаг 3. Загрузите документ и вложения.
Загрузите PDF-документ и просмотрите его вложения:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Шаг 4. Проверьте поддержку вложений
Проверьте, поддерживается ли прикрепленный файл GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Шаг 5. Добавьте водяной знак к вложениям
Загрузите прикрепленный документ и добавьте водяной знак:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Шаг 6. Сохраните изменения
Наконец, сохраните изменения в PDF-документе с водяными знаками:
```csharp
    watermarker.Save(outputFileName);
}
```

## Заключение
В этом руководстве мы рассмотрели, как добавлять водяные знаки ко всем вложениям в PDF-документе с помощью GroupDocs.Watermark для .NET. Следуя пошаговому руководству, вы сможете легко интегрировать водяные знаки в файлы PDF, гарантируя безопасность документа и фирменный стиль.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид водяного знака?
Да, вы можете настроить различные аспекты, такие как текст, шрифт, размер, цвет и положение водяного знака, в соответствии с вашими требованиями.
### Поддерживает ли GroupDocs.Watermark другие форматы документов, кроме PDF?
Да, GroupDocs.Watermark поддерживает широкий спектр форматов документов, включая Microsoft Word, Excel, PowerPoint, Visio, Outlook и изображения.
### Доступна ли пробная версия для GroupDocs.Watermark?
Да, вы можете изучить возможности GroupDocs.Watermark, загрузив бесплатную пробную версию с веб-сайта.
### Могу ли я добавить несколько водяных знаков в один документ?
Разумеется, GroupDocs.Watermark позволяет одновременно добавлять несколько водяных знаков, включая текст, изображение и аннотации, для повышения безопасности документа и брендинга.
### Доступна ли техническая поддержка для пользователей GroupDocs.Watermark?
Да, GroupDocs предоставляет комплексную техническую поддержку через форумы и специальные каналы поддержки, чтобы помочь пользователям с любыми вопросами или проблемами, с которыми они могут столкнуться.