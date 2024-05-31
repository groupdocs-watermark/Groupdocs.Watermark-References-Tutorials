---
title: PDF에 주석 워터마크 추가
linktitle: PDF에 주석 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF 문서에 주석 워터마크를 쉽게 추가하는 방법을 알아보세요. 문서 브랜딩과 보안을 쉽게 강화하세요.
type: docs
weight: 10
url: /ko/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---
## 소개
문서 관리 영역에서 PDF 파일에 워터마크를 추가하는 것은 특히 브랜딩, 보안 및 문서 식별 목적에서 중요한 측면입니다. GroupDocs.Watermark for .NET은 PDF를 포함한 다양한 문서 형식에 워터마크를 원활하게 통합할 수 있게 해주는 강력한 라이브러리입니다. 이 튜토리얼에서는 GroupDocs.Watermark for .NET에서 제공하는 기능을 활용하여 PDF 문서에 주석 워터마크를 추가하는 과정을 단계별로 자세히 살펴보겠습니다.
## 전제조건
튜토리얼을 진행하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 .NET 라이브러리용 GroupDocs.Watermark를 다운로드하고 설치합니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET IDE와 같은 적합한 개발 환경을 설정합니다.
3. C#의 기본 이해: C# 프로그래밍 언어 기본 사항을 숙지하는 것이 좋습니다.

## 필요한 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져옵니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: PDF 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 2단계: 워터마크 옵션 정의
```csharp
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## 3단계: 텍스트 워터마크 추가
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## 4단계: 이미지 워터마크 추가
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## 5단계: 워터마크가 포함된 문서 저장
```csharp
	watermarker.Save(outputFileName);
}
```

## 결론
결론적으로, .NET용 GroupDocs.Watermark는 프로그래밍 방식으로 PDF 문서에 주석 워터마크를 추가하기 위한 포괄적인 솔루션을 제공합니다. 설명된 단계를 따르면 사용자는 텍스트 및 이미지 워터마크를 PDF 파일에 원활하게 통합하여 문서 브랜딩 및 보안을 강화할 수 있습니다.
## FAQ
### GroupDocs.Watermark는 PDF 이외의 다른 문서 형식과 호환됩니까?
예, GroupDocs.Watermark는 Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 워터마크의 모양을 사용자 정의할 수 있나요?
전적으로! GroupDocs.Watermark는 텍스트와 이미지 워터마크 모두에 대한 광범위한 사용자 정의 옵션을 제공하므로 사용자는 크기, 위치, 불투명도 및 기타 매개변수를 조정할 수 있습니다.
### GroupDocs.Watermark는 문서 일괄 처리에 적합합니까?
틀림없이! GroupDocs.Watermark는 효율적인 일괄 처리 기능을 제공하므로 사용자는 여러 문서에 워터마크를 동시에 적용할 수 있습니다.
### GroupDocs.Watermark는 .NET Core 개발을 지원합니까?
예, GroupDocs.Watermark는 .NET Core를 지원하므로 개발자는 워터마킹 기능을 크로스 플랫폼 애플리케이션에 통합할 수 있습니다.
### GroupDocs.Watermark 사용자에게 기술 지원이 제공됩니까?
예, GroupDocs는 전용 포럼과 고객 서비스 채널을 통해 포괄적인 기술 지원을 제공합니다.