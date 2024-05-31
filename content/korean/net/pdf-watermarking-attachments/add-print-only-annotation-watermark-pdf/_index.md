---
title: PDF에 인쇄 전용 주석 워터마크 추가
linktitle: PDF에 인쇄 전용 주석 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF에 인쇄 전용 주석 워터마크를 추가하는 방법을 알아보세요. 손쉽게 문서 보안과 브랜딩을 강화하세요.
type: docs
weight: 13
url: /ko/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF에 인쇄 전용 주석 워터마크를 추가하는 과정을 자세히 살펴보겠습니다. 문서 워터마킹은 문서 보안 및 브랜딩의 중요한 측면이며 GroupDocs.Watermark는 .NET 개발자가 이를 달성할 수 있는 완벽한 솔루션을 제공합니다.
## 전제조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
- C# 프로그래밍 언어에 대한 기본 이해.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- 프로젝트에 설치된 .NET 라이브러리용 GroupDocs.Watermark.

## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
 먼저 워터마크를 추가하려는 PDF 문서를 로드해야 합니다. 바꾸다`"Your Document Path"` PDF 파일의 경로와`"Your Document Directory"` 출력 파일을 저장하려는 디렉토리를 사용하십시오.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마킹 코드가 여기에 추가됩니다
}
```
## 2단계: 워터마크 추가
다음으로, 원하는 텍스트와 글꼴을 사용하여 텍스트 워터마크 개체를 만듭니다. 세트`isPrintOnly` 에게`true` 보기 모드가 아닌 문서를 인쇄할 때만 워터마크가 표시되도록 합니다.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## 3단계: 워터마크 옵션 구성
워터마크를 추가해야 하는 페이지 색인 및 인쇄 전용 주석으로 지정하는 등 워터마크에 대한 옵션을 정의합니다.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## 4단계: 워터마크 적용
지정된 옵션을 사용하여 문서에 워터마크를 추가하고 출력 파일을 저장합니다.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서에 인쇄 전용 주석 워터마크를 추가하는 방법을 배웠습니다. 이를 통해 개발자는 문서 보안과 브랜딩을 쉽게 강화할 수 있습니다.
## FAQ
### GroupDocs.Watermark는 PDF 이외의 다른 문서 형식과 호환됩니까?
예, GroupDocs는 Word, Excel, PowerPoint 및 이미지와 같은 다양한 문서 형식을 지원합니다.
### 워터마크의 모양을 사용자 정의할 수 있나요?
확실히 GroupDocs.Watermark는 워터마크 텍스트, 글꼴, 색상, 크기 및 위치를 사용자 정의할 수 있는 광범위한 옵션을 제공합니다.
### GroupDocs.Watermark는 일괄 처리 기능을 제공합니까?
물론 개발자는 일괄 처리 기능을 사용하여 여러 문서에 동시에 워터마크를 표시할 수 있습니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
예, 제공된 링크에서 GroupDocs.Watermark의 무료 평가판에 액세스할 수 있습니다.
### GroupDocs.Watermark에 대한 기술 지원은 어떻게 받을 수 있나요?
제공된 지원 링크에 있는 GroupDocs.Watermark 포럼에서 기술 지원을 요청할 수 있습니다.