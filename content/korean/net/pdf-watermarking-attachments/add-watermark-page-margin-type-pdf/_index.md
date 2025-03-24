---
title: PDF에 페이지 여백 유형으로 워터마크 추가
linktitle: PDF에 페이지 여백 유형으로 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET을 사용하여 PDF에 페이지 여백 유형의 워터마크를 추가하는 방법을 알아보세요. 문서를 손쉽게 보호하세요.
weight: 21
url: /ko/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---

# PDF에 페이지 여백 유형으로 워터마크 추가

## 소개
오늘날의 디지털 시대에는 문서 보안이 그 어느 때보다 중요합니다. 문서의 무결성과 신뢰성을 보장하는 한 가지 방법은 워터마크를 추가하는 것입니다. .NET용 Groupdocs.Watermark는 이 프로세스를 쉽게 만들 수 있도록 설계된 뛰어난 도구입니다. 이 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF에 페이지 여백 유형의 워터마크를 추가하는 단계를 안내합니다.
## 전제조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
-  .NET용 Groupdocs.Watermark: 다운로드 및 설치[최신 버전](https://releases.groupdocs.com/Watermark/net/) .NET용 Groupdocs.Watermark.
- 개발 환경: Visual Studio와 같은 .NET 개발 환경입니다.
- C#에 대한 기본 지식: C# 프로그래밍 언어에 익숙합니다.
- PDF 문서: 워터마크를 추가하려는 PDF 문서입니다.
## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. 이러한 네임스페이스는 Groupdocs 기능에 대한 액세스를 제공합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
이제 프로세스를 관리 가능한 단계로 나누어 보겠습니다. PDF 문서에 워터마크를 추가하려면 각 단계를 주의 깊게 따르십시오.
## 1단계: 문서 경로 및 출력 디렉터리 설정
먼저, 문서 경로와 워터마크가 있는 PDF가 저장될 출력 디렉터리를 지정해야 합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2단계: PDF 문서 로드
 다음으로, 다음을 사용하여 PDF 문서를 로드합니다.`PdfLoadOptions` 수업. 이 클래스를 사용하면 PDF를 로드하는 데 필요한 옵션을 지정할 수 있습니다.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 3단계: 텍스트 워터마크 만들기
이제 워터마크를 만들 차례입니다. 이 예에서는 글꼴, 크기, 정렬과 같은 특정 속성을 사용하여 텍스트 워터마크를 만듭니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4단계: 페이지 여백 유형 설정
 워터마크의 위치를 적절하게 지정하려면 페이지 여백 유형을 설정해야 합니다. 여기서는 페이지 여백 유형을 다음으로 설정합니다.`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## 5단계: 워터마크 추가 및 저장
마지막으로 문서에 워터마크를 추가하고 수정된 PDF를 지정된 출력 디렉터리에 저장합니다.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## 결론
그리고 거기에 있습니다! 다음 단계를 수행하면 .NET용 Groupdocs.Watermark를 사용하여 PDF 문서에 특정 페이지 여백 유형의 워터마크를 쉽게 추가할 수 있습니다. 이는 문서를 보호하는 데 도움이 될 뿐만 아니라 문서의 신뢰성도 보장합니다. 기밀 보고서, 법률 문서, 창작물 등 무엇을 처리하든 워터마킹은 콘텐츠를 보호하는 간단하면서도 효과적인 방법입니다.
## FAQ
### .NET용 Groupdocs.Watermark란 무엇입니까?
.NET용 Groupdocs.Watermark는 프로그래밍 방식으로 다양한 문서 형식에 워터마크를 추가하기 위한 강력한 라이브러리입니다. 이미지, 텍스트 등을 지원하므로 광범위한 사용자 정의가 가능합니다.
### 이 방법을 사용하여 다른 문서 유형에 워터마크를 표시할 수 있습니까?
예, .NET용 Groupdocs.Watermark는 Word, Excel, PowerPoint 및 이미지를 포함한 광범위한 문서 형식을 지원합니다. 프로세스는 유사하지만 다양한 옵션과 클래스가 포함될 수 있습니다.
### .NET용 Groupdocs.Watermark 무료 평가판을 받으려면 어떻게 해야 합니까?
 당신은 할 수 있습니다[무료 평가판 다운로드](https://releases.groupdocs.com/) Groupdocs 웹사이트에서 라이브러리의 특징과 기능을 살펴보세요.
### 워터마크의 모양을 사용자 정의할 수 있습니까?
전적으로! 워터마크의 글꼴, 크기, 색상, 불투명도, 정렬 및 기타 속성을 필요에 맞게 사용자 정의할 수 있습니다.
### .NET용 Groupdocs.Watermark에 대한 지원은 어디서 받을 수 있나요?
 지원을 받으려면 다음을 방문하세요.[Groupdocs 워터마크 지원 포럼](https://forum.groupdocs.com/c/watermark/19) 커뮤니티와 Groupdocs 팀에 질문을 하고 도움을 받을 수 있는 곳입니다.