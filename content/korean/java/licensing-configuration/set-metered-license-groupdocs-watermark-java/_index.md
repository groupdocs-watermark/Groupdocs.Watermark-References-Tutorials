---
date: '2026-01-21'
description: Java에서 GroupDocs Watermark 라이선스를 설정하는 방법을 배우고, 워터마크 PDF 적용 및 미터링 라이선스로
  사용량을 관리하는 방법을 포함합니다.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Java에서 GroupDocs Watermark (Metered) 라이선스 설정 방법
type: docs
url: /ko/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# GroupDocs Watermark (Metered) 라이선스 설정 방법 (Java)

지적 재산 보호는 현대 비즈니스의 최우선 과제이며, 워터마크는 이를 입증된 방식으로 구현합니다. 이 튜토리얼에서는 **GroupDocs.Watermark**에 메터드 방식으로 **라이선스를 설정하는 방법**을 배우고, **PDF 파일에 워터마크를 적용**하면서 사용량을 완벽히 제어하는 방법을 확인합니다. 전제 조건부터 실제 사용 시나리오까지 모두 안내하고, 라이선스 활성화를 위해 **공개/비공개 키를 사용하는 위치**를 정확히 보여드립니다.

## 빠른 답변
- **메터드 라이선스란?** API 호출마다 사용량을 추적하는 사용량 기반 라이선스 모델입니다.  
- **라이선스 파일이 필요합니까?** 아니요 – 공개 키와 비공개 키로 활성화합니다.  
- **필요한 Java 버전은?** Java 8 이상.  
- **PDF 문서에 워터마크를 추가할 수 있나요?** 예, API는 PDF, DOCX, PPTX 및 이미지 형식을 지원합니다.  
- **이 방법은 안전한가요?** 예, 키는 HTTPS를 통해 전송되며 평문으로 저장되지 않습니다.

## 메터드 라이선스란 무엇이며 왜 사용하나요?
메터드 라이선스는 실제 사용량에 따라 비용을 지불하도록 해 SaaS 또는 마이크로서비스 아키텍처에 최적화됩니다. 전통적인 라이선스 파일을 관리할 필요 없이 **문서 보안 워터마크** 기능을 제공하며, 사용량을 즉시 확대·축소할 수 있습니다.

## 전제 조건
시작하기 전에 다음을 준비하세요:

1. **GroupDocs.Watermark for Java** ≥ 24.11 (최신 릴리스).  
2. **JDK 8+** 설치 및 `JAVA_HOME` 설정.  
3. **공개 및 비공개 키** – GroupDocs 계정에서 발급받은 키를 코드에 사용할 예정입니다.

## GroupDocs.Watermark for Java 설정

### 설치 정보
Maven 프로젝트에 GroupDocs.Watermark를 통합합니다:

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

> **팁:** 아래 직접 다운로드 옵션에서도 동일한 저장소 URL을 사용합니다.

#### 직접 다운로드
공식 릴리스 페이지에서 최신 JAR 파일을 받으세요: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### 라이선스 획득
프리미엄 기능을 사용하려면 임시 또는 체험 라이선스가 필요합니다. [GroupDocs 웹사이트](https://purchase.groupdocs.com/temporary-license/)에 가입하고 제공되는 공개/비공개 키를 복사하세요.

### 기본 초기화
라이브러리를 클래스패스에 추가한 뒤 다음과 같이 초기화합니다:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **왜 중요한가:** 메터드 라이선스를 사용하더라도 `License` 객체를 초기화하면 이후 워크플로에서 키 기반 활성화를 받을 준비가 됩니다.

## 구현 가이드

### 메터드 라이선스 설정

#### 단계 1: 공개 및 비공개 키 정의
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
이 키들은 **공개/비공개 키**를 사용해 계정을 안전하게 식별합니다.

#### 단계 2: Metered 클래스 인스턴스 생성
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
`Metered` 클래스가 내부에서 모든 사용량 추적을 담당합니다.

#### 단계 3: 제공된 키로 메터드 라이선스 설정
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
이 호출 이후 SDK는 완전히 라이선스가 적용되며 **PDF 파일에 워터마크를 추가**하거나 **워터마크가 적용된 문서를 생성**할 수 있습니다.

### 라이선스 파일 대신 공개/비공개 키를 사용하는 이유
- **보안:** 키가 평문으로 디스크에 저장되지 않습니다.  
- **유연성:** 환경(개발, 테스트, 운영) 전환 시 파일 복사 없이 키만 교체하면 됩니다.  
- **확장성:** 컨테이너가 불변인 클라우드‑네이티브 배포에 최적입니다.

## 실용적인 적용 사례

1. **문서 보안:** PDF에 눈에 보이거나 보이지 않는 워터마크를 삽입해 무단 배포를 방지합니다.  
2. **사용량 추적:** 매월 처리되는 문서 수를 모니터링해 메터드 할당량을 초과하지 않도록 관리합니다.  
3. **CMS 연동:** 콘텐츠 관리 시스템에 업로드되는 모든 파일에 자동으로 **PDF에 워터마크를 적용**합니다.

## 성능 고려 사항

- **필요할 때만 워터마크 적용** – 불필요한 대량 배치는 피합니다.  
- **요청 간 `Metered` 인스턴스 재사용** – 객체 생성 오버헤드를 줄입니다.  
- **고해상도 이미지 처리 시 메모리 모니터링** – SDK의 스트리밍 API를 활용해 메모리 사용량을 최소화합니다.

## 일반적인 문제와 해결책
| Issue | Solution |
|-------|----------|
| Keys are rejected | 문자열에 공백이나 줄바꿈이 없는지 다시 확인합니다. |
| License not activated | 워터마크 작업을 수행하기 **전에** `metered.setMeteredKey(...)` 호출을 했는지 확인합니다. |
| Out‑of‑memory errors on big PDFs | `WatermarkOptions.setUseMemoryCache(true)`를 사용해 처리 데이터를 디스크에 오프로드합니다. |

## 자주 묻는 질문

**Q: 메터드 라이선스가 무엇이며 왜 사용해야 하나요?**  
A: 메터드 라이선스는 각 API 호출을 추적해 실제 사용량에만 비용을 지불하게 하며, 애플리케이션을 손쉽게 확장할 수 있게 해줍니다.

**Q: 체험 라이선스 파일과 메터드 키를 전환할 수 있나요?**  
A: 예. 체험용 파일은 `license.setLicense("path/to/file.lic")`로 설정하고, 이후 `metered.setMeteredKey(...)`로 교체하면 됩니다.

**Q: 공개 키 또는 비공개 키를 잘못 입력하면 어떻게 되나요?**  
A: SDK가 인증 예외를 발생시키며 프리미엄 기능 접근을 차단합니다.

**Q: 한 달에 추가할 수 있는 워터마크 수에 제한이 있나요?**  
A: 제한은 계약에 따라 다르므로 대시보드에서 정확한 할당량을 확인하세요.

**Q: 이미지 파일에도 적용할 수 있나요?**  
A: 물론입니다. 동일 API가 JPEG, PNG, BMP 등 일반 이미지 포맷을 지원합니다.

## 리소스

- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-01-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs