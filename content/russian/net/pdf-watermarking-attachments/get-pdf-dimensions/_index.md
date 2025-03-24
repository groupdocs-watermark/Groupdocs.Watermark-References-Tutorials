---
title: Получить размеры PDF
linktitle: Получить размеры PDF
second_title: GroupDocs.Watermark .NET API
description: С легкостью защитите свои документы с помощью Groupdocs.Watermark для .NET. Добавляйте водяные знаки, штампы и аннотации без особых усилий.
weight: 26
url: /ru/net/pdf-watermarking-attachments/get-pdf-dimensions/
---

# Получить размеры PDF

## Введение
В наш век цифровых технологий защита ваших документов имеет первостепенное значение. Независимо от того, являетесь ли вы бизнес-профессионалом, юристом или творческим художником, защита вашей интеллектуальной собственности имеет важное значение. Groupdocs.Watermark для .NET предлагает надежное решение для добавления водяных знаков, штампов и аннотаций в ваши документы, обеспечивая их безопасность и подлинность.
## Предварительные условия
Прежде чем погрузиться в мир Groupdocs.Watermark для .NET, убедитесь, что у вас есть следующие предварительные условия:
1.  Установка Groupdocs.Watermark для .NET: загрузите и установите Groupdocs.Watermark для .NET с сайта[ссылка для скачивания](https://releases.groupdocs.com/Watermark/net/).
2.  Лицензионный ключ (необязательно). Хотя Groupdocs.Watermark для .NET предлагает бесплатную пробную версию, вы можете выбрать временную лицензию или приобрести полную лицензию на сайте[здесь](https://purchase.groupdocs.com/buy) для расширенного функционала.
3. Знакомство с C#. Для понимания и реализации представленных примеров рекомендуется базовое знание языка программирования C#.
4. Документ для защиты: подготовьте образец документа (например, PDF, Word, Excel) на локальном компьютере, чтобы поэкспериментировать с ним.

## Импортировать пространства имен
Чтобы начать работу с Groupdocs.Watermark для .NET, вам необходимо импортировать необходимые пространства имен в проект C#.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Шаг 1. Объявите переменные
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Шаг 2. Загрузите документ
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Шаг 3. Получите PDF-контент
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Шаг 4: Получение размеров
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Заключение
В заключение, Groupdocs.Watermark для .NET предлагает комплексное решение для защиты ваших документов от несанкционированного использования и распространения. Выполнив описанные выше шаги и используя возможности Groupdocs.Watermark для .NET, вы сможете обеспечить безопасность и целостность своих ценных цифровых активов.
## Часто задаваемые вопросы
### Могу ли я использовать Groupdocs.Watermark для .NET бесплатно?
Да, Groupdocs.Watermark для .NET предлагает бесплатную пробную версию для ознакомительных целей. Однако для расширения функциональности вы можете рассмотреть возможность приобретения полной лицензии.
### Поддерживает ли Groupdocs.Watermark несколько форматов документов?
Да, Groupdocs поддерживает широкий спектр форматов документов, включая PDF, Word, Excel, PowerPoint и другие.
### Могу ли я настроить водяные знаки и штампы с помощью Groupdocs.Watermark?
Абсолютно! Groupdocs.Watermark предоставляет широкие возможности настройки водяных знаков, штампов и аннотаций в соответствии с вашими конкретными требованиями.
### Доступна ли техническая поддержка для пользователей Groupdocs.Watermark?
 Да, вы можете получить техническую помощь и взаимодействовать с сообществом Groupdocs через[форум поддержки](https://forum.groupdocs.com/c/watermark/19).
### Как я могу получить временную лицензию для Groupdocs.Watermark?
 Вы можете получить временную лицензию для Groupdocs.Watermark на сайте[здесь](https://purchase.groupdocs.com/temporary-license/).