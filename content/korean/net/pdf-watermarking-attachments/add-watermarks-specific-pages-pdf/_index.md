---
title: PDF의 특정 페이지에 워터마크 추가
linktitle: PDF의 특정 페이지에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET을 사용하여 PDF의 특정 페이지에 텍스트 및 이미지 워터마크를 추가하는 방법을 알아보세요. 문서를 보호하려면 자세한 가이드를 따르세요.
weight: 15
url: /ko/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
---
## 소개
PDF 문서에 워터마크를 추가하는 것은 콘텐츠를 보호하고 소유권을 주장하는 데 있어 중요한 단계입니다. 초안을 표시하거나 민감한 정보를 보호하거나 단순히 브랜딩을 추가하는 등 워터마크는 효과적인 도구입니다. 이 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF 파일의 특정 페이지에 텍스트 및 이미지 워터마크를 모두 추가하는 방법을 살펴보겠습니다. 프로세스를 관리 가능한 단계로 나누어 프로젝트에서 이러한 기능을 따르고 구현할 수 있도록 하겠습니다.
## 전제조건
구현을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- Visual Studio 설치: .NET 코드를 작성하고 실행하려면 Visual Studio와 같은 IDE가 필요합니다.
- .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
-  .NET용 Groupdocs.Watermark: .NET용 Groupdocs.Watermark를 다운로드하고 설치합니다. 당신은 그것을 얻을 수 있습니다[여기](https://releases.groupdocs.com/Watermark/net/).
- C#에 대한 기본 지식: C# 프로그래밍 언어에 익숙하면 도움이 됩니다.
- PDF 문서: 워터마크 추가를 테스트하는 데 사용할 수 있는 PDF 파일을 준비하세요.
## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 이 단계는 Watermark 클래스 및 메소드에 액세스할 수 있도록 하기 때문에 중요합니다.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 프로젝트 설정
### 새 프로젝트 만들기
먼저 Visual Studio를 열고 새 C# 프로젝트를 만듭니다. 단순화를 위해 콘솔 애플리케이션을 선택할 수 있습니다.
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### Groupdocs.Watermark 설치
다음으로 NuGet 패키지 관리자를 통해 Groupdocs.Watermark 라이브러리를 설치합니다.
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
"Groupdocs.Watermark"를 검색하여 설치하세요.
## 2단계: PDF 문서 로드
### 문서 경로 정의
PDF 문서의 경로와 워터마크가 있는 PDF가 저장될 출력 디렉터리를 지정합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### PDF 문서 로드
 사용`PdfLoadOptions` PDF 문서를 로드하는 클래스입니다.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마크를 추가하는 코드가 여기에 표시됩니다.
}
```
## 3단계: 홀수 페이지에 텍스트 워터마크 추가
### 텍스트 워터마크 만들기
 만들기`TextWatermark` 원하는 텍스트와 글꼴 설정으로 개체를 만듭니다.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### 텍스트 워터마크 옵션 적용
 사용`PdfArtifactWatermarkOptions` 워터마크 적용 방법을 지정합니다.
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## 4단계: 첫 번째 페이지에 이미지 워터마크 추가
워터마크로 사용할 이미지를 불러옵니다. 이미지 경로가 올바른지 확인하세요.
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## 5단계: 워터마크가 있는 PDF 저장
마지막으로 워터마크가 있는 PDF를 지정된 출력 디렉터리에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```
## 결론
Groupdocs for .NET을 사용하여 PDF에 워터마크를 추가하는 과정은 간단합니다. 다음 단계를 따르면 PDF 문서의 특정 페이지에 텍스트 및 이미지 워터마크를 효율적으로 추가할 수 있습니다. 이는 문서 보안뿐 아니라 전문적인 외관을 유지하는 데도 도움이 됩니다. 워터마크를 독특하고 효과적으로 만드는 데 사용할 수 있는 다양한 사용자 정의 옵션을 시험해보고 탐색해 보십시오.
## FAQ
### .NET용 Groupdocs.Watermark란 무엇입니까?
Groupdocs.Watermark for .NET은 PDF, Word, Excel 등을 포함한 다양한 문서 형식의 워터마크를 추가, 검색 및 제거할 수 있는 라이브러리입니다.
### 워터마크 모양을 사용자 정의할 수 있나요?
예, 텍스트 워터마크의 텍스트 글꼴, 크기, 색상 및 위치를 사용자 정의할 수 있으며 이미지 워터마크의 크기, 불투명도 및 위치를 조정할 수 있습니다.
### 특정 페이지에만 워터마크를 추가할 수 있나요?
전적으로. .NET용 Groupdocs.Watermark는 특정 페이지, 홀수 또는 짝수 페이지 또는 페이지 범위에 워터마크를 추가하는 옵션을 제공합니다.
### Groupdocs.Watermark의 무료 평가판을 받으려면 어떻게 해야 합니까?
 다음에서 무료 평가판을 다운로드할 수 있습니다.[그룹닥스 웹사이트](https://releases.groupdocs.com/).
### 더 자세한 문서는 어디서 찾을 수 있나요?
 자세한 내용은 다음을 참조하세요.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/).