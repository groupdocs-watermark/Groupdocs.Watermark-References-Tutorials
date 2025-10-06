---
title: Word Docs의 모든 헤더에 이미지 워터마크 추가
linktitle: Word Docs의 모든 헤더에 이미지 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모든 헤더에 이미지 워터마크를 쉽게 추가할 수 있습니다. 자세한 코드 예제가 포함된 단계별 가이드를 따르세요.
weight: 10
url: /ko/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
type: docs
---
# Word Docs의 모든 헤더에 이미지 워터마크 추가

## 소개
워터마크는 소유권, 기밀성, 브랜드 정보 등의 정보를 문서에 삽입하는 방법을 제공하여 문서 관리의 필수적인 부분이 될 수 있습니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모든 헤더에 이미지 워터마크를 추가하는 단계를 안내합니다. 프로그래밍이 처음이시든 숙련된 개발자이시든, 이 가이드는 워터마킹 목표를 쉽게 달성하는 데 도움이 될 것입니다.
## 전제조건
코드를 살펴보기 전에 필요한 모든 것이 있는지 확인하겠습니다. 시작하기 위한 체크리스트는 다음과 같습니다.
1.  .NET용 GroupDocs.Watermark: 다음에서 최신 버전을 다운로드하세요.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 호환 IDE.
3. .NET Framework: .NET Framework가 설치되어 있는지 확인하세요.
4. 샘플 Word 문서: 워터마크를 추가하려는 Word 문서입니다.
5. 워터마크용 이미지: 워터마크로 사용할 이미지 파일입니다.
이러한 준비가 완료되면 프로젝트 설정을 시작할 수 있습니다.
## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 가져오겠습니다. 이러한 네임스페이스에는 문서의 워터마크 작업에 도움이 되는 클래스와 메서드가 포함되어 있습니다.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 프로젝트 설정
시작하려면 Visual Studio에서 새 콘솔 애플리케이션을 만듭니다. 프로젝트에 GroupDocs.Watermark DLL에 대한 참조를 추가합니다. GroupDocs.Watermark NuGet 패키지를 설치하면 됩니다.
```bash
Install-Package GroupDocs.Watermark
```
## 2단계: 문서 로드
 워터마크를 추가하는 첫 번째 단계는 워터마크가 추가될 문서를 로드하는 것입니다. 여기서는`WordProcessingLoadOptions` Word 문서를 로드합니다.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마크를 추가하는 코드가 여기에 표시됩니다.
}
```
## 3단계: 이미지 워터마크 만들기
다음으로 이미지 워터마크를 만들어 보겠습니다. 여기에는 워터마크로 사용하려는 이미지 파일을 지정하는 작업이 포함됩니다.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // 워터마크를 적용하는 코드가 여기에 표시됩니다.
}
```
## 4단계: 첫 번째 섹션 헤더에 워터마크 추가
 Word 문서의 첫 번째 섹션에 있는 모든 헤더에 워터마크를 추가해야 합니다. 이를 위해 우리는`WordProcessingWatermarkSectionOptions` 섹션 인덱스를 지정합니다.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## 5단계: 링크 머리글 및 바닥글
모든 섹션의 머리글에 워터마크가 나타나도록 하기 위해 다른 모든 머리글과 바닥글을 첫 번째 섹션의 머리글과 바닥글에 연결합니다.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## 6단계: 문서 저장
마지막으로 워터마크가 표시된 문서를 지정된 경로에 저장합니다. 이 단계에서는 원본 문서를 보존하면서 변경 사항이 새 파일에 기록되도록 합니다.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## 결론
그리고 거기에 있습니다! .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 모든 헤더에 이미지 워터마크를 성공적으로 추가했습니다. 이 강력한 라이브러리를 사용하면 다양한 문서 유형에 워터마크를 쉽게 관리하고 적용하여 콘텐츠를 보호하고 전문적인 브랜드를 부여할 수 있습니다.
## FAQ
### 이미지 외에 다른 유형의 워터마크를 사용할 수 있나요?
예, GroupDocs는 텍스트, 이미지, 심지어 복합 워터마크도 지원합니다.
### 헤더 외에 문서의 다른 부분에도 워터마킹이 가능한가요?
전적으로! 바닥글, 본문, 심지어 특정 페이지나 섹션까지 워터마킹할 수 있습니다.
### GroupDocs.Watermark는 다른 문서 형식을 지원합니까?
예, PDF, Excel, PowerPoint 등을 포함한 다양한 형식을 지원합니다.
### 워터마크의 위치와 모양을 사용자 정의할 수 있나요?
예, 워터마크의 크기, 위치, 불투명도 및 기타 다양한 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).