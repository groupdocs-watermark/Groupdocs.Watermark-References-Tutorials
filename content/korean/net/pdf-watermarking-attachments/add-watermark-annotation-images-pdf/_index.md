---
title: PDF의 주석 이미지에 워터마크 추가
linktitle: PDF의 주석 이미지에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 주석 이미지에 워터마크를 추가하여 PDF 문서를 보호하는 방법을 알아보세요.
weight: 17
url: /ko/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
type: docs
---
# PDF의 주석 이미지에 워터마크 추가

## 소개
이 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF 문서의 주석 이미지에 워터마크를 추가하는 방법을 살펴보겠습니다. 워터마킹은 문서를 무단 사용이나 배포로부터 보호하는 데 중요합니다. 이 단계별 가이드를 따르면 PDF의 주석 이미지에 텍스트 워터마크를 효과적으로 적용하는 방법을 배울 수 있습니다.
## 전제조건
계속하기 전에 다음 사항을 확인하세요.
1. C# 프로그래밍 언어에 대한 기본 이해.
2. .NET 라이브러리용 Groupdocs.Watermark를 설치했습니다.
3. Visual Studio와 같은 개발 환경에 액세스합니다.
4. 워터마크를 추가할 주석 이미지가 포함된 PDF 문서입니다.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 코드로 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## 2단계: PDF 콘텐츠 가져오기 및 워터마크 초기화
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // 이미지 또는 텍스트 워터마크 초기화
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## 3단계: PDF 페이지 및 주석 이미지 반복
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // 이미지에 워터마크 추가
                annotation.Image.Add(watermark);
            }
        }
    }
```
## 4단계: 워터마크가 포함된 문서 저장
```csharp
    watermarker.Save(outputFileName);
}
```
이 단계를 실행하면 PDF 문서에 지정된 워터마크가 주석 이미지에 추가됩니다.

## 결론
PDF의 주석 이미지에 워터마크를 추가하는 것은 문서의 무결성을 보호하고 오용되지 않도록 하는 데 필수적입니다. .NET용 Groupdocs.Watermark를 사용하면 이 프로세스가 간단하고 효율적이 되어 PDF 파일을 효과적으로 보호할 수 있습니다.
## FAQ
### 동일한 PDF 문서에 여러 워터마크를 추가할 수 있나요?
예, .NET용 Groupdocs.Watermark를 사용하여 동일한 PDF 문서에 여러 워터마크를 추가할 수 있습니다.
### Groupdocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, Groupdocs는 Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다.
### 워터마크의 모양을 사용자 정의할 수 있습니까?
물론, 귀하는 원하는 대로 워터마크의 텍스트, 글꼴, 색상, 크기 및 위치를 사용자 정의할 수 있습니다.
### Groupdocs.Watermark를 사용하여 PDF 문서에서 워터마크를 제거할 수 있습니까?
예, Groupdocs.Watermark는 PDF 문서에서 워터마크를 손쉽게 제거하는 기능을 제공합니다.
### .NET용 Groupdocs.Watermark에 사용할 수 있는 무료 평가판이 있습니까?
예, 웹사이트에서 .NET용 Groupdocs.Watermark 무료 평가판을 이용할 수 있습니다.