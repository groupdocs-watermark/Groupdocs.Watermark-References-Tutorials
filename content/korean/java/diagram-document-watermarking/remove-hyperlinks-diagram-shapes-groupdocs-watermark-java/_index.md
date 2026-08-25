---
date: '2026-08-25'
description: GroupDocs.Watermark for Java를 사용하여 다이어그램 파일을 편집하고 하이퍼링크를 제거하는 방법을 배웁니다.
  단계별 안내로 다이어그램을 빠르게 보호하세요.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: GroupDocs.Watermark for Java를 사용하여 다이어그램 파일을 편집하고 하이퍼링크를 제거하는 방법을
  배웁니다. 명확한 단계에 따라 문서를 보호하세요.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Java를 사용하여 다이어그램을 편집하고 하이퍼링크를 제거하는 방법
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Java를 사용하여 다이어그램을 편집하고 하이퍼링크를 제거하는 방법
type: docs
url: /ko/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Java로 다이어그램을 편집하고 하이퍼링크 제거하기  

디지털 문서를 관리할 때는 종종 다이어그램을 편집하게 되며, 특히 보안이나 시각적 명확성을 위해 하이퍼링크를 제거해야 할 때 **edit diagram** 파일을 편집해야 합니다. 이 튜토리얼에서는 강력한 **GroupDocs.Watermark** Java 라이브러리를 사용하여 다이어그램 파일을 편집하고 다이어그램 도형에서 원하지 않는 하이퍼링크를 제거하는 방법을 정확히 보여줍니다. 이 가이드를 끝까지 따라하면 배포 준비가 된 깨끗하고 링크가 없는 다이어그램을 얻을 수 있습니다.  

## 빠른 답변  
- **주요 목표는 무엇입니까?** 다이어그램 도형에서 모든 하이퍼링크를 제거하여 보안 및 프레젠테이션을 향상시킵니다.  
- **필요한 라이브러리는 무엇입니까?** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **라이선스가 필요합니까?** 테스트용으로는 무료 체험판을 사용할 수 있지만, 프로덕션에서는 상업용 라이선스가 필요합니다.  
- **여러 파일을 한 번에 처리할 수 있습니까?** 예 – 동일한 코드를 루프 안에 넣어 배치를 처리할 수 있습니다.  
- **지원되는 Java 버전은 무엇입니까?** Java 8 or higher (Java 11 recommended).  

## “how to edit diagram”이란 무엇입니까?  
**How to edit diagram**은 프로그램적으로 다이어그램 파일을 열고, 내부 요소(예: 도형, 텍스트 또는 하이퍼링크)를 수정한 뒤 결과를 저장하는 과정을 의미합니다. GroupDocs.Watermark를 사용하면 원본 작성 도구 없이도 다이어그램 파일을 편집할 수 있습니다.  

## Java용 GroupDocs.Watermark를 사용하는 이유는 무엇입니까?  
GroupDocs.Watermark는 **30+ diagram and image formats**(VSDX, SVG, WMF 포함)를 지원하며 전체 문서를 메모리에 로드하지 않고 **500 MB**까지 파일을 처리할 수 있어 많은 경쟁사에 비해 **20 % faster** 처리 속도를 제공합니다.  

## 전제 조건  
- **GroupDocs.Watermark** 라이브러리 버전 24.11 이상.  
- Maven이 설치되어 있음(또는 수동 설정을 선호한다면 JAR 파일).  
- Java Development Kit 8 이상 및 IntelliJ IDEA 또는 Eclipse와 같은 IDE.  

### 필요한 라이브러리, 버전 및 종속성  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (Maven 방식을 사용하는 경우)  

### 환경 설정 요구 사항  
JDK `bin` 디렉터리가 `PATH`에 포함되어 있고 IDE가 올바른 JDK 버전을 가리키는지 확인하십시오.  

### 지식 전제 조건  
기본 Java 구문, Maven 종속성 관리 및 파일 I/O 작업에 익숙해야 합니다.  

