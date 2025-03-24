---
title: PDF에 워터마크 추가
linktitle: PDF에 워터마크 추가
second_title: GroupDocs.Watermark .NET API
description: 포괄적인 단계별 가이드를 통해 .NET용 GroupDocs.Watermark를 사용하여 PDF에 텍스트 및 이미지 워터마크를 추가하는 방법을 알아보세요.
weight: 14
url: /ko/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## 소개
문서를 보호하거나 로고로 브랜드를 지정하기 위해 PDF에 워터마크를 추가하려고 하시나요? 더 이상 보지 마세요! 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 PDF 파일에 텍스트 및 이미지 워터마크를 추가하는 과정을 자세히 살펴보겠습니다. 숙련된 개발자이든 이제 막 시작하는 개발자이든 이 가이드는 워터마크를 쉽고 정확하게 적용할 수 있도록 각 단계를 안내합니다.
## 전제조건
시작하기 전에 이 튜토리얼을 따라야 할 모든 것이 있는지 확인하십시오.
-  .NET용 GroupDocs.Watermark: 최신 버전이 설치되어 있는지 확인하세요. 당신은 할 수 있습니다[여기에서 다운로드하십시오](https://releases.groupdocs.com/Watermark/net/).
- .NET 개발 환경: Visual Studio 또는 .NET을 지원하는 기타 IDE.
- C#에 대한 기본 지식: C# 프로그래밍의 기본 사항을 이해하면 단계를 쉽게 수행하는 데 도움이 됩니다.
- PDF 문서: 워터마킹을 위한 샘플 PDF 문서를 준비하세요.
- 워터마크용 이미지: 이미지 워터마크를 추가하는 경우 이미지 파일을 준비하세요.
## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. 이를 통해 GroupDocs.Watermark 기능에 액세스할 수 있습니다.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
이제 프로세스를 관리 가능한 단계로 나누어 보겠습니다.
## 1단계: PDF 문서 로드
첫 번째 단계는 PDF 문서를 워터마커에 로드하는 것입니다. 방법은 다음과 같습니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 여기에 추가 단계가 추가됩니다.
}
```
## 2단계: 첫 페이지에 텍스트 워터마크 추가
다음으로 PDF의 첫 페이지에 텍스트 워터마크를 추가하겠습니다. 다음 지침을 따르십시오.
```csharp
// 첫 번째 페이지에 텍스트 워터마크 추가
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

텍스트 워터마크를 추가하면 문서의 무단 사용을 방지하거나 문서에 브랜드를 부여하는 데 도움이 됩니다. 눈에 보이지 않는 정품 인증 도장을 문서에 찍는 것을 상상해 보십시오.
## 3단계: 두 번째 페이지에 이미지 워터마크 추가
이제 두 번째 페이지에 이미지 워터마크를 추가해 보겠습니다. 이는 로고나 그래픽 워터마크에 특히 유용합니다.
```csharp
// 두 번째 페이지에 이미지 워터마크 추가
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

이미지 워터마크를 사용하면 문서를 전문적으로 보이게 하고 브랜드를 항상 눈에 띄게 만들 수 있습니다. 이는 모든 페이지에 서명을 추가하는 것과 같습니다.
## 4단계: 워터마크가 있는 PDF 저장
워터마크를 추가한 후 마지막 단계는 워터마크가 있는 PDF를 원하는 위치에 저장하는 것입니다.
```csharp
watermarker.Save(outputFileName);
```
문서를 저장하면 모든 변경 사항이 완료됩니다. 여러분의 노력이 가시적인 결과로 굳어져 사용하거나 배포할 준비가 된 순간입니다.
## 결론
축하해요! .NET용 GroupDocs.Watermark를 사용하여 PDF에 텍스트 및 이미지 워터마크를 모두 성공적으로 추가했습니다. 이 프로세스는 간단할 뿐만 아니라 특정 요구 사항에 맞게 사용자 정의가 가능합니다. 문서를 보호하든 브랜딩을 하든 워터마크는 마음대로 사용할 수 있는 강력한 도구입니다.
## FAQ
### 동일한 페이지에 여러 개의 워터마크를 추가할 수 있나요?
 예, 다음을 호출하여 동일한 페이지에 여러 워터마크를 추가할 수 있습니다.`Add` 다른 워터마크 개체를 사용하여 메서드를 여러 번 사용하세요.
### 텍스트 워터마크의 모양을 어떻게 사용자 정의할 수 있나요?
 글꼴, 크기, 색상, 불투명도 등의 속성을 조정하여 텍스트 워터마크를 사용자 정의할 수 있습니다.`TextWatermark` 물체.
### PDF의 특정 페이지에만 워터마킹이 가능한가요?
 예, 워터마크를 설정할 페이지를 지정할 수 있습니다.`PageIndex` 에 있는 재산`PdfArtifactWatermarkOptions`.
### PDF에서 워터마크를 제거할 수 있나요?
예, GroupDocs.Watermark는 PDF 문서에서 워터마크를 검색하고 제거하는 기능을 제공합니다.
### GroupDocs.Watermark에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
방문하시면 임시면허증을 받으실 수 있습니다.[임시 라이센스 페이지](https://purchase.groupdocs.com/temporary-license/).