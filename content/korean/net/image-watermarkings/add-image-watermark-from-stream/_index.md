---
title: 스트림에서 이미지 워터마크 추가
linktitle: 스트림에서 이미지 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: .NET용 GroupDocs.Watermark를 사용하여 문서에 이미지 워터마크를 추가하는 방법을 알아보세요. 원활한 워터마크 통합을 위한 단계별 가이드를 따르세요.
weight: 12
url: /ko/net/image-watermarkings/add-image-watermark-from-stream/
---

# 스트림에서 이미지 워터마크 추가

## 소개
문서 관리 및 보안 영역에서는 워터마크를 파일에 통합하는 것이 가장 중요합니다. 브랜딩, 저작권 보호 또는 문서 무결성 유지와 관련하여 워터마크는 중요한 역할을 합니다. 다행히 .NET용 GroupDocs.Watermark는 다양한 문서 형식의 워터마크를 추가, 제거 및 검색할 수 있는 강력한 솔루션을 제공합니다.
## 전제조건
.NET용 GroupDocs.Watermark를 사용하여 워터마크 구현을 시작하기 전에 다음 전제 조건이 충족되는지 확인하세요.
1.  .NET용 GroupDocs.Watermark 설치: 다음에서 .NET 라이브러리용 GroupDocs.Watermark를 다운로드하고 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
2. 문서 접근 권한: 워터마크를 추가하거나 제거하려는 문서에 접근할 수 있습니다.
3. C#에 대한 기본 지식: 제공된 코드 조각을 이해하고 구현하려면 C# 프로그래밍 언어에 대한 지식이 필요합니다.

## 네임스페이스 가져오기
스트림에서 이미지 워터마크 추가를 진행하기 전에 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## 1단계: 문서 경로 및 출력 디렉터리 정의
먼저 워터마크를 추가하려는 문서의 경로를 정의하고 처리된 문서의 출력 디렉터리를 지정합니다.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## 2단계: 워터마크 스트림 공개
 다음을 사용하여 워터마크 이미지 파일을 스트림으로 엽니다.`File.OpenRead` 방법.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // 워터마크 처리 로직이 여기에 위치합니다.
}
```
## 3단계: 문서에 워터마크 추가
 초기화`Watermarker` 문서 경로를 사용하여 개체를 만든 다음`ImageWatermark` 2단계에서 얻은 워터마크 스트림을 객체에 추가합니다. 다음을 사용하여 문서에 워터마크를 추가합니다.`Add` 의 방법`Watermarker` 물체.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // 문서에 워터마크 추가
        watermarker.Add(watermark);
        // 워터마크가 포함된 문서를 저장하세요
        watermarker.Save(outputFileName);
    }
}
```

## 결론
.NET용 GroupDocs.Watermark는 문서에 워터마크를 추가하여 브랜드 아이덴티티, 저작권 보호 및 문서 무결성을 보장하는 완벽한 솔루션을 제공합니다. 간략한 단계를 따르고 제공된 코드 조각을 활용함으로써 사용자는 워터마크를 문서에 손쉽게 통합할 수 있습니다.
## FAQ
### GroupDocs.Watermark는 다양한 문서 형식과 호환됩니까?
예, GroupDocs.Watermark는 Word 문서, Excel 스프레드시트, PowerPoint 프리젠테이션, PDF 등을 포함한 광범위한 문서 형식을 지원합니다.
### 워터마크의 모양과 위치를 사용자 정의할 수 있나요?
물론, GroupDocs.Watermark는 워터마크 모양, 위치, 투명도, 회전 등을 특정 요구 사항에 맞게 사용자 정의할 수 있는 광범위한 옵션을 제공합니다.
### GroupDocs.Watermark는 기존 워터마크를 제거하기 위한 API를 제공합니까?
예, GroupDocs.Watermark를 사용하면 사용자는 워터마크를 추가할 수 있을 뿐만 아니라 문서에서 기존 워터마크를 쉽게 제거할 수도 있습니다.
### GroupDocs.Watermark 사용자에게 기술 지원이 제공됩니까?
 예, 사용자는 전담 서비스를 통해 기술 지원 및 지원을 받을 수 있습니다.[GroupDocs.Watermark 포럼](https://forum.groupdocs.com/c/watermark/19).
### 구매하기 전에 GroupDocs.Watermark를 평가할 수 있나요?
물론 사용자는 구매 결정을 내리기 전에 GroupDocs.Watermark의 무료 평가판을 선택하여 기능을 살펴볼 수 있습니다.