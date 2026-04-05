---
date: '2026-02-13'
description: GroupDocs.Watermark for Java를 사용하여 도형을 추출하고 도형에서 이미지를 추출하는 방법을 배우며, 자세한
  다이어그램 정보를 효율적으로 가져옵니다.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Java에서 GroupDocs.Watermark를 사용하여 다이어그램에서 도형 추출하는 방법
type: docs
url: /ko/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# 다이어그램에서 도형을 추출하는 방법 (GroupDocs.Watermark 사용, Java)

Visio‑style 다이어그램에서 프로그래밍 방식으로 **도형을 추출하는 방법**이 필요할 때, GroupDocs.Watermark 라이브러리는 Java‑first 방식으로 모든 세부 정보—크기, 위치, 포함된 이미지, 그리고 각 도형 내부의 텍스트까지—를 손쉽게 가져올 수 있게 해줍니다. 이 튜토리얼에서는 정확히 **도형을 추출하는 방법**을 보여주고, 왜 중요한지, 그리고 프로젝트에 복사해 사용할 수 있는 단계별 코드를 제공합니다.

## 빠른 답변
- **도형 추출을 처리하는 라이브러리는 무엇인가요?** GroupDocs.Watermark for Java  
- **필요한 Java 버전은 무엇인가요?** JDK 8 or higher  
- **도형에서 이미지 데이터를 얻을 수 있나요?** Yes – use `shape.getImage()`  
- **도형 내부의 텍스트에 접근할 수 있나요?** Absolutely, via `shape.getText()`  
- **프로덕션에 라이선스가 필요합니까?** A valid GroupDocs.Watermark license is required  

## 소개

복잡한 다이어그램을 관리하려면 종종 도형 및 이미지와 같은 구성 요소에 대한 자세한 정보를 접근해야 합니다. Java를 사용해 다이어그램 도형과 연관된 크기, 위치, 텍스트 등을 프로그래밍 방식으로 가져와야 했던 경험이 있다면 이 튜토리얼이 도움이 될 것입니다. GroupDocs.Watermark 라이브러리의 강력한 기능을 활용하면 Java 애플리케이션에서 이 과정을 간소화할 수 있습니다. 이 가이드에서는 **도형을 추출하는 방법**을 단계별로 살펴보고, **도형에서 이미지 추출** 및 **도형에서 텍스트 추출** 방법도 함께 보여드립니다.

## “도형을 추출하는 방법”이란?

도형을 추출한다는 것은 다이어그램 내부 객체(페이지, 도형, 이미지, 텍스트)를 읽어들여 분석, 변환, 혹은 다른 애플리케이션에서 재사용할 수 있게 하는 것을 의미합니다—자동화, 보고, CAD 도구와의 통합에 최적입니다.

## 도형 추출에 GroupDocs.Watermark를 사용하는 이유

- **Full format support** – works with VSDX, VDX, and many other diagram types.  
- **Rich object model** – gives direct access to shape geometry, images, and text.  
- **No external dependencies** – pure Java, easy to embed in Maven projects.  

## 사전 요구 사항

- **GroupDocs.Watermark for Java** (version 24.11 or later)  
- Java Development Kit (JDK) 8 or higher  
- Maven for dependency management  
- IntelliJ IDEA 또는 Eclipse와 같은 IDE  

## GroupDocs.Watermark for Java 설정

Maven `pom.xml`에 라이브러리를 추가합니다:

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

또한 최신 바이너리는 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 다운로드할 수 있습니다.

### 라이선스 획득 단계
- **Free Trial:** Download a trial package to evaluate the API.  
- **Temporary License:** Request a temporary key for extended testing.  
- **Purchase:** Obtain a full license for production use.

### 기본 초기화 및 설정

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## 도형 추출 – 구현 가이드

### 로드 및 콘텐츠 가져오기

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### 도형 순회

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### 도형에서 이미지 추출 방법

`shape.getImage()` 호출은 원시 비트맵, 해당 크기 및 바이트 배열을 포함하는 객체를 반환합니다. 위에 표시된 속성을 사용해 이미지를 디스크에 저장하거나 다른 처리 파이프라인에 전달할 수 있습니다.

### 도형에서 텍스트 추출 방법

`shape.getText()` 메서드는 도형 내부의 순수 텍스트를 반환합니다. 도형에 텍스트가 없으면 메서드는 `null`을 반환합니다. 샘플 루프는 이미 텍스트를 출력하고 있으며, 이를 활용해 예를 들어 모든 도형 레이블의 인덱스를 구축하는 등 추가 조작이 가능합니다.

## 문제 해결 팁
- 파일 경로와 읽기 권한을 확인하십시오.  
- 지원되는 다이어그램 형식(VSDX, VDX 등)을 사용하고 있는지 확인하십시오.  
- 도형에 예상 데이터가 없을 경우, 형식별 특이 사항에 대한 라이브러리 릴리스 노트를 확인하십시오.

## 실용적인 적용 사례

1. **Diagram Analysis:** 자동으로 도형 크기나 누락된 레이블을 검사하여 다이어그램을 규정 준수 여부를 감사합니다.  
2. **Data Visualization:** 추출된 크기를 보고 대시보드에 전달해 레이아웃 밀도를 시각화합니다.  
3. **CAD Integration:** 도형 데이터를 CAD API와 결합해 설계 사양을 여러 도구 간에 동기화합니다.  

## 성능 고려 사항

- **Close resources:** Call `watermarker.close()` when you’re done to free native resources.  
- **Memory management:** Large diagrams can consume significant heap; monitor memory and increase `-Xmx` if needed.  
- **Batch processing:** Process files in batches and reuse a single `Watermarker` instance when possible.

## 결론

이 가이드를 따라 하면 GroupDocs.Watermark for Java를 사용해 **도형을 추출하는 방법**, **도형에서 이미지 추출**, **도형에서 텍스트 추출**을 모두 알게 됩니다. 이러한 기술은 자동화된 다이어그램 분석, 보고 및 기타 엔지니어링 시스템과의 통합을 가능하게 합니다. 다음 단계로 전체 API를 확인하려면 [documentation](https://docs.groupdocs.com/watermark/java/)을 살펴보고, 도형 추출을 맞춤 비즈니스 로직과 결합해 보세요.

## FAQ 섹션

1. **What is GroupDocs.Watermark?**  
   - A comprehensive Java library designed for watermarking and extracting information from various document formats, including diagrams.  

2. **Can I use this library to process all types of diagram files?**  
   - Yes, but ensure that the file format is supported by checking the [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **How do I extract shape dimensions and positions from a diagram using Java and GroupDocs.Watermark?**  
   - Load the diagram, access `DiagramContent`, then iterate shapes to get properties like width, height, X, and Y.  

4. **Can GroupDocs.Watermark extract images embedded in diagram shapes with Java?**  
   - Yes, it provides methods to access image data within shapes, including size and pixel data, useful for analysis or modification.  

5. **What are the prerequisites for extracting diagram shape info in Java?**  
   - Java JDK 8+, Maven setup, GroupDocs.Watermark library (24.11+), and basic Java knowledge are essential for implementation.  

---

**Last Updated:** 2026-02-13  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs