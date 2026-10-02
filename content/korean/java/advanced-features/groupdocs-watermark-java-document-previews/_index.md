---
date: '2026-09-26'
description: GroupDocs.Watermark를 사용하여 문서를 이미지로 변환하고 Java로 generate thumbnails하는 방법을
  배웁니다. Step-by-step guide는 setup, preview streams, 그리고 performance tips를 다룹니다.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: GroupDocs.Watermark를 사용하여 문서를 이미지로 변환하고 Java로 generate thumbnails하는
  방법을 배웁니다. This guide는 installation, stream handling, 그리고 performance optimisation을
  통해 fast preview creation을 안내합니다.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: GroupDocs.Watermark Java를 사용하여 문서를 이미지로 변환
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: GroupDocs.Watermark Java를 사용하여 문서를 이미지로 변환
type: docs
url: /ko/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# GroupDocs.Watermark Java를 사용한 문서 이미지 변환

다중 페이지 문서의 가벼운 이미지 미리보기를 생성하는 것은 포털, 콘텐츠 관리 시스템 및 클라우드 스토리지 서비스에서 일반적인 요구 사항입니다. **convert document to image**를 사용하면 전체 파일을 로드하는 오버헤드 없이 최종 사용자에게 빠른 시각적 힌트를 제공할 수 있습니다. GroupDocs.Watermark Java 라이브러리는 워터마크를 추가할 뿐만 아니라 단일 패스에서 모든 페이지에 대해 **java generate thumbnails**를 수행할 수 있는 고성능 미리보기 엔진을 제공합니다.

이 튜토리얼에서는 라이브러리를 설정하고, 사용자 정의 페이지 스트림을 생성하고, 리소스를 안전하게 해제하며, 최종적으로 소스 문서의 각 페이지에 대한 이미지 미리보기를 만드는 방법을 배웁니다. 설명은 Java와 객체 지향 개념에 익숙한 개발자를 위해 작성되었으며, 대량 파일 배치를 처리하기 위한 모범 사례 팁을 포함합니다.

## 빠른 답변
- **첫 번째 단계는 무엇인가요?** GroupDocs.Watermark Maven 의존성을 추가하고 소스 파일 경로로 `Watermarker`를 초기화합니다.  
- **미리보기 이미지는 어떻게 생성되나요?** 각 페이지에 대한 출력 스트림을 열기 위해 `ICreatePageStream`을 구현한 다음 적절한 옵션으로 `generatePreview()`를 호출합니다.  
- **라이선스가 필요합니까?** 트라이얼은 기본 시나리오에 작동하지만 정식 라이선스를 사용하면 워터마크가 제거되고 배치 처리 기능이 활성화됩니다.  
- **200페이지 이상의 PDF를 처리할 수 있나요?** 예 – 라이브러리는 페이지를 스트리밍하므로 500페이지 파일에서도 메모리 사용량이 낮게 유지됩니다.  
- **지원되는 이미지 포맷은 무엇인가요?** PNG, JPEG, BMP, TIFF를 기본적으로 사용할 수 있습니다.

## convert document to image란 무엇인가요?
**convert document to image**라는 문구는 소스 파일(PDF, DOCX, PPTX 등)의 각 페이지를 PNG 또는 JPEG와 같은 래스터 이미지로 렌더링하는 과정을 설명합니다. 이 변환은 썸네일 갤러리, 미리보기 창 및 모바일 친화적인 문서 뷰어에 유용합니다.

## 미리보기 생성에 GroupDocs.Watermark를 사용하는 이유
GroupDocs.Watermark는 **30개 이상의 입력 포맷**을 지원하며 전체 파일을 메모리에 로드하지 않고 **500 페이지**까지의 문서에 대한 미리보기를 생성할 수 있습니다. 내부적으로 페이지를 순차적으로 처리하여 대용량 PDF에서도 Java 힙 사용량을 50 MB 이하로 유지합니다. 또한 라이브러리는 내장 이미지 최적화를 제공하여 DPI, 색상 깊이 및 압축 수준을 지정할 수 있으며, 이를 통해 일반적인 래스터화보다 **70 % 정도 작게** 썸네일을 만들 수 있습니다.

## 사전 요구 사항

- **Java Development Kit (JDK) 11 또는 최신 버전** – 라이브러리는 Java 8+용으로 컴파일되었지만 JDK 11을 사용하면 장기 지원 및 향상된 성능을 얻을 수 있습니다.
- **Maven 3.6+** – 의존성 관리를 위해 필요합니다.
- **GroupDocs.Watermark for Java 버전 24.11** – 작성 시점의 최신 안정 릴리스입니다.
- **Java I/O 스트림에 대한 기본 지식** – 각 미리보기 페이지에 대해 `FileOutputStream` 객체를 생성하게 됩니다.
- **라이선스 키** (프로덕션에서는 선택 사항) – 트라이얼은 문서당 미리보기 크기를 5 MB로 제한합니다.

## GroupDocs.Watermark for Java 설정 방법

GroupDocs.Watermark를 설정하려면 먼저 Maven 저장소를 추가하고 프로젝트의 `pom.xml`에 라이브러리를 의존성으로 포함합니다. 이렇게 하면 Maven이 올바른 아티팩트를 다운로드하고 컴파일 및 런타임 시 클래스패스에 클래스를 사용할 수 있게 됩니다.

### Maven 의존성 추가
라이브러리는 Maven Central을 통해 배포됩니다. `<dependencies>` 블록 안에 다음 스니펫을 `pom.xml`에 추가하십시오:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Pro tip:** 버전 번호를 속성(`\<groupdocs.watermark.version\>24.11\</groupdocs.watermark.version\>`)에 보관하면 쉽게 업그레이드할 수 있습니다.

