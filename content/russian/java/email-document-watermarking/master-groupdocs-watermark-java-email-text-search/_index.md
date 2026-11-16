---
date: '2025-12-31'
description: Узнайте, как искать текст в электронных письмах с помощью GroupDocs.Watermark
  для Java, эффективно управлять телами сообщений, темами и вложениями.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Как искать текст в электронных письмах с помощью GroupDocs.Watermark Java –
  Полное руководство
type: docs
url: /ru/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Как искать текст в электронных письмах с помощью GroupDocs.Watermark Java

Поиск конкретной фразы в теме, теле письма или вложениях может стать головной болью — особенно когда вы обрабатываете десятки или сотни сообщений. В этом руководстве вы узнаете, **как искать текст в электронных письмах** быстро и точно с помощью **GroupDocs.Watermark for Java**. Мы пройдем настройку, код и рекомендации по лучшим практикам, чтобы вы могли уверенно интегрировать поиск текста в письмах в свои приложения.

## Быстрые ответы
- **Какая библиотека позволяет искать текст в электронных письмах на Java?** GroupDocs.Watermark for Java.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для тестирования; для продакшн‑использования требуется платная лицензия.  
- **Можно ли искать и в теме, и в теле письма?** Да — настройте `EmailSearchableObjects`, включив Subject, HtmlBody и PlainTextBody.  
- **API чувствителен к регистру?** Можно выполнить поиск без учёта регистра, установив соответствующий флаг в `TextSearchCriteria`.  
- **Какая версия Java требуется?** JDK 8 или выше; рекомендуется использовать Maven для управления зависимостями.

## Что такое «поиск электронных писем» с помощью GroupDocs.Watermark?
GroupDocs.Watermark предоставляет единый API для поиска, удаления или изменения водяных знаков и обычного текста в различных типах документов, включая **сообщения электронной почты** (`.msg`, `.eml`). Используя модель searchable objects, вы можете точно выбирать нужные части письма, делая пакетную обработку быстрой и надёжной.

## Почему стоит использовать GroupDocs.Watermark Java для поиска в письмах?
- **Unified API** – Работает с PDF, изображениями, Office‑файлами и письмами, используя одинаковые шаблоны кода.  
- **Performance‑optimized** – Операции поиска выполняются в памяти без необходимости внешних сервисов.  
- **Robust handling** – Поддерживает HTML и обычный текст в теле, вложения и даже защищённые паролем письма.  
- **Easy integration** – Готов к использованию с Maven/Gradle, имеет понятную документацию и активную поддержку.

## Предварительные требования

- **Java Development Kit (JDK)** 8 или новее.  
- **Maven** (или Gradle) для управления зависимостями.  
- IDE, например **IntelliJ IDEA** или **Eclipse**.  
- Базовое знакомство с синтаксисом Java и форматами файлов электронной почты (`.msg`, `.eml`).

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
В качестве альтернативы вы можете скачать последнюю JAR‑файл с [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Приобретение лицензии
- **Free Trial:** Тестировать основные функции без лицензионного ключа.  
- **Temporary License:** Запросить ограниченный по времени ключ для расширенной оценки.  
- **Paid License:** Приобрести для неограниченного использования в продакшн.

#### Базовая инициализация
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Руководство по реализации

### Функция 1: Поиск текста в теле письма

#### Обзор
Мы настроим API для сканирования **темы**, **HTML‑тела** и **обычного текста** письма на наличие заданного ключевого слова.

#### Шаг 1: Определить пути к документам
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Шаг 2: Настроить параметры загрузки и Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Шаг 3: Создать критерии поиска
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Шаг 4: Указать места поиска
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Шаг 5: Выполнить поиск и очистить водяные знаки
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Шаг 6: Сохранить изменения
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Советы по устранению неполадок
- **Empty results:** Убедитесь, что ключевое слово действительно присутствует в выбранных частях письма.  
- **Performance:** Ограничьте searchable objects только теми, которые нужны (например, Subject + PlainTextBody), чтобы ускорить обработку больших пакетов.

### Функция 2: Параметры загрузки документа email

#### Обзор
`EmailLoadOptions` позволяет управлять способом разбора письма — полезно для зашифрованных сообщений или пользовательских кодировок.

#### Шаг 1: Настроить параметры загрузки
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Ключевые параметры конфигурации
- **Password Protection:** Установите `loadOptions.setPassword("yourPassword")` для зашифрованных файлов `.msg`.  
- **Encoding Settings:** Настройте `loadOptions.setEncoding(Charset.forName("UTF-8"))` при работе с нестандартными наборами символов.

## Практические применения

- **Automated Email Processing:** Пакетно сканировать входящие заявки в службу поддержки на наличие ключевых слов, таких как “refund” или “error”.  
- **Legal Compliance Checks:** Быстро находить конфиденциальные термины (например, SSN, номера кредитных карт) в корпоративных архивах почты.  
- **Customer Support Automation:** Перенаправлять письма на основе обнаруженных фраз в соответствующую команду поддержки.

## Соображения по производительности
- **Resource Management:** Вызовите `watermarker.close()` сразу после завершения обработки, чтобы освободить нативные ресурсы.  
- **Memory Best Practices:** При работе с тысячами сообщений обрабатывайте их пакетами и, где возможно, переиспользуйте экземпляр `Watermarker`.

## Заключение
Теперь у вас есть надёжный, готовый к продакшн подход для **поиска текста в электронных письмах** с использованием GroupDocs.Watermark Java. Гибкость API позволяет выбирать конкретные части письма, удалять нежелательные водяные знаки и интегрировать логику в более крупные рабочие процессы.

### Следующие шаги
- Поэкспериментировать с **множественными критериями поиска** (например, сочетание “invoice” + “overdue”).  
- Исследовать **добавление водяных знаков**, чтобы помечать письма, содержащие конфиденциальные данные.  
- Опробовать другие типы документов (PDF, DOCX) с тем же рабочим процессом Watermarker.

## Часто задаваемые вопросы

**Q1:** Как обрабатывать зашифрованные письма с помощью GroupDocs.Watermark?  
**A1:** Используйте `EmailLoadOptions.setPassword("yourPassword")` перед созданием экземпляра `Watermarker`.

**Q2:** Можно ли искать несколько ключевых слов одновременно?  
**A2:** Да — создайте отдельные объекты `SearchCriteria` для каждого ключевого слова и объедините их логическими операторами (например, `OrSearchCriteria`).

**Q3:** Бесплатно ли использовать GroupDocs.Watermark Java?  
**A3:** Доступна бесплатная пробная версия для оценки. Для продакшн‑использования требуется платная лицензия.

**Q4:** Как эффективно обрабатывать большие объёмы писем?  
**A4:** Ограничьте searchable objects только необходимыми, обрабатывайте письма пакетами и всегда закрывайте `Watermarker` для освобождения ресурсов.

**Q5:** Где можно найти дополнительную помощь или поддержку?  
**A5:** Посетите [форум GroupDocs](https://forum.groupdocs.com/c/watermark/10) для получения помощи от сообщества или свяжитесь напрямую со службой поддержки GroupDocs.

## Ресурсы
- **Documentation:** Ознакомьтесь с подробными руководствами на [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Получите технические детали на [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Последнее обновление:** 2025-12-31  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs  

---