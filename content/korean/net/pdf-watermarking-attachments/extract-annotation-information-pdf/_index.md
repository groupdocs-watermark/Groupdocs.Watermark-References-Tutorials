---
title: PDF에서 주석 정보 추출
linktitle: PDF에서 주석 정보 추출
second_title: GroupDocs.Watermark .NET API
description: 이 상세한 단계별 가이드에서 .NET용 GroupDocs.Watermark를 사용하여 PDF 문서에서 주석 정보를 추출하는 방법을 알아보세요.
weight: 23
url: /ko/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---

# PDF에서 주석 정보 추출

## 소개
PDF 문서에서 자세한 주석 정보를 추출해야 하는 경우가 자주 있습니까? 문서 관리 시스템을 작업하는 개발자이거나 수많은 PDF를 처리하는 비즈니스 전문가라면 주석을 효율적으로 추출하고 처리하는 것이 중요할 수 있습니다. .NET용 GroupDocs.Watermark를 사용하면 이 작업을 간단하고 효율적으로 수행할 수 있는 강력한 도구 키트를 사용할 수 있습니다.
## 전제조건
코드를 살펴보기 전에 시작하는 데 필요한 모든 것이 갖추어져 있는지 확인하겠습니다.
1. Visual Studio: Visual Studio가 설치되어 있는지 확인하세요. 이는 코드를 작성하고 실행하기 위한 IDE가 됩니다.
2.  .NET용 GroupDocs.Watermark: .NET용 GroupDocs.Watermark 라이브러리가 필요합니다. 당신은 할 수 있습니다[여기에서 다운로드하십시오](https://releases.groupdocs.com/Watermark/net/).
3. C#에 대한 기본 지식: 예제를 따라가려면 C# 프로그래밍에 대한 지식이 필요합니다.
## 네임스페이스 가져오기
우선, 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 이러한 네임스페이스에는 PDF 파일 작업 및 주석 추출에 필요한 클래스와 메서드가 포함되어 있습니다.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## 1단계: 프로젝트 설정
먼저 Visual Studio에서 프로젝트를 설정해 보겠습니다. 새 콘솔 앱(.NET Core) 프로젝트를 만듭니다. 프로젝트가 생성되면 .NET용 GroupDocs.Watermark 라이브러리에 대한 참조를 추가해야 합니다.
1. NuGet 패키지 관리자를 엽니다.
2.  검색`GroupDocs.Watermark`.
3.  설치하다`GroupDocs.Watermark` 패키지.
## 2단계: 문서 경로 정의
다음으로, 입력 PDF 문서의 경로와 추출된 정보가 저장될 출력 디렉터리를 지정해야 합니다. 이렇게 하면 응용 프로그램이 PDF 파일을 찾을 위치와 결과를 저장할 위치를 알 수 있습니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 3단계: PDF 문서 로드
 PDF 문서로 작업하려면 다음을 사용하여 로드해야 합니다.`PdfLoadOptions`. 이 클래스는 로딩 프로세스를 구성하는 옵션을 제공합니다.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 주석을 추출하는 코드가 여기에 표시됩니다.
}
```
## 4단계: PDF 콘텐츠에 액세스
문서가 로드되면 해당 내용에 액세스할 수 있습니다. 특히 페이지와 주석을 반복할 수 있도록 PDF 콘텐츠를 가져오고 싶습니다.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## 5단계: 페이지 및 주석 반복
PDF 콘텐츠를 손에 넣으면 각 페이지를 반복한 다음 해당 페이지의 각 주석을 반복할 수 있습니다. 이를 통해 우리는 필요한 정보를 추출할 수 있습니다.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // 여기에서 주석 세부정보를 추출하세요.
    }
}
```
## 6단계: 주석 세부정보 추출
중첩 루프 내에서 각 주석에 대한 다양한 세부 정보를 추출합니다. 여기에는 주석 유형, 관련 이미지, 텍스트 및 위치 데이터가 포함됩니다.
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## 7단계: 추출된 데이터 저장 또는 처리
마지막으로 추출된 주석 정보로 무엇을 할지 결정합니다. 필요에 따라 콘솔에 인쇄하거나 파일에 저장하거나 데이터베이스에 저장할 수도 있습니다.
```csharp
// 추출된 데이터를 파일로 저장하는 예
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## 결론
.NET용 GroupDocs.Watermark를 사용하여 PDF 문서에서 주석 정보를 추출하는 것은 많은 시간과 노력을 절약할 수 있는 간단한 프로세스입니다. 이 가이드에 설명된 단계를 따르면 이 기능을 프로젝트에 쉽게 통합하고 귀중한 주석 데이터 추출을 자동화할 수 있습니다.
 대량의 PDF를 관리하거나 단순히 특정 정보를 추출해야 하는 경우 .NET용 GroupDocs.Watermark는 안정적이고 효율적인 솔루션을 제공합니다. 꼭 확인해 보세요.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) 고급 기능과 사용자 정의 옵션을 확인하세요.
## FAQ
### .NET용 GroupDocs.Watermark란 무엇입니까?
.NET용 GroupDocs.Watermark는 개발자가 PDF, Word 문서 및 이미지를 포함한 다양한 문서 형식에서 워터마크를 추가, 검색 및 제거할 수 있는 포괄적인 라이브러리입니다.
### GroupDocs.Watermark를 무료로 사용해 볼 수 있나요?
 예, 다음을 얻을 수 있습니다.[무료 시험판](https://releases.groupdocs.com/) 구매하기 전에 라이브러리의 기능을 테스트합니다.
### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 GroupDocs 팀을 방문하면 지원을 받을 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/watermark/19).
### 테스트를 위해 임시 라이센스를 얻을 수 있습니까?
 예, 요청하실 수 있습니다[임시 면허증](https://purchase.groupdocs.com/temporary-license/)테스트 목적으로.
### .NET용 GroupDocs.Watermark 정식 버전은 어디서 구입할 수 있나요?
 정식 버전은 다음 사이트에서 구매하실 수 있습니다.[GroupDocs 웹사이트](https://purchase.groupdocs.com/buy).