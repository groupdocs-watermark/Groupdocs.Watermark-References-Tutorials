---
title: Word Docs의 특정 페이지에 잠긴 워터마크 추가
linktitle: Word Docs의 특정 페이지에 잠긴 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: 간편한 단계별 가이드를 통해 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 페이지에 잠긴 워터마크를 추가하는 방법을 알아보세요.
weight: 12
url: /ko/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Word Docs의 특정 페이지에 잠긴 워터마크 추가

## 소개
Word 문서의 특정 페이지에 워터마크를 추가하려고 하지만 쉽게 제거하거나 편집할 수 없도록 잠그고 싶으십니까? 당신은 바로 이곳에 있습니다! 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 페이지에 잠긴 워터마크를 추가하는 과정을 안내합니다. 이 강력한 라이브러리를 사용하면 다양한 문서 유형에 워터마크를 쉽게 적용, 관리 및 사용자 정의할 수 있습니다. 개발자이든 문서 보안이 필요한 사람이든 이 가이드는 각 단계를 간단한 방식으로 안내합니다.
## 전제조건
튜토리얼을 시작하기 전에 필요한 모든 것이 갖추어져 있는지 확인하십시오.
1.  .NET용 GroupDocs.Watermark: 다음을 수행할 수 있습니다.[다운로드](https://releases.groupdocs.com/Watermark/net/) 최신 버전.
2. 개발 환경: Visual Studio와 같은 IDE.
3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 도움이 됩니다.
4. 워터마크할 문서: 워터마크를 추가하려는 Word 문서(.docx 또는 .doc)입니다.
## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. 이러한 네임스페이스는 GroupDocs.Watermark 작업에 필요한 클래스 및 메서드에 대한 액세스를 제공합니다.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
이제 전제 조건을 다루고 필요한 네임스페이스를 가져왔으므로 프로세스를 단계별로 분석해 보겠습니다.
## 1단계: Word 문서 로드
 먼저 워터마크를 추가하려는 Word 문서를 로드해야 합니다. 이 작업은 다음을 사용하여 수행할 수 있습니다.`Watermarker` 함께 수업`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 다음 단계를 계속하세요.
}
```
## 2단계: 텍스트 워터마크 만들기
다음으로 텍스트 워터마크를 만듭니다. 요구 사항에 따라 텍스트, 글꼴, 색상 및 기타 속성을 사용자 정의할 수 있습니다.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## 3단계: 워터마크 옵션 구성
 특정 페이지에 워터마크를 적용하고 잠그려면`WordProcessingWatermarkPagesOptions`여기에서는 워터마크가 표시될 페이지 번호를 지정하고 잠금 옵션을 설정합니다.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // 페이지 지정
options.IsLocked = true; // 워터마크 잠금
options.LockType = WordProcessingLockType.AllowOnlyComments; // 잠금 유형 설정
// 비밀번호로 보호하려면
// 옵션.비밀번호 = "7654321";
```
## 4단계: 문서에 워터마크 추가
워터마크와 옵션이 구성되었으면 이제 문서에 워터마크를 추가할 수 있습니다.
```csharp
watermarker.Add(watermark, options);
```
## 5단계: 문서 저장
마지막으로 워터마크가 적용된 문서를 저장하세요. 적절한 출력 경로를 선택하고 파일을 저장합니다.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## 결론
축하해요! .NET용 GroupDocs.Watermark를 사용하여 Word 문서의 특정 페이지에 잠긴 워터마크를 성공적으로 추가했습니다. 이 튜토리얼에서는 문서 로드부터 워터마크가 있는 파일 저장까지 모든 필수 단계를 다루었습니다. 다음 단계를 따르면 문서에 안전하게 워터마크가 표시되어 콘텐츠를 무단 편집 및 사용으로부터 보호할 수 있습니다.
 자세한 내용은 다음을 참조하세요.[GroupDocs.Watermark 문서](https://tutorials.groupdocs.com/Watermark/net/) . 질문이 있거나 추가 도움이 필요하시면 언제든지 방문해주세요.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### .NET용 GroupDocs.Watermark란 무엇입니까?
.NET용 GroupDocs.Watermark는 개발자가 Word, PDF, Excel 등을 포함한 다양한 유형의 문서에 워터마크를 추가할 수 있는 강력한 라이브러리입니다.
### 문서의 여러 페이지에 워터마크를 적용할 수 있나요?
 예, 여러 페이지 번호를 지정할 수 있습니다.`PageNumbers` 여러 페이지에 워터마크를 적용하려면 배열을 사용하세요.
### 비밀번호로 워터마크를 어떻게 보호하나요?
 설정을 통해 비밀번호로 워터마크를 보호할 수 있습니다.`Password` 에 있는 재산`WordProcessingWatermarkPagesOptions`.
### 워터마크의 모양을 사용자 정의할 수 있습니까?
전적으로! 필요에 맞게 워터마크의 텍스트, 글꼴, 색상, 크기 및 기타 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Watermark에 대한 임시 라이센스는 어디서 얻을 수 있나요?
 임시면허를 취득하실 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).