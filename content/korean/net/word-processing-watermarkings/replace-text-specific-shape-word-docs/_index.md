---
title: Word Docs에서 특정 도형의 텍스트 바꾸기
linktitle: Word Docs에서 특정 도형의 텍스트 바꾸기
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 특정 도형의 텍스트를 바꾸는 방법을 알아보세요. 단계별 튜토리얼을 따라해보세요.
weight: 35
url: /ko/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
type: docs
---
# Word Docs에서 특정 도형의 텍스트 바꾸기

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 도형에 대한 텍스트를 바꾸는 방법을 살펴보겠습니다. .NET용 GroupDocs.Watermark는 Word 문서를 포함한 다양한 문서 형식의 워터마크 작업을 위한 광범위한 기능을 제공하는 강력한 라이브러리입니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: .NET용 GroupDocs.Watermark를 다운로드하여 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 문서: 특정 도형의 텍스트를 바꾸려는 Word 문서를 준비합니다.
3. 개발 환경: 필요한 도구와 종속성을 사용하여 개발 환경을 설정합니다.

## 네임스페이스 가져오기
먼저 .NET용 GroupDocs.Watermark 작업에 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 귀하의 코드는 여기에 있습니다
}
```
 이 단계에서는 Word 문서의 경로를 지정하고`WordProcessingLoadOptions` 문서를 로드합니다.
## 2단계: 문서 콘텐츠 가져오기
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 여기서는 다음을 사용하여 Word 문서의 내용을 검색합니다.`GetContent<T>()` 의 방법`Watermarker`클래스, 유형을 다음과 같이 지정`WordProcessingContent`.
## 3단계: 특정 모양의 텍스트 바꾸기
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
이 단계에서는 문서의 각 모양을 반복합니다. 도형에 지정된 텍스트(이 예에서는 "Some text")가 포함되어 있으면 이를 원하는 텍스트("Another text")로 바꿉니다.
## 4단계: 문서 저장
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
마지막으로 수정된 문서를 지정된 디렉터리에 저장합니다.

## 결론
.NET용 GroupDocs.Watermark는 Word 문서의 워터마크를 조작하는 편리하고 효율적인 방법을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 특정 모양의 텍스트를 쉽게 바꿀 수 있어 문서 처리 요구 사항에 맞는 유연성과 사용자 정의 옵션을 제공할 수 있습니다.
## FAQ
### Word 외에 다른 문서 형식의 도형 텍스트를 바꿀 수 있나요?
.NET용 GroupDocs.Watermark는 PDF, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다. 비슷한 방법을 사용하여 다양한 형식의 도형에 대한 텍스트를 바꿀 수 있습니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
GroupDocs 포럼을 방문하면 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19).
### .NET용 GroupDocs.Watermark를 사용하려면 임시 라이센스가 필요합니까?
 추가 기능이 필요하거나 확장된 사용이 필요한 경우 다음에서 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### .NET용 GroupDocs.Watermark의 정식 라이센스는 어디서 구입할 수 있나요?
 GroupDocs 웹사이트에서 전체 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy).