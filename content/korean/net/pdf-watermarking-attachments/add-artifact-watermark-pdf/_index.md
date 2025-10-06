---
title: PDF에 아티팩트 워터마크 추가
linktitle: PDF에 아티팩트 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 손쉽게 PDF 파일에 아티팩트 워터마크를 추가하는 방법을 알아보세요. 문서를 쉽게 보호하세요.
weight: 11
url: /ko/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
type: docs
---
# PDF에 아티팩트 워터마크 추가

## 소개
PDF 파일에 워터마크를 추가하는 것은 문서 관리의 중요한 측면이며, 특히 지적 재산이나 브랜딩 문서를 보호하는 경우 더욱 그렇습니다. .NET용 Groupdocs.Watermark는 PDF 파일에 워터마크를 쉽게 추가할 수 있는 강력한 솔루션을 제공합니다. 이 튜토리얼에서는 PDF 파일에 아티팩트 워터마크를 추가하는 과정을 단계별로 안내합니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 Groupdocs.Watermark: 다음에서 .NET용 Groupdocs.Watermark를 다운로드하여 설치하세요.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: .NET 개발 환경을 설정합니다.
3. PDF 문서: 워터마크를 추가할 PDF 문서를 준비합니다.
4. 출력 디렉터리: 워터마크가 표시된 PDF 파일을 저장할 디렉터리를 만듭니다.

## 네임스페이스 가져오기
시작하려면 C# 프로젝트에서 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Common;
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
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## 3단계: 텍스트 워터마크 추가
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## 4단계: 이미지 워터마크 추가
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## 5단계: 워터마크가 있는 PDF 저장
```csharp
watermarker.Save(outputFileName);
```

## 결론
이 자습서에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF 파일에 아티팩트 워터마크를 추가하는 방법을 배웠습니다. 다음 단계를 따르면 워터마킹 기능을 .NET 애플리케이션에 원활하게 통합하여 문서의 보안과 무결성을 보장할 수 있습니다.
## FAQ
### 텍스트 워터마크의 모양을 사용자 정의할 수 있나요?
예. 원하는 대로 텍스트 워터마크의 글꼴, 크기, 색상, 정렬 등 다양한 측면을 사용자 정의할 수 있습니다.
### Groupdocs.Watermark는 다른 문서 형식에 워터마크 추가를 지원합니까?
예, Groupdocs.Watermark는 Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식에 워터마크 추가를 지원합니다.
### .NET용 Groupdocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### Groupdocs.Watermark와 관련된 문제나 쿼리에 대한 지원을 어떻게 받을 수 있나요?
 Groupdocs 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark를 상업적 목적으로 사용할 수 있습니까?
예, 다음에서 상업적 사용을 위한 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy).