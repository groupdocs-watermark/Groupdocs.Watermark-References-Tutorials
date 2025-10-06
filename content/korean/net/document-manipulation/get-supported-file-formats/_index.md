---
title: 지원되는 파일 형식 얻기
linktitle: 지원되는 파일 형식 얻기
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 문서에 워터마크를 손쉽게 추가하세요. 디지털 자산을 보호하려면 포괄적인 단계별 가이드를 따르세요.
weight: 13
url: /ko/net/document-manipulation/get-supported-file-formats/
type: docs
---
# 지원되는 파일 형식 얻기

## 소개
문서에 워터마킹을 하는 것은 디지털 자산을 보호하는 데 있어 중요한 단계입니다. 지적 재산 보호, 기밀성 보장, 단순한 브랜딩 등 워터마크는 중요한 역할을 합니다. 워터마킹 기능을 응용 프로그램에 통합하려는 .NET 개발자라면 .NET용 GroupDocs.Watermark는 고려해야 할 강력하고 다양한 도구입니다. 이 튜토리얼에서는 설치부터 첫 번째 워터마크 적용까지 GroupDocs.Watermark를 사용하는 데 필요한 필수 사항을 안내하고, 쉽게 따라할 수 있도록 각 단계를 세분화합니다.
## 전제조건
세부 사항을 살펴보기 전에 시작하는 데 필요한 모든 것이 갖추어져 있는지 확인하겠습니다.
1.  Visual Studio: 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다.[비주얼 스튜디오 웹사이트](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark는 다양한 버전의 .NET Framework를 지원합니다. 프로젝트가 호환되는 버전을 대상으로 하는지 확인하세요.
3. .NET용 GroupDocs.Watermark: 다음에서 최신 버전을 다운로드할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/Watermark/net/).
4. C#에 대한 기본 지식: 이 자습서에서는 사용자가 C# 및 .NET 개발에 대한 기본 지식을 가지고 있다고 가정합니다.
## 네임스페이스 가져오기
먼저 프로젝트에 필요한 네임스페이스를 가져오겠습니다. C# 파일을 열고 맨 위에 다음 using 지시문을 추가합니다.
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
이러한 네임스페이스를 가져오면 문서에 워터마크를 추가할 수 있습니다.

## 1단계: 워터마킹 엔진 초기화
 첫 번째 단계는 워터마킹 엔진을 초기화하는 것입니다. 여기에는 인스턴스 생성이 포함됩니다.`Watermarker` 워터마크를 추가하려는 문서로 수업을 진행하세요.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 이 코드 조각은`Watermarker` 문서에 워터마크를 적용하는 데 사용할 개체입니다.
## 2단계: 텍스트 워터마크 추가
이제 문서에 간단한 텍스트 워터마크를 추가해 보겠습니다. 텍스트 워터마크는 "기밀" 또는 "초안"과 같은 라벨을 추가하는 데 적합합니다.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 여기에서 우리는`TextWatermark`"기밀"이라는 텍스트가 있는 개체를 선택하고 글꼴과 색상을 설정하고 문서 중앙에 정렬했습니다.
## 3단계: 이미지 워터마크 추가
이미지를 워터마크로 사용하려는 경우 GroupDocs.Watermark를 사용하면 쉽게 사용할 수 있습니다.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 이 예에서는`ImageWatermark` 개체를 선택하고 크기를 설정한 후 문서의 오른쪽 상단 모서리에 맞춥니다.
## 4단계: 문서 저장
원하는 워터마크를 추가한 후 마지막 단계는 수정된 문서를 저장하는 것입니다.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 그러면 워터마크가 있는 문서가 지정된 경로에 저장되고 문서에 사용된 모든 리소스가 해제됩니다.`Watermarker` 사례.
## 5단계: 지원되는 파일 형식 얻기
GroupDocs.Watermark에서 지원되는 파일 형식을 확인하려면 다음 코드 조각을 사용할 수 있습니다.
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
그러면 GroupDocs.Watermark가 처리할 수 있는 모든 파일 형식이 인쇄되어 해당 기능에 대한 포괄적인 보기를 제공합니다.
## 결론
GroupDocs for .NET을 사용하여 문서에 워터마킹하는 것은 간단하고 효율적입니다. 이 튜토리얼을 따라 워터마킹 엔진을 초기화하고, 텍스트 및 이미지 워터마크를 추가하고, 워터마킹된 문서를 저장하고, 지원되는 파일 형식을 나열하는 방법을 배웠습니다. 이러한 도구를 사용하면 자신있게 문서를 보호할 수 있습니다.
 궁금한 점이 있거나 추가 도움이 필요하면 주저하지 말고[GroupDocs.Watermark 지원 포럼](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### .NET용 GroupDocs.Watermark를 어떻게 설치합니까?
 다음에서 다운로드할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/Watermark/net/) 프로젝트에 DLL을 추가하십시오.
### GroupDocs.Watermark를 무료로 사용해 볼 수 있나요?
 예, 요청하실 수 있습니다[무료 시험판](https://releases.groupdocs.com/) 구매하기 전에 소프트웨어를 평가합니다.
### GroupDocs.Watermark는 어떤 파일 형식을 지원합니까?
제공된 코드 조각을 사용하여 지원되는 모든 파일 형식을 나열할 수 있습니다.
### GroupDocs.Watermark 라이센스를 어떻게 구입할 수 있나요?
 라이센스는 다음에서 직접 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark에 사용할 수 있는 문서가 있습니까?
 예, 포괄적인 문서가 제공됩니다.[여기](https://tutorials.groupdocs.com/Watermark/net/).