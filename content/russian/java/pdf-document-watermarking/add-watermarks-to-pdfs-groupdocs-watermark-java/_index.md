---
date: '2026-08-09'
description: Узнайте, как добавить watermark в PDF с помощью GroupDocs.Watermark для
  Java. Этот java pdf watermark пример демонстрирует текстовые и графические watermarks,
  сохранение PDF с watermark.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Узнайте, как добавить watermark в PDF с помощью GroupDocs.Watermark
  для Java. Этот пошаговый java pdf watermark пример поможет быстро сохранить PDF
  с watermark.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Добавить watermark в PDF с помощью GroupDocs.Watermark для Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  headline: Add watermark to PDF with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  name: Add watermark to PDF with GroupDocs.Watermark for Java
  steps:
  - name: create TextWatermark instance
    text: 'Create a `TextWatermark` using the desired text and font settings: This
      example sets the watermark text to “Protected image” using Arial, size 8.'
  - name: set alignment
    text: 'Center the watermark horizontally and vertically for uniform positioning:'
  - name: rotate watermark
    text: 'Apply a 45‑degree rotation to make the watermark harder to remove:'
  - name: configure sizing
    text: 'Scale the watermark relative to the target image dimensions:'
  - name: load image file
    text: 'Load the watermark image from disk: Replace the placeholder path with the
      actual location of your logo or seal.'
  - name: set alignment
    text: 'Center the image watermark for balanced visual impact:'
  - name: rotate image watermark
    text: 'Apply a –30‑degree rotation to introduce visual variation:'
  - name: configure sizing
    text: 'Define the image size as a percentage of the underlying image’s width:'
  - name: open the document
    text: 'Instantiate a `Watermarker` with the path to your source PDF:'
  - name: retrieve images
    text: 'Collect all images from the PDF that can receive a watermark:'
  type: HowTo
- questions:
  - answer: Yes. Open the document with `new Watermarker("file.pdf", "password")`
      and then apply the watermark as usual.
    question: Can I add a watermark to a password‑protected PDF?
  - answer: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker`
      for each file, apply the same watermark objects, and save the results.
    question: Does the API support batch processing of multiple PDFs?
  - answer: The library can handle **500+ watermarks per document** without performance
      degradation, thanks to its optimized rendering engine.
    question: What is the maximum number of watermarks I can add to a single PDF?
  - answer: Yes. Use the `setOpacity(0)` method on the watermark object to embed it
      invisibly for forensic tracking.
    question: Is it possible to make the watermark invisible (metadata only)?
  - answer: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- pdf watermark
- GroupDocs.Watermark
- Java document security
title: Добавить watermark в PDF с помощью GroupDocs.Watermark для Java
type: docs
url: /ru/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Добавить водяной знак в PDF с помощью GroupDocs.Watermark для Java

## Введение

В современном цифровом мире защита интеллектуальной собственности имеет решающее значение, и **добавить водяной знак в PDF** — один из самых эффективных способов сделать это. Этот учебник проведёт вас через использование GroupDocs.Watermark для Java, чтобы внедрять как текстовые, так и графические водяные знаки в PDF‑файлы. К концу вы сможете:

- Инициализировать текстовые и графические водяные знаки
- Применять водяные знаки условно, в зависимости от размеров изображения
- **сохранить PDF с водяным знаком**, сохраняя исходное качество

Готовы защитить свои документы? Приступим!

## Быстрые ответы
- **Какая библиотека добавляет водяные знаки в PDF на Java?** GroupDocs.Watermark for Java.
- **Могу ли я добавить как текстовые, так и графические водяные знаки?** Да, API поддерживает оба типа за один запуск.
- **Нужна ли лицензия для разработки?** Бесплатная пробная версия подходит для тестирования; постоянная лицензия требуется для продакшн.
- **Какие форматы файлов поддерживаются?** Более 30 форматов, включая PDF, DOCX, PPTX и изображения.
- **Какой размер PDF можно обработать?** До 2000 страниц без загрузки всего файла в память.

## Что такое добавление водяного знака в PDF?
**Добавление водяного знака в PDF** означает внедрение видимых или невидимых меток — таких как текстовые строки или логотипы — непосредственно в PDF‑файл, чтобы указать право собственности, конфиденциальность или брендинг. Этот процесс изменяет визуальные слои документа, оставляя исходное содержание нетронутым.

## Почему использовать GroupDocs.Watermark для Java?
GroupDocs.Watermark поддерживает **более 30 форматов документов**, может обрабатывать PDF до **2000 страниц** за один проход и добавлять до **500 водяных знаков на документ** без заметного снижения производительности. Его API полностью потокобезопасен, что делает его идеальным для высоконагруженных серверных сред.

## Требования

Перед началом убедитесь, что у вас есть:

1. **Java Development Kit (JDK):** Версия 8 или новее установлена.
2. **GroupDocs.Watermark for Java:** Версия 24.11 (или новее) добавлена в ваш проект.
3. **Инструмент сборки:** Предпочтительно Maven, но прямое скачивание JAR также работает.

### Настройка окружения

#### Конфигурация Maven

Добавьте репозиторий GroupDocs и зависимость в ваш файл `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

