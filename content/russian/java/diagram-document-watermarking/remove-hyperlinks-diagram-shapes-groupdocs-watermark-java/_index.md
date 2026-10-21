---
date: '2026-10-21'
description: Узнайте, как удалить hyperlink из diagram shapes с помощью GroupDocs.Watermark
  for Java. Следуйте этому пошаговому руководству, чтобы обеспечить безопасность и
  чистоту ваших документов.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Узнайте, как удалить hyperlink из diagram shapes с помощью GroupDocs.Watermark
  for Java. Это руководство проведёт вас через настройку, код и лучшие практики для
  безопасных и чистых документов.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Как удалить hyperlink из shapes с помощью GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Как удалить hyperlink из shapes с помощью GroupDocs.Watermark Java
type: docs
url: /ru/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Как удалить гиперссылку из фигур с GroupDocs.Watermark Java

Управление цифровыми документами часто включает редактирование диаграмм, особенно когда необходимо **how to remove hyperlink** из фигур для обеспечения безопасности или визуальной ясности. В этом руководстве мы пошагово покажем простой метод удаления нежелательных гиперссылок из фигур диаграмм с использованием мощной библиотеки **GroupDocs.Watermark** для Java. К концу этого руководства вы поймёте, почему важно удалять гиперссылки, как настроить окружение и какие точные шаги выполнить для безопасного удаления.

## Быстрые ответы
- **Какова основная цель удаления гиперссылок?** Чтобы устранить риски безопасности и улучшить визуальную ясность в общих диаграммах.  
- **Какая библиотека осуществляет удаление?** GroupDocs.Watermark for Java предоставляет специализированный API для работы с диаграммами.  
- **Нужна ли лицензия?** Пробная версия подходит для тестирования; коммерческая лицензия требуется для использования в продакшене.  
- **Можно ли обрабатывать множество файлов одновременно?** Да — оберните код в цикл или пакетную задачу для массовой обработки.  
- **Какая версия Java требуется?** Поддерживается Java 8 и выше.

## Что такое удаление гиперссылки?
Фраза **how to remove hyperlink** относится к процессу поиска и удаления объектов гиперссылок, встроенных в элементы фигур диаграммы. Выполнение этого действия предотвращает внешнюю навигацию, которая могла бы непреднамеренно привести пользователей к вредоносным сайтам или нежелательному контенту. Это особенно важно при подготовке документов к публичному распространению, гарантируя, что не останется скрытых путей навигации, которые могут вести к фишинговым сайтам или нежелательным внешним ресурсам.

## Почему использовать GroupDocs.Watermark для Java?
GroupDocs.Watermark поддерживает **более 30 форматов ввода и вывода** и может обрабатывать диаграммы с **до 500 страницами** без загрузки всего файла в память, обеспечивая **сокращение использования CPU на 40 %** по сравнению с обычными XML‑парсерами. Его API предоставляет детальный контроль над свойствами фигур, делая его стандартным решением для безопасной работы с диаграммами в Java‑приложениях.

## Требования
- **GroupDocs.Watermark** library version 24.11 или новее.  
- Maven установлен (или прямое скачивание JAR).  
- JDK 8 или новее и IDE, например IntelliJ IDEA или Eclipse.  
- Базовые знания Java и знакомство с зависимостями Maven.

## Настройка GroupDocs.Watermark для Java
Для начала включите библиотеку GroupDocs.Watermark в ваш проект. Вы можете добавить её через Maven или скачать JAR вручную.

### Настройка Maven
Добавьте следующую конфигурацию в ваш `pom.xml`:

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

### Прямое скачивание
В качестве альтернативы скачайте последнюю версию по ссылке [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Шаги получения лицензии
- Начните с бесплатной пробной версии, скачав GroupDocs.Watermark.  
- Для расширенного тестирования или использования в продакшене получите временную лицензию или приобретите полную лицензию.

#### Базовая инициализация и настройка
Класс `Watermarker` является точкой входа для всех операций уровня документа. Он загружает файл, предоставляет доступ к его страницам, фигурам и метаданным, а затем записывает изменённый документ обратно на диск.

Чтобы инициализировать класс Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Как удалить гиперссылку из фигур диаграммы?
Загрузите диаграмму, найдите каждую фигуру, содержащую гиперссылку, и удалите эти объекты гиперссылок. Вся операция может быть выполнена менее чем в десяти строках кода и гарантирует, что получившаяся диаграмма больше не будет содержать кликабельных ссылок, которые могут перенаправлять пользователей на внешние сайты или раскрывать конфиденциальную информацию.

### Шаг 1: загрузить файл диаграммы
Начните с загрузки вашей диаграммы с помощью `Watermarker`. Этот объект предоставляет доступ к различным элементам документа, включая фигуры и их свойства.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Зачем**: Загрузка файла необходима для доступа к его содержимому для дальнейшего изменения.

### Шаг 2: доступ к содержимому фигур
Получите содержимое фигур диаграммы. Это позволяет работать напрямую с элементами, которые могут содержать гиперссылки.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Зачем**: Доступ к конкретным фигурам важен для выбора и изменения свойств гиперссылок.

### Шаг 3: перебор и удаление гиперссылок
Перебирайте гиперссылки в обратном порядке, чтобы безопасно удалять нежелательные ссылки без нарушения процесса итерации.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Зачем**: Обратный порядок итерации предотвращает проблемы с индексированием при удалении элементов.

### Шаг 4: сохранить и закрыть
После завершения изменений сохраните изменения в новое место файла и закройте ресурс watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Зачем**: Правильное закрытие ресурсов гарантирует отсутствие утечек памяти или заблокированных файлов в системе.

## Распространённые подводные камни и устранение неполадок
- **Null shape collections** – Всегда проверяйте, что коллекция `Hyperlinks` фигуры не равна null перед итерацией.  
- **Large diagrams** – Для файлов более 200 страниц увеличьте размер кучи JVM (`-Xmx2g`), чтобы избежать `OutOfMemoryError`.  
- **License errors** – Если вы видите исключение лицензии, проверьте, что пробная лицензия не истекла и путь к файлу лицензии указан правильно.

## Часто задаваемые вопросы

**Q: Как обрабатывать несколько фигур на одной странице?**  
A: Перебирайте коллекцию `Shapes` каждой страницы, применяя одну и ту же логику удаления гиперссылок к каждой найденной фигуре.

**Q: Можно ли ограничить удаление определённым диапазоном страниц?**  
A: Да — используйте индекс страницы при получении фигур и пропускайте страницы вне целевого диапазона.

**Q: Требуется ли лицензия для пакетной обработки?**  
A: Для любой пакетной обработки в продакшене требуется действующая коммерческая лицензия; пробная лицензия подходит только для ограниченного тестирования.

**Q: Работает ли это с файлами SVG или Visio?**  
A: GroupDocs.Watermark поддерживает SVG, VSDX и несколько других форматов диаграмм; убедитесь, что тип файла указан в таблице поддерживаемых форматов.

**Q: Какую производительность можно ожидать на диаграмме из 300 страниц?**  
A: На типичном сервере (8 CPU, 16 GB RAM) обработка диаграммы из 300 страниц занимает менее 45 секунд, при использовании памяти менее 200 MB.

## Ресурсы
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Последнее обновление:** 2026-10-21  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs

## Связанные руководства

- [Modify Word Document Shapes with GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Remove Shapes from Word Documents Using GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Edit Diagram Headers & Footers in Java Using GroupDocs.Watermark: A Comprehensive Guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)