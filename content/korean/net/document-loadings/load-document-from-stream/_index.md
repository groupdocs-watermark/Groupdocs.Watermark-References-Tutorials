---
title: 스트림에서 문서 로드
linktitle: 스트림에서 문서 로드
second_title: GroupDocs.Watermark .NET API
description: 이 가이드에서 .NET용 GroupDocs.Watermark를 사용하여 문서에 워터마크를 추가하는 방법을 알아보세요. 문서 보안을 강화하려는 개발자에게 적합합니다.
type: docs
weight: 11
url: /ko/net/document-loadings/load-document-from-stream/
---
## 소개
.NET을 사용하여 문서에 워터마크를 원활하게 추가하고 싶으십니까? 더 이상 보지 마세요! GroupDocs.Watermark for .NET은 다양한 문서 형식의 워터마크를 관리할 수 있는 강력하고 사용하기 쉬운 라이브러리입니다. PDF, Word 문서, 이미지 등 어떤 작업을 하든 이 도구를 사용하면 됩니다. 이 튜토리얼에서는 스트림에서 문서를 로드하고 워터마크를 추가하는 과정을 단계별로 안내합니다. 그럼 바로 들어가 보겠습니다!
## 전제조건
시작하기 전에 다음이 설정되어 있는지 확인하세요.
1. Visual Studio: 최신 버전의 Visual Studio는 모두 정상적으로 작동합니다.
2. .NET Framework: .NET Framework 4.0 이상이 설치되어 있는지 확인하세요.
3.  .NET용 GroupDocs.Watermark: 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).
4. C#에 대한 기본 지식: C# 및 객체 지향 프로그래밍 개념에 익숙하면 도움이 됩니다.

## 네임스페이스 가져오기
프로젝트에서 GroupDocs.Watermark를 사용하려면 필요한 네임스페이스를 가져와야 합니다. 이렇게 하면 문제 없이 라이브러리의 기능에 액세스할 수 있습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1단계: 프로젝트 설정
먼저 Visual Studio에서 프로젝트를 설정해야 합니다. 방법은 다음과 같습니다.
1. 새 프로젝트 만들기: Visual Studio를 열고 새 C# 콘솔 애플리케이션 프로젝트를 만듭니다.
2.  GroupDocs.Watermark 설치: NuGet 패키지 관리자를 통해 GroupDocs.Watermark 라이브러리를 설치합니다. 간단히 검색해 보세요`GroupDocs.Watermark` 그리고 설치하세요.
## 2단계: 문서 경로 정의
다음으로 문서의 경로와 워터마크가 있는 문서가 저장될 출력 파일을 정의해야 합니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 워터마킹하려는 문서의 실제 경로와`"Your Document Directory"` 워터마크가 있는 문서를 저장하려는 디렉토리를 선택하세요.
## 3단계: 스트림에서 문서 로드
이제 스트림에서 문서를 로드해 보겠습니다. 여기에는 문서를 스트림으로 연 다음`Watermarker` GroupDocs.Watermark 라이브러리의 클래스를 사용하여 관리하세요.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // 워터마크를 관리하는 코드가 여기에 표시됩니다.
}
```
 이 코드 조각은 문서가 스트림으로 열리고`Watermarker` 클래스는 이 스트림으로 초기화됩니다. 그만큼`using` 명령문은 사용 후 리소스가 적절하게 폐기되도록 보장합니다.
## 4단계: 워터마크 생성 및 추가
GroupDocs.Watermark를 사용하면 워터마크를 만드는 것이 간단합니다. 이 예에서는 간단한 텍스트 워터마크를 만들어 보겠습니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 여기서는`TextWatermark` "워터마크 테스트"라는 텍스트가 있는 개체를 선택하고 글꼴 세부정보를 지정합니다. 그런 다음 다음을 사용하여 이 워터마크를 문서에 추가합니다.`Add` 의 방법`Watermarker` 수업.
## 5단계: 워터마크가 있는 문서 저장
마지막으로 워터마크가 있는 문서를 지정된 출력 경로에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```
 이 코드는 새로 추가된 워터마크로 문서를 저장합니다.`outputFileName` 이전에 정의한 경로입니다.

## 결론
축하해요! .NET용 GroupDocs.Watermark를 사용하여 문서에 워터마크를 성공적으로 추가했습니다. 이 라이브러리를 사용하면 다양한 문서 형식의 워터마크를 매우 쉽게 관리할 수 있습니다. 텍스트, 이미지 또는 기타 유형의 워터마크를 추가해야 하는 경우 GroupDocs.Watermark에는 필요한 도구가 있습니다. 꼭 확인해 보세요.[선적 서류 비치](https://reference.groupdocs.com/Watermark/net/) 고급 기능과 사용자 정의 옵션을 확인하세요.
## FAQ
### .NET용 GroupDocs.Watermark를 사용하여 어떤 유형의 워터마크를 추가할 수 있습니까?
텍스트 워터마크, 이미지 워터마크는 물론 복잡한 모양과 로고까지 추가할 수 있습니다. 라이브러리는 광범위한 사용자 정의 옵션을 지원합니다.
### GroupDocs.Watermark를 사용하여 문서에서 워터마크를 제거할 수 있습니까?
예, GroupDocs.Watermark를 사용하면 문서에서 기존 워터마크도 제거할 수 있습니다.
### GroupDocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Watermark 라이센스를 어떻게 구매하나요?
라이센스를 직접 구매하실 수 있습니다.[GroupDocs 웹사이트](https://purchase.groupdocs.com/buy).
### 문제가 발생하면 어디서 지원을 받을 수 있나요?
 지원을 받으려면 다음을 방문하세요.[GroupDocs.Watermark 지원 포럼](https://forum.groupdocs.com/c/watermark/19).