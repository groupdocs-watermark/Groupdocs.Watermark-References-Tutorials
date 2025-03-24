---
title: 타일식 이미지 워터마크 추가
linktitle: 타일식 이미지 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 문서에 타일식 이미지 워터마크를 추가하는 방법을 알아보세요. 쉽고 효율적이며 사용자 정의가 가능합니다.
weight: 10
url: /ko/net/image-watermarkings/add-tiled-image-watermark/
---

# 타일식 이미지 워터마크 추가

## 소개
.NET용 GroupDocs.Watermark는 개발자가 프로그래밍 방식으로 다양한 문서 형식의 워터마크를 추가, 제거 및 검색할 수 있는 강력한 API입니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 문서에 타일식 이미지 워터마크를 추가하는 과정을 안내합니다.
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- C# 프로그래밍 언어에 대한 기본 지식.
- 시스템에 Visual Studio가 설치되어 있습니다.
- .NET용 GroupDocs.Watermark 라이브러리가 프로젝트에 추가되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/Watermark/net/).

## 네임스페이스 가져오기
C# 파일 시작 부분에서 필요한 네임스페이스를 가져와야 합니다.
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## 1단계: 문서 경로 및 출력 디렉터리 설정
입력 문서의 경로와 출력 문서를 저장할 디렉터리를 정의합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 입력 문서의 절대 또는 상대 경로로.
## 2단계: 워터마커 개체 초기화
입력 문서 경로를 사용하여 Watermarker 개체를 만듭니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // 여기에 워터마크 추가
}
```
## 3단계: 타일식 이미지 워터마크 추가
워터마크로 사용하려는 이미지 파일의 경로를 사용하여 ImageWatermark 객체를 인스턴스화합니다.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // 타일 옵션 구성
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // 문서에 워터마크 추가
    watermarker.Add(watermark);
    // 수정된 문서를 저장하세요
    watermarker.Save(outputFileName);
}
```
 바꾸다`"Path to Your Image"` 워터마크 이미지 파일의 실제 경로를 사용하세요.

## 결론
다음 단계를 수행하면 .NET용 GroupDocs.Watermark를 사용하여 문서에 타일식 이미지 워터마크를 쉽게 추가할 수 있습니다. 원하는 결과를 얻으려면 다양한 옵션과 구성을 실험해 보세요.
## FAQ
### 단일 문서에 여러 개의 워터마크를 추가할 수 있나요?
예, .NET용 GroupDocs.Watermark를 사용하여 문서에 다양한 유형의 여러 워터마크를 추가할 수 있습니다.
### GroupDocs.Watermark는 모든 문서 형식을 지원합니까?
GroupDocs.Watermark는 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Watermark에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### 워터마크의 모양을 사용자 정의할 수 있나요?
예, 위치, 크기, 회전, 투명도 등 워터마크의 다양한 측면을 사용자 정의할 수 있습니다.
### GroupDocs.Watermark는 기술 지원을 제공합니까?
 예, GroupDocs.Watermark 포럼에서 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/watermark/19).