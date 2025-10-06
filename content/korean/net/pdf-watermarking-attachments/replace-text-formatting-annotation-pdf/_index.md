---
title: PDF의 주석 서식으로 텍스트 바꾸기
linktitle: PDF의 주석 서식으로 텍스트 바꾸기
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET으로 문서 보안을 강화하세요. PDF 파일의 주석 서식으로 텍스트를 손쉽게 바꾸는 방법을 알아보세요.
weight: 41
url: /ko/net/pdf-watermarking-attachments/replace-text-formatting-annotation-pdf/
type: docs
---
# PDF의 주석 서식으로 텍스트 바꾸기

## 소개
오늘날의 디지털 시대에는 민감한 정보와 지적 재산을 보호하는 것이 무엇보다 중요합니다. 법률 전문가, 기업체 또는 중요한 문서를 관리하는 개인이든 무단 액세스 및 배포로부터 보호하는 것이 필수입니다. .NET용 GroupDocs.Watermark는 PDF, Word, Excel, PowerPoint 및 이미지와 같은 다양한 문서 형식에서 워터마크를 추가, 검색 및 제거할 수 있는 포괄적인 기능을 제공하여 이 영역에서 강력한 도구로 부상하고 있습니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 파일의 주석 서식으로 텍스트를 바꾸는 복잡한 과정을 살펴보겠습니다.
## 전제조건
이 여정을 시작하기 전에 다음과 같은 전제 조건이 갖추어져 있는지 확인하세요.
### 1. .NET용 GroupDocs.Watermark 설치
 계속하기 전에 개발 환경에 .NET용 GroupDocs.Watermark를 설치했는지 확인하세요. 최신 버전은 다음 사이트에서 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
### 2. C# 프로그래밍의 기본 지식
이 튜토리얼에서 제공되는 예제를 따라가려면 C# 프로그래밍 언어에 대한 기본적인 이해가 필수적입니다.
### 3. PDF 문서 접근
주석 서식을 사용하여 텍스트를 바꾸려는 PDF 문서를 준비합니다.

## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 C# 코드로 가져오겠습니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: PDF 문서 로드
첫 번째 단계에서는 주석 서식을 사용하여 텍스트 바꾸기를 적용하려는 PDF 문서를 로드하는 작업이 포함됩니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 코드는 계속됩니다...
}
```
## 2단계: PDF 콘텐츠에 액세스
문서가 로드되면 주석에 대한 작업을 수행하기 위해 해당 콘텐츠에 액세스해야 합니다.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 3단계: 주석을 통해 반복
이제 PDF 문서의 첫 번째 페이지에 있는 주석을 반복합니다.
```csharp
foreach (PdfAnnotation annotation in pdfContent.Pages[0].Annotations)
{
    // 코드는 계속됩니다...
}
```
## 4단계: 텍스트를 서식으로 바꾸기
반복 내에서 대체할 지정된 텍스트가 주석에 포함되어 있는지 확인하십시오.
```csharp
if (annotation.Text.Contains("Test"))
{
    // 코드는 계속됩니다...
}
```
## 5단계: 대체 서식 적용
텍스트가 발견되면 기존 텍스트 조각을 지우고 서식 있는 텍스트를 대체 텍스트로 추가합니다.
```csharp
annotation.FormattedTextFragments.Clear();
annotation.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
```
## 6단계: 문서 저장
마지막으로 변경 사항이 적용된 수정된 문서를 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
.NET용 GroupDocs.Watermark는 개발자가 다양한 문서 형식에서 워터마크를 효율적으로 관리할 수 있는 강력한 기능을 제공합니다. PDF 문서의 주석 서식으로 텍스트를 대체함으로써 사용자는 문서 보안과 무결성을 원활하게 향상시킬 수 있습니다.
## FAQ
### GroupDocs.Watermark는 PDF 이외의 다른 문서 형식과 호환됩니까?
예, GroupDocs는 Word, Excel, PowerPoint, 이미지 등 다양한 형식을 지원합니다.
### 여러 문서에 동시에 워터마크를 적용할 수 있나요?
물론, GroupDocs.Watermark는 일괄 처리를 용이하게 하여 한 번에 여러 문서에 워터마크를 적용합니다.
### GroupDocs.Watermark는 사용자 정의 워터마크 디자인을 지원합니까?
예, 개발자는 .NET용 GroupDocs.Watermark를 사용하여 사용자 정의 워터마크 디자인을 만들 수 있습니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Watermark에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 기술 지원 및 문의 사항이 있는 경우 GroupDocs.Watermark를 방문하세요.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).