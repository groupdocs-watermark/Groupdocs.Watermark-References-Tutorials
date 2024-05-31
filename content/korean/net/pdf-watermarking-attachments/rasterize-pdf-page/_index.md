---
title: PDF 페이지 래스터화
linktitle: PDF 페이지 래스터화
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET으로 문서 보안을 강화하세요. PDF 및 기타 형식에 워터마크를 원활하게 추가하세요.
type: docs
weight: 28
url: /ko/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## 소개
.NET용 GroupDocs.Watermark는 개발자가 PDF, Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식에 워터마크를 원활하게 추가할 수 있는 강력한 API입니다. 직관적인 인터페이스와 광범위한 기능을 갖춘 GroupDocs.Watermark는 문서에 텍스트 또는 이미지 워터마크를 추가하는 프로세스를 단순화하여 사용자가 지적 재산을 보호하고 문서 보안을 손쉽게 강화할 수 있도록 해줍니다.
## 전제조건
.NET용 GroupDocs.Watermark를 사용하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. 설치: 다음에서 .NET용 GroupDocs.Watermark를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/Watermark/net/).
2.  라이센스: .NET용 GroupDocs.Watermark 라이센스를 취득합니다. 평가 목적으로 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/) , 또는 다음 사이트에서 정식 라이센스를 구매하세요.[구매 페이지](https://purchase.groupdocs.com/buy).
3. .NET Framework: 개발 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
4. 문서: 워터마크를 추가할 문서를 준비합니다.

## 네임스페이스 가져오기
.NET용 GroupDocs.Watermark 사용을 시작하려면 필요한 네임스페이스를 프로젝트로 가져옵니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 귀하의 코드는 여기에 있습니다
}
```
## 2단계: 워터마크 초기화
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## 3단계: 워터마크 추가
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## 4단계: 페이지 래스터화
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## 5단계: 문서 저장
```csharp
watermarker.Save(outputFileName);
```

## 결론
결론적으로, .NET용 GroupDocs.Watermark는 PDF 및 기타 문서 형식에 워터마크를 추가하기 위한 완벽한 솔루션을 제공합니다. 위에 설명된 단계별 가이드를 따르면 개발자는 PDF 페이지를 효율적으로 래스터화하고 문서 보안을 쉽게 강화할 수 있습니다.
## FAQ
### GroupDocs.Watermark는 PDF 이외의 다른 문서 형식과 호환됩니까?
예, GroupDocs.Watermark는 Word, Excel, PowerPoint, Visio 등을 포함한 광범위한 문서 형식을 지원합니다.
### 문서에 추가된 워터마크의 모양을 사용자 정의할 수 있나요?
전적으로! GroupDocs.Watermark는 텍스트 및 이미지 워터마크에 대한 광범위한 사용자 정의 옵션을 제공하므로 사용자는 기본 설정에 따라 글꼴, 크기, 색상, 불투명도 및 위치를 조정할 수 있습니다.
### GroupDocs.Watermark는 개인용 및 상업용 모두에 적합합니까?
예, GroupDocs.Watermark는 개인 및 기업 요구 사항을 모두 충족할 수 있는 유연한 라이센스 옵션을 제공하므로 개인 프로젝트는 물론 대규모 상업 응용 프로그램에도 적합합니다.
### GroupDocs.Watermark는 개발자를 위한 기술 지원을 제공합니까?
예, 개발자는 GroupDocs.Watermark 포럼을 통해 포괄적인 기술 지원에 액세스하여 도움을 구하고, 경험을 공유하고, 동료 개발자와 교류할 수 있습니다.
### 구매하기 전에 GroupDocs.Watermark를 사용해 볼 수 있나요?
틀림없이! GroupDocs.Watermark의 무료 평가판을 다음 사이트에서 이용할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/), 구매를 결정하기 전에 특징과 기능을 탐색할 수 있습니다.