### 직접 다운로드 (대안)
수동 설치를 선호한다면 공식 릴리스 페이지에서 JAR를 다운로드할 수 있습니다: [GroupDocs.Watermark for Java 릴리스](https://releases.groupdocs.com/watermark/java/).

## 라이선스 획득 및 적용 방법

GroupDocs.Watermark에 라이선스를 적용하면 트라이얼 제한이 해제되고 기본 워터마크 오버레이가 비활성화됩니다. 라이선스 파일을 알려진 위치에 배치하고 API가 해당 파일을 가리키도록 하거나, 다른 호출보다 먼저 코드에 라이선스 경로를 직접 삽입합니다. 로드가 완료되면 이후 모든 작업이 전체 기능 모드로 실행됩니다.

가능한 방법:

- **무료 트라이얼 요청** – GroupDocs 포털에서 30일 라이선스 파일을 제공합니다.
- **임시 라이선스 생성** – 평가 환경을 위한 온라인 라이선스 생성기를 사용합니다.
- **상용 라이선스 구매** – 무제한 프로덕션 사용 및 우선 지원을 제공합니다.

라이선스 파일(`GroupDocs.Watermark.lic`)을 프로젝트 루트에 두거나 `Watermarker.setLicense("path/to/license.file")`를 사용해 프로그래밍 방식으로 경로를 지정하십시오.

## Watermarker 초기화 방법

`Watermarker`를 초기화하려면 소스 문서 경로를 제공하고, 필요에 따라 보호된 파일의 비밀번호를 포함합니다. 생성자는 형식을 검증하고 내부 파서를 준비하여 즉시 미리보기 또는 워터마크 메서드를 호출할 수 있게 합니다. 생성 후에는 필요에 따라 여러 작업에 재사용할 수 있도록 인스턴스 참조를 유지하십시오.

`Watermarker` 클래스는 문서를 로드하고 워터마크 삽입 및 미리보기 생성과 같은 작업을 노출하는 GroupDocs.Watermark의 핵심 객체입니다.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – 소스 파일에 대한 절대 또는 상대 경로.
- 생성자는 파일 형식을 검증하고 내부 파서를 준비합니다.

> **Definition anchor:** `Watermarker`는 GroupDocs.Watermark for Java에서 모든 문서 처리 작업의 진입점입니다.

## 미리보기 생성을 위한 페이지 스트림 만들기

`ICreatePageStream` 인터페이스를 구현하여 사용자 정의 페이지 스트림을 만들 수 있습니다. 라이브러리는 렌더링하는 각 페이지마다 이 인터페이스를 호출합니다. 구현에서는 일반적으로 `FileOutputStream`인 새 `OutputStream`을 생성하여 페이지 번호를 기반으로 고유한 파일 이름을 지정해야 합니다. 이 접근 방식은 각 페이지의 출력을 분리하고 데이터 겹침을 방지합니다.

**java generate thumbnails**를 수행하려면 렌더링된 이미지가 기록될 각 페이지에 대한 스트림을 제공해야 합니다. `ICreatePageStream` 인터페이스를 구현하면 라이브러리가 처리하는 모든 페이지에 대해 구현이 호출됩니다.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`**을 사용하면 파일 이름에 페이지 번호를 직접 삽입할 수 있어 배치 처리가 간편합니다.
- 메서드는 각 페이지에 대해 새 `OutputStream`을 반환하므로 이전 페이지가 이후 쓰기에 영향을 주지 않습니다.

> **Definition anchor:** `ICreatePageStream`은 각 미리보기 페이지에 대한 출력 스트림 생성 방식을 정의할 수 있는 콜백 인터페이스입니다.

## 미리보기 생성 후 페이지 스트림 해제 방법

페이지 이미지가 기록된 후 라이브러리는 `IReleasePageStream`을 호출하여 해당 출력 스트림을 닫고 정리할 수 있게 합니다. 이 콜백을 구현하면 파일 핸들을 안전하게 해제하고 버퍼를 플러시하며 추가 로깅을 수행할 수 있습니다. 적절한 정리는 디스크 기술자 누수를 방지하고 이후 페이지가 방해받지 않고 처리될 수 있도록 합니다.

적절한 리소스 정리는 파일‑핸들 누수를 방지하고 JVM이 디스크 기술자를 고갈시키는 것을 막습니다. 라이브러리가 페이지가 완료되었다고 신호를 보낼 때 `IReleasePageStream`을 구현하여 스트림을 닫으십시오.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Definition anchor:** `IReleasePageStream`은 페이지‑특정 출력 리소스를 해제하는 사용자 정의 로직을 정의할 수 있는 콜백 인터페이스입니다.

## 문서 미리보기 생성 (convert document to image)

`Watermarker` 인스턴스에서 `generatePreview()`를 호출하고, 해상도, 이미지 포맷 및 페이지 범위를 정의하는 `PreviewOptions` 객체를 제공하여 미리보기를 생성합니다. 메서드는 각 페이지를 순회하면서 스트림 생성기를 사용해 래스터 이미지를 기록하고 스트림을 해제합니다. 이 과정은 문서 페이지를 나타내는 이미지 파일 집합을 생성합니다.

`Watermarker`, `FeatureCreatePageStream`, `FeatureReleasePageStream`이 준비되면 미리보기 엔진을 호출할 수 있습니다. `generatePreview()` 메서드는 각 페이지를 순회하면서 스트림 생성기를 호출하고 이미지를 기록한 뒤 최종적으로 스트림을 해제합니다.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`**은 DPI를 제어합니다; 웹 썸네일에는 150 DPI가 좋은 균형입니다.
- **`ImageFormat`**은 PNG, JPEG, BMP, TIFF 중 선택할 수 있으며, 이는 다운스트림 요구 사항에 따라 결정됩니다.
- 메서드는 페이지를 순차적으로 처리하므로 수백 페이지 문서에서도 메모리 사용량이 낮게 유지됩니다.

> **Definition anchor:** `generatePreview()`는 제공된 스트림을 사용해 로드된 문서의 각 페이지를 이미지로 렌더링하는 API 호출입니다.

## convert document to image의 실용적인 적용 사례

이미지 미리보기를 생성하면 다양한 가능성이 열립니다:

1. **문서 브라우저** – PNG 썸네일 그리드를 표시하여 사용자가 대용량 PDF를 열지 않고도 스크롤할 수 있습니다.
2. **검색 결과 스니펫** – 검색 인덱스 항목에 미리보기 이미지를 첨부해 UI를 풍부하게 합니다.
3. **이메일 첨부 파일** – 이메일 본문에 첨부된 PDF의 작은 미리보기를 삽입합니다.
4. **모바일 앱** – 전체 PDF 대신 200 KB PNG 미리보기를 전송해 대역폭을 절감합니다.
5. **컴플라이언스 포털** – 계약서와 같은 법적 요구 워터마크가 적용된 버전을 이미지로 렌더링해 감사 추적을 제공합니다.

## java generate thumbnails 시 성능 고려 사항
대량 처리를 할 때 다음 최적화 팁을 기억하십시오:

- **스트림 버퍼링** – `FileOutputStream`을 `BufferedOutputStream`으로 감싸 디스크 I/O를 최소화합니다.
- **병렬 배치 실행** – Java의 `ForkJoinPool`을 사용해 여러 문서를 동시에 처리합니다; 각 작업은 스레드‑안전 문제를 피하기 위해 자체 `Watermarker` 인스턴스를 생성해야 합니다.
- **썸네일 DPI 제한** – 대부분 UI 시나리오에는 72–150 DPI가 충분합니다; 인쇄용 미리보드에는 높은 DPI를 사용하십시오.
- **라이선스 객체 재사용** – JVM당 한 번 라이선스 파일을 로드하면 오버헤드가 감소합니다.
- **메모리 모니터링** – 라이브러리는 현재 페이지만 메모리에 유지합니다. 매우 큰 파일의 경우 가끔 발생하는 스파이크를 대비해 JVM 힙을 약간 늘리는 것을 고려하십시오(예: `-Xmx512m`).

## 일반적인 함정 및 회피 방법

| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| `OutOfMemoryError` 발생 중 미리보기 생성 | 1000‑페이지 PDF에서 300 DPI의 `ImageFormat.Jpeg` 사용 | DPI를 낮추거나 색상 깊이가 낮은 PNG로 전환 |
| 미리보기 파일이 비어 있음 | `FeatureCreatePageStream`이 모든 페이지에 대해 동일한 `FileOutputStream` 반환 | `pageNumber`마다 새로운 스트림이 생성되도록 보장 |
| 미리보기 이미지가 회전됨 | 원본 PDF에 회전 메타데이터가 포함되어 있으나 적용되지 않음 | `previewOptions.setRotatePages(true)` 호출 (가능한 경우) |
| 라이선스 경고 표시 | 라이선스 파일을 찾을 수 없거나 경로가 잘못됨 | `Watermarker.setLicense("path/to/license.file")`가 다른 API 호출보다 먼저 실행되는지 확인 |

## 자주 묻는 질문

**Q: 암호로 보호된 PDF에 대한 미리보기를 생성할 수 있나요?**  
A: 예. 비밀번호를 `Watermarker` 생성자에 전달하면 됩니다: `new Watermarker("file.pdf", "password")`.

**Q: 미리보기 출력에 지원되는 이미지 포맷은 무엇인가요?**  
A: PNG, JPEG, BMP, TIFF를 사용할 수 있습니다. 손실 없는 썸네일에는 PNG를 권장합니다.

**Q: 한 번의 호출로 처리할 수 있는 페이지 수는 얼마인가요?**  
A: 라이브러리는 하드 제한을 두지 않으며, 저장 공간과 I/O 처리량만 허용한다면 수천 페이지 문서도 미리볼 수 있습니다.

**Q: 각 서버 인스턴스마다 별도의 라이선스가 필요합니까?**  
A: 단일 라이선스 파일을 여러 인스턴스에서 재사용할 수 있으며, 총 사용량이 라이선스 조건을 준수하는 한 문제 없습니다.

**Q: 단일 결합 썸네일(예: 첫 페이지만) 생성 방법이 있나요?**  
A: 예. `previewOptions.setPages(new int[]{1})`을 설정하면 첫 페이지만 생성하도록 제한할 수 있습니다.

## 결론

이제 GroupDocs.Watermark를 사용해 **convert document to image**와 **java generate thumbnails**를 위한 완전하고 프로덕션 수준의 워크플로우를 갖추었습니다. 사용자 정의 페이지‑스트림 핸들러를 구성하면 메모리 사용량을 낮게 유지하고, `PreviewOptions`를 조정해 이미지 품질과 파일 크기를 제어할 수 있습니다. 이러한 기술을 통해 웹 포털, 데스크톱 클라이언트 또는 클라우드‑네이티브 마이크로서비스 등 어떤 Java 기반 애플리케이션에도 빠르고 고품질의 미리보기를 삽입할 수 있습니다.

---

**마지막 업데이트:** 2026-09-26  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## 관련 튜토리얼

- [GroupDocs.Watermark for Java를 사용한 문서 정보 검색: 단계별 가이드](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [GroupDocs.Watermark Java 고급 워터마크 기능 튜토리얼](/watermark/java/advanced-features/)
- [GroupDocs.Watermark를 사용한 Java 이미지 워터마크 추가: 단계별 가이드](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)