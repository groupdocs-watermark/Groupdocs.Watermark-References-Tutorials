---
date: '2026-04-07'
description: GroupDocs.Watermark를 사용하여 Java에서 이메일 본문을 검색하는 방법을 배우고, 여러 키워드로 이메일을 검색하는
  방법과 이메일 워터마크를 제거하는 방법을 포함합니다.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'GroupDocs.Watermark를 사용한 Java 이메일 본문 검색: 종합 가이드'
type: docs
url: /ko/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark를 사용한 Java 이메일 본문 검색

빠르고 신뢰할 수 있게 **search email body java**를 검색해야 한다면, 올바른 곳에 오셨습니다. 이 튜토리얼에서는 GroupDocs.Watermark for Java가 이메일 제목, HTML 본문 및 일반 텍스트 본문 안의 특정 텍스트를 찾는 방법과 원하지 않는 워터마크를 제거하는 방법을 단계별로 안내합니다. 끝까지 읽으면 단일 또는 다중 키워드에 작동하고 필요에 따라 이메일 워터마크까지 제거할 수 있는 견고한 솔루션을 구현할 수 있게 됩니다.

## 빠른 답변
- **search email body java**가 무엇을 의미합니까? 이는 Java 코드( GroupDocs.Watermark와 함께)를 사용하여 이메일 내용 안의 텍스트를 찾는 것을 의미합니다.  
- **여러 키워드 이메일을 한 번에 검색할 수 있나요?** 예 – 별도의 `SearchCriteria` 객체를 생성하고 결합하면 됩니다.  
- **이메일 워터마크를 제거하는 방법은?** 검색 후 `PossibleWatermarkCollection.clear()` 메서드를 사용하십시오.  
- **라이선스가 필요합니까?** 테스트용으로는 무료 체험판을 사용할 수 있지만, 운영 환경에서는 영구 라이선스가 필요합니다.  
- **어떤 IDE가 가장 적합합니까?** IntelliJ IDEA와 Eclipse 모두 완전히 지원됩니다.

## 배우게 될 내용
- GroupDocs.Watermark for Java 설치 및 구성.  
- 제목 및 본문 전체에서 **search email body java**를 위한 검색 기준 설정.  
- 단일 실행에서 **search multiple keywords email**를 수행하는 기술.  
- 찾은 후 **how to remove email watermarks**의 정확한 단계.

## 왜 GroupDocs.Watermark로 Java 이메일 본문을 검색하나요?
GroupDocs.Watermark는 .msg 파일 파싱, 다양한 본문 형식 처리 및 워터마크 관리를 추상화하는 고수준 API를 제공합니다. 맞춤 파서를 직접 구축하는 것보다 시간을 절약하고 대량 이메일 배치에서도 일관된 결과를 보장합니다.

## 필수 조건
- Java Development Kit (JDK) 8 이상.  
- Maven(또는 JAR를 수동으로 추가할 수 있는 환경).  
- Java 및 이메일 파일 형식(.msg, .eml)에 대한 기본 지식.

## GroupDocs.Watermark for Java 설정
GroupDocs.Watermark for Java는 문서(이메일 포함) 내 워터마크 삽입 및 텍스트 검색을 간소화합니다. 아래는 프로젝트에 라이브러리를 추가하는 가장 일반적인 두 가지 방법입니다.

### Maven 설정
`pom.xml` 파일에 다음을 포함하여 GroupDocs.Watermark를 종속성으로 추가합니다:
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
또는 최신 버전을 직접 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 다운로드할 수 있습니다.

### 라이선스 획득 단계
- **Free Trial:** 기본 기능을 테스트하기 위해 무료 체험으로 시작하십시오.  
- **Temporary License:** 확장된 접근 및 테스트를 위해 임시 라이선스를 획득하십시오.  
- **Purchase:** GroupDocs.Watermark가 필요에 맞는 경우 구매를 고려하십시오.

#### 기본 초기화
아래와 같이 `Watermarker` 클래스를 초기화합니다:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## 구현 가이드

### 기능 1: 이메일 본문에서 텍스트 검색
이 기능은 이메일의 제목 및 본문에서 특정 텍스트를 검색할 수 있게 합니다.

#### 개요
Java 코드를 사용하여 이메일 메시지의 다양한 부분을 검색하도록 GroupDocs.Watermark를 구성하는 방법을 보여드리겠습니다.

##### Step 1: 문서 경로 정의
이메일 처리를 위한 입력 및 출력 경로를 설정합니다:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Step 2: 로드 옵션 및 Watermarker 설정
`EmailLoadOptions`와 `Watermarker`를 초기화하여 이메일 문서와 함께 작업합니다.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Step 3: 검색 기준 생성
텍스트 검색을 위한 기준을 정의합니다. 키워드 **"test"**에 대해 대소문자를 구분하지 않는 검색을 사용할 것입니다:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Step 4: 검색 위치 지정
검색이 이메일의 제목과 본문 모두를 포함하도록 구성합니다:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Step 5: 검색 실행 및 워터마크 제거
검색을 수행하고 발견된 워터마크를 제거합니다:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Step 6: 변경 사항 저장
처리 후 변경 사항을 새 문서에 저장합니다:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### 문제 해결 팁
- **Common Issue:** 검색 결과가 비어 있는 경우, 이메일 본문이나 제목에 텍스트가 존재하는지 확인하십시오.  
- **Performance Tip:** 실제로 필요한 섹션만 검색하도록 제한하여 최적화하십시오.

### 기능 2: 이메일 문서 로드 옵션
이 섹션에서는 GroupDocs.Watermark로 처리하기 위해 이메일 문서를 로드할 때 추가 옵션을 설정하는 방법을 설명합니다.

#### 개요
로드 옵션을 구성하면 문서 처리 방식을 보다 세밀하게 제어할 수 있으며, 비밀번호 보호나 인코딩 설정 등을 지정할 수 있습니다.

##### Step 1: 로드 옵션 구성
`EmailLoadOptions`에 대한 기본 설정은 다음과 같습니다:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### 핵심 구성 옵션
- **Password Protection:** 이메일이 암호화된 경우 비밀번호를 지정하십시오.  
- **Encoding Settings:** 필요에 따라 특정 인코딩 유형을 정의하십시오.

## 여러 키워드 이메일 검색 방법
한 번에 여러 용어를 찾으려면 여러 `SearchCriteria` 객체를 생성하고 논리 **OR** 또는 **AND** 연산자를 사용해 결합합니다. API를 통해 기준을 체인으로 연결할 수 있어 별도의 루프 없이 “invoice” **or** “receipt”를 검색할 수 있습니다.

## 이메일 워터마크 제거 방법
워터마크(또는 기준에 일치하는 텍스트)를 찾은 후, `PossibleWatermarkCollection.clear()` 메서드가 이메일 문서에서 이를 제거합니다. 이는 위의 **Step 5**에서 사용한 정확한 단계이며, 매치 수에 관계없이 작동합니다.

## 실용적인 적용 사례

### 사용 사례 1: 자동 이메일 처리
대량 이메일 데이터를 필터링하고 처리하여 특정 콘텐츠를 효율적으로 찾도록 자동화합니다.

### 사용 사례 2: 법적 컴플라이언스 검사
기업 이메일 내 민감 정보를 검색하여 컴플라이언스를 보장합니다.

### 사용 사례 3: 고객 지원 자동화
고객 문의에서 키워드나 구문을 빠르게 찾아 지원 워크플로를 간소화합니다.

## 성능 고려 사항
GroupDocs.Watermark를 사용할 때 성능을 최적화하기 위해 다음 사항을 고려하십시오:
- **Resource Management:** 대용량 이메일 데이터셋을 처리하기 위해 메모리와 처리 능력을 효율적으로 관리하십시오.  
- **Java Memory Management Best Practices:** 리소스 사용량을 정기적으로 모니터링하고 즉시 해제하십시오.

## 자주 묻는 질문

**Q:** GroupDocs.Watermark로 암호화된 이메일을 처리하려면 어떻게 해야 하나요?  
**A:** `Watermarker`를 초기화할 때 `EmailLoadOptions`를 사용하여 비밀번호를 지정하십시오.

**Q:** 여러 키워드를 한 번에 검색할 수 있나요?  
**A:** 예, 별도의 `SearchCriteria` 인스턴스를 생성하고 논리 연산을 사용해 결합하십시오.

**Q:** GroupDocs.Watermark Java는 무료로 사용할 수 있나요?  
**A:** 무료 체험판을 이용할 수 있으며, 확장된 기능을 위해 라이선스 구매를 고려하십시오.

**Q:** 대량 이메일을 효율적으로 처리하려면 어떻게 해야 하나요?  
**A:** 특정 이메일 섹션을 대상으로 검색을 최적화하고 리소스를 효과적으로 관리하십시오.

**Q:** 추가 도움이나 지원을 어디서 찾을 수 있나요?  
**A:** 커뮤니티 지원을 위해 [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10)을 방문하거나 무료 지원 채널에 연락하십시오.

## 리소스
- **Documentation:** [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/)에서 자세한 가이드를 확인하십시오.  
- **API Reference:** [GroupDocs API](https://apireference.groupdocs.com/watermark/java/)에서 기술 세부 정보를 확인하십시오.

---

**마지막 업데이트:** 2026-04-07  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs