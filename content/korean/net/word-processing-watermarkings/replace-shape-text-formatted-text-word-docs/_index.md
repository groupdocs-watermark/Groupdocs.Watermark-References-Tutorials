---
title: Word Docs에서 도형 텍스트를 서식 있는 텍스트로 바꾸기
linktitle: Word Docs에서 도형 텍스트를 서식 있는 텍스트로 바꾸기
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 도형 텍스트를 서식 있는 텍스트로 바꾸는 방법을 알아보세요. 문서 편집 기능을 쉽게 사용할 수 있습니다.
weight: 34
url: /ko/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---

# Word Docs에서 도형 텍스트를 서식 있는 텍스트로 바꾸기

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 도형 텍스트를 서식 있는 텍스트로 바꾸는 과정을 안내합니다. 이 라이브러리는 모양 내의 텍스트 교체를 포함하여 워터마크 작업을 위한 강력한 기능을 제공합니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: .NET용 GroupDocs.Watermark를 설치하고 설정했는지 확인하세요. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 문서 경로: 텍스트를 바꾸려는 Word 문서의 경로가 있어야 합니다.

## 네임스페이스 가져오기
코드를 작성하기 전에 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
 다음을 사용하여 Word 문서를 로드합니다.`Watermarker` 수업:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 귀하의 코드는 여기에 계속됩니다 ...
}
```
## 2단계: 콘텐츠 가져오기 및 텍스트 바꾸기
문서가 로드되면 콘텐츠를 가져와 도형 내의 텍스트를 바꿉니다.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## 3단계: 문서 저장
텍스트를 바꾼 후 수정된 문서를 저장합니다.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 결론
.NET용 Watermark를 사용하면 Word 문서에서 도형 텍스트를 서식 있는 텍스트로 쉽게 바꿀 수 있습니다. 이 튜토리얼에 설명된 단계를 따르면 문서 내의 텍스트를 효율적으로 관리하고 조작할 수 있습니다.

## FAQ
### .NET용 GroupDocs.Watermark를 사용하여 다른 유형의 문서에서 텍스트를 바꿀 수 있습니까?
예, GroupDocs는 PDF, Excel, PowerPoint 등과 같은 다양한 문서 형식을 지원합니다.
### GroupDocs.Watermark는 .NET Core와 호환됩니까?
예, GroupDocs.Watermark는 .NET Framework와 .NET Core를 모두 지원합니다.
### GroupDocs.Watermark는 이미지를 워터마크로 추가하는 기능을 지원합니까?
물론, GroupDocs.Watermark를 사용하면 문서에 텍스트와 이미지 워터마크를 모두 추가할 수 있습니다.
### GroupDocs.Watermark를 사용하여 추가된 워터마크의 모양을 사용자 정의할 수 있습니까?
예, 워터마크의 모양, 위치 및 기타 속성을 완전히 제어할 수 있습니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).