---
title: Word Docs에서 특정 텍스트 서식이 있는 도형 제거
linktitle: Word Docs에서 특정 텍스트 서식이 있는 도형 제거
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 특정 텍스트 서식이 있는 도형을 제거하는 방법을 알아보세요. 워터마크를 효율적으로 조작하려면 가이드를 따르세요.
type: docs
weight: 31
url: /ko/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
---
## 소개
.NET용 GroupDocs.Watermark는 개발자가 다양한 문서 형식의 워터마크를 프로그래밍 방식으로 조작할 수 있는 강력한 API입니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 특정 텍스트 서식이 있는 도형을 제거하는 방법에 중점을 둘 것입니다. 숙련된 개발자이든 이제 막 시작하는 개발자이든 이 단계별 가이드는 모양을 효율적이고 효과적으로 제거하는 과정을 이해하는 데 도움이 될 것입니다.
## 전제조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: 개발 환경에 .NET용 GroupDocs.Watermark 라이브러리가 설치되어 있는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET IDE가 설치된 적절한 개발 환경을 설정합니다.
3. Word 문서: 제거하려는 특정 텍스트 서식이 포함된 도형이 포함된 Word 문서를 준비합니다.

## 네임스페이스 가져오기
구현을 시작하기 전에 필요한 네임스페이스를 가져오겠습니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 구현은 여기로 이동
}
```
## 2단계: 콘텐츠 가져오기 및 섹션 반복
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    // 구현은 여기로 이동
}
```
## 3단계: 모양을 반복하고 텍스트 서식을 기준으로 제거
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## 4단계: 문서 저장
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 특정 텍스트 서식이 있는 도형을 제거하는 방법을 배웠습니다. 단계별 가이드를 따르고 제공된 코드 예제를 활용함으로써 개발자는 요구 사항에 따라 워터마크를 쉽게 조작할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 Word 이외의 다른 문서 형식과 호환됩니까?
예, .NET용 GroupDocs.Watermark는 Excel, PowerPoint, PDF 등을 포함한 다양한 문서 형식을 지원합니다.
### 텍스트 서식을 기반으로 도형 제거 기준을 사용자 정의할 수 있나요?
전적으로! 글꼴 크기, 스타일, 색상 등과 같은 특정 텍스트 속성을 대상으로 코드를 수정할 수 있습니다.
### .NET용 GroupDocs.Watermark는 워터마크 추가도 지원합니까?
예, 제거 외에도 .NET용 GroupDocs.Watermark를 사용하여 문서에 텍스트 또는 이미지 워터마크를 추가할 수도 있습니다.
### 구매하기 전에 테스트할 수 있는 평가판이 있나요?
 예, GroupDocs에서 무료 평가판을 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark에 대한 기술 지원이나 지원을 받으려면 어떻게 해야 합니까?
 기술 지원을 받으려면 다음 지원 포럼을 방문하세요.[GroupDocs.Watermark 포럼](https://forum.groupdocs.com/c/watermark/19).