---
date: '2026-02-18'
description: Узнайте, как добавить водяной знак и как удалить водяной знак в файлах
  диаграмм, таких как .vsdx, с помощью GroupDocs.Watermark для Java. Защитите целостность
  документа с помощью GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Как добавить водяной знак в диаграммы с помощью GroupDocs.Watermark для Java
type: docs
url: /ru/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Как добавить водяной знак в диаграммы с помощью GroupDocs.Watermark для Java

Управление водяными знаками в файлах диаграмм является ключевой частью защиты интеллектуальной собственности и обеспечения чистоты документов для публичного распространения. В этом руководстве вы узнаете **how to add watermark** в диаграмму Visio, а также **how to remove watermark**, когда он больше не нужен, используя библиотеку **groupdocs watermark java**. Независимо от того, создаёте ли вы корпоративный конвейер обработки документов или быстрый утилитный скрипт, эти шаги дадут вам полный контроль над наложением водяных знаков на диаграммы.

## Быстрые ответы
- **Какая библиотека обрабатывает водяные знаки в диаграммах на Java?** GroupDocs.Watermark for Java.  
- **Могу ли я добавить и удалить водяные знаки в одном запуске?** Да — загрузите диаграмму один раз и выполните обе операции: добавление и удаление.  
- **Какие форматы файлов поддерживаются?** Visio formats such as `.vsdx`, `.vdx`, plus other diagram types.  
- **Нужна ли лицензия?** A trial license works for development; a full license is required for production.  
- **Какая версия Java требуется?** JDK 8 or higher.

## Что означает “how to add watermark” в контексте диаграмм?
Добавление водяного знака означает встраивание видимого или невидимого маркера — текста, логотипа или изображения — в файл диаграммы. Этот маркер перемещается вместе с файлом, облегчая доказательство прав собственности или пометку черновых версий.

## Почему использовать GroupDocs.Watermark для Java?
* **Rich API** – Поиск, добавление и удаление как текстовых, так и графических водяных знаков с помощью нескольких строк кода.  
* **Cross‑format support** – Работает с Visio (`.vsdx`, `.vdx`) и многими другими типами диаграмм.  
* **Performance‑focused** – Загружает только те части диаграммы, которые необходимы для операций с водяными знаками, снижая использование памяти.

## Предварительные требования
1. **Java Development Kit (JDK) 8+** – Убедитесь, что `java -version` выводит 1.8 или новее.  
2. **IDE** – IntelliJ IDEA, Eclipse или любой предпочитаемый редактор.  
3. **GroupDocs.Watermark for Java** – Добавьте её в проект через Maven или прямую загрузку JAR.  

### Требуемые библиотеки и зависимости
Добавьте репозиторий и зависимость в ваш `pom.xml`:

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

*Если вы предпочитаете не использовать Maven, можете скачать последнюю JAR‑файл с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Приобретение лицензии
- **Free Trial:** Тестируйте все функции без лицензионного ключа.  
- **Temporary License:** Запросите ограниченный по времени ключ для оценки.  
- **Full License:** Приобретите подписку для неограниченного использования в продакшене.

## Настройка GroupDocs.Watermark для Java
1. **Add the library** to your project (Maven or manual JAR). – Добавьте библиотеку в проект (Maven или вручную JAR).  
2. **Create a `Watermarker` instance** – this object is the entry point for loading diagrams, searching, adding, and removing watermarks. – этот объект является точкой входа для загрузки диаграмм, поиска, добавления и удаления водяных знаков.

## Руководство по реализации

### Загрузка документа диаграммы
Загрузка — первый шаг перед тем, как вы сможете **add watermark** или **remove watermark**. Ниже приведён код, показывающий, как открыть файл `.vsdx` с пользовательскими параметрами загрузки.

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

### Поиск текстовых водяных знаков
Прежде чем добавить новый водяной знак, вы можете проверить, существует ли уже текстовый водяной знак. Этот фрагмент ищет фразу «Company Name».

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

### Поиск графических водяных знаков
Если необходимо найти логотип или любое изображение, использованное в качестве водяного знака, используйте `ImageDctHashSearchCriteria`. Это удобно, когда нужно **remove watermark**, соответствующий известному логотипу.

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

### Удаление водяных знаков
После того как вы определили водяные знаки — текстовые, графические или оба — вы можете удалить их из диаграммы. Пример ниже демонстрирует комбинированную операцию удаления.

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

## Практические применения
1. **Enterprise Software Integration** – Внедрите управление водяными знаками в вашу ERP‑систему или платформу генерации документов для обеспечения брендинга.  
2. **Content Management Systems (CMS)** – Автоматически сканируйте загруженные диаграммы на наличие неавторизованных логотипов и удаляйте их.  
3. **Legal Document Handling** – Добавьте текстовый водяной знак «Confidential» на этапе черновика и позже **remove watermark** перед окончательной подачей.

## Распространённые проблемы и решения

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Водяные знаки не найдены | Текст/изображение поиска не совпадает точно | Используйте `or()` для объединения критериев или настройте чувствительность к регистру. |
| `OutOfMemoryError` при работе с большими файлами | Диаграмма загружается полностью в память | Используйте `DiagramLoadOptions.setLoadPages()` для загрузки только необходимых страниц. |
| Сохранённый файл повреждён | `watermarker.save()` вызван до очистки всех водяных знаков | Убедитесь, что `possibleWatermarks.clear()` завершён, а `watermarker.close()` вызывается после сохранения. |

## Часто задаваемые вопросы

**Q: Могу ли я искать одновременно и текст, и изображения?**  
A: Да. Объедините `TextSearchCriteria` и `ImageDctHashSearchCriteria` с помощью метода `or()`, как показано в примере удаления.

**Q: Можно ли удалить водяные знаки без повреждения диаграммы?**  
A: Абсолютно. Библиотека изолирует объекты водяных знаков, поэтому вызов `clear()` удаляет только слои водяных знаков, сохраняя оригинальное содержимое диаграммы.

**Q: Поддерживает ли GroupDocs.Watermark несколько форматов диаграмм?**  
A: Да. Форматы такие как `.vsdx`, `.vdx` и другие совместимые с Visio файлы полностью поддерживаются.

**Q: Как эффективно обрабатывать большие объёмы документов?**  
A: Реализуйте циклы пакетной обработки, переиспользуйте один экземпляр `Watermarker`, где это возможно, и ограничьте загрузку страниц с помощью `DiagramLoadOptions`.

**Q: Есть ли способ автоматизировать обнаружение водяных знаков в CI/CD конвейере?**  
A: Вы можете встроить предоставленные Java‑фрагменты в скрипты сборки (например, Maven или Gradle), чтобы проверять отсутствие неавторизованных водяных знаков перед выпуском артефактов.

---

**Последнее обновление:** 2026-02-18  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs