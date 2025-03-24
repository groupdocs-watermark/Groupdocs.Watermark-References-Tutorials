---
title: Word Docs에서 도형 이미지에 워터마크 추가
linktitle: Word Docs에서 도형 이미지에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모양 이미지에 워터마크를 추가하는 방법을 알아보세요. 이 튜토리얼을 통해 문서 보안을 강화하세요.
weight: 17
url: /ko/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서 내의 모양 이미지에 워터마크를 추가하는 방법을 살펴보겠습니다. 워터마킹은 특히 민감하거나 기밀 정보를 다룰 때 문서 보호의 중요한 측면입니다. 모양 이미지에 워터마크를 추가하면 문서의 무결성과 보안을 보장할 수 있습니다.
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: 다음에서 GroupDocs.Watermark 라이브러리를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/Watermark/net/).
2. 문서: 워터마크를 추가할 Word 문서를 준비합니다.
3. 개발 환경: 선호하는 .NET 개발 환경을 설정합니다.
## 네임스페이스 가져오기
코드를 작성하기 전에 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
먼저 문서 경로를 정의하고 출력 파일 이름을 지정합니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 2단계: 워터마커 초기화
 인스턴스화`Watermarker` 문서 경로와 선택적 로드 옵션을 제공하여 객체를 생성합니다.
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 여기에 워터마킹 논리를 추가하세요.
}
```
## 3단계: 텍스트 워터마크 만들기
텍스트, 글꼴, 정렬, 회전, 크기 조정 등과 같은 원하는 속성으로 텍스트 워터마크를 정의합니다.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4단계: 모양 이미지에 워터마크 적용
문서 섹션과 모양을 반복하여 모양 이미지를 식별하고 워터마크를 추가합니다.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## 5단계: 문서 저장
워터마크가 추가된 문서를 지정된 출력 파일에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모양 이미지에 워터마크를 추가하는 방법을 배웠습니다. 단계별 가이드를 따르고 GroupDocs.Watermark의 강력한 기능을 활용하면 문서의 보안과 보호를 효과적으로 강화할 수 있습니다.
## FAQ
### 워터마크 텍스트의 모양을 사용자 정의할 수 있나요?
네. 글꼴, 크기, 색상, 회전 각도, 정렬 등 다양한 속성을 조정하여 원하는 대로 워터마크를 맞춤 설정할 수 있습니다.
### GroupDocs.Watermark는 Word 외에 다른 문서 형식을 지원합니까?
예, GroupDocs.Watermark는 PDF, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 단일 문서에 여러 개의 워터마크를 추가할 수 있습니까?
물론, 동일한 문서 내에서 콘텐츠, 스타일, 위치가 다른 여러 워터마크를 추가할 수 있습니다.
### GroupDocs.Watermark를 사용하여 문서에서 워터마크를 제거할 수 있습니까?
예, GroupDocs.Watermark는 문서에서 워터마크를 효율적으로 감지하고 제거하는 기능을 제공합니다.
### GroupDocs.Watermark는 플랫폼 간 호환성을 제공합니까?
예, GroupDocs.Watermark는 .NET Framework, .NET Core 및 .NET Standard와 호환되므로 다양한 플랫폼 간의 원활한 통합을 보장합니다.