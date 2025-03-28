---
title: Создать предварительный просмотр документа
linktitle: Создать предварительный просмотр документа
second_title: GroupDocs.Watermark .NET API
description: Из этого руководства вы узнаете, как создавать предварительные просмотры документов с помощью GroupDocs.Watermark для .NET. Повысьте безопасность и управление документами без особых усилий.
weight: 10
url: /ru/net/document-manipulation/generate-document-preview/
---

# Создать предварительный просмотр документа

## Введение
В мире управления цифровыми документами водяные знаки играют решающую роль в обеспечении безопасности и подлинности документов. GroupDocs.Watermark для .NET — это мощный инструмент, который позволяет разработчикам легко добавлять водяные знаки в документы. В этом руководстве мы познакомим вас с процессом создания предварительного просмотра документов с помощью GroupDocs.Watermark для .NET. Независимо от того, являетесь ли вы опытным разработчиком или только начинаете, это руководство предоставит вам подробный пошаговый процесс достижения вашей цели.
## Предварительные условия
Прежде чем углубиться в реализацию, давайте убедимся, что у вас есть все необходимое для начала работы:
- Базовое понимание C# и .NET framework.
- Visual Studio установлена на вашем компьютере.
- GroupDocs.Watermark для библиотеки .NET. Ты можешь[скачай это здесь](https://releases.groupdocs.com/Watermark/net/).
-  Действующая лицензия для GroupDocs.Watermark. Вы можете либо купить его[здесь](https://purchase.groupdocs.com/buy) или получить[временная лицензия](https://purchase.groupdocs.com/temporary-license/) в целях оценки.
## Импортировать пространства имен
Чтобы начать использовать GroupDocs.Watermark в своем проекте, вам необходимо импортировать необходимые пространства имен. Это можно сделать, добавив в код следующие директивы using:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Эти пространства имен обеспечат доступ к классам и методам, необходимым для нанесения водяных знаков и создания предварительного просмотра документов.

Давайте разобьем процесс создания предварительного просмотра документа на простые и понятные шаги.
## Шаг 1. Настройте свой проект
Прежде всего настройте свой проект .NET в Visual Studio. Если у вас еще нет проекта, создайте новый, выполнив следующие действия:
1. Откройте Visual Studio.
2. Нажмите «Создать новый проект».
3. Выберите «Консольное приложение (.NET Core)» и нажмите «Далее».
4. Назовите свой проект и выберите место для его сохранения, затем нажмите «Создать».
## Шаг 2. Установите GroupDocs.Watermark для .NET.
Чтобы использовать GroupDocs.Watermark в своем проекте, вам необходимо установить библиотеку. Это можно сделать с помощью диспетчера пакетов NuGet:
1. Щелкните правой кнопкой мыши свой проект в обозревателе решений.
2. Выберите «Управление пакетами NuGet».
3. Найдите «GroupDocs.Watermark» на вкладке «Обзор».
4. Нажмите «Установить», чтобы добавить библиотеку в свой проект.
Альтернативно вы можете установить его через консоль диспетчера пакетов:
```powershell
Install-Package GroupDocs.Watermark
```
## Шаг 3. Определите путь к документу и выходной каталог
Перед созданием предварительного просмотра вам необходимо указать путь к документу, который вы хотите просмотреть, и каталог, в котором будут сохранены изображения предварительного просмотра:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Замените «Путь к вашему документу» на путь к вашему документу, а «Каталог вашего документа» на каталог, в котором вы хотите сохранить изображения предварительного просмотра.
## Шаг 4. Инициализация объекта водяного знака
Создайте экземпляр`Watermarker` класс, передав путь к документу его конструктору. Этот объект будет использоваться для выполнения всех операций с водяными знаками:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Ваш код здесь
}
```
## Шаг 5. Создайте методы делегирования для обработки потока
Чтобы создать предварительный просмотр, вам необходимо определить методы делегата для создания и выпуска потоков. Эти методы будут обрабатывать создание и выпуск потоков для каждой страницы документа:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
`createPageStreamDelegate` метод создает поток для каждой страницы документа, а метод`releasePageStreamDelegate` метод закрывает поток после создания предварительного просмотра.
## Шаг 6. Настройте параметры предварительного просмотра
 Затем настройте параметры предварительного просмотра, создав экземпляр`PreviewOptions` сорт. Укажите методы делегата и установите формат предварительного просмотра PNG. Вы также можете указать, какие страницы включать в предварительный просмотр:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
В этом примере мы создаем предварительный просмотр для первых двух страниц документа.
## Шаг 7: Создайте предварительный просмотр документа
 Наконец, позвоните в`GeneratePreview` метод на`Watermarker`объект, передавая настроенный`PreviewOptions`. Это создаст изображения предварительного просмотра и сохранит их в указанном каталоге:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Заключение
Создание предварительного просмотра документов с помощью GroupDocs.Watermark для .NET — это простой процесс, который можно выполнить с помощью всего нескольких строк кода. Следуя инструкциям, описанным в этом руководстве, вы сможете легко настроить свой проект, настроить необходимые параметры и создавать предварительные просмотры для своих документов. Эта мощная библиотека не только упрощает процесс создания водяных знаков, но также предоставляет надежные функции для управления водяными знаками и манипулирования ими.
 Если у вас есть какие-либо вопросы или вам нужна дополнительная помощь, не стесняйтесь посетить[Форум поддержки GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) или обратитесь к[документация](https://tutorials.groupdocs.com/Watermark/net/).
## Часто задаваемые вопросы
### Какие форматы файлов поддерживаются GroupDocs.Watermark для .NET?
 GroupDocs.Watermark для .NET поддерживает широкий спектр форматов файлов, включая PDF, DOCX, PPTX, XLSX и многие другие. Полный список поддерживаемых форматов см.[документация](https://tutorials.groupdocs.com/Watermark/net/).
### Могу ли я настроить внешний вид водяных знаков?
Да, GroupDocs.Watermark позволяет полностью настроить внешний вид водяных знаков, включая текстовые, графические и фигурные водяные знаки. Вы можете настроить такие свойства, как шрифт, цвет, размер и прозрачность.
### Доступна ли пробная версия?
 Да, вы можете получить[бесплатная пробная версия](https://releases.groupdocs.com/) GroupDocs.Watermark для .NET, чтобы оценить его возможности перед покупкой.
### Как приобрести лицензию на GroupDocs.Watermark?
 Вы можете приобрести лицензию на GroupDocs.Watermark.[здесь](https://purchase.groupdocs.com/buy). Существуют различные варианты лицензирования для удовлетворения различных потребностей.
### Могу ли я использовать GroupDocs.Watermark в коммерческом проекте?
 Да, при наличии действующей лицензии вы можете использовать GroupDocs.Watermark в коммерческих проектах. Обязательно ознакомьтесь с условиями лицензирования на сайте[страница покупки](https://purchase.groupdocs.com/buy).