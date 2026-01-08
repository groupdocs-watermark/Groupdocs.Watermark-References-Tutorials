---
date: '2025-12-19'
description: Узнайте, как удалить гиперссылки из фигур диаграммы с помощью GroupDocs.Watermark
  Java, ключевой шаг для обеспечения безопасности Java‑документов и пакетного удаления
  гиперссылок.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Как удалить гиперссылки из фигур диаграммы с помощью GroupDocs.Watermark Java
type: docs
url: /ru/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Как удалить гиперссылки из фигур диаграммы с помощью GroupDocs.Watermark Java

Управление цифровыми документами часто включает редактирование диаграмм, особенно при **удалении гиперссылок** в целях безопасности или ясности. В этом руководстве вы узнаете **как удалить гиперссылки** из фигур диаграммы с помощью GroupDocs.Watermark для Java, обеспечивая чистоту, безопасность и профессиональный вид ваших файлов.

## Quick Answers
- **Какова основная цель?** Удалить нежелательные гиперссылки из фигур диаграммы для повышения безопасности документа.  
- **Какая библиотека используется?** GroupDocs.Watermark for Java (version 24.11 or later).  
- **Нужна ли лицензия?** Пробная версия подходит для тестирования; для продакшна требуется действующая лицензия.  
- **Можно ли обрабатывать множество файлов одновременно?** Да — ту же логику можно разместить внутри пакетного цикла.  
- **Достаточно ли Java 8?** Поддерживается Java 8+; рекомендуется использовать более новые JDK.

## Что означает «удаление гиперссылок» в контексте диаграмм?
Удаление гиперссылок означает удаление URL‑ссылок, прикреплённых к фигурам внутри файла диаграммы (например, Visio *.vsdx). Эта операция предотвращает случайный переход на внешние сайты и помогает соответствовать требованиям комплаенса или внутренним политикам безопасности.

## Почему использовать GroupDocs.Watermark Java для этой задачи?
- **Широкая поддержка форматов** – работает с большим набором типов диаграмм.  
- **Тонко настроенный API** – позволяет работать с отдельными фигурами и их коллекциями гиперссылок.  
- **Оптимизированная производительность** – подходит как для одиночных файлов, так и для пакетной обработки.  

## Prerequisites
- **GroupDocs.Watermark** library version 24.11 or later.  
- Maven или прямое скачивание JAR (см. шаги настройки ниже).  
- Java Development Kit (JDK 8 или новее) и IDE, например IntelliJ IDEA или Eclipse.  

## Setting Up GroupDocs.Watermark for Java
Для начала включите библиотеку в ваш проект через Maven или скачав JAR.

### Maven Setup
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

### Direct Download
Или скачайте последнюю версию с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### License Acquisition Steps
- Начните с бесплатной пробной версии, чтобы оценить API.  
- Для продакшна получите временную или полную лицензию через портал GroupDocs.  

#### Basic Initialization and Setup
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## How to Remove Hyperlinks from Diagram Shapes
Ниже представлено пошаговое руководство, которое проведёт вас через загрузку диаграммы, поиск фигур и удаление нежелательных гиперссылок.

### Step 1: Load the Diagram File
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Почему?* Загрузка файла предоставляет программный доступ к его внутренней структуре.

### Step 2: Access Shape Content
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Почему?* Вам нужна ссылка на конкретную фигуру, которая может содержать гиперссылки.

### Step 3: Iterate and Remove Hyperlinks
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Почему?* Обратный обход предотвращает ошибки индексов при удалении элементов из коллекции.

### Step 4: Save and Close
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Почему?* Сохранение изменений и освобождение ресурсов предотвращает утечки памяти и блокировку файлов.

## Batch Remove Hyperlinks (Advanced Use Case)
Если необходимо очистить множество диаграмм одновременно, оберните вышеуказанную логику в цикл, который проходит по списку путей к файлам. Те же вызовы API применяются; просто измените входные и выходные каталоги для каждой итерации. Такой подход соответствует требованиям **batch remove hyperlinks** для больших репозиториев документов.

## Practical Applications
Удаление гиперссылок из фигур диаграммы может быть полезным в нескольких реальных сценариях:

1. **Цели безопасности** – Предотвратить внешние ссылки, которые могут подвергнуть вашу сеть фишингу или вредоносному ПО.  
2. **Соответствие** – Соблюдать корпоративные политики, запрещающие внешние URL в общих документах.  
3. **Ясность** – Создавать более чистые презентации, где гиперссылки не нужны или отвлекают.  

## Performance Considerations
### Optimizing Performance
- Используйте обратный обход, показанный выше, чтобы сделать циклы более эффективными.  
- Закрывайте объект `Watermarker` сразу после завершения работы, чтобы освободить память.

### Resource Usage Guidelines
- Следите за загрузкой CPU и RAM при обработке больших диаграмм.  
- Для пакетных задач рассмотрите потоковую обработку файлов вместо их одновременной загрузки.

### Best Practices for Java Memory Management
- Избегайте создания объектов внутри плотных циклов.  
- При возможности используйте try‑with‑resources для автоматической очистки.

## Frequently Asked Questions
1. **Как обрабатывать несколько фигур?**  
   Итерируйтесь по всем страницам и их фигурам, применяя одну и ту же логику удаления гиперссылок к каждой фигуре.  

2. **Можно ли автоматизировать процесс для больших пакетов диаграмм?**  
   Да — внедрите код в процедуру пакетной обработки или интегрируйте его с вашей системой управления документами.  

3. **Что делать, если нужно удалить гиперссылки только с определённых страниц?**  
   Получите нужную страницу по её индексу (`content.getPages().get_Item(pageIndex)`) и целенаправленно обрабатывайте фигуры только на этой странице.  

4. **Требуется ли лицензия для продакшн‑использования GroupDocs.Watermark?**  
   Для использования за пределами пробного периода требуется действующая коммерческая лицензия.  

5. **Можно ли использовать этот метод с другими форматами диаграмм?**  
   GroupDocs.Watermark поддерживает множество типов диаграмм; проверьте совместимость в официальной документации.  

**Additional Q&A**

**Q:** *Is it possible to log which hyperlinks were removed?*  
**A:** Yes – before calling `removeAt(i)`, capture `shape.getHyperlinks().get_Item(i).getAddress()` and write it to a log file.

**Q:** *Will removing hyperlinks affect the visual appearance of the shape?*  
**A:** No. The shape’s geometry stays unchanged; only the link metadata is stripped.

**Q:** *Do I need to re‑apply any styling after removal?*  
**A:** Not usually. Hyperlink removal does not alter fill, line, or text styles.

## Conclusion
Вы теперь имеете полный, готовый к продакшну метод **как удалить гиперссылки** из фигур диаграммы с помощью GroupDocs.Watermark для Java. Следуя приведённым шагам, вы сможете защитить свои диаграммы, соблюдать политики и поддерживать документы в безупречном виде.

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Resources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)