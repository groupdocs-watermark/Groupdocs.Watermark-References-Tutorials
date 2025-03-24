---
title: Word Docs의 도형 유형 사용
linktitle: Word Docs의 도형 유형 사용
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 모양을 조작하는 방법을 알아보세요. 이 튜토리얼은 효율적인 문서 처리를 위한 지침을 제공합니다.
weight: 37
url: /ko/net/word-processing-watermarkings/shape-type-usage-word-docs/
---

# Word Docs의 도형 유형 사용

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서에서 모양 유형을 활용하는 방법을 살펴보겠습니다. Word 문서의 모양은 다양할 수 있으며 이를 조작하는 방법을 이해하는 것은 다양한 문서 처리 작업에 매우 중요할 수 있습니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 .NET 라이브러리용 GroupDocs.Watermark를 다운로드하고 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
2. 문서 경로: 처리할 Word 문서를 준비합니다.
3. 개발 환경: .NET Framework 지원으로 적합한 개발 환경을 설정합니다.

## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 이러한 네임스페이스는 Word 문서 작업에 필요한 클래스와 메서드에 대한 액세스를 제공합니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1단계: 문서 로드
Word 문서를 Watermarker 개체에 로드하는 것부터 시작하세요. 로드 프로세스 중에 필요한 문서 경로와 추가 옵션을 지정했는지 확인하세요.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 문서 처리 코드가 여기에 표시됩니다.
}
```
## 2단계: 문서 콘텐츠에 액세스
 다음을 사용하여 로드된 Word 문서의 내용에 액세스합니다.`GetContent<WordProcessingContent>()` 방법. 이렇게 하면 문서에 있는 섹션, 단락 및 도형에 액세스할 수 있습니다.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## 3단계: 섹션과 모양 반복
문서 내의 각 섹션과 모양을 반복하여 필요에 따라 검사하고 조작합니다.
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // 도형 조작 코드가 여기에 표시됩니다.
    }
}
```
## 4단계: 도형 유형 확인
루프 내에서 다음을 사용하여 특정 모양 유형을 확인합니다.`ShapeType` 재산. 이 예에서는 대각선 모서리가 둥근 모양을 식별하고 처리하는 방법을 보여줍니다.
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // 도형별 조작 코드가 여기에 표시됩니다.
}
```
## 5단계: 모양 조작
식별된 도형에 텍스트 추가, 서식 수정, 시각적 변경 사항 적용 등의 작업을 수행합니다.
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## 6단계: 문서 저장
필요한 모든 수정이 완료되면 지정된 출력 파일에 변경 사항이 적용된 문서를 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
Word 문서에서 도형을 조작하는 것은 다양한 문서 처리 작업에 필수적일 수 있습니다. .NET용 GroupDocs.Watermark를 사용하면 요구 사항을 효율적으로 충족하기 위해 모양을 쉽게 식별, 수정 및 조작할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 Word 이외의 다른 문서 형식을 처리할 수 있습니까?
예, .NET용 GroupDocs.Watermark는 PDF, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판에 액세스할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark는 기술 지원을 제공합니까?
 예, 다음을 통해 도움을 구하고 지역사회에 참여할 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).
### 특정 문서 요구 사항에 맞게 워터마킹 프로세스를 사용자 정의할 수 있습니까?
물론 .NET용 GroupDocs.Watermark는 필요에 따라 워터마킹 프로세스를 맞춤화할 수 있는 광범위한 사용자 정의 옵션을 제공합니다.
### .NET용 GroupDocs.Watermark의 임시 라이센스를 어떻게 얻을 수 있습니까?
 임시면허를 취득할 수 있습니다.[임시 라이센스 구매 페이지](https://purchase.groupdocs.com/temporary-license/) 테스트 및 평가 목적으로.