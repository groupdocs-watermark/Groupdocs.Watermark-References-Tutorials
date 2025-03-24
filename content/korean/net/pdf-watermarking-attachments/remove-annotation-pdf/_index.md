---
title: PDF에서 주석 제거
linktitle: PDF에서 주석 제거
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 PDF에서 주석을 제거하는 방법을 알아보세요. 손쉽게 문서 가독성을 향상하세요.
weight: 29
url: /ko/net/pdf-watermarking-attachments/remove-annotation-pdf/
---

# PDF에서 주석 제거

## 소개
PDF 문서의 주석은 때때로 내용을 복잡하게 만들거나 문서의 가독성을 방해할 수 있습니다. .NET용 GroupDocs.Watermark를 사용하면 PDF 파일에서 주석을 쉽게 제거할 수 있습니다. 이 튜토리얼에서는 프로세스를 단계별로 안내합니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Watermark: .NET용 GroupDocs.Watermark를 설치했는지 확인하세요. 다음에서 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 문서 경로: 주석을 제거하려는 PDF 문서의 경로가 있습니다.
3. 출력 디렉터리: 수정된 문서가 저장될 디렉터리를 준비합니다.
4. .NET 환경: 제공된 코드를 실행하도록 .NET 환경이 설정되어 있는지 확인하세요.

## 네임스페이스 가져오기
먼저, .NET용 Watermark 기능에 액세스하는 데 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System.IO;
using System;
```
## 1단계: 문서 로드
제공된 문서 경로를 사용하여 PDF 문서를 로드하는 것부터 시작하세요.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 2단계: 주석 제거
이제 PDF 문서에서 주석을 제거해 보겠습니다. 주석을 제거하는 방법에는 인덱스 또는 참조라는 두 가지 옵션이 있습니다.
### 색인별로 주석 제거
색인별로 주석을 제거하려면 다음 안내를 따르세요.
```csharp
// 색인별로 주석 제거
pdfContent.Pages[0].Annotations.RemoveAt(0);
```
### 참조로 주석 제거
참조로 주석을 제거하려면 다음을 수행하십시오.
```csharp
// 참조로 주석 제거
pdfContent.Pages[0].Annotations.Remove(pdfContent.Pages[0].Annotations[0]);
```
## 3단계: 문서 저장
주석을 제거한 후 수정된 문서를 지정된 출력 디렉터리에 저장합니다.
```csharp
    watermarker.Save(outputFileName);
}
```

## 결론
PDF 문서에서 주석을 제거하는 것은 .NET용 GroupDocs.Watermark를 사용하는 간단한 프로세스입니다. 이 튜토리얼에 설명된 단계를 따르면 주석을 효율적으로 관리하고 PDF 파일의 가독성을 높일 수 있습니다.
## FAQ
### 여러 주석을 동시에 제거할 수 있나요?
예, .NET용 GroupDocs.Watermark를 사용하여 필요에 따라 주석을 반복하고 제거할 수 있습니다.
### GroupDocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, GroupDocs는 Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### 주석을 완전히 제거하는 대신 수정할 수 있나요?
예, GroupDocs.Watermark는 기존 주석을 수정하는 방법도 제공합니다.
### 추가 지원이나 지원은 어디서 찾을 수 있나요?
 GroupDocs.Watermark 포럼을 방문할 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19) 문의사항이나 도움이 필요하시면