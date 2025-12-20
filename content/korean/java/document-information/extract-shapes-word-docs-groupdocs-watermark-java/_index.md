---
date: '2025-12-20'
description: Java용 GroupDocs.Watermark를 사용하여 워드 문서에서 이미지를 추출하고 도형을 추출하는 방법을 배우세요.
  문서 자동화 및 조작에 최적입니다.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Java에서 GroupDocs.Watermark를 사용하여 Word 문서에서 이미지 추출하는 방법
type: docs
url: /ko/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark를 사용하여 Java에서 Word 문서에서 이미지 추출하기

현대 문서 처리 애플리케이션에서 **Word 문서에서 이미지 추출**은 그래픽 재사용, OCR 수행, 혹은 콘텐츠 감사를 위해 자주 요구됩니다. 이 튜토리얼에서는 Java와 GroupDocs.Watermark를 사용해 Word 문서를 로드하고 **Word 파일에서 이미지 추출**하는 방법을 단계별로 보여주며, **도형 추출 방법**도 함께 설명합니다. 끝까지 따라오시면 자동화 파이프라인에 바로 적용할 수 있는 재사용 가능한 코드 스니펫을 얻을 수 있습니다.

## 빠른 답변
- **이미지 추출을 담당하는 라이브러리는?** GroupDocs.Watermark for Java  
- **그림과 벡터 도형을 모두 추출할 수 있나요?** 예 – API가 이미지와 도형 메타데이터에 대한 접근을 제공합니다.  
- **필요한 Java 버전은?** JDK 8 이상.  
- **프로덕션에 라이선스가 필요합니까?** 상용 라이선스를 권장하지만, 평가용 무료 트라이얼도 사용할 수 있습니다.  
- **대용량 파일에 메모리 효율적인가요?** 예, 리소스를 즉시 해제하고 섹션별로 점진적으로 처리할 수 있습니다.

## “Word에서 이미지 추출”이란?
Word에서 이미지를 추출한다는 것은 `.docx` 파일 내부에 포함된 모든 사진, 그림, 임베디드 그래픽을 프로그래밍적으로 찾아 그 바이너리 데이터 또는 메타데이터를 가져오는 것을 의미합니다. 이를 통해 이미지 분석, 콘텐츠 마이그레이션, 동적 보고서 생성 등 다양한 후속 작업을 수행할 수 있습니다.

## 이 작업에 GroupDocs.Watermark를 사용하는 이유
GroupDocs.Watermark는 OpenXML 포맷의 복잡성을 추상화한 고수준 API를 제공합니다. 몇 줄의 코드만으로 **Java에서 Word 문서 로드**가 가능하며, 상세한 도형 정보도 제공하므로 이미지 추출과 도형 분석을 모두 필요로 하는 개발자에게 최적입니다.

## 사전 준비 사항
- **Java Development Kit (JDK)** 8 이상  
- **IDE** – IntelliJ IDEA, Eclipse 또는 기타 Java 호환 편집기  
- 기본 Java I/O 지식  
- GroupDocs.Watermark 라이선스 접근 권한 (테스트용 트라이얼 가능)

## Java용 GroupDocs.Watermark 설정
Maven 또는 직접 다운로드 방식으로 라이브러리를 통합합니다.

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
또는 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 최신 JAR 파일을 다운로드합니다.

### 라이선스 획득
전체 기능을 사용하려면 GroupDocs 포털에서 라이선스 키를 받아야 합니다. 제한 없이 모든 기능을 체험하려면 임시 트라이얼 라이선스를 요청할 수 있습니다.

## 구현 가이드
구현을 두 개의 논리적 파트로 나눕니다:

1. **Java에서 Word 문서를 로드하는 방법**  
2. **도형 및 이미지 추출 방법 (즉, Word에서 이미지 추출)**

### Word 문서 로드
먼저 로드 옵션을 설정하고 `Watermarker` 인스턴스를 생성합니다.

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

> **Pro tip:** `"YOUR_DOCUMENT_DIRECTORY/document.docx"`를 처리하려는 파일의 절대 경로나 상대 경로로 교체하세요.

### 도형 및 이미지 정보 추출
문서가 로드되었으니 이제 각 섹션과 각 도형을 순회하면서 벡터 도형 데이터와 임베디드 이미지 세부 정보를 모두 가져올 수 있습니다.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

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

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
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

> **왜 중요한가:** `shape.getImage()` 호출을 통해 각 사진의 바이너리 표현에 직접 접근할 수 있어, 디스크에 저장하거나 네트워크 전송, 혹은 이미지‑처리 라이브러리로 전달하는 것이 가능합니다.

## 일반적인 문제와 해결책
| 문제 | 해결책 |
|---------|----------|
| **FileNotFoundException** – 경로 오류 | 파일 경로를 확인하고 애플리케이션에 읽기 권한이 있는지 확인합니다. |
| **OutOfMemoryError** – 대용량 문서 | 섹션을 하나씩 처리하고 배치를 마친 즉시 `watermarker.close()`를 호출합니다. |
| 도형에서 `getImage()`가 `null` 반환 | 모든 도형이 이미지가 아니라는 뜻이며, 이미지에 접근하기 전에 `shape.getShapeType()`을 확인하세요. |
| 라이선스 적용 안 됨 | `Watermarker` 생성 전에 `License.setLicense("path/to/license/file.lic");`를 추가합니다. |

## 실용적인 활용 사례
- **자동 보고서 생성:** 템플릿에서 차트와 로고를 추출해 대시보드에 재사용.  
- **콘텐츠 감사:** 기업 문서에서 금지된 그래픽을 스캔.  
- **마이그레이션 프로젝트:** 새 CMS로 이전하기 전에 임베디드 이미지를 내보냄.

## 성능 고려 사항
- `Watermarker` 인스턴스를 즉시 해제(`watermarker.close()`)합니다.  
- 50 MB 이상의 대용량 파일은 전체 문서를 메모리에 로드하기보다 섹션을 스트리밍 방식으로 처리하는 것이 좋습니다.  
- 최신 GroupDocs.Watermark 버전을 사용하면 성능 향상을 기대할 수 있습니다.

## 결론
이제 GroupDocs.Watermark for Java를 활용해 **Word 문서에서 이미지 추출**과 도형 메타데이터 조회를 수행하는 완전한 프로덕션‑레디 방식을 갖추었습니다. 이 기능을 통해 동적 보고서 생성부터 대규모 문서 감사까지 강력한 자동화 시나리오를 구현할 수 있습니다.

### 다음 단계
- 추출한 이미지를 디스크에 저장해 보세요 (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- 워터마크 제거·추가와 같은 추가 API를 탐색합니다.  
- 기존 문서‑관리 워크플로에 이 로직을 통합합니다.

## FAQ 섹션
**Q: GroupDocs.Watermark for Java란?**  
A: 다양한 문서 형식에서 워터마크 관리와 시각 요소 추출을 지원하는 종합 라이브러리로, 문서 조작 자동화를 강화합니다.

**Q: 비밀번호로 보호된 Word 파일에서도 이미지를 추출할 수 있나요?**  
A: 예. 비밀번호를 포함한 `WordProcessingLoadOptions`로 문서를 로드한 뒤 동일한 추출 로직을 적용하면 됩니다.

**Q: API가 .doc (바이너리) 파일도 지원하나요?**  
A: 라이브러리는 주로 OpenXML `.docx` 형식을 목표로 하지만, 변환 후 레거시 `.doc` 파일도 열 수 있습니다.

**Q: 추출한 이미지를 파일 시스템에 저장하려면 어떻게 하나요?**  
A: 루프 안에서 `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());`를 사용하면 됩니다.

**Q: 처리할 수 있는 도형 수에 제한이 있나요?**  
A: 하드 제한은 없지만 문서 크기에 따라 메모리 사용량이 증가하므로, 매우 큰 파일은 섹션별로 순차 처리하는 것이 좋습니다.

---

**마지막 업데이트:** 2025-12-20  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs