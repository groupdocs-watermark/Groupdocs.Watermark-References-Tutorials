---
date: '2026-02-13'
description: Узнайте, как извлекать формы и получать изображение из формы с помощью
  GroupDocs.Watermark для Java, эффективно получая подробную информацию о диаграмме.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Как извлечь формы из диаграмм с помощью GroupDocs.Watermark в Java
type: docs
url: /ru/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Как извлекать фигуры из диаграмм с помощью GroupDocs.Watermark на Java

Когда вам нужно **how to extract shapes** из диаграммы в стиле Visio программно, библиотека GroupDocs.Watermark предоставляет чистый, ориентированный на Java способ получить каждую деталь — размеры, позиции, встроенные изображения и даже текст внутри каждой фигуры. В этом руководстве вы увидите точно **how to extract shapes**, почему это важно, и пошаговый код, который можно скопировать в ваш проект.

## Быстрые ответы
- **Какая библиотека обрабатывает извлечение фигур?** GroupDocs.Watermark for Java  
- **Какая версия Java требуется?** JDK 8 или выше  
- **Можно ли получить данные изображения из фигуры?** Да – используйте `shape.getImage()`  
- **Доступен ли текст внутри фигуры?** Абсолютно, через `shape.getText()`  
- **Нужна ли лицензия для продакшн?** Требуется действующая лицензия GroupDocs.Watermark  

## Введение

Управление сложными диаграммами часто требует доступа к подробной информации об их компонентах, таких как фигуры и изображения. Если вам когда‑нибудь нужно было программно получать данные, такие как размеры, позиции или текст, связанные с фигурами диаграммы, используя Java, это руководство для вас. Использование возможностей библиотеки GroupDocs.Watermark может упростить этот процесс в Java‑приложении. В этом руководстве мы пройдем через **how to extract shapes** из файла диаграммы, а также покажем, как **extract image from shape** и **extract text from shape**.

## Что такое “how to extract shapes”?

Извлечение фигур означает чтение внутренних объектов диаграммы (страницы, фигуры, изображения, текст), чтобы вы могли анализировать, преобразовывать или повторно использовать их в других приложениях — идеально для автоматизации, отчетности или интеграции с CAD‑инструментами.

## Почему использовать GroupDocs.Watermark для извлечения фигур?

- **Полная поддержка форматов** – работает с VSDX, VDX и многими другими типами диаграмм.  
- **Богатая объектная модель** – предоставляет прямой доступ к геометрии фигур, изображениям и тексту.  
- **Отсутствие внешних зависимостей** – чистый Java, легко встраивается в Maven‑проекты.  

## Предварительные требования
- **GroupDocs.Watermark for Java** (version 24.11 or later)  
- Java Development Kit (JDK) 8 или выше  
- Maven для управления зависимостями  
- IDE, например IntelliJ IDEA или Eclipse  

## Настройка GroupDocs.Watermark для Java

Добавьте библиотеку в ваш Maven `pom.xml`:

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

Вы также можете скачать последние бинарные файлы с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Шаги получения лицензии
- **Free Trial:** Скачайте пробный пакет для оценки API.  
- **Temporary License:** Запросите временный ключ для расширенного тестирования.  
- **Purchase:** Приобретите полную лицензию для использования в продакшн.  

### Базовая инициализация и настройка

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Как извлекать фигуры – руководство по реализации

### Загрузка и получение содержимого

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Итерация по фигурам

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Как извлечь изображение из фигуры

Вызов `shape.getImage()` возвращает объект, содержащий необработанный bitmap, его размеры и массив байтов. Используйте показанные выше свойства, чтобы сохранить изображение на диск или передать его в другой конвейер обработки.

### Как извлечь текст из фигуры

Метод `shape.getText()` возвращает простой текст внутри фигуры. Если фигура не содержит текста, метод возвращает `null`. Пример цикла уже выводит текст, и вы можете дальше манипулировать им — например, построить индекс всех меток фигур.

## Советы по устранению неполадок
- Проверьте путь к файлу и права чтения.  
- Убедитесь, что используете поддерживаемый формат диаграммы (VSDX, VDX и т.д.).  
- Если фигура отображается без ожидаемых данных, проверьте примечания к выпуску библиотеки на предмет особенностей формата.  

## Практические применения
1. **Diagram Analysis:** Автоматически проверять диаграммы на соответствие, проверяя размеры фигур или отсутствие меток.  
2. **Data Visualization:** Передавать извлечённые размеры в панель отчётов для визуализации плотности размещения.  
3. **CAD Integration:** Объединять данные фигур с CAD‑API для синхронизации спецификаций дизайна между инструментами.  

## Соображения по производительности
- **Close resources:** Вызовите `watermarker.close()` после завершения, чтобы освободить нативные ресурсы.  
- **Memory management:** Большие диаграммы могут потреблять значительный объём heap; следите за памятью и при необходимости увеличьте `-Xmx`.  
- **Batch processing:** Обрабатывайте файлы пакетами и при возможности переиспользуйте один экземпляр `Watermarker`.  

## Заключение

Следуя этому руководству, вы теперь знаете **how to extract shapes**, как **extract image from shape**, и как **extract text from shape** с помощью GroupDocs.Watermark for Java. Эти техники открывают возможности для автоматизированного анализа диаграмм, отчетности и интеграции с другими инженерными системами. На следующем этапе изучите полный API, ознакомившись с его [documentation](https://docs.groupdocs.com/watermark/java/), и попробуйте комбинировать извлечение фигур с пользовательской бизнес‑логикой.

## Раздел FAQ
1. **Что такое GroupDocs.Watermark?**  
   - Комплексная Java‑библиотека, предназначенная для наложения водяных знаков и извлечения информации из различных форматов документов, включая диаграммы.  

2. **Могу ли я использовать эту библиотеку для обработки всех типов файлов диаграмм?**  
   - Да, но убедитесь, что формат файла поддерживается, проверив [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Как извлечь размеры и позиции фигур из диаграммы с помощью Java и GroupDocs.Watermark?**  
   - Загрузите диаграмму, получите доступ к `DiagramContent`, затем пройдитесь по фигурам, чтобы получить свойства такие как ширина, высота, X и Y.  

4. **Может ли GroupDocs.Watermark извлекать изображения, встроенные в фигуры диаграмм, с помощью Java?**  
   - Да, она предоставляет методы доступа к данным изображений внутри фигур, включая размер и пиксельные данные, полезные для анализа или модификации.  

5. **Каковы предварительные требования для извлечения информации о фигурах диаграммы в Java?**  
   - Java JDK 8+, настройка Maven, библиотека GroupDocs.Watermark (24.11+), и базовые знания Java являются необходимыми для реализации.  

---

**Последнее обновление:** 2026-02-13  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs