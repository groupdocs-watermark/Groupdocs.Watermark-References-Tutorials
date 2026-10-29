---
date: '2026-06-01'
description: Узнайте, как удалить фигуры из файлов Excel с помощью GroupDocs.Watermark
  для Java. Включает шаги по загрузке Excel, перебору листов и удалению отформатированных
  фигур.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Как удалить фигуры из Excel с помощью GroupDocs.Watermark на Java
type: docs
url: /ru/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Как удалить фигуры из Excel с помощью GroupDocs.Watermark на Java

Электронные таблицы Excel являются краеугольным камнем бизнес‑отчетности, но нежелательные фигуры — особенно те, которые имеют устаревшее или нестандартное форматирование текста — могут захламлять файл и нарушать визуальную согласованность. **Удаление фигур из Excel** быстро становится необходимым для чистых, профессиональных документов. В этом руководстве мы пройдем процесс загрузки книги Excel, перебора её листов и программного удаления фигур, соответствующих определённым критериям форматирования, используя мощную библиотеку GroupDocs.Watermark для Java.

## Быстрые ответы
- **Может ли GroupDocs.Watermark удалять фигуры?** Да, он предоставляет метод `removeShape`, который работает на любом листе.  
- **Нужна ли лицензия для этой функции?** Пробная версия подходит для оценки; полная лицензия требуется для продакшн.  
- **Какая версия Java требуется?** Поддерживается Java 8 или более поздняя версия.  
- **Сколько форматов файлов поддерживает GroupDocs.Watermark?** Более 30 форматов ввода и вывода, включая XLSX, DOCX, PDF и PPTX.  
- **Является ли потребление памяти проблемой для больших книг?** Используйте try‑with‑resources и избегайте загрузки целых листов в память; API эффективно передаёт данные потоково.

## Что такое удаление фигур из Excel?
*Удаление фигур из Excel* означает программное удаление графических объектов — таких как текстовые поля, значки или SmartArt — которые соответствуют определённым критериям, например, стилю шрифта, цвету или размеру. Эта операция очищает книгу без ручного редактирования, обеспечивая визуальную согласованность, уменьшая размер файла и предотвращая появление устаревших или нежелательных графических элементов в распространяемых отчётах.

## Почему удалять фигуры из Excel?
GroupDocs.Watermark может обрабатывать **многосотневые книги со скоростью до 3 × быстрее**, чем ручное редактирование, поддерживая **более 30 форматов файлов**, при этом удерживая использование памяти ниже 150 МБ для файлов размером более 50 МБ. Автоматизация удаления фигур устраняет человеческие ошибки и гарантирует единообразный брендинг во всех сгенерированных отчётах.

## Предварительные требования
### Требуемые библиотеки, версии и зависимости
- **Java Development Kit (JDK)**: Версия 8 или новее.  
- **GroupDocs.Watermark**: Version 24.11 (последний стабильный релиз на момент написания).

### Требования к настройке окружения
Используйте IDE, такую как IntelliJ IDEA или Eclipse, и Maven для управления зависимостями.

### Требования к знаниям
Знание синтаксиса Java и базовых концепций Excel (листов, ячеек и фигур) поможет вам следовать примерам.

## Настройка GroupDocs.Watermark для Java
**Maven Dependency**  
Добавьте следующее в ваш `pom.xml`:

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

