---
date: '2026-01-23'
description: Узнайте, как добавлять текстовые и графические водяные знаки в PDF‑файлы
  с помощью GroupDocs.Watermark для Java — полное руководство по защите PDF‑документов.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Как добавить водяной знак в PDF с помощью GroupDocs.Watermark для Java
type: docs
url: /ru/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Как добавить водяной знак в PDF с помощью GroupDocs.Watermark для Java

В современном цифровом мире **как добавить водяной знак в PDF**‑файлы — это частый вопрос для тех, кто хочет защитить интеллектуальную собственность или бренд‑активы. Добавление водяных знаков — текстовых или изображений — помогает обеспечить **безопасность PDF‑документов** и делает несанкционированное распространение гораздо сложнее. В этом руководстве вы шаг за шагом узнаете, как использовать **GroupDocs.Watermark для Java**, чтобы добавить как текстовые, так и графические водяные знаки в PDF‑документы.

## Быстрые ответы
- **Какая библиотека добавляет водяные знаки в PDF на Java?** GroupDocs.Watermark для Java.  
- **Можно ли добавить одновременно текстовый и графический водяной знак?** Да, API поддерживает оба типа.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для оценки; платная лицензия снимает ограничения.  
- **Какая версия Java требуется?** JDK 8 или выше.  
- **Поддерживается ли Maven?** Абсолютно — достаточно добавить репозиторий и зависимость.

## Что такое водяной знак PDF и зачем он нужен?
Водяной знак PDF — это видимый или скрытый маркер, который указывает на право собственности, конфиденциальность или брендирование. Это лёгкий, но мощный способ препятствовать копированию, подтверждать авторство и соответствовать корпоративным политикам.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

1. **Java Development Kit (JDK) 8+** установлен на вашем компьютере.  
2. **GroupDocs.Watermark для Java** (последняя версия).  
3. **Maven** (или возможность добавить JAR вручную).

### Настройка окружения

#### Конфигурация Maven
Добавьте репозиторий GroupDocs и зависимость watermark в ваш `pom.xml`:

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
Если вы предпочитаете не использовать Maven, можете скачать JAR напрямую с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Получение лицензии
Чтобы начать с бесплатной пробной версии или получить временную лицензию, посетите [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Для производственного использования приобретите подписку, чтобы разблокировать все функции.

## Настройка GroupDocs.Watermark для Java

Импортируйте основной класс, который управляет всеми операциями с водяными знаками:

```java
import com.groupdocs.watermark.Watermarker;
```

Этот импорт даёт доступ к классу `Watermarker`, который является точкой входа для добавления водяных знаков в любой поддерживаемый тип документа.

## Пошаговая реализация

Ниже процесс разбит на логические части: создание текстовых водяных знаков, создание графических водяных знаков и, наконец, их применение к изображениям внутри PDF.

### 1. Инициализация текстового водяного знака

**Зачем нужен текстовый водяной знак?** Он лёгок, индексируем, и идеально подходит для добавления уведомлений об авторском праве или конфиденциальности.

#### 1.1 Создание экземпляра TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Установка выравнивания
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Поворот водяного знака
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Настройка размеров
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Инициализация графического водяного знака

**Когда использовать графический водяной знак?** Идеально для брендирования логотипами или добавления сложных визуальных паттернов.

#### 2.1 Загрузка файла изображения
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Установка выравнивания
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Поворот графического водяного знака
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Настройка размеров
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Добавление водяных знаков к изображениям внутри PDF

Теперь соберём всё вместе: откроем PDF, найдём каждое изображение и применим либо текстовый, либо графический водяной знак в зависимости от размеров.

#### 3.1 Открытие PDF‑документа
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Получение всех изображений
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Условное применение водяных знаков
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

#### 3.4 Освобождение ресурсов изображения
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Сохранение изменённого PDF
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Очистка
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Практические применения водяных знаков PDF

| Сценарий использования | Как водяной знак помогает |
|------------------------|----------------------------|
| **Безопасность документов** | Помечает конфиденциальные файлы, препятствуя утечкам. |
| **Защита бренда** | Встраивает логотипы в маркетинговые PDF, усиливая идентичность бренда. |
| **Утверждение авторских прав** | Добавляет имя автора или символ © для подтверждения собственности. |
| **Контроль версий** | Отображает номер версии или дату непосредственно на странице. |

## Распространённые ошибки и рекомендации

- **Разделители путей:** Используйте двойные обратные слеши (`\\`) в Windows или прямые слеши (`/`) в Linux/macOS, чтобы избежать `FileNotFoundException`.  
- **Большие PDF:** Обрабатывайте изображения пакетами или увеличьте размер кучи JVM (`-Xmx2g`), чтобы предотвратить ошибки OutOfMemory.  
- **Ограничения лицензии:** Пробная версия может ограничивать количество обрабатываемых страниц; для неограниченного использования требуется обновление.  
- **Путаница с поворотом:** Помните, что `setRotateAngle` принимает градусы; отрицательные значения вращают против часовой стрелки.

## Часто задаваемые вопросы

**В: Можно ли добавить водяной знак в защищённые паролем PDF?**  
О: Да. Откройте документ с паролем, используя конструктор `Watermarker`, который принимает строку пароля.

**В: Поддерживает ли библиотека другие форматы, такие как DOCX или PPTX?**  
О: Абсолютно. GroupDocs.Watermark работает с Word, PowerPoint, Excel и графическими файлами.

**В: Как изменить непрозрачность водяного знака?**  
О: Вызовите `setOpacity(float opacity)` у объекта водяного знака (значение от 0.0 до 1.0).

**В: Можно ли добавить водяной знак только на первую страницу?**  
О: Получите коллекцию страниц через `watermarker.getPages()` и примените водяной знак к нужному индексу страницы.

**В: Что делать, если PDF хранится в облачном бакете?**  
О: Загрузите PDF в `InputStream` и передайте его конструктору `Watermarker`; после обработки запишите выходной поток обратно в облако.

## Заключение

Теперь у вас есть полностью готовый к производству метод **как добавить водяной знак в PDF** с помощью GroupDocs.Watermark для Java. Комбинируя текстовые и графические водяные знаки, вы получаете надёжную **безопасность PDF‑документов**, отвечающую требованиям брендинга и соответствия нормативам. Исследуйте другие возможности библиотеки — например, удаление водяных знаков или пакетную обработку, чтобы ещё больше расширить ваш документооборот.

---

**Последнее обновление:** 2026-01-23  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs  

---