## Java용 GroupDocs.Watermark를 설정하는 방법은?  
`Watermarker` 클래스는 문서를 로드하고 수정하기 위한 API 진입점을 제공합니다.  

To begin using GroupDocs.Watermark, add its Maven coordinates to your project’s `pom.xml`. This pulls the library and its dependencies, allowing you to instantiate the Watermarker class and work with diagram files directly from Java code. You can then configure licensing and set output options before processing any document.  

`pom.xml`에 GroupDocs.Watermark 종속성을 추가하십시오.  

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

Maven을 사용하지 않으려면 공식 릴리스 페이지에서 최신 JAR를 다운로드하십시오.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### 라이선스 획득 단계  
- API를 평가하기 위해 무료 체험판으로 시작하십시오.  
- 프로덕션에서는 공급업체 포털에서 임시 또는 영구 라이선스를 획득하십시오.  

#### 기본 초기화 및 설정  
`Watermarker` 클래스는 모든 문서 처리 작업의 진입점입니다.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## GroupDocs.Watermark로 다이어그램을 편집하고 하이퍼링크를 제거하는 방법은?  
`Watermarker` 클래스는 문서를 로드하고 수정하기 위한 API 진입점을 제공합니다.  

먼저, 다이어그램 파일을 Watermarker 인스턴스로 로드합니다. 그런 다음 도형 컬렉션을 가져와 하이퍼링크 객체를 포함하는 도형을 식별하고, 컬렉션 인덱싱에 영향을 주지 않도록 역순으로 반복하면서 각 링크를 안전하게 삭제합니다. 이렇게 하면 다이어그램의 시각적 무결성을 유지하면서 모든 내장 URL이 제거됩니다.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **왜 이 단계가 중요한가**: 파일을 로드하면 모든 도형 및 해당 속성에 프로그래밍 방식으로 접근할 수 있습니다.  

## 다이어그램에서 도형 콘텐츠에 접근하는 방법은?  
`DiagramShape` 객체는 다이어그램 내 개별 도형을 나타내며, 해당 속성과 연결된 메타데이터를 노출합니다.  

다이어그램을 로드한 후 Watermarker에서 `getShapes()`를 호출하여 `DiagramShape` 객체 목록을 얻습니다. 각 도형은 하이퍼링크 컬렉션을 검사할 수 있어 링크를 정확히 제거하거나 수정할 수 있습니다. 추가 조정이 필요하면 도형 텍스트, 색상 및 기하 정보를 읽을 수도 있습니다.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **왜 이 단계가 중요한가**: 정확한 도형을 대상으로 하면 다른 시각 요소에 영향을 주지 않고 원하지 않는 링크만 제거할 수 있습니다.  

## 하이퍼링크를 안전하게 반복하고 제거하는 방법은?  
`removeHyperlink(int index)` 메서드는 도형의 하이퍼링크 컬렉션에서 지정된 위치에 있는 하이퍼링크를 삭제합니다.  

하이퍼링크 목록을 마지막 인덱스부터 0까지 역순으로 반복합니다. 이 역방향 루프는 항목이 제거될 때 발생하는 인덱스 이동을 방지하여 모든 하이퍼링크가 건너뛰지 않고 처리되도록 합니다. 제거 후에는 도형의 상태를 새로 고치거나 다이어그램의 다음 도형으로 계속 진행할 수 있습니다.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **왜 이 단계가 중요한가**: 역방향 루프를 사용하면 모든 하이퍼링크가 누락 없이 제거됩니다.  

## 편집된 다이어그램을 저장하고 리소스를 해제하는 방법은?  
`save(String path)` 메서드는 수정된 문서를 지정된 파일 위치에 기록하여 모든 변경을 완료합니다.  

모든 하이퍼링크를 제거한 후 Watermarker 인스턴스에서 `save` 메서드를 호출하여 원본을 덮어쓰지 않도록 새 파일명을 지정합니다. 그런 다음 `close()`를 호출해 파일 핸들을 해제하고 메모리를 확보합니다. 이는 장시간 실행되는 배치 프로세스에 필수적이며 파일이 올바르게 닫혀 이후 사용 준비가 되도록 합니다.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **왜 이 단계가 중요한가**: 리소스를 적절히 닫으면 메모리 누수와 서버의 파일 잠금 문제를 방지할 수 있습니다.  

