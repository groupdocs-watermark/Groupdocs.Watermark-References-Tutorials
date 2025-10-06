---
title: Word Docs에서 도형 설정으로 워터마크 추가
linktitle: Word Docs에서 도형 설정으로 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET을 사용하여 Word 문서에 모양 설정이 포함된 워터마크를 추가하는 방법을 알아보세요. 문서를 효과적으로 보호하세요.
weight: 20
url: /ko/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# Word Docs에서 도형 설정으로 워터마크 추가

## 소개
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에 모양 설정이 포함된 워터마크를 추가하는 과정을 안내합니다.
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Watermark가 설치되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. C# 프로그래밍에 대한 기본 지식.
3. Word 문서 처리에 대한 이해.

## 네임스페이스 가져오기
먼저 필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
워터마크를 추가하려는 Word 문서를 로드합니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마크 추가 코드가 여기에 표시됩니다.
}
```
## 2단계: 워터마크 추가
 인스턴스화`TextWatermark` 개체를 선택하고 워터마크로 사용할 텍스트를 지정합니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## 3단계: 워터마크 설정 사용자 정의
정렬, 회전 각도, 색상, 불투명도 등 워터마크에 대한 다양한 설정을 지정합니다.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## 4단계: 워터마크 섹션 옵션 정의
모양 이름, 대체 텍스트 등 워터마크 섹션에 대한 옵션을 정의합니다.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## 5단계: 문서에 워터마크 추가
지정된 옵션을 사용하여 문서에 워터마크를 추가합니다.
```csharp
watermarker.Add(watermark, options);
```
## 6단계: 문서 저장
워터마크가 추가된 문서를 저장하세요.
```csharp
watermarker.Save(outputFileName);
```

## 결론
GroupDocs용 워터마크를 사용하여 Word 문서에 모양 설정이 포함된 워터마크를 추가하는 과정은 간단합니다. 이 튜토리얼에 설명된 단계를 따르면 사용자 정의된 워터마크로 문서를 효과적으로 보호할 수 있습니다.
## FAQ
### 동일한 문서에 여러 워터마크를 추가할 수 있나요?
예, 동일한 문서에 설정이 다른 여러 워터마크를 추가할 수 있습니다.
### GroupDocs.Watermark는 Word 외에 다른 문서 형식을 지원합니까?
예, GroupDocs.Watermark는 Excel, PowerPoint, PDF 등을 포함한 다양한 문서 형식을 지원합니다.
### 워터마크의 모양을 추가로 사용자 정의할 수 있나요?
물론, 글꼴 크기, 스타일, 색상, 위치 등 다양한 매개변수를 필요에 맞게 조정할 수 있습니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 받을 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Watermark에 대한 지원은 어디서 찾을 수 있나요?
 GroupDocs 포럼에서 지원을 찾고 질문할 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19).