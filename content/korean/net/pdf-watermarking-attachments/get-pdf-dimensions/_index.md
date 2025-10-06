---
title: PDF 치수 가져오기
linktitle: PDF 치수 가져오기
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 문서를 쉽게 보호하세요. 워터마크, 스탬프, 주석을 손쉽게 추가하세요.
weight: 26
url: /ko/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# PDF 치수 가져오기

## 소개
오늘날의 디지털 시대에는 문서를 보호하는 것이 무엇보다 중요합니다. 귀하가 비즈니스 전문가이건, 법률 전문가이건, 창의적인 예술가이건 간에 귀하의 지적 재산을 보호하는 것은 필수적입니다. .NET용 Groupdocs.Watermark는 문서에 워터마크, 스탬프 및 주석을 추가하여 문서의 보안과 신뢰성을 보장하는 강력한 솔루션을 제공합니다.
## 전제조건
.NET용 Groupdocs.Watermark의 세계로 뛰어들기 전에 다음 전제 조건이 갖추어져 있는지 확인하세요.
1.  .NET용 Groupdocs.Watermark 설치: 다음에서 .NET용 Groupdocs.Watermark를 다운로드하여 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
2.  라이센스 키(선택 사항): .NET용 Groupdocs.Watermark는 무료 평가판을 제공하지만 임시 라이센스를 선택하거나 다음에서 정식 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy) 확장된 기능을 위해.
3. C#에 대한 지식: 제공된 예제를 이해하고 구현하려면 C# 프로그래밍 언어에 대한 기본 지식이 권장됩니다.
4. 보호할 문서: 실험할 샘플 문서(예: PDF, Word, Excel)를 로컬 컴퓨터에 준비하세요.

## 네임스페이스 가져오기
.NET용 Groupdocs.Watermark 작업을 시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### 1단계: 변수 선언
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### 2단계: 문서 로드
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### 3단계: PDF 콘텐츠 가져오기
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 4단계: 차원 검색
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## 결론
결론적으로, .NET용 Groupdocs.Watermark는 문서를 무단 사용 및 배포로부터 보호하는 포괄적인 솔루션을 제공합니다. 위에 설명된 단계를 따르고 .NET용 Groupdocs.Watermark의 기능을 활용하면 귀중한 디지털 자산의 보안과 무결성을 보장할 수 있습니다.
## FAQ
### .NET용 Groupdocs.Watermark를 무료로 사용할 수 있나요?
예, .NET용 Groupdocs.Watermark는 평가 목적으로 무료 평가판을 제공합니다. 그러나 확장된 기능을 사용하려면 정식 라이센스 구입을 고려할 수 있습니다.
### Groupdocs.Watermark는 다양한 문서 형식을 지원합니까?
예, Groupdocs는 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### Groupdocs.Watermark를 사용하여 워터마크와 스탬프를 사용자 정의할 수 있습니까?
전적으로! Groupdocs.Watermark는 특정 요구 사항에 맞게 워터마크, 스탬프 및 주석에 대한 광범위한 사용자 정의 옵션을 제공합니다.
### Groupdocs.Watermark 사용자에게 기술 지원이 제공됩니까?
 예, 다음을 통해 기술 지원을 받고 Groupdocs 커뮤니티에 참여할 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark에 대한 임시 라이센스를 어떻게 얻을 수 있습니까?
 Groupdocs.Watermark에 대한 임시 라이센스는 다음에서 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).