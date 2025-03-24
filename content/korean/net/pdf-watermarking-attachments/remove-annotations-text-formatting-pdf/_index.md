---
title: PDF에서 특정 텍스트 형식의 주석 제거
linktitle: PDF에서 특정 텍스트 형식의 주석 제거
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET을 사용하여 PDF 문서에서 특정 텍스트 형식의 주석을 제거하는 방법을 알아보세요.
weight: 30
url: /ko/net/pdf-watermarking-attachments/remove-annotations-text-formatting-pdf/
---

# PDF에서 특정 텍스트 형식의 주석 제거

## 소개
이 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF 문서에서 특정 텍스트 형식의 주석을 제거하는 과정을 안내합니다. 이 라이브러리는 다양한 형식의 워터마크, 주석 및 기타 문서 요소 작업을 위한 강력한 기능을 제공합니다.
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET 라이브러리용 Groupdocs.Watermark: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: 컴퓨터에 설정된 .NET 개발 환경입니다.
3. PDF 문서: 수정하려는 주석이 포함된 PDF 문서가 있습니다.

## 네임스페이스 가져오기
먼저 필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using System.IO;
using System;
```
## 1단계: PDF 문서 로드
```csharp
string documentPath = "YourDocumentPath";
string outputDirectory = "YourDocumentDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## 2단계: PDF 콘텐츠 가져오기 및 페이지 반복
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfPage page in pdfContent.Pages)
    {
```
## 3단계: 주석 반복 및 텍스트 형식 확인
```csharp
        for (int i = page.Annotations.Count - 1; i >= 0; i--)
        {
            foreach (FormattedTextFragment fragment in page.Annotations[i].FormattedTextFragments)
            {
```
## 4단계: 특정 텍스트 형식으로 주석 제거
```csharp
                if (fragment.Font.FamilyName == "Verdana")
                {
                    page.Annotations.RemoveAt(i);
                    break;
                }
            }
        }
    }
```
## 5단계: 수정된 PDF 문서 저장
```csharp
    watermarker.Save(outputFileName);
}
```
이제 .NET용 Groupdocs.Watermark를 사용하여 PDF 문서에서 특정 텍스트 형식의 주석을 성공적으로 제거했습니다.

## 결론
.NET용 Groupdocs.Watermark는 PDF 문서의 주석 및 기타 요소 작업을 위한 편리한 솔루션을 제공합니다. 이 튜토리얼을 따르면 특정 텍스트 형식을 기반으로 주석을 쉽게 조작하여 PDF 파일의 가독성과 모양을 향상시킬 수 있습니다.
## FAQ
### 다른 문서 형식과 함께 .NET용 Groupdocs.Watermark를 사용할 수 있습니까?
예, Groupdocs.Watermark는 DOCX, PPTX, XLSX, PDF 등을 포함한 다양한 문서 형식을 지원합니다.
### .NET용 Groupdocs.Watermark에 대한 무료 평가판이 있습니까?
 예, 다음에서 .NET용 Groupdocs.Watermark 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 Groupdocs.Watermark에 대한 설명서는 어디에서 찾을 수 있습니까?
 자세한 문서와 API 참조를 찾을 수 있습니다.[여기](https://tutorials.groupdocs.com/Watermark/net/).
### Groupdocs.Watermark와 관련된 문제나 쿼리에 대한 지원을 어떻게 받을 수 있나요?
 Groupdocs.Watermark 포럼에 질문이나 문제를 게시할 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19).
### .NET용 Groupdocs.Watermark의 임시 라이센스를 구입할 수 있습니까?
 예, 다음에서 임시 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).