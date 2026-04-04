---
date: '2026-04-04'
description: Узнайте, как удалять ссылки из фигур диаграмм с помощью GroupDocs.Watermark
  Java, обеспечивая безопасность и ясность документов.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Как удалить ссылки из фигур диаграммы с помощью GroupDocs.Watermark Java
type: docs
url: /ru/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Как удалить ссылки из фигур диаграммы с помощью GroupDocs.Watermark Java

Управление цифровыми документами часто включает редактирование диаграмм, особенно когда необходимо **how to strip links** для обеспечения безопасности или ясности. В этом руководстве вы узнаете простой пошаговый способ удаления нежелательных гиперссылок из фигур диаграммы с использованием мощной библиотеки **GroupDocs.Watermark** для Java. К концу вы получите чистые диаграммы без ссылок, безопасные для распространения.

## Быстрые ответы
- **What does “how to strip links” mean?** Это относится к удалению объектов гиперссылок, встроенных в фигуры диаграммы.  
- **Which library handles this?** GroupDocs.Watermark for Java (version 24.11 или новее).  
- **Do I need a license?** Бесплатная пробная версия подходит для тестирования; для продакшна требуется действующая лицензия.  
- **Can I process many files at once?** Да — оберните код в цикл или пакетную задачу.  
- **Is this approach language‑specific?** Пример написан на Java, но тот же концепт применим к другим API .NET/Java.

## Что означает «how to strip links» в редактировании диаграмм?
Удаление ссылок означает поиск объектов гиперссылок, прикреплённых к фигурам внутри диаграммы (например, Visio *.vsdx) и их удаление. Это устраняет внешние URL‑адреса, которые могут раскрыть конфиденциальную информацию или нарушить поток презентации.

## Почему использовать GroupDocs.Watermark для Java?
- **Precision** – Прямой доступ к объектам фигур и их коллекциям гиперссылок.  
- **Performance** – Оптимизировано для больших диаграмм без загрузки всего документа в память.  
- **Cross‑format support** – Работает со многими форматами диаграмм (Visio, Draw.io и др.).

## Предварительные требования
- **GroupDocs.Watermark** library ≥ 24.11.  
- Maven (или ручное подключение JAR).  
- Java JDK 8 или новее.  
- IDE, например IntelliJ IDEA или Eclipse.

## Настройка GroupDocs.Watermark для Java
### Настройка Maven
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

### Прямое скачивание
Если вы предпочитаете не использовать Maven, скачайте последнюю JAR‑файл с официального сайта:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Шаги получения лицензии
- Начните с загрузки бесплатной пробной версии.  
- Для продакшна получите временную или полную лицензию через портал GroupDocs.

#### Базовая инициализация и настройка
Создайте экземпляр `Watermarker`, указывающий на папку, содержащую вашу диаграмму:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Как удалить ссылки из фигур диаграммы
Ниже представлен краткий четырёхшаговый процесс, демонстрирующий **remove hyperlinks java** в действии.

### Шаг 1: Загрузка файла диаграммы
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Почему?* Загрузка файла предоставляет программный доступ к его страницам, фигурам и коллекциям гиперссылок.

### Шаг 2: Доступ к содержимому фигуры
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Почему?* Необходима ссылка на конкретную фигуру, которая может содержать гиперссылки.

### Шаг 3: Итерация и удаление гиперссылок
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Почему?* Обратный проход предотвращает проблемы со смещением индексов при удалении элементов из коллекции.

### Шаг 4: Сохранение и закрытие
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Почему?* Сохранение записывает очищенную диаграмму на диск, а закрытие освобождает файловые дескрипторы, предотвращая утечки памяти.

## Практические применения удаления ссылок
1. **Security** – Удалить внешние URL, которые могут привести к фишингу или утечке данных.  
2. **Compliance** – Обеспечить соответствие диаграмм внутренним политикам перед распространением.  
3. **Presentation Cleanliness** – Удалить ненужные кликабельные области, отвлекающие зрителей.

## Соображения по производительности
- **Loop Efficiency** – Используйте обратный паттерн итерации, показанный выше.  
- **Resource Management** – Предпочтительно использовать `try‑with‑resources` или явные вызовы `close()`.  
- **Large Files** – Следите за загрузкой CPU/памяти; рассмотрите обработку страниц пакетами.

## Распространённые проблемы и решения
- **No hyperlinks found** – Убедитесь, что диаграмма действительно содержит объекты гиперссылок; некоторые форматы хранят их иначе.  
- **IndexOutOfBoundsException** – Всегда итеративно проходите в обратном порядке при удалении элементов из коллекции.  
- **License errors** – Убедитесь, что файл лицензии правильно размещён или передан в конструктор `Watermarker`.

## Часто задаваемые вопросы

**Q: How do I handle multiple shapes on multiple pages?**  
A: Пройдите цикл по `content.getPages()`, а затем по коллекции `getShapes()` каждой страницы, применяя ту же логику удаления к каждой фигуре.

**Q: Can I filter links by domain instead of a full URL?**  
A: Да — измените проверку `contains`, чтобы искать строку домена (например, `"example.com"`).

**Q: Is there a way to log which links were removed?**  
A: Внутри цикла захватывайте `shape.getHyperlinks().get_Item(i).getAddress()` перед удалением и записывайте его в файл журнала.

**Q: Does this work with PDF diagrams embedded in other documents?**  
A: GroupDocs.Watermark поддерживает многие форматы; убедитесь, что тип файла распознаётся как диаграмма (Visio, VDX и др.).

**Q: What licensing is required for batch processing?**  
A: Для любых не‑пробных, высокообъёмных операций требуется полная производственная лицензия.

## Заключение
Теперь у вас есть полный, готовый к продакшну метод для **how to strip links** из фигур диаграммы с помощью GroupDocs.Watermark для Java. Внедрите его в свои конвейеры обработки документов, чтобы повысить безопасность, соответствие требованиям и визуальное качество.

### Следующие шаги
- Исследуйте другие функции манипуляций, такие как добавление водяных знаков или штампов текста.  
- Скомбинируйте эту процедуру с сервисом наблюдения за файлами, чтобы автоматически очищать диаграммы при их загрузке.

---

**Последнее обновление:** 2026-04-04  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs  

## Ресурсы
- [Документация](https://docs.groupdocs.com/watermark/java/)
- [Справочник API](https://reference.groupdocs.com/watermark/java)
- [Скачать](https://releases.groupdocs.com/watermark/java/)
- [Репозиторий GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Бесплатный форум поддержки](https://forum.groupdocs.com/c/watermark/10)
- [Получение временной лицензии](https://purchase.groupdocs.com/temporary-license/)