---
date: '2025-12-19'
description: Узнайте, как использовать GroupDocs Watermark Maven для управления водяными
  знаками в файлах диаграмм, таких как .vsdx, с помощью Java, повышая целостность
  документов и защищая интеллектуальную собственность.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Управляйте водяными знаками диаграмм с помощью
  Java
type: docs
url: /ru/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Управление водяными знаками диаграмм с помощью Java

Управление водяными знаками в документах необходимо для защиты интеллектуальной собственности и поддержания целостности документов. **В этом руководстве мы покажем, как использовать groupdocs watermark maven для эффективной загрузки, поиска и удаления водяных знаков из файлов диаграмм, таких как `.vsdx`**. Независимо от того, разрабатываете ли вы корпоративное программное обеспечение или автоматизируете документооборот, освоение этих техник даст вам полный контроль над управлением водяными знаками диаграмм.

## Быстрые ответы
- **Какая библиотека нужна?** GroupDocs.Watermark for Java (доступна через Maven).  
- **Какие форматы диаграмм поддерживаются?** `.vsdx`, `.vdx` и другие форматы Visio.  
- **Можно ли искать как текстовые, так и графические водяные знаки?** Да – комбинируйте критерии поиска с `or()`.  
- **Нужна ли лицензия для продакшн?** Требуется действующая лицензия GroupDocs.Watermark.  
- **Как интегрировать это в Maven?** Добавьте репозиторий и зависимость, показанные ниже.

## Что такое groupdocs watermark maven?
`groupdocs watermark maven` — это интеграция библиотеки GroupDocs.Watermark для Java на основе Maven. Объявив библиотеку в вашем `pom.xml`, Maven автоматически разрешит все необходимые бинарные файлы, позволяя вам сосредоточиться на коде, который загружает диаграммы, ищет водяные знаки и удаляет их программно.

## Почему стоит использовать GroupDocs.Watermark для управления водяными знаками диаграмм?
- **Полнофункциональное API** — поддерживает текстовые, графические и фигурные водяные знаки во множестве типов диаграмм.  
- **Точное удаление** — устраняет водяные знаки без повреждения исходного макета диаграммы.  
- **Масштабируемость** — подходит для пакетной обработки больших коллекций диаграмм.  
- **Удобство Maven** — простое управление зависимостями, ваш проект остаётся чистым.

## Предварительные требования
1. **Java Development Kit (JDK) 8+** — обеспечивает совместимость с библиотекой.  
2. **IDE** — IntelliJ IDEA, Eclipse или любой совместимый с Java редактор.  
3. **GroupDocs.Watermark for Java** — добавляется через Maven (рекомендовано) или прямой загрузкой JAR‑файла.  

### Требуемые библиотеки и зависимости
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

#### Прямая загрузка
Или скачайте последнюю версию с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Приобретение лицензии
- **Бесплатная пробная версия:** протестируйте библиотеку с пробной лицензией.  
- **Временная лицензия:** запросите краткосрочный ключ для оценки.  
- **Покупка:** получите производственную лицензию для неограниченного использования.

## Использование groupdocs watermark maven для загрузки документа диаграммы
Загрузка документа диаграммы — первый шаг перед любой операцией с водяными знаками. Ниже приведён минимальный пример, создающий экземпляр `Watermarker` с `DiagramLoadOptions`.

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
  - `inputFilePath` — путь к вашему файлу `.vsdx`.  
  - `loadOptions` — позволяет управлять тем, как диаграмма будет разобрана (например, защита паролем).

## Поиск водяных знаков с помощью groupdocs watermark maven
### Текстовые водяные знаки
Чтобы найти текстовые водяные знаки, определите `TextSearchCriteria` и выполните запрос к первой странице диаграммы.

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
  - `TextSearchCriteria` — задаёт точный текст для поиска.  
  - `PossibleWatermarkCollection` — хранит найденные совпадения.

### Графические водяные знаки
Если в вашей диаграмме присутствуют логотипы или изображения‑водяные знаки, используйте `ImageDctHashSearchCriteria` для сравнения с эталонным изображением.

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

- **Ключевые методы:**  
  - `ImageDctHashSearchCriteria` — создаёт перцептивный хеш эталонного изображения для надёжного сопоставления.

## Удаление водяных знаков
После того как нежелательные водяные знаки обнаружены, их можно очистить и сохранить чистую копию диаграммы.

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

- **Ключевой метод:** `clear()` — удаляет каждый найденный водяной знак, соответствующий объединённым критериям, оставляя диаграмму нетронутой.

## Практические применения
1. **Интеграция в корпоративное ПО** — внедрите управление водяными знаками в бизнес‑приложения для защиты собственных диаграмм.  
2. **Системы управления контентом (CMS)** — автоматизируйте обнаружение и удаление неавторизованных логотипов перед публикацией.  
3. **Юридические документообороты** — добавляйте или удаляйте водяные знаки на разных этапах обработки контрактов.  

## Распространённые проблемы и их решение
- **Ошибки лицензии:** убедитесь, что файл лицензии правильно указан перед созданием `Watermarker`.  
- **Большие файлы:** используйте потоковые API или увеличьте размер кучи JVM (`-Xmx2g`) для диаграмм более 100 МБ.  
- **Не найдены водяные знаки:** проверьте, что критерии поиска (регистр текста, порог схожести изображения) соответствуют реальному содержимому водяного знака.

## Часто задаваемые вопросы

**В: Можно ли искать одновременно текст и изображения?**  
О: Да. Комбинируйте критерии с `or()` как показано в примере удаления.

**В: Безопасно ли удалять водяные знаки без изменения макета диаграммы?**  
О: Абсолютно. API точно нацеливается на объекты водяных знаков, сохраняя все остальные элементы диаграммы.

**В: Какие форматы диаграмм поддерживает GroupDocs.Watermark?**  
О: Поддерживаются форматы Visio, такие как `.vsdx`, `.vdx`, а также другие векторные типы диаграмм.

**В: Как эффективно обрабатывать сотни диаграмм?**  
О: Реализуйте пакетный цикл, переиспользуйте один экземпляр `Watermarker`, когда это возможно, и рассмотрите параллельную обработку с помощью `ExecutorService` в Java.

**В: Можно ли интегрировать обнаружение водяных знаков в CI/CD pipeline?**  
О: Да. Включите Java‑фрагменты в скрипты сборки (например, Maven‑плагины или задачи Gradle) для проверки диаграмм перед развертыванием.

## Заключение
Используя **groupdocs watermark maven**, вы получаете мощный, управляемый Maven способ загрузки, поиска и удаления водяных знаков из файлов диаграмм с помощью Java. Эта возможность повышает безопасность документов, упрощает рабочие процессы с контентом и без труда масштабируется на большие коллекции файлов.

---

**Последнее обновление:** 2025-12-19  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs  

---