---
title: PDF의 모든 첨부 파일에 워터마크 추가
linktitle: PDF의 모든 첨부 파일에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF 첨부 파일에 워터마크를 추가하는 방법을 알아보세요. 사용자 정의 워터마크로 문서를 쉽게 보호하세요.
weight: 16
url: /ko/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
type: docs
---
# PDF의 모든 첨부 파일에 워터마크 추가

## 소개
PDF 첨부 파일에 워터마크를 추가하는 것은 특히 보안이나 브랜딩을 보장할 때 문서 관리에서 중요한 단계가 될 수 있습니다. .NET용 GroupDocs.Watermark는 PDF 파일에 워터마크를 원활하게 삽입하기 위한 포괄적인 솔루션을 제공합니다. 이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서 내의 모든 첨부 파일에 워터마크를 추가하는 과정을 안내합니다.
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: 아직 설치하지 않은 경우 다음 위치에서 .NET용 GroupDocs.Watermark를 다운로드하여 설치하세요.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 호환 IDE를 사용하여 적합한 개발 환경을 설정합니다.
3. PDF 문서: 워터마크를 추가할 첨부 파일과 함께 워터마크를 추가할 PDF 문서를 준비합니다.

## 네임스페이스 가져오기
코드를 살펴보기 전에 .NET용 GroupDocs.Watermark 기능에 액세스하는 데 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 문서 경로 및 출력 디렉터리 정의
먼저 입력 PDF 문서의 경로와 워터마크가 있는 문서가 저장될 디렉터리를 정의합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2단계: 로드 옵션 및 워터마크 초기화
다음으로 PDF 문서의 로드 옵션을 초기화하고 텍스트 워터마크를 만듭니다.
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## 3단계: 문서 및 첨부 파일 로드
PDF 문서를 로드하고 첨부 파일을 반복합니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## 4단계: 첨부 파일 지원 확인
첨부된 파일이 GroupDocs.Watermark에서 지원되는지 확인하세요.
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## 5단계: 첨부 파일에 워터마크 추가
첨부된 문서를 로드하고 워터마크를 추가하세요.
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## 6단계: 변경 사항 저장
마지막으로 워터마크가 있는 PDF 문서의 변경 사항을 저장합니다.
```csharp
    watermarker.Save(outputFileName);
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서 내의 모든 첨부 파일에 워터마크를 추가하는 방법을 살펴보았습니다. 단계별 가이드를 따르면 워터마크를 PDF 파일에 원활하게 통합하여 문서 보안과 브랜딩을 보장할 수 있습니다.
## FAQ
### 워터마크의 모양을 사용자 정의할 수 있나요?
예. 요구 사항에 따라 워터마크의 텍스트, 글꼴, 크기, 색상, 위치 등 다양한 측면을 사용자 정의할 수 있습니다.
### GroupDocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, GroupDocs.Watermark는 Microsoft Word, Excel, PowerPoint, Visio, Outlook 및 이미지를 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
예, 웹사이트에서 무료 평가판을 다운로드하여 GroupDocs.Watermark의 기능을 탐색할 수 있습니다.
### 단일 문서에 여러 개의 워터마크를 추가할 수 있나요?
물론, GroupDocs.Watermark를 사용하면 텍스트, 이미지, 주석을 포함한 여러 워터마크를 동시에 추가하여 문서 보안과 브랜딩을 강화할 수 있습니다.
### GroupDocs.Watermark 사용자에게 기술 지원이 제공됩니까?
예, GroupDocs는 포럼과 전용 지원 채널을 통해 포괄적인 기술 지원을 제공하여 사용자가 직면할 수 있는 모든 질문이나 문제를 지원합니다.