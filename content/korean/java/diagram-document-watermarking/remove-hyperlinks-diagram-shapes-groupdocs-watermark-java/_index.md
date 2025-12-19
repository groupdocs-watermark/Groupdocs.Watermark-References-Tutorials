---
date: '2025-12-19'
description: GroupDocs.Watermark Java를 사용하여 다이어그램 도형에서 하이퍼링크를 제거하는 방법을 배우세요. 이는 Java
  문서 보안의 핵심 단계이며 하이퍼링크를 일괄 제거할 수 있습니다.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: GroupDocs.Watermark Java를 사용하여 다이어그램 도형에서 하이퍼링크 제거하는 방법
type: docs
url: /ko/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java를 사용하여 다이어그램 도형에서 하이퍼링크 제거하기

디지털 문서를 관리할 때는 종종 다이어그램을 편집하게 되며, 특히 보안이나 명확성을 위해 **하이퍼링크 제거**가 필요합니다. 이 튜토리얼에서는 GroupDocs.Watermark for Java를 사용하여 다이어그램 도형에서 **하이퍼링크를 제거하는 방법**을 배우게 되며, 파일을 깨끗하고 안전하며 전문적으로 유지할 수 있습니다.

## 빠른 답변
- **주요 목적은 무엇인가요?** 다이어그램 도형에서 원치 않는 하이퍼링크를 제거하여 문서 보안을 강화합니다.  
- **어떤 라이브러리를 사용하나요?** GroupDocs.Watermark for Java (버전 24.11 이상).  
- **라이선스가 필요합니까?** 테스트용으로는 트라이얼을 사용할 수 있지만, 프로덕션에서는 유효한 라이선스가 필요합니다.  
- **여러 파일을 한 번에 처리할 수 있나요?** 예 – 동일한 로직을 배치 루프에 넣어 사용할 수 있습니다.  
- **Java 8이면 충분한가요?** Java 8+을 지원하며, 최신 JDK 사용을 권장합니다.

## 다이어그램에서 “하이퍼링크 제거”가 의미하는 바는 무엇인가요?
하이퍼링크를 제거한다는 것은 다이어그램 파일(예: Visio *.vsdx) 내부의 도형에 연결된 URL 참조를 삭제하는 것을 의미합니다. 이 작업은 외부 사이트로의 실수 클릭을 방지하고, 규정 준수 또는 내부 보안 정책을 충족하는 데 도움이 됩니다.

## 이 작업에 GroupDocs.Watermark Java를 사용하는 이유
- **Robust format support** – 다양한 다이어그램 형식을 지원합니다.  
- **Fine‑grained API** – 개별 도형 및 해당 하이퍼링크 컬렉션을 대상으로 할 수 있습니다.  
- **Performance‑optimized** – 단일 파일 및 대량 처리 모두에 적합합니다.

## 사전 요구 사항
- **GroupDocs.Watermark** 라이브러리 버전 24.11 이상.  
- Maven 또는 직접 JAR 다운로드(아래 설정 단계 참고).  
- Java Development Kit (JDK 8 이상) 및 IntelliJ IDEA 또는 Eclipse와 같은 IDE.

## GroupDocs.Watermark for Java 설정하기
시작하려면 Maven을 사용하거나 JAR 파일을 다운로드하여 프로젝트에 라이브러리를 포함합니다.

### Maven 설정
다음 구성을 `pom.xml`에 추가하세요:

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
또는 최신 버전을 [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)에서 다운로드합니다.

#### 라이선스 획득 단계
- API를 평가하기 위해 무료 트라이얼로 시작합니다.  
- 프로덕션에서는 GroupDocs 포털에서 임시 또는 정식 라이선스를 획득합니다.

#### 기본 초기화 및 설정
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## 다이어그램 도형에서 하이퍼링크 제거 방법
다음은 다이어그램을 로드하고, 도형을 찾으며, 원치 않는 하이퍼링크를 제거하는 단계별 가이드입니다.

### 단계 1: 다이어그램 파일 로드
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*왜?* 파일을 로드하면 내부 구조에 프로그래밍 방식으로 접근할 수 있습니다.

### 단계 2: 도형 콘텐츠 접근
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*왜?* 하이퍼링크가 포함될 수 있는 특정 도형에 대한 참조가 필요합니다.

### 단계 3: 반복하면서 하이퍼링크 제거
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*왜?* 컬렉션에서 항목을 삭제할 때 역순으로 반복하면 인덱스 오류를 방지할 수 있습니다.

### 단계 4: 저장 및 닫기
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*왜?* 변경 사항을 저장하고 리소스를 해제하면 메모리 누수와 파일 잠금을 방지할 수 있습니다.

## 배치 하이퍼링크 제거 (고급 사용 사례)
여러 다이어그램을 한 번에 정리해야 할 경우, 위 로직을 파일 경로 목록을 순회하는 루프 안에 넣습니다. 동일한 API 호출을 사용하며, 각 반복마다 입력 및 출력 디렉터리를 변경하면 됩니다. 이 방법은 대규모 문서 저장소에서 **배치 하이퍼링크 제거** 요구사항에 부합합니다.

## 실용적인 적용 사례
다이어그램 도형에서 하이퍼링크를 제거하면 여러 실제 시나리오에서 유용합니다:

1. **Security Purposes** – 네트워크가 피싱이나 악성코드에 노출되는 것을 방지하기 위해 외부 링크를 차단합니다.  
2. **Compliance** – 공유 문서에서 외부 URL 사용을 금지하는 기업 정책을 준수합니다.  
3. **Clarity** – 하이퍼링크가 불필요하거나 방해가 되는 경우 더 깔끔한 프레젠테이션을 만들 수 있습니다.

## 성능 고려 사항
### 성능 최적화
- 위에서 보여준 역순 반복 패턴을 사용하여 루프 효율성을 유지합니다.  
- 작업이 끝나면 `Watermarker` 객체를 즉시 닫아 메모리를 해제합니다.

### 리소스 사용 가이드라인
- 대형 다이어그램을 처리할 때 CPU와 RAM 사용량을 모니터링합니다.  
- 대량 작업의 경우 파일을 한 번에 모두 로드하는 대신 스트리밍을 고려합니다.

### Java 메모리 관리 모범 사례
- 빈번한 루프 내에서 객체 생성을 피합니다.  
- 가능한 경우 try‑with‑resources를 사용하여 자동 정리를 수행합니다.

## 자주 묻는 질문
1. **여러 도형을 어떻게 처리하나요?**  
   모든 페이지와 해당 도형을 순회하면서 각 도형에 동일한 하이퍼링크 제거 로직을 적용합니다.  

2. **이 프로세스를 대량 다이어그램에 자동화할 수 있나요?**  
   예 – 코드를 배치 처리 루틴에 삽입하거나 문서 관리 시스템에 통합합니다.  

3. **특정 페이지에서만 하이퍼링크를 제거해야 하면 어떻게 하나요?**  
   원하는 페이지를 인덱스(`content.getPages().get_Item(pageIndex)`)로 접근하고 해당 페이지의 도형만 대상으로 합니다.  

4. **GroupDocs.Watermark를 프로덕션에서 사용하려면 라이선스가 필요합니까?**  
   트라이얼 기간 이후에는 유효한 상업용 라이선스가 필요합니다.  

5. **이 방법을 다른 다이어그램 형식에도 적용할 수 있나요?**  
   GroupDocs.Watermark는 다양한 다이어그램 유형을 지원하므로 공식 문서에서 호환성을 확인하십시오.

**추가 Q&A**

**Q:** *제거된 하이퍼링크를 기록할 수 있나요?*  
**A:** 예 – `removeAt(i)`를 호출하기 전에 `shape.getHyperlinks().get_Item(i).getAddress()`를 캡처하여 로그 파일에 기록합니다.

**Q:** *하이퍼링크를 제거하면 도형의 시각적 모양에 영향을 줍니까?*  
**A:** 아니요. 도형의 기하학적 형태는 그대로 유지되며, 링크 메타데이터만 제거됩니다.

**Q:** *제거 후에 스타일을 다시 적용해야 합니까?*  
**A:** 일반적으로 필요하지 않습니다. 하이퍼링크 제거는 채우기, 선, 텍스트 스타일을 변경하지 않습니다.

## 결론
이제 GroupDocs.Watermark for Java를 사용하여 다이어그램 도형에서 **하이퍼링크를 제거하는 방법**에 대한 완전하고 프로덕션 준비된 방법을 갖추었습니다. 위 단계들을 따르면 다이어그램을 보호하고, 정책을 준수하며, 문서를 깔끔하게 유지할 수 있습니다.

---

**마지막 업데이트:** 2025-12-19  
**테스트 환경:** GroupDocs.Watermark 24.11 for Java  
**작성자:** GroupDocs  

**리소스**  
- [문서](https://docs.groupdocs.com/watermark/java/)  
- [API 레퍼런스](https://reference.groupdocs.com/watermark/java)  
- [다운로드](https://releases.groupdocs.com/watermark/java/)  
- [GitHub 저장소](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [무료 지원 포럼](https://forum.groupdocs.com/c/watermark/10)  
- [임시 라이선스 획득](https://purchase.groupdocs.com/temporary-license/)