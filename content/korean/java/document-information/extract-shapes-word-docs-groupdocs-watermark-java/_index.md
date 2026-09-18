---
date: '2026-02-05'
description: GroupDocs.Watermark for Java를 사용하여 Word 문서에서 도형을 추출하는 방법을 배우고, Java에서
  Word 문서를 로드하고 도형 데이터를 조작하는 방법을 포함합니다.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: GroupDocs.Watermark Java를 사용하여 Word 문서에서 도형 추출하는 방법
type: docs
url: /ko/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Java에서 GroupDocs.Watermark를 사용하여 Word 문서에서 도형 추출하는 방법

이 튜토리얼에서는 GroupDocs.Watermark Java 라이브러리를 사용하여 Word 문서에서 **도형을 추출하는 방법**을 알아봅니다. 다이어그램을 분석하거나, 삽입된 이미지를 추출하거나, 보고서 생성을 자동화하려는 경우에도, 도형 메타데이터를 추출하면 보다 스마트한 문서 처리 파이프라인을 구축할 수 있습니다. 라이브러리 설정, Word 문서 로드, 상세 도형 정보 추출 과정을 단계별 Java 코드와 함께 안내합니다.

## 빠른 답변
- **“extract shapes”는 무엇을 의미하나요?** Word 파일의 각 그리기 객체에 대한 메타데이터(유형, 크기, 위치, 텍스트, 이미지)를 가져오는 것입니다.  
- **어떤 라이브러리가 이를 처리하나요?** GroupDocs.Watermark for Java.  
- **라이선스가 필요합니까?** 개발용으로는 체험판으로 충분하며, 정식 라이선스를 사용하면 사용 제한이 해제됩니다.  
- **도형에서 이미지도 가져올 수 있나요?** 예 – API가 그림 도형의 이미지 바이트를 제공합니다.  
- **필요한 Java 버전은?** JDK 8 이상.

## Word 문서에서 “도형 추출”이란 무엇인가요?
도형을 추출한다는 것은 프로그램적으로 모든 그리기 요소—그림, WordArt, 자동 도형, 차트, 그리고 머리글이나 바닥글에 삽입된 도형까지—에 접근하는 것을 의미합니다. 이 정보를 검증, 마이그레이션 또는 콘텐츠 기반 분석에 활용할 수 있습니다.

## Java용 GroupDocs.Watermark를 사용하는 이유
GroupDocs.Watermark는 기본 Office Open XML 형식의 복잡성을 추상화한 고수준·메모리 효율적인 API를 제공합니다. 이를 통해 다음을 수행할 수 있습니다:
- 문서를 빠르게 로드(`WordProcessingLoadOptions`).  
- 저수준 XML을 다루지 않고 섹션과 도형을 순회.  
- 이미지 데이터, 텍스트, 정렬 및 회전을 한 번에 가져오기.  
- 기존 Java 서비스나 마이크로서비스에 원활히 통합.

## 사전 요구 사항
- **Java Development Kit (JDK)** 8 이상.  
- **IDE** (IntelliJ IDEA 또는 Eclipse 등).  
- 기본 Java I/O 지식.  
- **GroupDocs.Watermark for Java** 라이선스 또는 체험판에 대한 접근 권한.

## Java용 GroupDocs.Watermark 설정
Maven 또는 직접 다운로드를 통해 라이브러리를 통합합니다.

### Maven 사용
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
또는 최신 JAR 파일을 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 다운로드합니다.

### 라이선스 획득
테스트용으로는 무료 체험판으로 충분합니다. 운영 환경에서는 모든 기능을 사용하려면 영구 라이선스를 요청하세요.

## 구현 가이드
구현을 두 단계로 나눕니다: **Word 문서 로드**와 **도형 정보 추출**.

### 단계 1: Word 문서 로드 (load word document java)
먼저 로드 옵션을 설정하고 `Watermarker` 인스턴스를 생성합니다. 이렇게 하면 문서를 추가 검사할 준비가 됩니다.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Pro tip:** `Watermarker` 인스턴스의 범위를 가능한 한 좁게 유지하세요; 즉시 닫으면 네이티브 리소스가 해제되고 메모리 누수를 방지할 수 있습니다.

### 단계 2: 도형 정보 추출 (extract images from shapes)
이제 모든 도형의 세부 정보를 가져옵니다(삽입된 이미지 포함). 코드는 각 섹션과 각 도형을 순회하며 유용한 메타데이터를 출력합니다.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**이 코드가 수행하는 작업:**  
- 각 도형의 **type**(예: picture, WordArt)을 가져옵니다.  
- **size**, **position**, **rotation** 값을 출력합니다.  
- 접근성 검증에 유용한 **alternative text**와 **name**을 표시합니다.  
- 도형에 이미지가 포함된 경우 이미지의 **pixel dimensions**와 **byte size**를 출력합니다—도형에서 이미지를 추출하는 데 적합합니다.

### 일반적인 함정 및 해결 방법
| 문제 | 원인 | 해결책 |
|------|------|--------|
| `FileNotFoundException` | 잘못된 파일 경로 또는 권한 부족 | 절대/상대 경로를 확인하고 파일이 읽기 가능한지 확인합니다. |
| Null `shape.getImage()` | 도형이 그림이 아님(예: 자동 도형) | `if (shape.getImage() != null)` 로 방어합니다. |
| High memory usage on large docs | 문서를 한 번에 전체 로드 | 섹션을 하나씩 처리하거나 JVM 힙을 늘립니다(`-Xmx`). |
| Missing header/footer shapes | `shape.getHeaderFooter()` 를 확인하지 않음 | 샘플은 도형이 머리글/바닥글에 속할 경우 이미 로그를 남깁니다. |

## 실용적인 적용 사례
1. **자동 보고서 생성** – 차트와 다이어그램을 추출하여 하위 PDF에 삽입합니다.  
2. **규정 준수 감사** – 모든 도형에 접근성을 위한 적절한 대체 텍스트가 포함되어 있는지 확인합니다.  
3. **콘텐츠 마이그레이션** – 레거시 Word 파일에 삽입된 이미지를 디지털 자산 관리 시스템으로 내보냅니다.

## 성능 고려 사항
- **리소스 해제**: `finally` 블록에서 항상 `watermarker.close()`를 호출하거나 API를 감싸는 경우 try‑with‑resources를 사용합니다.  
- **청크 처리**: 50 MB를 초과하는 문서는 메모리 사용량을 낮게 유지하기 위해 섹션별로 처리하는 것을 고려하세요.  
- **스레드 안전성**: `Watermarker` 인스턴스는 스레드 안전하지 않으므로 스레드당 새 인스턴스를 생성합니다.

## 결론
이제 GroupDocs.Watermark for Java를 사용하여 Word 문서에서 **도형을 추출하는 방법**을 알게 되었습니다. 파일 로드부터 각 도형의 메타데이터와 삽입된 이미지 데이터를 읽는 과정까지. 이 기능을 통해 고급 문서 분석, 자동화된 콘텐츠 파이프라인, 접근성 검증 등을 구현할 수 있습니다.

### 다음 단계
- 도형 속성(예: 크기 조정 또는 위치 변경) 수정 실험.  
- 이 방법을 **GroupDocs.Parser**와 결합하여 주변 텍스트를 추출.  
- 추출 로직을 REST 서비스에 통합하여 온디맨드 처리 구현.

## FAQ 섹션
**Q: GroupDocs.Watermark for Java란 무엇인가요?**  
A: 다양한 형식의 워터마크와 문서 콘텐츠를 관리하도록 설계된 포괄적인 라이브러리로, 도형 추출, 이미지 검색, 텍스트 조작과 같은 작업을 수행할 수 있습니다.

**Q: 라이선스 없이 도형에서 이미지를 추출할 수 있나요?**  
A: 체험판에서도 추출이 가능하지만, 정식 라이선스를 사용하면 사용 제한이 해제되고 상업적 배포가 가능합니다.

**Q: 이 방법이 `.doc` (바이너리) 파일에서도 작동하나요?**  
A: 예, API는 `.docx`와 레거시 `.doc` 형식을 모두 지원합니다.

**Q: 암호로 보호된 문서는 어떻게 처리하나요?**  
A: `Watermarker`를 생성하기 전에 `WordProcessingLoadOptions.setPassword("yourPassword")` 로 비밀번호를 지정합니다.

**Q: 추출한 도형 데이터를 JSON으로 내보낼 수 있나요?**  
A: 출력값을 POJO에 매핑하고 원하는 JSON 라이브러리(예: Jackson)를 사용해 컬렉션을 직렬화하면 됩니다.

---

**마지막 업데이트:** 2026-02-05  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs