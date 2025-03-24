---
title: PDF에서 워터마크 제거
linktitle: PDF에서 워터마크 제거
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF 파일에서 워터마크를 제거하는 방법을 알아보세요. 전문적인 문서 편집을 위한 쉬운 단계.
weight: 34
url: /ko/net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## 소개
오늘날 디지털 시대에는 민감한 문서를 워터마크로 보호하는 것이 일반적인 관행입니다. 그러나 다양한 이유로 PDF 파일에서 워터마크를 제거해야 하는 경우가 있습니다. 문서를 편집하거나 단순히 프리젠테이션을 위한 클린 버전이 필요한 경우 .NET용 GroupDocs.Watermark는 PDF 파일에서 워터마크를 제거하기 위한 완벽한 솔루션을 제공합니다.
## 전제조건
.NET용 GroupDocs.Watermark를 사용하여 PDF 파일에서 워터마크를 제거하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: Visual Studio 또는 호환되는 IDE가 시스템에 설치되어 있습니다.
3. 워터마크가 있는 문서: 제거하려는 워터마크가 포함된 PDF 문서를 준비합니다.

## 네임스페이스 가져오기
C# 프로젝트에서 필요한 네임스페이스를 가져오는 것부터 시작합니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## 1단계: PDF 문서 로드
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
이 단계에서는 PDF 문서의 경로와 출력 파일을 저장할 디렉터리를 지정합니다.
## 2단계: 워터마커 및 검색 기준 초기화
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
PDF 문서 경로 및 로드 옵션을 사용하여 워터마커 개체를 초기화합니다. 그런 다음 제거하려는 워터마크에 대한 검색 기준을 정의합니다. 이미지나 텍스트를 기반으로 워터마크를 검색할 수 있습니다.
## 3단계: 워터마크 검색 및 제거
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // 발견된 워터마크 모두 제거
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
정의된 검색 기준에 따라 PDF 문서의 첫 번째 페이지에서 가능한 워터마크를 검색합니다. 그런 다음 가능한 워터마크 모음을 반복하여 하나씩 제거합니다. 마지막으로 수정된 PDF 문서를 워터마크 없이 저장하세요.

## 결론
PDF 파일에서 워터마크를 제거하는 것은 문서 편집부터 프레젠테이션 준비까지 다양한 시나리오에서 중요한 작업입니다. .NET용 GroupDocs.Watermark를 사용하면 간단한 C# 코드를 사용하여 PDF 파일에서 워터마크를 손쉽게 제거하여 문서를 깔끔하고 전문적으로 유지할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 모든 버전의 Visual Studio와 호환됩니까?
예, .NET용 GroupDocs.Watermark는 Visual Studio 2019 및 Visual Studio 2022를 포함한 모든 버전의 Visual Studio와 호환됩니다.
### .NET용 GroupDocs.Watermark를 사용하여 단일 PDF 문서에서 여러 워터마크를 제거할 수 있습니까?
예, 적절한 검색 기준을 지정하여 단일 PDF 문서에서 여러 워터마크를 검색하고 제거할 수 있습니다.
### .NET용 GroupDocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, .NET용 GroupDocs.Watermark는 Word 문서, Excel 스프레드시트, PowerPoint 프레젠테이션 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 .NET용 GroupDocs.Watermark 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Watermark에 대한 추가 지원은 어디서 찾을 수 있나요?
 추가 지원을 받으려면 GroupDocs.Watermark 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/watermark/19).