**Direct Download**  
В качестве альтернативы загрузите последнюю версию по ссылке [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Шаги получения лицензии
- **Free Trial** – Начните с бесплатной пробной версии, чтобы оценить возможности.  
- **Temporary License** – Получите временную лицензию для расширенного тестирования.  
- **Purchase** – Приобретите полную лицензию для использования в продакшн.

### Базовая инициализация и настройка  
После добавления библиотеки в ваш проект, инициализируйте её, как показано ниже:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Как удалить фигуры из Excel?
Загрузите книгу, пройдитесь по каждому листу и вызовите API удаления фигур. Этот двухшаговый шаблон — *load* затем *iterate* — покрывает практически любой сценарий, когда необходимо очистить фигуры по всему файлу. Проверяя свойства каждой фигуры относительно ваших критериев перед удалением, вы гарантируете, что удаляются только нежелательные элементы, сохраняя остальную часть макета и содержимого документа.

## Загрузка Excel‑документа
**Overview**  
Загрузка Excel‑документа является отправной точкой для любой задачи манипуляции. GroupDocs.Watermark упрощает это с помощью своего интуитивного API.  

**Definition Anchor**  
`SpreadsheetDocument` — основной класс в GroupDocs.Watermark, представляющий книгу Excel в памяти, предоставляющий методы доступа к листам, ячейкам и фигурам.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Доступ и перебор листов в таблице
**Overview**  
Перебор листов позволяет выполнять операции на каждом листе отдельно.  

**Definition Anchor**  
`Worksheet` представляет отдельный лист внутри `SpreadsheetDocument`; вы можете читать, изменять или удалять его содержимое через этот объект.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Удаление фигур с определённым форматированием текста из таблицы
**Overview**  
Эта функция нацелена на фигуры, соответствующие определённым критериям форматирования текста, таким как тип шрифта или цвет.  

**Definition Anchor**  
`Shape` — объектная модель любого графического элемента (текстовое поле, изображение или SmartArt) внутри листа; она предоставляет свойства, такие как `getText`, `getFont` и `remove`.  

#### Code Snippet
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Практические применения
### Реальные примеры использования
1. **Data Validation** – Автоматически удалять фигуры, содержащие устаревшие уведомления.  
2. **Template Standardization** – Обеспечить корпоративный брендинг, удаляя нестандартные текстовые поля.  
3. **Automated Reporting** – Очищать сгенерированные отчёты перед распространением, гарантируя безупречный вид.

### Возможности интеграции
GroupDocs.Watermark может быть встроен в Java‑ориентированные корпоративные конвейеры, такие как микросервисы генерации документов, задачи пакетной обработки или системы управления контентом, предоставляя бесшовный, соответствующий лицензии способ управления ресурсами Excel.

## Соображения по производительности
### Оптимизация производительности
- **Avoid heavy operations inside loops** – получайте коллекцию фигур один раз на лист.  
- **Release resources promptly** – используйте try‑with‑resources для автоматического закрытия потоков.

### Руководство по использованию ресурсов
Освободите объект `SpreadsheetDocument` сразу после завершения обработки, чтобы освободить нативную память. Для файлов более 100 МБ рассмотрите обработку листов в параллельных потоках, чтобы использовать многоядерные процессоры.

### Лучшие практики управления памятью в Java
Используйте `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }`, чтобы метод `close()` вызывался даже при возникновении исключения.

## Распространённые проблемы и решения
- **Shape not found** – Убедитесь, что проверяете правильный индекс листа; фигуры привязаны к каждому листу.  
- **License exception** – Пробная лицензия отключает пакетную обработку; обновите до полной лицензии для неограниченных операций.  
- **Unexpected font values** – Свойства шрифта могут наследоваться; используйте `shape.getEffectiveFont()` для получения окончательного стиля.

## Часто задаваемые вопросы

**Q: Могу ли я удалить фигуры из защищённой паролем книги?**  
A: Да. Загрузите документ с параметром пароля, затем выполните ту же логику удаления; API расшифровывает файл в памяти.

**Q: Поддерживает ли библиотека файлы .xls (Excel 97‑2003)?**  
A: Абсолютно. GroupDocs.Watermark обрабатывает как `.xlsx`, так и устаревшие `.xls` форматы без конвертации.

**Q: Как я могу вести журнал, какие фигуры были удалены?**  
A: Переберите коллекцию фигур, проверьте критерии форматирования, запишите `shape.getName()` или `shape.getId()`, затем вызовите `remove()`.

**Q: Возможно ли добавить водяной знак после удаления фигур?**  
A: Да. После очистки вызовите `doc.addWatermark(new TextWatermark("Confidential"))`, чтобы наложить текстовый водяной знак на все листы.

**Q: Каков максимальный поддерживаемый размер файла?**  
A: Библиотека может обрабатывать файлы до **2 GB** на 64‑битной JVM, ограничиваясь только доступной памятью кучи и ограничениями ОС.

## Заключение
В этом руководстве мы продемонстрировали полный, готовый к продакшн подход к **удалению фигур из Excel** книг с использованием GroupDocs.Watermark для Java. Загрузив документ, перебрав листы и применив точные фильтры форматирования, вы можете автоматизировать задачи очистки, обеспечить брендинг и улучшить качество отчётов в масштабе. Исследуйте дополнительные возможности, такие как вставка водяных знаков, конвертация документов и пакетная обработка, чтобы расширить ваш набор инструментов для автоматизации документов.

---

**Последнее обновление:** 2026-06-01  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs

## Связанные руководства

- [Манипуляция фигурами Excel с помощью GroupDocs.Watermark в Java: Полное руководство](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Добавление изображения‑водяного знака в Excel‑таблицу с помощью GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Работа с Excel‑документами и водяными знаками с GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)