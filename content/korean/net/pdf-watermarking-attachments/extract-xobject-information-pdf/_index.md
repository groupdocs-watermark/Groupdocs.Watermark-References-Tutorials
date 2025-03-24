---
title: PDF에서 XObject 정보 추출
linktitle: PDF에서 XObject 정보 추출
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 문서 워터마킹의 강력한 기능을 활용하세요. PDF, Word 문서 및 이미지의 워터마크를 원활하게 관리합니다.
weight: 25
url: /ko/net/pdf-watermarking-attachments/extract-xobject-information-pdf/
---

# PDF에서 XObject 정보 추출

## 소개
GroupDocs.Watermark for .NET은 PDF, Word, Excel, PowerPoint 및 이미지와 같은 다양한 문서 형식의 워터마크를 조작하도록 설계된 강력한 문서 워터마킹 API입니다. 이는 개발자에게 프로그래밍 방식으로 문서의 워터마크를 추가, 제거, 검색 및 교체할 수 있는 간단한 접근 방식을 제공합니다. 문서에 회사 로고, 저작권 고지 또는 기밀 스탬프를 추가해야 하는 경우 GroupDocs.Watermark는 직관적인 API를 통해 프로세스를 단순화합니다.
## 전제조건
.NET용 GroupDocs.Watermark를 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. 설치: 다음에서 .NET용 GroupDocs.Watermark를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/Watermark/net/).
2. 개발 환경: 시스템에 Visual Studio 또는 기타 .NET IDE가 설치되어 있어야 합니다.
3. .NET Framework: 개발 컴퓨터에 필수 .NET Framework가 설치되어 있는지 확인하세요.

## 네임스페이스 가져오기
프로젝트에서 .NET용 GroupDocs.Watermark 사용을 시작하려면 필요한 네임스페이스를 가져와야 합니다.
.NET 프로젝트에서 GroupDocs.Watermark.dll에 대한 참조를 추가합니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 1단계: 문서 로드
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## 2단계: PDF 콘텐츠에 액세스
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 3단계: 페이지 반복
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## 4단계: XObject에 액세스
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## 5단계: 정보 추출
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## 결론
.NET용 GroupDocs.Watermark를 사용하면 개발자가 .NET 응용 프로그램에서 문서 워터마크를 원활하게 관리할 수 있습니다. 직관적인 API와 강력한 기능을 갖춘 이 제품은 모든 워터마킹 요구 사항에 적합한 솔루션입니다. 이 가이드에 설명된 단계를 따르면 GroupDocs의 잠재력을 최대한 활용하고 문서 관리 작업 흐름을 향상시킬 수 있습니다.
## FAQ
### GroupDocs.Watermark는 모든 .NET 프레임워크와 호환됩니까?
예, GroupDocs.Watermark는 .NET Core 및 .NET Framework를 포함하여 광범위한 .NET 프레임워크를 지원합니다.
### GroupDocs.Watermark를 사용하여 단일 문서에 여러 워터마크를 적용할 수 있습니까?
전적으로! GroupDocs.Watermark를 사용하면 단일 문서에 다양한 유형의 여러 워터마크를 추가할 수 있습니다.
### GroupDocs.Watermark는 문서 암호화를 지원합니까?
예, GroupDocs.Watermark는 무단 액세스로부터 문서를 보호하는 암호화 기능을 제공합니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 GroupDocs.Watermark 무료 평가판에 액세스할 수 있습니다.[다운로드 페이지](https://releases.groupdocs.com/).
### GroupDocs.Watermark에 대한 추가 지원과 리소스는 어디서 찾을 수 있나요?
GroupDocs.Watermark 설명서를 살펴보거나, 커뮤니티 포럼에 가입하거나, 지원 팀에 도움을 요청할 수 있습니다.