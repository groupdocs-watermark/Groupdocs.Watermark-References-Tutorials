---
title: PDF 문서 래스터화
linktitle: PDF 문서 래스터화
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF 문서를 래스터화하는 방법을 알아보세요. 손쉽게 문서 보안과 시각적 매력을 강화하세요.
weight: 27
url: /ko/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## 소개
문서 관리 및 조작 영역에서 .NET용 GroupDocs.Watermark는 다양한 문서 형식의 워터마크를 추가, 제거 및 검색할 수 있는 강력한 기능을 제공하는 강력한 도구로 우뚝 서 있습니다. 저작권 표시로 문서를 보호하든, 브랜딩을 위한 기업 로고를 추가하거나, 단순히 스탬프로 문서에 주석을 달든, GroupDocs.Watermark는 직관적인 API와 광범위한 기능 세트를 통해 프로세스를 단순화합니다.
## 전제조건
.NET용 GroupDocs.Watermark를 사용하여 워터마킹의 세계를 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
### 1. .NET 프레임워크 설치
개발 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요. Microsoft 웹사이트에서 다운로드하거나 원하는 패키지 관리자를 사용할 수 있습니다.
#### 1단계: .NET Framework 다운로드
Microsoft .NET Framework 다운로드 페이지를 방문하세요.
#### 2단계: .NET Framework 설치
다운로드 페이지에 제공된 설치 지침에 따라 시스템에 .NET Framework를 설치하십시오.
### 2. GroupDocs.Watermark 라이센스 획득
GroupDocs.Watermark의 모든 기능을 활용하려면 유효한 라이센스가 필요합니다. 라이센스를 구매하거나 평가 목적으로 임시 라이센스를 얻을 수 있습니다.
#### 1단계: 라이선스 받기
GroupDocs.Watermark 구매 페이지를 방문하세요.
#### 2단계: 임시 라이센스 구매 또는 획득
필요에 따라 적절한 라이선스 옵션을 선택하세요. 지속적인 사용을 위해 라이선스를 구매하거나 평가 목적으로 임시 라이선스를 획득하세요.

## 네임스페이스 가져오기
문서 워터마킹을 시작하기 전에 GroupDocs 기능에 원활하게 액세스하는 데 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

이제 모든 설정이 완료되었으므로 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서를 래스터화하는 방법을 살펴보겠습니다. 래스터화는 PDF 문서의 각 페이지를 PNG와 같은 래스터 이미지 형식으로 변환합니다.
## 1단계: 변수 초기화
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
"문서 경로" 및 "문서 디렉터리"를 각각 PDF 문서의 실제 경로와 원하는 출력 디렉터리로 바꾸십시오.
## 2단계: 문서 로드 및 워터마크 추가
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 이미지 또는 텍스트 워터마크 초기화
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // 먼저 모든 유형의 워터마크를 추가하세요.
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // 모든 페이지 래스터화
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // 모든 페이지의 콘텐츠가 래스터 이미지로 대체됩니다.
    watermarker.Save(outputFileName);
}
```
이 단계에서는 PDF 문서를 로드하고 텍스트, 글꼴, 정렬, 회전 각도, 크기 유형, 배율 및 불투명도와 같은 지정된 속성을 사용하여 텍스트 워터마크를 초기화합니다. 그런 다음 문서에 워터마크를 추가합니다. 다음으로 PDF 문서의 내용을 검색하고 모든 페이지를 100DPI 해상도의 PNG 형식으로 래스터화합니다. 마지막으로 수정된 문서를 래스터화된 콘텐츠와 함께 저장합니다.

## 결론
.NET용 GroupDocs.Watermark는 다양한 문서 형식에 워터마크를 쉽게 추가할 수 있는 포괄적인 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 PDF 문서를 효과적으로 래스터화하고 보안과 시각적 매력을 향상시킬 수 있습니다.
## FAQ
### GroupDocs.Watermark는 PDF 이외의 다른 문서 형식과 호환됩니까?
예, GroupDocs.Watermark는 Microsoft Word, Excel, PowerPoint, Visio, Outlook 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Watermark를 사용하여 추가된 워터마크의 모양을 사용자 정의할 수 있습니까?
전적으로! GroupDocs.Watermark는 텍스트, 글꼴, 색상, 크기, 불투명도, 회전 및 위치와 같은 워터마크 속성을 사용자 정의하기 위한 광범위한 옵션을 제공합니다.
### GroupDocs.Watermark는 일괄 처리를 지원합니까?
예, GroupDocs를 사용하면 일괄 모드에서 여러 문서를 쉽게 처리할 수 있으므로 대규모 파일 세트를 워터마킹하는 데 드는 시간과 노력을 절약할 수 있습니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
예, 웹사이트에서 GroupDocs.Watermark 무료 평가판을 다운로드하여 구매하기 전에 기능을 평가해 볼 수 있습니다.
### GroupDocs.Watermark에 대해 문제가 발생하거나 질문이 있는 경우 어떻게 도움을 받을 수 있습니까?
GroupDocs.Watermark 포럼을 방문하여 커뮤니티의 지원을 구하거나 GroupDocs 지원 팀에 도움을 요청할 수 있습니다.