#### Прямое скачивание

Или скачайте последнюю JAR‑файл со страницы официальных релизов: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Получение лицензии

Для бесплатной пробной версии или временной лицензии посетите портал лицензирования: [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Для продакшн‑развёртываний следует использовать приобретённую лицензию, чтобы убрать все ограничения пробной версии.

## Настройка GroupDocs.Watermark для Java

После добавления библиотеки импортируйте необходимые классы в ваш Java‑исходный файл:

```java
import com.groupdocs.watermark.Watermarker;
```

Этот блок импорта делает API, связанные с водяными знаками, доступными во всём проекте.

## Руководство по реализации

Мы разобьём реализацию на логические разделы, каждый из которых отвечает на конкретный вопрос.

### Как добавить водяной знак в PDF на Java?

`Watermarker` — основной класс, который загружает документ и позволяет применять водяные знаки.  
Загрузите ваш PDF с помощью `new Watermarker("input.pdf")`, затем примените объект водяного знака перед вызовом `save("output.pdf")`. Такой двухшаговый подход обрабатывает как текстовые, так и графические водяные знаки за один проход, обеспечивая эффективное **сохранить PDF с водяным знаком**.

### Инициализация текстового водяного знака

**Definition anchor:** `TextWatermark` — класс, представляющий текстовое наложение, которое может быть размещено на страницах, изображениях или векторной графике внутри документа.

#### Шаг 1: создать экземпляр TextWatermark

Создайте `TextWatermark`, используя желаемый текст и параметры шрифта:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

Этот пример устанавливает текст водяного знака «Protected image» с использованием Arial, размер 8.

#### Шаг 2: установить выравнивание

Центрируйте водяной знак по горизонтали и вертикали для равномерного позиционирования:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Шаг 3: повернуть водяной знак

Примените поворот на 45 градусов, чтобы сделать водяной знак труднее удалить:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Шаг 4: настроить размер

Масштабируйте водяной знак относительно размеров целевого изображения:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Инициализация графического водяного знака

**Definition anchor:** `ImageWatermark` инкапсулирует изображение (PNG, JPEG, BMP и т.д.), которое будет наложено на содержимое документа в качестве водяного знака.

#### Шаг 1: загрузить файл изображения

Загрузите изображение водяного знака с диска:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Замените путь-заполнитель фактическим расположением вашего логотипа или печати.

#### Шаг 2: установить выравнивание

Центрируйте графический водяной знак для сбалансированного визуального эффекта:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Шаг 3: повернуть графический водяной знак

Примените поворот на –30 градусов, чтобы добавить визуальное разнообразие:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Шаг 4: настроить размер

Определите размер изображения как процент от ширины базового изображения:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Добавление водяных знаков к изображениям в документе

**Definition anchor:** `Watermarker` — основной класс, который загружает документ, предоставляет доступ к его элементам и записывает водяные знаки обратно в файл.

#### Шаг 1: открыть документ

Создайте экземпляр `Watermarker`, указав путь к исходному PDF:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Шаг 2: получить изображения

Соберите все изображения из PDF, которые могут принимать водяной знак:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Шаг 3: добавить водяные знаки условно

Для каждого изображения проверьте его размеры; если ширина превышает 300 px, примените текстовый водяной знак, иначе используйте графический:

```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

Эта условная логика гарантирует, что только подходящие изображения получают более заметный текстовый наложение, оптимизируя время обработки.

#### Шаг 4: освободить ресурсы изображения

После обработки закройте объект графического водяного знака, чтобы освободить нативные ресурсы:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Шаг 5: сохранить изменения

Сохраните модификации, записав документ в новый файл:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

Полученный файл — это версия **сохранить PDF с водяным знаком**, готовая к распространению.

#### Шаг 6: очистка

Уничтожьте экземпляр `Watermarker`, чтобы предотвратить утечки памяти:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Распространённые проблемы и их устранение

- **Ошибки лицензии:** Убедитесь, что путь к файлу лицензии правильно установлен через `License.setLicense("license_file_path")`. Отсутствующая или просроченная лицензия вызывает `LicenseException`.
- **Большие PDF:** Для документов более 1000 страниц включите режим потоковой передачи, вызвав `watermarker.setStreamMode(true)`, чтобы снизить потребление памяти.
- **Неподдерживаемые форматы изображений:** GroupDocs.Watermark поддерживает PNG, JPEG, BMP и GIF. Конвертация других форматов в PNG перед загрузкой избегает `UnsupportedFormatException`.

## Часто задаваемые вопросы

**В: Могу ли я добавить водяной знак в PDF, защищённый паролем?**  
О: Да. Откройте документ с помощью `new Watermarker("file.pdf", "password")`, а затем примените водяной знак как обычно.

**В: Поддерживает ли API пакетную обработку нескольких PDF?**  
О: Абсолютно. Пройдитесь по папке с PDF, создайте `Watermarker` для каждого файла, примените одинаковые объекты водяных знаков и сохраните результаты.

**В: Каково максимальное количество водяных знаков, которое можно добавить в один PDF?**  
О: Библиотека может обработать **500+ водяных знаков на документ** без деградации производительности благодаря оптимизированному движку рендеринга.

**В: Можно ли сделать водяной знак невидимым (только метаданные)?**  
О: Да. Используйте метод `setOpacity(0)` у объекта водяного знака, чтобы внедрить его невидимо для судебного отслеживания.

**В: Какие версии Java официально поддерживаются?**  
О: GroupDocs.Watermark for Java поддерживает JDK 8, 11 и 17, обеспечивая совместимость как со старыми, так и с современными приложениями.

## Практические применения

1. **Безопасность документов:** Помечать конфиденциальные файлы, чтобы предотвратить несанкционированное распространение.
2. **Защита бренда:** Накладывать логотипы компании на маркетинговые PDF.
3. **Утверждение авторских прав:** Встраивать имена авторов или символы © в опубликованные работы.
4. **Контроль версий:** Проставлять номера версий или даты в черновиках.

## Заключение

Следуя этому **примеру водяного знака pdf на java**, вы теперь имеете полное, готовое к продакшн решение для **добавления водяного знака в PDF** с помощью GroupDocs.Watermark для Java. Вы можете настраивать текст, изображения, поворот и размер, а также условно применять водяные знаки в зависимости от размеров изображений — всё это быстро и с небольшим потреблением памяти.

---  

**Last Updated:** 2026-08-09  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## Связанные руководства

- [Как добавить текстовые и графические водяные знаки на отдельные страницы PDF с помощью GroupDocs.Watermark для Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Добавление только печатных водяных знаков в PDF с помощью GroupDocs.Watermark Java: Полное руководство](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Доступ и перебор артефактов PDF с помощью GroupDocs.Watermark в Java для водяного знака документов](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)