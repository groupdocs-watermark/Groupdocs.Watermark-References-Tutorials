---
title: PDF 이미지에 워터마크 추가
linktitle: PDF 이미지에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: 자세한 단계별 튜토리얼을 통해 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서의 이미지에 워터마크를 추가하는 방법을 알아보세요. PDF를 쉽게 보호하세요.
weight: 19
url: /ko/net/pdf-watermarking-attachments/add-watermark-images-pdf/
type: docs
---
# PDF 이미지에 워터마크 추가

## 소개
PDF 문서 내의 이미지에 워터마크를 추가하는 것은 지적 재산을 보호하거나 문서의 신뢰성을 보장하는 데 필수적일 수 있습니다. .NET용 GroupDocs.Watermark를 사용하면 이 작업을 효율적이고 쉽게 수행할 수 있습니다. 이 튜토리얼은 환경 설정부터 워터마크 추가, 최종 문서 저장까지 프로세스의 각 단계를 안내합니다. 뛰어들어보자!
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1. Visual Studio: .NET 애플리케이션용 IDE(통합 개발 환경)인 Visual Studio를 설치합니다.
2.  .NET용 GroupDocs.Watermark: 다음에서 .NET용 GroupDocs.Watermark 라이브러리를 다운로드하고 설치합니다.[릴리스 페이지](https://releases.groupdocs.com/Watermark/net/).
3. PDF 문서: 워터마킹 기능을 테스트할 수 있는 이미지가 포함된 PDF 문서를 준비하세요.
4.  임시 면허 취득:[임시 면허증](https://purchase.groupdocs.com/temporary-license/) 제품을 평가한다면.
## 네임스페이스 가져오기
먼저 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. 여기에는 PDF 문서 및 워터마크 작업에 필요한 핵심 네임스페이스가 포함됩니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 경로 및 출력 디렉터리 설정
시작하려면 입력 문서의 경로와 워터마크가 있는 문서가 저장될 출력 디렉터리를 정의합니다. 이 단계는 프로그램이 소스 문서를 찾을 위치와 처리된 파일을 저장할 위치를 알고 있는지 확인하는 데 중요합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2단계: PDF 문서 로드
 다음으로 다음을 사용하여 PDF 문서를 로드해야 합니다.`PdfLoadOptions`. 이 클래스를 사용하면 필요한 경우 비밀번호 보호와 같은 PDF 로드 옵션을 지정할 수 있습니다.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마킹 코드가 여기에 표시됩니다.
}
```
## 3단계: 워터마크 만들기
이제 워터마크를 초기화합니다. 이 예에서는 "보호된 이미지"라는 텍스트 워터마크를 생성합니다. 필요에 따라 글꼴, 정렬, 회전 및 배율을 사용자 정의하세요.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## 4단계: PDF 콘텐츠에 액세스
PDF 문서의 내용을 검색합니다. 특히 PDF 내의 이미지에 액세스해야 합니다. 여기서는 첫 번째 페이지에 중점을 두고 있지만 필요에 따라 이를 다른 페이지로 확장할 수 있습니다.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// 첫 페이지에서 모든 이미지 가져오기
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## 5단계: 이미지에 워터마크 적용
첫 번째 페이지에 있는 각 이미지를 반복하고 워터마크를 적용하세요. 이렇게 하면 지정된 페이지의 모든 이미지에 워터마크가 적용됩니다.
```csharp
// 발견된 모든 이미지에 워터마크 추가
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## 6단계: 워터마크가 있는 문서 저장
마지막으로 워터마크가 있는 PDF를 지정된 출력 디렉터리에 저장합니다. 이 단계에서는 변경 사항을 새 파일에 기록하여 프로세스를 마무리합니다.
```csharp
watermarker.Save(outputFileName);
```
## 결론
그리고 거기에 있습니다! GroupDocs for .NET을 사용하여 PDF 내의 이미지에 워터마크를 추가하는 것은 문서의 보안과 신뢰성을 크게 향상시킬 수 있는 간단한 프로세스입니다. 다음 단계를 따르면 지적 재산을 보호하고 문서를 안전하게 보호할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark란 무엇입니까?
.NET용 GroupDocs.Watermark는 개발자가 PDF를 포함한 다양한 문서 형식의 워터마크를 추가, 검색 및 제거할 수 있는 포괄적인 라이브러리입니다.
### GroupDocs.Watermark를 사용하여 텍스트와 이미지 워터마크를 모두 추가할 수 있나요?
예, GroupDocs.Watermark는 텍스트와 이미지 워터마크를 모두 지원하므로 다양한 유형의 워터마킹 요구 사항에 유연성을 제공합니다.
### PDF의 여러 페이지에 워터마킹을 할 수 있나요?
전적으로! PDF의 각 페이지를 반복하여 각 페이지의 이미지에 워터마크를 적용할 수 있습니다.
### .NET용 GroupDocs.Watermark를 사용하려면 라이센스가 필요합니까?
 예, 라이센스가 필요합니다. 당신은 얻을 수 있습니다[임시 면허증](https://purchase.groupdocs.com/temporary-license/) 평가 목적으로.
### .NET용 GroupDocs.Watermark에 대한 추가 문서는 어디에서 찾을 수 있습니까?
 다음에서 포괄적인 문서를 찾을 수 있습니다.[GroupDocs.Watermark 문서 페이지](https://tutorials.groupdocs.com/Watermark/net/).