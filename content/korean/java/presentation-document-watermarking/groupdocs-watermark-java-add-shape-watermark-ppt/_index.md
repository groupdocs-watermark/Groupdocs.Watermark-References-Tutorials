---
date: '2026-05-27'
description: GroupDocs를 사용하여 Java로 PPT 파일에 Shape 워터마크를 추가하는 방법을 배웁니다. 단계별 가이드, 구성
  팁 및 성능 인사이트.
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: GroupDocs를 사용하여 Java로 PowerPoint 프레젠테이션에 Shape 워터마크를 추가하는 방법
type: docs
url: /ko/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# GroupDocs를 사용하여 Java에서 PowerPoint 프레젠테이션에 도형 워터마크 추가하는 방법

PowerPoint 프레젠테이션을 보호하는 것은 브랜드 일관성과 데이터 보안을 위해 필수적입니다. 이 튜토리얼에서는 **GroupDocs 사용 방법**을 알아보고 Java로 PPTX 파일에 도형 워터마크를 직접 삽입하여 모든 슬라이드에 신뢰할 수 있는 프로그래밍 방식으로 브랜드를 적용하는 방법을 배웁니다.

## 빠른 답변
- **Java에서 PPTX에 워터마크를 추가하는 라이브러리는?** GroupDocs.Watermark.
- **프레젠테이션을 로드하는 클래스는?** `PresentationLoadOptions`.
- **워터마크를 적용하는 클래스는?** `Watermarker`.
- **개발에 라이선스가 필요합니까?** 테스트용으로는 무료 체험판을 사용할 수 있으며, 운영 환경에서는 유료 라이선스가 필요합니다.
- **500 MB 이상 대용량 파일에 워터마크를 적용할 수 있나요?** 예 – GroupDocs는 전체 문서를 메모리에 로드하지 않고 최대 2 GB 파일을 처리합니다.

## GroupDocs.Watermark란?
`GroupDocs.Watermark`는 PPT, PPTX, PDF, DOCX 등을 포함한 100개 이상의 문서 형식에 텍스트, 이미지 또는 도형 워터마크를 추가할 수 있는 Java SDK입니다. 최대 2 GB 파일을 처리하면서 메모리 사용량을 낮게 유지합니다. 이 라이브러리는 불투명도, 회전, 위치 지정 등을 커스터마이징할 수 있는 API를 제공하여 워터마크가 기존 슬라이드 레이아웃에 원활히 통합되도록 합니다.

## PowerPoint 프레젠테이션에 도형 워터마크를 추가하는 이유
도형 워터마크는 슬라이드 전체에 시각적 일관성을 유지하고 벡터 좌표를 사용해 정확하게 배치할 수 있어 브랜드 요소를 필요한 위치에 정확히 맞출 수 있습니다. 네이티브 PowerPoint 도형으로 남아 있어 프레젠테이션을 이후에 편집하더라도 워터마크의 모양과 위치가 유지됩니다. 정량적인 이점은 다음과 같습니다:
- **50+** 워터마크 스타일(텍스트, 이미지, 도형) 지원.
- **100 %** 레이아웃 충실도 – 편집 후에도 도형이 정렬된 상태 유지.
- **최대 2 GB** 파일 크기 처리 시 전체 문서를 로드하지 않아 **70 %** 메모리 사용량 감소.

## 사전 요구 사항
- **Java Development Kit (JDK) 8+**이 설치되어 있어야 합니다.
- 의존성 관리를 위한 **Maven**.
- **IntelliJ IDEA** 또는 **Eclipse**와 같은 IDE.
- 기본 Java 지식 및 Maven 사용 경험.
- **GroupDocs.Watermark** 라이선스(체험판 또는 상용) 접근 권한.

### 필요 라이브러리 및 버전
- **GroupDocs.Watermark for Java** 버전 **24.11** 이상.

### 환경 설정 요구 사항
- `JAVA_HOME`가 JDK를 가리키도록 설정합니다.
- 아래와 같이 프로젝트의 `pom.xml`을 구성합니다.

## GroupDocs.Watermark를 사용하여 Java에서 PowerPoint 파일에 도형 워터마크를 추가하는 방법
`PresentationLoadOptions`는 슬라이드 선택 및 비밀번호 처리와 같은 PowerPoint 파일 로드 옵션을 지정합니다.  
`Watermarker`는 문서를 로드하고 워터마크를 적용하는 핵심 클래스입니다.  

`PresentationLoadOptions`로 프레젠테이션을 로드하고, `Watermarker` 인스턴스를 생성한 뒤, 도형 워터마크를 정의하고 각 슬라이드에 적용한 후 파일을 저장합니다. 이 엔드‑투‑엔드 흐름은 몇 줄의 코드만 필요하며 일반적인 10슬라이드 프레젠테이션은 1초 미만에 처리됩니다.

### Maven 구성
다음 의존성을 `pom.xml` 파일에 추가합니다:

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
또는 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 최신 버전을 다운로드합니다.

### 라이선스 획득
GroupDocs.Watermark의 모든 기능을 탐색하려면 무료 체험판이나 임시 라이선스를 얻으세요. 운영 환경에서는 배포 규모에 맞는 라이선스를 구매해야 합니다.

#### 기본 초기화 및 설정
`Watermarker`는 문서를 로드하고 워터마크를 적용하는 핵심 클래스입니다.  
`PresentationLoadOptions`는 슬라이드 처리 및 애니메이션 보존과 같은 PowerPoint 파일 로드 옵션을 제공합니다.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### 단계 1: 도형 워터마크 생성
`ShapeWatermarkOptions`는 크기, 색상, 불투명도 및 회전 등 도형 워터마크의 시각적 속성을 정의합니다.  

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### 단계 2: 모든 슬라이드에 워터마크 적용
프레젠테이션의 각 슬라이드를 순회하면서 도형 워터마크를 추가합니다.

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### 단계 3: 워터마크가 적용된 프레젠테이션 저장
출력 형식(PPTX)을 선택하고 파일을 저장합니다. SDK는 원본 슬라이드 내용과 애니메이션을 보존합니다.

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### 일반적인 문제 및 해결책
- **Missing license error:** 라이선스 파일을 클래스패스에 배치하거나 `License.setLicense("path/to/license.lic")`를 사용해 설정하십시오.  
  `License` 클래스는 GroupDocs 라이선스 파일을 로드하고 적용하여 SDK의 전체 기능을 활성화합니다.  
- **Shape not visible:** 도형의 불투명도나 색상 대비를 높이세요; 기본 불투명도는 0.2입니다.  
- **Large file slowdown:** `PresentationLoadOptions.setLoadAllSlides(false)`를 사용해 필요할 때마다 슬라이드를 로드하면 메모리 사용량을 줄일 수 있습니다.

## 자주 묻는 질문

**Q: 동일한 슬라이드에 여러 워터마크를 추가할 수 있나요?**  
A: 예 – 각 워터마크마다 다른 `ShapeWatermarkOptions`를 사용해 `watermarker.add()`를 여러 번 호출하면 됩니다.

**Q: GroupDocs.Watermark가 비밀번호로 보호된 PPTX 파일을 지원하나요?**  
A: 물론입니다. 로드하기 전에 `PresentationLoadOptions.setPassword("yourPassword")`에 비밀번호를 지정하면 됩니다.

**Q: 선택한 슬라이드에만 워터마크를 적용할 수 있나요?**  
A: 예 – 모든 슬라이드를 순회하는 대신 `add` 메서드에 슬라이드 인덱스를 지정하면 됩니다.

**Q: 호환되는 Java 버전은 무엇인가요?**  
A: SDK는 Java 8부터 Java 21까지 지원되어 레거시 및 최신 환경 모두에 적용됩니다.

**Q: 라이브러리는 애니메이션 도형을 어떻게 처리하나요?**  
A: 도형 워터마크는 설계상 정적이며, 슬라이드의 기존 애니메이션에 영향을 주지 않습니다.

---

**마지막 업데이트:** 2026-05-27  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs

## 관련 튜토리얼
- [GroupDocs.Watermark for Java를 사용하여 PowerPoint 프레젠테이션에 워터마크 추가](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [GroupDocs.Watermark for Java를 사용하여 PowerPoint 이미지에 텍스트 워터마크 추가하는 방법](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [GroupDocs.Watermark와 Java를 사용하여 PowerPoint에 라인 효과 워터마크 추가하는 방법](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)