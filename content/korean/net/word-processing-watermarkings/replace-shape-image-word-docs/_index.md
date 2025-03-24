---
title: Word Docs에서 도형 이미지 바꾸기
linktitle: Word Docs에서 도형 이미지 바꾸기
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모양 이미지를 프로그래밍 방식으로 바꾸는 방법을 알아보세요. 문서 조작 작업을 손쉽게 단순화하세요.
weight: 33
url: /ko/net/word-processing-watermarkings/replace-shape-image-word-docs/
---

# Word Docs에서 도형 이미지 바꾸기

## 소개
소프트웨어 개발 영역, 특히 .NET 환경에서는 문서 조작을 효율적이고 안전하게 처리하는 것이 중요합니다. 개발자가 자주 직면하는 수많은 작업 중에서 일반적인 과제 중 하나는 프로그래밍 방식으로 Word 문서 내의 도형 이미지를 바꾸는 것입니다. 올바른 도구와 라이브러리가 없으면 지루한 작업이 될 수 있습니다.
다행스럽게도 GroupDocs는 Word 문서를 포함한 다양한 문서 형식 내에서 워터마킹 및 워터마크 조작을 처리하도록 설계된 다목적 라이브러리인 GroupDocs.Watermark for .NET 형태의 강력한 솔루션을 제공합니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모양 이미지를 바꾸는 과정을 단계별로 살펴보겠습니다.
## 전제조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 .NET 라이브러리용 GroupDocs.Watermark를 다운로드하고 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
2. 조작할 문서: 프로그래밍 방식으로 바꾸려는 모양 이미지가 포함된 Word 문서를 준비합니다.
3. 개발 환경: .NET 기능을 갖춘 작업 개발 환경(바람직하게는 Visual Studio)을 설정하십시오.
4. C# 프로그래밍의 기본 지식: GroupDocs 라이브러리와 상호 작용하기 위해 C#을 사용하므로 C# 프로그래밍 기본 사항을 숙지하세요.
## 네임스페이스 가져오기
코딩 부분을 살펴보기 전에 필요한 네임스페이스를 C# 프로젝트로 가져오겠습니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System;
using System.IO;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 문서가 성공적으로 로드되었습니다.
}
```
 이 단계에서는 조작하려는 Word 문서의 경로를 정의합니다. 그런 다음`WordProcessingLoadOptions` Word 문서에 대한 로드 옵션을 지정합니다. 다음으로, 우리는`Watermarker` 문서 경로 및 로드 옵션이 있는 개체입니다.
## 2단계: 문서 콘텐츠에 액세스
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 여기서는 다음을 사용하여 Word 문서의 내용을 검색합니다.`GetContent` 의 방법`Watermarker` 물체. 콘텐츠는`WordProcessingContent` 문서 내의 다양한 요소에 접근하고 조작할 수 있게 해주는 객체입니다.
## 3단계: 모양 이미지 바꾸기
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Image != null)
    {
        shape.Image = new WordProcessingWatermarkableImage(File.ReadAllBytes(Constants.TestPng));
    }
}
```
이 단계에서는 문서의 첫 번째 섹션에 있는 각 모양을 반복합니다. 이미지가 포함된 각 도형에 대해(`shape.Image != null`), 기존 이미지를 새 이미지로 교체합니다. 이 예에서는 상수를 사용하고 있습니다.`TestPng` 대체 이미지로 원하는 이미지의 경로로 바꾸십시오.
## 4단계: 문서 저장
```csharp
watermarker.Save(outputFileName);
```
마지막으로, 교체된 이미지가 포함된 수정된 문서를 지정된 출력 파일 이름으로 저장합니다.

## 결론
.NET용 GroupDocs.Watermark는 프로그래밍 방식으로 Word 문서의 모양 이미지를 바꾸는 프로세스를 단순화합니다. 이 자습서에 설명된 단계를 따르면 이 기능을 .NET 애플리케이션에 원활하게 통합하여 문서 조작 작업에 드는 시간과 노력을 절약할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 다른 버전의 Word 문서와 호환됩니까?
예, .NET용 GroupDocs.Watermark는 .doc 및 .docx 형식을 포함하여 다양한 버전의 Word 문서를 지원합니다.
### GroupDocs.Watermark를 사용하여 도형 이미지 외에 다른 유형의 요소를 바꿀 수 있나요?
전적으로. GroupDocs.Watermark는 다양한 형식의 문서 내 워터마크, 이미지, 텍스트 및 기타 요소를 바꾸는 광범위한 기능을 제공합니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드하여 .NET용 GroupDocs.Watermark의 기능을 탐색할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark는 PDF 문서의 워터마크 처리를 지원합니까?
예, .NET용 GroupDocs.Watermark는 Word, Excel, PowerPoint 등과 같은 다른 형식과 함께 PDF 문서 내에서 워터마킹 및 워터마크 조작을 지원합니다.
### .NET용 GroupDocs.Watermark에 대한 도움을 받으려면 어떻게 해야 합니까?
 GroupDocs.Watermark 포럼을 방문할 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19) 귀하가 직면할 수 있는 질문이나 문제에 대해 도움을 구하거나 커뮤니티에 참여합니다.