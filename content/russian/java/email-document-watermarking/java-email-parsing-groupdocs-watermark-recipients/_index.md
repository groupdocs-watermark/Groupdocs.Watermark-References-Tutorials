---
date: '2026-01-03'
description: Узнайте, как вывести список получателей электронной почты на Java с помощью
  GroupDocs.Watermark – автоматизируйте извлечение полей To, CC и BCC из email‑документов.
keywords:
- Java email parsing
- GroupDocs.Watermark Java
- listing email recipients
title: Список получателей электронной почты Java с GroupDocs.Watermark
type: docs
url: /ru/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Список получателей электронной почты Java с GroupDocs.Watermark

Извлечение каждого адреса **To**, **CC** и **BCC** из файла электронной почты может быть утомительным, когда вы обрабатываете десятки или сотни сообщений. В этом руководстве вы узнаете, как быстро и надёжно **list email recipients java** с помощью библиотеки GroupDocs.Watermark для Java. Мы пройдём через настройку, разбор кода и реальные примеры использования, чтобы вы могли интегрировать эту возможность в свои приложения.

## Quick Answers
- **Что делает этот код?** Он открывает файл электронной почты и выводит все адреса To, CC и BCC.  
- **Какая библиотека требуется?** GroupDocs.Watermark для Java (версия 24.11).  
- **Можно ли читать файлы .msg и .eml?** Да — API поддерживает распространённые форматы электронной почты.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для тестирования; полная лицензия требуется для продакшн.  
- **Возможна ли пакетная обработка?** Конечно — можно перебрать несколько файлов, используя тот же шаблон.

## Introduction

Устали вручную просматривать данные электронной почты, чтобы извлечь списки получателей? Автоматизация этой задачи может сэкономить время и снизить количество ошибок, особенно при работе с большим объёмом писем. Это руководство покажет, как использовать мощную библиотеку GroupDocs.Watermark для Java, чтобы парсить документы электронной почты и **list email recipients java** эффективно.

**Что вы узнаете**
- Настройка среды для использования GroupDocs.Watermark для Java  
- Загрузка и инициализация документа электронной почты с помощью API GroupDocs.Watermark  
- Получение списков получателей To, CC и BCC из документов электронной почты  
- Практические применения и соображения по производительности  

Начнём с рассмотрения предварительных требований.

## Prerequisites

Прежде чем погрузиться в код, убедитесь, что ваша среда готова:

### Required Libraries, Versions, and Dependencies

Вам необходимо установить GroupDocs.Watermark для Java. В этом руководстве используется версия 24.11.

### Environment Setup Requirements

- **Java Development Kit (JDK):** Версия 8 или выше  
- **Integrated Development Environment (IDE):** Рекомендуются IntelliJ IDEA или Eclipse  
- **Dependency Management:** Maven или прямой способ загрузки  

### Knowledge Prerequisites

Базовое понимание программирования на Java и знакомство с обработкой форматов электронной почты (например, файлов .msg) будет полезным.

## Setting Up GroupDocs.Watermark for Java

Чтобы начать, вам нужно настроить проект с необходимыми зависимостями. Вот как это сделать:

**Maven Setup**

Add the following configuration in your `pom.xml` file to include GroupDocs.Watermark:

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

В качестве альтернативы скачайте последнюю версию с [выпусков GroupDocs.Watermark для Java](https://releases.groupdocs.com/watermark/java/).

### License Acquisition Steps

- **Free Trial:** Начните с бесплатной пробной версии, чтобы изучить функции.  
- **Temporary License:** Получите временную лицензию, если вам нужен расширенный доступ для тестирования.  
- **Purchase:** Рассмотрите возможность покупки лицензии для использования в продакшн.

После того как настройка готова, давайте инициализируем и подготовим среду для обработки документов электронной почты.

## How to List Email Recipients Java – Implementation Guide

В этом разделе каждая функция разбивается на управляемые шаги, чтобы вы могли эффективно реализовать разбор электронной почты с помощью GroupDocs.Watermark.

### Load and Initialize Email Document

**Overview**  
Загрузка документа электронной почты — первый шаг нашего пути. Этот процесс включает инициализацию объекта `Watermarker`, который служит шлюзом для взаимодействия с файлами электронной почты.

**Implementation Steps**

1. **Import Required Classes**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```
2. **Define Email File Path and Load Options**  
   Укажите путь к вашему документу электронной почты. Замените `"YOUR_DOCUMENT_DIRECTORY/email.msg"` фактическим путём.  
   ```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```
3. **Resource Management**  
   Всегда помните закрывать экземпляр `Watermarker` после использования, чтобы освободить системные ресурсы.  
   ```java
   watermarker.close();
   ```

### List All Direct Recipients of an Email

**Overview**  
Получение прямых (To) получателей просто, как только вы инициализировали документ электронной почты.

**Implementation Steps**

1. **Retrieve Email Content**  
   Убедитесь, что объект `watermarker` уже инициализирован, как показано в предыдущем разделе.  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```
2. **Iterate and List Recipients**  
   Пройдитесь по списку прямых получателей и выведите каждый адрес электронной почты.  
   ```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### List All CC Recipients of an Email

**Overview**  
Список получателей CC следует аналогичному процессу, позволяя получить дополнительные адреса, включённые в поле CC.

**Implementation Steps**

1. **Retrieve and Iterate**  
   Используйте объект `EmailContent`, полученный ранее:  
   ```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### List All BCC Recipients of an Email

**Overview**  
Несмотря на то, что получатели BCC не видны в заголовке письма, их всё равно можно получить с помощью GroupDocs.Watermark.

**Implementation Steps**

1. **Access and Display BCC Addresses**  
   ```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Practical Applications

Эти функции могут быть интегрированы в различные системы, такие как:

- **Системы управления электронной почтой:** Автоматизировать категоризацию и обработку писем на основе списков получателей.  
- **Инструменты анализа данных:** Извлекать данные о получателях для аналитики, чтобы выявлять модели коммуникаций внутри организации.  
- **Программное обеспечение безопасности:** Мониторить трафик электронной почты для обнаружения несанкционированного распространения или утечек.

## Performance Considerations

При работе с большим объёмом писем учитывайте следующие рекомендации:

- **Оптимизировать использование ресурсов:** Закрывать объект `Watermarker` сразу после использования.  
- **Управление памятью:** Следить за сборкой мусора в Java и использованием памяти при обработке нескольких файлов.  
- **Пакетная обработка:** Обрабатывать письма пакетами, чтобы снизить нагрузку на системные ресурсы.

## Frequently Asked Questions

**Q: Как обрабатывать ошибки при парсинге электронной почты?**  
A: Убедитесь, что пути к файлам правильные, файлы соответствуют ожидаемым форматам, и оберните код в блоки try‑catch для перехвата `IOException` или `GroupDocsException`.

**Q: Можно ли использовать эту библиотеку с другими форматами писем, например .eml?**  
A: Да, GroupDocs.Watermark поддерживает различные форматы электронной почты. См. документацию для параметров загрузки, специфичных для формата.

**Q: Какие типичные подводные камни при выводе получателей?**  
A: Неправильные пути к файлам, неподдерживаемые типы файлов или забывание закрыть экземпляр `Watermarker` могут привести к утечкам ресурсов.

**Q: Как улучшить производительность при парсинге большого количества писем?**  
A: Обрабатывайте файлы параллельно с помощью `ExecutorService` в Java, но контролируйте загрузку CPU и использование памяти, чтобы избежать перегрузки.

**Q: Где получить помощь, если возникнут проблемы?**  
A: Посетите [форум бесплатной поддержки GroupDocs](https://forum.groupdocs.com/c/watermark/10) для получения помощи от сообщества и официальной поддержки.

## Additional Resources

- **Документация:** [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **Справочник API:** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Скачать:** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  

## Conclusion

Теперь вы знаете, как эффективно **list email recipients java** с помощью GroupDocs.Watermark для Java. Этот мощный инструмент может упростить процессы управления электронной почтой и открыть новые возможности для анализа данных и автоматизации.

**Next Steps**

- Исследуйте дополнительные возможности в [GroupDocs.Watermark API](https://docs.groupdocs.com/watermark/java/).  
- Интегрируйте эти фрагменты кода в более крупные проекты или конвейеры пакетной обработки.  
- Экспериментируйте с различными конфигурациями, чтобы подобрать оптимальные настройки под ваши задачи.

---

**Последнее обновление:** 2026-01-03  
**Тестировано с:** GroupDocs.Watermark 24.11 for Java  
**Автор:** GroupDocs