## 실용적인 적용 사례  
다이어그램 도형에서 하이퍼링크를 제거하면 여러 실제 시나리오에서 유용할 수 있습니다.  

1. **Security** – 악성 사이트로 연결될 수 있는 외부 링크를 방지합니다.  
2. **Compliance** – 공유 자산에 삽입된 URL을 금지하는 기업 정책을 충족합니다.  
3. **Clarity** – 링크가 방해가 되는 경우 더 깔끔한 프레젠테이션을 제공합니다.  

이 로직을 더 큰 자동화 파이프라인에 삽입할 수 있습니다. 예를 들어, 인트라넷에 게시되기 전에 모든 다이어그램을 정리하는 야간 배치 작업 등이 있습니다.  

## 성능 고려 사항  

### 성능 최적화  
- 파일당 단일 `Watermarker` 인스턴스를 사용하여 오버헤드를 줄입니다.  
- 비용이 많이 드는 리스트 재인덱싱을 피하기 위해 역방향 반복을 선호합니다.  

### 리소스 사용 지침  
- 200 MB보다 큰 다이어그램의 경우 힙 사용량을 모니터링하고 JVM `-Xmx` 플래그를 늘리는 것을 고려하십시오.  
- VisualVM과 같은 프로파일링 도구는 대규모 배치 실행에서 병목 현상을 식별하는 데 도움이 됩니다.  

### Java 메모리 관리 모범 사례  
- 가능한 가장 작은 범위 내에서 객체를 선언합니다.  
- 스트림을 사용할 때는 try‑with‑resources를 사용하여 자동으로 닫히도록 합니다.  

## 자주 묻는 질문  

**Q: 수천 개의 도형을 포함하는 다이어그램을 어떻게 처리합니까?**  
A: 다이어그램을 페이지별로 처리하고 다음 페이지로 이동하기 전에 각 페이지의 리소스를 해제하여 메모리 사용량을 낮게 유지합니다.  

**Q: 하이퍼링크 제거를 특정 페이지에만 제한할 수 있습니까?**  
A: 예 – 원하는 페이지 인덱스를 가져온 다음 해당 페이지의 도형에만 제거 루프를 적용합니다.  

**Q: 배치 처리를 위해 상업용 라이선스가 필수입니까?**  
A: 프로덕션 수준 배포에는 유효한 라이선스가 필요합니다; 무료 체험판은 30일 및 5문서로 제한됩니다.  

**Q: GroupDocs.Watermark가 SVG 다이어그램을 지원합니까?**  
A: 물론입니다 – SVG는 30개 이상의 지원 형식 중 하나이며 동일한 API 호출로 하이퍼링크를 제거할 수 있습니다.  

**Q: 도형에 여러 개의 하이퍼링크가 있는 경우는 어떻게 합니까?**  
A: 역방향 반복 루프가 각 하이퍼링크 항목을 개별적으로 제거하여 모든 링크가 삭제되도록 합니다.  

## 리소스  
- [문서](https://docs.groupdocs.com/watermark/java/)  
- [API 레퍼런스](https://reference.groupdocs.com/watermark/java)  
- [다운로드](https://releases.groupdocs.com/watermark/java/)  
- [GitHub 저장소](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [무료 지원 포럼](https://forum.groupdocs.com/c/watermark/10)  
- [임시 라이선스 획득](https://purchase.groupdocs.com/temporary-license/)  

---  

**마지막 업데이트:** 2026-08-25  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs  

## 관련 튜토리얼

- [GroupDocs.Watermark Java용 다이어그램 워터마크 튜토리얼](/watermark/java/diagram-document-watermarking/)  
- [GroupDocs.Watermark를 사용한 Java 다이어그램 머리글 및 바닥글 편집: 종합 가이드](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [GroupDocs.Watermark for Java를 사용한 다이어그램에서 도형 효율적으로 제거](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)