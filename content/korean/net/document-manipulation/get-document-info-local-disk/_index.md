---
title: 로컬 디스크에서 문서 정보 가져오기
linktitle: 로컬 디스크에서 문서 정보 가져오기
second_title: GroupDocs.Watermark .NET API
description: 이 포괄적인 단계별 가이드를 통해 GroupDocs for .NET을 사용하여 문서에서 워터마크를 추가, 제거 및 추출하는 방법을 알아보세요.
weight: 11
url: /ko/net/document-manipulation/get-document-info-local-disk/
---

# 로컬 디스크에서 문서 정보 가져오기

## 소개
.NET용 GroupDocs.Watermark 사용에 대한 최고의 가이드에 오신 것을 환영합니다! 숙련된 개발자이든 이제 막 시작하는 개발자이든 이 문서에서는 이 강력한 도구를 사용하여 문서에 워터마킹을 적용하는 필수 사항을 안내합니다. 결국에는 문서에 워터마크를 삽입하여 문서가 보호되고 사양에 맞게 브랜드화되도록 하는 전문가가 될 것입니다.
## 전제조건
단계별 가이드를 시작하기 전에 충족해야 할 몇 가지 전제 조건이 있습니다.
1.  .NET Framework: 시스템에 .NET Framework가 설치되어 있는지 확인하십시오. .NET용 GroupDocs.Watermark는 다양한 버전의 .NET Framework와 호환되므로[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) 호환성 세부정보를 확인하세요.
2.  .NET 라이브러리용 GroupDocs.Watermark: 다음에서 최신 버전을 다운로드하여 설치하세요.[다운로드 페이지](https://releases.groupdocs.com/Watermark/net/).
3. 개발 환경: 개발 환경이 설정되어 있어야 합니다. Visual Studio는 .NET 개발에 널리 사용되는 선택입니다.
4. 기본 C# 지식: C# 프로그래밍의 기본 사항을 이해하면 예제를 따라가는 데 도움이 됩니다.
## 네임스페이스 가져오기
.NET용 GroupDocs.Watermark를 사용하려면 먼저 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 이는 간단한 프로세스이며 라이브러리 기능에 액세스하는 데 필수적입니다.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
문서 워터마킹 프로세스를 명확하고 관리 가능한 단계로 나누어 보겠습니다. 각 단계는 기능을 쉽게 이해하고 구현하는 데 도움이 되도록 설계되었습니다.
## 1단계: 문서 로드
 첫 번째 단계는 워터마크를 추가하려는 문서를 로드하는 것입니다. 이 작업은 다음을 사용하여 수행됩니다.`Watermarker` 문서에 액세스하고 조작할 수 있는 클래스입니다.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // 이제 문서가 로드되었으며 워터마킹할 준비가 되었습니다.
}
```
 이 단계에서는 교체합니다.`"Your Document Path"` 문서의 실제 경로와 함께. 이렇게 하면`Watermarker`개체를 통해 다양한 워터마킹 기능에 액세스할 수 있습니다.
## 2단계: 문서 정보 가져오기
워터마크를 추가하기 전에 문서에 대한 몇 가지 정보를 수집할 수 있습니다. 이는 문서 속성에 따라 워터마크를 사용자 정의하는 데 유용할 수 있습니다.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 이 단계에서는`GetDocumentInfo` 메서드는 파일 형식, 페이지 수, 문서 크기 등의 세부 정보를 검색합니다. 이 정보는 콘솔에 인쇄되지만 필요에 따라 애플리케이션에서 사용할 수 있습니다.
## 3단계: 텍스트 워터마크 추가
이제 문서가 로드되었고 해당 정보가 준비되었으므로 워터마크를 추가할 차례입니다. 간단한 텍스트 워터마크부터 시작하겠습니다.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 여기서는`TextWatermark` 원하는 텍스트, 글꼴, 스타일을 사용하여 개체를 만듭니다. 색상, 불투명도, 회전 각도 등의 속성을 필요에 맞게 조정하세요. 마지막으로 워터마크가 문서에 추가되고 지정된 경로에 저장됩니다.
## 4단계: 이미지 워터마크 추가
텍스트 워터마크는 훌륭하지만 로고나 다른 이미지를 추가하고 싶다면 어떻게 해야 할까요? 이 단계에서는 이미지 워터마크를 추가하는 방법을 다룹니다.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 바꾸다`"Path to Your Image"` 워터마크 이미지의 경로를 입력하세요. 불투명도, 회전 각도 등의 속성을 설정하여 이미지 워터마크의 모양을 맞춤설정하세요. 워터마크를 추가하고 저장하는 과정은 텍스트 워터마크와 유사합니다.
## 5단계: 기존 워터마크 제거
 때로는 문서에서 기존 워터마크를 제거해야 할 수도 있습니다. 이 작업은 다음을 사용하여 수행할 수 있습니다.`Remove` 에서 제공하는 방법`Watermarker` 수업.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 여기서는`Remove` 문서에서 텍스트 워터마크를 제거하는 데 메서드가 사용됩니다. 필요에 따라 이미지, 텍스트 등 제거할 다양한 유형의 워터마크를 지정할 수 있습니다. 변경 사항을 보려면 문서를 새 경로에 저장하세요.
## 6단계: 워터마크 추출
문서에서 워터마크를 추출하고 검사해야 하는 경우 .NET용 GroupDocs.Watermark를 사용하면 이를 쉽게 수행할 수 있습니다.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // 각 워터마크의 추가 속성 및 논리
    }
}
```
 이 단계에는`GetWatermarks`문서의 모든 워터마크를 검색하는 방법입니다. 그런 다음 워터마크 목록을 반복하여 해당 속성을 검사하거나 필요에 따라 추가 작업을 수행할 수 있습니다.
## 결론
 축하해요! 이제 .NET용 GroupDocs.Watermark를 사용하여 문서에서 워터마크를 추가, 제거 및 추출하는 방법을 배웠습니다. 이러한 기술을 사용하면 문서를 효과적으로 보호하고 브랜드화할 수 있습니다. 기억하세요.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) 더 자세한 정보나 고급 기능이 필요한 경우 항상 있습니다.
## FAQ
### 모든 .NET 버전에서 .NET용 GroupDocs.Watermark를 사용할 수 있습니까?
 예, .NET용 GroupDocs.Watermark는 다양한 .NET Framework 버전과 호환됩니다. 을 체크 해봐[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) 구체적인 내용은.
### .NET용 GroupDocs.Watermark를 어디서 다운로드할 수 있나요?
 최신 버전은 다음 사이트에서 다운로드할 수 있습니다.[다운로드 페이지](https://releases.groupdocs.com/Watermark/net/).
### 임시 면허는 어떻게 얻나요?
 임시면허를 취득할 수 있습니다.[임시 라이센스 페이지](https://purchase.groupdocs.com/temporary-license/).
### 무료 평가판이 제공되나요?
 예, 다음 사이트를 방문하여 무료 평가판을 시작할 수 있습니다.[무료 평가판 페이지](https://releases.groupdocs.com/).
### 문제가 발생하면 어디서 지원을 받을 수 있나요?
 지원은 다음에서 가능합니다.[GroupDocs 워터마크 포럼](https://forum.groupdocs.com/c/watermark/19).