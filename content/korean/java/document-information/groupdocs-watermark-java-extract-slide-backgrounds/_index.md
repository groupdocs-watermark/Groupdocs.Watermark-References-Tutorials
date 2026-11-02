---
date: '2026-09-11'
description: GroupDocs.Watermark for Java를 사용하여 슬라이드 배경 java를 추출하고 PowerPoint 슬라이드
  크기를 읽는 방법을 배웁니다. 몇 분 안에 이미지 크기, 파일 크기 및 메타데이터를 확인할 수 있습니다.
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: GroupDocs.Watermark for Java를 사용하여 슬라이드 배경 java를 추출하고 PowerPoint 슬라이드
  크기를 읽습니다. 설정, 코드 및 문제 해결을 포함한 자세한 가이드.
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: GroupDocs.Watermark를 사용한 슬라이드 배경 java 추출
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: 슬라이드 배경 java 추출 방법
type: docs
url: /ko/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# 슬라이드 배경을 추출하는 Java 방법

## 소개

슬라이드 배경 Java를 추출하는 것은 PowerPoint 파일 내부의 시각적 자산을 분석, 재사용 또는 문서화하려는 경우 흔히 필요한 작업입니다. GroupDocs.Watermark for Java를 사용하면 프레젠테이션을 PowerPoint에서 열지 않고도 이미지 차원, 파일 크기 및 기타 메타데이터를 프로그래밍 방식으로 가져올 수 있습니다. 이 튜토리얼은 환경 설정부터 배경 세부 정보를 추출하고 해석하는 전체 워크플로우를 단계별로 안내하므로 Java 기반 자동화 파이프라인에 이 기능을 통합할 수 있습니다.

### 빠른 답변
- **어떤 라이브러리가 슬라이드 배경 추출을 처리합니까?** GroupDocs.Watermark for Java.  
- **어떤 메서드가 이미지 차원을 반환합니까?** `getBackground().getImageInfo().getWidth()` 및 `getHeight()`.  
- **배경 이미지의 파일 크기를 얻을 수 있나요?** 예, `getBackground().getImageInfo().getSize()`를 통해 가능합니다.  
- **이 기능에 라이선스가 필요합니까?** 임시 또는 정식 라이선스를 적용하면 전체 기능을 사용할 수 있으며, 체험판 모드도 제한 사항과 함께 작동합니다.  
- **Maven을 지원합니까?** 물론입니다—`pom.xml`에 GroupDocs.Watermark 의존성을 추가하면 됩니다.

## 슬라이드 배경 추출 Java란 무엇인가요?
슬라이드 배경 Java는 Java 코드를 사용해 PowerPoint 프레젠테이션의 각 슬라이드에 설정된 시각적 배경을 프로그래밍 방식으로 읽는 과정을 의미합니다. 이 작업을 통해 이미지 너비, 높이, 파일 크기와 같은 메타데이터를 얻을 수 있어 브랜드 검증이나 자산 재사용과 같은 후속 처리에 활용할 수 있습니다.

## 이 작업에 GroupDocs.Watermark를 사용하는 이유
GroupDocs.Watermark는 **30개 이상의 입력 및 출력 형식**을 지원하고, **500슬라이드**까지 전체 파일을 메모리에 로드하지 않고 처리할 수 있으며, 슬라이드 배경에 접근하기 위한 전용 API를 제공합니다. 이러한 정량적인 기능은 엔터프라이즈 규모 자동화에 신뢰할 수 있는 선택이 됩니다.

## 전제 조건
- **Java 11+**이 개발 머신에 설치되어 있어야 합니다.  
- **Maven**을 사용한 의존성 관리.  
- **GroupDocs.Watermark 24.11**(또는 이후 버전) – 이 가이드에서 사용되는 `PresentationLoadOptions`와 `PresentationContent` 클래스를 포함합니다.  
- 전체 기능을 활성화하기 위한 **유효한 라이선스**(임시 또는 정식).

## Java용 GroupDocs.Watermark 설정

### Maven 구성
`pom.xml` 파일에 GroupDocs.Watermark 의존성을 추가합니다:

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
수동 설치를 선호한다면 공식 릴리스 페이지에서 최신 JAR 파일을 받으세요: [GroupDocs.Watermark for Java 릴리스](https://releases.groupdocs.com/watermark/java/).

### 라이선스 획득
임시 라이선스를 사용하면 API를 평가할 수 있고, 정식 라이선스를 적용하면 모든 체험판 제한이 해제됩니다. 라이선스 포털에서 라이선스를 받으세요: [GroupDocs 라이선스 페이지](https://purchase.groupdocs.com/temporary-license/).

#### 기본 초기화 및 설정
첫 번째 단계는 PowerPoint 파일을 가리키는 `Watermarker` 인스턴스를 생성하는 것입니다:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## 슬라이드 배경을 추출하는 Java 방법은?
이 프로세스는 Watermarker 인스턴스로 PowerPoint 파일을 로드하고 적절한 로드 옵션을 만든 뒤, 문서를 연 후 각 슬라이드의 콘텐츠에 접근하여 배경 이미지를 가져오고 차원 및 파일 크기와 같은 메타데이터를 추출하는 순서로 진행됩니다. 아래 단계는 정확한 순서를 설명하며, 코드 자리표시자는 기존 스니펫이 들어갈 위치를 나타냅니다.

### 단계 1: 로드 옵션 생성
`PresentationLoadOptions`는 비밀번호 처리 및 메모리 사용량과 같은 로드 환경 설정을 정의합니다.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### 단계 2: PowerPoint 문서 열기
앞서 만든 로드 옵션을 사용해 `.pptx` 파일 경로와 함께 `Watermarker`를 인스턴스화합니다.

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### 단계 3: 슬라이드 콘텐츠 접근
`PresentationContent`는 슬라이드 수준 객체(배경 이미지 포함)를 가져오는 진입점입니다.

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### 단계 4: 슬라이드를 반복하고 배경 세부 정보 읽기
Slide는 프레젠테이션 내 개별 슬라이드를 나타내며 시각 요소에 접근할 수 있습니다. 각 `Slide` 객체에 대해 `getBackground()`를 호출해 이미지를 얻은 뒤, 차원과 크기를 읽어냅니다.

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### 단계 5: Watermarker 닫기
네이티브 리소스를 해제하고 메모리 누수를 방지하려면 `Watermarker` 인스턴스를 반드시 닫아야 합니다.

```java
watermarker.close();
```

## GroupDocs.Watermark를 사용하여 PowerPoint 슬라이드 차원을 읽는 방법
API는 슬라이드 배경에 연결된 `ImageInfo` 객체를 통해 너비와 높이를 노출합니다. `getWidth()`와 `getHeight()`를 호출하면 픽셀 단위 값을 얻을 수 있으며, 이를 레이아웃 계산이나 브랜드 가이드라인 검증에 활용할 수 있습니다.

## 일반적인 문제 및 해결 방법
- **File not found** – 파일 경로가 절대 경로인지, 프로젝트 루트에 대해 올바르게 상대 경로인지 확인하세요.  
- **Unsupported format** – GroupDocs.Watermark는 PPTX, PPT, ODP를 지원합니다. 오래된 바이너리 PPT 파일은 먼저 변환이 필요할 수 있습니다.  
- **License not applied** – 다른 API를 사용하기 전에 `License.setLicense("path/to/license.file")` 호출을 반드시 수행하세요.

## 실용적인 적용 사례
1. **자동화된 브랜드 준수** – 슬라이드 배경을 스캔해 기업 색상 팔레트나 로고 크기와 일치하는지 확인합니다.  
2. **자산 인벤토리** – 문서 라이브러리 전체에 걸친 배경 이미지 카탈로그를 구축해 마케팅 자산에 재사용합니다.  
3. **콘텐츠 마이그레이션** – 배경을 추출해 디지털 자산 관리 시스템에 저장하고, 새로운 프레젠테이션에 프로그래밍 방식으로 재적용합니다.  
4. **성능 모니터링** – 이미지 크기 통계를 기록해 슬라이드 렌더링을 저해할 수 있는 비정상적으로 큰 자산을 감지합니다.

## 성능 고려 사항
- **Resource cleanup** – `Watermarker`를 즉시 닫으면 네이티브 메모리가 해제되어 대용량 덱을 처리할 때 중요합니다.  
- **Memory footprint** – 라이브러리는 슬라이드 데이터를 스트리밍하므로 전체 프레젠테이션을 로드하지 않고 슬라이드당 하나씩 처리하면 사용량을 더욱 줄일 수 있습니다.  
- **Batch processing tip** – 수십 개 파일을 처리할 때는 단일 `License` 인스턴스를 재사용하고 파일당 새로운 `Watermarker`를 생성해 JVM 힙을 안정적으로 유지합니다.

## 결론
이제 GroupDocs.Watermark를 사용해 슬라이드 배경 Java를 추출하는 완전하고 실무에 적용 가능한 가이드를 확보했습니다. 위 단계대로 진행하면 이미지 차원, 파일 크기 및 기타 메타데이터를 가져와 브랜드 검증, 자산 관리 또는 원하는 맞춤 워크플로에 활용할 수 있습니다.

**다음 단계**
- 다양한 `PresentationLoadOptions`(예: 비밀번호 보호 파일)를 실험해 보세요.  
- 배경을 자동으로 추가하거나 교체하는 워터마킹 API를 탐색하세요.  
- 이 추출 로직을 REST 서비스와 결합해 슬라이드 메타데이터 엔드포인트를 제공하세요.

## 자주 묻는 질문

**Q: 최소 Java 버전은 무엇인가요?**  
A: Java 11 이상이 필요합니다; 이전 버전은 라이브러리에서 요구하는 언어 기능을 지원하지 않습니다.

**Q: 비밀번호로 보호된 프레젠테이션에서 배경을 추출할 수 있나요?**  
A: 예—파일을 열기 전에 `PresentationLoadOptions`에 비밀번호를 설정하면 됩니다.

**Q: 체험판 모드가 처리 가능한 슬라이드 수를 제한하나요?**  
A: 체험판은 출력 파일에 워터마크를 삽입하지만 메타데이터 추출을 위한 슬라이드 수에는 제한을 두지 않습니다.

**Q: 추출한 배경 이미지를 디스크에 저장할 수 있나요?**  
A: 물론입니다—`ImageInfo` 객체를 얻은 뒤 `ImageInfo.save("output.png")`를 사용하면 됩니다.

**Q: 추출한 이미지를 어떤 형식으로 내보낼 수 있나요?**  
A: API는 PNG, JPEG, BMP, GIF 형식으로 배경 이미지 내보내기를 지원합니다.

## 리소스

- **Documentation:** [GroupDocs 문서](https://docs.groupdocs.com/watermark/java/)  
- **Documentation:** [GroupDocs Watermark 문서](https://docs.groupdocs.com/watermark/java/)  
- **API reference:** [GroupDocs Watermark API 레퍼런스](https://reference.groupdocs.com/watermark/java)  
- **Download:** [GroupDocs 다운로드](https://releases.groupdocs.com/watermark/java/)  
- **GitHub repository:** [GroupDocs GitHub 페이지](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Support forum:** [GroupDocs 지원 포럼](https://forum.groupdocs.com/c/watermark/10)

---

**마지막 업데이트:** 2026-09-11  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs

## 관련 튜토리얼

- [PowerPoint 슬라이드 차원을 GroupDocs.Watermark Java API로 가져오는 방법](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)  
- [Java에서 GroupDocs.Watermark 라이브러리로 PowerPoint 슬라이드 배경 제거](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)  
- [GroupDocs.Watermark for Java를 사용해 문서 정보를 가져오는 단계별 가이드](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)