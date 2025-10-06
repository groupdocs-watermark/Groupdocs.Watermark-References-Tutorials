---
title: PDF의 XObject에 워터마크 추가
linktitle: PDF의 XObject에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 PDF의 XObject에 워터마크를 추가하는 방법을 알아보세요. 쉬운 구현을 위해 단계별 가이드를 따르세요.
weight: 20
url: /ko/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# PDF의 XObject에 워터마크 추가

## 소개
PDF 워터마킹은 문서를 무단 사용으로부터 보호하기 위한 중요한 단계입니다. .NET용 Groupdocs.Watermark를 사용하면 PDF 내의 XObject에 워터마크를 추가하는 것이 그 어느 때보다 쉬워졌습니다. 이 튜토리얼에서는 PDF 문서에 워터마크를 자신있게 적용할 수 있도록 프로세스를 단계별로 안내합니다. 시작하자!
## 전제조건
튜토리얼을 시작하기 전에 원활하게 따라하는 데 필요한 모든 것이 갖추어져 있는지 확인하십시오.
-  .NET용 Groupdocs.Watermark: 다음에서 최신 버전을 다운로드하여 설치하세요.[여기](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: 개발 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
- 개발 환경: Visual Studio 또는 .NET 개발을 지원하는 기타 IDE를 사용합니다.
-  임시 면허 취득:[임시 면허증](https://purchase.groupdocs.com/temporary-license/) 제품을 평가한다면.
이러한 전제 조건을 갖추고 나면 PDF에 워터마킹을 시작할 준비가 된 것입니다.
## 네임스페이스 가져오기
먼저 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. C# 프로젝트를 열고 다음 using 지시문을 추가합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 경로 설정
첫 번째 단계에는 문서의 경로를 설정하는 작업이 포함됩니다. PDF가 있는 경로와 워터마크가 있는 PDF를 저장할 위치를 정의하세요.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 그리고`"Your Document Directory"` 컴퓨터의 실제 경로와 함께.
## 2단계: PDF 로드 옵션 초기화
다음으로 PDF 로드 옵션을 초기화해야 합니다. 이는 PDF 콘텐츠를 올바르게 로드하는 데 중요합니다.
```csharp
var loadOptions = new PdfLoadOptions();
```
## 3단계: PDF 문서 로드
로드 옵션을 사용하여 PDF 문서를 로드합니다.`Watermarker` 수업.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 4단계: 워터마크 만들기
이제 PDF에 추가할 워터마크를 만들어야 합니다. 이 튜토리얼에서는 텍스트 워터마크를 만들어 보겠습니다.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## 5단계: XObject에 워터마크 추가
PDF 내의 각 페이지와 각 XObject를 반복하여 워터마크를 적용합니다.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // 이미지에 워터마크 추가
            xObject.Image.Add(watermark);
        }
    }
}
```
## 6단계: 워터마크가 있는 PDF 저장
마지막으로 워터마크가 있는 PDF를 지정된 출력 파일에 저장합니다.
```csharp
    watermarker.Save(outputFileName);
}
```
그리고 거기에 있습니다! 이제 PDF의 모든 XObject에 워터마크가 포함됩니다.
## 결론
 Groupdocs를 사용하여 PDF 문서에 워터마크를 추가하는 것은 추가 보안 계층을 제공하는 간단한 프로세스입니다. 이 튜토리얼에 설명된 단계를 따르면 문서가 무단 사용으로부터 보호될 수 있습니다. 기억하세요. 언제든지 다음을 참조할 수 있습니다.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) 더 자세한 정보와 고급 기능을 확인하세요.
## FAQ
### 텍스트 대신 이미지를 워터마크로 사용할 수 있나요?
예, .NET용 Groupdocs.Watermark는 텍스트 및 이미지 워터마크를 모두 지원합니다.
### Groupdocs.Watermark를 구매하지 않고 어떻게 테스트할 수 있나요?
 당신은 사용할 수 있습니다[임시 면허증](https://purchase.groupdocs.com/temporary-license/) 제품을 평가합니다.
### 워터마크의 모양을 사용자 정의할 수 있습니까?
전적으로! 글꼴, 크기, 회전 각도 등을 사용자 정의할 수 있습니다.
### Groupdocs.Watermark는 다른 문서 형식을 지원합니까?
예, Word, Excel, PowerPoint를 포함한 다양한 형식을 지원합니다.
### 문제가 발생하면 어디서 지원을 받을 수 있나요?
 에서 지원을 받으실 수 있습니다.[Groupdocs 포럼](https://forum.groupdocs.com/c/watermark/19).