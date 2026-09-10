---
date: '2025-12-31'
description: GroupDocs.Watermark for Java를 사용하여 이메일 텍스트를 검색하고, 본문, 제목 및 첨부 파일을 효율적으로
  관리하는 방법을 배워보세요.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: GroupDocs.Watermark Java를 사용한 이메일 텍스트 검색 방법 – 종합 가이드
type: docs
url: /ko/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark Java로 이메일 텍스트 검색하는 방법

특정 구문을 이메일의 제목, 본문 또는 첨부 파일에서 찾아야 할 때, 특히 수십 개에서 수백 개의 메시지를 다룰 경우 머리가 아플 수 있습니다. 이 튜토리얼에서는 **GroupDocs.Watermark for Java**를 사용하여 **이메일 내용을 빠르고 정확하게 검색하는 방법**을 알아봅니다. 설정, 코드, 그리고 모범 사례 팁을 단계별로 안내하므로 자신만의 애플리케이션에 이메일 텍스트 검색을 자신 있게 통합할 수 있습니다.

## 빠른 답변
- **Java에서 이메일 텍스트를 검색할 수 있는 라이브러리는?** GroupDocs.Watermark for Java.  
- **라이선스가 필요한가요?** 테스트용 무료 체험이 가능하며, 프로덕션에서는 유료 라이선스가 필요합니다.  
- **제목과 본문 모두 검색할 수 있나요?** 예—`EmailSearchableObjects`에 Subject, HtmlBody, PlainTextBody를 포함하도록 설정하면 됩니다.  
- **API가 대소문자를 구분하나요?** `TextSearchCriteria`에 적절한 플래그를 설정하여 대소문자 구분 없이 검색할 수 있습니다.  
- **필요한 Java 버전은?** JDK 8 이상; 의존성 관리를 위해 Maven 사용을 권장합니다.

## GroupDocs.Watermark와 함께 “이메일 검색”이란?
GroupDocs.Watermark는 **이메일 메시지**(`.msg`, `.eml`)를 포함한 다양한 문서 유형에서 워터마크와 일반 텍스트를 찾고, 제거하고, 수정할 수 있는 통합 API를 제공합니다. 검색 가능한 객체 모델을 활용하면 이메일에서 필요한 부분만 정확히 대상으로 삼아 대량 처리를 빠르고 안정적으로 수행할 수 있습니다.

## 왜 GroupDocs.Watermark Java를 이메일 검색에 사용하나요?
- **통합 API** – PDF, 이미지, Office 파일, 이메일을 동일한 코드 패턴으로 처리합니다.  
- **성능 최적화** – 외부 서비스 없이 메모리 내에서 검색 작업을 수행합니다.  
- **견고한 처리** – HTML 및 일반 텍스트 본문, 첨부 파일, 심지어 비밀번호로 보호된 이메일도 지원합니다.  
- **쉬운 통합** – Maven/Gradle에 바로 적용 가능하고, 문서가 명확하며 지원이 활발합니다.

## 사전 요구 사항

- **Java Development Kit (JDK)** 8 이상.  
- **Maven**(또는 Gradle) – 의존성 관리용.  
- **IntelliJ IDEA** 또는 **Eclipse** 같은 IDE.  
- `.msg`, `.eml` 등 이메일 파일 형식에 대한 기본적인 이해와 Java 문법에 대한 기초 지식.

## GroupDocs.Watermark for Java 설정하기

### Maven 설정
`pom.xml`에 저장소와 의존성을 추가합니다:

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

### 직접 다운로드
또는 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 최신 JAR 파일을 다운로드할 수 있습니다.

### 라이선스 획득
- **무료 체험:** 라이선스 키 없이 핵심 기능을 테스트합니다.  
- **임시 라이선스:** 평가 기간을 연장하기 위한 시간 제한 키를 요청합니다.  
- **유료 라이선스:** 무제한 프로덕션 사용을 위해 구매합니다.

#### 기본 초기화
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 구현 가이드

### 기능 1: 이메일 본문에서 텍스트 검색

#### 개요
키워드가 포함된 **제목**, **HTML 본문**, **일반 텍스트 본문**을 스캔하도록 API를 구성합니다.

#### 1단계: 문서 경로 정의
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### 2단계: 로드 옵션 및 Watermarker 설정
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### 3단계: 검색 기준 생성
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### 4단계: 검색 위치 지정
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### 5단계: 검색 실행 및 워터마크 제거
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### 6단계: 변경 사항 저장
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 문제 해결 팁
- **결과가 비어 있음:** 선택한 이메일 부분에 키워드가 실제로 존재하는지 확인합니다.  
- **성능:** 필요한 객체(예: Subject + PlainTextBody)만 검색 대상으로 제한하여 대량 배치 처리 속도를 높입니다.

### 기능 2: 이메일 문서 로드 옵션

#### 개요
`EmailLoadOptions`를 사용하면 암호화된 메시지나 사용자 정의 인코딩을 처리할 때 이메일 파싱 방식을 제어할 수 있습니다.

#### 1단계: 로드 옵션 구성
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 주요 구성 옵션
- **비밀번호 보호:** 암호화된 `.msg` 파일에 대해 `loadOptions.setPassword("yourPassword")`를 설정합니다.  
- **인코딩 설정:** 비표준 문자 집합을 다룰 때 `loadOptions.setEncoding(Charset.forName("UTF-8"))`로 인코딩을 조정합니다.

## 실용적인 적용 사례

- **자동 이메일 처리:** “refund” 또는 “error”와 같은 키워드가 포함된 지원 티켓을 대량 스캔합니다.  
- **법적 준수 검사:** 기업 메일 아카이브 전체에서 SSN, 신용카드 번호 등 기밀 용어를 신속히 찾습니다.  
- **고객 지원 자동화:** 감지된 구문에 따라 이메일을 적절한 지원 팀으로 라우팅합니다.

## 성능 고려 사항
- **리소스 관리:** 처리가 끝나면 `watermarker.close()`를 호출해 네이티브 리소스를 즉시 해제합니다.  
- **메모리 모범 사례:** 수천 개의 메시지를 다룰 경우 배치 단위로 처리하고, 가능하면 `Watermarker` 인스턴스를 재사용합니다.

## 결론
이제 GroupDocs.Watermark Java를 사용해 **이메일 텍스트를 검색하는 방법**에 대한 견고하고 프로덕션 수준의 접근 방식을 갖추었습니다. API의 유연성을 활용해 이메일의 특정 부분을 목표로 하고, 원하지 않는 워터마크를 제거하며, 로직을 더 큰 워크플로에 통합할 수 있습니다.

### 다음 단계
- **다중 검색 기준**을 실험해 보세요(예: “invoice” + “overdue”).  
- 민감한 데이터가 포함된 이메일에 워터마크를 추가해 표시하는 방법을 탐색합니다.  
- 동일한 Watermarker 워크플로를 사용해 다른 문서 유형(PDF, DOCX)도 다뤄봅니다.

## 자주 묻는 질문

**Q1:** GroupDocs.Watermark로 암호화된 이메일을 어떻게 처리하나요?  
**A1:** `EmailLoadOptions.setPassword("yourPassword")`를 `Watermarker` 인스턴스를 만들기 전에 사용합니다.

**Q2:** 한 번에 여러 키워드를 검색할 수 있나요?  
**A2:** 예—각 키워드마다 별도의 `SearchCriteria` 객체를 만들고 `OrSearchCriteria`와 같은 논리 연산자로 결합합니다.

**Q3:** GroupDocs.Watermark Java는 무료인가요?  
**A3:** 평가용 무료 체험이 제공됩니다. 프로덕션 사용 시 유료 라이선스가 필요합니다.

**Q4:** 대량 이메일을 효율적으로 처리하려면 어떻게 해야 하나요?  
**A4:** 필요한 검색 객체만 제한하고, 배치 처리하며, 항상 `Watermarker`를 닫아 리소스를 해제합니다.

**Q5:** 추가 도움이나 지원을 어디서 받을 수 있나요?  
**A5:** 커뮤니티 지원을 위해 [GroupDocs 포럼](https://forum.groupdocs.com/c/watermark/10)을 방문하거나 직접 GroupDocs 지원팀에 문의하세요.

## 리소스
- **문서:** 자세한 가이드는 [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/)에서 확인하세요.  
- **API 레퍼런스:** 기술 세부 사항은 [GroupDocs API](https://apireference.groupdocs.com/watermark/java/)에서 확인할 수 있습니다.

---

**마지막 업데이트:** 2025-12-31  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs  

---