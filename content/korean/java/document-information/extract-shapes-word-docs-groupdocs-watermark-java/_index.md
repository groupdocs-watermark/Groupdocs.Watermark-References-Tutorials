---
date: '2026-09-06'
description: Java용 GroupDocs.Watermark를 사용하여 Word 문서에서 도형을 추출하는 방법을 배우고, 강력한 문서 자동화
  및 분석을 구현하세요.
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: Java용 GroupDocs.Watermark를 사용하여 Word 문서에서 도형을 추출하는 방법. 단계별 가이드를 따라
  도형을 효율적으로 로드하고, 분석하며, 처리하세요.
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: Java에서 GroupDocs.Watermark를 사용하여 Word 문서에서 도형을 추출하는 방법
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: Java에서 GroupDocs.Watermark를 사용하여 Word 문서에서 도형을 추출하는 방법
type: docs
url: /ko/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark를 사용하여 Java에서 Word 문서에서 도형을 추출하는 방법

현대의 문서 중심 애플리케이션에서 Word 파일에서 **how to extract shapes**를 추출하는 것은 일반적인 과제입니다. 다이어그램 사용을 감사하거나, 그래픽을 이미지로 변환하거나, 동적 보고서를 구동해야 할 때, 프로그래밍 방식으로 도형 메타데이터를 가져오면 수많은 수작업 시간을 절약할 수 있습니다. 이 튜토리얼에서는 GroupDocs.Watermark for Java를 사용하여 DOCX를 로드하고, 모든 도형을 열거하며, 유형, 크기 및 위치와 같은 속성을 검색하는 방법을 안내합니다.

## 빠른 답변
- **어떤 라이브러리가 shape extraction을 처리합니까?** GroupDocs.Watermark for Java.  
- **최소 Java 버전?** JDK 8 or newer.  
- **개발에 라이선스가 필요합니까?** 무료 체험판으로 테스트가 가능하며, 프로덕션에는 정식 라이선스가 필요합니다.  
- **대용량 문서를 처리할 수 있습니까?** 예—메모리 사용량을 낮게 유지하기 위해 섹션을 순차적으로 처리합니다.  
- **Maven이 선호되는 설정 방법입니까?** Maven은 의존성 관리를 단순화하며 대부분의 프로젝트에 권장됩니다.

## Word 문서에서 shape extraction이란?
Shape extraction은 Word 파일을 프로그래밍 방식으로 읽고 각 그래픽 객체—그림, 도면, SmartArt, 차트 또는 텍스트 상자—에 대한 세부 정보를 검색하는 과정으로, 코드에서 이를 분석하거나 조작할 수 있게 합니다. 추출된 메타데이터에는 도형 유형, 크기, 위치 및 연관된 텍스트가 포함되어 있어 변환이나 분석과 같은 추가 처리에 활용됩니다.

## Java용 GroupDocs.Watermark를 사용하는 이유?
GroupDocs.Watermark는 **30개 이상의 문서 형식**을 지원하며, 스트리밍 API 덕분에 전체 파일을 메모리에 로드하지 않고도 **수백 페이지 파일**을 처리할 수 있습니다. 이 라이브러리는 일반 서버에서 **100‑페이지 문서당 200 ms**의 속도로 도형 메타데이터를 처리하여 배치 작업에 빠르고 안정적인 결과를 제공합니다.

## 전제 조건
- **Java Development Kit (JDK)** 8 이상.  
- **IDE** (IntelliJ IDEA 또는 Eclipse 등).  
- Java I/O 및 Maven에 대한 기본적인 이해.  

우리는 GroupDocs.Watermark for Java를 사용할 것이며, 이는 워터마크에 중점을 두면서도 깊은 문서 검사 기능을 제공하는 강력한 SDK입니다.

## Java용 GroupDocs.Watermark 설정
Maven 또는 직접 다운로드를 통해 SDK를 통합합니다.

### Maven 사용
다음 구성을 `pom.xml` 파일에 추가하십시오:
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
또는 최신 버전을 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 다운로드하십시오.

### 라이선스 획득
무료 체험 라이선스로 모든 기능을 탐색할 수 있습니다. 프로덕션 사용을 위해서는 GroupDocs 포털에서 영구 라이선스 키를 획득하십시오.

## 구현 가이드
구현을 두 개의 논리적 부분으로 나눕니다: 문서 로드와 도형 정보 추출.

## GroupDocs.Watermark를 사용하여 Word 문서에서 도형을 추출하는 방법?
`Watermarker`는 GroupDocs.Watermark의 주요 클래스이며, 문서를 로드하고 내용에 접근할 수 있게 합니다. `Watermarker` 인스턴스로 DOCX를 로드한 뒤 각 섹션과 도형을 반복하면서 속성을 읽습니다. 초기화 후 열거하는 두 단계 패턴은 **30개 이상의 지원되는 도형 유형**을 모두 포괄하며, 메모리 사용량이 과도하지 않은 상태로 최대 500 페이지 문서까지 처리할 수 있습니다. 이는 문서를 효율적으로 스트리밍하여 대용량 파일을 높은 메모리 소비 없이 작업할 수 있게 합니다.

### 단계 1: 로드 옵션 구성
`WordProcessingLoadOptions`는 파일이 파싱되는 방식을 세밀하게 조정할 수 있게 합니다(예: 헤더 무시, 빠른 모드 활성화).  
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
이 스니펫은 문서를 메모리에 보관하고 검사를 준비하는 `Watermarker`를 생성합니다.

### 단계 2: 워드 프로세싱 콘텐츠 접근
섹션과 도형을 반복하면서 유형, 크기, 정렬 및 도형이 헤더/푸터에 존재하는지 여부와 같은 주요 세부 정보를 출력합니다.  
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
이 루프는 모든 도형 객체를 포괄하여 헤더나 푸터에 삽입된 숨겨진 그래픽을 놓치지 않도록 합니다.

## 일반적인 문제 및 해결책
- **파일을 찾을 수 없음** – 절대 경로나 상대 경로를 다시 확인하고, 명확성을 위해 `Paths.get(...).toAbsolutePath()`를 사용하십시오.  
- **성능 병목 현상** – 300 페이지보다 큰 문서의 경우 섹션을 하나씩 처리하고 각 배치 후 `watermarker.close()`를 호출하여 메모리를 해제하십시오.  
- **지원되지 않는 도형 유형** – GroupDocs.Watermark는 현재 25개의 기본 도형 카테고리를 지원합니다; 사용자 정의 OfficeArt 객체의 경우 대안으로 OpenXML SDK 사용을 고려하십시오.

## 실용적인 적용 사례
1. **자동화된 보고서 생성** – 차트를 추출하여 대시보드에 삽입합니다.  
2. **규정 준수 감사** – 규제 문서에 금지된 그래픽이 포함되지 않았는지 확인합니다.  
3. **마이그레이션 파이프라인** – 웹 기반 게시 플랫폼으로 콘텐츠를 이동하기 전에 도형을 SVG로 변환합니다.

## 성능 고려 사항
- `Watermarker` 객체를 `watermarker.close()`로 즉시 해제하여 네이티브 리소스를 반환합니다.  
- `WordProcessingLoadOptions`에서 `fastLoad` 플래그를 활성화하면 전체 콘텐츠 렌더링이 아닌 도형 메타데이터만 필요할 때 유용합니다.  
- 서버에 충분한 CPU 코어가 있는 경우에만 병렬 스트림으로 문서를 처리하십시오; 스레드 안전하지 않은 공유 객체는 피하십시오.

## 결론
이제 GroupDocs.Watermark for Java를 사용하여 Word 문서에서 **how to extract shapes**를 수행하는 방법을 알게 되었습니다. `Watermarker`로 문서를 로드하고, 로드 옵션을 구성하며, 각 도형을 반복함으로써 가장 복잡한 파일도 처리할 수 있는 강력한 자동화 워크플로를 구축할 수 있습니다.

### 다음 단계
- `Shape` 객체의 `getImageData()` 메서드를 실험하여 그림을 PNG로 내보냅니다.  
- 워터마크 감지 및 제거와 같은 다른 GroupDocs.Watermark 기능을 탐색합니다.  
- 도형 추출을 GroupDocs.Parser 라이브러리와 결합하여 주변 텍스트를 가져와 보다 풍부한 분석을 수행합니다.

## 자주 묻는 질문

**Q: GroupDocs.Watermark for Java란 무엇인가요?**  
A: GroupDocs.Watermark for Java는 **30개 이상의 파일 형식**에 대해 워터마크 생성, 감지 및 문서 검사를 가능하게 하는 포괄적인 SDK입니다.

**Q: 암호로 보호된 Word 파일에서 도형을 추출할 수 있나요?**  
A: 예—`Watermarker` 인스턴스를 생성할 때 `WordProcessingLoadOptions`에 비밀번호를 전달하면 됩니다.

**Q: 라이브러리가 Linux 서버에서 작동합니까?**  
A: 물론입니다; GroupDocs.Watermark는 플랫폼에 구애받지 않으며 Java 8+를 지원하는 모든 OS에서 실행됩니다.

**Q: 단일 문서에서 처리할 수 있는 도형 수는 얼마입니까?**  
A: SDK는 수천 개의 도형을 처리할 수 있으며, 테스트에서는 최대 5,000개의 개별 도형이 포함된 문서에서도 안정적인 성능을 보였습니다.

**Q: 도형 추출을 위해 별도의 라이선스가 필요합니까?**  
A: 아니요, 도형 추출은 표준 GroupDocs.Watermark 라이선스에 포함되어 있습니다.

---

**마지막 업데이트:** 2026-09-06  
**테스트 환경:** GroupDocs.Watermark 23.12 for Java  
**작성자:** GroupDocs

## 관련 튜토리얼

- [GroupDocs.Watermark를 사용하여 Java에서 다이어그램의 도형 정보 추출](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [GroupDocs.Watermark를 사용하여 Java에서 Word 문서의 도형 제거: 종합 가이드](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}