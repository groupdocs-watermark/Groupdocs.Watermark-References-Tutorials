---
title: 문서 미리보기 생성
linktitle: 문서 미리보기 생성
second_title: GroupDocs.Watermark .NET API
description: 이 가이드를 통해 .NET용 GroupDocs.Watermark를 사용하여 문서 미리보기를 생성하는 방법을 알아보세요. 문서 보안 및 관리를 손쉽게 강화하세요.
weight: 10
url: /ko/net/document-manipulation/generate-document-preview/
type: docs
---
# 문서 미리보기 생성

## 소개
디지털 문서 관리의 세계에서 워터마킹은 문서의 보안과 신뢰성을 보장하는 데 중요한 역할을 합니다. .NET용 GroupDocs.Watermark는 개발자가 손쉽게 문서에 워터마크를 추가할 수 있는 강력한 도구입니다. 이 튜토리얼에서는 .NET용 GroupDocs.Watermark를 사용하여 문서 미리보기를 생성하는 과정을 안내합니다. 숙련된 개발자이든 이제 막 시작하는 개발자이든 이 가이드는 목표 달성을 위한 포괄적인 단계별 프로세스를 제공합니다.
## 전제조건
구현을 시작하기 전에 시작하는 데 필요한 모든 것이 갖추어져 있는지 확인하십시오.
- C# 및 .NET 프레임워크에 대한 기본적인 이해.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- .NET 라이브러리용 GroupDocs.Watermark. 당신은 할 수 있습니다[여기에서 다운로드하십시오](https://releases.groupdocs.com/Watermark/net/).
-  GroupDocs.Watermark에 대한 유효한 라이센스입니다. 구매하셔도 됩니다[여기](https://purchase.groupdocs.com/buy) 또는[임시 면허증](https://purchase.groupdocs.com/temporary-license/) 평가 목적으로.
## 네임스페이스 가져오기
프로젝트에서 GroupDocs.Watermark 사용을 시작하려면 필요한 네임스페이스를 가져와야 합니다. 이는 코드에 다음 using 지시문을 추가하여 수행할 수 있습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
이러한 네임스페이스는 워터마킹 및 문서 미리보기 생성에 필요한 클래스 및 메서드에 대한 액세스를 제공합니다.

문서 미리보기를 생성하는 과정을 간단하고 따라하기 쉬운 단계로 나누어 보겠습니다.
## 1단계: 프로젝트 설정
가장 먼저 Visual Studio에서 .NET 프로젝트를 설정합니다. 아직 프로젝트가 없다면 다음 단계에 따라 새 프로젝트를 만드세요.
1. 비주얼 스튜디오를 엽니다.
2. "새 프로젝트 만들기"를 클릭하세요.
3. "콘솔 앱(.NET Core)"을 선택하고 "다음"을 클릭합니다.
4. 프로젝트 이름을 지정하고 저장할 위치를 선택한 다음 "만들기"를 클릭하세요.
## 2단계: .NET용 GroupDocs.Watermark 설치
프로젝트에서 GroupDocs.Watermark를 사용하려면 라이브러리를 설치해야 합니다. NuGet 패키지 관리자를 사용하여 이 작업을 수행할 수 있습니다.
1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭합니다.
2. "NuGet 패키지 관리"를 선택하십시오.
3. 찾아보기 탭에서 "GroupDocs.Watermark"를 검색합니다.
4. 프로젝트에 라이브러리를 추가하려면 "설치"를 클릭하세요.
또는 패키지 관리자 콘솔을 통해 설치할 수 있습니다.
```powershell
Install-Package GroupDocs.Watermark
```
## 3단계: 문서 경로 및 출력 디렉터리 정의
미리보기를 생성하기 전에 미리보려는 문서의 경로와 미리보기 이미지가 저장될 디렉터리를 지정해야 합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
"문서 경로"를 문서 경로로 바꾸고 "문서 디렉터리"를 미리 보기 이미지를 저장할 디렉터리로 바꾸세요.
## 4단계: 워터마커 개체 초기화
인스턴스를 생성합니다.`Watermarker` 클래스 생성자에 문서 경로를 전달하여 클래스를 생성합니다. 이 객체는 모든 워터마킹 작업을 수행하는 데 사용됩니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // 여기에 귀하의 코드가 있습니다
}
```
## 5단계: 스트림 처리를 위한 위임 메서드 생성
미리보기를 생성하려면 스트림 생성 및 릴리스를 위한 대리자 메서드를 정의해야 합니다. 이러한 메소드는 문서의 각 페이지에 대한 스트림 생성 및 릴리스를 처리합니다.
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 그만큼`createPageStreamDelegate` 메소드는 문서의 각 페이지에 대한 스트림을 생성하는 반면`releasePageStreamDelegate` 메소드는 미리보기가 생성된 후 스트림을 닫습니다.
## 6단계: 미리보기 옵션 구성
 다음으로, 인스턴스를 생성하여 미리보기 옵션을 구성합니다.`PreviewOptions` 수업. 대리자 메서드를 지정하고 미리보기 형식을 PNG로 설정합니다. 미리보기에 포함할 페이지를 지정할 수도 있습니다.
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
이 예에서는 문서의 처음 두 페이지에 대한 미리 보기를 생성합니다.
## 7단계: 문서 미리보기 생성
 마지막으로`GeneratePreview` 에 대한 방법`Watermarker`객체, 구성된 전달`PreviewOptions`. 그러면 미리보기 이미지가 생성되어 지정된 디렉터리에 저장됩니다.
```csharp
watermarker.GeneratePreview(previewOptions);
```
## 결론
.NET용 GroupDocs.Watermark를 사용하여 문서 미리보기를 생성하는 것은 단 몇 줄의 코드만으로 수행할 수 있는 간단한 프로세스입니다. 이 가이드에 설명된 단계를 따르면 쉽게 프로젝트를 설정하고, 필요한 옵션을 구성하고, 문서에 대한 미리 보기를 생성할 수 있습니다. 이 강력한 라이브러리는 워터마킹 프로세스를 단순화할 뿐만 아니라 워터마크 관리 및 조작을 위한 강력한 기능도 제공합니다.
 궁금한 점이 있거나 추가 도움이 필요하면 주저하지 말고[GroupDocs.Watermark 지원 포럼](https://forum.groupdocs.com/c/watermark/19) 또는[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/).
## FAQ
### .NET용 GroupDocs.Watermark는 어떤 파일 형식을 지원합니까?
 .NET용 GroupDocs.Watermark는 PDF, DOCX, PPTX, XLSX 등을 포함한 광범위한 파일 형식을 지원합니다. 지원되는 형식의 전체 목록은 다음을 참조하세요.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/).
### 워터마크의 모양을 사용자 정의할 수 있나요?
예, GroupDocs.Watermark를 사용하면 텍스트, 이미지, 모양 워터마크를 포함한 워터마크의 모양을 완전히 사용자 정의할 수 있습니다. 글꼴, 색상, 크기, 투명도 등의 속성을 조정할 수 있습니다.
### 평가판을 사용할 수 있나요?
 예, 다음을 얻을 수 있습니다.[무료 시험판](https://releases.groupdocs.com/) 구매하기 전에 .NET용 GroupDocs.Watermark의 기능을 평가해 보세요.
### GroupDocs.Watermark 라이센스를 어떻게 구매할 수 있나요?
 GroupDocs.Watermark에 대한 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy). 다양한 요구에 맞게 다양한 라이센스 옵션을 사용할 수 있습니다.
### 상업용 프로젝트에서 GroupDocs.Watermark를 사용할 수 있습니까?
 예, 유효한 라이센스가 있으면 상업용 프로젝트에서 GroupDocs.Watermark를 사용할 수 있습니다. 라이센스 이용 약관을 반드시 검토하십시오.[구매 페이지](https://purchase.groupdocs.com/buy).