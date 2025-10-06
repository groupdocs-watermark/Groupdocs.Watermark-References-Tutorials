---
title: 텍스트 워터마크 추가
linktitle: 텍스트 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: 이 단계별 가이드를 통해 Groupdocs for .NET을 사용하여 문서에 텍스트 워터마크를 추가하는 방법을 알아보세요.
weight: 11
url: /ko/net/watermarking-basics/add-text-watermark/
type: docs
---
# 텍스트 워터마크 추가

## 소개
.NET용 GroupDocs.Watermark는 개발자가 .NET 응용 프로그램의 다양한 문서 형식에서 워터마크를 추가, 검색 및 제거할 수 있는 강력한 라이브러리입니다. 이 튜토리얼에서는 GroupDocs.Watermark를 사용하여 문서에 텍스트 워터마크를 추가하는 방법에 중점을 둘 것입니다.
## 전제조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1. C# 프로그래밍 언어에 대한 기본 지식.
2. 시스템에 Visual Studio가 설치되어 있습니다.
3.  .NET 라이브러리용 GroupDocs.Watermark가 설치되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1단계: 문서 경로 및 출력 디렉터리 정의
입력 문서의 경로와 워터마크가 있는 문서가 저장될 출력 디렉터리를 정의합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 입력 문서에 대한 절대 또는 상대 경로를 사용합니다. 예:`@"C:\Docs\document.pdf"`. 또한 워터마크가 있는 문서를 저장할 디렉터리를 지정하세요.
## 2단계: 텍스트 워터마크 추가
 인스턴스화`Watermarker` 입력 문서 경로가 있는 클래스입니다. 그런 다음`TextWatermark` 원하는 텍스트와 글꼴 설정으로 개체를 만듭니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 문서에 텍스트 워터마크를 추가하는 방법을 배웠습니다. 직관적인 API를 통해 개발자는 다양한 문서 형식의 워터마크를 쉽게 조작할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark는 모든 문서 형식과 호환됩니까?
GroupDocs.Watermark는 PDF, Microsoft Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 텍스트 워터마크의 모양을 사용자 정의할 수 있나요?
예, 텍스트 워터마크의 글꼴, 색상, 정렬, 불투명도 등 다양한 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Watermark는 문서에서 워터마크 제거를 지원합니까?
예, GroupDocs.Watermark는 문서에서 워터마크를 검색하고 제거하는 기능을 제공합니다.
### 구매하기 전에 .NET용 GroupDocs.Watermark를 사용해 볼 수 있나요?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Watermark에 대한 기술 지원은 어떻게 받을 수 있나요?
 방문하시면 기술지원을 받으실 수 있습니다.[GroupDocs.Watermark 포럼](https://forum.groupdocs.com/c/watermark/19).