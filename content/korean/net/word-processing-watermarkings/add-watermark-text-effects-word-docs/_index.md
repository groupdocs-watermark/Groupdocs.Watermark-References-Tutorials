---
title: Word Docs에서 텍스트 효과로 워터마크 추가
linktitle: Word Docs에서 텍스트 효과로 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서에 텍스트 효과가 있는 사용자 정의 워터마크를 추가하는 방법을 알아보세요. 문서 보안과 시각적 매력을 쉽게 확보할 수 있습니다.
type: docs
weight: 21
url: /ko/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에 텍스트 효과가 있는 워터마크를 추가하는 방법을 살펴보겠습니다. 이러한 단계별 지침을 따르면 다양한 텍스트 효과가 포함된 사용자 정의 워터마크로 문서를 향상시킬 수 있습니다.
## 전제조건
시작하기 전에 다음 사항을 확인하세요.
1.  .NET용 GroupDocs.Watermark: 다음에서 라이브러리를 다운로드하고 설치합니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 문서 경로: 워터마크를 추가하려는 Word 문서의 경로를 알아보세요.
3. 출력 디렉터리: 수정된 문서를 저장할 디렉터리가 있습니다.

## 네임스페이스 가져오기
필수 클래스 및 메소드에 액세스하려면 필수 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Contents;
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
    // 워터마크 추가 코드는 여기에 있습니다.
}
```
## 2단계: 텍스트 효과로 워터마크 추가
원하는 텍스트와 글꼴로 텍스트 워터마크를 만든 다음 선 형식과 같은 텍스트 효과를 정의합니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## 3단계: 워터마크 옵션 사용자 정의
텍스트 효과 등 워터마크 섹션 옵션을 정의하고 워터마크에 할당합니다.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## 4단계: 문서 저장
워터마크가 추가된 수정된 문서를 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
Word 문서에 텍스트 효과가 있는 워터마크를 추가하면 시각적 매력과 보호 기능이 크게 향상될 수 있습니다. .NET용 GroupDocs.Watermark를 사용하면 이 프로세스가 간소화되고 사용자 정의가 가능해 전문가 수준의 문서를 효율적으로 만들 수 있습니다.
## FAQ
### 워터마크 텍스트의 글꼴과 크기를 사용자 정의할 수 있나요?
예, TextWatermark 개체를 생성하는 동안 글꼴과 크기를 지정할 수 있습니다.
### 단일 문서에 여러 개의 워터마크를 추가할 수 있습니까?
물론, .NET용 GroupDocs.Watermark는 단일 문서에 서로 다른 설정을 가진 여러 워터마크를 추가하는 것을 지원합니다.
### GroupDocs.Watermark는 Word 외에 다른 문서 형식을 지원합니까?
예, PDF, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 문서에 워터마크를 추가한 후 제거할 수 있나요?
예, 라이브러리는 문서에서 워터마크를 쉽게 제거하는 방법을 제공합니다.
### 테스트 목적으로 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).