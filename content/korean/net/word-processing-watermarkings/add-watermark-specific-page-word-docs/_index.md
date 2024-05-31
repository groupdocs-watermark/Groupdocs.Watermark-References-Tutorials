---
title: Word Docs의 특정 페이지에 워터마크 추가
linktitle: Word Docs의 특정 페이지에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET을 사용하여 Word 문서의 특정 페이지에 워터마크를 추가하는 방법을 알아보세요. 콘텐츠를 손쉽게 보호하세요.
type: docs
weight: 14
url: /ko/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## 소개
문서에 워터마킹을 하는 것은 문서 보안과 브랜딩의 중요한 측면입니다. 이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 페이지에 워터마크를 추가하는 방법을 살펴보겠습니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- C# 프로그래밍에 대한 기본 지식.
- 비주얼 스튜디오 IDE를 설치했습니다.
- 프로젝트에 .NET용 GroupDocs.Watermark가 설치되어 있습니다.

## 네임스페이스 가져오기
코드를 살펴보기 전에 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 귀하의 코드는 여기에 저장됩니다
}
```
## 2단계: 워터마크 추가
```csharp
// 워터마크 텍스트 및 스타일 정의
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// 마지막 페이지에 워터마크 추가
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## 3단계: 문서 저장
```csharp
// 워터마크가 포함된 문서를 저장하세요.
watermarker.Save(outputFileName);
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 페이지에 워터마크를 추가하는 방법을 배웠습니다. 다음 단계를 수행하면 문서를 효과적으로 보호하고 필요에 따라 브랜딩 요소를 추가할 수 있습니다.
## FAQ
### 워터마크 텍스트와 스타일을 사용자 정의할 수 있나요?
예. 요구 사항에 따라 워터마크의 텍스트, 글꼴, 크기, 색상 및 위치를 사용자 정의할 수 있습니다.
### .NET용 GroupDocs.Watermark는 다른 문서 형식과 호환됩니까?
예, GroupDocs.Watermark는 Word, Excel, PowerPoint, PDF 등을 포함한 다양한 문서 형식을 지원합니다.
### 단일 문서에 여러 개의 워터마크를 추가할 수 있나요?
물론, 동일한 문서에 다양한 콘텐츠와 스타일을 가진 여러 워터마크를 추가할 수 있습니다.
### .NET용 GroupDocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 무료 평가판을 통해 GroupDocs.Watermark의 기능을 탐색할 수 있습니다. 시작하려면 제공된 링크를 방문하세요.[여기](https://releases.groupdocs.com/).
### GroupDocs.Watermark에 대한 기술 지원은 어디서 받을 수 있나요?
 다음에서 유용한 리소스를 찾고 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19)GroupDocs.Watermark 포럼. 커뮤니티에 가입하려면 제공된 링크를 방문하세요.