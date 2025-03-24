---
title: 지정된 위치에 문서 저장
linktitle: 지정된 위치에 문서 저장
second_title: GroupDocs.Watermark .NET API
description: 이 단계별 가이드를 통해 .NET용 GroupDocs.Watermark를 사용하여 문서에 워터마크를 쉽게 추가하는 방법을 알아보세요. 문서 보안을 강화하세요.
weight: 11
url: /ko/net/document-savings/save-document-specified-location/
---

# 지정된 위치에 문서 저장

## 소개
디지털 시대에는 문서 보안이 그 어느 때보다 중요해졌습니다. 워터마킹은 문서를 무단 사용으로부터 보호하는 효과적인 방법입니다. .NET용 GroupDocs.Watermark는 문서에 워터마크를 추가하기 위한 강력한 솔루션을 제공합니다. 워터마킹을 애플리케이션에 통합하려는 개발자이거나 문서 보호에 관심이 있는 사람이라면 이 튜토리얼이 프로세스를 단계별로 안내할 것입니다.
## 전제조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- .NET 개발 환경: Visual Studio 또는 기타 .NET 개발 환경이 설치되어 있는지 확인하세요.
-  .NET 라이브러리용 GroupDocs.Watermark: 프로젝트에서 라이브러리를 다운로드하고 참조하세요.[.NET용 GroupDocs.Watermark 다운로드](https://releases.groupdocs.com/Watermark/net/)
- C# 프로그래밍의 기본 지식: 기본 C# 프로그래밍 개념을 이해하면 도움이 됩니다.
- 워터마크를 적용할 문서: 워터마크를 적용할 샘플 문서를 준비하세요.
## 네임스페이스 가져오기
예제를 시작하기 전에 필요한 네임스페이스를 가져와야 합니다. 코드 파일 상단에 다음 using 문을 추가합니다.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
.NET용 GroupDocs.Watermark를 사용하여 문서에 워터마크를 추가하는 과정을 관리 가능한 단계로 나누어 보겠습니다. 워터마크를 성공적으로 적용하고 문서를 지정된 위치에 저장하려면 다음 단계를 따르십시오.
## 1단계: 프로젝트 설정
Visual Studio에서 새 .NET 프로젝트를 만드는 것부터 시작하세요. 단순화를 위해 콘솔 앱을 선택할 수 있습니다.
1. 비주얼 스튜디오를 엽니다.
2.  선택하다`File` >`New` >`Project`.
3.  선택하다`Console App (.NET Core)` 또는`Console App (.NET Framework)`.
4.  프로젝트 이름을 지정하고 클릭하세요.`Create`.

## 2단계: 문서 및 워터마크 텍스트 준비
### 문서 경로 지정
워터마크를 추가할 문서의 경로를 정의하세요. 이 예에서는 자리 표시자 경로를 사용해 보겠습니다.
```csharp
string documentPath = "Your Document Path";
```
### 출력 경로 정의
워터마킹된 문서를 저장할 출력 경로를 설정하세요.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 3단계: 문서 로드
 사용`Watermarker` 문서를 로드하는 클래스입니다. 이 클래스는 워터마크를 추가, 제거 및 편집하는 메서드를 제공합니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // 여기에 워터마킹 논리를 추가하세요.
}
```
## 4단계: 워터마크 생성 및 추가

### 텍스트 워터마크 만들기
 인스턴스화`TextWatermark` 원하는 텍스트 및 글꼴 속성을 사용하여 개체를 만듭니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### 문서에 워터마크 추가
 생성된 워터마크를 다음을 사용하여 문서에 추가하세요.`Add` 의 방법`Watermarker` 수업.
```csharp
watermarker.Add(watermark);
```
## 5단계: 문서 저장
마지막으로 워터마크가 포함된 문서를 지정된 위치에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```
## 결론
GroupDocs for .NET을 사용하여 문서에 워터마크를 표시하는 것은 문서 보안을 크게 향상시킬 수 있는 간단한 프로세스입니다. 이 단계별 가이드를 따르면 문서에 워터마크를 쉽게 추가하고 원하는 위치에 저장할 수 있습니다. 지적 재산을 보호하든, 문서 신뢰성을 보장하든, 아니면 단순히 전문적인 손길을 추가하든 .NET용 GroupDocs.Watermark는 필요한 도구를 제공합니다.
## FAQ
### .NET용 GroupDocs.Watermark에서 이미지를 워터마크로 사용할 수 있습니까?
예, GroupDocs for .NET에서는 텍스트와 이미지 워터마크를 모두 사용할 수 있습니다. 라이브러리는 귀하의 필요에 맞게 다양한 유형의 워터마크를 지원합니다.
### .NET용 GroupDocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark 라이센스를 어떻게 구매할 수 있나요?
 다음에서 라이센스를 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy).
### .NET용 GroupDocs.Watermark는 일괄 워터마킹을 지원합니까?
예, 문서 목록을 반복하고 워터마크를 적용하여 일괄 처리로 여러 문서에 워터마크를 적용할 수 있습니다.
### .NET용 GroupDocs.Watermark에 대한 지원은 어디서 받을 수 있나요?
 지원은 다음에서 가능합니다.[GroupDocs 포럼](https://forum.groupdocs.com/c/watermark/19).