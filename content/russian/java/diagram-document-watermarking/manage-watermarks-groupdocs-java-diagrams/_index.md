---
date: '2026-10-27'
description: Узнайте, как удалить text watermark из файлов диаграмм с помощью GroupDocs.Watermark
  for Java и эффективно обнаруживать image watermark. Пошаговое руководство для разработчиков.
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: Удалите text watermark из файлов диаграмм с помощью GroupDocs.Watermark
  for Java. Узнайте, как обнаруживать image watermark, выполнять поиск и удалять водяные
  знаки с помощью code snippets.
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: Быстро удалить text watermark из файлов диаграмм с помощью Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: Как удалить text watermark в диаграммах с Java
type: docs
url: /ru/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Как удалить текстовый водяной знак в диаграммах с помощью Java

Управление водяными знаками в документах необходимо для защиты интеллектуальной собственности и поддержания целостности документа. В этом руководстве вы узнаете, как **удалить текстовый водяной знак** из файлов диаграмм, таких как `.vsdx`, с помощью GroupDocs.Watermark для Java, а также как **обнаружить графический водяной знак** при необходимости. Независимо от того, создаёте ли вы корпоративный конвейер обработки документов или автоматизируете простую пакетную задачу, эти техники дают вам детальный контроль над водяными знаками в диаграммах.

**Что вы узнаете**
- Настройка библиотеки GroupDocs.Watermark
- Загрузка документа диаграммы с определёнными параметрами
- Поиск и удаление текстовых водяных знаков
- Обнаружение графических водяных знаков и их удаление
- Лучшие практики для масштабной обработки

Готовы погрузиться? Сначала подготовим вашу среду.

## Быстрые ответы
- **Могу ли я удалить одновременно текстовые и графические водяные знаки?** Да – объедините `TextSearchCriteria` и `ImageDctHashSearchCriteria` с условием `or()`.  
- **Библиотека загружает всю диаграмму в память?** Нет – она потоково обрабатывает страницы, позволяя работать с файлами до 500 МБ без полного потребления памяти.  
- **Какие форматы диаграмм поддерживаются?** Более 20 форматов, включая `.vsdx`, `.vdx` и `.drawio`.  
- **Требуется ли лицензия для продакшн?** Для использования не в пробном режиме необходима действительная лицензия GroupDocs.Watermark.  
- **Могу ли я запускать это в CI/CD конвейере?** Конечно – API без графического интерфейса и работает на Windows, Linux и macOS.

## Что такое удаление текстового водяного знака?
Удаление текстового водяного знака означает удаление наложенных текстовых объектов, которые были добавлены в документ для указания прав собственности, конфиденциальности или статуса черновика. В GroupDocs.Watermark эта операция выполняется путем поиска объектов водяного знака с помощью критериев поиска и последующего вызова `clear()` у полученной коллекции.

## Почему обнаруживать графический водяной знак?
Обнаружение графического водяного знака позволяет идентифицировать графические логотипы или печати, встроенные в диаграмму. Это критически важно для проверок соответствия, защиты бренда и автоматической модерации контента. GroupDocs.Watermark использует перцептивное хеширование (DCT) для быстрого и точного сравнения изображений.

## Предварительные требования
Перед началом убедитесь, что у вас есть:
1. **Java Development Kit (JDK)** 8 или выше.  
2. **IDE** – IntelliJ IDEA, Eclipse или любой другой редактор по вашему выбору.  
3. **GroupDocs.Watermark for Java** – JAR‑файлы библиотеки должны быть в вашем classpath.  

### Требуемые библиотеки и зависимости
Вы можете добавить библиотеку через Maven или загрузить JAR‑файлы вручную.

#### Настройка Maven
Добавьте следующую конфигурацию в ваш файл `pom.xml`:

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
Либо загрузите последнюю версию с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Приобретение лицензии
- **Free trial** – протестировать все функции без лицензионного ключа.  
- **Temporary license** – запросить ограниченный по времени ключ для оценки.  
- **Purchase** – получить бессрочную или подписную лицензию для использования в продакшн.

## Настройка GroupDocs.Watermark для Java
1. **Install the library** – убедитесь, что репозиторий Maven и записи зависимостей присутствуют, либо разместите JAR‑файлы в `libs/` и добавьте их в путь сборки вашего проекта.  
2. **Initialize the API** – создайте экземпляр `Watermarker`; этот объект является точкой входа для загрузки диаграмм и выполнения операций с водяными знаками.

## Как удалить текстовый водяной знак в диаграммах с помощью Java
Чтобы удалить текстовый водяной знак, загрузите диаграмму с помощью `Watermarker`, создайте `TextSearchCriteria`, соответствующий тексту водяного знака, получите совпадающую `PossibleWatermarkCollection` и вызовите у неё `clear()`. Это удалит только указанные текстовые наложения, оставив остальную часть диаграммы нетронутой.

`Класс `Watermarker` представляет один документ в памяти и предоставляет методы для загрузки, поиска и изменения водяных знаков.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```
- **Параметры:**  
  - `inputFilePath`: Путь к вашему файлу `.vsdx`.  
  - `loadOptions`: Настраивает способ загрузки документа (например, диапазон страниц, пароль).

## Как обнаружить графический водяной знак в файле диаграммы?
Обнаружение графического водяного знака включает создание `ImageDctHashSearchCriteria` с эталонным изображением, а затем использование `Watermarker` для поиска в диаграмме. API генерирует перцептивный хеш каждого встроенного изображения и сравнивает его с эталоном, возвращая совпадения с оценками схожести, чтобы вы могли идентифицировать и удалить нежелательные логотипы или печати.

`ImageDctHashSearchCriteria` создаёт хеш эталонного изображения и сравнивает его с изображениями, встроенными в диаграмму, возвращая совпадения с оценкой схожести.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```
- **Ключевые методы:**  
  - `TextSearchCriteria` – создаёт критерий для текстовых водяных знаков.  
  - `PossibleWatermarkCollection` – содержит результаты любой операции поиска.

## Как удалить водяные знаки после их обнаружения?
После того как водяные знаки обнаружены, вы можете удалить их, вызвав метод `clear()` у `PossibleWatermarkCollection`, возвращённого поиском. Эта операция удаляет объекты водяных знаков, сохраняя все остальные элементы диаграммы, гарантируя, что оригинальное содержимое остаётся полностью неизменным.

`clear()` удаляет каждый водяной знак в коллекции, сохраняя остальное содержимое диаграммы.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```
- **Key method:** `clear()` – удаляет все водяные знаки в предоставленной коллекции без изменения других элементов диаграммы.

## Практические применения
1. **Enterprise software integration** – внедрить управление водяными знаками в бизнес‑приложения, ориентированные на документы, для защиты собственных диаграмм.  
2. **Content Management Systems (CMS)** – автоматизировать обнаружение неавторизованных логотипов перед публикацией пользовательских диаграмм.  
3. **Legal document handling** – добавлять или удалять водяные знаки на разных этапах рабочего процесса дел, обеспечивая соответствие политикам конфиденциальности.

## Распространённые подводные камни и устранение неполадок
- **Large files** – увеличьте параметр `maxMemory` в `LoadOptions`, если столкнётесь с `OutOfMemoryError`.  
- **Password‑protected diagrams** – укажите пароль в `LoadOptions` для открытия файла.  
- **Missing image hash matches** – убедитесь, что эталонное изображение имеет достаточное разрешение; изображения низкого разрешения могут давать слабые хеши.

## Часто задаваемые вопросы

**Q: Могу ли я искать одновременно текст и изображения?**  
A: Да – объедините `TextSearchCriteria` и `ImageDctHashSearchCriteria` с оператором `or()`, чтобы найти оба типа за один проход.

**Q: Возможно ли удалить водяные знаки без повреждения диаграммы?**  
A: Абсолютно. API изолирует объекты водяных знаков и удаляет их, оставляя оригинальную структуру диаграммы нетронутой.

**Q: Поддерживает ли GroupDocs.Watermark несколько форматов диаграмм?**  
A: Да – поддерживает более 20 форматов, включая `.vsdx`, `.vdx`, `.drawio` и `.svg`, обеспечивая широкие возможности управления диаграммами.

**Q: Как эффективно обрабатывать большие объёмы документов?**  
A: Используйте циклы пакетной обработки, переиспользуйте один экземпляр `Watermarker`, где это возможно, и настройте `LoadOptions` для потоковой обработки страниц вместо загрузки целых файлов.

**Q: Могу ли я интегрировать обнаружение водяных знаков в CI/CD конвейер?**  
A: Да – библиотека без графического интерфейса и может вызываться из Maven, Gradle или любого скрипта сборки для автоматической проверки ресурсов диаграмм.

**Последнее обновление:** 2026-10-27  
**Тестировано с:** GroupDocs.Watermark 23.6 for Java  
**Автор:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Связанные руководства

- [Как добавить текстовые водяные знаки в диаграммы с помощью GroupDocs.Watermark в Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Руководство по добавлению водяных знаков в диаграммы с помощью GroupDocs.Watermark для Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [Как получить информацию о документе с помощью GroupDocs.Watermark для Java: пошаговое руководство](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)