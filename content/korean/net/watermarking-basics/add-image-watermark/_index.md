---
title: 이미지 워터마크 추가
linktitle: 이미지 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 문서에 이미지 워터마크를 손쉽게 추가하세요. 귀하의 지적 재산을 쉽게 보호하세요.
weight: 10
url: /ko/net/watermarking-basics/add-image-watermark/
---

# 이미지 워터마크 추가

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 문서에 이미지 워터마크를 추가하는 과정을 자세히 살펴보겠습니다. 워터마킹 문서는 지적 재산과 브랜딩을 보호하는 데 필수적입니다. .NET용 GroupDocs.Watermark를 사용하면 워터마크를 Word, Excel, PowerPoint, PDF 등과 같은 다양한 문서 형식에 원활하게 통합할 수 있습니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 .NET 라이브러리용 GroupDocs.Watermark를 다운로드하고 설치합니다.[웹사이트](https://releases.groupdocs.com/Watermark/net/).
2. 문서: 워터마크를 추가할 문서를 준비하세요.
3. 워터마크용 이미지: 워터마크로 사용할 이미지 파일을 준비합니다.

## 네임스페이스 가져오기
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## 1단계: 문서 경로 및 출력 디렉터리 초기화
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"`문서의 절대 또는 상대 경로와`"Your Document Directory"` 워터마크가 있는 문서를 저장하려는 디렉토리를 선택하세요.
## 2단계: 문서 스트림 열기 및 워터마커 초기화
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // 워터마킹 과정은 여기로 갈 것입니다.
    }
}
```
 다음을 사용하여 문서 스트림을 엽니다.`FileStream` 그리고 초기화`Watermarker` 물체.
## 3단계: 이미지 워터마크 추가
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 만들기`ImageWatermark` 워터마크로 사용하려는 이미지 파일의 경로가 있는 개체입니다. 워터마크의 가로 및 세로 정렬을 설정합니다.
## 4단계: 워터마크가 있는 문서 저장
```csharp
watermarker.Save(outputFileName);
```
워터마크가 있는 문서를 원하는 파일 이름으로 지정된 출력 디렉토리에 저장합니다.

## 결론
결론적으로, .NET용 GroupDocs.Watermark는 다양한 문서 형식에 워터마크를 쉽게 추가할 수 있는 포괄적인 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 문서에 이미지 워터마크를 효율적으로 추가하고 지적 재산을 보호할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Watermark를 사용하여 텍스트 워터마크를 추가할 수 있습니까?
예, .NET용 GroupDocs.Watermark는 문서에 이미지 및 텍스트 워터마크 추가를 모두 지원합니다.
### .NET용 GroupDocs.Watermark는 다른 문서 형식과 호환됩니까?
물론, .NET용 GroupDocs.Watermark는 Word, Excel, PowerPoint, PDF 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Watermark는 워터마크에 대한 사용자 정의 옵션을 제공합니까?
예, 위치, 크기, 불투명도, 회전 등 워터마크의 다양한 측면을 사용자 정의할 수 있습니다.
### .NET용 GroupDocs.Watermark를 사용하여 문서에서 워터마크를 제거할 수 있습니까?
예, .NET용 GroupDocs.Watermark는 문서에서 워터마크를 감지하고 제거하는 기능을 제공합니다.
### .NET용 GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예. 구매하기 전에 웹사이트에서 무료 평가판을 사용해 기능을 살펴볼 수 있습니다.[여기](https://releases.groupdocs.com/).