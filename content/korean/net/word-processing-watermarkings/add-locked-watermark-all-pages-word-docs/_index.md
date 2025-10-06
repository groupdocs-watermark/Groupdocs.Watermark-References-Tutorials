---
title: Word Docs의 모든 페이지에 잠긴 워터마크 추가
linktitle: Word Docs의 모든 페이지에 잠긴 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 잠긴 워터마크를 추가하여 문서를 보호하세요. 쉬운 구현을 위해 단계별 가이드를 따르세요.
weight: 11
url: /ko/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Word Docs의 모든 페이지에 잠긴 워터마크 추가

## 소개
문서에 워터마크를 추가하는 것은 콘텐츠를 보호하고 브랜드화하는 데 있어 중요한 단계입니다. 무단 사용을 방지하거나 단순히 전문적인 손길을 추가하는 등 워터마크는 다양한 용도로 사용될 수 있습니다. 이 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 Word 문서의 모든 페이지에 잠긴 워터마크를 추가하는 과정을 안내합니다.
## 전제조건
단계별 가이드를 살펴보기 전에 필요한 모든 것이 갖추어져 있는지 확인하세요.
1. .NET용 Groupdocs.Watermark: 다음에서 최신 버전을 다운로드하세요.[여기](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
3. 개발 환경: Visual Studio와 같은 개발 환경입니다.
4.  라이센스: 다음을 선택할 수 있습니다.[무료 시험판](https://releases.groupdocs.com/) 또는 구매[임시 면허증](https://purchase.groupdocs.com/temporary-license/).
## 네임스페이스 가져오기
먼저, 프로젝트에 필요한 네임스페이스를 가져와야 합니다. 이는 Groupdocs.Watermark에서 제공하는 클래스와 메서드에 액세스하는 데 필수적입니다.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 프로젝트 설정

개발 환경을 열고 새 .NET 프로젝트를 만듭니다. 이는 콘솔 애플리케이션일 수도 있고 필요에 맞는 다른 유형일 수도 있습니다.

프로젝트에 Groupdocs.Watermark 패키지를 추가해야 합니다. 이는 NuGet 패키지 관리자를 통해 수행할 수 있습니다. NuGet 패키지 관리자 콘솔에서 다음 명령을 실행합니다.
```sh
Install-Package GroupDocs.Watermark
```
## 2단계: Word 문서 로드
### 문서 경로 정의
Word 문서의 경로를 지정합니다. 이것이 워터마크를 추가하려는 문서가 됩니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### 로드 옵션 설정
 인스턴스 만들기`WordProcessingLoadOptions` 특정 옵션으로 Word 문서를 로드합니다.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3단계: 워터마크 만들기
### 워터마커 초기화
 사용하여`Watermarker`클래스에서 지정된 로드 옵션을 사용하여 문서를 로드합니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 추가 단계는 이 using 블록 내부에 있습니다.
}
```
### 워터마크 속성 정의
 만들기`TextWatermark` 원하는 텍스트, 글꼴, 색상으로 인스턴스를 만듭니다.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 4단계: 모든 페이지에 워터마크 적용
### 워터마크 옵션 설정
 정의하다`WordProcessingWatermarkPagesOptions` 그리고 설정`IsLocked` 워터마크를 잠그려면 속성을 true로 설정합니다. 이렇게 하면 워터마크가 쉽게 제거되지 않습니다.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### 선택 사항: 비밀번호 보호 추가
추가 보안 계층을 추가하려면 워터마크에 대한 비밀번호를 설정할 수 있습니다.
```csharp
// 비밀번호로 보호하려면
// 옵션.비밀번호 = "7654321";
```
### 워터마크 추가
 사용`Add` 의 방법`Watermarker` 지정된 옵션을 사용하여 문서에 워터마크를 추가하는 클래스입니다.
```csharp
watermarker.Add(watermark, options);
```
## 5단계: 문서 저장
마지막으로 수정된 문서를 지정된 출력 파일에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
다음 단계를 수행하면 .NET용 Groupdocs.Watermark를 사용하여 Word 문서의 모든 페이지에 잠긴 워터마크를 쉽게 추가할 수 있습니다. 이는 무단 사용으로부터 문서를 보호하는 데 도움이 될 뿐만 아니라 콘텐츠에 전문적인 느낌을 더해줍니다. Groupdocs.Watermark는 워터마킹 요구 사항에 대한 포괄적인 솔루션을 제공하여 문서의 보안과 브랜드를 보장합니다.
## FAQ
### 텍스트 대신 이미지를 워터마크로 사용할 수 있나요?
 예, Groupdocs는 텍스트와 이미지 워터마크를 모두 지원합니다. 교체할 수 있습니다`TextWatermark` ~와 함께`ImageWatermark` 이미지를 지정하세요.
### 워터마크 위치를 맞춤 설정할 수 있나요?
 전적으로! 다음과 같은 속성을 사용하여 워터마크의 위치를 설정할 수 있습니다.`HorizontalAlignment` 그리고`VerticalAlignment`.
### 문서의 페이지별로 워터마크를 다르게 적용할 수 있나요?
 예, 다음을 사용하여 특정 페이지에 대한 워터마크를 사용자 정의할 수 있습니다.`PageIndex` 에 있는 재산`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark는 Word 외에 다른 문서 형식을 지원합니까?
예, Groupdocs는 PDF, Excel, PowerPoint 등을 포함한 다양한 형식을 지원합니다.
### Groupdocs.Watermark를 사용하기 위한 시스템 요구 사항은 무엇입니까?
.NET Framework가 설치된 시스템과 Visual Studio와 같은 개발 환경이 필요합니다.