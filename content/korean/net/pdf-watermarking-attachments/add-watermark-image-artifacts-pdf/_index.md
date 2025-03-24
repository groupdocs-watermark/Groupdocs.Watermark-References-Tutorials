---
title: PDF의 이미지 아티팩트에 워터마크 추가
linktitle: PDF의 이미지 아티팩트에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 개인화된 워터마크로 PDF 파일을 보호하세요. PDF 문서의 이미지 아티팩트에 텍스트 또는 이미지 워터마크를 쉽게 추가할 수 있습니다.
weight: 18
url: /ko/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서의 이미지 아티팩트에 워터마크를 추가하는 과정을 안내합니다. 다음 단계를 따르면 개인화된 워터마크를 사용하여 PDF 파일을 효율적으로 보호할 수 있습니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: 다음에서 .NET용 GroupDocs.Watermark 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 문서 경로: 워터마크를 추가하려는 PDF 문서의 경로를 가지고 있습니다.
3. 출력 디렉터리: 워터마크가 표시된 문서가 저장될 디렉터리를 만듭니다.

## 네임스페이스 가져오기
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 로드 및 워터마커 초기화
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 2단계: PDF 콘텐츠 가져오기 및 워터마크 추가
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// 이미지 또는 텍스트 워터마크 초기화
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// 이미지에 워터마크 추가
				artifact.Image.Add(watermark);
			}
		}
	}
```
## 3단계: 워터마크가 있는 문서 저장
```csharp
	watermarker.Save(outputFileName);
}
```

## 결론
.NET용 GroupDocs.Watermark를 사용하면 PDF 문서의 이미지 아티팩트에 워터마크를 추가하는 과정이 원활해집니다. 이 튜토리얼을 따르면 사용자 정의된 워터마크로 PDF 파일을 효율적으로 보호하여 보안과 신뢰성을 보장할 수 있습니다.
## FAQ
### 내 PDF 문서에 이미지와 텍스트 워터마크를 모두 추가할 수 있나요?
예, .NET용 GroupDocs.Watermark는 이미지와 텍스트 워터마크를 동시에 추가하는 것을 지원합니다.
### 문서에 추가할 수 있는 워터마크 수에 제한이 있나요?
아니요, 제한 없이 문서에 여러 개의 워터마크를 추가할 수 있습니다.
### 워터마크의 모양과 위치를 사용자 정의할 수 있나요?
물론, 워터마크의 모양, 위치, 속성을 완전히 제어할 수 있습니다.
### .NET용 GroupDocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다.
### 문서에서 워터마크를 제거하는 방법이 있나요?
예, .NET용 GroupDocs.Watermark는 필요한 경우 문서에서 워터마크를 제거하는 방법을 제공합니다.