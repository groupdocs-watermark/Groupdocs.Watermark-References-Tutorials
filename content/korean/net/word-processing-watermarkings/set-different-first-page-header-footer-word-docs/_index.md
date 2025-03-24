---
title: Word Docs에서 다른 첫 페이지 머리글/바닥글 설정
linktitle: Word Docs에서 다른 첫 페이지 머리글/바닥글 설정
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 첫 번째 페이지에 다양한 머리글과 바닥글을 설정하는 방법을 알아보세요.
weight: 36
url: /ko/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---
## 소개
문서 관리 및 조작 영역에서 .NET용 GroupDocs.Watermark는 워터마킹 문서에 대한 원활한 통합과 강력한 기능을 제공하는 강력한 도구로 등장합니다. 문서 처리의 일반적인 요구 사항 중 하나는 Word 문서의 첫 번째 페이지에 서로 다른 머리글과 바닥글을 설정하는 것입니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 이 작업을 수행하는 프로세스를 설명하고 각 단계를 쉽게 이해할 수 있는 부분으로 분류합니다.
## 전제조건
구현을 시작하기 전에 다음 전제 조건이 충족되는지 확인하세요.
1.  .NET용 GroupDocs.Watermark 설치: 다음에서 .NET용 GroupDocs.Watermark를 다운로드하여 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
2. 문서 준비: 첫 페이지에 서로 다른 머리글과 바닥글을 설정해야 하는 Word 문서를 준비하세요.

## 네임스페이스 가져오기
시작하려면 .NET용 GroupDocs.Watermark 기능을 활용하는 데 필요한 필수 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
이 단계에서는 처리해야 하는 문서의 경로를 정의하고 출력 파일 이름과 디렉터리를 지정합니다. 추가적으로, 우리는`Watermarker` 문서 경로 및 로드 옵션이 있는 개체입니다.
## 2단계: 문서 콘텐츠에 액세스
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 여기서는 다음을 사용하여 Word 문서의 내용을 검색합니다.`GetContent<T>()` 의 방법`Watermarker` 객체, 콘텐츠 유형 지정`WordProcessingContent`.
## 3단계: 페이지 설정 구성
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
이 단계에서는 첫 번째 페이지에 대해 다양한 머리글과 바닥글을 활성화하도록 페이지 설정 옵션을 구성합니다(`DifferentFirstPageHeaderFooter`), 홀수 및 짝수 페이지(`OddAndEvenPagesHeaderFooter`).
## 4단계: 변경 사항 저장
```csharp
watermarker.Save(outputFileName);
```
 마지막으로 다음을 호출하여 문서에 대한 수정 사항을 저장합니다.`Save()` 의 방법`Watermarker` 객체, 출력 파일 이름을 전달합니다.

## 결론
.NET용 GroupDocs.Watermark는 Word 문서의 첫 번째 페이지에 다양한 머리글과 바닥글을 설정하기 위한 간단한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 사용자는 요구 사항에 따라 문서 내용을 쉽게 조작할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 Word 이외의 다른 문서 형식을 처리할 수 있습니까?
예, .NET용 GroupDocs.Watermark는 PDF, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 테스트 목적으로 사용할 수 있는 평가판이 있습니까?
예, 사용자는 다음에서 .NET용 GroupDocs.Watermark 무료 평가판을 이용할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark는 기술 지원을 제공합니까?
 예, .NET용 Watermark에 대한 기술 지원은 다음을 통해 제공됩니다.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).
### 단기 사용을 위해 임시 라이센스를 구입할 수 있나요?
 예, .NET용 Watermark의 임시 라이센스는 다음에서 얻을 수 있습니다.[임시 라이센스 구매 페이지](https://purchase.groupdocs.com/temporary-license/).
### .NET용 GroupDocs.Watermark에 대한 포괄적인 문서는 어디에서 찾을 수 있습니까?
 .NET용 GroupDocs.Watermark에 대한 자세한 설명서는 다음에서 확인할 수 있습니다.[참고 페이지](https://tutorials.groupdocs.com/Watermark/net/).